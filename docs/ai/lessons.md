# 踩坑记录

## GitHub Pages 应直接提供 standalone 文件
- 问题现象：需要让页面不经过 Jekyll 处理。
- 根因：历史提交只确认 Jekyll 转换不符合此页面的发布方式，具体故障细节未记录。
- 解决办法：保留根目录 `.nojekyll`，并通过 Pages 原样托管。
- 相关文件：`.nojekyll`、`index.html`。
