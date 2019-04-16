# webStorage帮助类

标签: webStorage 帮助类

```javascript

//设置sessionStorage项
export function setSessionStore(name, value) {
    if (typeof Storage !== "undefined") {
      sessionStorage.setItem(name, JSON.stringify(value));
    }
  };
  //获取sessionStorage项
  export function getSessionStore(name) {
    if (typeof Storage !== "undefined") {
      return JSON.parse(sessionStorage.getItem(name));
    }
  };
  
  //移除sessionStorage项
  export function removeSessionStore(name) {
    if (typeof Storage !== "undefined") {
      sessionStorage.removeItem(name);
    }
  };
  
  //设置localStorage项
  export function setLocalStore(name, value) {
    if (typeof Storage !== "undefined") {
      localStorage.setItem(name, JSON.stringify(value));
    }
  };
  
  //获取localStorage项
  export function getLocalStore(name) {
    if (typeof Storage !== "undefined") {
      return JSON.parse(localStorage.getItem(name));
    }
  };
  
  //移除localStorage项
  export function removeLocalStore(name) {
    if (typeof Storage !== "undefined") {
      localStorage.removeItem(name);
    }
  };

```