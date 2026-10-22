# 工业标签与轮胎标签：首轮 SEO 基线与执行清单

日期：2026-10-17（Asia/Shanghai）  
站点：https://www.cyjlabels.com/  
仓库：https://github.com/chadwick-ho/custom-tire-industrial-labels  
审计提交：`70c9cfb6acacee106297151313fe1f75e24a9e88`

## 结论

现有网站与 SEO 配置仍保存在 GitHub，可以从当前版本继续。用户已确认面向英语市场，轮胎标签和工业标签并重。首轮未发现需要紧急修复的基础元数据、静态内链或 sitemap 一致性问题；当前应建立流量基线，再优化有采购意图的核心页面。

本轮交付为项目接续记录、SEO 基线与关键词分工方案。未修改正式网页、未合并 PR、未上线变更；未恢复原聊天记录。

## 已核实的架构

- GitHub Pages 从 main 根目录发布，CNAME 为 www.cyjlabels.com；GitHub API 返回 built。
- 当前仓库树含 594 个文件、150 个 HTML 页面；其中 120 篇为博客文章。
- 仓库含静态 HTML、图片、CSS 和已编译 JS；未发现原应用源代码或 package.json。
- 原始工程是否还有备份未知。不能把静态导出目录当成已恢复的可构建应用。

## 基础检查结果

| 检查项 | 源码检查结果 |
|---|---|
| 页面 Title / description | 150/150 均非空；分别无重复 |
| H1 | 150/150 每页一个 |
| canonical | 150/150 与现有 HTTPS 页面 URL 对应 |
| robots meta | 150/150 为 index, follow |
| XML sitemap | 150 个唯一 URL，与页面集合一致 |
| robots.txt | 允许抓取，并声明正确 sitemap URL |
| 静态页面内链 | 未发现指向仓库缺失页面的链接 |
| 可达性与锚点 | 150 页均可从首页沿静态内链到达；未发现缺失的目标锚点 |
| HTML 直接资源引用 | 所引用文件存在于审计提交的仓库树 |
| 图片标记 | 解析到的 img 均含 ALT 属性与 width/height；未评估 ALT 质量 |
| JSON-LD | 所解析脚本均为有效 JSON；尚未做富媒体结果/语义验收 |

方法：通过 GitHub API 获取固定提交的文件树与 162 个文本文件，用 HTMLParser 解析全部 HTML，比较页面、内链、锚点、JSON-LD 与 sitemap。没有下载或逐个测试全部图片/运行文件，也没有验证 JS 的间接 import 依赖。文件树存在不等于线上网络请求一定成功。

## 本轮发现的优化机会

### 1. 先补数据基线，才能判断实际瓶颈

尚无 Search Console 或 GA4 数据，当前不能判断“未收录”“有曝光无点击”还是“有访问无询盘”。建议记录最近 28 天和 90 天的查询、落地页、国家、点击、曝光和索引状态，之后按有效询盘衡量两条产品线。

### 2. 首页主标题可以更直接表达业务

当前 H1 为 “FACTORY CUSTOM LABELS MADE TO YOUR SPEC”，覆盖了定制意图，但没有在主标题中直接说明轮胎与工业标签。

下一轮建议草案：**Custom Tire & Industrial Labels Made to Your Spec**。保留现有设计和询盘入口，调整后检查桌面与手机换行。此建议尚未写入网页，不能视为已上线。

### 3. 核心产品页与博客要承担不同任务

已存在 120 篇博客。下一轮先完善采购页的选型、样品和报价信息，再把相关博客正文中的上下文链接导向对应采购页。分类页承担商业词，博客解答实际问题，避免同一商业主题在多个页面反复争夺主位置。这是工作假设，需用 Search Console 的查询与页面数据验证，尚未证明存在关键词冲突。

关键词映射见同目录 seo-keyword-map.csv；词组按现有业务与内容推导，**不是搜索量、竞争难度或排名数据**。tire/tyre 先自然覆盖于同一主题，不仅为拼写差异新建重复页。

### 4. 询盘路径需要真实验证

联系页按钮为 “Prepare My Requirements”，页面说明随后使用邮件草稿并添加附件，且提供 WhatsApp 与邮箱入口。它不能直接当作已接通后台收件的在线表单。应验证需求整理、邮件草稿、附件说明及手机端操作，并将“点击入口”和“实际收到询盘”分开统计。本轮没有发送测试询盘。

### 5. 增加可验证的采购证据

分类页中多处仍使用通用的 material/adhesive/project discussion 描述。可补充真实产品图、对应材质、表面、尺寸范围、样品确认过程和已证明的应用限制。工厂身份、认证、MOQ、交期与性能未获新证据前，不扩写承诺。

## 下一轮执行批次

| 批次 | 轮胎标签 | 工业标签 | 验收依据 |
|---|---|---|---|
| 基线 | 分类页、胎面页、条码页 | 分类页、设备页、工业条码页 | 记录现有查询、页面指标与询盘入口 |
| 内容 | 选型、图稿、SKU、卷向与样品信息 | 表面、环境、识别字段与样品信息 | 文字可证实，每页意图明确，无新增重复 URL |
| 内链 | 相关轮胎博客 → 对应采购页 | 相关工业博客 → 对应采购页 | 上下文匹配、目标页存在、保留现有结构 |
| 转化 | 轮胎需求示例 | 工业需求示例 | 手机可用，发送步骤清楚，询盘送达验证 |

先以各三页并重推进；国家、搜索量和真实转化数据出来后，再调整优先级。所有网页修改先在独立分支验证，以 PR 审阅，main 合并会触发正式站发布。

## 尚未验证

- 150 个线上 URL 的实际 HTTP 状态、重定向和 Google 收录状态。
- 搜索词、排名、点击率、流量国家、Search Console / GA4 与询盘归因。
- 桌面/手机视觉与客户端交互：浏览器打开正式站超时。
- Core Web Vitals、运行时 JS 完整性、Schema 语义及富媒体结果资格。
- 邮件送达、WhatsApp 会话、附件发送和真实订单转化。
- 原始可编辑工程的位置、工厂与产品信息的证明材料。

## 参考依据

- [Google：canonical 与站内链接一致性](https://developers.google.com/search/docs/crawling-indexing/consolidate-duplicate-urls)。现有一致配置予以保留。
- [Google：标题链接](https://developers.google.com/search/docs/appearance/title-link)。标题应准确表达页面主题，不为固定字数盲目重写。
- [Google：面向用户的有帮助内容](https://developers.google.com/search/docs/fundamentals/creating-helpful-content)。优先完善有实际采购价值的现有内容。
- [Google：Search Console 使用说明](https://developers.google.com/search/docs/monitor-debug/search-console-start)。用索引与表现数据建立基线。
