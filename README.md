# 精选 AI Skills 专属合集

> Agent Skills 是"装上就能用的 AI 能力包"：文案、视频、营销、去 AI 味，一行命令装好，AI 直接按里面的方法干活。
> 这个库只收**真实可用、有 SKILL.md 干货**的 skills，每条都提炼到"不点源链接也能拿走 80%"，并给出一行安装命令——**帮你便捷用上，是这个库唯一的价值**。
>
> A curated collection of genuinely usable AI agent skills: video production, copywriting, marketing growth, de-AI and prompt craft. Each entry is distilled so you get 80% of the value without leaving this page, with a one-line install command.

## 目录

- [先读（S 级）](#先读s-级)
- [视频生产](#视频生产)
- [文案钩子](#文案钩子)
- [营销增长](#营销增长)
- [去 AI 味](#去-ai-味)
- [提示词](#提示词)

---

## 先读（S 级）

> 电商视觉是离钱最近的 skill，先看这一个。

### ecommerce-visual-copywriting-skill
- **一句话**：把商品资料变成"设计师 / 生图模型能直接开工"的电商视觉全案：转化策略、主图/详情页分镜、图内文案、生图 Prompt、证据与合规审查一条龙——适合做电商、带货、给商家做视觉的人。
- **核心用法**：
  1. 先路由任务、收最小输入：产品是什么、卖哪（淘宝 / Amazon / TikTok Shop…）、卖给谁、核心卖点和证据；不影响定位的信息直接假设并标注，最多追问 3 个关键问题
  2. 建证据账本：所有数据/资质/功效宣称先登记来源——包装写明的才叫"已确认"，缺证据的降级为中性表达或占位符，绝不编造销量、证书、功效
  3. 定成交驱动力：从视觉质感 / 痛点效率 / 理性参数 / 信任证据 / 情绪身份里选 1 主 +1 辅，把卖点做成 Feature→Advantage→Benefit→Evidence，只留 Top 3 购买理由
  4. 锁 Campaign Style Lock：产品身份（包装/Logo/颜色/结构不变项）、构图、色彩、光影、字体、背景先锁定，再画 Storyboard（主图角色：KV/利益/证据/对比/场景/规格；详情页顺序：承接首屏 → 利益 → 机制 → 场景 → 证据 → 对比 → FAQ）
  5. 输出执行稿 + 过五维质量门：每张图给视觉任务、画面描述、图内文案、设计说明、生图 Prompt、Negative Prompt、证据备注；证据合规/转化逻辑/视觉层级/一致性/可执行性任一 Fail 就返修
- **安装**：`npx skills add feichanggege/ecommerce-visual-copywriting-skill`（README 官方安装方式）
- **怎么用它搞钱**：接电商视觉策划单：商家给产品资料，你交付"分镜 + 文案 + 生图 Prompt"全套，设计师或 AI 直接出图；跨境卖家做 Amazon / TikTok Shop 本地化 Listing，一套流程多国复用。
- **来源**：[feichanggege/ecommerce-visual-copywriting-skill](https://github.com/feichanggege/ecommerce-visual-copywriting-skill) · ⭐876

---

## 视频生产

> 用 skill 把视频生成变成可重复的工程：Vidu 文生视频 / 对口型 / 拼片、mediagen 多模型统一 CLI、HeyGen 照片转数字人、Anthropic 官方的视觉设计与生成艺术。

### vidu Text-to-Video
- **一句话**：调 Vidu 官方 API 做文生视频 / 图生视频 / 首尾帧视频，适合想用代码批量产 AI 短片的人
- **核心用法**：
  1. 先定可复用元素：`vidu-cli element create --name "角色A" --image /path/a.png` 把主角做成可复用素材（返回 id/version），解决多镜人物崩坏
  2. 提交异步任务：`vidu-cli task submit --type character2video --prompt "[@角色A] walks into office" --material "角色A:ID:VERSION" --duration 5`，拿到 task_id
  3. 轮询下载：`vidu-cli task get <task_id> -o <dir>`，成功即落盘
  4. 所有命令走 argv 数组直接传参，不包 shell 字符串；图片任务 `--duration 0`，视频任务查 `references/parameters.md` 定时长
- **安装**：`npx skills add shengshu-ai/vidu-skills && npm install -g vidu-cli@latest`（需 VIDU_TOKEN）
- **怎么用它搞钱**：批量产竖屏短剧发抖音 / 视频号跑流量分成；或接"AI 短片代做"单，一条片子=多次 API 调用，成本透明好报价
- **来源**：[shengshu-ai/vidu-skills](https://github.com/shengshu-ai/vidu-skills) · ⭐76

### vidu Lip Sync
- **一句话**：让视频里的人物对上指定音频的口型，适合做数字人口播 / 翻译视频的人
- **核心用法**：
  1. 准备好人物视频 + 目标音频（TTS 生成或真人录音）
  2. 走 `vidu-cli task lip-sync` 提交对口型任务（与 submit 同一套异步模型：拿 task_id 再 poll）
  3. 音频建议先用 `vidu-cli task tts --prompt "旁白文本" --voice-id "Chinese (Mandarin)_Gentleman"` 生成，注意参数是 `--voice-id` 不是 `--voice`
  4. 下载后检查口型同步率，不行换模型版本重提（查 `references/parameters.md` 的模型矩阵）
- **安装**：`npx skills add shengshu-ai/vidu-skills && npm install -g vidu-cli@latest`（需 VIDU_TOKEN）
- **怎么用它搞钱**：做"真人不出镜"的口播账号；或接多语言视频翻译单（配目标语言音频 + lip-sync，比重新拍便宜 90%）
- **来源**：[shengshu-ai/vidu-skills](https://github.com/shengshu-ai/vidu-skills) · ⭐76

### vidu Video Compose
- **一句话**：把多个视频片段按时间线拼成成片（含转场 / 字幕），适合做 AI 短剧最后组装的人
- **核心用法**：
  1. 先读 `references/compose.md`——拼片 timeline JSON 有固定结构，不能凭感觉写
  2. 用 `vidu-cli task compose --timeline <json>` 提交，json 里排好每个片段的顺序、时长、转场
  3. 同一套异步流程：task_id → `vidu-cli task get` 轮询 → 下载；字幕会以 subtitle JSON 一起下
  4. 报错只看 JSON 字段原文，不要猜原因；`references/errors_and_retry.md` 有重试策略
- **安装**：`npx skills add shengshu-ai/vidu-skills && npm install -g vidu-cli@latest`（需 VIDU_TOKEN）
- **怎么用它搞钱**：AI 短剧"最后一公里"自动化——前面分镜都用 AI 生成，最后用 compose 拼成片，接单时按集收费
- **来源**：[shengshu-ai/vidu-skills](https://github.com/shengshu-ai/vidu-skills) · ⭐76

### mediagen
- **一句话**：一条 CLI 调 Gemini / OpenAI / Kie 生图生视频，适合不想记各家 API 的人
- **核心用法**：
  1. 永远 `npx -y mediagen image "<prompt>" --json`（或 video），`--json` 让输出只有干净 JSON，不用解析废话
  2. 生图前先跑 `npx -y mediagen models --json` 看哪个 provider 可用、有 key，按用户优先级选，别猜
  3. 提示词自己写全六要素：主体 / 构图 / 光线 / 镜头或媒介 / 材质 / 氛围——模型不会替你脑补，缺什么它就瞎填什么
  4. 视频只说"一个连续镜头 + 运镜 + 画面里什么在变"；图里要精确文字先预警（各家文字渲染都不稳）
- **安装**：`npx -y mediagen`（免安装，有 key 就能用；`mediagen init` 需用户自己在终端跑）
- **怎么用它搞钱**：给客户批量做 logo / 海报 / 产品图，一条命令一个交付；或打包成"AI 配图服务"按张收费
- **来源**：[Cripacx/mediagen](https://github.com/Cripacx/mediagen) · ⭐52

### lipnardo photo-to-avatar
- **一句话**：一张照片变成会说话的数字人（HeyGen），适合做真人不出镜的口播 / 批量个性化视频的人
- **核心用法**：
  1. `/lipnardo avatar create <photo>` 走完整照片转数字人管线，先 `validate_setup.py` 确认 HEYGEN_API_KEY 有效
  2. 生成前必估成本：`credit_check.py estimate --feature video_agent --duration 60`，给用户看报价再动手
  3. 简单需求用 agent 模式（AI 自动选形象写脚本），多场景用 studio 模式（JSON 配 avatar/voice/background），批量用 batch/template 模式（CSV 灌数据）
  4. 视频翻译直接 `/lipnardo translate <video_id> <lang>` 带对口型；下载要在链接过期前 `/lipnardo download`
- **安装**：`git clone https://github.com/AgriciDaniel/lipnardo.git && bash install.sh`（需 HeyGen API key）
- **怎么用它搞钱**：批量做"千人千面"的营销视频（CSV 一灌，每行一个客户名）；或做 AI 主播带货账号，7×24 不停播
- **来源**：[AgriciDaniel/lipnardo](https://github.com/AgriciDaniel/lipnardo) · ⭐22

### canvas-design
- **一句话**：Anthropic 官方 skill，让 AI 先写"设计宣言"再出手绘海报级视觉稿，适合要出封面 / 概念图的人
- **核心用法**：
  1. 两步走：先写 DESIGN PHILOSOPHY（给流派起名如 "Brutalist Joy"，4-6 段讲清空间 / 色彩 / 尺度 / 构图），再按宣言画 canvas
  2. 宣言里反复强调"大师级工艺感"——这是 skill 的核心 trick，不写 AI 就出敷衍稿
  3. 埋一条"隐性概念线"（如爵士乐手引用名曲）：懂的人会心一笑，不懂的也觉得是好设计
  4. 最后只做"精修"不做"加法"：第二遍问"怎么让现有构图更像艺术品"，而不是加元素
- **安装**：`npx skills add anthropics/skills`
- **怎么用它搞钱**：接品牌概念海报 / 播客封面 / 课程封面单；宣言+成图双交付显得专业，溢价空间大
- **来源**：[anthropics/skills](https://github.com/anthropics/skills) · ⭐180612

### algorithmic-art
- **一句话**：Anthropic 官方 skill，用 p5.js 写生成艺术（flow field / 粒子系统），适合要做动态视觉 / NFT 风格藏品的人
- **核心用法**：
  1. 同样两步：先写 ALGORITHMIC PHILOSOPHY（计算美学宣言），再按宣言写 p5.js 算法
  2. 必须用种子随机数（`randomSeed(seed); noiseSeed(seed)`），同一种子永远出同一张图——可复现才能卖
  3. 先读 `templates/viewer.html` 当起点，只替换算法和参数控件，Anthropic 的 UI 骨架不动
  4. 输出单文件 HTML（含 p5.js CDN + 参数滑杆 + 种子导航），浏览器打开即玩，方便交付和传播
- **安装**：`npx skills add anthropics/skills`
- **怎么用它搞钱**：卖"一键生成 100 张不重样"的头像 / 壁纸包；或给品牌做可交互的生成艺术装置
- **来源**：[anthropics/skills](https://github.com/anthropics/skills) · ⭐180612

---

### Hyperframes 整库总览

- **一句话**：用 HTML 写代码直接渲染成视频的框架（HeyGen 官方出品），23 个 skills 覆盖全流程，适合想"代码驱动做视频"的人
- **核心用法**：
  1. 本质：composition 就是一份 HTML，DOM 用 `data-*` 属性声明时间轴，动画 runtime 可 seek，媒体播发框架接管
  2. 标准循环：`init` 脚手架 → 查 primitive（`catalog --query` 找现成效果，有就别手写）→ 写 composition → `lint` 快检 → `check` 终检 → `preview` 预览 → 用户点头后 `render`
  3. 先搜后写：要缩放/运镜/剪辑/音频，先读对应的 domain skill（keyframes/audio/media-use），不要自己造轮子
  4. 质量门：`--quality draft` 迭代、`looks` 首版、`delivery` 交付；渲染只在用户批准后
  5. 需要 Node.js 22+ 和 FFmpeg；先 `npx hyperframes usage --json` 查额度
- **安装**：`claude plugin marketplace add heygen-com/hyperframes && claude plugin install hyperframes@hyperframes`
- **怎么用它搞钱**：接"代码视频"定制单（数据可视化/产品演示/动态海报）：改数字就重新渲染，边际成本为零；Fiverr 上 AI 视频 $100/单档，代码驱动是降本利器
- **来源**：[heygen-com/hyperframes](https://github.com/heygen-com/hyperframes) · ⭐61,304

### hyperframes-cli（开发循环）

- **一句话**：Hyperframes 的命令行工作流 skill，10 步标准循环，适合天天用 Hyperframes 做片子的人
- **核心用法**：
  1. `init` 建项目 → `catalog --query` 找现成动效 primitive → `add` 装上，手写是最后选项
  2. 查时间轴用 `timeline --json`（别去读 index.html 和子文件，token 省一半）
  3. 边写边 `lint`，结构大改后必 lint；终检用 `check`（自带 lint + 浏览器审计）
  4. 预览 `preview --background`，确认 200 才给用户看；渲染分三档：draft/looks/delivery
  5. 改崩了用 `history undo` 回滚，别手改回去；每轮开头 `history begin`、结尾 `history end`
  6. 验片：`ffprobe` 对时长/fps，读 render summary 第二行看 GPU 模式（Linux 上 screenshot+software gpu 是慢路径）
- **安装**：随 Hyperframes 插件安装，`npx hyperframes` 即用
- **怎么用它搞钱**：把"10 步循环"变成你的 SOP，接单时"当天出片"就是竞争力；改片用 history 回滚，不返工就是利润
- **来源**：[heygen-com/hyperframes](https://github.com/heygen-com/hyperframes) · ⭐61,304

### hyperframes-core（技术契约）

- **一句话**：Hyperframes 的 HTML composition 技术规范，适合要自己写/改 composition 的人
- **核心用法**：
  1. 两种根形态别混用：standalone（顶层 index.html，根 div 直接放 body）vs 子 composition（包 `<template>`，style/script 放 template 里面）
  2. 时间轴三件套：`data-track-index` 管轨道、`class="clip"` 声明片段、子 composition 用 `data-composition-src` 挂载
  3. 确定性规则：时间轴必须可 seek，布局/文字适配有硬性约束，lint 会拦
  4. 按需读 references：最小骨架看 minimal-composition、选单体还是模块化看 composition-patterns、剪辑手法抄 creator-editing-recipes
- **安装**：随 Hyperframes 插件安装
- **怎么用它搞钱**：吃透这套契约才能做"模板化"：一套 composition 换数据批量出片（百条矩阵号/多语言版本），这是代码视频真正的规模红利
- **来源**：[heygen-com/hyperframes](https://github.com/heygen-com/hyperframes) · ⭐61,304

### general-video（通用视频工作流）

- **一句话**：Hyperframes 的通用视频生产流程 skill（非幻灯片/非 Remotion 移植走这个），适合从零做一条片子的人
- **核心用法**：
  1. 先过"源适配器"：音频/图片/字体/调色走 `/media-use` 解析复用，别自己用 CSS 瞎调；Figma 链接先跑 `/figma` 拿资产和 token
  2. 有 BRIEF.md 就按 brief 的 workflow 执行，不问问题；没有就跑 intent interview 再路由
  3. 脚手架：`npx hyperframes init "videos/<项目>" --non-interactive --example=blank --skill=general-video`
  4. 素材要先 `npx hyperframes auth status` 确认登录，离线走可用 provider，卡住就如实报 blocker
- **安装**：随 Hyperframes 插件安装
- **怎么用它搞钱**：这是"接单-生产"的主流程跑道；Figma 到成片一条龙，设计师客户给稿你直接出片
- **来源**：[heygen-com/hyperframes](https://github.com/heygen-com/hyperframes) · ⭐61,304

### Remotion 最佳实践

- **一句话**：Remotion 官方的 skills 路由器（创建/排版/地图/多媒体/交互），适合用 React 写代码做视频的人
- **核心用法**：
  1. 这是个路由器：做新视频/新项目读 remotion-create、写 React 排版读 remotion-markup、地图动画读 remotion-maps、剪视频/取元数据读 remotion-multimedia
  2. 原则：用户说"做个视频"先开 Studio 预览，别直接渲染；保持预览开着让用户边看边指挥
  3. 用户在外部改了代码别覆盖，先确认
  4. 和 Hyperframes 的关系：Remotion 是 React 范式，Hyperframes 是 HTML 范式；已有 Remotion 工程可走 remotion-to-hyperframes 迁移
- **安装**：`npx skills add remotion-dev/remotion`（官方仓库 skills 目录）
- **怎么用它搞钱**：React 开发者做视频零学习成本；接数据视频/播客剪辑单，代码复用率高
- **来源**：[remotion-dev/remotion](https://github.com/remotion-dev/remotion) · skills 目录

### qiaomu-anything-to-notebooklm（内容转播客）

- **一句话**：微信文章 / 网页 / YouTube / 小宇宙 / B站 / PDF 一键喂给 NotebookLM，批量生成播客 / PPT / 思维导图，适合做知识二创和内容矩阵的人
- **核心用法**：
  1. 克隆到 `~/.claude/skills/` 跑 `./install.sh` 一键装依赖（自带 `check_env.py` 做 13 项环境检查）
  2. 按提示配 weixin-read-mcp（微信文章走 MCP 抓取，绕反爬），再 `notebooklm login` 认证
  3. 自然语言触发：`/qiaomu-anything-to-notebooklm [微信文章链接]`，或"把这个 B 站视频转写传到 NotebookLM"
  4. 付费墙自动绕过（300+ 站点：UA 伪装 → AMP → archive.today）；小宇宙 / 喜马拉雅 / B 站转写走 Get笔记 API（带时间戳）
- **安装**：`cd ~/.claude/skills/ && git clone https://github.com/joeseesun/qiaomu-anything-to-notebooklm && cd qiaomu-anything-to-notebooklm && ./install.sh`（需 `notebooklm login`）
- **怎么用它搞钱**：把爆款文章 / 播客变成自己的播客节目或 PPT 课程素材，一源多用；或接"知识库搭建 / 播客代运营"单
- **来源**：[joeseesun/qiaomu-anything-to-notebooklm](https://github.com/joeseesun/qiaomu-anything-to-notebooklm) · ⭐6229

### product-launch-video（产品发布视频）

- **一句话**：产品官网 URL / 文案 brief 一键变成产品发布或推广视频（SaaS 宣传、功能揭示、产品演示），适合要给自己或客户产品做推广片的人
- **核心用法**：
  1. 入口固定 `/hyperframes`：意图路由把"给产品做推广片"分流到这个 skill，意图不明就先走主路由
  2. 动工前先 `npx hyperframes skills update product-launch-video` 保鲜，再 `npx hyperframes capture "<URL>" -o ./capture` 抓官网素材，站内文案直接当配音底稿
  3. 8 步编排：setup（锁 BRIEF.md）→ capture → design system → storyboard/script → audio → visual → frames（每帧一个 sub-agent 并行）→ render 成片
  4. 三处用户门卡：brief（Step 0）、故事板（Step 3）、成片（Step 6）；音频/BGM 先 `npx hyperframes auth status` 看走 HeyGen 还是本地引擎
- **安装**：随 Hyperframes 插件安装，`npx hyperframes` 即用；`npx hyperframes skills update product-launch-video` 保鲜
- **怎么用它搞钱**：给 SaaS / 独立开发者做产品发布视频代工——他们缺这个；自己产品上线时一条推广片全渠道分发
- **来源**：[heygen-com/hyperframes](https://github.com/heygen-com/hyperframes) · ⭐61891

### mortiflix-oss（本地动态设计工作室）

- **一句话**：本地 motion design 工作室：brief→脚本→风格帧→转场→动态分镜→配音→音乐→成片，每阶段人工审核，适合要做高质量动态设计/品牌片但不想外包的人
- **核心用法**：
  1. `/mortiflix` 进向导：`mortiflix init` 建工作室，`setup status` 按部就班装转场/配音/音乐/素材/发布/3D 六件套（每件可跳过）
  2. 铁律：每道门卡都要主人亲口确认——approve、改意见、重开都等你说，绝不自动过；Key 永远自己在终端输，不进聊天
  3. 后端三选一：claude-code（走你的 Claude 订阅）、anthropic-api（按 token 计费）、demo（占位试玩）
  4. 管线按阶段推进：brief→脚本→风格帧→animatic→音乐→终剪；每阶段 `review` 看产物再决定下一步
- **安装**：`git clone https://github.com/GTKottman/mortiflix-oss.git ~/mortiflix-oss && cd ~/mortiflix-oss && npm install && npm link`（需 Node 20+、ffmpeg）
- **怎么用它搞钱**：接"品牌动态设计/宣传片"单——本地管线成本透明、每阶段可审，交付显得专业；或做模板化短视频代工
- **来源**：[GTKottman/mortiflix-oss](https://github.com/GTKottman/mortiflix-oss) · ⭐593

### baoyu-design（Claude Design 本地运行）

- **一句话**：把 Anthropic 官方 Claude Design（claude.ai/design 背后的设计引擎）打包成可本地运行的 Agent Skill，在 Cursor/Claude Code/Codex 里直接出 UI 高保真稿、交互原型、落地页、PPT——不用官网、不用另开订阅，@dotey 实测推荐
- **核心用法**：
  1. 一条命令装进你的 agent：`npx skills add jimliu/baoyu-design -g`（自动识别 agent，装到 .claude/skills 或 .agents/skills；也可用 --agent 指定）
  2. 直接说"设计/原型/画个落地页/做个 PPT"即触发——harness-agnostic，Cursor/Claude Code/Codex 及 70+ agents 通用
  3. 按完整设计方法论干活：需求→设计系统/品牌 token→线框→高保真→交互原型，全是自包含 HTML，留在你自己仓库里
  4. 交付物广：UI mockup、交互原型、落地页、仪表盘、移动端界面、幻灯片（deck 结构的可导出 PPTX）、HTML 邮件、海报
  5. 最佳搭配 Claude Opus 4.8；中英双语 README+CHANGELOG，四端同 prompt 截图对比可查
- **安装**：`npx skills add jimliu/baoyu-design -g`（官方安装方式）
- **怎么用它搞钱**：接 UI/落地页/原型设计单（"AI 出稿+人工精修"交付，快 10 倍）；给客户做产品演示原型/融资 Deck，按项目收费
- **来源**：[jimliu/baoyu-design](https://github.com/jimliu/baoyu-design) · ⭐4344

### video-transcribe（视频转文字）
- **一句话**：视频/音频转文字 + 核心提炼：YouTube / B站 / 本地文件，有字幕直接抓、没字幕用 Gemini 2.5 Flash AI 听写，还能输出结构化要点——适合做二创、知识蒸馏、口播文案复用的人。
- **核心用法**：
  1. 字幕优先策略：URL 先抓现有字幕（快、0 API 消耗），无字幕才下音频走转录
  2. 本地文件：`python3 Tools/transcribe.py --input "video.mp4"`，ffmpeg 自动提音频；URL 直接传 YouTube / B站链接
  3. 引擎二选一：默认 Gemini 2.5 Flash（有标点、需免费申请的 API Key）；离线用 `--engine mlx`（mlx-whisper，仅 Apple Silicon）
  4. 两条工作流：`Workflows/Transcribe.md` 只转录，`Workflows/Extract.md` 提炼要点，两者都要就先转再提炼
  5. 输出默认存 `~/Downloads/transcript_时间戳.txt`，`--output` 可指定路径
- **安装**：`git clone https://github.com/Jane-xiaoer/claude-skill-video-transcribe`，按 README 装依赖（`pip3 install google-genai` + `brew install yt-dlp ffmpeg` + Gemini 免费 API Key）
- **怎么用它搞钱**：把爆款视频批量转文字攒"拆解库"，二创脚本 / 课程笔记 / 公众号文章一鱼多吃；或接"视频内容整理 / 会议纪要"单，按分钟收费。
- **来源**：[Jane-xiaoer/claude-skill-video-transcribe](https://github.com/Jane-xiaoer/claude-skill-video-transcribe) · ⭐231

### faceless-explainer（无脸讲解视频）
- **一句话**：任意文本（文章 / 笔记 / 话题 / brief）变成无脸讲解视频：视觉逐场景现发明（字体排印 / 抽象图形 / 图表 / 数据可视化），适合做知识号 / 讲解号、真人不出镜的人。
- **核心用法**：
  1. 入口固定 `/hyperframes`：意图路由把"讲清楚一个话题但无素材"分流到这个 skill
  2. 动工前先 `npx hyperframes skills update faceless-explainer` 保鲜；BGM / 音效先走 `/media-use` 解析
  3. 流程：定设计系统 → 规划教学故事线 → 逐帧建 composition（Step 5 每帧一个 sub-agent 并行）→ render 成片
  4. 三处用户门卡：brief（Step 0）、故事板（Step 3）、成片（Step 6）；无采集步骤，所有视觉都是下游发明的
- **安装**：随 Hyperframes 插件安装，`npx hyperframes` 即用
- **怎么用它搞钱**：批量做"无脸知识视频"矩阵号（读书 / 科普 / 财经解读），一条文本 = 一条视频；或接"文章转视频"代工单。
- **来源**：[heygen-com/hyperframes](https://github.com/heygen-com/hyperframes) · ⭐64,282

### talking-head-recut（口播/访谈包装）
- **一句话**：给现成的口播 / 访谈 / 播客视频加定时设计的图形卡片（动态标题 / 下三分之一 / 数据标注 / 金句卡 / 画中画），按转录文本同步；原片不动，适合做访谈节目 / 播客切片 / 课程包装的人。
- **核心用法**：
  1. 准备好本地口播 / 访谈视频（完整播放，16:9 / 9:16 / 4:5 任选画幅）
  2. Agent 按转录内容设计卡片（时机 + 内容），每张卡的 HTML 直接在对话里写好
  3. 组装成单个 composition HTML，用 `hyperframes` 渲染成 MP4；纯字幕需求走 embedded-captions
  4. 无固定卡片模板——卡片从转录实际内容里长出来，按需出现
- **安装**：随 Hyperframes 插件安装；动工前 `npx hyperframes skills update talking-head-recut` 保鲜
- **怎么用它搞钱**：接"访谈 / 播客视频包装"单（别人给 raw 片子，你交付带图形包装的成片）；自己做口播号时，卡片包装是完播率杠杆。
- **来源**：[heygen-com/hyperframes](https://github.com/heygen-com/hyperframes) · ⭐64,282

### motion-graphics（动态图形短片）
- **一句话**：10 秒内的设计驱动动态图形：动态字体 / 数字滚动 / 图表打击 / Logo 定格 / 动态地图 / 推文卡片动画，motion 本身就是信息——适合做品牌片头 / 数据可视化 / 营销动效的人。
- **核心用法**：
  1. 适用场景：10 秒内、无旁白、无真人主体——长片 / 旁白 / 多场景走 general-video
  2. 先 `npx hyperframes skills update motion-graphics` 保鲜；Logo / 素材来自 Figma 先跑 `/figma`（带 SVG 清洗和品牌 token 绑定）
  3. 选类型：kinetic typography / stat count-up / chart hit / logo sting / lower-third / animated map / tweet card / 网页 UI 动画
  4. 输出 MP4 或透明通道 overlay（可叠到别的视频上用）
- **安装**：随 Hyperframes 插件安装，`npx hyperframes` 即用
- **怎么用它搞钱**：接"品牌动态设计 / 数据可视化"单（一条 10 秒动效抵十页 PPT）；或打包"社交媒体动效模板"按套卖。
- **来源**：[heygen-com/hyperframes](https://github.com/heygen-com/hyperframes) · ⭐64,282

### music-to-video（音乐卡点视频）
- **一句话**：一首音乐变成卡点同步的视频：歌词视频 / 幻灯片 / 动感宣传片，音乐定全部节奏；零素材也能出完整片子，适合做音乐号 / 卡点视频 / 歌词视频的人。
- **核心用法**：
  1. 输入一首音乐（音频文件 / 从视频提取 / 按情绪 brief 生成），用户图片 / 视频可选——全部按同一 beat 网格剪辑
  2. 流程：Step 0 落 `hyperframes.json` + `assets/bgm.mp3` → Step 1 音频分析出 `audiomap.json` → Step 2/3 排 STORYBOARD.md → Step 4 每帧一个 sub-agent 并行建 composition → Step 5 组装 → Step 6 渲染
  3. 两处门卡：Step 3 计划确认、Step 6 渲染确认；无旁白无网站采集，字体和模板是下限
- **安装**：随 Hyperframes 插件安装；`npx hyperframes skills update music-to-video` 保鲜
- **怎么用它搞钱**：批量做卡点 / 歌词视频矩阵号；接"音乐人宣传片 / 品牌 BGM 视频"单，beat 网格是专业卖点。
- **来源**：[heygen-com/hyperframes](https://github.com/heygen-com/hyperframes) · ⭐64,282

### embedded-captions（特效字幕）
- **一句话**：给口播视频加字幕：默认"安静字幕轨 + 高潮处嵌入式大字"，另有纯电影感嵌入和 35 套主题风格（含中文"炸 / 特效 / 酷炫字幕"）；转录和人物抠像全本地跑，适合做口播号 / 知识视频的人。
- **核心用法**：
  1. 先选视觉身份：CATALOG.md 里 35 套风格按"视觉身份"选，不按后端引擎选；默认 Standard（字幕轨 + 高潮嵌入），要纯电影感选 Cinematic
  2. 工作流全本地：转录 + 人物抠像都在本地跑；多镜头素材先分段再套字幕
  3. Theme 模式是完整主题宪法：正文字体范式 × 高潮大字 × 前景特效 × 底板反应，从 themes 注册表组合
  4. 这是字幕不是包装——要图形卡片叠加走 talking-head-recut
- **安装**：随 Hyperframes 插件安装；`npx hyperframes skills update embedded-captions` 保鲜
- **怎么用它搞钱**：接"口播视频字幕包装"单（特效字幕是中文口播号标配）；或做"字幕风格包"卖给 MCN / 代运营团队。
- **来源**：[heygen-com/hyperframes](https://github.com/heygen-com/hyperframes) · ⭐64,282

### stickman-video-director（火柴人动画视频）
- **一句话**：文案 / 话题变成火柴人线条动画讲解视频（默认 60 秒，10 秒倍数可调），4 套视觉风格（含治愈故事风），走 Gemini Omni Flash 分段生成 prompt 包——适合做职场 / 情感解说类短视频、成本趋近于 0 的人。
- **核心用法**：
  1. 准备源材料 + 定三要素：画幅（16:9 / 9:16）、时长（10 秒倍数，默认 60s）、视觉风格（4 套：经典极简 / 现代 Zeke / 史前手绘 / 治愈故事风）
  2. 先读 `references/storyboard-template.md` + `style-catalog.md` + `voice-continuity.md`，按 5 阶段高完播情绪叙事弧结构化
  3. 输出导演提案确认后，生成 N 个独立 10 秒分镜 prompt（N=时长/10），走 Gemini Omni Flash 逐段生成
  4. 配剪映热门解说音色 + 口播文案即成片
- **安装**：`git clone https://github.com/kaomei/stickman-video-director`（`skills/directing-stickman-videos` 为 skill 本体）
- **怎么用它搞钱**：批量做火柴人解说矩阵号（职场 / 情感 / 故事赛道），"妥妥的爆款预定，成本趋近于 0"；或接"文案转火柴人视频"代工单。
- **来源**：[kaomei/stickman-video-director](https://github.com/kaomei/stickman-video-director) · ⭐2124（@CrazyKaomei 推荐帖 21K 浏览）

### youtube-clipper（长视频切短视频）
- **一句话**：YouTube 长视频智能剪辑：下载 + AI 生成精细章节 → 你选片段 → 自动剪辑 + 中英双语字幕烧录 + 总结文案，适合做二创切片、搬运本地化的人。
- **核心用法**：
  1. 环境检测：`yt-dlp` + FFmpeg（含 libass，字幕烧录必需）+ `pysrt`
  2. 下载视频和字幕，AI 分析生成几分钟粒度的精细章节
  3. 人工选片段 → 自动剪辑、字幕翻译成中英双语并烧录进视频
  4. 附带生成总结文案（可直接当发布文案）
- **安装**：`npx skills add https://github.com/op7418/Youtube-clipper-skill`（官方安装方式）
- **怎么用它搞钱**：把英文长视频批量切成中文双语短视频发抖音 / B站，做"海外精选"类账号；或接"长视频切片"代工单。
- **来源**：[op7418/Youtube-clipper-skill](https://github.com/op7418/Youtube-clipper-skill) · ⭐2240

### dexhunter/seedance2-skill（Seedance 2.0 提示词）
- **一句话**：字节官方手册整理的 Seedance 2.0 视频提示词 skill（中英双版）：@ 引用语法、运镜词表、12 类场景写法，适合用即梦 Seedance 批量产视频的人
- **核心用法**：
  1. `npx skills add dexhunter/seedance2-skill`，中英 SKILL.md 各一份（`zh/SKILL.md` 中文版）
  2. 先看输入约束：图最多 9 张、视频最多 3 个素材，超了直接报错——先数素材再写提示词
  3. 用 @ 引用语法指定首帧图 / 运镜参考视频；12 类场景（人物一致性 / 视频延长 / 音乐卡点 / 一镜到底 / 电商展示 / 短剧）照写法套
  4. 6 个现成模板直接改：产品广告、短剧、舞蹈、风光卡点、仙侠、科普动画
- **安装**：`npx skills add dexhunter/seedance2-skill`
- **怎么用它搞钱**：接 AI 短剧 / 广告片代做单：Seedance 2.0 是当前中文社区最热的视频模型，模板化接单报价透明；或批量产竖屏带货视频跑流量分成
- **来源**：[dexhunter/seedance2-skill](https://github.com/dexhunter/seedance2-skill) · ⭐4322

### Vincentwei1021/video-shotcraft（镜头配方卡）
- **一句话**：150+ 镜头配方卡 + 200+ 动效在线预览，每个动效对应确定性 Remotion 组件——让 AI 做视频先给"菜谱"再动手，适合不想让 AI 凭空写 CSS 动画的人
- **核心用法**：
  1. `npx skills add Vincentwei1021/video-shotcraft`，先从在线 Gallery 挑动效再开工
  2. 直接点名配方（如 deck-deal-flyin、spotlight-hero-card），AI 调用对应的 Remotion 组件，不自己造轮子
  3. 交付后用类剪映 Motion Workbench 微调（镜头 / 转场 / 字幕 / 音效轨道），可导出剪映草稿（macOS 剪映专业版 11.2 已验证）
  4. 中文 README_CN.md 齐全；Ink Press 样片（36 秒、10 镜头、钉好时间点的音效）可照着拆
- **安装**：`npx skills add Vincentwei1021/video-shotcraft`
- **怎么用它搞钱**：接"代码视频"定制单（产品演示 / 动态海报 / 数据可视化）：配方卡保证效果下限，改数字重渲染边际成本为零
- **来源**：[Vincentwei1021/video-shotcraft](https://github.com/Vincentwei1021/video-shotcraft) · ⭐12170

### liyupi/ai-promo-video-maker（产品宣传片）
- **一句话**：一句话描述产品，AI 自动调研、两轮提问、画样帧、配音配乐、剪辑校验，最后交付 4K 商业宣传片——适合要给产品做宣传片但没预算请外包的人
- **核心用法**：
  1. `npx skills add liyupi/ai-promo-video-maker -g`（需 Node 18+、Python 3.9+、ffmpeg）
  2. 一句话告诉 AI 宣传什么，它先调研产品，再两轮提问（画幅时长 / 目标受众 / 风格方向；开场 / 配乐 / 截图来源），每问带推荐选项和理由
  3. 动手前 AI 画 3-4 张样帧供挑选——风格由你定，不是预设模板
  4. 有 ElevenLabs key 就配 AI 旁白配乐，否则用免费可商用曲库 + 大字幕
- **安装**：`npx skills add liyupi/ai-promo-video-maker -g`
- **怎么用它搞钱**：接产品宣传片单：外包一支几千上万，你用 AI 一天交片，成本主要是时间；或给自己的产品批量做宣传片跑获客
- **来源**：[liyupi/ai-promo-video-maker](https://github.com/liyupi/ai-promo-video-maker) · ⭐304

## 文案钩子（6 个）

### price-anchor
- **一句话**：中高客单价产品被嫌贵、促销缺"超值感"时，用"高价锚点先行"让价格显得划算的定价文案法；源自关健明《爆款文案》第三章。
- **核心用法**：
  1. 确认价格痛点：摸清消费者心理价格阈值与当前定价的差距（如"定价 1999，心理预期 1000"）。
  2. 找锚点：三种来源——同品类高端竞品、同品类组合购买总成本、跨行业高价参照（跨界用"共同概念"连接，如用"保养"连接汽车保养和体检套餐）；锚点必须真实可信，不能凭空捏造。
  3. 写锚点文案：格式"通常[场景]需要[锚点价格]，而[产品]只要[实际价格]"——先抛高价锚点建立"贵"的心理预期，再揭示实际价格制造惊喜感。
  4. 标题版"惊喜优惠标题"：标题 14 字内完成价格冲击，格式"价值[锚点价格]的[产品描述]，现在只要[实际价格]"。
  5. 最终检查：锚点真实、对比逻辑合理、实际价格确有划算感、读起来自然。
- **安装**：git clone https://github.com/kangarooking/viral-copywriting-skill.git
- **怎么用它搞钱**：做带货文案代写——给客户写短视频/朋友圈文案时套用"惊喜优惠标题"公式，让中高客单价产品在标题里直接制造价格冲击，按篇收费卖差异化。
- **来源**：[kangarooking/viral-copywriting-skill](https://github.com/kangarooking/viral-copywriting-skill) · ⭐67


### fear-appeal
- **一句话**：痛点产品（电动牙刷、保险、净水器）读者不够重视时，用"痛苦场景 + 严重后果"两步法激发紧迫购买欲；源自《爆款文案》第一章。
- **核心用法**：
  1. 识别并验证真实痛点：痛点来自用户反馈或调研，能让读者"对号入座"，不靠办公室想象。
  2. 写具体的痛苦场景：有时间、有地点、有动作、有身体感受——说"牙龈发炎出血，阵阵作痛"，不说"牙齿不好"；越具体越能代入。
  3. 推导严重后果：回答"不解决会怎样"，强度要达到"难以承受"——经济损失、身体痛苦、社交损失、时间损失都行，用具体数字和画面增强冲击（如"每天洗碗 30 分钟，四十年≈两年半洗碗刑期"）。
  4. 自然过渡产品：恐惧达到高点时递出产品作"解药"，像及时雨一样自然，不许断裂。
  5. 边界：享乐型产品（零食、旅游、娱乐）与品牌形象广告不用；不给读者贴负面标签（"懒癌""拖延症晚期"会激起逆反），用自测打钩让读者自己下结论。
- **安装**：git clone https://github.com/kangarooking/viral-copywriting-skill.git
- **怎么用它搞钱**：接牙科/体检/课程机构的公众号推文单——用恐惧诉求结构替换干巴巴的功能介绍，接单话术直接用书中案例（"电动牙刷 24 小时卖光 1 万支"）。
- **来源**：[kangarooking/viral-copywriting-skill](https://github.com/kangarooking/viral-copywriting-skill) · ⭐67


### friend-chat-title
- **一句话**：朋友圈、私域、个人 IP 需要"像朋友聊天一样"的亲切标题时用的三步改写法；源自《爆款文案》第四章。
- **核心用法**：
  1. 先用书面语写正式标题当底稿，确保信息传达准确。
  2. 加入"你"：标题出现"你"字，或明确"跟你说话"的语气（"教你""给你""帮你"）。
  3. 逐词检查，把书面语换成口语词：凡"不会在聊天里这样说"的词都换掉（购买→买，优惠→便宜）。
  4. 加入惊叹词：至少一个强烈情绪词（太/最/真/竟然/居然/绝对/一定要）。
  5. 朗读检验：读起来像"发给朋友的一条微信消息"才算通过，像广告语就回炉继续改。
- **安装**：git clone https://github.com/kangarooking/viral-copywriting-skill.git
- **怎么用它搞钱**：做微商/私域代运营的起手服务——把客户原有硬广标题批量改成好友对话体，案例句式"赚了 1173 万元，愿意手把手教你"，按账号收月费。
- **来源**：[kangarooking/viral-copywriting-skill](https://github.com/kangarooking/viral-copywriting-skill) · ⭐67


### ai-copywriter
- **一句话**：英文双技能——写转化文案时先"以读者为先"摸准需求再动笔，写完再过一遍 33 项 AI 味检查；适合做跨境文案和英文内容的人。
- **核心用法**：
  1. 动笔前先答两个问题：读者收到这行字时正在经历什么情绪（疲惫筛邮件？付款失败焦虑？被十个工具伤过的怀疑？）；能不能用"厨房餐桌上的话"把产品讲清楚——讲不清就不配开卖。
  2. 需求不全就一次问清三件事：精准画像（角色+场景+试过什么+深夜会搜什么词）、品类归属（读者会把它误当成什么）、真实故事（发生了什么、付出什么代价、改变了什么，带真实数字和对话）。
  3. 草稿→审核→终稿循环：用三个问题自检——"读者看一遍能复述出承诺吗？""单独立在广告牌上能不能活？""这行字是迎合了读者的情绪还是自说自话？"
  4. 人性化审核：33 项 AI 特征（浮夸比喻、营销腔、-ing 式浅层分析、模糊归因、破折号滥用、三连句、AI 高频词、被动语态、否定平行句、填充词）；铁律——不编造产品事实，文案里的数字必须来自用户或来源。
  5. 误杀保护：看的是"特征簇"不是孤立证据（单个破折号、一处 however 不算病）；有作者真实样稿时，样稿的风格优先级高于去 AI 规则。
- **安装**：npx skills add mikiarlo3/ai-copywriter --global
- **怎么用它搞钱**：接英文跨境文案单——给独立站/SaaS 写落地页和 LinkedIn 帖，卖点是"读起来像真人写的转化文案"，可打包卖"文案 + 去 AI 味审核"两道工序。
- **来源**：[mikiarlo3/ai-copywriter](https://github.com/mikiarlo3/ai-copywriter) · ⭐1207


### tt-hook-scripter
- **一句话**：给 TikTok/短视频写前 1–3 秒钩子——口播台词 + 屏幕文案 + 首帧画面三层一起定，目标就是让人刷不走；钩子是全平台最大留存杠杆。
- **核心用法**：
  1. 收齐输入：视频创意、受众、视频要兑现的"一个承诺"、目标（完播/收藏/评论/分享）。
  2. 按目标选公式（共 10 个）：完播选 T1 冷开场结果 / T2 打破预期 / T8 故事高潮切入；收藏选 T3 具体数字揭秘 / T7 清单承诺 / T9 教程冷启动；评论选 T4 开放式提问 / T6 无修饰的反常识断言；分享选 T5 高共鸣点名 / T10 蹭趋势改编。
  3. 写三层：口播台词、屏幕文案（3–7 词）、首帧画面（结果/张力/打断）——口播和屏幕文案必须用不同的词（静音刷屏场景）；首帧直接放结果或冲突，不许"大家好"/logo 动画；一个具体数字胜过任何形容词。
  4. 写 loop-close（结尾如何自然重播一次）+ 过一遍 tt-humanizer 去脚本味。
  5. 硬规避："嘿 guys/这期视频"开场、屏幕文案抄口播、承诺视频里没展示的东西、为节奏硬插"结果是？"式揭秘。
- **安装**：npx skills add sergebulaev/tiktok-skills
- **怎么用它搞钱**：做短视频代运营的"钩子外包"——按条收钩子脚本费，或给带货账号做钩子诊断（"你的视频死在第一秒"），诊断话术直接来自 skill 的触发场景。
- **来源**：[sergebulaev/tiktok-skills](https://github.com/sergebulaev/tiktok-skills) · ⭐69

### dontbesilent2025/dbskill（选题与 Hook 诊断）
- **一句话**：从 16152 条公开推文筛选的 4176 个知识原子，35 个中文 skills 覆盖商业判断 / 选题 Hook / 内容创作——适合做中文内容不知写什么、标题没点击的人
- **核心用法**：
  1. 装好后在 Agent 里调 `/dbs` 或具体 skill（如 `/dbs-diagnosis`）
  2. 选题诊断：把选题丢给它，用知识原子库诊断 Hook 强度（小红书标题 / 封面文字 / 短视频前 3 秒开头）
  3. 新版逻辑：先用你给的材料推进，只在缺"会改变结论的事实"时才提问，不用来回确认
  4. 按任务查 skill：商业诊断 / 对标分析 / 执行力诊断 / 概念拆解 / 好问题，各有专精
- **安装**：`npx skills add dontbesilent2025/dbskill`
- **怎么用它搞钱**：注意 CC BY-NC 4.0 仅限非商业用途——自用做账号选题诊断提效，等于请了个免费选题军师；拿它接单前先确认授权
- **来源**：[dontbesilent2025/dbskill](https://github.com/dontbesilent2025/dbskill) · ⭐10708

---

## 营销增长

> 39 个 skill：X/Twitter 增长、广告拆解、文案生产、YouTube 研究、TikTok 热点、小红书运营、SEO/GEO 获客、封面配图全覆盖。每个条目不点源链接也能拿走 80% 价值。

### twitter-algorithm-optimizer
- **一句话**：基于 X 开源算法的四层模型（Real-graph / SimClusters / TwHIN / Tweepcred）诊断并改写推文，让每条推都吃到推荐流量——适合做 X 账号增长的人。
- **核心用法**：
  1. 先提炼推文的核心信息：这条推到底在说什么、说给谁听、想触发哪种互动（回复/转发/收藏）
  2. 对号入座算法模型：粉丝会不会互动（Real-graph）、能不能打中某个紧密社区（SimClusters）、是否符合你的人设定位（TwHIN）、会不会损伤账号信誉（Tweepcred）
  3. 按想要的信号改写：要回复就加提问或安全争议点，要转发就给可分享的干货/代表性观点，要收藏就给教程清单/数据
  4. 排雷：删掉"求转发"式 engagement bait、炎性语言、偏离人设的内容，避免被举报/拉黑降权
  5. 发布后第一小时内尽快回复评论——算法奖励活跃对话
- **安装**：`git clone https://github.com/ComposioHQ/awesome-claude-skills.git`（awesome 合集，按需取单个 skill 目录即可）
- **怎么用它搞钱**：把"凭感觉发帖"变成"按算法改帖"的 X 代运营服务，按月收费；或每天把热点帖套算法模板改写成自己风格，蹭流量涨粉再变现。
- **来源**：[ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills) · ⭐76904

### competitive-ads-extractor
- **一句话**：从 Facebook / LinkedIn 广告库批量扒下竞品在跑的广告，拆解它们在打什么痛点、用什么文案套路——适合跑广告、做投放代运营的人。
- **核心用法**：
  1. 指定竞品 + 平台（"把 Notion 在 Facebook 广告库的在跑广告全扒下来"），批量抓取广告截图存档
  2. 拆解每条广告的主题、痛点、文案公式、CTA 和受众定位
  3. 找重复出现的模式：哪些痛点被反复打、哪种视觉（前后对比/产品实拍/社会证明）出现频率最高
  4. 找竞品没覆盖的角度，做差异化定位
  5. 按"痛点 → 模式 → 缺口"输出分析报告，并给出自己广告的测试建议
- **安装**：`git clone https://github.com/ComposioHQ/awesome-claude-skills.git`（awesome 合集，按需取单个 skill 目录即可）
- **怎么用它搞钱**：接广告代投单时先出一份《竞品广告拆解报告》当签单钩子；跨境卖家上新前先抄验证过的痛点和文案公式，少交测试学费。
- **来源**：[ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills) · ⭐76904

### content-research-writer
- **一句话**：一个陪你写长文的 AI 搭档：搭大纲、找资料加引用、改开头钩子、逐段给反馈——适合写公众号 / 博客 / Newsletter 的人。
- **核心用法**：
  1. 先定大纲：讲清主题、目标读者、写作目标（教育/说服/娱乐），并标出每节需要补的研究点
  2. 分块研究补证据：每条数据、引用都带来源出处，单独建 research.md 存资料
  3. 开头钩子单独打磨：一次给 3 个版本（金句 / 故事 / 惊人数据），逐条解释为什么有效
  4. 写完一节交一节：按清晰度、逻辑流、证据、文风四项逐段反馈，而不是一次性改全文
  5. 全稿终审过发布清单：所有断言有来源、引用格式统一、有行动号召，再发布
- **安装**：`git clone https://github.com/ComposioHQ/awesome-claude-skills.git`（awesome 合集，按需取单个 skill 目录即可）
- **怎么用它搞钱**：接"深度长文代写"单（行业白皮书、创始人 IP 稿），有引用、有结构就能收高客单价；长文拆成推文串/短视频脚本，一鱼多吃。
- **来源**：[ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills) · ⭐76904

### x-twitter-growth
- **一句话**：X 账号增长全套引擎：审主页 → 扒竞品 → 定内容 → 算法规则 → 增长日历，还附带 5 个 Python 脚本——适合从 0 起号或想系统化做 X 的人。
- **核心用法**：
  1. 先审主页：跑 `profile_auditor.py`，按 bio 清单（第一句讲清价值主张、细分具体、有社会证明、不放标签）+ 置顶帖 + 近 30 条内容配比（回复占比 >30%）打分
  2. 竞品情报：用搜索找细分领域 5–10 个高互动账号，扒它们的钩子模式、内容主题、发帖时间
  3. 按增长影响力排序做内容：长推串（涨粉最强：7 词内钩子、每条独立成段、结尾 CTA）> 原子推文（<200 字、链接放评论区）> 引用推（加数据或反方观点，绝不只说"说得好"）> 回复（找 2–10 倍于自己体量的账号抢首评）
  4. 避算法红线：正文不放链接（放首条评论）、不超过 2 个标签、发帖 30 分钟内不编辑、发完别立刻离线
  5. 按体量定节奏：<1K 粉每天 2–3 推 + 每周 1–2 串 + 每天 10–20 条回复；跑 `growth_tracker.py` 跟踪 30 天数据
- **安装**：`git clone https://github.com/alirezarezvani/claude-skills.git`（README 官方方式：clone 后按所用平台跑对应安装脚本）
- **怎么用它搞钱**：X 代运营标准化 SOP：先出《账号诊断报告》签单，再按周交付内容日历 + 数据复盘；帮跨境/出海品牌起英文 X 账号。
- **来源**：[alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) · ⭐28040

### youtube-full
- **一句话**：YouTube 的"读"能力：取字幕、搜视频、看频道更新、扒播放列表——适合做选题研究、竞品监控、内容二创的人。
- **核心用法**：
  1. 先配好 `TRANSCRIPT_API_KEY`（transcriptapi.com 免费领 100 额度），或走开源备选（youtube-transcript-api / yt-dlp）
  2. 研究流：先 search 找相关视频 → 挑中意的取 transcript → 总结或摘金句
  3. 监控流：用免费的 channel/latest 接口定时看目标频道上新 → 有新视频再取字幕抓信号（新品发布、新话题）
  4. 语料库流：playlist/videos 批量拿播放列表所有视频 ID → 批量取字幕攒成可检索文档集
  5. 省额度纪律：先用免费接口确认有更新再花额度；不经用户确认不批量转录整个频道
- **安装**：`git clone https://github.com/alirezarezvani/claude-skills.git`（README 官方方式：clone 后按所用平台跑对应安装脚本）
- **怎么用它搞钱**：监控 20 个对标 YouTube 频道，一出爆款视频 10 分钟内产出中文拆解/二创脚本，抢时效流量；把英文教程字幕批量转成中文付费专栏/课程素材。
- **来源**：[alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) · ⭐28040

### copywriting
- **一句话**：转化文案写作：从首页到落地页到定价页，按"清晰 > 机智、利益 > 功能、具体 > 模糊"写出让人行动的页面文案——适合自己卖产品或接建站文案单的人。
- **核心用法**：
  1. 动笔前先收齐四要素：页面唯一目标（一个行动）、受众（痛点 + 他们的原话）、产品差异点 + 证据、流量来源
  2. 先写首屏：标题写 5–10 个候选，用 `headline_scorer.py` 按 6 维度打分（低于 60 不用）+ 副标题加具体性 + CTA 用"动词 + 所得"（"开始免费试用"而非"注册"）
  3. 按固定结构铺页面：社会证明 → 痛点 → 方案/利益 → 怎么做 → 打消疑虑 → 最终 CTA
  4. 文风过五关：用简单词、给具体数字、主动语态、不堆副词、不编数据
  5. 交付带注释 + 备选：每个关键文案说明为什么这么写，标题和 CTA 至少给 2–3 个选项
- **安装**：`git clone https://github.com/alirezarezvani/claude-skills.git`（README 官方方式：clone 后按所用平台跑对应安装脚本）
- **怎么用它搞钱**：接独立站/落地页文案单，"标题打分 + 结构 + 注释"的交付物显得专业、好收高价；给自己的产品页重写一遍，直接提转化率。
- **来源**：[alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) · ⭐28040

### ad-creative
- **一句话**：付费广告的文案生产线：按漏斗阶段选框架、批量生成多平台合规广告文案、拿数据迭代——适合跑 Google / Meta / TikTok 广告的人。
- **核心用法**：
  1. 先定三要素：卖什么（核心价值一句话）、卖给谁（职位/痛点/异议）、哪个平台 + 漏斗阶段（认知/考虑/决策）
  2. 按阶段选框架：认知期讲痛点（问题 → 放大 → 暗示方案）、考虑期讲机制（方案 → 原理 → 证据）、决策期讲证明（证言 → 风险消除 → 真实紧迫感）
  3. 批量生成：每个标题公式（利益优先/好奇/社会证明/痛点煽动）出 5–10 条，写正文时守各平台字数（Google RSA 标题 30 字符×15、Meta 正文 125 字符等）
  4. 拿数据迭代：先诊断赢家的钩子类型 → 提炼模式（具体数字 vs 模糊、客户口吻 vs 品牌口吻）→ 赢的主题出 3–5 个变体 → 再开 1 个全新角度测试
  5. 发布前过质检清单：字数合规、无全大写/多感叹号、无"点击这里"、无无法佐证的"第一/最佳"
- **安装**：`git clone https://github.com/alirezarezvani/claude-skills.git`（README 官方方式：clone 后按所用平台跑对应安装脚本）
- **怎么用它搞钱**：广告代投的核心交付：每周产出几十条合规测试素材 + 迭代报告，按效果收费；帮电商卖家把一条爆款文案扩展成"角度 × 平台"矩阵批量测。
- **来源**：[alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) · ⭐28040

### tt-trend-mapper
- **一句话**：TikTok 蹭热点的"该不该蹭"决策器：先做四项适配检查，通过了才给你编" recognizable 的梗 + 你 niche 的转折"——适合做 TikTok / 抖音、不想蹭得尴尬的人。
- **核心用法**：
  1. 先跑四项适配检查：跟你的 niche 有没有天然关联？还处在爆发前 1–3 天吗？有没有必须致敬的原生结构（卡点/包袱位置）？你能不能给出只有你 niche 才讲得出的转折？有一项不过就建议跳过
  2. 判断热点生命周期：萌芽期（立刻上）→ 爆发期（有强转折才上）→ 饱和期（跳过或反着玩）→ 过气（用了显得晚）
  3. 拆原生结构：说出这个梗的 beat、笑点、预期剪辑点
  4. 编转折钩子："这个梗的预期开头，但讲你们行业的事"——第一秒必须让人认出是这个梗，转折必须让你的受众觉得"这是讲给我们的"
  5. 口播稿交给 tt-humanizer 过一遍口语化，再交给 tt-caption-writer 写配文
- **安装**：`npx skills add sergebulaev/tiktok-skills`（README 官方安装方式）
- **怎么用它搞钱**：给品牌/商家做 TikTok 代运营时，每天筛 3 个热点只推 1 个"适配 + 有转折"的蹭法，避免翻车；把"热点日历 + 转折脚本"做成按周交付的服务。
- **来源**：[sergebulaev/tiktok-skills](https://github.com/sergebulaev/tiktok-skills) · ⭐69

### oh-story-claudecode（网文工具箱）
- **一句话**：网文写作工具箱（14 个 skills）：长篇 / 短篇的扫榜 → 拆文 → 规划 → 写作 → 审稿 → 封面全流程，扫起点 / 番茄 / 晋江 / 七猫榜单找风口——适合写网文变现的人。
- **核心用法**：
  1. 主入口 `/story` 自动路由：`/story-long-scan` 扫榜（看什么火）→ `/story-long-analyze` 拆文（黄金三章 / 灵感库）
  2. `/story-long-write` 规划长篇结构 / 细纲 / 连载；`/story-short-write` 写短篇（盐言 / 万字）
  3. `/story-review` 审稿、`/story-cover` 做封面、`/story-import` 导入
  4. `/story dashboard` 开本地工作台，管作者习惯与连载进度
- **安装**：`git clone https://github.com/zenstory-ai/oh-story-claudecode` 后按 README 安装（Claude Code / Codex / OpenCode / OpenClaw 均支持）
- **怎么用它搞钱**：网文是最成熟的 AI 变现赛道之一：扫榜找风口 → 拆文学生产 → 多平台投稿，工具箱把"试错成本"压到最低。
- **来源**：[zenstory-ai/oh-story-claudecode](https://github.com/zenstory-ai/oh-story-claudecode) · ⭐7605

### khazix-writer（卡兹克公众号长文）
- **一句话**：数字生命卡兹克的公众号长文写作 skill：以"有见识的普通人在认真聊一件打动他的事"为底色，素材（PDF / brief / 新闻链接 / 语音转文字）→ 长文——适合写公众号深度长文的人。
- **核心用法**：
  1. 丢素材（PDF / brief / 新闻链接 / 语音转文字）说"帮我写篇文章"即触发；不用于短内容（小红书 / 推特 / 朋友圈）
  2. 按卡兹克价值观写：永远对世界保持好奇、讲人话有活人感
  3. 同仓库另有 aihot（热点引擎）/ hv-analysis 等 skill，按需取用（`khazix-writer` 为写作本体）
  4. 适用：公众号文章、写稿子、续写扩写、按固定风格出稿
- **安装**：`git clone https://github.com/KKKKhazix/khazix-skills`（取 `khazix-writer` 目录；或按 README 用 `<skill-name>` 路径安装）
- **怎么用它搞钱**：接"公众号深度稿代写"单（风格化长文比通用 AI 稿溢价高）；自己做 IP 时，固定风格 = 固定读者预期。
- **来源**：[KKKKhazix/khazix-skills](https://github.com/KKKKhazix/khazix-skills) · ⭐21427

### notebooklm-skill（NotebookLM 研究转内容）
- **一句话**：把 Google NotebookLM 变成研究后端：URL / 文本 / 本地文件建笔记本 → 带引用提问 → 深网研究 → 一键生成文章 / 播客 / 视频 / 幻灯片 / 思维导图，适合写深度文 / 行研、做知识付费的人。
- **核心用法**：
  1. `notebooklm-auth setup` 登录（走浏览器 session + 非官方 web API，配额 / 稳定性不保证）
  2. 建笔记本：URL / 文本 / 本地文件 / RSS 都行；带引用问答 + 深网研究，结果可追溯到来源
  3. 一键生成：文章 / 播客音频 / 视频 / 幻灯片 / 学习指南 / 测验 / 思维导图 / 信息图 / 数据表
  4. 与库内 qiaomu-anything-to-notebooklm 互补：那个是"内容→多形态"，这个是"研究→内容"
- **安装**：`git clone https://github.com/claude-world/notebooklm-skill && ./install.sh`（13 个 MCP tools 可选接入）
- **怎么用它搞钱**：接"行研 / 深度内容代写"单（带引用的研究报告溢价高）；把公开资料变成自己的课程 / 播客 / 专栏，一源多吃。
- **来源**：[claude-world/notebooklm-skill](https://github.com/claude-world/notebooklm-skill) · ⭐471

---

### marketingskills 整库总览

- **一句话**：约 50 个营销 skills 的军火库（文案/广告/邮件/定价/转化率/获客），给做产品、做增长、接营销单的人一次装全
- **核心用法**：
  1. 一行装全库：`npx skills add coreyhaines31/marketingskills`，也可以只装单个 skill
  2. 按任务调 skill：写落地页调 copywriting、投广告调 ad-creative、做邮件调 emails、定价格调 pricing、提转化调 cro
  3. 每个 skill 开头先读"上下文清单"再动手（产品/受众/目标），不做无米之炊
  4. skills 之间互相引用（如 copywriting 写完调 copy-editing 逐行改），形成流水线
- **安装**：`npx skills add coreyhaines31/marketingskills`
- **怎么用它搞钱**：接"增长顾问"单：用这套 skills 给客户做落地页+广告+邮件全案；或自己做产品时，营销环节全部 AI 化，一个人跑完获客闭环
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐54,281

### copywriting（转化文案）

- **一句话**：写高转化营销文案的专家 skill（落地页/定价页/首页），适合卖产品、卖服务、做落地页的人
- **核心用法**：
  1. 动笔前先收四类上下文：页面目的（唯一行动是什么）、受众（痛点/顾虑/原话）、产品（差异化/证据）、流量来源
  2. 原则：清晰压倒 clever（清晰定位带来 +81% 转化）、利益压倒功能、具体压倒模糊（"每周报告从 4 小时压到 15 分钟"）、一屏只讲一个论点
  3. 写完过"去 AI 味"质检：禁"不是 X 而是 Y"翻案句、禁三段否定排比、禁"in today's fast-paced world"式 stock 开头、短文案不用破折号
  4. 缺证据就标 `[NEED: ...]`，绝不编造数据和 testimonials
- **安装**：`npx skills add coreyhaines31/marketingskills --skill copywriting`
- **怎么用它搞钱**：接落地页文案单；自己卖课/卖服务时，销售页转化率直接挂钩收入
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐54,281

### ad-creative（广告创意量产）

- **一句话**：批量生成/迭代付费广告创意（标题/描述/正文），适合投 Meta/Google/TikTok 广告的人
- **核心用法**：
  1. 四种模式：从零生成、用历史投放数据迭代、按获胜主题扩展、按平台规格校验
  2. 动手前收五类信息：平台与版位、产品与卖点、受众与认知阶段、历史数据（CTR/ROAS 哪条赢）、品牌与合规红线
  3. 核心循环：拉数据 → 找获胜模式 → 按获胜主题生成新变体 → 探新角度 → 校验规格 → 交付
  4. 覆盖 UGC/绿幕/口播/信息流等多格式，文案同样过"去 AI 味"质检
- **安装**：`npx skills add coreyhaines31/marketingskills --skill ad-creative`
- **怎么用它搞钱**：接广告代投/素材单：别人一条条写，你一次出几十条变体做 A/B 测试；自己带货时素材迭代速度就是 ROAS
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐54,281

### lead-magnets（获客钩子）

- **一句话**：设计"拿邮箱换资料"的获客钩子（电子书/清单/模板/课程），适合做私域、做 newsletter、卖课的人
- **核心用法**：
  1. 原则：只解决一个具体痛点（"怎么写出有回复的冷邮件" > "营销指南"）；钩子匹配购买阶段（认知期给教育、决策期给实施帮助）
  2. 先盘点：现有内容资产（博客/指南/数据）、内部用的模板工具、能包装的专业经验
  3. 选形态：清单/模板/速查表转化最高，别一上来就写电子书
  4. 钩子要自然导向产品试用，写完调 copywriting 写落地页、调 emails 写捕获后的培育序列
- **安装**：`npx skills add coreyhaines31/marketingskills --skill lead-magnets`
- **怎么用它搞钱**：帮客户搭"钩子→邮箱→培育→成交"漏斗收服务费；自己做号时这是涨粉最稳的路径之一
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐54,281

### pricing（定价策略）

- **一句话**：定产品价格/分档的 skill（SaaS/电商/服务都适用），适合定价拍脑袋、总被客户嫌贵的人
- **核心用法**：
  1. 三轴定价：分档含什么（Packaging）、按什么收费（用户数/用量/一口价）、收多少（Price Point）
  2. 价值定价：价格定在"次优替代品"和"客户感知价值"之间；成本只是底线不是依据；不对标竞品价格（那是抄它的战略）
  3. 核心洞察：多数"能不能便宜点"本质是"分子不够大/分母不够小"，先调价值再调价格
  4. 新品定价先定"能学到东西的价格"，跑数据再调
- **安装**：`npx skills add coreyhaines31/marketingskills --skill pricing`
- **怎么用它搞钱**：给 SaaS/知识付费做定价咨询；自己产品定价从"成本加成"换成"价值定价"，利润率直接上一个台阶
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐54,281

### offers（offer 设计）

- **一句话**：设计让人无法拒绝的 offer（服务/课程/教练/信息产品/高客单），适合卖高价但转化不行的人
- **核心用法**：
  1. 核心哲学：offer 本体比页面重要——弱 offer 配好文案慢慢爬，强 offer 配平庸文案立刻转化；多数"文案不行"本质是"offer 不行"
  2. 价值公式（Hormozi）：价值 =（梦想结果 × 感知达成概率）/（时间延迟 × 付出成本）；调四个杠杆：放大梦想、加证据与保证提概率、加速首胜、降低付出
  3. 适用：服务/课程/教练/信息产品/5K 美金以上高客单；自助 SaaS 分档订阅以 pricing 为主
  4. 设计完调 copywriting 写销售页、调 pricing 定档
- **安装**：`npx skills add coreyhaines31/marketingskills --skill offers`
- **怎么用它搞钱**：帮知识付费/教练做 offer 重构收咨询费；自己卖课时 offer 改好，转化率翻倍比投流便宜得多
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐54,281

### cro（转化率优化）

- **一句话**：按影响力排序诊断落地页的 skill，适合有流量没转化的页面
- **核心用法**：
  1. 先定三要素：页面类型、唯一转化目标、流量来源（不同来源预期不同）
  2. 按影响力顺序查：价值主张 5 秒能否看懂 → 标题是否讲清核心价值 → 是否客户语言 → 行动路径 friction
  3. 强标题公式：结果导向（"得到 X 而不用忍受 Y"）、具体数字、社交证明（"10,000+ 团队在用"）
  4. 表单 abandonment、A/B 测试想法有专门的 references 可调
- **安装**：`npx skills add coreyhaines31/marketingskills --skill cro`
- **怎么用它搞钱**：接"落地页诊断"单，按页收费；自己投流时，转化率提 1 个点等于获客成本降一截
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐54,281

### cold-email（冷邮件）

- **一句话**：写高回复率冷邮件的 skill，适合做 BD、找客户、谈合作的人
- **核心用法**：
  1. 动笔前收五样：写给谁（职位/公司/为什么是他）、要什么（回复/会议/介绍）、价值点、证据、研究信号（融资/招聘/动态）
  2. 语气像同行不像销售：多用"you"，少用"I/we"；每句必须推动回复，否则删
  3. 个性化必须连着痛点（删掉开头个性化整封还通顺 = 个性化失败）
  4. 一个低 friction 的 CTA（"值得聊聊？"），不要一上来就约会议
- **安装**：`npx skills add coreyhaines31/marketingskills --skill cold-email`
- **怎么用它搞钱**：帮 B2B/出海客户做冷启动获客；自己找商单、谈分销时，回复率就是 pipeline
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐54,281

### emails（邮件序列）

- **一句话**：搭邮件培育序列的 skill（欢迎/培育/唤醒/ onboarding），适合有名单但不会养的人
- **核心用法**：
  1. 先定序列类型（欢迎/培育/唤醒/售后/销售），再定受众触发点和转化目标
  2. 原则：一封邮件只干一件事；按生命周期查缺补漏（onboarding/留存/账单/唤醒）
  3. 写单封邮件调 copy-guidelines（结构/语气/长度/个性化字段）
  4. 和 lead-magnets 联动：钩子捕获 → 欢迎序列 → 培育 → 成交
- **安装**：`npx skills add coreyhaines31/marketingskills --skill emails`
- **怎么用它搞钱**：帮客户搭"名单→培育→复购"邮件体系收服务费；自己做私域时，邮件是复购率最高的渠道之一
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐54,281

### marketing-skills（广告审计整库总览）

- **一句话**：49 个投放审计型 skills：Google / Meta / Reddit / LinkedIn 广告诊断、SEO、AI 可见度审计，适合接投放代运营或做独立站获客的人（与 marketingskills 的文案/转化线互补）
- **核心用法**：
  1. `skills/` 下 49 个独立 SKILL.md 按需触发，每个 skill 都列明交付物（先跑 AI Visibility Audit 定基线）
  2. `ai-visibility-audit`：自动生成 30–50 个品类问句面板，测 ChatGPT / Claude / Gemini / Perplexity 里品牌 vs 竞品被引用率，输出引用源地图和修补清单
  3. `wasted-spend-finder` / `meta-ads-audit`：抓烧钱广告组的具体问题（频次/出价/创意疲劳），按动作清单逐项修
  4. 要读实时账户数据时接免费 Ryze MCP：`claude mcp add ryze --transport http https://connector.get-ryze.ai/mcp`
- **安装**：`cd ~/.claude/skills/ && git clone https://github.com/irinabuht12-oss/marketing-skills`（按 `skills/` 目录名逐个启用）
- **怎么用它搞钱**：接"投放审计"单——一次审计输出可见度评分卡 + 竞品引用源地图 + 修补动作清单，按次收费；AI 可见度是 2026 年新蓝海，信息差大
- **来源**：[irinabuht12-oss/marketing-skills](https://github.com/irinabuht12-oss/marketing-skills) · ⭐4398

### xhs-account-teardown（小红书账号拆解）

- **一句话**：丢一个小红书账号链接，自动抓主页扒封面逐张识图，按六问框架输出账号拆解报告+9:16 长图，适合做小红书获客/对标拆解的人
- **核心用法**：
  1. `python3 scripts/fetch_profile.py "<账号链接>" -o <工作目录>` 抓主页：profile.json + notes_list.json + 每篇笔记封面图（匿名可抓，零登录零 Cookie）
  2. 用视觉能力逐张识图：封面模板（栏目期号/钩子句/点睛句）、品类、客单价、橱窗销量，登记进封面目录表
  3. 带 token 的笔记链接可深度拆解：`python3 scripts/fetch_note.py` 拿全文+全部图片；拿不到的数据必须标"未获取"，严禁编造
  4. 按六问框架出《账号拆解报告.md》：每板块一句"一句话公式"，结尾"能抄的/抄不了的/最大的坑"三段；默认再出一张可分享的 9:16 长图
- **安装**：`git clone https://github.com/chenjin-cmd/xhs-account-teardown`（需 python3 + curl；宿主要会执行 shell、读图、写文件）
- **怎么用它搞钱**：接"对标账号拆解"单——别人还在手动截图，你一条命令出报告+长图；或做自己小红书起号前的调研
- **来源**：[chenjin-cmd/xhs-account-teardown](https://github.com/chenjin-cmd/xhs-account-teardown) · ⭐66

### xhs-product-picker（小红书虚拟产品选品）

- **一句话**：输入你的职业/技能背景，输出完整虚拟产品方案：定位+指南目录+引流款/利润款/旗舰款矩阵+7 天行动计划，适合想在小红书卖虚拟产品的人
- **核心用法**：
  1. 把仓库完整文件夹装进 Agent 的 skills 目录（不要只拷 SKILL.md，案例摘要和配置指南是配套）
  2. 告诉它你的背景：职业、技能、能持续输出什么——它按背景定产品定位
  3. 拿到三层产品矩阵：引流款（低价拉人）/利润款（主力变现）/旗舰款（高客单），每款给标题和指南目录
  4. 按 7 天行动计划执行：内容选题→首篇笔记→引流钩子→成交路径，一步步来
- **安装**：下载仓库 ZIP 解压，把 `xhs-product-picker` 完整文件夹复制到 Agent 的 skills 目录（或用平台的 Skill 导入功能）
- **怎么用它搞钱**：虚拟产品是小红书最低成本变现——零库存、边际成本为零；用它把自己的经验打包成可卖的指南/模板/课
- **来源**：[chensongyue10-design/xhs-product-picker](https://github.com/chensongyue10-design/xhs-product-picker) · ⭐120

### qiaomu-seo（SEO 全流程审计）

- **一句话**：网站 SEO 全流程 skill：技术审计、关键词意图、AI 搜索可见度（ChatGPT/Perplexity/AI Overviews），适合做独立站/内容站获客的人
- **核心用法**：
  1. 先定工作模式：advisory（只出方案）/ page（单页深挖）/ incident（流量掉了查因）/ migration（改版保权）/ experiment（AB 测 SEO）
  2. 按模块路由：技术审计读 audit-playbook、关键词读 keyword-content、AI 搜索读 ai-search——一次只读相关的，不全量灌
  3. 证据铁律：每个结论标"直接观察/合理推断/缺少证据"，绝不编造搜索量排名流量；排名收录 AI 引用一律不承诺
  4. 实施只做最小安全改动：改前拍快照、改后验证、保留回滚信息
- **安装**：`npx skills add joeseesun/qiaomu-seo`（同作者的 qiaomu-anything-to-notebooklm 已入库，内容转播客+SEO 成套用）
- **怎么用它搞钱**：接独立站 SEO 审计单；AI 搜索可见度是 2026 新需求，帮客户在 ChatGPT/Perplexity 里被引用
- **来源**：[joeseesun/qiaomu-seo](https://github.com/joeseesun/qiaomu-seo) · ⭐446

### xyskill 整库总览（中文商业操盘 48 skills）

- **一句话**：48 个中文商业 skills：私域运营、成交诊断、选品诊断、长内容切片、爆款复刻、公众号排版，一句 `/xy` 点名即用，适合做私域/内容/小生意的人
- **核心用法**：
  1. `npx -y skills add xyaz1313/xyskill -g --all` 装完，`/xy 新手入门` 开场
  2. 直接说事不用记名：`/xy 客户嫌贵不回消息`——路由按意图分发（每个 skill 首行自报家门）
  3. 获客线：xy-clip（直播逐字稿切短视频方案，零字新增硬约束）/ xy-replica（爆款结构复刻）/ xy-idea-desk（想法变选题）
  4. 变现线：xy-private-ops（私域运营）/ xy-close（成交诊断）/ xy-selection（选品诊断）/ xy-fde（接单报价）/ xy-biz-scan（商业诊断）
- **安装**：`npx -y skills add xyaz1313/xyskill -g --all`（支持 Claude Code/Codex/豆包/WorkBuddy）
- **怎么用它搞钱**：把私域操盘经验变成可调用工具——帮客户做账号诊断/选品/成交，按次收费；底层有 2.8 万条知识原子+333 概念节点背书
- **来源**：[xyaz1313/xyskill](https://github.com/xyaz1313/xyskill) · ⭐79

### anatomy（概念可视化演示）

- **一句话**：把"讲清楚一个技术概念"变成"造一台会动的机器"：生成带四色等距渲染、可交互、可动效的精美 SVG/HTML 解释图（悬停拆解、实时读数、WebGL 特效），适合写技术文档、做课程、做产品落地页的人
- **核心用法**：
  1. 先定尺寸再动手：Figure（40–80 零件，一个机制）/ Hero（80–150 零件）/ Epic（整车整厂级，只给 Hero 方案不直接做）——命名尺寸再开工
  2. 真实第一：先收齐要解释对象的真实数值和行为（尺寸、阈值、曲线），所有读数、动效、标注都从同一个模型驱动，绝不编造
  3. 发明机器：选一台"机制与概念一一对应"的机器（仪表、绘图仪、试车台），一句话说清"什么在动、动代表什么"；自带 8 个完整示例，先翻最接近的再开工
  4. 按工作流建造：列零件清单（40 起）→ 布世界坐标与相机（默认方位 45°/仰角 30°）→ 几何一次成型 → 从后往前画（painter's order）→ 装卡片框（标题/交互提示/实时读数）→ 加缓动动效
  5. 像批评家一样验：headless Chrome 截图 + `node build.mjs --audit` 归零 + line check 归零 + 4× 放大看每个接缝，迭代到"一眼是真东西"
- **安装**：`npx skills add wheresryan22/anatomy -g -a claude-code`（官方安装方式；也支持 OpenCode/Codex）
- **怎么用它搞钱**：接"技术解释图"定制单（产品落地页/白皮书/课程的可交互演示图，一张图抵十页文档）；或做付费技术课程的配图演示，一套工作流复用
- **来源**：[wheresryan22/anatomy](https://github.com/wheresryan22/anatomy) · ⭐7762（2026-10-08 开源，5 天破 7000★，中英文社区反复推荐）

### xiaohongshu-ops-skill（小红书全链路运营）
- **一句话**：小红书全链路运营 skill：账号定位 → 选题研究 → 内容生产 → 发布执行 → 复盘修复，含 Viral Copy 链路（输爆款 URL 学封面 / 标题 / 正文结构）——适合想系统化做小红书获客的人。
- **核心用法**：
  1. 先定账号定位与内容方向，再跑选题产出 + 争议点挖掘
  2. 竞品 / 同类账号对标：扒爆款的封面 / 标题 / 正文结构
  3. Viral Copy 链路：输入爆款 URL，高贴合学习其结构并生成可发布近似结构笔记
  4. 发布后快速复盘：互动结构、评论回复、热点追踪
  5. 注意：默认走 OpenClaw 内置浏览器流程（profile="openclaw"），其他 agent 按 `references/xhs-runtime-rules.md` 配环境
- **安装**：`git clone https://github.com/Xiangyu-CAS/xiaohongshu-ops-skill`（含 knowledge-base + references + examples）
- **怎么用它搞钱**：接"小红书代运营"单：一套流程多账号复用；或自己起号做私域获客，选题 / 复盘环节标准化后边际成本极低。
- **来源**：[Xiangyu-CAS/xiaohongshu-ops-skill](https://github.com/Xiangyu-CAS/xiaohongshu-ops-skill) · ⭐2428

### guizang-social-card-skill（小红书图文/封面）
- **一句话**：文字秒变小红书竖版轮播图 + 公众号封面：28 套版式 / 10 套主题，直接转 PNG，还能做 Live Photo 动态卡片——适合做小红书图文号、公众号的人。
- **核心用法**：
  1. 输入文章 / 脚本 / 截图 / 产品笔记 / 字幕 / 照片，指定用途（小红书 3:4 轮播 / 公众号封面 / Live Photo）
  2. 按 28 套版式 × 10 套主题选风格（杂志风 / Swiss Style 可选）
  3. 输出封面 + 内容页成套卡片，直接转 PNG 发布；视频素材可做 Live Photo 拼图
  4. 产物放任务文件夹，不污染 skill 根目录
- **安装**：`git clone https://github.com/op7418/guizang-social-card-skill`
- **怎么用它搞钱**：接"小红书图文代做"单（封面 + 轮播图成套交付）；自己做图文号时，排版环节从 1 小时压到 5 分钟。
- **来源**：[op7418/guizang-social-card-skill](https://github.com/op7418/guizang-social-card-skill) · ⭐7540

### guizang-ppt-skill（杂志风演示稿）
- **一句话**：一句话生成杂志级排版的单文件 HTML 演示稿（横向翻页，含 WebGL 背景 / 演讲者视图 / 讲稿备注）：电子杂志 × 电子墨水 / 瑞士国际主义两套风格，适合做路演 / 方案 / 课程演示的人。
- **核心用法**：
  1. 一句话描述需求即生成，两种视觉基调二选一：风格 A 电子杂志 × 电子墨水（衬线 + 流体背景，人文 / 商业发布）、风格 B 瑞士国际主义（无衬线 + 网格点阵，信息驱动）
  2. 模板在 `assets/template.html`，主题色 / 布局查 `references/themes.md` + `references/layouts.md`
  3. 自带演讲者视图、观众屏同步、讲稿备注、章节幕封、数据大字报、图片网格
  4. 输出单 HTML 文件，手机 / 电脑直接打开演讲，不依赖 Office
- **安装**：`git clone https://github.com/op7418/guizang-ppt-skill`
- **怎么用它搞钱**：接"路演 PPT / 课程演示稿"单（杂志级排版是差异化卖点）；给自己的课程 / 方案做演示稿，交付质感直接拉高客单价。
- **来源**：[op7418/guizang-ppt-skill](https://github.com/op7418/guizang-ppt-skill) · ⭐28013

### wewrite（公众号全流程）
- **一句话**：公众号写作一条龙 skill 套件（10 个 skills）：选题 → 任务书 → 初稿 → 改写 → 审稿 → 发布 → 数据复盘，带风格人格与质量门，适合做公众号 / 内容 IP 的人。
- **核心用法**：
  1. `wewrite-topic` 定选题 → `wewrite-write` 出文章任务书（目标读者 / 核心判断 / 最强反方）+ 主张证据 + 初稿
  2. `wewrite-rewrite` 改写、`wewrite-review` 过审稿质量门（`artifacts.article` 审稿通过后才生成）
  3. `wewrite-style` 定风格人格（`style.yaml` + personas，只控制表达偏好不覆盖事实）
  4. `wewrite-publish` 发布、`wewrite-stats` 数据复盘、`wewrite-visual` 配图
  5. 全程 `wewrite run` 管理任务状态，CLI 驱动
- **安装**：`git clone https://github.com/imraywang/wewrite && ./install.sh`
- **怎么用它搞钱**：接"公众号代运营"单（选题到发布全流程标准化）；自己做 IP 时，一人即编辑部。
- **来源**：[imraywang/wewrite](https://github.com/imraywang/wewrite) · ⭐3464

### vivy-yi/xiaohongshu-skills（小红书 139 技能知识库）
- **一句话**：139 个小红书运营技能的知识库（内容创作 / 账号运营 / 数据分析 / 电商转化 / 平台规则 9 大类全覆盖），适合想系统做小红书起号、带货的人
- **核心用法**：
  1. `/plugin marketplace add vivy-yi/xiaohongshu-skills` 后 `/plugin install xiaohongshu-complete-skills@xiaohongshu-skills`，139 个技能一次装好
  2. 先定目标再进分类：起号走 01-内容创作 + 02-账号运营，带货走 04-电商转化（选品 / 种草 / 销售漏斗 17 个技能）
  3. 每个技能都是独立 SKILL.md：理论框架 + 操作指南 + 常见错误 + 真实案例，直接照着执行
  4. 放量阶段用 07-营销推广（KOL / 广告 / 活动 / 预算）+ 08-增长策略（算法 / 变现 / 长期战略）
- **安装**：`/plugin marketplace add vivy-yi/xiaohongshu-skills` 后 `/plugin install xiaohongshu-complete-skills@xiaohongshu-skills`
- **怎么用它搞钱**：接小红书代运营 / 起号单：139 个技能就是现成 SOP，定位→内容→转化全链路可交付；自己做带货号，选品 + 种草 + 漏斗一条龙跑通
- **来源**：[vivy-yi/xiaohongshu-skills](https://github.com/vivy-yi/xiaohongshu-skills) · ⭐492

### AgriciDaniel/claude-seo（全栈 SEO 审计系统）
- **一句话**：26 个子 skill + 19 个专家 agent 并行的全栈 SEO 系统（技术 SEO / 内容 E-E-A-T / Schema / GEO / 本地 / 电商 / 国际化），适合做独立站、内容站靠搜索获客的人
- **核心用法**：
  1. `/plugin marketplace add AgriciDaniel/claude-seo` 后 `/plugin install claude-seo@agricidaniel-claude-seo`（需 Claude Code 1.0.33+）
  2. `seo-audit` 起手跑全站体检，输出按优先级排序的行动清单（每条建议都可测试验证）
  3. 内容线：`seo-content-brief` 按 E-E-A-T 生成内容简报再写；结构化数据走 `seo-schema`
  4. AI 搜索流量用 `seo-geo`，电商站加 `seo-ecommerce`，多语言站加 `seo-hreflang`
- **安装**：`/plugin marketplace add AgriciDaniel/claude-seo` 后 `/plugin install claude-seo@agricidaniel-claude-seo`
- **怎么用它搞钱**：接 SEO 审计 / 代运营单：26 个子 skill 并行出报告，一次审计即交付物，按月收 retainer；自己做利基站，GEO + 传统 SEO 双吃搜索流量
- **来源**：[AgriciDaniel/claude-seo](https://github.com/AgriciDaniel/claude-seo) · ⭐19053

### zubair-trabzada/geo-seo-claude（GEO：AI 搜索优化）
- **一句话**：专攻 AI 搜索（ChatGPT / Claude / Perplexity / Gemini / Google AI Overviews）的 GEO 优化 skill，适合传统 SEO 流量被 AI 搜索分流的人
- **核心用法**：
  1. `curl -fsSL https://raw.githubusercontent.com/zubair-trabzada/geo-seo-claude/main/install.sh | bash` 一键安装
  2. `geo-audit` 先审站点在 AI 搜索里的可见度缺口
  3. `geo-citability` + `geo-llmstxt` 把内容改成 AI 愿意引用的格式（llms.txt、引用友好结构）
  4. `geo-brand-mentions` 做品牌提及——在 AI 搜索里品牌提及的相关性是外链的 3 倍
- **安装**：`curl -fsSL https://raw.githubusercontent.com/zubair-trabzada/geo-seo-claude/main/install.sh | bash`
- **怎么用它搞钱**：接"AI 搜索可见度优化"新品类单：传统 SEO 公司还没反应过来，GEO 是蓝海；给自己的产品做 GEO，被 ChatGPT / Perplexity 回答引用 = 免费精准流量
- **来源**：[zubair-trabzada/geo-seo-claude](https://github.com/zubair-trabzada/geo-seo-claude) · ⭐11067

### mvanhorn/last30days-skill（跨平台热源研究）
- **一句话**：AI agent 主导的跨平台热源搜索引擎（Reddit / X / YouTube / HN / Polymarket），按点赞和真金白银排序——不看编辑推荐、看市场投票，适合找选题、追热点的人
- **核心用法**：
  1. `npx skills add mvanhorn/last30days-skill -g`（或 `/plugin marketplace add mvanhorn/last30days-skill`）
  2. 直接问"过去 30 天 AI 视频领域最火的 10 个话题"，它跨平台抓取按热度排序返回
  3. 排序依据是 upvote / like / 真钱（Polymarket），不是编辑精选
  4. v3 pipeline，SKILL.md 是唯一真相源；GitHub Trending 日榜 #1
- **安装**：`npx skills add mvanhorn/last30days-skill -g`
- **怎么用它搞钱**：做"热点监测"服务：每天给客户或自己的账号输出热点选题清单；或做爆款选题预警，接单按月收费
- **来源**：[mvanhorn/last30days-skill](https://github.com/mvanhorn/last30days-skill) · ⭐64489

### helloianneo/ian-xiaohei-illustrations（小黑手绘配图）
- **一句话**：把中文文章里的判断、流程、隐喻变成"小黑"白底手绘怪诞配图（16:9），适合写中文干货文章需要正文配图、又不想用俗套信息图的人
- **核心用法**：
  1. `git clone https://github.com/helloianneo/ian-xiaohei-illustrations.git`，把子目录装到 Codex
  2. 在 Codex 里说：`Use $ian-xiaohei-illustrations 为这篇中文文章设计并生成 5 张小黑怪诞正文配图`
  3. 核心不是"配一张图"：先理解文章的认知锚点，再把关键判断 / 流程画出来
  4. 视觉语言固定：小黑 IP + 纯白手绘 + 少量红橙蓝中文批注，形成个人识别度
- **安装**：`git clone https://github.com/helloianneo/ian-xiaohei-illustrations.git`（子目录装入 Codex）
- **怎么用它搞钱**：接公众号 / 小红书配图单：统一视觉 IP 的配图比通用 AI 生图更有辨识度；自己做内容时，怪诞手绘风是天然的点击率加成
- **来源**：[helloianneo/ian-xiaohei-illustrations](https://github.com/helloianneo/ian-xiaohei-illustrations) · ⭐12607

### rohunvora/x-research-skill（X 调研 agent）
- **一句话**：把 X API 包成 CLI 的调研 skill：在终端里搜帖、拉 thread、监控账号，适合做竞品监测、热点追踪、选题调研的人
- **核心用法**：
  1. `git clone https://github.com/rohunvora/x-research-skill.git x-research` 到 `.claude/skills`（需 X API key）
  2. 按互动排序搜帖 + 时间过滤 + 噪音去除，一次拿到干净的调研结果
  3. watchlist 监控指定账号，cache 避免重复烧 API 钱
  4. 每次搜索显示花费，成本透明
- **安装**：`git clone https://github.com/rohunvora/x-research-skill.git`（需 X API key）
- **怎么用它搞钱**：接"竞品 / 舆情监测"单：给客户搭 watchlist，每日输出监测简报按月收费；自己做号时，用它追对标账号的爆款
- **来源**：[rohunvora/x-research-skill](https://github.com/rohunvora/x-research-skill) · ⭐1244

### sergebulaev/x-skills（X 营销工具集）
- **一句话**：20 个 X 营销 skills：按指定口吻写推文 / Thread / 回复、剔除 AI 味，适合在 X 上做内容获客的人
- **核心用法**：
  1. `/plugin marketplace add sergebulaev/x-skills` 后 `/plugin install x-skills@x-skills`（MIT）
  2. 20 个 skills 各管一摊：推文写作、Thread 展开、回复、营销话术
  3. 写出的东西先过"去 AI 味"处理再发，口吻可指定
  4. 支持 Publora 发布流程；与库内 sergebulaev/tiktok-skills（TikTok 向）是不同 repo，不重复
- **安装**：`/plugin marketplace add sergebulaev/x-skills` 后 `/plugin install x-skills@x-skills`
- **怎么用它搞钱**：接 X 代运营单：20 个 skills 就是 SOP，内容生产标准化；自己做英文获客时，一人即小编
- **来源**：[sergebulaev/x-skills](https://github.com/sergebulaev/x-skills) · ⭐137

### ponyodong2026/ponyo-cover-anchor-system（小红书封面锚点）
- **一句话**：小红书 / 公众号封面"信息密度 × 视觉锚点"生成系统：3 秒内让用户判断"这条和我有没有关系"，适合封面点击率上不去的人
- **核心用法**：
  1. 输入主题、目标人群、内容类型，输出推荐封面模板 + 锚点位置 + 配色 + 字重层级
  2. 直接生成可用于 ChatGPT Image 2 / DALL-E 的成品封面提示词
  3. 数字型 / 冲突型 / 情绪型模板按内容类型自动推荐
  4. 生成的封面不硬塞作者水印，可换自己的账号署名
- **安装**：`git clone https://github.com/ponyodong2026/ponyo-cover-anchor-system.git`（SKILL.md 喂给 Agent 用）
- **怎么用它搞钱**：接封面设计单：按"3 秒决策"方法论出封面，比纯美工更有说服力；自己做号时，封面点击率是最便宜的流量杠杆
- **来源**：[ponyodong2026/ponyo-cover-anchor-system](https://github.com/ponyodong2026/ponyo-cover-anchor-system) · ⭐195

### JimLiu/baoyu-skills（宝玉 20+ 效率 skills）
- **一句话**：宝玉 (@dotey) 分享的 20+ 日常工作效率 skills（含封面图、文章插画等内容生产向），适合想抄"顶流博主工作流"的人
- **核心用法**：
  1. `npx skills add jimliu/baoyu-skills`，但别全装——只装需要的，省 context
  2. 内容生产向：`baoyu-cover-image` 做封面、`baoyu-article-illustrator` 配文章插画
  3. 每个 skill 独立目录，可单独拷到项目的 `.agents/skills` 按需用
  4. 与库内 jimliu/baoyu-design（Claude Design 本地运行）是不同 repo，不重复
- **安装**：`npx skills add jimliu/baoyu-skills`（按需单装）
- **怎么用它搞钱**：学顶流的内容生产管线：封面 + 插画 + 效率工具一套，复制到自己的内容业务里降本；或照着它的 skill 结构给自己定制专属 skills
- **来源**：[JimLiu/baoyu-skills](https://github.com/JimLiu/baoyu-skills) · ⭐26716

## 去 AI 味（4 个）

> 注：op7418/Humanizer-zh 不在本批次提炼范围（已有独立 skill 在用）。humanizer 走检查清单路线，tt-humanizer 专攻短视频口播，qu-ai-wei 专攻简体中文改写，humanizer-skill 带检测评分 + 多人声改写。

### humanizer
- **一句话**：把 AI 味文本改得像真人写的（不改意思、不编事实），基于维基百科"AI 写作特征"指南的 26 项可操作检查清单；适合所有要公开发布的文字。
- **核心用法**：
  1. 四步流程：全文标记所有 AI 特征（强项见一个改一个）→ 起草改写（保留全部事实，不删信息）→ 朗读检查（"还有没有 AI 味""有没有增删事实"）→ 写终稿。每句必须给读者新信息，否则就是水话。
  2. 五大最强特征（见一个就改）：①"不是 X 而是 Y"转折（"不只是功能，更是一种生活方式"）；②独句结尾/戏剧碎片（"细品。""这才是真正的赢。"）；③故作深沉的格言（"本质上，真正重要的是……"）；④ staged 开场（"说句实话？""听我说"）；⑤ 与空气辩论（"我不是说 X，但是……"）。
  3. 节奏类：删强制三连句（出现率是人类的 2 倍）、破折号当万能连接词、句式开头重复、被动语态 + 缺主语。
  4. 膨胀类：AI 高频词（早期：delve/realm/旅程；2026 耐用品是 significant、crucial、notably、robust、leverage、streamline、elevate 这类"普通大词"）、模糊归因、-ing 式浅层分析、销售腔、借用权威背书。
  5. 误杀保护：有作者真实样稿时，样稿优先级高于去 AI 规则（作者真用破折号就按作者频率保留）；学术/技术/法律文本中性平实就是"人味"，不强加观点。
- **安装**：npx skills add blader/humanizer
- **怎么用它搞钱**：做公众号/小红书代运营的"去 AI 味润色"增值服务——客户用 AI 写初稿，你按 26 项清单人工过一遍再发布，按千字收费；或打包卖"AI 代写 + 去味"两道工序，做差异化接单。
- **来源**：[blader/humanizer](https://github.com/blader/humanizer) · ⭐55953


### tt-humanizer
- **一句话**：专给短视频口播脚本/字幕去 AI 味——纸上读着顺、嘴上说出来像机器人的问题，用四道工序逐个修；注意它不保证过 AI 检测器，目标是观众听着像真人。
- **核心用法**：
  1. 四道工序：① Scrub 按"每拍密度"扫词库（一个 AI 词不算，同一拍出现 3 个才重写；reveal bridge、否定平行、真诚宣告、死 filler、模型泄露见一个杀一个）；② Rhythm 只修"说不出口"——换口语（缩写、一口气一行）、拆需要两口气的长句，绝不为节奏硬插短促金句（那是 humanizer 自己的指纹）；③ Add 加人味指纹——要一个平直的、有日期的、甚至让人不舒服的具体事实；④ Over-correction Guard 检查前三道工序有没有引入新的 AI 味，拿不准就别动。
  2. 2026 新认知：词汇按密度判不按删除名单判（delve/tapestry 已过时，耐用品是 significant/crucial/notably/comprehensive/insights/robust/leverage/foster/landscape/nuanced/streamline/elevate 等"普通大词"加名词化、-ing 开头句式，出现率是人类 5.3 倍）；破折号不封杀，提词器里用".."当呼吸记号，字幕卡最多 1 个。
  3. 禁区清单：真诚宣告（"不骗你""说真的"）、"The X? Y." 式揭秘、"No X. No Y. Just Z." 三连、"原因？因为……"伪苏格拉底问答、为节奏硬插的独词行（"Still." "Exactly."）。
  4. 拍前 audit 模式：不改文只出结论——前 3 秒钩子强度、静音刷屏适配、完播结构、字幕/话题标签适配，输出 Blocker + Warning；还有 --mode profile 可从用户旧稿学习其声音指纹。
- **安装**：npx skills add sergebulaev/tiktok-skills
- **怎么用它搞钱**：做短视频团队的"拍前质检"外包——客户发口播脚本，你跑 audit 模式出 Blocker/Warning 报告按次收费；或给 MCN 做批量脚本去味，按账号收月费。
- **来源**：[sergebulaev/tiktok-skills](https://github.com/sergebulaev/tiktok-skills) · ⭐69

### qu-ai-wei（简体中文去 AI 味）
- **一句话**：专治简体中文 AI 味的改写 skill——删套话、保事实、技术文不降格，适合写公众号 / 小红书 / 视频文案总被说"一看就是 AI 写的"的人
- **核心用法**：
  1. `npx skills add https://github.com/LifelongLazyLearner/qu-ai-wei`，对中文说"去 AI 味"即触发（`/qu-ai-wei`）
  2. 先识别 10 类中文 AI 味结构（"随着…发展""值得一提"等），只改空转、反复出现的套话，单独出现一次不误杀
  3. 铁律：删空话不丢数字（"发布 3 个版本、修复 17 个问题"原样保留），技术词、因果关系、正式程度保持不变
  4. 真人味文字（有具体经历 / 自嘲 / 自然节奏）会停手不乱改；输入含密码、key 等敏感信息先过门检
- **安装**：`npx skills add https://github.com/LifelongLazyLearner/qu-ai-wei`
- **怎么用它搞钱**：接文案代写单：AI 初稿 + qu-ai-wei 去味，交付"真人感"文案按千字收费；做矩阵号时去味后多平台分发，降低被判营销号 / 限流风险
- **来源**：[LifelongLazyLearner/qu-ai-wei](https://github.com/LifelongLazyLearner/qu-ai-wei) · ⭐660

### Aboudjem/humanizer-skill（55 模式检测 + 5 人声）
- **一句话**：55 种 AI 写作模式检测 + 0-100 AI 味评分 + 5 种人声改写，适合发英文博客 / LinkedIn / Newsletter 怕被看出 AI 味的人
- **核心用法**：
  1. 三种模式：`detect` 只扫描打分不改写；`rewrite` 按选定人声改写；`edit` 直接改文件（`--mode` 切换）
  2. 5 种声音按场景选：casual / professional / technical / warm / blunt，`--voice` 指定
  3. 纯 Markdown、零依赖、不联网，本地跑完；`--iterate N` 多轮改写直到分数满意
  4. `--purpose` 按用途调（essay / email / marketing / technical），`--score` 输出量化分
- **安装**：`claude plugin marketplace add Aboudjem/10x && claude plugin install humanizer@10x`
- **怎么用它搞钱**：接英文内容代写 / 领英代运营单：AI 量产 + humanizer 去味，交付"母语写手"质感收溢价；做英文利基站，内容去味后广告审核、投稿通过率更高
- **来源**：[Aboudjem/humanizer-skill](https://github.com/Aboudjem/humanizer-skill) · ⭐281

---

## 提示词

> 提示词本身也是生产力：prompt-master 把"写好提示词"变成标准化流程，skill-creator 教你把任何工作流封装成可复用的 skill。

### prompt-master
- **一句话**：专职"提示词工程师"角色，把一句话需求变成可直接粘贴的生产级提示词，适合天天要调 AI 工具的人
- **核心用法**：
  1. 先确认目标工具再动笔（Claude / ChatGPT / Midjourney / Cursor 写法完全不同），含糊就问，最多问 3 个澄清问题
  2. 静默提取 9 个维度：任务 / 目标工具 / 输出格式 / 约束 / 输入 / 上下文 / 受众 / 成功标准 / 示例，缺关键项才追问
  3. 按目标工具路由写法：Claude 用 XML 标签分段、推理模型（o3/o4）只给短指令绝不加"一步步思考"、Midjourney 走画面描述模板
  4. 输出格式固定：单个可复制提示词块 + 🎯目标行（一句话说明优化了什么）+ 必要时 1-2 行粘贴前准备说明，不加废话
- **安装**：`git clone https://github.com/nidhinjs/prompt-master.git ~/.claude/skills/prompt-master`
- **怎么用它搞钱**：接"提示词代写 / 优化"单；或把它嵌进自己的 AI 工作流产品里当标配模块
- **来源**：[nidhinjs/prompt-master](https://github.com/nidhinjs/prompt-master) · ⭐14345

### skill-creator
- **一句话**：Anthropic 官方 skill，教你从零创建、测试、迭代一个 skill，适合想把自己的工作流变成资产的人
- **核心用法**：
  1. 先抓意图：从对话里提取"要让 Claude 会做什么、什么时候触发、输出什么格式"，用户确认后再写
  2. 按标准骨架写 SKILL.md：`name/description`（description 是触发器，要写得"pushy"一点多列触发场景）+ 正文指令 + 可选的 scripts/references/assets 三层渐进加载
  3. 写 2-3 个真实测试 prompt 跑一遍，存进 evals/evals.json；能量化就加断言，不能就定性看
  4. 根据测试结果改一版再测，循环到满意；最后跑 description 优化器提升触发准确率
- **安装**：`npx skills add anthropics/skills`
- **怎么用它搞钱**：把验证过的 skill 打包卖（kk 的 13 视频库就是这么攒出来的）；或给企业做定制 skill 咨询，一个 skill 一份报价
- **来源**：[anthropics/skills](https://github.com/anthropics/skills) · ⭐180612

### cangjie-skill（书/播客蒸馏成 skills）

- **一句话**：把一本书、长视频转写、播客、课程蒸馏成一组可被 Agent 调用的 skills（方法论/决策框架/清单原子化），适合想把知识变成生产力工具的人
- **核心用法**：
  1. 准备文本来源（PDF/EPUB/转写稿）+ 元信息（书名+作者+出版年）；视频/播客先拿转写文本——绝不凭记忆蒸馏
  2. 确认使用目的：自己学→single 模式；接入工作流/跨书组合→pack 模式
  3. 跑 RIA-TV++ 五阶段流水线：整书理解→5 agent 并行提取→三重验证→能力卡→压力测试→`cangjie.py compile` 编译交付
  4. 首次先蒸馏 1 份试点验证流程再批量；确定性脚本需 Python 3.10+ 和 PyYAML
- **安装**：下载 [v2.5.0 Release 包](https://github.com/kangarooking/cangjie-skill/releases) 解压安装完整目录（或 `git clone https://github.com/kangarooking/cangjie-skill`）
- **怎么用它搞钱**：把行业经典书/课程蒸馏成专属 skills，打包卖"知识工具箱"；或给企业做知识资产 skill 化咨询
- **来源**：[kangarooking/cangjie-skill](https://github.com/kangarooking/cangjie-skill) · ⭐11247

---

---

## 收录标准

- 源仓库 star > 20（官方 / 新库可破格，需注明原因）
- 一年内有更新
- skill 有真实可用内容（SKILL.md 或等价文档），纯链接列表不收
- 热度看 GitHub star + 更新时间交叉验证，不单独信分发站的 install 数（防刷量）
- 与库内现有条目去重，宁缺毋滥

## 和 13 个视频库的关系

- 这个库是"工具层"：装上就能用的 skills
- [x-viral-video-skills](https://github.com/kkone1238899/x-viral-video-skills) 13 个分类库是"方法层"：爆款生产方法
- 两边互补，互链不合并

## 更新日志

- 2026-10-16：v1.7 X 信号轮追加 10 条（视频生产 3 条：dexhunter/seedance2-skill Seedance 2.0 提示词（中英双版）4322★、Vincentwei1021/video-shotcraft 镜头配方卡+Remotion 12170★、liyupi/ai-promo-video-maker 产品宣传片全流程 304★；文案钩子 1 条：dontbesilent2025/dbskill 选题与 Hook 诊断（4176 知识原子，CC BY-NC 4.0）10708★；营销增长 6 条：mvanhorn/last30days-skill 跨平台热源研究 64489★、helloianneo/ian-xiaohei-illustrations 小黑手绘配图 12607★、rohunvora/x-research-skill X 调研 agent 1244★、sergebulaev/x-skills X 营销工具集 137★、ponyodong2026/ponyo-cover-anchor-system 小红书封面锚点 195★、JimLiu/baoyu-skills 宝玉 20+ 效率 skills 26716★），共 80 个 skills；淘汰 aaaronmiller/create-viral-content（75★，star 太弱无热度佐证）、adrianpunk/Punk-Skill（1325★，商业用途需书面付费授权，与搞钱用途冲突）、bobobo2026/explainer-video（0★ 未达标）、TheMattBerman/x-algo-skill（68★，热度弱）、wshuyi/x-article-publisher-skill（873★，纯发布工具无方法论）、LunarXuan/image-prompt-reverse（529★，生图向，章节不匹配）、nexu-io/html-anything（9143★，HTML 生成，dev/设计向）、QianXiguaAI/video-privacy-blur（小众工具，需求弱）；X 信号源：@nicebabycat/@fhwofjow51260/@GitHub_Daily/@voidJan/@starkljm/@superfang119/@kafkaup/@b70670555886391/@Lonely__MH 等 12 帖命中（48h 窗口，宁缺毋滥）；记信号不收录：@Williamsungo 外快清单（链接截断无法验证）、@kaitoxhacker SEO 方法论（无仓库）、@xiaohu Opus 5.5 展示帖（无具体 skill）、@vista8 skill 行业讨论（无推荐）
- 2026-10-16：v1.6 追加 5 条（营销增长 3 条：vivy-yi/xiaohongshu-skills 小红书 139 技能知识库 492★、AgriciDaniel/claude-seo 全栈 SEO 审计系统（26 子 skill）19053★、zubair-trabzada/geo-seo-claude AI 搜索 GEO 专项 11067★；去 AI 味 2 条：LifelongLazyLearner/qu-ai-wei 简体中文去 AI 味改写 660★、Aboudjem/humanizer-skill 55 模式检测+5 人声 281★），共 70 个 skills；淘汰 autoclaw-cc/xiaohongshu-skills（1974★，真实账号自动发布/互动，封号风险，与 white0dew 同类）、DeliciousBuding/xiaohongshu-skill（42★，同类自动化）、freestylefly/xiaohongshu-skills（97★，付费 API 包装，本体无方法论干货）、crabin/paper-humanizer-skill（127★，学术论文向）、robpalmer99/claude-code-copywriting-skills（41★，库内已有更强同类 ai-copywriter）、jherrodthomas/automotive-skills-suite（3226★，汽车工程向，章节不匹配）、Jakeschincariol/replica-skill（2839★，应用逆向工程向，章节不匹配）；skillhub.cn 全站详情页无 GitHub 源码链接、无法交叉验证，0 收录（但去 AI 味类下载极旺：李白.Skill 88.4万、文章去AI味工具 62.4万，记为需求信号）；skills.sh 榜单仍是老面孔（open.feishu.cn/mattpocock/superpowers 分叉/runcomfy），无新货；X 热度洞察 browser task 进行中，结果另起 v1.7 批次
- 2026-10-15：v1.5 追加 15 条（视频生产 8 条：Jane-xiaoer/claude-skill-video-transcribe 视频转文字 231★、hyperframes 5 子 skill——faceless-explainer 无脸讲解视频、talking-head-recut 口播/访谈包装、motion-graphics 动态图形短片、music-to-video 音乐卡点视频、embedded-captions 特效字幕（主库 64,282★ 当日更新，双高验证）、kaomei/stickman-video-director 火柴人动画 2124★（@CrazyKaomei 推荐帖 21K 浏览）、op7418/Youtube-clipper-skill 长视频切片 2240★；文案钩子 3 条：zenstory-ai/oh-story-claudecode 网文工具箱 7605★、KKKKhazix/khazix-skills 卡兹克长文写作 21427★、claude-world/notebooklm-skill 研究转内容 471★；营销增长 4 条：Xiangyu-CAS/xiaohongshu-ops-skill 小红书全链路 2428★、op7418/guizang-social-card-skill 小红书图文 7540★、op7418/guizang-ppt-skill 杂志风演示稿 28013★、imraywang/wewrite 公众号全流程 3464★），共 65 个 skills；淘汰 superpowers 系 7 分叉 + prime-skills/runcomfy-agent-skills（skills.sh 数十万 install 对应 GitHub 0–55★，刷量嫌疑再验证）、pr-to-video（GitHub PR 转代码讲解，dev 向）、slideshow（交互式 deck 非视频形态）、hyperframes 技术参考类子 skill（keyframes/animation/creative/audio/studio/registry/media-use/figma/remotion-to-hyperframes，已有 cli/core/general-video 覆盖，不凑数）、feichanggege/pderr-short-video-skill（18★ 未达标）、white0dew/XiaohongshuSkills（3503★，自动发布/评论，SKILL.md 自带封号风险警告）、Weizhena/Deep-Research-skills（2361★，章节不匹配）、gzlliyu/generate_article（92★，纯脚本非 skill）、sansan0/TrendRadar（62924★，独立监控工具非 skill）、freestylefly/awesome-gpt-image-2（提示词库非 skill）、LangGPT/linexjlin/GPTs/lijigang/prompts（提示词合集非 skill）；去重 openakita content-research-writer / qiaomu-anything-to-notebooklm / marketingskills / Humanizer-zh（库内已有）；skillhub.cn 热榜仍为通用"专家.Skill"无 GitHub 可验证，0 收录；X 侧记信号不收录：YouMind youtube skill（平台内无公开仓库）、@HastyRick135248 网盘打包（无具体仓库名）、@densancar 广告仿写 skill（非公开仓库）
- 2026-10-13：v1.4 X 信号轮追加 2 条（wheresryan22/anatomy 概念可视化演示 7762★、jimliu/baoyu-design Claude Design 本地运行 4344★），共 50 个 skills；淘汰 vercel-labs/skills（34264★ 基础设施工具、无 SKILL.md，不符合收录标准）、101-skills/superpowers（7★）与 qu-skills/superpowers（3★，榜单高 install 均为刷量嫌疑）、travisvn/BehiSecc awesome-claude-skills（纯链接列表，库内已有两个同类）、Jeffallan/claude-skills·SnailSploit/Claude-Red·SawyerHood/dev-browser·juliusbrussee/caveman·nextlevelbuilder/ui-ux-pro-max·emilkowalski/skills·vercel-labs/agent-skills·obra/superpowers（dev/设计/安全向，与五章节需求不匹配）、designed-by-ai/skills（15★ 未达标）、scrapegraphai/just-scrape（CLI 非 skill 形态）；skillhub.cn 新上新 10 个全无 GitHub 源码不可验证、热榜通用"专家.Skill"需求不匹配，0 收录
- 2026-10-13：v1.3 X 信号轮追加 6 条（mortiflix-oss 本地动态设计 593★、xhs-account-teardown 小红书账号拆解 66★、xhs-product-picker 选品 120★、qiaomu-seo 446★、xyskill 中文商业操盘 79★、cangjie-skill 知识蒸馏 11247★），共 48 个 skills；淘汰 genmedia-labs/skills（与 runcomfy 刷量生态关联、27★ 未达双高）、flowkit-labs/skills（16★）、analyze_xhs_blogger_skill（404 无效）
- 2026-10-13：v1.2 追加 3 条（qiaomu-anything-to-notebooklm 内容转播客 6229★、irinabuht12-oss/marketing-skills 广告审计整库 4398★、hyperframes product-launch-video 产品发布视频），共 42 个 skills
- 2026-10-12：v1.1 追加 P0 三套（marketingskills 9 条、Hyperframes 4 条、Remotion 1 条），共 39 个 skills
- 2026-10-12：v1 首版，25 个 skills（12 个源仓库深读提炼），每日深度比对分析持续收录中
