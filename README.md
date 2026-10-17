# 金山文档 PDF 阅读壳（测试）

把金山文档分享链接放进同页 iframe，顶层域名不是 `kdocs.cn`，用于验证 iPad Safari 顶部 WPS 横幅是否由 kdocs 顶层域名触发。

## 用法

```
https://chowalai.github.io/kdocs-shell-test/?doc=<URL 编码后的金山文档链接>
```

调试模式加 `&debug=1`，底部会显示运行信息。

## 说明

- 仅接受 `https://www.kdocs.cn/l/...` 与 `https://www.kdocs.cn/office/...`。
- 不保存、不上传任何文档内容或登录信息。
- iOS Safari 会隔离第三方 Cookie；若文档要求登录，可能需要在嵌入页内重新登录，甚至无法登录。这是该方案的已知限制。
