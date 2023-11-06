# GetOpenaiAccessToken
### 食用方法
F12打开控制台，执行下面代码
```javascript
// 创建一个新的 XMLHttpRequest 对象
var xhr = new XMLHttpRequest();

// 设置请求方法和URL
xhr.open("GET", "https://chat.openai.com/api/auth/session", true);

// 设置响应类型为 JSON
xhr.responseType = "json";

// 处理响应
xhr.onload = function () {
  if (xhr.status === 200) {
    // 提取 accessToken 字段
    var accessToken = xhr.response.accessToken;
    console.log("accessToken:", accessToken);

    // 复制到剪贴板
    var tempInput = document.createElement("input");
    tempInput.value = accessToken;
    document.body.appendChild(tempInput);
    tempInput.select();
    document.execCommand("copy");
    document.body.removeChild(tempInput);

    console.log("accessToken 已复制到剪贴板");
  } else {
    console.error("HTTP请求错误：" + xhr.status);
  }
};

// 发送请求
xhr.send();
```