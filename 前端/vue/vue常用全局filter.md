# vue常用全局filter

标签： filter

---

1. 保留小数位数
```javascript

    Vue.filter("toFixed", function (val, acc) {  //保留小数位，acc为保留几位小数位
        let num = parseFloat(val);
        if (isNaN(num)) {
            num = 0;
        }
        let accuracy = parseInt(acc);
        if (isNaN(accuracy) || accuracy < 0 || accuracy > 10) {
            accuracy = 2;
        }
        return num.toFixed(accuracy);
    });
    
```
2. 转百分比
```javascript

Vue.filter("toPercent", function (val, acc) {  //小数转百分比 ，acc为保留小数位
    let num = parseFloat(val);
    if (isNaN(num)) {
        num = 0;
    }   
    let accuracy = parseInt(acc);
    if (isNaN(accuracy) || accuracy < 0 || accuracy > 10) {
        accuracy = 2;
    }
    return (num * 100).toFixed(accuracy) + "%"
});

```

3. 通用键值转换
```javascript

import _ from 'underscore';
Vue.filter("keyToValueConverter", function (val, dataSource,keyname,valuename) { 
    if (val != null) {
        val = val.toString().trim();
        let matched = _.find(dataSource, function (obj) { return obj[keyname] == val; });
        if (matched) {
            return matched[valuename];
        }
    }
    return "";
});

```
4. 通用多键转多值
```javascript

import _ from 'underscore';
Vue.filter("keysToValuesConverter", function (val, dataSource, keyname, valuename, keySeparator, valueSeparator) {  //默认分隔符为逗号
    let text = "";
    if (!keySeparator || typeof (keySeparator) != 'string') {
        keySeparator = ',';
    }
    if (!valueSeparator || typeof (valueSeparator) != 'string') {
        valueSeparator = ',';
    }
    if (val != null) {
        let valueArr = val.split(',');
        let nameArr = _.map(valueArr, function (valueItem) {
            let matched = _.find(dataSource, function (item) { return item[keyname] == valueItem; });
            return matched ? matched[valuename] : null;
        });
        nameArr = _.filter(nameArr, (item) => { return item != null })
        if (nameArr && nameArr.length > 0) {
            text = nameArr.join(',');
        }
    }
    return text;
});

```

5. 日期格式化(用法同C# "yyyy-MM-dd HH:mm:ss")
```javascript

Vue.filter("dateTimeFormat", function (date, fmt = 'yyyy-MM-dd HH:mm:ss') {  //日期时间格式化 
    if (!date) {
        return ''
    }
    if (typeof date === 'string') {
        date = date.replace('T', ' ').replace('Z', '');
        date = new Date(date.replace(/-/g, '/'))
    }
    if (typeof date === 'number') {
        date = new Date(date)
    }
    var o = {
        'M+': date.getMonth() + 1,
        'd+': date.getDate(),
        'h+': date.getHours() % 12 === 0 ? 12 : date.getHours() % 12,
        'H+': date.getHours(),
        'm+': date.getMinutes(),
        's+': date.getSeconds(),
        'q+': Math.floor((date.getMonth() + 3) / 3),
        'S': date.getMilliseconds()
    }
    var week = {
        '0': '\u65e5',
        '1': '\u4e00',
        '2': '\u4e8c',
        '3': '\u4e09',
        '4': '\u56db',
        '5': '\u4e94',
        '6': '\u516d'
    }
    if (/(y+)/.test(fmt)) {
        fmt = fmt.replace(RegExp.$1, (date.getFullYear() + '').substr(4 - RegExp.$1.length))
    }
    if (/(E+)/.test(fmt)) {
        fmt = fmt.replace(RegExp.$1, ((RegExp.$1.length > 1) ? (RegExp.$1.length > 2 ? '\u661f\u671f' : '\u5468') : '') + week[date.getDay() + ''])
    }
    for (var k in o) {
        if (new RegExp('(' + k + ')').test(fmt)) {
            fmt = fmt.replace(RegExp.$1, (RegExp.$1.length === 1) ? (o[k]) : (('00' + o[k]).substr(('' + o[k]).length)))
        }
    }
    return fmt
});

```
6. 毫秒转时长(例：65000ms => 1分5秒)
```javascript
Vue.filter("msToShow", function (value) {  //毫秒转时长。例：65000ms => 1分5秒
    let totalS = parseInt(value / 1000);
    let hours = parseInt(totalS / 3600);
    let minutes = parseInt((totalS % 3600) / 60);
    let seconds = (totalS % 3600) % 60;
    let h = hours == 0 ? "" : `${hours}时`;
    let m = minutes == 0 ? "" : `${minutes}分`;
    let s = seconds == 0 ? "" : `${seconds}秒`;
    return h + m + s;
});
```
7. 毫秒格式化为时分秒（例：65000ms => 00:01:05）
```javascript
Vue.filter('msFormat', function (value) { // 毫秒格式化为时分秒  例：65000ms => 00:01:05
    let totalS = parseInt(value / 1000);
    let hours = parseInt(totalS / 3600);
    let minutes = parseInt((totalS % 3600) / 60);
    let seconds = (totalS % 3600) % 60;
    let h = hours > 9 ? hours : '0' + hours;
    let m = minutes > 9 ? minutes : '0' + minutes;
    let s = seconds > 9 ? seconds : '0' + seconds;
    return h + ':' + m + ':' + s;
});
```
8. byte转K、M、G
```javascript
Vue.filter("bytesToSize", function (bytes) { //文件大小单位转换
    if (bytes === 0) { return '0 B' };
    var k = 1024;
    var sizes = ['B', 'KB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB'];
    var i = Math.floor(Math.log(bytes) / Math.log(k));
    return (bytes / Math.pow(k, i)).toPrecision(4) + ' ' + sizes[i];
});
```




