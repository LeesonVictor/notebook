# js生成uuid

标签: uuid guid

---

- [js生成uuid](#js生成uuid)
  - [guid(全局唯一标识符)](#guid全局唯一标识符)
    - [描述：](#描述)
  - [uuid（通用唯一标识符）](#uuid通用唯一标识符)
    - [1.描述：](#1描述)
    - [2.分类：](#2分类)
    - [3.生成](#3生成)
    - [4.作用](#4作用)
    - [5.冲突](#5冲突)
  - [参考资料](#参考资料)
  
---

## guid(全局唯一标识符)

### 描述：

 Globally Unique Identifier，为微软实现的uuid。

## uuid（通用唯一标识符）

### 1.描述：

Universally Unique Identifier。
  
### 2.分类：

uuid 有v1-v5五个版本，其中v2一般没用。

- **UUID Version 1**：基于时间的UUID
基于时间的UUID通过计算当前时间戳、随机数和机器MAC地址得到。由于在算法中使用了MAC地址，这个版本的UUID可以保证在全球范围的唯一性。但与此同时，使用MAC地址会带来安全性问题，这就是这个版本UUID受到批评的地方。如果应用只是在局域网中使用，也可以使用退化的算法，以IP地址来代替MAC地址－－Java的UUID往往是这样实现的（当然也考虑了获取MAC的难度）。

- **UUID Version 2**：DCE安全的UUID
DCE（Distributed Computing Environment）安全的UUID和基于时间的UUID算法相同，但会把时间戳的前4位置换为POSIX的UID或GID。这个版本的UUID在实际中较少用到。

- **UUID Version 3**：基于名字的UUID（MD5）
基于名字的UUID通过计算名字和名字空间的MD5散列值得到。这个版本的UUID保证了：相同名字空间中不同名字生成的UUID的唯一性；不同名字空间中的UUID的唯一性；相同名字空间中相同名字的UUID重复生成是相同的。

- **UUID Version 4**：随机UUID
根据随机数，或者伪随机数生成UUID。这种UUID产生重复的概率是可以计算出来的，但随机的东西就像是买彩票：你指望它发财是不可能的，但狗屎运通常会在不经意中到来。

- **UUID Version 5**：基于名字的UUID（SHA1）
和版本3的UUID算法类似，只是散列值计算使用SHA1（Secure Hash Algorithm 1）算法。

**如何选择**：

- 如果你只需要一个唯一的ID，你想要一个版本1或版本4。
  - 版本1：这将基于网卡MAC地址和计时器生成唯一的ID。这些ID很容易预测（给出一个，我可能会猜到另一个），可以追溯到你的网卡。不建议创建这些。
  - 版本4：这些是从随机（或伪随机）数字生成的。如果你只需要生成一个UUID，这可能是你想要的。

- 如果你需要始终从给定名称生成相同的UUID，则需要版本3或版本5。  
  - 版本3：这将从名称空间和名称的MD5哈希生成一个唯一的ID。如果您需要向后兼容（使用另一个从名称生成UUID的系统），请使用此选项。
  - 版本5：这将从名称空间和名称的SHA-1哈希生成唯一的ID。这是首选版本。
  
### 3.生成

直接使用开源类库uuid （[github地址](https://github.com/kelektiv/node-uuid)）。

    npm i uuid

```javascript

const uuidv1 = require('uuid/v1');
uuidv1(); //v1版本根据硬件信息（一般是网卡mac地址）和当前时间戳生成唯一性较高的uuid

```

或者由服务端生成返回前端

### 4.作用

唯一标识一条数据，一般可用作分布式数据库的主键。

### 5.冲突

uuid用有限字符标识无限的事物，理论上肯定会发生重复。
每秒产生10亿笔UUID，100年后只产生一次重复的机率是50%。如果地球上每个人都各有6亿笔GUID，发生一次重复的机率是50%。
产生重复GUID并造成错误的情况非常低，是故大可不必考虑此问题。

## 参考资料

[维基百科uuid](https://en.wikipedia.org/wiki/Universally_unique_identifier)
