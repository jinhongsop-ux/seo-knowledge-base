# Google 技术 SEO

[知识库首页](../README.md) · [术语索引](glossary-index.md)

6 个分类 · 40 条术语

## 分类目录

- [抓取机制 (Crawling Mechanism)](#category-1)
- [索引机制 (Indexing Mechanism)](#category-2)
- [渲染机制 (Rendering Mechanism)](#category-3)
- [核心网页指标 (Core Web Vitals)](#category-4)
- [结构化数据 (Structured Data / Schema.org)](#category-5)
- [算法更新与惩罚机制 (Algorithm Updates & Penalty Terms)](#category-6)

<a id="category-1"></a>

## 抓取机制 (Crawling Mechanism)

- [Googlebot / 谷歌爬虫](#term-3-01)
- [Crawl Budget / 抓取预算](#term-3-02)
- [Crawl Frequency / 抓取频率](#term-3-03)
- [Crawl Errors / 抓取错误](#term-3-04)
- [Link Discovery / 链接发现](#term-3-05)
- [Fetch as Google / 谷歌抓取测试](#term-3-06)

<a id="term-3-01"></a>

### Googlebot / 谷歌爬虫

**定义**

Google 的自动化网页抓取程序，分为 Googlebot Desktop 和 Googlebot Smartphone 两个版本，通过跟随链接发现和下载网页内容供 Google 索引系统处理。

**实战意义**

监控 Googlebot 的访问行为：在 Google Search Console \> Coverage 报告中查看抓取错误；在服务器 access.log 中过滤 'Googlebot' User-Agent；确保 Googlebot Smartphone（移动版爬虫，负责 Mobile-First Indexing）能正常访问所有关键页面。

<a id="term-3-02"></a>

### Crawl Budget / 抓取预算

**定义**

Google 在特定时间段内愿意对某网站分配的爬虫访问资源总量，受站点权威度、服务器响应速度和内容质量综合影响。

**实战意义**

大型独立站（1000+ 页面）需主动管理爬虫预算：①通过 robots.txt 屏蔽低价值页面（购物车/账户页/过滤器页）②提高服务器响应速度（TTFB \< 200ms）③优化内部链接结构聚焦权重 ④在 Search Console 监控抓取频率趋势。

<a id="term-3-03"></a>

### Crawl Frequency / 抓取频率

**定义**

Googlebot 访问特定页面的时间间隔，受页面更新频率、域名权威度和链接重要性共同影响——高权重、频繁更新的页面被更频繁抓取。

**实战意义**

提高核心页面的抓取频率：①频繁更新内容 ②获取高质量外链 ③在 Sitemap 中准确设置 `<changefreq>` 和 `<lastmod>` ④通过 Search Console「URL Inspection」手动请求重新抓取新发布的重要页面。

<a id="term-3-04"></a>

### Crawl Errors / 抓取错误

**定义**

Googlebot 在访问网站页面时遇到的错误类型，包括 4xx 客户端错误（404 Not Found, 403 Forbidden）、5xx 服务器错误（500 Internal Server Error）和 DNS 解析错误。

**实战意义**

在 Google Search Console \> Coverage \> Excluded 报告中监控；404 错误：检查是否有重要页面被意外删除，设置 301 重定向；5xx 错误：通常是服务器过载或配置问题，需立即修复，持续 5xx 会导致 Crawl Budget 减少和排名下降。

<a id="term-3-05"></a>

### Link Discovery / 链接发现

**定义**

Googlebot 通过跟踪 HTML 页面中的超链接 `<a href>` 发现新 URL 的主要机制，这是 Google 索引生态系统的核心工作原理。

**实战意义**

确保重要页面有足够的内链指向（孤儿页面 Orphan Pages 无法被有效发现）；检查 JavaScript 渲染的链接是否可被爬虫发现（非渲染状态下查看 HTML 源码中是否存在链接 href）；Sitemap 作为链接发现的补充路径。

<a id="term-3-06"></a>

### Fetch as Google / 谷歌抓取测试

**定义**

Google Search Console 中的「URL Inspection」工具允许站长查看 Google 对特定 URL 的抓取结果、渲染状态和索引状态，是排查技术 SEO 问题的核心工具。

**实战意义**

每次重要页面上线或更新后使用：① URL Inspection 输入页面 URL ② 查看「Page is indexed / Not indexed」状态 ③「Test Live URL」测试当前可见内容 ④「View Crawled Page」查看 Google 看到的 HTML ⑤点击「Request Indexing」加速收录。

<a id="category-2"></a>

## 索引机制 (Indexing Mechanism)

- [Google Index / 谷歌索引](#term-3-07)
- [Mobile-First Indexing / 移动优先索引](#term-3-08)
- [Index Coverage Report / 索引覆盖报告](#term-3-09)
- [Crawled Currently Not Indexed / 已抓取暂未收录](#term-3-10)
- [Index Bloat / 索引膨胀](#term-3-11)

<a id="term-3-07"></a>

### Google Index / 谷歌索引

**定义**

Google 存储和组织已抓取网页内容的超大型数据库，是 Google 搜索系统的核心基础设施，只有进入索引的页面才可能出现在搜索结果中。

**实战意义**

通过 site:yourdomain.com 查看被索引的总页面数；定期与实际页面数量对比，识别「已抓取但未索引」的页面（通常说明内容质量问题或技术障碍）；Google Search Console 的 Coverage 报告是索引状态的权威数据源。

<a id="term-3-08"></a>

### Mobile-First Indexing / 移动优先索引

**定义**

Google 自 2019 年起正式将移动版本的网页内容作为索引和排名的主要评判标准，而非桌面版，对应 Googlebot Smartphone 爬虫的内容抓取结果。

**实战意义**

确保：①移动版页面包含与桌面版完全相同的主要内容和结构化数据 ②移动版加载速度优化（Core Web Vitals 移动分数通常低于桌面）③图片和视频在移动端正确显示 ④避免「桌面有内容移动端隐藏」的做法——隐藏内容不被索引。

<a id="term-3-09"></a>

### Index Coverage Report / 索引覆盖报告

**定义**

Google Search Console 提供的详细报告，分类展示所有已提交 URL 的索引状态（已索引/已排除/包含错误/包含警告），并标注排除原因。

**实战意义**

重点关注四大状态：Error（错误，需立即修复）、Valid with Warning（有警告，需处理）、Valid（正常索引）、Excluded（被排除，查看原因是否合理）；常见排除原因：Crawled Currently Not Indexed（内容质量问题）、Duplicate Without Canonical（重复内容）。

<a id="term-3-10"></a>

### Crawled Currently Not Indexed / 已抓取暂未收录

**定义**

Google 已成功抓取页面内容，但主动决定不将其纳入索引的状态，通常表明 Google 判断该页面质量不足以提供独特价值。

**实战意义**

这是 2023-2026 年间独立站最常见的严重技术 SEO 问题；解决方案：①大幅提升页面内容质量和独特性 ②增加外链权威信号 ③检查是否存在 Thin Content ④添加 E-E-A-T 信号（作者信息/引用来源）⑤合并相似低质量页面。

<a id="term-3-11"></a>

### Index Bloat / 索引膨胀

**定义**

网站中被 Google 索引的页面数量远超实际有价值内容页面数量的问题状态，大量低质量页面的索引会稀释整站的 Crawl Budget 和内容权威信号。

**实战意义**

常见来源：无限参数 URL（?color=red&size=M 等组合）、分页页面、标签/分类归档页、会话 ID URL；解决方案：robots.txt 阻止抓取 + Meta Robots noindex + 在 Shopify 的 URL 过滤器参数处理 + 合理使用 canonical。

<a id="category-3"></a>

## 渲染机制 (Rendering Mechanism)

- [JavaScript Rendering / JavaScript 渲染](#term-3-12)
- [Server-Side Rendering (SSR) / 服务端渲染](#term-3-13)
- [Dynamic Rendering / 动态渲染](#term-3-14)
- [Static Site Generation (SSG) / 静态站点生成](#term-3-15)
- [Render Budget / 渲染预算](#term-3-16)

<a id="term-3-12"></a>

### JavaScript Rendering / JavaScript 渲染

**定义**

Googlebot 执行网页 JavaScript 代码以获取动态生成内容的过程——与 HTML 内容即时可见不同，JS 内容需经过渲染队列处理，存在延迟。

**实战意义**

React/Vue/Next.js 等前端框架搭建的独立站需特别注意：用 Google Search Console 的 URL Inspection 工具中「View Crawled Page」截图，确认 Googlebot 是否成功渲染关键内容；关键 SEO 内容（产品描述/价格/评论）不应依赖纯客户端 JS 渲染。

<a id="term-3-13"></a>

### Server-Side Rendering (SSR) / 服务端渲染

**定义**

在服务器端生成完整 HTML 后发送给浏览器和爬虫，确保内容在不执行 JavaScript 的情况下即时可见的技术架构。

**实战意义**

SSR 对 SEO 最友好（内容无需 JS 执行即可被爬取）；Next.js（React 框架）支持 SSR，是搭建 SEO 友好型独立站前端的优选方案；Shopify 和 WooCommerce 原生使用服务端渲染，无需额外配置。

<a id="term-3-14"></a>

### Dynamic Rendering / 动态渲染

**定义**

服务器检测到爬虫 User-Agent 时提供预渲染 HTML 版本，而对普通用户提供 JavaScript 版本的临时解决方案。

**实战意义**

这是 Google 官方建议的 JS SEO 临时解决方案（非长期最佳实践）；工具：Rendertron、Prerender.io；但 Google 官方建议最终迁移至 SSR 或静态生成（SSG）；避免将动态渲染误用于向爬虫展示不同内容（Cloaking 违规）。

<a id="term-3-15"></a>

### Static Site Generation (SSG) / 静态站点生成

**定义**

在构建时预先生成所有 HTML 页面文件，部署为纯静态文件的技术架构，具有极快的 TTFB 和对爬虫的最佳可见性。

**实战意义**

SSG 是 Core Web Vitals 性能优化的终极形态；适用于内容不频繁变化的页面（博客文章/FAQ 页面）；Gatsby、Hugo、Astro 等 SSG 框架可将博客内容编译为纯 HTML，实现极低 TTFB（\< 50ms）。

<a id="term-3-16"></a>

### Render Budget / 渲染预算

**定义**

与 Crawl Budget 类似，Google 为每个网站分配的 JavaScript 渲染资源有限，JS 密集型站点的所有页面可能无法获得同等渲染资源。

**实战意义**

优化渲染预算：①核心 SEO 内容不依赖 JS ②减少页面 JS bundle 大小 ③使用 SSR/SSG ④避免在 SEO 关键页面使用复杂的客户端框架；可通过「Fetch as Google」定期抽检关键页面的渲染状态。

<a id="category-4"></a>

## 核心网页指标 (Core Web Vitals)

- [Core Web Vitals (CWV) / 核心网页指标](#term-3-17)
- [LCP (Largest Contentful Paint) / 最大内容绘制](#term-3-18)
- [INP (Interaction to Next Paint) / 下次绘制交互](#term-3-19)
- [FID (First Input Delay) / 首次输入延迟](#term-3-20)
- [CLS (Cumulative Layout Shift) / 累积布局偏移](#term-3-21)
- [TTFB (Time to First Byte) / 首字节时间](#term-3-22)
- [FCP (First Contentful Paint) / 首次内容绘制](#term-3-23)
- [PageSpeed Insights (PSI) / 页面速度洞察](#term-3-24)

<a id="term-3-17"></a>

### Core Web Vitals (CWV) / 核心网页指标

**定义**

Google 于 2021 年纳入排名算法的三项用户体验量化指标（LCP、INP、CLS），是 Page Experience 评分系统的核心组成部分，通过真实用户数据（CrUX）衡量。

**实战意义**

在 Google Search Console \> Core Web Vitals 报告中监控；主要数据来源是 Chrome User Experience Report（CrUX），反映真实用户体验数据（Field Data）；优先修复「Poor URLs」（差）\> 「Need Improvement URLs」（需改进）；这是 Google 官方确认影响排名的 UX 信号。

<a id="term-3-18"></a>

### LCP (Largest Contentful Paint) / 最大内容绘制

**定义**

页面视口内最大可见内容元素（通常是主图或大标题）完成渲染所需的时间，衡量页面的感知加载速度。阈值：Good ≤ 2.5s / Poor \> 4s。

**实战意义**

独立站 LCP 最常见问题元素：Hero Image（首屏大图）；优化方案：①压缩 Hero Image 至 WebP/AVIF 格式 ②在 `<head>` 添加 `<link rel='preload'>` 预加载 Hero Image ③使用 CDN（Shopify 内置 Fastly CDN）④避免对 LCP 元素使用懒加载。

<a id="term-3-19"></a>

### INP (Interaction to Next Paint) / 下次绘制交互

**定义**

2024 年 3 月正式取代 FID 成为 CWV 指标，测量页面对用户交互（点击/键盘输入）的响应到下次视觉更新之间的最慢延迟。阈值：Good ≤ 200ms / Poor \> 500ms。

**实战意义**

INP 取代 FID 后覆盖更完整的交互生命周期；优化方案：①拆分长任务（Long Tasks \> 50ms）②避免在交互处理器中执行繁重计算 ③移除非必要第三方脚本（ChatBot/弹窗/追踪像素等）④使用 Chrome DevTools Performance 面板分析 INP 瓶颈。

<a id="term-3-20"></a>

### FID (First Input Delay) / 首次输入延迟

**定义**

已被 INP 取代的原 CWV 指标，测量用户首次交互（如点击按钮）到浏览器响应开始处理的延迟时间。

**实战意义**

【已废弃 — 2024年3月被 INP 取代】如仍见旧报告数据，了解即可；所有针对 FID 的优化措施（减少主线程阻塞）在 INP 优化中仍有效；重要区别：INP 测量所有交互中最慢的那次，而 FID 仅测量第一次交互。

<a id="term-3-21"></a>

### CLS (Cumulative Layout Shift) / 累积布局偏移

**定义**

测量页面整个生命周期内发生的所有意外布局移动的累积分数，量化「页面元素在加载过程中突然移动」给用户造成的视觉不稳定性。阈值：Good ≤ 0.1 / Poor \> 0.25。

**实战意义**

Shopify 独立站常见 CLS 原因：①未指定尺寸的图片（加载后撑开布局）②异步加载的广告/嵌入内容 ③自定义字体加载导致文字重排（FOUT）；修复：为所有 img/video 元素明确设置 width 和 height 属性，避免动态注入影响布局的 DOM 元素。

<a id="term-3-22"></a>

### TTFB (Time to First Byte) / 首字节时间

**定义**

浏览器发出 HTTP 请求后，接收到服务器响应的第一个字节所需的时间，反映服务器响应速度和网络延迟。阈值：Good ≤ 800ms / Poor \> 1800ms。

**实战意义**

TTFB 是所有性能优化的起点——再好的前端优化也无法弥补极慢的服务器响应；优化方案：①使用高质量主机或 CDN ②启用服务器端缓存（对于 WooCommerce 尤为重要）③优化数据库查询 ④Shopify 的全球 Fastly CDN 使 TTFB 通常 \< 100ms。

<a id="term-3-23"></a>

### FCP (First Contentful Paint) / 首次内容绘制

**定义**

浏览器渲染出第一个可见 DOM 内容（文本/图片/SVG）的时间，是用户感知页面「开始有东西显示」的时刻。阈值：Good ≤ 1.8s。

**实战意义**

优化 FCP：①消除渲染阻塞资源（render-blocking CSS/JS）②预加载关键字体 ③减少服务器响应时间（TTFB）④内联关键 CSS（Critical CSS）直接嵌入 `<head>`，无需等待外部 CSS 文件加载。

<a id="term-3-24"></a>

### PageSpeed Insights (PSI) / 页面速度洞察

**定义**

Google 官方提供的免费网页性能分析工具，同时展示实验室数据（Lighthouse）和真实用户数据（CrUX Field Data），是评估 Core Web Vitals 的主要工具。

**实战意义**

使用 PSI（pagespeed.web.dev）分别测试：①产品页 ②集合页 ③首页 ④博客文章（各类型页面性能特征不同）；优先关注「Field Data」（真实用户数据）而非 Lab Data（Lighthouse 模拟数据）——Field Data 才是 Google 排名算法使用的数据源。

<a id="category-5"></a>

## 结构化数据 (Structured Data / Schema.org)

- [JSON-LD / JSON 链接数据](#term-3-25)
- [Product Schema / 产品结构化数据](#term-3-26)
- [Review Schema / 评论结构化数据](#term-3-27)
- [FAQ Schema / 常见问题结构化数据](#term-3-28)
- [BreadcrumbList Schema / 面包屑列表结构化数据](#term-3-29)
- [Organization Schema / 机构结构化数据](#term-3-30)
- [Article Schema / 文章结构化数据](#term-3-31)
- [SitelinksSearchbox Schema / 站内搜索框结构化数据](#term-3-32)

<a id="term-3-25"></a>

### JSON-LD / JSON 链接数据

**定义**

Google 官方推荐的结构化数据实现格式，将 Schema 标记以独立的 `<script type='application/ld+json'>` 标签嵌入页面，与 HTML 内容完全分离，易于实施和维护。

**实战意义**

优先使用 JSON-LD 而非 Microdata 或 RDFa；可放置在 `<head>` 或 `<body>` 末尾；Shopify 主题通过 Liquid 模板动态生成 JSON-LD；使用 Google Rich Results Test Tool（search.google.com/test/rich-results）验证实现是否正确。

<a id="term-3-26"></a>

### Product Schema / 产品结构化数据

**定义**

使用 Schema.org/Product 标记产品页面的名称、描述、价格、货币、可用性、品牌、评分等信息，使 Google 能在 SERP 中展示产品富结果（价格/评分/库存状态）。

**实战意义**

独立站产品页必做项：包含 name、description、image、sku、brand、offers（price、priceCurrency、availability、url）、aggregateRating；产品富结果可在 SERP 中直接展示价格和评分，显著提升 CTR；在 Shopify 通过主题 liquid 或 SEO 插件实现。

<a id="term-3-27"></a>

### Review Schema / 评论结构化数据

**定义**

使用 Schema.org/Review 或 AggregateRating 标记产品或业务的用户评分数据，可触发 SERP 中的星级评分显示（星星富结果）。

**实战意义**

在产品页的 Product Schema 中嵌套 aggregateRating（ratingValue、reviewCount）；仅标记真实用户评价（Google 明确禁止对自家产品的编辑性评分使用 Review Schema）；Shopify 的评价应用（如 Loox, Okendo）通常自动生成 Review Schema。

<a id="term-3-28"></a>

### FAQ Schema / 常见问题结构化数据

**定义**

使用 Schema.org/FAQPage 标记页面中的问答内容，可在 SERP 中触发 FAQ 富结果展开（直接在搜索结果下方展示问答对），大幅扩展 SERP 占据空间。

**实战意义**

在博客文章底部添加 3-5 个相关 FAQ，配套实现 FAQPage Schema；FAQ 富结果使你的搜索结果占据双倍甚至三倍 SERP 空间，CTR 可提升 20-30%；注意：Google 2023 年起大幅限制 FAQ 富结果的展示（主要展示给权威政府/医疗网站），独立站出现概率降低但仍值得实施。

<a id="term-3-29"></a>

### BreadcrumbList Schema / 面包屑列表结构化数据

**定义**

使用 Schema.org/BreadcrumbList 标记页面的导航路径层级，可触发 SERP 中 URL 位置显示为可读的面包屑路径而非原始 URL。

**实战意义**

Shopify 主题通常自动生成 BreadcrumbList Schema；在 URL 外观上将 'https://yourstore.com/collections/bikes/products/carbon-road-bike' 替换为 'yourstore.com › Bikes › Carbon Road Bike'，更可读且提升 CTR；所有具有层级结构的页面均应实施。

<a id="term-3-30"></a>

### Organization Schema / 机构结构化数据

**定义**

使用 Schema.org/Organization 标记品牌/企业的基本信息（名称、Logo、联系方式、社交媒体链接），帮助 Google 建立对品牌实体的知识图谱理解。

**实战意义**

在网站首页或全站 `<head>` 中实施一次 Organization Schema；包含 name、url、logo、contactPoint、sameAs（链接所有社交媒体主页）；这是建立 E-E-A-T 「权威性（Authority）」信号的基础，也有助于触发 Google Knowledge Panel（知识面板）。

<a id="term-3-31"></a>

### Article Schema / 文章结构化数据

**定义**

使用 Schema.org/Article（或子类型 BlogPosting、NewsArticle）标记博客文章的作者、发布日期、修改日期和内容，可增强文章的 E-E-A-T 信号。

**实战意义**

博客文章页面必须实施：包含 headline、datePublished、dateModified、author（含 Person Schema）、image；特别重要：author 的 Person Schema 应包含作者真实姓名和 URL（链接至作者简介页），这是 E-E-A-T「经验（Experience）」信号的结构化表达。

<a id="term-3-32"></a>

### SitelinksSearchbox Schema / 站内搜索框结构化数据

**定义**

允许用户直接在 SERP 的品牌搜索结果中使用站内搜索功能的 Schema 标记，提升品牌搜索结果的功能性。

**实战意义**

当用户搜索你的品牌名时，Google 可能在搜索结果中直接展示你的站内搜索框；实施 SearchAction Schema 并确保站内搜索功能完善；对于品牌词搜索量可观的成熟独立站，可提升用户直接找到目标产品的效率。

<a id="category-6"></a>

## 算法更新与惩罚机制 (Algorithm Updates & Penalty Terms)

- [Google Panda Algorithm / 熊猫算法](#term-3-33)
- [Google Penguin Algorithm / 企鹅算法](#term-3-34)
- [Google Helpful Content System / 有用内容系统](#term-3-35)
- [Core Algorithm Update / 核心算法更新](#term-3-36)
- [Manual Action / 手动惩罚](#term-3-37)
- [Cloaking / 隐藏作弊](#term-3-38)
- [Thin Content / 稀薄内容](#term-3-39)
- [Duplicate Content / 重复内容](#term-3-40)

<a id="term-3-33"></a>

### Google Panda Algorithm / 熊猫算法

**定义**

2011 年推出的 Google 算法更新，专门针对低质量、Thin Content（稀薄内容）、内容农场（Content Farm）和高重复性内容，大幅降低其搜索排名。

**实战意义**

2016 年已整合入 Google 核心算法成为持续更新信号；当前对应表现：大量低质量页面会拖累整站权重；解决方案：合并 Thin Content 页面、添加实质性内容、删除或 noindex 低质量页面、提升整体内容质量。

<a id="term-3-34"></a>

### Google Penguin Algorithm / 企鹅算法

**定义**

2012 年推出的 Google 算法，专门打击通过操纵性外链建设（购买链接/链接农场/过度关键词锚文本）人工堆积外链权重的网站。

**实战意义**

2016 年整合入核心算法成为实时更新；当前独立站风险：购买批量低质量外链、过度精确匹配锚文本；若发现异常排名下降，使用 Google Search Console 的 Disavow Links Tool 否认有害外链；2024 年后 Google 通常自动忽略垃圾链接而非惩罚，但极端情况仍可触发 Manual Action。

<a id="term-3-35"></a>

### Google Helpful Content System / 有用内容系统

**定义**

Google 2022 年推出并于 2024 年 3 月完全整合入核心算法的评估系统，专门识别并降权为搜索引擎而非为用户写作的内容，奖励真正解决用户需求的原创深度内容。

**实战意义**

这是 2024-2026 年最影响独立站博客流量的算法系统；「为人写作」检查清单：①是否包含第一手经验（亲测/真实案例）②是否提供与其他页面不同的独特见解 ③是否能在没有广告收入驱动下仍然存在的内容 ④是否满足用户的完整需求（让用户不需要二次搜索）。

<a id="term-3-36"></a>

### Core Algorithm Update / 核心算法更新

**定义**

Google 每年发布 3-5 次的广泛性排名算法更新，重新评估整个索引中内容的相对质量和相关性，可导致网站排名出现大幅波动。

**实战意义**

监控方法：关注 Google 官方公告 + SEMrush Sensor 或 Mozcast 追踪 SERP 波动；核心更新后流量下降的应对：对照 Google 的《Core Update Quality Questions》自查文章列表；核心更新恢复通常需要等待下一次核心更新（3-6 个月）才会生效。

<a id="term-3-37"></a>

### Manual Action / 手动惩罚

**定义**

Google 人工审核员（Human Reviewer）对违反 Google Webmaster Guidelines 的网站手动施加的排名惩罚，与算法惩罚不同，需要提交「Reconsideration Request」（重新审核申请）才能解除。

**实战意义**

在 Google Search Console \> Manual Actions 检查是否存在；常见原因：购买/出售链接、隐藏文字关键词堆砌、Cloaking（针对爬虫展示不同内容）、垃圾结构化数据；发现 Manual Action 后：修复违规行为、提交 Disavow 文件（如有有害链接）、提交重新审核申请并详细说明已采取的整改措施。

<a id="term-3-38"></a>

### Cloaking / 隐藏作弊

**定义**

向搜索引擎爬虫展示与真实用户看到的不同内容的黑帽 SEO 技术，是 Google Webmaster Guidelines 明确禁止的严重违规行为，可导致永久驱逐出 Google 索引。

**实战意义**

独立站严禁：①针对 Googlebot User-Agent 展示特殊优化版本 ②动态渲染用于展示爬虫专属关键词填充内容；合法的动态渲染必须展示与用户一致的内容；若使用 A/B 测试工具，确保爬虫看到的是原始版本（非测试变体）。

<a id="term-3-39"></a>

### Thin Content / 稀薄内容

**定义**

对用户几乎没有实质价值的低质量页面，包括字数极少的页面、自动生成的页面、大量复制的页面或 Doorway Pages（门页）。

**实战意义**

Shopify 独立站常见 Thin Content 来源：①空或内容稀少的 Collection 页面 ②缺乏描述的产品页 ③纯参数过滤页（URL 参数生成的变体页面）；解决方案：为每个 Collection 页面添加 200-500 字的分类介绍文案、优化产品描述、合并或 noindex 稀薄页面。

<a id="term-3-40"></a>

### Duplicate Content / 重复内容

**定义**

同一网站或跨网站间存在相同或高度相似内容的情况，会导致 Google 困惑于哪个版本是权威来源，可能导致相互竞争的页面都无法获得最优排名。

**实战意义**

内部重复：使用 canonical 标签解决（如 Shopify 产品 URL 路径重复）；外部重复（抄袭）：使用 Copyscape 检测；生产者权威解决：通过 First-Mover 发布原创内容并在 GSC 提交建立来源 - 即便被复制，Google 通常会将原创者作为权威来源。

[知识库首页](../README.md) · [术语索引](glossary-index.md) · [上一章](02-keyword-sop.md) · [下一章](04-ecommerce-cro.md)
