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

## 实测结论（2026-10-17）

- `https://www.kdocs.cn/l/...` 中的 `/l/*` 是 WPS App 的 Universal Link 路径，Safari 顶部横幅由系统触发，网页 CSS / JS 无法移除。
- 把这个链接放进 iframe，会跳到 `account.wps.cn` 的登录页并停在空白页；用 CSP 拦掉登录跳转也不行，因为原页面已经导航走。
- 因此这个壳只适合「不需要登录、允许 iframe」的文档；对当前这份 PDF 不适用。
