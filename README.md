# 前端安全策略

## xss
xss(Cross Site Scripting)跨站脚本攻击
### 进攻原理
利用web应用中的安全漏洞，恶意在web页面中嵌入恶意的攻击性脚本。当用户浏览此网页时脚本就会在用户浏览器中执行，达到攻击目的。

### 进攻主要方法
大部分的 XSS 漏洞都是由于没有处理好用户的输入，导致恶意脚本在浏览器中执行。任何输入提交数据的地方都有可能存在 XSS。

### 防御
1. 使用XSS Filter
- 提交的表单添加判断校验，控制内容和长度，过滤掉特殊的html标签和js的onclikc事件标签。
2. html实体
- 从后台获取的html进行html entity编码，例如空格改成 & nbsp; 等
3. 对不可信的js进行编码，\ 转成 \\、/ 转成 \/、 ; 转成 ；(全角;)
4. httponly cookie,许多 XSS 攻击的目的就是为了获取用户的 cookie，将重要的 cookie 标记为 http only，这样的话当浏览器向服务端发起请求时就会带上 cookie 字段，但是在脚本中却不能访问 cookie，这样就避免了 XSS 攻击利用 js 的 document.cookie获取 cookie。