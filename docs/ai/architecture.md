# 架构概览

## 交付形态
仓库根目录只有 `.nojekyll` 与 `index.html`。没有后端、包管理文件、构建配置、测试目录或 CI 工作流。项目通过 GitHub Pages 提供静态页面；2026-11-08 的提交说明页面按 standalone viewer 原样发布。

## 页面结构与数据流
1. 浏览器加载根目录 `index.html`。最外层文档提供页面标题、基础样式和 iframe 容器。
2. 容器为 `#codex-visualization`，设置 `sandbox="allow-scripts"`，可视化内容以内嵌的 `data-srcdoc` HTML 提供。
3. 页面内嵌 CSP 允许特定 CDN 的脚本/样式/资源来源；其 `connect-src` 仅允许 `blob:` 和 `data:`。没有发现仓库级服务端数据流或环境变量配置。
4. `.nojekyll` 阻止 Pages 对 standalone 文件做 Jekyll 处理。

## 模块边界
HTML/CSS/JavaScript 集中在单个大型文件内，仓库没有拆分模块或生成源。本文只依据文件开头、CSP、iframe 外壳和 Git 历史整理；没有通读嵌入页面的全部实现。若需要改 3D 场景内部逻辑，应先定位相关内嵌片段，不要把整个文件注入上下文。

## 未确认
- 3D 场景实际使用的库及精确版本；CSP 白名单不等于实际依赖清单。
- 生成该 HTML 的源文件或工具是否存在于仓库外。
- 手动验收步骤、浏览器支持范围和产品行为规则。
