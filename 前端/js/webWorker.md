# WebWorker

标签： js 工作线程

---

## 特点

- webWorker中不能操作DOM
- 不能使用大部分window对象的属性和方法（可以使用.createObjectURL()）
- webWorker中可以发起ajax请求
- 与主线程通过postMessage、onMessage传递通信
- 通信传的参数被复制，而非共享
  
## 分类

- 专用worker:仅能被首次生成它的脚本使用。
- 共享worker:可以同时被多个脚本使用。

## 限制
  
- 子线程代码需单独放一个文件里
- postMessage不能传方法过去

## 参考资料

- [https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Workers_API/Using_web_workers](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Workers_API/Using_web_workers)
