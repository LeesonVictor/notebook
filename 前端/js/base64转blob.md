# base64转blob

标签: base64 blob

---

```javascript

export function convertBase64ToBlob (imgData,imgType) {
    let bytes=window.atob(imgData);        //去掉url的头,并转换为byte  
    let imgBuffer = new ArrayBuffer(bytes.length);   //处理异常,将ascii码小于0的转换为大于0  
    let imgUnit = new Uint8Array(imgBuffer);
    for (var i = 0; i < bytes.length; i++) {  
        imgUnit[i] = bytes.charCodeAt(i);  
    }  
    return new Blob( [imgBuffer] , {type: imgType});    // 'image/png'
}

```