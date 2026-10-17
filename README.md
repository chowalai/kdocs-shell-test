# 金山文档 PDF 去横幅测试 · 结论页

原计划把金山文档分享链接放进同页 iframe，验证 iPad Safari 顶部 WPS 横幅是否由 kdocs 顶层域名触发。2026-10-17 实测完成，iframe 方案不可用，本页改为结论说明。

## 用法

```
https://chowalai.github.io/kdocs-shell-test/?doc=<URL 编码后的金山文档链接>
```

## 说明

- 页面不再嵌入 iframe，不会触发 WPS 登录跳转，也不会出现闪烁的诊断按钮。
- 只读取 `doc` 参数并生成「打开原文档」链接，不保存、不上传任何内容。

## 实测结论（2026-10-17）

- `https://www.kdocs.cn/l/...` 中的 `/l/*` 是 WPS App 的 Universal Link 路径，Safari 顶部横幅由系统触发，网页 CSS / JS 无法移除。
- 把这个链接放进 iframe，会跳到 `account.wps.cn` 的登录页并停在空白页；用 CSP 拦掉登录跳转也不行，因为原页面已经导航走。
- `/office/s/` 能避开 Universal Link，但用 shareId 调 `/open/et` 返回 `InvalidArgument`，PDF 渲染不出来。
- 渲染完成后用 `history.replaceState` 改 URL，Safari 也不会撤掉已出现的横幅（iPad 实测）。
- 结论：保留 WPS App 的前提下，Safari 里没有纯网页方案能去掉这条横幅。
