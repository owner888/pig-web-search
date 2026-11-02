# pig-web-search

pig 编程助手的网络搜索：纯 PHP 实现搜索和读网页，不需要 API key——DuckDuckGo 搜索结果、网页正文，以及用无头 Chrome 渲染后的页面内容（适合 JavaScript 生成的页面）。

[English](README.md)

## 安装

```bash
pig install git:github.com/owner888/pig-web-search
```

搜索和读网页不需要别的：没有 Composer 依赖，也不用 API key。`browse_web_page` 另外需要本机装有 Chrome 或 Chromium。

网络搜索以前是 pig 自带的扩展，现在是独立的包。`pig update` 会删掉旧的自带副本并打印上面的安装命令；`disabledExtensions: ["pig-web-search"]` 照样对这个包生效。

## 工具

| 工具 | 作用 |
| --- | --- |
| `web_search` | 用 DuckDuckGo 搜索，返回前几条结果：标题、摘要、网址（`maxResults`，默认 5，最多 10） |
| `fetch_web_page` | 网页的正文，去掉脚本、导航和样式（`maxLength`，默认 30000 字符，最多 60000）。只读服务器直接返回的内容，速度快 |
| `browse_web_page` | 用无头 Chrome 渲染页面，等 JavaScript 跑完后返回页面文字——适合 `fetch_web_page` 拿回来是空白或加载壳的单页应用、控制台、文档站。慢几秒 |

### 命令

`/search <关键词>` 搜索并显示前五条结果。

### Chrome

`browse_web_page` 用一次性的配置目录以无头模式启动 Chrome，通过 pig 自己的 socket 走 DevTools 协议控制它，用完删掉配置目录。查找顺序：先看 `CHROME_PATH`，再看常见安装位置，最后在 `PATH` 里找 `google-chrome`、`chromium`、`chromium-browser` 或 `chrome`。找不到时这个工具会说明原因，另外两个工具照常可用。

## 开发

测试依赖一份 pig 源码：

```bash
PIG_DIR=~/path/to/pig ~/path/to/pig/vendor/bin/phpunit -c phpunit.xml
```

`PIG_DIR` 默认是本包旁边的 `pig` 目录。渲染页面的那个测试需要 Chrome，没有时会跳过。

## 许可证

MIT，见 [LICENSE](LICENSE)。
