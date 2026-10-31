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
- **安装**：`npx skills add remotion-dev/skills`（官方独立 skills 仓，含 create/markup/captions/maps/studio/render 等 12 个 skills）
- **怎么用它搞钱**：React 开发者做视频零学习成本；接数据视频/播客剪辑单，代码复用率高
- **来源**：[remotion-dev/skills](https://github.com/remotion-dev/skills) · ⭐5703（2026-10-22 更新；⚠️ 该独立仓暂无 LICENSE 文件，商用前请确认授权）

### qiaomu-anything-to-notebooklm（内容转播客）

- **一句话**：微信文章 / 网页 / YouTube / 小宇宙 / B站 / PDF 一键喂给 NotebookLM，批量生成播客 / PPT / 思维导图，适合做知识二创和内容矩阵的人
- **核心用法**：
  1. 克隆到 `~/.claude/skills/` 跑 `./install.sh` 一键装依赖（自带 `check_env.py` 做 13 项环境检查）
  2. 按提示配 weixin-read-mcp（微信文章走 MCP 抓取，绕反爬），再 `notebooklm login` 认证
  3. 自然语言触发：`/qiaomu-anything-to-notebooklm [微信文章链接]`，或"把这个 B 站视频转写传到 NotebookLM"
  4. 付费墙自动绕过（300+ 站点：UA 伪装 → AMP → archive.today）；小宇宙 / 喜马拉雅 / B 站转写走 Get笔记 API（带时间戳）
- **安装**：`cd ~/.claude/skills/ && git clone https://github.com/joeseesun/qiaomu-anything-to-notebooklm && cd qiaomu-anything-to-notebooklm && ./install.sh`（需 `notebooklm login`）
- **怎么用它搞钱**：把爆款文章 / 播客变成自己的播客节目或 PPT 课程素材，一源多用；或接"知识库搭建 / 播客代运营"单
- **来源**：[joeseesun/qiaomu-anything-to-notebooklm](https://github.com/joeseesun/qiaomu-anything-to-notebooklm) · ⭐6441

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
- **来源**：[Vincentwei1021/video-shotcraft](https://github.com/Vincentwei1021/video-shotcraft) · ⭐15169

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

### Jakeschincariol/youtube-agent-skill（YouTube 频道全链路）
- **一句话**：11 个 skill 承包一个 YouTube 频道的全部活：按 21 个钩子公式写脚本并打分、标题+缩略图打包质检、剪辑决策清单、评论区分类回帖、周计划、爆款研究、留存分析——适合做 YouTube 广告分成 / 出海获客的人
- **核心用法**：
  1. 先花 10 分钟填 `templates/voice.md`（或丢 3 条自己的视频让 AI 提炼），所有 skill 都读它——口播场景"人声"比什么都重要
  2. `/yt-script`：给一个想法，AI 按 21 个钩子公式写 5 个钩子并打分，选最高分的再写带留存节拍标记的完整口播稿
  3. `/yt-package`：标题和缩略图文字当成一个组合写，自动查截断、重复、模糊
  4. `/yt-edit`：录制 transcript 丢进去，输出带时间码的剪辑决策清单（冷场/废话/重录段）
  5. `/yt-viral`：找本赛道爆款，按"超出该频道自身均值倍数"排名——抄公式不抄大号
- **安装**：`git clone https://github.com/Jakeschincariol/youtube-agent-skill.git && cp -r youtube-agent-skill/skills/yt-* ~/.claude/skills/`（或 Claude Code 里 `/plugin marketplace add Jakeschincariol/youtube-agent-skill`）
- **怎么用它搞钱**：YouTube 广告分成——一个人跑 N 个频道做矩阵；或接"YouTube 频道代运营"单：脚本+封面+剪辑清单一套交付，比请剪辑师便宜一个数量级
- **来源**：[Jakeschincariol/youtube-agent-skill](https://github.com/Jakeschincariol/youtube-agent-skill) · ⭐3874

### AirsupHQ/machine-skill（工程机械 3D 动画）
- **一句话**：一句话描述一台机器，Claude 按真实尺寸和物理原理在浏览器里造出一台可交互的 3D 机器（three.js，无需构建），再一键转成可发的短片——适合做工业品演示、产品技术展示的人
- **核心用法**：
  1. `npx skills add AirsupHQ/machine-skill -g -a claude-code`
  2. 一句话描述：`/machine a turbofan jet engine, the kind that pushes a widebody off the runway`
  3. Claude 先研究真实机器的尺寸与物理，造出可交互 3D 场景（拉油门真的出推力、剖开真是实心金属）
  4. 一条命令转成短片（`scripts/record.mjs` 录制），直接发 feed
  5. 改参数重跑即可换机器——有多少产品就能产多少演示片
- **安装**：`npx skills add AirsupHQ/machine-skill -g -a claude-code`
- **怎么用它搞钱**：工业品/设备商的产品演示片：传统三维外包贵且慢，这个一句话一条片；或做"AI 工业演示"代做单，按产品收费
- **来源**：[AirsupHQ/machine-skill](https://github.com/AirsupHQ/machine-skill) · ⭐286

### lhlGitHub/hand-drawn-storybook-animation-skill（手绘水彩动态绘本）
- **一句话**：在浏览器里做"会自己画画的"手绘水彩动态绘本：分层场景、设计镜头、翻页/笔刷/撕纸转场、豆包配音+中英双语字幕——适合做儿童故事/治愈系账号起号的人（X 中文社区 48h 互动最高的 skills 帖，32.9K 浏览）
- **核心用法**：
  1. `git clone https://github.com/lhlGitHub/hand-drawn-storybook-animation-skill.git && cp -r hand-drawn-storybook-animation-skill/hand-drawn-storybook-animation ~/.claude/skills/`
  2. 一句话开工："做一本会自己画画的绘本"——画面在浏览器实时画出，不是预渲染视频
  3. 加章节/换配音："给绘本加一章，用豆包配音"（豆包 TTS 需自己的火山引擎 API Key，放项目 `.env`，不提交）
  4. 跑通后按 README 的验证流程检查转场与字幕，再录屏发布
- **安装**：`git clone https://github.com/lhlGitHub/hand-drawn-storybook-animation-skill.git && cp -r hand-drawn-storybook-animation-skill/hand-drawn-storybook-animation ~/.claude/skills/`
- **怎么用它搞钱**：儿童故事/睡前故事账号起号：手绘水彩风差异化强；或接"动态绘本定制"单（品牌 IP、电子绘本系列），按本收费。注：仓库暂无 LICENSE 文件声明，商用前建议与作者确认授权
- **来源**：[lhlGitHub/hand-drawn-storybook-animation-skill](https://github.com/lhlGitHub/hand-drawn-storybook-animation-skill) · ⭐36

### alchaincyf/huashu-art-motion（艺术动画：代码逐镜做片）
- **一句话**：中文艺术动画 skill：36 种实做风格＋16 种可迁移研究配方、9 种解说动画语法，用代码逐镜渲染讲解视频——适合做知识科普动画、接"AI 动画代做"单的人
- **核心用法**：
  1. 先写镜头表：照 `references/镜头表模板.md` 每行一镜（时间段｜画面里的物｜它在做什么｜镜头｜屏上字≤8 字｜做法）；先锁画风+色板，开头 3 秒必须是一个具体小场景，不能是标题
  2. 过 lint：`uv run scripts/storyboard_lint.py <项目>/镜头表.md`，红灯不清不许开工（有口播稿加 `--script` 查屏上数字和口播是否一致）
  3. 逐镜渲染：参数化片段 `render.py --spec 镜NN.json`（单个片段最多撑 8 秒，超了拆镜）；艺术风格画面写 `scenes/<id>.js` 登记进 `eras.js`；全片一套色板、最多 2 种片段语法
  4. 拼接：`ffmpeg -f concat` 硬切成片，有口播再混音；每镜抽帧排成一排对着镜头表看，哪一镜像从别的片子拿来的就按画风重做
  5. QA+交付：`qa.py` 逐镜自查"六种做坏方式"，`deliver.py` 红灯不交付、黄灯逐条写理由
- **安装**：`npx skills add alchaincyf/huashu-art-motion`（需 uv、ffmpeg、Playwright Chromium）
- **怎么用它搞钱**：接知识科普/教育机构动画定制单：镜头表+lint+逐镜渲染是标准化交付流程，一套模板复用多单；或做"艺术史速览"类账号，36 种风格配方是护城河
- **来源**：[alchaincyf/huashu-art-motion](https://github.com/alchaincyf/huashu-art-motion) · ⭐4381

### lemomo-ai/lemo-opuscar（66 种影片风格提示词）
- **一句话**：66 种影片风格、每种配一支"纯代码做出来"的样片（含 OPUSCAR 98 奥斯卡百年风格库）：不用视频生成模型，agent 写代码逐帧画——适合要风格化短片、想零成本试风格的人
- **核心用法**：
  1. 先逛在线画廊选风格：66 种风格每种有样片+可复用的 style prompt，风格与内容解耦，同一风格换题材即出新片
  2. 讲自己的故事：拿 style prompt 喂自己的题材，agent 按 DIRECTOR.md/TECHNIQUE.md 写代码导演
  3. 画面 canvas/WebGL 逐帧渲染、配乐用免费采样库、旁白 TTS，全链路零视频模型成本
  4. 新增「实证影像」8 种风格：拍真实素材、每个数字有出处，适合要"看起来像真的"的纪实风
  5. 一支片子约 30–60 分钟 agent 时间，注意 token 成本；默认 1920×1080@24fps
- **安装**：`claude plugin marketplace add lemomo-ai/lemo-opuscar && claude plugin install lemo-opuscar@lemolab`（需 Node 20+、ffmpeg、Python 3.11+）
- **怎么用它搞钱**：风格化短片定制（婚礼/品牌故事/产品发布）：风格库是现成菜单，客户点风格你出片；或做"一镜一世界"系列账号，66 种风格=66 期内容不断更
- **来源**：[lemomo-ai/lemo-opuscar](https://github.com/lemomo-ai/lemo-opuscar) · ⭐9450（注：风格为 Claude Opus 5.5 调优，其他模型效果可能打折）

### echris6/motion-video-kit（商业级动态影片）
- **一句话**：商业级 AI 辅助视频 skill kit：从 28 部 SaaS 产品发布片提炼的动效语法＋独立 critic 评审循环＋可测量的质量门，专做"看起来贵"的商业宣传片——适合接 B 端宣传片/发布会视频单的人
- **核心用法**：
  1. 走 Gauntlet 评审循环：builder ≠ judge，用现成的 critic prompts 让"新鲜评审"逐项验片，ledger 记账，不达标不交付
  2. 动效按 6 规则+16 种可复用机制选（motion-grammar.md），不凭感觉加特效；节奏数字有出处
  3. 质量门可测量：frozen time、响度、对比度、品牌色，脚本一键跑（scripts/ 里有现成工具）
  4. 声音设计单独一环：配乐按买家画像选、卡点踩在 end card 上，每个小动效配干净音效，混音有目标值
  5. 报价直接套 business-offers.md：垂直行业+购买证据+价格锚点+pilot offer 模板
- **安装**：`git clone https://github.com/echris6/motion-video-kit.git && cp -r motion-video-kit/business-motion-film ~/.claude/skills/`（脚本需 ffmpeg/ffprobe）
- **怎么用它搞钱**：接 B 端商业宣传片/产品发布视频：critic loop+质量门是"贵"的证据，报价时把品控流程写进方案；28 部发布片的动效原理是谈单话术
- **来源**：[echris6/motion-video-kit](https://github.com/echris6/motion-video-kit) · ⭐1139

### higgsfield-ai/skills（Higgsfield 官方 8 件套：生成+品牌+爆款预测）
- **一句话**：Higgsfield 官方 skill 包：30+ 模型（Veo 3.1/Kling 3.0/Seedance 2.5/Nano Banana 2）一键生成图/视频/3D/音频，Marketing Studio 做品牌广告（avatar/产品/钩子/场景），Virality Predictor 给成片打爆款分——适合做产品广告、电商素材、短视频矩阵的人
- **核心用法**：
  1. `npx skills add higgsfield-ai/skills` 一行装好，CLI 安装和鉴权自动走完（也支持 gh skill install / Claude Code marketplace）
  2. 生图/视频走 `higgsfield-generate`：一句话描述→30+ 模型自动路由，Seedance 2.5/Veo 3.1/Kling 3.0 直接调
  3. 做品牌广告走 Marketing Studio：avatar+产品+钩子+场景一次配齐，批量出品牌素材
  4. 成片先过 Virality Predictor 打分：分低就改钩子/前 3 秒，不凭感觉发布
  5. 锁脸需求走 `higgsfield-soul-id`：训一个可复用的高保真数字身份，多条视频同一张脸不崩
- **安装**：`npx skills add higgsfield-ai/skills`（需 Higgsfield 账号，鉴权自动处理）
- **怎么用它搞钱**：接电商产品图/广告视频单：product-photoshoot 10 种模式（studio/lifestyle/广告包/虚拟试穿）是标准化交付；或做短视频带货矩阵，soul-id 锁脸+爆款预测是"稳定出片"的卖点
- **来源**：[higgsfield-ai/skills](https://github.com/higgsfield-ai/skills) · ⭐1326

### robonuggets/seedance-skill（App/SaaS 液态玻璃宣传片）
- **一句话**：专做"苹果发布会质感"产品宣传片的 skill：截几张 App/SaaS 界面图，Seedance 2.0 经 Fal 生成液态玻璃动效广告——适合给 App/工具站做推广视频的人
- **核心用法**：
  1. 截图产品界面当参考图：黄金法则 1 张图撑 2 秒，生产级 10 秒片用 5 张
  2. 选 prompt 模板：Liquid Glass（默认，半透明面板+折射）/Floating Desktop（黑底产品悬浮）/Glass UI Ad（交互特写）/Abstract Motion Identity
  3. 先跑 4 秒测试片（约 $1.21）验风格，再跑 10 秒生产片（约 $3.03），默认 Pro 档
  4. 三条铁律：logo 不写进 prompt（传原图当参考）、视频里不出文字（后期叠加）、参考图不超过 5 张
  5. 批量：同一套模板换截图即出新品广告，一套流程多产品复用
- **安装**：`mkdir -p ~/.claude/skills/seedance && curl -sL https://raw.githubusercontent.com/robonuggets/seedance-skill/master/SKILL.md -o ~/.claude/skills/seedance/SKILL.md`（再配 FAL_KEY，见 fal.ai）
- **怎么用它搞钱**：接 App/SaaS 产品宣传片单：截图→成片一条龙，成本透明（10 秒约 $3）好报价；或给自己的工具站批量做发布视频跑量
- **来源**：[robonuggets/seedance-skill](https://github.com/robonuggets/seedance-skill) · ⭐107

### LeoYeAI/seedance-skills（导演级 Seedance prompt OS：28 skills）
- **一句话**：把"导演判断"编码成 28 个模块化 skills 的 Seedance 2.0 prompt 操作系统：需求访谈→分镜序列→多语言原生 prompt→交付质检全流程——适合要稳定出导演级 AI 短片的人
- **核心用法**：
  1. 想法模糊先走 `seedance-interview`：结构化追问把"要个电影感"变成可执行的 brief
  2. 长故事/多镜走 `seedance-sequence`：锁统一导演语调，多 clip 串成 campaign 不散
  3. 域 skills 分工：camera（机位/运镜）/motion（动作编排）/lighting（情绪光）各管一摊
  4. 6 国语言原生 prompt 模板（中/英/日/韩/西/俄），中文文档齐全
  5. IP 安全改写：翻拍/致敬类需求先过 IP-safe rewrite，避免直接复刻惹麻烦
- **安装**：`git clone https://github.com/LeoYeAI/seedance-skills ~/.claude/skills/seedance-20`（OpenClaw/Hermes/Claude Code/Codex/Cursor 均支持，路径见 README 安装表）
- **怎么用它搞钱**：接 AI 短剧/广告导演单：interview→sequence→QC 是"导演服务"的标准化交付流程；或做 Seedance 教程账号，28 个 skills=28 期内容
- **来源**：[LeoYeAI/seedance-skills](https://github.com/LeoYeAI/seedance-skills) · ⭐47

### alchaincyf/seedance-skill（白模驱动：几何级精确运镜）
- **一句话**：用白模（三维 clay 渲染）精确控制 Seedance 运镜和空间关系的 skill：白模参考视频与提示词出自同一份 scene.json，渲染前先做几何体检——适合对运镜精度有执念、做产品演示/建筑漫游的人
- **核心用法**：
  1. 先过 intake：只问三件必须问的（多长、发在哪、一镜到底还是切镜头），其余先推断再摊给用户否决
  2. 白模只管三件事：空间关系、运镜路径、时间节奏；材质光线色彩全交给参考图
  3. 渲染前跑 `engine/probe.mjs` 几何体检：主体出画/太小被丢/死时间/相机穿墙/队形超框，纯数学扫一遍
  4. 提示词用 `engine/make_prompt.mjs` 从白模实际几何量出来（景别/机位距离/俯角/环绕角度），不用手写猜
  5. 记住"白模坏了看不出来"是常态：lint 全绿也可能运镜全错，几何体检是必经环节
- **安装**：`git clone https://github.com/alchaincyf/seedance-skill.git ~/.claude/skills/seedance-skill`（兼容 Claude Code/Codex/Cursor/OpenClaw；engine 脚本需 Node）
- **怎么用它搞钱**：接"运镜必须准"的单：产品 3D 演示、建筑漫游、电商场景视频——几何体检是"一次过"的谈单证据；或做白模控制教程，差异化明显
- **来源**：[alchaincyf/seedance-skill](https://github.com/alchaincyf/seedance-skill) · ⭐41

### HeyChengC/wallstreet-explainer（华尔街式财经解读短片）
- **一句话**：复刻"华尔街式"财经解读短片的 skill：真实素材（发布会/采访抠人）+数字可视化 B-roll+克制转场，代码逐帧渲染——适合做财经/科技解读视频的人（@Daveyang1916 推荐："开头还会出几个钩子让你挑"）
- **核心用法**：
  1. `git clone` 到 `~/.claude/skills/wallstreet-explainer`，装好 pip/npm 依赖+ffmpeg+Playwright
  2. 给选题（自己定或让它出）：开头 5–7 秒抛反差钩子，结尾收成一句判断——钩子可自选，AI 也会备几个让你挑
  3. 素材按优先级自动找：主流视频网站找合适片段裁剪，人物从发布会/采访一帧帧抠出来站大字前讲
  4. 数字表达是 B-roll 重点：数据怎么放、关系怎么画、图表怎么呈现，控制整片风格
  5. 转场铁律：克制——同一对象挂镜头运动，禁 PPT 式渐入渐出、禁连续硬切；配乐平稳底乐+人声自动压低
- **安装**：`git clone https://github.com/HeyChengC/wallstreet-explainer.git ~/.claude/skills/wallstreet-explainer`（再装 requirements.txt/npm 依赖+ffmpeg；抠人需 rembg）
- **怎么用它搞钱**：做财经/科技解读账号：77 秒样片《AI 到底有多烧钱》是可直接抄的作业；或接"高级感"商业解读视频单，素材+数字表达+转场三件套是报价依据
- **来源**：[HeyChengC/wallstreet-explainer](https://github.com/HeyChengC/wallstreet-explainer) · ⭐172（注：仓库未声明 LICENSE，商用前请确认授权）

### threerocks/sweety-handdraw-video（手绘口播视频）
- **一句话**：给主题/文章/故事，做出"边画边讲"的有声手绘视频：逐笔描线、填色、手写文字、配音对齐全自动——适合做知识/故事类口播账号的人（@leo_xiaolei 长文 25K 浏览：黄金 5 秒开场钩子+自动配音+v1.4 变现盘点）
- **核心用法**：
  1. `npx skills add threerocks/sweety-handdraw-video --skill sweety-handdraw-video --agent claude-code codex --global --copy --yes` 一行装好（macOS/Linux）
  2. 丢主题/文章/完整故事：Agent 写口播、设计分镜、生成插画，本地工具负责描线填色手写配音
  3. 画什么、什么画风、讲多久按内容定：淡彩叙事/冷色棱角等插画风格+毛笔/女性手部可选
  4. 默认竖屏 9:16，导演 `presentation.mode` 控单页疏密；样片《那条死于愤怒的蛇》49 秒可先看叙事密度
  5. 版本固定：releases 页有 v1.4.1 安装包+SHA256 校验，更新仓库不会自动动已安装副本
- **安装**：`npx skills add threerocks/sweety-handdraw-video --skill sweety-handdraw-video --agent claude-code codex --global --copy --yes`
- **怎么用它搞钱**：做手绘故事/知识账号：小红书《AI 替我说》500 亿流量激励、YouTube CPM $3–5、Faceless 频道月入 $5000（@leo_xiaolei 变现盘点）；或接"手绘讲解"定制单，描线+配音是标准化交付
- **来源**：[threerocks/sweety-handdraw-video](https://github.com/threerocks/sweety-handdraw-video) · ⭐891

### Kianzzz/xilo-opus-video（Opus 5.5 写代码做视频：三方案竞标）
- **一句话**：让 Opus 5.5"竞标式"做视频的 skill：先给三个拉开差别的方案+预览，你挑一个，它再写成 brief.md 逐镜渲染——适合要风格化短片、怕"一句话丢过去靠运气"的人（@growaiskills 8 skills 选型指南收录对比）
- **核心用法**：
  1. 给想法/文章/产品网址/代码库/参考视频：先问你要做什么
  2. 收三个方案：风格、技术组合、逐镜头画面概括、声音、预计渲染时间，刻意拉开差别
  3. 每个方案看预览：一张关键帧或 2–4 秒小样，再决定
  4. 确认后写成 `brief.md`（结构化提示词，可复用），逐个镜头制作+静帧自检，最后渲染 MP4
  5. 技术栈：Canvas/HTML·CSS·SVG/WebGL 着色器/Three.js/Remotion/HyperFrames/Manim，配乐代码合成
- **安装**：`npx skills add Kianzzz/xilo-opus-video`（skills/ 目录，Claude Code skill）
- **怎么用它搞钱**：接产品宣传片/知识讲解/数据故事单：三方案竞标是"专业感"的谈单流程，brief.md 可复用=边际成本递减；或照着参考视频的结构手法做同款（README 明确支持）
- **来源**：[Kianzzz/xilo-opus-video](https://github.com/Kianzzz/xilo-opus-video) · ⭐207

### chuspeeism/dashi-animationstyle（7 套风格中文知识口播动画）
- **一句话**：把 15–60 秒中文知识口播做成 7 种画风讲解动画的 skill：1920×1080/30fps，画面全由 Claude 写 HTML/Canvas 代码画、不用生图模型——适合做中文知识口播账号的人（@growaiskills 选型指南收录）
- **核心用法**：
  1. `git clone` 到 `~/.claude/skills/dashi-animationstyle`（macOS Apple 芯片实测，Node 22+/ffmpeg/Chrome）
  2. 交一段口播+选风格：立体卡通/黑底科技/超现实拼贴/复古剪纸/复古报刊/扁平流程图/手绘笔记，7 套各有适配场景
  3. Claude 转写字幕→写分镜给你确认→画 3 张静帧给你确认→出整段（也可一句话描述新风格，查 27 种风格词典出方向）
  4. 成片带口播和字幕，可直接拖进剪映接着剪；每套风格卡（配色/字体/动效）在 `styles/<风格>/风格卡.md`
  5. 先跑自检：装好后说"检查一下风格动画的环境"，Claude 会渲一段 21 秒例子验环境
- **安装**：`git clone https://github.com/chuspeeism/dashi-animationstyle.git ~/.claude/skills/dashi-animationstyle`（需 Node 22+/ffmpeg/Chrome；macOS）
- **怎么用它搞钱**：做中文知识口播矩阵号：7 套风格=7 个账号定位，一套口播多风格复用；或接"讲解动画"单，风格卡是现成菜单
- **来源**：[chuspeeism/dashi-animationstyle](https://github.com/chuspeeism/dashi-animationstyle) · ⭐100（注：仓库未声明 LICENSE，商用前请确认授权）

### op7418/guizang-product-video-skill（软件更新宣传片：复用真实产品组件）
- **一句话**：给 AI 你的产品代码库，它整理卖点、写文案、接入你原来的组件做动画、写配乐配音效，输出"看起来像你产品"的更新宣传片——适合独立开发者/小团队发版时用（@YuGuo936066 早报视频 skill 栈实战验证）
- **核心用法**：
  1. `npx skills add https://github.com/op7418/guizang-product-video-skill --skill guizang-product-video-skill`
  2. 打开你的产品代码库，告诉它这次更新了什么（或介绍整个产品）
  3. 三件事是重点：看起来像你的产品（复用真实组件和设计语言）、听得懂在讲什么、看完不觉得拖沓
  4. 输出视频+可继续修改的工程：分镜文案、原创配乐都在工程里，改文案不用重做
- **安装**：`npx skills add https://github.com/op7418/guizang-product-video-skill --skill guizang-product-video-skill`
- **怎么用它搞钱**：给独立开发者/小商家做"发版宣传片"接单：复用真实组件是差异化卖点；或自己每次发版都出一支，保持产品声量
- **来源**：[op7418/guizang-product-video-skill](https://github.com/op7418/guizang-product-video-skill) · ⭐888（注：AGPL-3.0，商用/二次分发注意开源义务）

### calesthio/OpenMontage（AI 剪辑工作室：12 条制片流水线）
- **一句话**：把 Claude Code/Cursor 变成完整视频制片工作室：12 条制片流水线（AI 成片/真实素材混剪/口播/动画/换脸配音等）、49 个 skills，一句"给我做个 60 秒讲解视频"就开工——适合想批量产视频、不想学剪辑的人。
- **核心用法**：
  1. `git clone https://github.com/calesthio/OpenMontage.git && cd OpenMontage && make setup`（需 Python 3.10+、FFmpeg、Node 18+；各模型走自己 API key）
  2. AI 成片流：`create-video`（HeyGen Video Agent：提示词→脚本/形象/配音/字幕全自动）、`ai-video-gen` 调各家文生视频模型
  3. 代码成片流：`remotion-best-practices`（React 视频）+ `manim-composer`（数据动画），字幕走 rules/subtitles.md 的规格
  4. 数字人流：`avatar-video`（HeyGen）+ `faceswap`，配音用 `elevenlabs`/`azure-text-to-speech`
  5. 真实素材流：直接说"只用真实素材"——agent 联网找素材、写脚本、配播客级配音、自动找 BGM 混音
  6. MCP 优先：每个 skill 的 Tool Selection 表列了 MCP 工具和 curl 兜底，有 MCP 就走 MCP，不用手拼请求
- **安装**：`git clone https://github.com/calesthio/OpenMontage.git && cd OpenMontage && make setup`
- **怎么用它搞钱**：批量产 AI 短视频跑流量分成（多流水线=多账号多风格不重复）；接"AI 视频代做"单：选题→成片一条龙，按条收费
- **来源**：[calesthio/OpenMontage](https://github.com/calesthio/OpenMontage) · ⭐71617

### rossark-motion-skill
- **一句话**：把任意 SVG 变成 60 帧专业动画的方法论+小引擎：人物微动、身体表演、植物火焰水光天气全覆盖，React Native/SwiftUI 双模板，离线渲染成视频——适合要做 App 开屏、吉祥物、产品演示动画的人。
- **核心用法**：
  1. 先读 MOTION.md：12 条动效原则（不瞬移、小幅度、弧线关节、重叠跟随、减法优先）是全库的灵魂
  2. 按平台拷引擎：React Native 用 `templates/react-native/motion.ts`，SwiftUI 用 `templates/swiftui/Motion.swift`，一个时钟管一个角色/场景
  3. 画分层 SVG：每个会动的部位单独一层、绕关节点旋转；重复元素（雨滴/星星）用 `seeded(i)` 错相位，绝不同步
  4. 一镜一主角+两三个待机循环；`tools/` 里有逐帧量参考视频的工具，离线渲染直接出视频（含手机框版）
- **安装**：`git clone https://github.com/rossark0/rossark-motion-skill.git`（按需取 templates/ + MOTION.md）
- **怎么用它搞钱**：接 App 开屏/吉祥物动效单：设计稿→代码动效→渲染视频，一套方法论多单复用；或做知识类 MG 动画账号，动效质感是涨粉杠杆
- **来源**：[rossark0/rossark-motion-skill](https://github.com/rossark0/rossark-motion-skill) · ⭐296（2026-10-23，MIT；X @agentskillshub 每日榜推荐，日增速 236+）

### anything2explainer
- **一句话**：给一个主题，约 2 小时产出一条黑底 MG 风、有配音字幕章节进度条的科普讲解视频：Remotion 代码逐帧绘制、4 个确认点、多组并行构建+三轮 QC，附《RAG 与知识库》完整样片当质量标尺——适合做知识/科普/教程视频的人。
- **核心用法**：
  1. 建项目：`template/scripts/new_project.sh <目录> <slug>`，先看 `examples/rag/` 样片帧建立标尺
  2. 按 8 阶段走：调研→解说词定稿→分镜→覆盖层图元→并行构建→渲染→QC 修复→交付；4 个确认点必须停下问用户（时长语言/文案/配音/前 30 秒样片）
  3. 配音默认免费 TTS（中文 edge-tts 云希、英文 kokoro），字幕≤16 字/块，动效词汇库在 `reference/motion-vocabulary.md`
  4. 质检硬指标：`motion_check.py`（最长静止≤3s、末拍稳定期≥30 帧）；样片档两轮 QC 后高 0/中 0/低≤5
- **安装**：`git clone https://github.com/Vincentwei1021/anything2explainer.git`（需 Node + Remotion；同作者 video-shotcraft 已入库）
- **怎么用它搞钱**：接知识付费/企业培训的科普视频单：一个主题=一条成片，2 小时交付；或批量做"一本书一支视频"账号，黑底 MG 风是低成本高辨识度的路线
- **来源**：[Vincentwei1021/anything2explainer](https://github.com/Vincentwei1021/anything2explainer) · ⭐2687（2026-10-23；⚠️ 暂无 LICENSE 文件，商用前请联系作者确认授权）

### pixel-diary
- **一句话**：复刻"像素角色+对话框"类爆款视频（B 站"AI 接管账号"系列 3 天 100 万播放的方法论开源版）：分集 JSON → HyperFrames 代码渲染，改一句台词重出一条约 1 分钟、不花视频模型钱——适合做剧情/养成系账号的人。
- **核心用法**：
  1. 先拆对标：拿原片数据+热评+逐镜头分镜表，判断它靠什么火（选题人设先于制作）；同题跟风号已挤满就只偷内核换变量
  2. 节拍映射：原片拆成节拍表，A 版照事件链换角色台词，B 版只改评审定下的一个点
  3. 做角色：图像模型画草稿（同组角色画一张图保统一）→ `python -m pixel_diary.sprite` 压像素 → `faces.py` 画表情差分
  4. 写分集 JSON → `python -m pixel_diary build 分集.json --render out.mp4`（自动响度归一 -16 LUFS）；质检用 hyperframes snapshot 抽帧对比原片
- **安装**：`git clone https://github.com/garycaogan/pixel-diary.git`（MIT；需 Python + HyperFrames；配套 creator-workbench 二创工作台）
- **怎么用它搞钱**：复制"AI 接管账号"模式做垂类养成号（B 站案例：6 条视频破 100 万、3.6 万粉）：一条 1 小时多、成本不到 2 块钱，矩阵号放大
- **来源**：[garycaogan/pixel-diary](https://github.com/garycaogan/pixel-diary) · ⭐10（2026-10-23 新库；MIT，附真实爆款数据：B 站 3 天 100 万播放）

### ffmpeg-skill
- **一句话**：给 coding agent 的本地视频剪辑工具箱：42 个 FFmpeg 工具+MCP server，裁剪拼接、调音量、压字幕、抽帧、响度归一化、平台导出全覆盖，纯本地跑不花钱——适合要把剪辑做成自动化流水线的人。
- **核心用法**：
  1. 先 `probe.py` 量输入（时长/帧率/分辨率/编码），从真实数字做计划，不猜
  2. 能无损就不重编码：`cut.py`/`loudness.py` 默认流拷贝；三步以上用 `render.py` + project.json
  3. 链式顺序：调色→剪切→拼接→去静音→适配画幅→字幕/叠加→混音→响度→导出；`check.py OUTPUT --platform X` 按目标平台验收
  4. 看图确认：`look.py OUTPUT --tiles 3x2` 抽帧看，探针看不见字幕压没压上
- **安装**：`npx ffmpeg-skill doctor`（需 Python 3.10+、本地 FFmpeg；MCP 接入见仓库）
- **怎么用它搞钱**：做"AI 剪辑代工"：口播/知识视频的批量剪辑按条收费，本地 FFmpeg 零边际成本
- **来源**：[kajisho5/ffmpeg-skill](https://github.com/kajisho5/ffmpeg-skill) · ⭐2048（2026-10-23；MIT）

### sugarforever/boring-video-studio（视频策划全链路：选题到成片）
- **一句话**：一套视频策划 Agent Skill 组合：boring-video 把选题变成可执行方案（选题研究→成文→节拍→口播稿→分镜→故事板），再交给 HyperFrames 做生产渲染；另含 verysmallwoods-video 完整发布工作流（封面/平台文案/博客/社媒）——适合做知识/口播类视频、想把"选题到发布"装进终端的人。
- **核心用法**：
  1. 一行安装：`npx skills add sugarforever/boring-video-studio --skill setup-boring-video-skills boring-video develop-topic to-article to-spec-beats to-narration to-scenes to-storyboard to-video record-terminal`
  2. 喊 `$boring-video` 丢选题或源文档：先定论点论据边界（develop-topic），再写内容母稿（to-article），每一步都要你点头才往下走
  3. 节拍→口播→分镜→故事板：to-spec-beats 定学习节奏，to-narration 写口播稿（不加新料），to-scenes/to-storyboard 出可执行的镜头方案
  4. 交给 HyperFrames 成片：`npx hyperframes doctor` 先验环境；配 ListenHub TTS 可顺手出配音+字幕
  5. 发活用 verysmallwoods-video：视频、封面、平台文案、博客、社媒帖一条龙
- **安装**：`npx skills add sugarforever/boring-video-studio --skill setup-boring-video-skills boring-video develop-topic to-article to-spec-beats to-narration to-scenes to-storyboard to-video record-terminal`
- **怎么用它搞钱**：接"知识视频代策划"单：选题→成片方案一条龙；或自己批量产口播视频跑流量，口播稿调教是差异化卖点
- **来源**：[sugarforever/boring-video-studio](https://github.com/sugarforever/boring-video-studio) · ⭐184（2026-10-24；MIT，@verysmallwoods 日常在用、口播稿去 AI 味调教实证）

### xixihhhh/ai-short-drama-skill（Dramake：文字到 AI 短剧成片）
- **一句话**：把一句话点子、故事、小说、剧本串成可理解、可衔接、可发布的 AI 短剧：故事诊断→剧本→角色母版→分镜→模型与费用路线→配音→质检一条线，适合不会编剧分镜也想做短剧的人
- **核心用法**：
  1. `npx skills add xixihhhh/ai-short-drama-skill --skill dramake`，把故事直接交给 Agent（点子/小说/剧本/已有素材都行）
  2. 先建生产简报：渠道/画幅/时长/受众/模型与预算上限/对白策略，project-state.md 是唯一生产状态机
  3. 按十条铁律走：父段通过剧情/身份/物理/声音检查前不生成下一段；静音观看也要能看懂因果；身份/服装/道具/轴线全程锁定
  4. 模型选路：Wan 3、Seedance 2.5/2.0/Fast、MiniMax H3 按场景选，15–30 秒长段优先，费用路线先算再生成
  5. 交付前冷观众验收+抽帧实查：没实际看过听过抽帧检查过的素材不算通过
- **安装**：`npx skills add xixihhhh/ai-short-drama-skill --skill dramake`
- **怎么用它搞钱**：接 AI 短剧代制单（抖音/红果短剧按集收费，剧本+分镜+成片一条龙比单卖提示词好报价）；或自己跑短剧矩阵号，同一套母版换故事批量出集吃流量/分账
- **来源**：[xixihhhh/ai-short-drama-skill](https://github.com/xixihhhh/ai-short-drama-skill) · ⭐78

### muxia0396/novel-to-ai-short-drama-skill（小说改编导演台本）
- **一句话**：把小说/网文/故事片段改编成按秒闭合的 AI 短剧导演分镜台本：分场节拍、表演调度、镜头语言、声音设计、连续性锚点全齐，适合做网文改编短剧的人
- **核心用法**：
  1. 必填两项先确认：小说正文（或可读文件）+单集成片时长（30/60/90/120 秒），没给时长先追问不假设
  2. 建原作事实账本：人物/关系/目标/阻力/秘密/关键道具/因果链，区分原文事实与合理推断
  3. 做时长账本：先按节拍分秒，再写台词镜头，逐镜时长之和必须等于目标成片时长
  4. 输出逐镜导演台本：景别/机位/运镜起止与叙事动机/表演节拍/对白/声音/AI 生成注意点，抽象情绪拆成可执行动作
  5. 过质量闸门：时长、原作保真、空间/人物/道具连续、口型负担、单镜头动作复杂度、钩子兑现，逐项校验再交付
- **安装**：`git clone https://github.com/muxia0396/novel-to-ai-short-drama-skill.git ~/.codex/skills/novel-to-ai-short-drama`（README 官方安装方式，Codex）
- **怎么用它搞钱**：接小说改编短剧分镜单（网文作者/短剧团队按集付分镜费）；或把网文 IP 快速改编成短剧投红果/抖音，用分镜台本直接对接生成管线
- **来源**：[muxia0396/novel-to-ai-short-drama-skill](https://github.com/muxia0396/novel-to-ai-short-drama-skill) · ⭐32

### YvonneMovingon/short-drama-skills（短剧 prompt 规则 7 件套）
- **一句话**：LuxReal 内部短剧管线沉淀的 7 套 prompt 规则：剧本拆分镜、情绪刻画、动态描述、连贯拆分、单视频润色、高能/慢节奏润色，适合已有剧本、缺分镜方法的人
- **核心用法**：
  1. 剧本先走 01 通用叙事拆解：拆成带景别/运镜/角度/时长预估的结构化分镜序列
  2. 按戏选刻画文件：情绪戏走 02 深度情绪刻画，动作戏走 03 详细动态描述，多段连贯走 04 按剧情连贯拆分副本
  3. 单条视频提示词先走 05 润色；要爆点走 06 高能戏剧化润色，要质感走 07 慢节奏细腻质感润色
  4. 输出直接接视频生成工作流（Seedance/可灵/MiniMax 等提示词），不依赖特定 Agent
- **安装**：`git clone https://github.com/YvonneMovingon/short-drama-skills.git`，取 skills/ 下对应 prompt.md 贴进 LLM 用（README 官方用法）
- **怎么用它搞钱**：接短剧剧本拆分镜单（按集收拆分镜费）；或把拆分镜变成自己的短剧生产 SOP，批量出集降本
- **来源**：[YvonneMovingon/short-drama-skills](https://github.com/YvonneMovingon/short-drama-skills) · ⭐96

### gnipbao/codex-whiteboard-video-skill（本地白板手绘视频）
- **一句话**：Codex 调用本地白板引擎，把图片/SVG/线稿/脚本转成白板手绘视频，30 种内置视觉风格可选，适合做知识讲解/口播号的人
- **核心用法**：
  1. 先装引擎再装 Skill：`python3 -m pip install "git+https://github.com/gnipbao/whiteboard-video-engine.git"`，再把本仓库 clone 到 ~/.codex/skills/whiteboard-video
  2. `python3 ~/.codex/skills/whiteboard-video/scripts/whiteboard_cli.py doctor` 验 wrapper 通不通
  3. 在 Codex 里点名 Skill：给输入图+时长（如 15 秒），指定线稿细节（rich）与手势风格，引擎做笔画追踪与合成
  4. 从 30 种内置风格里选/推荐/扩展配方，输出成片 MP4
- **安装**：`python3 -m pip install "git+https://github.com/gnipbao/whiteboard-video-engine.git"` + `git clone https://github.com/gnipbao/codex-whiteboard-video-skill.git ~/.codex/skills/whiteboard-video`
- **怎么用它搞钱**：接白板讲解视频单（知识付费/企业培训/科普号按条收费，本地渲染无模型按量成本）；或自己做白板知识号，图片转视频批量产
- **来源**：[gnipbao/codex-whiteboard-video-skill](https://github.com/gnipbao/codex-whiteboard-video-skill) · ⭐343

### tuzhechen2005/opus-video-skills（Opus 5.5 纯代码做视频：水彩动画+动态字体）
- **一句话**：Claude Opus 5.5 纯代码做视频的两个风格 skill：手绘水彩动画与动态字体 showreel，全程零视频生成模型、每帧都是时间的纯函数，适合要零模型成本出片的人
- **核心用法**：
  1. 按风格选 skill：手绘水彩动画走 painted-animation，动态字体作品集走 kinetic-reel
  2. 流程固定：分镜→动画→评审→音乐→终编码，画面与音乐全由代码程序化生成（p5.js/three.js/WebGL）
  3. 音乐卡点：按实测节拍剪辑，歌词视频带逐词卡拉 OK 字幕
  4. 渲染：无头 Chrome 渲染 + ffmpeg 编码成片，不依赖任何生图/生视频模型
- **安装**：`/plugin marketplace add tuzhechen2005/opus-video-skills` 后 `/plugin install painted-animation@opus-video-skills` / `/plugin install kinetic-reel@opus-video-skills`（README 官方插件方式）
- **怎么用它搞钱**：接纯代码动画单（歌词视频/作品集 showreel/品牌短片，零模型成本=报价全是利润）；或把水彩/字体两套风格做成模板包按套卖
- **来源**：[tuzhechen2005/opus-video-skills](https://github.com/tuzhechen2005/opus-video-skills) · ⭐398

### makevoid/motion-graphics-music-video-skill（Opus 5.5 音乐 MV 全流程）
- **一句话**：一首歌+一句创意提示词，Opus 5.5 出完整音乐 MV：角色/画面用 GPT 生图、MiniMax H3 做动画、p5.js 做动效，适合做音乐人 MV/翻唱视频的人
- **核心用法**：
  1. 插件装好并配好 Fal API key：`claude plugin marketplace add makevoid/motion-graphics-music-video-skill` 后 `/plugin configure` 填 key
  2. 给一首歌+创意提示词，Agent 先出角色/场景方案等你批准再动手
  3. 分波次生成评审：2→3–4→4–8→6–10 轮次推进，效果不好就地改、不硬凑
  4. 成片 MP4 落 output 目录；成本先算清：约 $30 Fal 额度 + 约 3M Opus tokens / 3 分钟歌
- **安装**：`claude plugin marketplace add makevoid/motion-graphics-music-video-skill` 后 `claude plugin install motion-graphics-music-video@makevoid-music-video --scope user`（需 Fal API key）
- **怎么用它搞钱**：接音乐人 MV 代工单（独立音乐人/翻唱号按支收费，成本透明好报价）；或自己做 MV 矩阵号吃音乐流量
- **来源**：[makevoid/motion-graphics-music-video-skill](https://github.com/makevoid/motion-graphics-music-video-skill) · ⭐187

### video-use（对话剪片：素材丢进去，聊着剪出成片）
- **一句话**：把原始素材丢给 Claude Code，用对话剪片：去口头禅/死区、自动调色、烧字幕、并行动画叠加，剪完自检才交片——适合有口播/教程/访谈素材但不想自己剪的人
- **核心用法**：
  1. 素材丢进文件夹，用仓库 setup prompt 让 Agent 按 install.md 装好 ffmpeg、注册 skill、配 ElevenLabs key
  2. 先聊后剪：Agent 从逐词转写稿（takes_packed.md）出发，按说话边界和静音断点给出剪辑策略，你点头后才动手，绝不先斩后奏
  3. 剪辑全包：删嗯啊/假起头和空隙、每段自动调色、每个切点 30ms 音频淡入淡出防爆音、按你的风格烧字幕（默认双词大写分块）
  4. 动画并行做：HyperFrames/Remotion/Manim/PIL 四路子 Agent 各做一种叠加动画，最后拼进成片
  5. 交片前自检：每个切点边界都渲染自查一遍，会话记忆存 project.md，下周接着剪不用重讲
- **安装**：把仓库 setup prompt 粘贴给 Claude Code（按 install.md 装 ffmpeg、注册 skill、配 ElevenLabs key）
- **怎么用它搞钱**：接口播/课程/播客切片剪辑单：按条收费；或给客户做周更剪辑包，project.md 记忆让续单零磨合
- **来源**：[browser-use/video-use](https://github.com/browser-use/video-use) · ⭐29832（2026-10-08 更新，MIT；X 8 视频 Skill 合集推荐）

### BaoCut（可编辑视频：转录/双语字幕/翻译配音/剪辑一条龙）
- **一句话**：以“可编辑视频”为中心的剪辑 Agent：转录、字幕、翻译、配音、剪口播、切短视频都在同一条时间线上改，改完再导出——适合做双语视频、翻译视频、口播剪辑的人
- **核心用法**：
  1. 先装 BaoCut App（macOS/Windows），再把仓库 skills/baocut 交给 Agent；经命令行 baocut 或 MCP 操作同一套目录
  2. 建可编辑视频：转写后建原文字幕层，译文/双语字幕逐句另起一层，词的时间戳不动，校对只改错字术语标点
  3. 翻译配音：先自己逐句翻译，再按译文逐句合成放上配音轨；说话人按声纹区分，凭证据起真名、你确认后写回
  4. 剪辑成片：剪口播、切短视频、分章、总结写稿、从链接下载、压缩转码都在时间线上做，文件（字幕/文稿/音频/成片）都从视频导出
  5. 人机共编：你和 Agent 共用同一编辑器，你随时可手工改，编辑器状态会同步给 Agent
- **安装**：下载 BaoCut App（https://baocut.com，macOS/Windows）+ 把仓库 skills/baocut/SKILL.md 交给 Agent（README 官方方式）
- **怎么用它搞钱**：接双语视频/翻译视频单（老演讲、课程、访谈翻成双语画报是 X 上已验证的需求）；或做“一句话出双语视频画报”服务，按条收费
- **来源**：[JimLiu/baocut](https://github.com/JimLiu/baocut) · ⭐1471（2026-10-26 更新；⚠️ LICENSE 文件存在但 SPDX 未识别，商用前请确认授权；X @huangyun_122 实测推荐，需装 BaoCut App）

### html-video（HTML 写代码出视频：文章/仓库链接一键成片）
- **一句话**：把 HTML/CSS/数据变成真实 MP4 的本机渲染器：粘贴文章或仓库链接、或一句话描述，Agent 选模板、逐帧改文案、加 AI 配乐，本地出片不按次收费——适合不会剪辑、想用代码批量做知识/产品视频的人
- **核心用法**：
  1. 本机装好：pnpm install + pnpm -r build，起 studio（http://127.0.0.1:3071），先 `npx playwright install chromium` 装浏览器引擎
  2. 选输入：直接描述、或粘贴文章链接/GitHub 仓库，Agent 按意图搜模板（search-templates --intent），21 个模板覆盖数据图/产品/时间线等
  3. 逐帧改：在 studio 里改每帧文案、换模板、加配乐，14 种 Agent 后端自动识别（Claude Code/Cursor/Codex/Gemini 等）
  4. 本地渲染：无头 Chromium 逐帧录制 + ffmpeg（libx264）编码成 MP4，无按次费用、无厂商锁定
  5. 可选 AI 配乐：AI 音乐 + 旁白，成片直接导出
- **安装**：`git clone https://github.com/nexu-io/html-video.git && pnpm install && pnpm -r build` 后 `node packages/cli/dist/bin.js studio`（README 官方方式；需先 `npx playwright install chromium`）
- **怎么用它搞钱**：接知识视频/产品介绍批量单：文章转视频、仓库转演示视频，改字就重渲染，边际成本为零；或卖“链接→视频”月包
- **来源**：[nexu-io/html-video](https://github.com/nexu-io/html-video) · ⭐4754（2026-06-21 更新，Apache-2.0）

### agent-caption（本地精准字幕：强制对齐时间轴，绝不漂移）
- **一句话**：本机给任何视频/音频加精准字幕：词来自语音识别、时间来自波形强制对齐，字幕永不早晚漂移，多语言、支持 Hinglish/中英混说——适合做口播、课程、播客切片的人
- **核心用法**：
  1. 本机装好：Python 3.10+、ffmpeg，python setup.py 一键建虚拟环境装 WhisperX（large-v3）
  2. 识别与对齐分开：先语音识别出词，再用强制对齐定每个词在波形上的准确时间，转写有错字也不影响时间轴
  3. 多语言：默认英文，任何语言都可做，语音和歌声都支持，Hinglish/中英混说一流
  4. 全平台：Windows/macOS/Linux 都能跑，100% 本地，素材不上传云端
- **安装**：`git clone https://github.com/ahkamboh/agent-caption.git && python setup.py`（需 Python 3.10+、ffmpeg）
- **怎么用它搞钱**：接字幕外包单：口播/课程/播客切片的字幕按分钟收费，时间轴精准是卖点；或打包进剪辑服务里提价
- **来源**：[ahkamboh/agent-caption](https://github.com/ahkamboh/agent-caption) · ⭐38（2026-10-21 更新，MIT；X 8 视频 Skill 合集推荐）

### classical-poem-silk-video（古诗国风竖屏：逐句一景+毛笔字逐字题写）
- **一句话**：把整首古诗做成 1080×1920 国风动态竖屏：逐句或两句一景分镜、中国画风格分化、画中物象真实运动、毛笔字逐字题写、原环境声+BGM、成片质检——适合做国风/古诗短视频账号的人
- **核心用法**：
  1. 先读 runtime-contract 并跑 check_prerequisites.sh（装好 ImageGen、Docker 版 Gemini I2V 等前置）
  2. 读全诗定意象：标题/诗人/时代/地点/季节/时间/显性意象/情感弧线，四句以内一行一景、四句以上两句一景
  3. 分镜分化：中国画风格按场景分（水墨山水/工笔花鸟/青绿山水/绢本等），不用同一套古绸模板套全诗
  4. 运动真实化：用静态锚点限制图生视频重画，让水纹/飞鸟/马蹄/柳枝/衣袍真正动起来，保留每段原环境声
  5. 题写与质检：毛笔字逐字出现、本地 BGM 混音可选、最后整片质检后交付 MP4
- **安装**：把 README 的一句话安装提示粘贴给 Agent（自动装 skill 并校验 SKILL.md/agents/references/scripts/字体资产）
- **怎么用它搞钱**：做国风古诗账号：逐诗成片、系列化更新跑流量分成；或接“一首诗一条片”定制单，按诗收费
- **来源**：[Mr-funny/hbg-classical-poem-silk-video](https://github.com/Mr-funny/hbg-classical-poem-silk-video) · ⭐373（2026-08-03 更新，MIT；需 Docker + Gemini I2V 前置）

### andyhuo520/digital-human-koubo（数字人口播：一张照片+一句话出片）
- **一句话**：一张照片加一句话出数字人口播成片：写稿、分段、对口型生成、包装剪辑全包，适合做口播、带货、解读号、真人不出镜的人
- **核心用法**：
  1. 先定风格再开工：按内容在 5 档里选（小林式解说/网红花字口播/发布解读/保姆级教程/多主播多语言），风格、比例时长、花字强度、主播一次定进 brief.json
  2. 写稿按 10 秒切段：每段一句或两句约 40-55 字，标 full/pip/vlog/depth 镜头；生成前先报段数、秒数、预估 credits、余额，用户点头才生成（720p 约 17 credits/秒、480p 约 10 credits/秒）
  3. 走 Renoise MCP 分段生成：每 10 个任务一批，下载用多段并发加断点续传、ffmpeg 解码校验；逐段回听（whisper 转写比对文稿）、每段抽 4 帧查烧字幕，有问题只重拍那段
  4. 套 48 个包装组件出片：开场钩子、数字钉子、文字在人身后、证据截图、地图路线、弹幕、投票、复盘板，Remotion 拼接、loudnorm -16 出片
  5. 红线：成片标“内容由 AI 数字人演绎”；用户本人形象只用在自己的片子；不冒充真人、不学真实创作者的脸和声音
- **安装**：`git clone https://github.com/andyhuo520/digital-human-koubo.git` 后把 skills/digital-human-koubo 拷进 ~/.claude/skills/，再按 README 接 Renoise MCP（需 Renoise 账号，credits 按量付）
- **怎么用它搞钱**：接“数字人口播代做”单：一张客户照片加一句话卖点出 30-120 秒带货/解读片，按条收费；或自己起矩阵号，同一数字人多风格复用，边际成本只剩 credits
- **来源**：[andyhuo520/digital-human-koubo](https://github.com/andyhuo520/digital-human-koubo) · ⭐761

### eternityspring/shuohao-skills（AI 短剧制作 7 件套：小说到分镜）
- **一句话**：小说到可拍摄物料的短剧全链路 skill 组：大纲、角色、美术、剧本、开场走位、分镜，适合做 AI 短剧、小说改编的人
- **核心用法**：
  1. 按管线顺序跑：novel-outline 定改编大纲 → novel-characters 立角色卡 → novel-art 出场景与道具设定 → novel-script 写剧本 → novel-staging 定每场开场站位 → novel-storyboard 出分镜，character-refs 单独出角色参考图
  2. 每步产物是结构化文件，上一步的文件就是下一步的输入，不靠口头传话；场景图里能站能坐的物件就是走位依据，没有场景图时走位标“暂定”
  3. 装一次长期用：clone 后 ./scripts/install.sh 软链全部 skill 进 Claude Code/Codex，git pull 即更新；单装某一个就 ./scripts/install.sh novel-characters
  4. 零 API 依赖：脚本只用 Node 18 标准库，不装 npm 包；不走 API key，用当前会话额度；只有 character-refs 需要出图通道（自建 ComfyUI / Codex 出图 / OpenAI API / 自定义命令四选一）
- **安装**：`git clone https://github.com/eternityspring/shuohao-skills.git && cd shuohao-skills && ./scripts/install.sh`（需 Node 18+）
- **怎么用它搞钱**：接“小说改短剧”代制单：大纲到分镜一套交付，按集/按本收费；或自己跑短剧矩阵号，7 件套是可复用的生产管线不是一次性 prompt
- **来源**：[eternityspring/shuohao-skills](https://github.com/eternityspring/shuohao-skills) · ⭐5418

### konlu/story-studio（故事工坊：历史/人物故事视频号一条龙）
- **一句话**：历史与真实人物故事的中文视频号内容一条龙 skill：选题核实 → 3 秒钩子 → 爆款正文 → 豆包配音 → 本地毫秒级字音对齐 → 三套画风分镜生图 → pyJianYingDraft 导出带推拉运镜的剪映草稿，适合做视频号历史/人物故事带货的人
- **核心用法**：
  1. `git clone https://github.com/konlu/story-studio.git ~/.codex/skills/story-studio`（macOS/Linux；Windows 为 `$HOME\.codex\skills\story-studio` + install.ps1/install.bat），首次调用触发依赖检查
  2. 开关制：只开请求的阶段——write（选题/核实/写稿/钩子/字数检查）/ illustrate（分镜/生图）/ draft（对齐/时间轴/运镜/导出草稿），不默认全开
  3. Audio-First：先出音频再排分镜，约 8 秒/图；三画风（厚涂历史漫画/黑白纪实/历史写实）；剪映草稿平滑推拉约 16–20 秒走 12%、切点缩放 1.28x/1.50x
  4. 先核实生平关键时间点与数字再写钩子：3 版黄金开头，字数误差 ±5%；依赖缺失时由 Agent 按 bootstrap 脚本配 Python/Node/FFmpeg/Coli/剪映，缺授权才问用户
  5. 只出分镜/提示词时不授权生图，缺图交付已完成部分和缺口；不把创作产物写进技能目录
- **安装**：`git clone https://github.com/konlu/story-studio.git ~/.codex/skills/story-studio`（或 Release.zip + install.bat/install.sh）
- **怎么用它搞钱**：视频号历史/人物故事挂车带货（图书、滋补健康品）或接同类账号代运营：一条龙省掉选题/写稿/配音/分镜/剪辑多道人工，同一管线多账号复用
- **来源**：[konlu/story-studio](https://github.com/konlu/story-studio) · ⭐175（⚠️ 带货与播放数据为作者自述未核验；克隆音色须自备授权音频，勿用他人音频克隆）

### maxazure/video-editing-skill（小红书/抖音/视频号三平台剪辑流水线）
- **一句话**：为小红书/抖音/微信视频号调过参的中文剪辑大流水线：素材导入→口播重组→平台守门→渲染→三平台导出一条龙，80+ 条平台雷区 lint + 全程 approval gate——适合做口播/教程/访谈/播客短视频、要稳定过审出片的人。
- **核心用法**：
  1. `git clone https://github.com/maxazure/video-editing-skill ~/projects/video-editing-skill`，按 README 配 FFmpeg + Whisper/FunASR（Apple Silicon 用 mlx-whisper、NVIDIA 用 faster-whisper）
  2. 先跑素材导入与 conform：VFR 转 CFR、黑场/黑边处理、多机位同步，全部带 proof/gate，不凭感觉剪
  3. 转写后走语义审校：词级时间戳 + 幻觉疑点回听 + 最少补丁验证，再定剪辑决策
  4. 出片前过三道门：内容守门（80+ 平台雷区 lint）→ 事实收据（claim 配 URL/截图）→ 审批收据（渲染后任何改动都让旧审批过期重审）
  5. 发布只出上传包不直传：`publish_package.py` 只合成平台视频/封面/字幕/文案 + gate 状态，不调用平台 API，手工上传或交外部 connector
- **安装**：`git clone https://github.com/maxazure/video-editing-skill ~/projects/video-editing-skill`（需 FFmpeg + Python，⚠️ 该仓暂无 LICENSE）
- **怎么用它搞钱**：接口播/教程类剪辑代做单：平台 lint + 审批收据就是“一次过审”的谈单证据；或自己跑三平台矩阵号，同一管线换平台参数即复用
- **来源**：[maxazure/video-editing-skill](https://github.com/maxazure/video-editing-skill) · ⭐205

### pycodebr/heditor（风格化创意剪辑：每条片子单独设计）
- **一句话**：把口播/课程/播客录像剪成竖屏短视频或长片的创意剪辑 CLI：30+ 命名风格（电影/游戏/预告片/纪录片…）+ 逐词字幕 + 声音设计 + 钩子换头测试，HyperFrames/GSAP 本地渲染——适合不满足于模板剪辑、要“每条都不一样”的创作者。
- **核心用法**：
  1. `npx skills add pycodebr/heditor -g` 后跑 `bash <skill>/scripts/setup.sh`，`heditor doctor` 必须报 ready；首次填 `~/.heditor/brand.json`（名字/handle/配色/logo）
  2. 先定模式：固定风格（`heditor styles` 查表）/ 创意模式 / 创意+参考（如 GTA 6 风）/ 长片模式 / 原始素材先 `heditor triage`（读口误、重录、破第四墙的剪辑备注）
  3. 剪辑按“每条单独设计”走：风格是视觉语言不是模板，同一批两条长得一样算没做完
  4. 已跑量视频换钩子不用重剪：`heditor splice` 只换开头、片体原样，A/B 测新开头
  5. 可选 HeyGen 数字人分身当素材源（需自有账号与授权），或 Mixkit 免费 B-roll（已核 license 并记录来源）
- **安装**：`npx skills add pycodebr/heditor -g` 后按 README 跑 setup.sh（需 FFmpeg/Node/Python + Chrome；⚠️ LICENSE 文件存在但 SPDX 未识别）
- **怎么用它搞钱**：接高单价创意剪辑单：风格库 + 钩子换头测试是“不像模板”的溢价点；或给课程/播客客户做长片 + 竖屏切片打包收费
- **来源**：[pycodebr/heditor](https://github.com/pycodebr/heditor) · ⭐103

### chang416/cutcraft（对话式剪片：字幕先看图再开剪）
- **一句话**：用对话把 raw 素材剪成成片的中文剪辑 skill：先检查环境、先看片、先出三套字幕预览图让你选、改逐字稿可逆、成品与过程分开交付——适合怕“剪完不满意返工”、要逐句改稿的口播/短影音作者。
- **核心用法**：
  1. 首次跑 readiness gate：`python3 helpers/check_environment.py`，缺依赖先停下来给官方安装指引，不静默装东西
  2. 盘点素材并转写：先看代表性画面，再把所有创意问题一次问清，不边剪边问
  3. 字幕先看图再开剪：生成三套字幕预览图（推荐/干净叙事/大胆社交），按“往下 4%”“字大 15%”这类口头调整直接改
  4. 成片只放 `成品/`（`<项目>_final.mp4` + 逐字稿 md + srt），预览/片段/EDL/校验全放 `過程/`，交付物一眼分清
  5. 改稿不用重转写：说“第 18 句改成……”即对 master.srt 打补丁、重渲染、重校验，时间轴不动
- **安装**：`git clone https://github.com/chang416/cutcraft` 后把 skills/cutcraft 拷进 ~/.claude/skills/（MIT；转写可用本地 Whisper，ElevenLabs key 只放 ~/.config/cutcraft/.env 且权限 600）
- **怎么用它搞钱**：接口播/知识类剪辑单：三套字幕预览 + 逐句改稿是“改到满意为止”的服务卖点，返工成本低；或做剪辑教学，流程本身就是 SOP
- **来源**：[chang416/cutcraft](https://github.com/chang416/cutcraft) · ⭐53

### Pluviobyte/awesome-talking-head-skills（口播博主动作蒸馏：不露脸数字人口播）
- **一句话**：把 5 位抖音口播博主的出镜动作逐帧拆成 Agent Skill：手势词汇表、节拍规则、机位、开头结构、禁止动作，配一个“拆新博主”的 analyzer skill——适合做不露脸口播数字人、总被手崩/表情脱节卡住的人。
- **核心用法**：
  1. 按难度选风格：求稳选李一帆（表情主导、手基本不入画、崩手风险最低）或大师（证据先行）；要活力借秋芝的 3–4 个标志手势；长教程目录式开场用木子；财经/讲故事用小Lin说（素材冷开场 + 小窗配音 + 情绪句回全屏）
  2. 复制对应 `skills/talking-head-<slug>/` 到 Agent 的 skills 目录，对 Agent 说“用某某风格，给这段台词写一份数字人动作说明书”
  3. 动作只写可执行的：哪只手、什么形状、在什么高度、持续多久、卡在哪个词上；不写“自然、生动”这类模型无法执行的词
  4. 生成描述里写死禁止动作（如手不过下巴和肩、不频繁耸肩），并写明“双手在画面下沿以外”防模型自加手势
  5. 想拆新博主走 `talking-head-analyzer`：选 4 条本人棚拍口播、只截开头 25 秒、观察与建议分开写
- **安装**：`git clone https://github.com/Pluviobyte/awesome-talking-head-skills` 后把 `skills/talking-head-<风格>/` 拷进 Agent 的 skills 目录（MIT）
- **怎么用它搞钱**：接不露脸口播数字人代做单：动作说明书 + 难度分档（低/中/高）就是可报价的交付标准；或自己跑口播矩阵号，同一说明书换台词和 B-roll 即复用
- **来源**：[Pluviobyte/awesome-talking-head-skills](https://github.com/Pluviobyte/awesome-talking-head-skills) · ⭐56（⚠️ 2026-10-27 新库，X 原帖 @Pluvio9yte 10-28 20:26 北京，22.8K 浏览/224 收藏；红线已在条目中注明：只学动作节奏、不描述长相服饰、不把样本片段喂给生成模型、参考图只用自有或已授权形象、发布按平台要求标注 AI 生成）

### 10291124jcjc-dotcom/ai-anime-series（AI 动画单元剧：一句话出一集）
- **一句话**：固定几个原创角色、立好 IP 后，每集只说一句主题就能出一集：角色设定图 + 宫格故事板 + 即梦 Seedance 2.5 一次生成——适合想做 AI 动画号、要系列化不断更的人。
- **核心用法**：
  1. 立 IP：剪影差别大、每人一个招牌能力，出角色设定图（三视图 + 表情 + 动作 + 剪影）
  2. 写一集：开场 → 冲突 → 反转 → 反击 → 结尾笑点，先出镜头表，你确认后再开工
  3. 拼提示词：出场角色几个、@图 编号就排几个；时长多长、宫格就几格；秒数自动对齐（30 秒默认 9 格、每格约 3.3 秒；1 分钟上下两段各 9 格拼起来）
  4. 即梦画布：框选设定图出黑白素描宫格故事板，再用 Seedance 2.5 全能参考一次出视频（先 480p 验证）
  5. 检查成片、改单个情节、记录已拍、拼合集：脚本负责拼宫格、抽帧检查、两段拼接、换段、拼合集
- **安装**：`git clone https://github.com/10291124jcjc-dotcom/ai-anime-series.git ~/.claude/skills/ai-anime-series`（需即梦会员 + Python 3.9+、ffmpeg、pillow；⚠️ LICENSE 文件存在但 SPDX 未识别）
- **怎么用它搞钱**：做 AI 动画单元剧账号：固定角色 + 一句话一集是可复制的连载模式，涨粉后接商单 / 带货；或给客户做系列动画外包，角色设定与故事板方法论就是交付物。
- **来源**：[10291124jcjc-dotcom/ai-anime-series](https://github.com/10291124jcjc-dotcom/ai-anime-series) · ⭐179（X 原帖 @DDJCXX 2026-10-29 12:51 北京；“不到两个月百万粉”为帖内引用的抖音案例说法，未独立核验；仓内实证为汤圆和油条第 1 集 30 秒成片）

### topo-ai/ai-video-skills（AI 资讯快报 + 音效 + 简笔画：HyperFrames 垂类工作流 5 件套）
- **一句话**：基于 HyperFrames 的垂类视频工作流合集：AI 资讯快报、产品介绍、音效方案、简笔画动画、Anime.js 适配——适合想把“想法→脚本→画面→音频→成片”沉淀成固定流程的创作者与小团队
- **核心用法**：
  1. `npx skills add topo-ai/ai-video-skills`，按触发词点名子 skill（如“AI快报”“音效”“简笔画动画”）
  2. 资讯快报走 5 步：新闻检索筛选→真实素材下载→edge-tts 口播→HyperFrames 页面编排→渲染导出；默认 16:9，逐句口播字幕跟随配音、每屏 1–2 行每行 ≤22 字
  3. 音效走两条路：免费库搜索下载（Freesound / Mixkit / Pixabay / BBC SFX，按文件核许可）或 Web Audio API 合成，无需外部文件
  4. 简笔画动画：具象物体先联网搜参考图临摹线稿（逼真可辨、拒绝默认抽象），GSAP 主时间线 + Anime.js 微动效分工，`npm run check` 抽检闭环
  5. 产品介绍：官网信息提炼→叙事结构→成片节奏，同一流程换产品即出新片
- **安装**：`npx skills add topo-ai/ai-video-skills`（HyperFrames 渲染环境见仓内说明；作者为小红书“拓扑同学”）
- **怎么用它搞钱**：接 AI 资讯快报 / 产品介绍视频外包：检索→口播→成片一条线可按周交付；或做自己的资讯号，同一流程换选题即出新片，边际成本低
- **来源**：[topo-ai/ai-video-skills](https://github.com/topo-ai/ai-video-skills) · ⭐49 MIT（2026-05-18 推送，一年内；资讯快报 / 音效 / 简笔画 3 个 SKILL.md 逐个读过确认干货，约 1.5 万 / 1.1 万 / 0.6 万字；注：与库内 HyperFrames 引擎条目是“引擎 vs 垂类工作流”关系，不重复立引擎条目）

## 文案钩子（9 个）

### shangdan-post-skill
- **一句话**：给接商单的创作者的"商单前置质检员"：新单先调历史经验拆 Brief、给 3 组策划方向+写好的开篇钩子、发布前自检、复盘归档——解决商单博主"每单从零起步"的重复劳动。
- **核心用法**：
  1. 记录→提炼→新单先检索→完工再回存：经验存本地 Markdown 或接 EverOS 记忆产品
  2. 新单到手走前置三步：调取创作者档案+品牌历史打法/驳回记录→按 9 项模板拆 Brief（不猜不编）→给 3 组策划方向+每组 1 个写好的开篇钩子拍板
  3. 钩子标准：前两句点名人群+说清价值+留悬念，共鸣优先，禁用灾难化夸大
  4. 成稿按"钩子—中段揭晓—结尾回收"写，发布前过自检清单，复盘归档沉淀（品牌禁词/法务审核/驳回根源变案例）
- **安装**：`git clone https://github.com/modengsir/shangdan-post-skill.git`（MIT；记忆层可选本地 Markdown 或 EverOS）
- **怎么用它搞钱**：商单博主的接单 SOP：Brief 拆解+钩子一次成型，减少改稿轮次；经验库越用越值钱，是个人护城河
- **来源**：[modengsir/shangdan-post-skill](https://github.com/modengsir/shangdan-post-skill) · ⭐1（2026-10-23 新库待观察；MIT，X 原帖 33 回复/1717 浏览验证需求）

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
- **来源**：[kangarooking/viral-copywriting-skill](https://github.com/kangarooking/viral-copywriting-skill) · ⭐74

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
- **来源**：[kangarooking/viral-copywriting-skill](https://github.com/kangarooking/viral-copywriting-skill) · ⭐74

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
- **来源**：[kangarooking/viral-copywriting-skill](https://github.com/kangarooking/viral-copywriting-skill) · ⭐74

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
- **来源**：[mikiarlo3/ai-copywriter](https://github.com/mikiarlo3/ai-copywriter) · ⭐1232

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
- **来源**：[sergebulaev/tiktok-skills](https://github.com/sergebulaev/tiktok-skills) · ⭐90

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

### rediumvex/viral-hooks-skill（100 条钩子公式 × 10 种心理触发）
- **一句话**：短视频钩子公式库：100 条公式按好奇/反常识/权威/情绪/清单/提问/故事/否定/具体/自白 10 种心理触发分类，每次给脚本配 3 条不同类别的钩子——适合每条视频开头都要“3 秒留人”的短视频作者。
- **核心用法**：
  1. 丢脚本或只给话题：只有话题时先问一句受众/角度，再动手
  2. 先判脚本的情绪节拍属于 10 触发中的哪一类，再从 `hooks-database.md` 里挑
  3. 一次出 3 条且类别要混搭：一条止滑类（否定/具体/提问）+ 一条留存类（故事/自白/情绪）+ 一条自由选，两条同类钩子等于白给
  4. 填空只填脚本里的具体话题/数字/痛点/受众，每条钩子压到 12 词以内，并按平台调性出中文版（TikTok/IG 偏口语、X 偏短促反常识、YouTube 偏标题式）
  5. 每条附类别标签和一句“适合什么”，最后给一句“先用哪条、为什么”，方便 A/B 测
- **安装**：`npx skills add rediumvex/viral-hooks-skill`
- **怎么用它搞钱**：接短视频脚本/钩子代写单：100 公式 × 10 触发是可量化的交付物；或自己做账号时每条配 3 钩子轮测，留存数据反哺选题
- **来源**：[rediumvex/viral-hooks-skill](https://github.com/rediumvex/viral-hooks-skill) · ⭐113

### hongfamonvAI/hook-lab（短视频爆款拆解：前 3 秒 Hook + 脚本结构 + 改写方向）
- **一句话**：丢一条 TikTok / Reels / Shorts 链接，它先抓数据和字幕，再拆前 3 秒 Hook、脚本结构、爆款原因，最后给 3 个适配小红书 / 视频号的改写方向并自动归档成对标库——适合做短视频对标拆解、给账号找爆款公式的人。
- **核心用法**：
  1. 装好后在 Claude Code 里跑 `/analyze <视频链接>`（TikTok / Instagram Reels / YouTube Shorts），没给链接时它会先问你要
  2. 提取：脚本调 yt-dlp 抓元数据（播放 / 点赞 / 评论 / 时长）与字幕；失败按 WebFetch → 人工粘贴文案两级回退，输出开头注明数据来源与完整度
  3. 分析（中文输出）：数据面板算互动率 → 前 3 秒 Hook 定类型（好奇缺口 / 震惊数据 / 大胆断言 / 提问 / 视觉钩子 / 打破预期）并判强度 → 脚本按 Hook → 问题 → 揭示 → 证明 → CTA 分段标节奏 → 风格 / 内容 / 情绪三组标签 → 2–3 条具体爆款原因（不许“内容好”式空话）
  4. 改写：给 3 个可落地角度，每个含一句话角度 + 写好的 Hook 示例 + 适配平台；结果自动追加到 results/analyzed-videos.md，跨视频可对比
- **安装**：`cp -r hook-lab ~/.claude/skills/hook-lab && pip3 install yt-dlp`（需本机 yt-dlp；MIT）
- **怎么用它搞钱**：接短视频对标拆解单：给客户账号或竞品爆款出“为什么爆 + 怎么改写”报告，按条或按账号包收费；自己做号时先拆 20 条同赛道爆款建结果库，选题不再凭感觉。
- **来源**：[hongfamonvAI/hook-lab](https://github.com/hongfamonvAI/hook-lab) · ⭐103

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
- **来源**：[sergebulaev/tiktok-skills](https://github.com/sergebulaev/tiktok-skills) · ⭐90

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
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐56,714

### copywriting（转化文案）

- **一句话**：写高转化营销文案的专家 skill（落地页/定价页/首页），适合卖产品、卖服务、做落地页的人
- **核心用法**：
  1. 动笔前先收四类上下文：页面目的（唯一行动是什么）、受众（痛点/顾虑/原话）、产品（差异化/证据）、流量来源
  2. 原则：清晰压倒 clever（清晰定位带来 +81% 转化）、利益压倒功能、具体压倒模糊（"每周报告从 4 小时压到 15 分钟"）、一屏只讲一个论点
  3. 写完过"去 AI 味"质检：禁"不是 X 而是 Y"翻案句、禁三段否定排比、禁"in today's fast-paced world"式 stock 开头、短文案不用破折号
  4. 缺证据就标 `[NEED: ...]`，绝不编造数据和 testimonials
- **安装**：`npx skills add coreyhaines31/marketingskills --skill copywriting`
- **怎么用它搞钱**：接落地页文案单；自己卖课/卖服务时，销售页转化率直接挂钩收入
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐56,714

### ad-creative（广告创意量产）

- **一句话**：批量生成/迭代付费广告创意（标题/描述/正文），适合投 Meta/Google/TikTok 广告的人
- **核心用法**：
  1. 四种模式：从零生成、用历史投放数据迭代、按获胜主题扩展、按平台规格校验
  2. 动手前收五类信息：平台与版位、产品与卖点、受众与认知阶段、历史数据（CTR/ROAS 哪条赢）、品牌与合规红线
  3. 核心循环：拉数据 → 找获胜模式 → 按获胜主题生成新变体 → 探新角度 → 校验规格 → 交付
  4. 覆盖 UGC/绿幕/口播/信息流等多格式，文案同样过"去 AI 味"质检
- **安装**：`npx skills add coreyhaines31/marketingskills --skill ad-creative`
- **怎么用它搞钱**：接广告代投/素材单：别人一条条写，你一次出几十条变体做 A/B 测试；自己带货时素材迭代速度就是 ROAS
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐56,714

### lead-magnets（获客钩子）

- **一句话**：设计"拿邮箱换资料"的获客钩子（电子书/清单/模板/课程），适合做私域、做 newsletter、卖课的人
- **核心用法**：
  1. 原则：只解决一个具体痛点（"怎么写出有回复的冷邮件" > "营销指南"）；钩子匹配购买阶段（认知期给教育、决策期给实施帮助）
  2. 先盘点：现有内容资产（博客/指南/数据）、内部用的模板工具、能包装的专业经验
  3. 选形态：清单/模板/速查表转化最高，别一上来就写电子书
  4. 钩子要自然导向产品试用，写完调 copywriting 写落地页、调 emails 写捕获后的培育序列
- **安装**：`npx skills add coreyhaines31/marketingskills --skill lead-magnets`
- **怎么用它搞钱**：帮客户搭"钩子→邮箱→培育→成交"漏斗收服务费；自己做号时这是涨粉最稳的路径之一
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐56,714

### pricing（定价策略）

- **一句话**：定产品价格/分档的 skill（SaaS/电商/服务都适用），适合定价拍脑袋、总被客户嫌贵的人
- **核心用法**：
  1. 三轴定价：分档含什么（Packaging）、按什么收费（用户数/用量/一口价）、收多少（Price Point）
  2. 价值定价：价格定在"次优替代品"和"客户感知价值"之间；成本只是底线不是依据；不对标竞品价格（那是抄它的战略）
  3. 核心洞察：多数"能不能便宜点"本质是"分子不够大/分母不够小"，先调价值再调价格
  4. 新品定价先定"能学到东西的价格"，跑数据再调
- **安装**：`npx skills add coreyhaines31/marketingskills --skill pricing`
- **怎么用它搞钱**：给 SaaS/知识付费做定价咨询；自己产品定价从"成本加成"换成"价值定价"，利润率直接上一个台阶
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐56,714

### offers（offer 设计）

- **一句话**：设计让人无法拒绝的 offer（服务/课程/教练/信息产品/高客单），适合卖高价但转化不行的人
- **核心用法**：
  1. 核心哲学：offer 本体比页面重要——弱 offer 配好文案慢慢爬，强 offer 配平庸文案立刻转化；多数"文案不行"本质是"offer 不行"
  2. 价值公式（Hormozi）：价值 =（梦想结果 × 感知达成概率）/（时间延迟 × 付出成本）；调四个杠杆：放大梦想、加证据与保证提概率、加速首胜、降低付出
  3. 适用：服务/课程/教练/信息产品/5K 美金以上高客单；自助 SaaS 分档订阅以 pricing 为主
  4. 设计完调 copywriting 写销售页、调 pricing 定档
- **安装**：`npx skills add coreyhaines31/marketingskills --skill offers`
- **怎么用它搞钱**：帮知识付费/教练做 offer 重构收咨询费；自己卖课时 offer 改好，转化率翻倍比投流便宜得多
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐56,714

### cro（转化率优化）

- **一句话**：按影响力排序诊断落地页的 skill，适合有流量没转化的页面
- **核心用法**：
  1. 先定三要素：页面类型、唯一转化目标、流量来源（不同来源预期不同）
  2. 按影响力顺序查：价值主张 5 秒能否看懂 → 标题是否讲清核心价值 → 是否客户语言 → 行动路径 friction
  3. 强标题公式：结果导向（"得到 X 而不用忍受 Y"）、具体数字、社交证明（"10,000+ 团队在用"）
  4. 表单 abandonment、A/B 测试想法有专门的 references 可调
- **安装**：`npx skills add coreyhaines31/marketingskills --skill cro`
- **怎么用它搞钱**：接"落地页诊断"单，按页收费；自己投流时，转化率提 1 个点等于获客成本降一截
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐56,714

### cold-email（冷邮件）

- **一句话**：写高回复率冷邮件的 skill，适合做 BD、找客户、谈合作的人
- **核心用法**：
  1. 动笔前收五样：写给谁（职位/公司/为什么是他）、要什么（回复/会议/介绍）、价值点、证据、研究信号（融资/招聘/动态）
  2. 语气像同行不像销售：多用"you"，少用"I/we"；每句必须推动回复，否则删
  3. 个性化必须连着痛点（删掉开头个性化整封还通顺 = 个性化失败）
  4. 一个低 friction 的 CTA（"值得聊聊？"），不要一上来就约会议
- **安装**：`npx skills add coreyhaines31/marketingskills --skill cold-email`
- **怎么用它搞钱**：帮 B2B/出海客户做冷启动获客；自己找商单、谈分销时，回复率就是 pipeline
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐56,714

### emails（邮件序列）

- **一句话**：搭邮件培育序列的 skill（欢迎/培育/唤醒/ onboarding），适合有名单但不会养的人
- **核心用法**：
  1. 先定序列类型（欢迎/培育/唤醒/售后/销售），再定受众触发点和转化目标
  2. 原则：一封邮件只干一件事；按生命周期查缺补漏（onboarding/留存/账单/唤醒）
  3. 写单封邮件调 copy-guidelines（结构/语气/长度/个性化字段）
  4. 和 lead-magnets 联动：钩子捕获 → 欢迎序列 → 培育 → 成交
- **安装**：`npx skills add coreyhaines31/marketingskills --skill emails`
- **怎么用它搞钱**：帮客户搭"名单→培育→复购"邮件体系收服务费；自己做私域时，邮件是复购率最高的渠道之一
- **来源**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) · ⭐56,714

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
- **来源**：[vivy-yi/xiaohongshu-skills](https://github.com/vivy-yi/xiaohongshu-skills) · ⭐506

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

### Jakeschincariol/instagram-agent-skill（Instagram 账号全链路）
- **一句话**：13 个 skill 运营 Instagram 账号：按 26 个钩子公式写 Reels 并打分、找本赛道真爆款 Reels、主页 100 分制诊断改写、周计划，还自带去 AI 味 humanizer——适合做 IG 引流/带货/出海获客的人
- **核心用法**：
  1. `git clone https://github.com/Jakeschincariol/instagram-agent-skill.git && cp -r instagram-agent-skill/skills/ig-* ~/.claude/skills/`
  2. 先跑主页诊断 skill：0-100 打分，逐项改写 bio 和置顶——主页是转化页
  3. 写 Reels 脚本：给主题，AI 按 26 个钩子公式写并打分，烂钩子不开拍
  4. 文案先过自带 humanizer：去破折号、去 AI 味词汇、去隐形水印字符，再过 5 项检查
  5. 每周跑一遍周计划 skill：固定节奏出 Reels，不断更
- **安装**：`git clone https://github.com/Jakeschincariol/instagram-agent-skill.git && cp -r instagram-agent-skill/skills/ig-* ~/.claude/skills/`
- **怎么用它搞钱**：IG 带货/引流：Reels 钩子公式+主页诊断是涨粉两件套；或接"IG 账号代运营"，周计划+文案流水线化交付
- **来源**：[Jakeschincariol/instagram-agent-skill](https://github.com/Jakeschincariol/instagram-agent-skill) · ⭐3938

### Jakeschincariol/founder-skill（创业想法验证）
- **一句话**：11 个 skill 在花大钱之前验证生意：董事会（Hormozi/Thiel/Jobs 框架）挑刺、营销总监定打法、CFO 算真实利润率、100 个买家代理跑购买场景——适合想搞副业/创业但怕踩坑的人
- **核心用法**：
  1. Claude Code 里 `/plugin marketplace add Jakeschincariol/founder-skill` 再 `/plugin install founder-skill@founder-skill`
  2. founder-board：把商业想法丢给"董事会"，按三位大佬的框架挑刺
  3. founder-consumer：起 100 个目标客户画像的买家代理，跑 100 个购买场景，看真实付费意愿
  4. founder-cfo + founder-pricing：算真实利润率和定价，不赚钱的当场毙掉
  5. 通过验证的才进 founder-launch 流程——省下几万块试错费
- **安装**：Claude Code 里 `/plugin marketplace add Jakeschincariol/founder-skill` 后 `/plugin install founder-skill@founder-skill`
- **怎么用它搞钱**：副业立项前先验证——100 买家代理≈免费用户访谈；或做"商业 idea 验证"咨询，按项目收费帮人省试错钱
- **来源**：[Jakeschincariol/founder-skill](https://github.com/Jakeschincariol/founder-skill) · ⭐906

### marswaveai/skills（一稿多发：ListenHub 内容复用包）
- **一句话**：ListenHub.ai/ColaOS 官方 skill 包：一稿多发是核心用法——一个链接拆成播客/解说视频/幻灯片/TTS 配音/图文成套出，外加声音克隆/AI 配乐——适合做小红书起号、多平台分发的人（@xoyif63862452《小红书起号：7 个 Skill 搞定运营流水线》推荐的一稿多发环节）
- **核心用法**：
  1. `npx skills add marswaveai/skills` 一行装好（MIT）
  2. 一稿多发：长图文/链接→小红书图文+短视频口播稿+播客+封面成套出，注意按平台调性调长度（小红书要短）
  3. `/podcast` 做单人/对谈/辩论播客，`/explainer` 做解说视频，`/slides` 出幻灯片
  4. `/voice-clone` 克隆自己音色成 reusable speaker，多条内容同一声音
  5. 先跑通"找资料→一稿多发→去 AI 味"最小闭环，再叠自动化（@xoyif63862452 方法论：别一次装七个）
- **安装**：`npx skills add marswaveai/skills`（需 ListenHub.ai 账号）
- **怎么用它搞钱**：做小红书/多平台起号代运营：一稿多发把"一篇稿磨三小时"压到"三十分钟量级"+多平台铺（@xoyif63862452）；或做播客/解说代做单，声音克隆是复购钩子
- **来源**：[marswaveai/skills](https://github.com/marswaveai/skills) · ⭐79

### social-auto-upload
- **一句话**：视频/图文一键分发 6 大平台（抖音/小红书/视频号/TikTok/YouTube/B 站）：统一 CLI + 18 个 Agent Skills，Codex/OpenClaw/Claude Code 直接调用——适合做内容矩阵、多平台分发的人。
- **核心用法**：
  1. `sau_commands/` 里每个平台独立命令，`uploader/` 走发布流程，日常用 GitHub Release 稳定版
  2. Agent 调用：仓库提供 18 个 skills（如 douyin-upload），skills.sh 可查，按平台装
  3. 发布=一条命令：视频+标题+标签一次推多平台；CHANGELOG 跟踪各平台接口变更
  4. 先小号实测再上矩阵号：各平台风控规则不同，分开发布节奏
- **安装**：`npx skills add dreammis/social-auto-upload`（MIT；详见仓库 README 的平台对照表）
- **怎么用它搞钱**：内容矩阵的"最后一公里"：一条视频 6 平台同步发，吃满各平台流量补贴；或打包成"代发服务"按账号收费
- **来源**：[dreammis/social-auto-upload](https://github.com/dreammis/social-auto-upload) · ⭐15731（2026-10-23；MIT）

### gzh-design-skill
- **一句话**：把 Markdown 一键排成能直接粘进公众号编辑器的精致 HTML：6 套精选主题+主题生成器，自动章节编号、引言卡片、代码块、作者签名——适合写公众号的人。
- **核心用法**：
  1. 触发：说"公众号排版"或丢 md/docx/pdf/纯文本（非 md 先自动归一化）
  2. 选主题：按题材自动推荐（教程→摸鱼绿、深度分析→红白色系、设计评论→石墨极简风…），一步确认；不满意可按描述/参考图生成自定义主题存本地复用
  3. 组件全从 `references/` 主题库取（引言卡/章节标题/正文标记/签名），不手写 HTML，保证粘贴后样式不丢
  4. "直接排/一键"进全自动模式：自动推断结构+选主题+校验，交付附决策说明
- **安装**：`git clone https://github.com/isjiamu/gzh-design-skill.git`
- **怎么用它搞钱**：接公众号排版/代运营单：一篇文章的排版从半天压缩到几分钟；或做"排版工作台"服务按篇收费
- **来源**：[isjiamu/gzh-design-skill](https://github.com/isjiamu/gzh-design-skill) · ⭐4119（2026-10-23；⚠️ AGPL-3.0 copyleft 许可：自用/内部分发没问题，对外提供网络服务需注意传染条款）

### md2wechat-skill
- **一句话**：面向 AI Agent 的公众号创作与发布 CLI：Markdown 排版、AI 配图、预览与草稿创建一条龙，还支持 humanize 去 AI 味和标题建议——适合把公众号当获客渠道的人。
- **核心用法**：
  1. 意图路由：排版/预览/草稿用 `convert`、`preview`；封面/信息图用 `generate_cover`/`generate_infographic`；标题用 `title suggest`
  2. 先 `md2wechat themes list --json` 看主题和版式，不猜配置
  3. `convert --draft` 直接推进公众号草稿箱；知乎/CSDN/头条草稿走浏览器流程
  4. 写作用 `write`/`humanize` 去 AI 味，`advise` 做发布前诊断
- **安装**：`git clone https://github.com/geekjourneyx/md2wechat-skill.git`（skills/ + platforms/openclaw 双入口）
- **怎么用它搞钱**：公众号矩阵的内容生产管线：写→排→配图→进草稿全自动，日更号的人力成本砍半
- **来源**：[geekjourneyx/md2wechat-skill](https://github.com/geekjourneyx/md2wechat-skill) · ⭐3753（2026-10-23；⚠️ 非 OSI 开源许可（Source Available/BSL 变体）：个人学习可用，商用/对外服务受限，用前请读 LICENSE）

### ecommerce-image-skills
- **一句话**：12 个电商出图 Agent Skill：丢一张手机随手拍，Claude Code/Codex/Cursor 按平台规则出白底主图、场景图、卖点图、A+、模特图、大促 Banner、小红书封面、淘宝详情长图——适合跨境卖家/电商运营。
- **核心用法**：
  1. 一行安装：`npx skills add xianyu110/ecommerce-image-skills`（Claude Code/Codex/Cursor 通用）
  2. 丢商品照片：每个 skill 先锁定产品身份（形状/颜色/Logo/文字）再进提示词，防"图好看但产品被改"
  3. 按平台选 skill：amazon-white-background（白底主图+检查修复脚本）、lifestyle-scene、model-try-on、selling-point-infographic、sale-banner（多平台尺寸预设）、xiaohongshu-cover、taobao-detail-long-image、ecommerce-listing-suite（整套调度入口）
  4. 出图三路：agent 自带生图工具 / 配 GPTIMAGE_API_KEY 用 `scripts/generate.py` / 都没有就输出最终提示词+在线运行链接
- **安装**：`npx skills add xianyu110/ecommerce-image-skills`（MIT；生图走 GPT Image 2.5，需配 API 或用 agent 自带工具）
- **怎么用它搞钱**：接电商出图单：随手拍→全套 Listing 图，一单多图；跨境卖家多国站点复用同一套流程
- **来源**：[xianyu110/ecommerce-image-skills](https://github.com/xianyu110/ecommerce-image-skills) · ⭐108（2026-10-22；MIT，仓库有真实出图画廊）

### kiki-lgtm-dot/light-retro-collage-xiaohongshu-skill（轻复古拼贴风小红书知识图文）
- **一句话**：把关键词/文章/截图/文档变成一套 4–12 页 3:4 小红书知识图文：选题澄清→联网查证→写文案→生成轻复古拼贴插画→动态排版→四维质检，全链路半自动——适合做小红书知识号、想批量出图文的人。
- **核心用法**：
  1. 定选题：说清主题和受众；有歧义先澄清，不带着模糊选题开工
  2. 先查证再写：每个核心观点配两个独立来源，时效/专业内容不许凭记忆写
  3. 批计划：给出 4–12 页、每页一句话目的，确认页数和版式（文字中心/插画中心）
  4. 写文案：每页一个主论点，配文+话题≤200 字；禁用"赋能/颠覆"类 AI 腔
  5. 出图排版：1080×1440 画布，暖象牙纸+低饱和包豪斯色+钴蓝点缀；文案先定稿，插画不抢字
- **安装**：`git clone https://github.com/kiki-lgtm-dot/light-retro-collage-xiaohongshu-skill.git "$HOME/.agents/skills/generate-light-retro-collage-xhs-notes" && cd "$HOME/.agents/skills/generate-light-retro-collage-xhs-notes" && python3 -m pip install -r scripts/requirements.txt && python3 scripts/self_test.py`
- **怎么用它搞钱**：接小红书知识图文代做单（选题到成图一条龙，按套收费）；或自己起知识号批量产图文吃平台流量
- **来源**：[kiki-lgtm-dot/light-retro-collage-xiaohongshu-skill](https://github.com/kiki-lgtm-dot/light-retro-collage-xiaohongshu-skill) · ⭐25（2026-10-24；Apache-2.0，README+SKILL.md+scripts/tests 全套）

### Irixil/xiaohongshu-skill（小红书知识图解+长文排版发布）
- **一句话**：两种模式：①把杂乱素材变成选题严选的小红书知识图解（Gate 0–5 流程）；②把已确认的长文完整排版成小红书长文（封面/原生分页/原创与 AI 声明/话题 Tag/发布核验），母稿保护不被反向覆盖——适合有长文要发小红书、做知识图解的人。
- **核心用法**：
  1. 先选模式：新做图解走 Gate 0–5；已有文章直接走长文排版发布流
  2. 选题严选：从素材里挑最小可用的一个 idea，给出 3 个可发布角度并推荐最优
  3. 母稿保护：用户确认过的文字稿是唯一母稿，排版只改派生文件，不改标题正文标点
  4. 发布有门：排版只许保存草稿；"审核后再发"必须等批准；明确说"直接发布"才提交
- **安装**：`git clone https://github.com/Irixil/xiaohongshu-skill.git`，把目录加入 Codex/agent 的 Skills 目录
- **怎么用它搞钱**：接"公众号/知乎长文转小红书"代发单；知识图解模式适合做科普号批量出卡片
- **来源**：[Irixil/xiaohongshu-skill](https://github.com/Irixil/xiaohongshu-skill) · ⭐22（2026-10-24；⚠️ 仓库无 LICENSE 声明，商用前先确认授权）

### kangarooking/x-skills（X 推文创作全链路：收集→筛选→创作→草稿箱）
- **一句话**：中文 X 账号的内容创作流水线：4 轮搜索收集素材→多维打分筛选选题→意图路由写推文→只发到草稿箱等你点头，适合做 X 账号、想把推文变成固定流程的人
- **核心用法**：
  1. 克隆后把 x-collect/x-filter/x-create/x-publish 复制或软链到 ~/.claude/skills/
  2. 首次跑 /x-create 建人设档案：领域、目标受众（中文/英文/双语）、人设风格
  3. /x-collect [话题] 4 轮深度搜索收集素材，/x-filter 多维加权打分 + 负样本过滤 + 多样性衰减筛选题
  4. /x-create 按意图路由（收藏/转发/讨论）选创作模式，默认出 A/B 两个版本 + Critic 自检，低于阈值自动重写一次，并强制过一遍 humanize 去 AI 味
  5. /x-publish 只发到 X 草稿箱 + 事件记录（JSONL），人工点头后才真发；正/负样本库做反馈闭环
- **安装**：`git clone https://github.com/kangarooking/x-skills.git`，把 x-collect/x-filter/x-create/x-publish 复制或软链到 ~/.claude/skills/（README 官方安装方式）
- **怎么用它搞钱**：接 X 账号代运营/推文代写单（选题→成稿→草稿箱一条龙，按周交付）；或自己做 X 矩阵号，选题库与反馈闭环越用越准
- **来源**：[kangarooking/x-skills](https://github.com/kangarooking/x-skills) · ⭐340

### sharbelxyz/x-bookmarks（X 收藏夹变行动清单）
- **一句话**：把 X 收藏夹从“存了不看”变成可执行的工作：拉取最新收藏→按话题分类→每条给可执行的行动建议，还能定期出摘要
- **核心用法**：
  1. 装成 OpenClaw skill：`openclaw skill install x-bookmarks`（拉取需 bird CLI 或 X API v2）
  2. 直接说“check my bookmarks”：自动拉取最新收藏，按话题分类（crypto/AI/marketing/tools 等）
  3. 每条不止给摘要，给行动：如“克隆这个仓库实测并搭好”这类 agent 可直接干的事
  4. 常用口令：bookmark digest 出分类摘要、what did I bookmark this week 按时间过滤、find patterns 找反复收藏的方向、clean up old bookmarks 清理过期收藏
  5. 定时摘要：设每日/每周 cron，自动查新收藏、分类并投递摘要
- **安装**：`openclaw skill install x-bookmarks`（需 bird CLI 或 X API v2 拉取收藏）
- **怎么用它搞钱**：接“信息整理/选题挖掘”服务：客户的收藏夹定期变成选题库+行动清单；或自己用收藏夹养选题，收藏方向就是市场信号
- **来源**：[sharbelxyz/x-bookmarks](https://github.com/sharbelxyz/x-bookmarks) · ⭐290

### Jakeschincariol/x-agent-skill（X 账号全流程：21 钩子公式+分析审计）
- **一句话**：11 个 Claude skills 跑通一个 X 账号：21 钩子公式写帖、线程、回复、主页评分、周计划、分析审计，另带 9 个实测工具，写完必须你点头才发
- **核心用法**：
  1. `git clone https://github.com/Jakeschincariol/x-agent-skill.git`，把 skills/x-* 复制到 ~/.claude/skills/（或在 Claude 里粘贴仓库链接安装，确认 /x-post 可用）
  2. 创作走 virality skill：找 niche 里真正跑赢的帖子，拆成钩子/结构/形式，再按你的声音和受众复刻赢家
  3. 9 个工具兜底：按 X 的计数法数字符（链接算 23、emoji 算 2）、发前给首句打分、长稿切成合规线程、读 X 公开排序代码看本周奖励什么
  4. 分析审计读你的 Analytics 导出：按内容类型比曝光/互动/回复/分享，每个结论都标样本量，不凭一两篇爆款下结论
  5. 铁律：Nothing is posted until you approve it——skills 只写，你发
- **安装**：`git clone https://github.com/Jakeschincariol/x-agent-skill.git` 后 `cp -r x-agent-skill/skills/x-* ~/.claude/skills/`（README 官方安装方式）
- **怎么用它搞钱**：接 X 账号代运营单（钩子+线程+周计划+复盘一条龙）；或用分析审计给客户出“什么内容真有效”的复盘报告，按次收费
- **来源**：[Jakeschincariol/x-agent-skill](https://github.com/Jakeschincariol/x-agent-skill) · ⭐41

## 去 AI 味（16 个）

> 注：op7418/Humanizer-zh 不在本批次提炼范围（已有独立 skill 在用）。humanizer 走检查清单路线，tt-humanizer 专攻短视频口播，qu-ai-wei 专攻简体中文改写，humanizer-skill 带检测评分 + 多人声改写。kill-ai-slop 专攻 vibe-coded 网页的视觉+文案双重去味（带扫描器）。

### kill-ai-slop
- **一句话**：给 vibe-coded 网页"去 AI 味"的 field guide+扫描器：indigo→violet 渐变、gradient-clip 标题、emoji 泛滥、"not just X—it's Y" 腔调等几十种 AI 痕迹逐条定位，先出报告再动手改——适合做落地页/产品站的人。
- **核心用法**：
  1. 先扫：`node scripts/scan.mjs <项目根>`（零依赖），按 tell id 分组输出 file:line 命中
  2. 逐条 triage：打开文件判 slop vs 刻意设计，确认是刻意的用 `deslop-ignore` 标注
  3. 按 6 原则修：先做决定再装饰、一主色一语调、层级靠字号留白、先做减法
  4. 文案同步去味：specific beats punchy，删"not just X—it's Y"式腔调
- **安装**：`git clone https://github.com/yetone/kill-ai-slop.git`（Apache-2.0；扫描器需 Node）
- **怎么用它搞钱**：接落地页"去 AI 味"优化单：vibe-coded 的站花一天变"有人味"，按页收费；或打包进建站交付流程当增值项
- **来源**：[yetone/kill-ai-slop](https://github.com/yetone/kill-ai-slop) · ⭐1377（2026-10-23；Apache-2.0，X 去 AI 味三帖共推品类）

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
- **来源**：[blader/humanizer](https://github.com/blader/humanizer) · ⭐61069（10-19 复核，持续上涨）

### tt-humanizer
- **一句话**：专给短视频口播脚本/字幕去 AI 味——纸上读着顺、嘴上说出来像机器人的问题，用四道工序逐个修；注意它不保证过 AI 检测器，目标是观众听着像真人。
- **核心用法**：
  1. 四道工序：① Scrub 按"每拍密度"扫词库（一个 AI 词不算，同一拍出现 3 个才重写；reveal bridge、否定平行、真诚宣告、死 filler、模型泄露见一个杀一个）；② Rhythm 只修"说不出口"——换口语（缩写、一口气一行）、拆需要两口气的长句，绝不为节奏硬插短促金句（那是 humanizer 自己的指纹）；③ Add 加人味指纹——要一个平直的、有日期的、甚至让人不舒服的具体事实；④ Over-correction Guard 检查前三道工序有没有引入新的 AI 味，拿不准就别动。
  2. 2026 新认知：词汇按密度判不按删除名单判（delve/tapestry 已过时，耐用品是 significant/crucial/notably/comprehensive/insights/robust/leverage/foster/landscape/nuanced/streamline/elevate 等"普通大词"加名词化、-ing 开头句式，出现率是人类 5.3 倍）；破折号不封杀，提词器里用".."当呼吸记号，字幕卡最多 1 个。
  3. 禁区清单：真诚宣告（"不骗你""说真的"）、"The X? Y." 式揭秘、"No X. No Y. Just Z." 三连、"原因？因为……"伪苏格拉底问答、为节奏硬插的独词行（"Still." "Exactly."）。
  4. 拍前 audit 模式：不改文只出结论——前 3 秒钩子强度、静音刷屏适配、完播结构、字幕/话题标签适配，输出 Blocker + Warning；还有 --mode profile 可从用户旧稿学习其声音指纹。
- **安装**：npx skills add sergebulaev/tiktok-skills
- **怎么用它搞钱**：做短视频团队的"拍前质检"外包——客户发口播脚本，你跑 audit 模式出 Blocker/Warning 报告按次收费；或给 MCN 做批量脚本去味，按账号收月费。
- **来源**：[sergebulaev/tiktok-skills](https://github.com/sergebulaev/tiktok-skills) · ⭐90

### qu-ai-wei（简体中文去 AI 味）
- **一句话**：专治简体中文 AI 味的改写 skill——删套话、保事实、技术文不降格，适合写公众号 / 小红书 / 视频文案总被说"一看就是 AI 写的"的人
- **核心用法**：
  1. `npx skills add https://github.com/LifelongLazyLearner/qu-ai-wei`，对中文说"去 AI 味"即触发（`/qu-ai-wei`）
  2. 先识别 10 类中文 AI 味结构（"随着…发展""值得一提"等），只改空转、反复出现的套话，单独出现一次不误杀
  3. 铁律：删空话不丢数字（"发布 3 个版本、修复 17 个问题"原样保留），技术词、因果关系、正式程度保持不变
  4. 真人味文字（有具体经历 / 自嘲 / 自然节奏）会停手不乱改；输入含密码、key 等敏感信息先过门检
- **安装**：`npx skills add https://github.com/LifelongLazyLearner/qu-ai-wei`
- **怎么用它搞钱**：接文案代写单：AI 初稿 + qu-ai-wei 去味，交付"真人感"文案按千字收费；做矩阵号时去味后多平台分发，降低被判营销号 / 限流风险
- **来源**：[LifelongLazyLearner/qu-ai-wei](https://github.com/LifelongLazyLearner/qu-ai-wei) · ⭐700

### Aboudjem/humanizer-skill（55 模式检测 + 5 人声）
- **一句话**：55 种 AI 写作模式检测 + 0-100 AI 味评分 + 5 种人声改写，适合发英文博客 / LinkedIn / Newsletter 怕被看出 AI 味的人
- **核心用法**：
  1. 三种模式：`detect` 只扫描打分不改写；`rewrite` 按选定人声改写；`edit` 直接改文件（`--mode` 切换）
  2. 5 种声音按场景选：casual / professional / technical / warm / blunt，`--voice` 指定
  3. 纯 Markdown、零依赖、不联网，本地跑完；`--iterate N` 多轮改写直到分数满意
  4. `--purpose` 按用途调（essay / email / marketing / technical），`--score` 输出量化分
- **安装**：`claude plugin marketplace add Aboudjem/10x && claude plugin install humanizer@10x`
- **怎么用它搞钱**：接英文内容代写 / 领英代运营单：AI 量产 + humanizer 去味，交付"母语写手"质感收溢价；做英文利基站，内容去味后广告审核、投稿通过率更高
- **来源**：[Aboudjem/humanizer-skill](https://github.com/Aboudjem/humanizer-skill) · ⭐291

### ilien-dev/quiron（量得出来的英文去 AI 味）
- **一句话**：英文去 AI 味 skill，改完不凭感觉：对照实测人类写作基线量一遍，改没改到位有数，支持博客/小说/西班牙语三种语体，适合做英文内容代写的人
- **核心用法**：
  1. `npx skills add ilien-dev/quiron`，无需 API key，脚本只用 Python 3 标准库
  2. 把草稿丢给它：先 strip AI slop 痕迹，再按语体（博客/小说/西班牙语）改写
  3. 改完对照人类写作实测基线量一遍，拿到改写结果+测量结论，不是一句“像真人了”
  4. README/博客类文本直接说“让这段读起来不像 ChatGPT”，自动触发改写+测量
- **安装**：`npx skills add ilien-dev/quiron`
- **怎么用它搞钱**：接英文内容代写/领英代运营单：AI 量产 + quiron 去味+测量，交付“母语写手”质感收溢价；测量结论本身就是交付凭证
- **来源**：[ilien-dev/quiron](https://github.com/ilien-dev/quiron) · ⭐60

### numen-tech/slopornot（5 遍去味+声音指纹+本机检测）
- **一句话**：去 AI 味双 skill：agentic-humanizer 走 5 遍改写流程（还支持按你的范文 matching 声音指纹），slop-check 本机跑 AI 检测打分，支持 7 种语言，适合要稳定交付“人味”的代写团队
- **核心用法**：
  1. `npx skills add numen-tech/slopornot`（或按 README 插件方式装），先定改写偏好
  2. 5 遍流程：AI 痕迹手术→变体与语气对齐→阅读难度调整→清理感知 targeted 编辑→不够再结构重写
  3. 声音指纹：把你的范文放 ~/.agentic-humanizer/voice.txt，改写按你的节奏/句式/口头禅靠拢
  4. slop-check 本机检测：改前改后各跑一遍 AI 分+可读性，Pro 版多一层检测循环收敛
- **安装**：`npx skills add numen-tech/slopornot`
- **怎么用它搞钱**：接多语言内容代写单（英/西/德/意/北欧语），5 遍流程+声音指纹是按账号收月费的卖点；检测报告当交付凭证，减少返工扯皮
- **来源**：[numen-tech/slopornot](https://github.com/numen-tech/slopornot) · ⭐56

### hardikpandya/stop-slop（删 AI 痕迹：短语+结构+范例三件套）
- **一句话**：专门删 AI 写作痕迹的 skill：短语库+结构模式+前后对照范例三件套，教 Claude 抓住并去掉那些可预测的 AI 腔
- **核心用法**：
  1. 把 stop-slop 文件夹作为 skill 加入（Claude Code），或把 SKILL.md 及 references 上传到项目知识库（Claude Projects）
  2. 对照 phrases.md 删可预测短语，对照 structures.md 避开结构套路，对照 examples.md 看前后 transformation 怎么改
  3. API 调用时把 SKILL.md 放进 system prompt，references 按需加载
  4. 改完自查：是不是还留着 AI 的节奏、结构和短语——有就再过一遍
- **安装**：`git clone https://github.com/hardikpandya/stop-slop.git`，把 stop-slop 文件夹作为 skill 加入（README 官方用法）
- **怎么用它搞钱**：接英文内容去味/润色单（博客/Newsletter/落地页文案按篇收费）；或嵌进自己的英文内容工作流当质检关
- **来源**：[hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop) · ⭐18315

### MrGeDiao/shuorenhua（中文优先说人话：删套话保事实保口气）
- **一句话**：中文优先的去 AI 味改写 skill：删套话、重复铺垫和生硬句式，数字、条件、承诺和你的口气原样留下，改完可直接发
- **核心用法**：
  1. `npx skills add MrGeDiao/shuorenhua`，Claude Code/Codex/Cursor 都能用
  2. 把写好的文字交给它：删开头的招呼和预告、重复的一句、结尾的致谢这类套话
  3. 铁律：数字、条件、承诺和口气保持原样；本来就没问题的文字不动，不硬改
  4. 适用场景：工作同步、公众号/小红书/视频文案，改完直接发不用二次加工
- **安装**：`npx skills add MrGeDiao/shuorenhua`
- **怎么用它搞钱**：接中文文案去味单（按千字收费）；或给矩阵号批量去味后多平台分发，降低被判营销号/限流风险
- **来源**：[MrGeDiao/shuorenhua](https://github.com/MrGeDiao/shuorenhua) · ⭐2257

### jzOcb/writing-style-skill（文风自动学习模板：越用越像你）
- **一句话**：可复用的写作风格 skill 模板，内置自动学习：AI 按 SKILL.md 写初稿→你改到满意→diff 两版提规则→SKILL.md 越用越准
- **核心用法**：
  1. `git clone https://github.com/jzOcb/writing-style-skill.git`，复制到 ~/.claude/skills/my-writing-style（或 `npx clawhub@latest install jz-writing-style-skill`）
  2. 先把模板里的风格规则改成你自己的（或留空，让自动学习帮你填）
  3. 让 AI 用这个 skill 写内容，你改到满意
  4. 记录两版：`python3 scripts/observe.py record-original draft.md` → 改完 → `record-final final.md`，脚本 diff 提规则更新 SKILL.md
  5. 只要 original 和 final 两个数据点，中间改了多少轮不管；下次写就更像你
- **安装**：`git clone https://github.com/jzOcb/writing-style-skill.git` 后 `cp -r writing-style-skill ~/.claude/skills/my-writing-style`（README 官方安装方式）
- **怎么用它搞钱**：接“品牌文风定制”单：给客户训一套越用越准的专属写作 skill，按账号收月费；或自己养多个账号人设，一套模板多套风格
- **来源**：[jzOcb/writing-style-skill](https://github.com/jzOcb/writing-style-skill) · ⭐273

### Anbeeld/WRITING.md（人味规则集：具体锚点+体裁校准+自审计）
- **一句话**：Anbeeld 的 AI 写作规则集：用具体锚点代替空泛表述、按体裁校准声音、自审计改写循环，不靠造假式“人味” tricks（不编 typo、不硬造口语）
- **核心用法**：
  1. 把 skills/writing 目录作为 skill 加入（或直接把 WRITING.md 交给 AI 按规则应用）
  2. 先定上下文：体裁、受众、读者需求、这段文字的任务；再动手写
  3. 规则要点：无可核查细节的段落必须改写；引言、数字、日期、因果、署名都要有依据；删 keynote 腔、客服腔、仪式化开头结尾
  4. 改写循环：先按规则出初稿→按 required checks 审计→按审计结果重写，大稿重复一两轮即可
  5. 红线：不编造 typo、不硬插俚语、不搞程序化句长变化、不做 staged messiness
- **安装**：把 skills/writing 目录作为 skill 加入（或直接把 WRITING.md 交给 AI 按规则应用）
- **怎么用它搞钱**：接英文写作润色/审校单（文档、博客、发布稿按篇收费）；或把规则集嵌进团队写作 SOP，当审稿标准
- **来源**：[Anbeeld/WRITING.md](https://github.com/Anbeeld/WRITING.md) · ⭐381

### adewale/anti-slop-writing（具体细节胜过 inflated significance）
- **一句话**：面向 README/文章/DevRel 写作的去 AI 味 skill，核心规则就一句：具体细节胜过 inflated significance，给的是一套可执行的编辑测试而非空泛建议
- **核心用法**：
  1. 只装 skill 目录：skills/anti-slop-writing/（SKILL.md + references）
  2. 按编辑测试改：把含糊的重要性表述换成具体机制；揪“not just X but Y”式装饰对比和套路节奏
  3. 段落流转按因果/对比/依赖/推断/层级变化命名，不靠空话衔接
  4. 结尾回到具体载体，不以泛泛结论收束；压缩有用信息的同时去掉假装判断的腔调
- **安装**：`git clone https://github.com/adewale/anti-slop-writing.git`，只取 skills/anti-slop-writing/ 目录作 skill 用（README 官方安装方式）
- **怎么用它搞钱**：接技术文档/DevRel 写作润色单（README/发布稿/技术博客按篇收费）；或给技术团队做写作审校，腔调统一就是交付标准
- **来源**：[adewale/anti-slop-writing](https://github.com/adewale/anti-slop-writing) · ⭐21

### op7418/Humanizer-zh（中文去 AI 味：保事实保声音）
- **一句话**：中文专用的去 AI 味编辑 skill：删空话、重复和模板化表达，但不改事实、不改作者声音，适合所有要公开发布的中文稿件
- **核心用法**：
  1. 先定约束再改：不增删事实、数字、名字、日期和限定词（可能/据称/仅/正在/计划）；不把相关改成因果、可能改成确定
  2. 按 31 条模式清单查表达问题：假对比（“不仅是 X，更是 Y”）、空泛铺垫、强凑三段式、破折号泛滥——但清单只是线索，不是黑名单，没有问题的段落原样保留
  3. 匹配作者声音：有样稿就学句长、用词和标点，不把样稿里的经历和数据搬进目标文本；技术/商务/学术文本保留正式程度，不强行口语化
  4. 交稿前对照原文自查：有没有新增、遗漏或强化主张；施事者、时间、条件、范围、否定与归因是否一致；通读一遍，通顺的文字不为凑工作量硬改
  5. 边界：只润色已有文本，不判断作者身份、不保证通过 AI 检测器；代码块、链接、YAML、表格数据原样不动
- **安装**：`npx skills add https://github.com/op7418/Humanizer-zh.git`（README 官方安装方式）
- **怎么用它搞钱**：做“AI 代写 + 去味”两道工序的代运营增值服务，按千字收费；或给公众号/小红书客户做发前润色包月，中文稿是刚需
- **来源**：[op7418/Humanizer-zh](https://github.com/op7418/Humanizer-zh) · ⭐21083

### Nutlope/hallmark（网页去 AI 味：16 条硬底线 + 自动 lint）
- **一句话**：治网页“一眼 AI”味的设计 skill：16 条硬底线加自动 lint，让 AI 出的页面看起来像人设计的，适合做落地页、产品页、活动页的人
- **核心用法**：
  1. 先过硬底线（Floor，16 条不可豁免）：颜色字体全走 :root token、不许 transition: all、不许标题里单个斜体词、不许 eyebrow 小字大写标签、不许紫蓝渐变/卡片套卡片/emoji 当图标、不许编造数据、证言、logo 墙
  2. 一屏只讲一件事：首屏 1280×800 内放下标题、一句话和主按钮；单屏约 80 词；容器居中封顶，大屏只长边距不拉宽版式
  3. 按流程走：先读项目（pre-flight）→ 一次问清材料/受众/用途/语气 → 定版式和主题 → 先出首屏再铺全页 → sloplint --render 扫到干净才交付
  4. 有料才设计：材料（截图/真实数字/署名引言/可用 logo）先行，没有的标“缺失”不编造；真实品牌不凭记忆套主题
  5. 只在用户点名时才动老设计：redesign/audit 两个动词专用于已有页面，平时只用于新页面
- **安装**：`npx skills add nutlope/hallmark -g`（README 官方安装方式；需 Node 18+；浏览器检查另需 puppeteer-core + Chrome，没有也能跑静态检查）
- **怎么用它搞钱**：接“AI 建站精修”单：客户用 AI 出的落地页一眼假，你用 Hallmark 底线加 lint 重做一版，按页收费；或给独立开发者做产品页，设计感就是转化率
- **来源**：[Nutlope/hallmark](https://github.com/Nutlope/hallmark) · ⭐36633

### larashero3-dotcom/lieflat-less-ai-tone（证据驱动的中文去 AI 味：先出检测报告、你点头再改）
- **一句话**：基于两轮实测语料（629 篇对照 + 270 对同题配对，约 520 万字、100+ 项指标、约 50 万次语义判断）的中文去 AI 味 skill：不直接改稿，先交付有指标、研究参照、原文例句和具体改法的检测报告，你回复“按建议改”后才改写并复测出前后对比，适合写公众号 / 小红书 / 长文、怕被一眼认出 AI 味的人
- **核心用法**：
  1. `npx skills add larashero3-dotcom/lieflat-less-ai-tone` 装好，把成稿交给 AI
  2. 第一步脚本检测：`python3 scripts/detect.py <文件> --json` 出分级报告（A 机械改 / B 建议改 / C 只报告 / X 已否决 / F 指纹），改前务必带 `--json` 存档供复测对比
  3. 第 1.5 步语义判读：`python3 scripts/detect.py <文件> --candidates --out /tmp/candidates.json`，按封闭判据判四类候选（同义重命名 / 衔接连环 / 结论冒号 / 同构三连），拿不准标兜底、不自造标签
  4. 第二步等用户点头：AI 交付改前报告（本篇指标 + 研究显著性 + 原文例句 + 改法），此时只建议不改正文；你回“按建议改”才进第三步改写，第四步复测出对比报告
  5. 红线记牢：报告不能删项（误报标误报、不抹数）、不能凭单篇命中就断言作者是 AI、X 级已否决规则只出现在报告里永不执行、比喻贴切度等人审区不让模型假装能判
- **安装**：`npx skills add larashero3-dotcom/lieflat-less-ai-tone`
- **怎么用它搞钱**：自用发稿先过检测报告提质；商用接单前先联系作者拿授权，拿到后可把“检测报告 + 改写复测”打包成按篇收费的去味质检服务——报告本身就是客户看得见的交付物，改了什么、为什么改都有据可查
- **来源**：[larashero3-dotcom/lieflat-less-ai-tone](https://github.com/larashero3-dotcom/lieflat-less-ai-tone) · ⭐4333（⚠️ 许可为 CC BY-NC 4.0：署名 - 非商业使用，商用接单前需联系作者拿授权，别直接当商用工具卖）

### Nanako0129/sepia（架构级去 AI 味：不只换词，从叙事结构下手）
- **一句话**：架构级去 AI 味 skill：不只换词改句，从叙事结构、主题阐释、因果单线等深层特征下手，6 个子 skill（主 skill + review/refactor/write/hemingway/recreate），适合写小说/技术文档/长文、怕被一眼认出 AI 味的人
- **核心用法**：
  1. `npx skills add Nanako0129/sepia -g`（或 Claude Code：`claude plugin marketplace add Nanako0129/sepia` 后 `claude plugin install sepia@sepia --scope user`）
  2. 按任务选模式：review 先诊断、refactor 改写最常用；小说先梳叙事结构再优措辞，技术写作按发布说明/PR 回复/复盘/工单/技术文章分规范
  3. 三种处理按需选：问题诊断 / 局部修改 / 全文重写，不默认全文重写；事实、数字、限定词不动，只改表达
  4. Import code 导入坑：只解析目录时须补传 SKILL.md + professional-pass.md + languages/zh.md 并复述对照，否则正文规则进不来
  5. 附 evals/tests 可自测改写效果；改后对照检查事实与归因是否一致，不为去味硬改原意
- **安装**：`npx skills add Nanako0129/sepia -g`
- **怎么用它搞钱**：接“AI 代写 + 架构级去味”质检单（比换词改写更难被替代）；或给长文客户做发前诊断报告 + 改写包月，诊断报告本身就是交付物
- **来源**：[Nanako0129/sepia](https://github.com/Nanako0129/sepia) · ⭐3526

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
- **来源**：[nidhinjs/prompt-master](https://github.com/nidhinjs/prompt-master) · ⭐15297

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

### alchaincyf/nuwa-skill（蒸馏任何人的思维方式：心智模型+决策启发式+表达 DNA）
- **一句话**：蒸馏任何人的思维方式：输入一个名字，自动调研、提炼、验证，产出带心智模型、决策启发式和表达 DNA 的 skill，让乔布斯、芒格、费曼都给你打工
- **核心用法**：
  1. `npx skills add alchaincyf/nuwa-skill`（自动识别 runtime；或告诉 agent“帮我安装这个 skill：https://github.com/alchaincyf/nuwa-skill”）
  2. 输入一个名字：女娲自动完成调研→提炼→验证全流程
  3. 蒸馏产物：心智模型、决策启发式、表达 DNA，可直接作为 agent 的思维方式调用
  4. 适用：向名人/专家学决策和表达，或把某个人的工作方式固化成可复用的 skill 资产
- **安装**：`npx skills add alchaincyf/nuwa-skill`
- **怎么用它搞钱**：接“专家思维蒸馏”咨询：给企业/创作者把创始人或专家的决策方式做成 agent skill，按人收费；或把蒸馏出的名人思维包做成课程/模板卖
- **来源**：[alchaincyf/nuwa-skill](https://github.com/alchaincyf/nuwa-skill) · ⭐35832

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

- 2026-10-31：v3.4 追加 1 条（视频生产 1 条：topo-ai/ai-video-skills HyperFrames 垂类工作流 5 件套（AI 资讯快报 + 产品介绍 + 音效方案 + 简笔画动画 + Anime.js 适配；资讯快报 5 步 + 逐句字幕跟随口播、音效搜索 / 合成双路径、简笔画先搜参考图临摹，资讯快报 / 音效 / 简笔画 3 个 SKILL.md 逐个读过确认干货）49★ MIT，2026-05-18 推送一年内；注：与库内 HyperFrames 引擎条目为引擎 vs 垂类工作流关系，不重复立引擎），共 149 个 skills；星数刷新：video-shotcraft 14766→15169、guizang-product-video 886→888、opus-video-skills 383→398、qiaomu-anything-to-notebooklm 6399→6441、instagram-agent-skill 1724→3938、youtube-agent-skill 1583→3874、prompt-master 15116→15297；去重 / 淘汰 / 记信号：GitHub `claude skills` 前 15 全已入库或已淘汰（目录 / dev / 安全 / 游戏 / LinkedIn 向不匹配先例）；补充关键词：`video skill`：chengfeng-videocut-skills 3158★ README 当日实测仍声明公开 Runtime v0.4.11 不满足新 Skill ≥0.5.9 要求，hold 延续；wshuyi/remotion-video-skill 439★ 仍无 LICENSE 续 hold；SpaceZephyr/creator-buddy 仍无 LICENSE 续 hold；mediastormDev/dream-to-video-skill 375★ 解梦赛道窄 + 即梦网页登录自动化链路脆弱，暂缓延续；LearnPrompt/awesome-seedance 2363★ 与 zhuyansen/awesome-claude-video-skills 1311★、UnderleveledBuilder/awesome-short-drama-skills 1490★ 均为纯目录 / 合集形态，按目录先例不收；`short drama skill` 其余全已入库或 <20★；`wechat article skill`：aiworkskills/wechat-article-skills 717★ 与库内 wewrite 同属全流程大包不堆记观察、BND-1 318★ 无 LICENSE 且重叠不收、MaydayV 36★ 2026-10-19 后未更新记观察延续；`douyin skill`：zJay26/douyin-skills 60★ 封号风险先例不收，其余 <20★ 或采集 / 风控类不收；`ai video skill` 新冒头 topo-ai 49★ 即本轮收录，其余 <20★；skills.sh All Time 首页当日实测仍老面孔（hyperframes / mattpocock / vercel 系已入库或 dev / 设计向；flowkit reddit-automation 站内 1.2M install 对应 GitHub 25★、uizze ios-design 417.1K 对应 78★、runcomfy video-edit 442.1K 对应 62★、gencraft 351.1K 对应 0★，防刷量铁律均不收；Trending(24h) API 本轮实测已改为需 Vercel OIDC 认证，文本抓取与浏览器任务均返回 authentication_required、无登录前提下无法读取，记缺口不编造榜单）；skillhub.cn：站内抖音热点类 skill 成新需求信号（飙升榜查询、上升热点选题、实时热榜、视频号热点简报，均需 API Key 且无 GitHub 源码链接，无法交叉验证 0 收录）；X 浏览器扫描任务已派（只读指令），截至发稿未回，结果待补记；热度洞察一句话：资讯快报与音效正在补齐视频生产链的最后两块短板——选题有源头、成片有声音，而抖音热点选题工具的站内热度说明“拍什么”比“怎么拍”更缺趁手家伙
- 2026-10-30 补记：v3.3 X 信号轮补录 1 条（视频生产：10291124jcjc-dotcom/ai-anime-series AI 动画单元剧（固定原创角色 + 宫格故事板 + 即梦 Seedance 2.5 一次生成，一句话出一集，仓内有汤圆和油条 30 秒实证成片）179★，2026-10-28 推送，⚠️ LICENSE 文件存在但 SPDX 未识别），共 148 个 skills；星数刷新：lemo-opuscar 8730→9450、风格数 59→66 种（X 帖称 9800+★ 为作者约数，以 GitHub API 9450 为准）；X 信号 12 帖核验（只读无互动，@Hjn8899 登录态正常、未遇验证，窗口 2026-10-28 10:46 至 2026-10-30 10:46 北京）：去重：lemo-opuscar 库内已有仅刷新、火柴人 Skill 即库内 stickman-video-director、marketingskills 库内已有、awesome-short-drama-skills 纯目录形态先例不收；章节不合：pbakaus/impeccable 95567★ Apache-2.0（设计词汇 skill，设计向先例不收，设计去 AI 味需求记信号）、cathrynlavery/diagram-design 62971★ MIT（图表设计向不收）；记信号不收：@EianLu 代码出片 6 步工作流文章（65K 浏览 / 1304 收藏，无具名仓库）、@CyberAlice3269 口播视效包装 Skill（未给仓库名无法核验）、@dashu5ai 求推荐访谈长视频剪辑（现有工具不满意，需求缺口）、@mushengziyue Opus Clip 变现案例（商业产品非 skill，长视频自动切短视频 ARR 八位数自述）、@Passenger0522 朱雀检测 + 手改工作流（检测工具非 skill，平台审查趋严信号）、@WinterPHD8866 求推荐去 AI 味（需求存在但无答案）；热度洞察一句话：系列化是动画号的新门槛——角色固定 + 一句话一集的连载模式正在替代单条爆款抽卡，而口播与访谈剪辑仍是“有需求、无趁手工具”的缺口
- 2026-10-30：v3.3 追加 1 条（文案钩子 1 条：hongfamonvAI/hook-lab 短视频爆款拆解（/analyze 抓数据→前 3 秒 Hook 定类型判强度→脚本结构分段→风格标签→具体爆款原因→3 个小红书 / 视频号改写方向→结果库归档，aiposthub 10-11 实测 6 款中唯一能直接用）103★ MIT，2026-06-11 推送一年内），共 147 个 skills；星数刷新：video-shotcraft 13855→14766、guizang-product-video 872→886、opus-video-skills 345→383、ai-short-drama-skill 71→78、novel-to-ai-short-drama 31→32、short-drama-skills 95→96；去重/淘汰/记信号：GitHub `claude skills` 前 15 全已入库或已淘汰（导航 / dev / 安全 / LinkedIn / 游戏向不匹配先例）；补充关键词：`video skill` 全已入库或 hold（chengfeng-videocut-skills 3156★ README 当日实测仍声明公开 Runtime v0.4.11 不满足新 Skill ≥0.5.9 要求，hold 延续；dream-to-video-skill 375★ 解梦赛道窄 + 即梦网页登录自动化链路脆弱，暂缓延续）；`short drama skill` 全已入库或 <20★；`wechat article skill`：aiworkskills/wechat-article-skills 716★ 与库内 wewrite 同属全流程大包不堆记观察、MaydayV/wechat-article-skill 36★（风格 DNA 学习 + 一句话成文 + 草稿推送，SKILL.md 真实，但与 wewrite / md2wechat / gzh-design 三重重叠、无 LICENSE、2026-03-14 后未更新，记观察不堆）、BND-1 318★ 无 LICENSE 且重叠不收；`douyin skill`：zJay26/douyin-skills 60★ 封号风险先例不收，其余 <20★ 或采集 / 风控类不收；watch list：wshuyi/remotion-video-skill 437★ 仍无 LICENSE + Remotion 官方路由重叠续 hold、SpaceZephyr/creator-buddy 1769★ 仍无 LICENSE 且类目库已收暂缓、flowkit-labs/skills 25★ reddit-automation 记观察（Reddit 非中文搞钱主战场）、500bitcoins/recast 仍 0★、xiaolu-ai26/video-close-reading 1★ 均记观察、843645440/wechat-skill 132★ 与库内三重重叠待 X 信号再议、UnderleveledBuilder/awesome-short-drama-skills 1295★ 纯目录形态不收；skills.sh All Time / Trending（24h）仍老面孔：uizze 30.1K trending 对应 GitHub 71★ 站内 install 严重背离防刷量不收、gencraft-labs 15.7K trending 对应 GitHub 0★ 刷量嫌疑延续、prime-skills/runcomfy 441.6K All Time 对应 GitHub 60★ 刷量嫌疑延续、designed-by-ai 20★ 未达硬线且设计向、autonnel 5★ 未达硬线、antibrow / liarjs 系规避工具不收、masseater / rigorpilot / lark / azure / prisma 等 dev / 办公向章节不合；skillhub.cn 飙升榜：搜索引擎 1043.6 万、视频全能创作 136.0 万（Beatra 平台工具详情页无 GitHub 源码链接无法交叉验证 0 收录，记需求信号）、防诈专家 139.0 万新上榜；公开网页搜索补信号：aiposthub 10-11 视频 skill 选型文佐证 HyperFrames / Remotion / OpenMontage / Higgsfield / hook-lab 路线、hsingdaily IG 13 skills 即库内 instagram-agent-skill 去重、debpalash/VoiceStudio 94433★ 为独立本地配音工具非 skill 形态不收（记语音克隆配音需求信号）；X 浏览器扫描任务截至发稿仍在跑（@Hjn8899 登录态正常，已见去 AI 味讨论帖在扫），结果待下档补记；X 全程只读无互动；热度洞察一句话：爆款拆解正在从“看感觉”变成“可复用的拆解动作”（hook-lab 把一条爆款拆成数据面板 + Hook 类型 + 改写方向并归档），而视频人群的配音环节开始转向本地语音克隆——能拆、能改、能归档的 skill 比单点生成更值钱
- 2026-10-29：v3.2 追加 5 条（视频生产 4 条：maxazure/video-editing-skill 小红书/抖音/视频号三平台剪辑大流水线（80+ 平台雷区 lint + 审批收据，发布只出上传包不直传）205★（⚠️ 暂无 LICENSE）、pycodebr/heditor 风格化创意剪辑（30+ 命名风格 + 钩子换头 splice，HyperFrames 本地渲染）103★（⚠️ LICENSE 未识别）、chang416/cutcraft 对话式剪片（字幕三方案预览图 + 逐句改稿可逆）53★ MIT、Pluviobyte/awesome-talking-head-skills 口播博主动作蒸馏（5 风格 + analyzer，10-27 新库，X 原帖 @Pluvio9yte 22.8K 浏览/224 收藏，只学动作节奏、不喂样本、不克隆脸声、标注 AI 生成）；文案钩子 1 条：rediumvex/viral-hooks-skill 100 钩子公式 × 10 心理触发（每次配 3 条混搭）113★ MIT），共 146 个 skills；去重/淘汰/记信号：GitHub `claude skills` 前 15 全已入库或已淘汰（导航/ dev /安全/LinkedIn 场景不匹配先例）；Jaycheng1103/chatgpt-video-editing-skills（607★ MIT，setup + 8 步剪辑双 skill）与库内 video-use 重叠不另立；znyupup/ai-video-editing-skill（168★ MIT，旅行 vlog 自动剪辑）与本轮 maxazure 重叠、赛道更窄不堆；843645440/wechat-skill（128★，排版确定性渲染器 + 校验）与库内 md2wechat/gzh-design/wewrite 三重重叠待 X 信号再议；aiworkskills/wechat-article-skills（715★ Apache-2.0，9 子 skill 公众号一条龙，默认只写草稿箱）与库内 wewrite 同属全流程大包不堆（默认 draft + sticker 子 skill 为差异化点，记观察）；gainubi/wechat-skills（172★，无 LICENSE，2026-05-21 后未更新）与 BND-1/wechat_article_skills（318★，无 LICENSE，2026-01-16 后未更新）重叠且久未更新不收；zJay26/douyin-skills（60★）10-25 封号风险一致性先例延续不收；UnderleveledBuilder/awesome-short-drama-skills（1154★）纯目录形态先例不收；X 侧已核验：@Pluvio9yte 数字人口播 Article（2026-10-28 20:26 北京）→收录 talking-head；@liangzhu_AI LinkedIn 17-skill 帖（2026-10-28 10:20 北京，1703 浏览）即 charlie947/social-media-skills，v3.0 已淘汰（LinkedIn 核心）不重复算；其余 X 浏览器任务与 skills.sh/skillhub.cn 浏览器任务报告截至发稿仍未送达，结果待下档补记；X 全程只读无互动；热度洞察一句话：剪辑 skill 正在分化成三条线——平台过审流水线（maxazure）、风格化创意剪辑（heditor）、对话式改稿（cutcraft），而数字人口播的瓶颈已从“能不能生成”变成“动作说明书够不够具体”
- 2026-10-28 补记：v3.1 追加 2 条（视频生产 1 条：konlu/story-studio 历史/人物故事视频号一条龙（选题核实→钩子→正文→豆包配音→本地字音对齐→三画风分镜→剪映草稿导出）175★ MIT，带货与播放数据为作者自述未核验、克隆音色须自备授权音频；去 AI 味 1 条：Nanako0129/sepia 架构级去 AI 味 6 子 skill（review/refactor 最常用，Import code 导入坑已注）3526★ MIT，去 AI 味计 15→16 条），共 141 个 skills；星数刷新：lemo-opuscar 51→59 种风格、3064→8730★；迟到 X 报告闭环（只读无互动，@Hjn8899 登录态正常、未遇验证；两帖已在 v3.0 记过的不重复算）：@Tanghulu188 Story Studio→收录、@QQTeng sepia（原帖链接经 fxtwitter 展开核实为 Nanako0129/sepia）→收录、@vista8 Hallmark→库内已有（Nutlope/hallmark）仅作刷屏佐证、@liangzhu_AI charlie947→v3.0 已记淘汰不重复；去重/淘汰/记信号：tigerless-labs/autoharness 10932★ MIT（自学习 skill 层，dev 向章节不合；Windows python3 钩子静默失败为实测踩坑，记信号不收）、UnderleveledBuilder/awesome-short-drama-skills（纯目录形态，按目录先例不收；AXIS 拆解方法论记信号：短剧 skill 须用对照组实测，收藏≠会用）、Skillry/LaunchMotion（无 GitHub 仓库，平台产品不收；卖 skill 平台月入自述记市场信号）、Smaug Humanizer（仅 Hugging Face 线索，无可核验 GitHub skill 不收）、Creator Buddy（SpaceZephyr/creator-buddy 1737★，无 LICENSE；类目库已收，本库暂缓不堆，待授权补齐再议）、Obsidian skills/Cloudflare security-audit/MotionSites/skill-forge（笔记/安全/设计向或仓库路径未核实，章节不合或无法交叉验证，均不收）；X 热度洞察一句话：视频人群要一句话跑通选题到剪映草稿并挂车带货的全流程，去 AI 味人群要带依据的最小改写，同时 demo 落地与短剧套壳正被对照组实测质疑——收藏和 star 不再等于好用
- 2026-10-28：v3.0 追加 1 条（去 AI 味 1 条：larashero3-dotcom/lieflat-less-ai-tone 证据驱动中文去 AI 味（两轮实测：629 篇对照 + 270 对同题配对，约 520 万字、100+ 指标；先出检测报告、用户点头再改写复测，SKILL.md + detect.py + DETECT.md + 案例齐全）4333★（⚠️ CC BY-NC 4.0，商用接单前需作者授权），去 AI 味计 14→15 条），共 139 个 skills；去重/淘汰/记信号：X 信号 2 帖核验（只读无互动，@Hjn8899 登录态正常、未遇验证，原帖经 fxtwitter API 逐条直读核验）：@GaoXiaoxiao2022（2026-10-28 09:07 北京）推荐 lieflat-less-ai-tone→收录；@liangzhu_AI（2026-10-28 10:20 北京）推荐 charlie947/social-media-skills 17 skills 4383★ MIT 今日更新→未收：hook-generator/post-scorer 均为 LinkedIn 定制、post-scorer 真实数据需 Apify，按 sergebulaev/linkedin-skills 三次淘汰先例（LinkedIn 场景与中文搞钱人群不匹配）需求匹配不过，整库不入，reels-scripting/youtube-thumbnail 通用模块可待单拎评估；GitHub `claude skills` 前 15 全已入库或 dev/平台向不匹配；skills.sh All Time/Trending 仍老面孔为主：新冒头 uizze/uizze 71★（站内 78 万 install 严重背离，防刷量铁律不收；设计向章节亦不合）、flowkit-labs/skills 23★（reddit-automation 方法干净：人工复核后发、诚实披露，但刚过硬线且 Reddit 非中文搞钱主战场，记观察）、gencraft-labs 0★ 刷量嫌疑延续、prime-skills/runcomfy 60★ 刷量嫌疑延续、iannuttall/seo 597★（Search Console 真实数据 SEO，MCP/CLI 为主、与库内 claude-seo + geo-seo 重叠，记信号不堆）、binance-skills-hub 1095★（加密钱包 Agent、无 LICENSE、章节不合）、AliceMarket 143★（金融数据 MCP、无 LICENSE、章节不合）、ponytail 178266★（dev 向）、autonnel 5★/designed-by-ai 20★ 未达硬线、antibrow/liarjs 系规避工具不收；观察项续 hold：chengfeng-videocut（公开 Runtime 仍 v0.4.11，不满足新 Skill ≥0.5.9）、wshuyi/remotion-video-skill（433★ 仍无 LICENSE + Remotion 官方路由重叠）、500bitcoins/recast 仍 0★、xiaolu-ai26/video-close-reading 仍 0★；skillhub.cn 飙升榜：搜索引擎 799.6 万、编程专家 Pro 526.0 万、视频全能创作 114.8 万、文章去 AI 味 77.8 万，抽查视频全能创作详情页（Beatra 平台工具）无 GitHub 源码链接、无法交叉验证 0 收录；X 热度洞察一句话：去 AI 味正在从“凭感觉改写”升级为“先拿数据报告、再动手改”的证据路线——中文搞钱人群要的是改前能讲清依据、改后能复测的家伙，而不是又一张禁用词表
- 2026-10-26 晚：v2.9 追加 4 条（视频生产 2 条：andyhuo520/digital-human-koubo 一张照片出数字人口播（5 档风格+48 包装组件+先报价后生成，Renoise credits 按量付）761★、eternityspring/shuohao-skills AI 短剧 7 件套（大纲→角色→美术→剧本→走位→分镜，Node 标准库零 API 依赖）5418★；去 AI 味 2 条：op7418/Humanizer-zh 中文去 AI 味 31 条模式清单（保事实保声音，不承诺过检测）21083★、Nutlope/hallmark 网页去 AI 味 16 条硬底线+sloplint（与 kill-ai-slop 互补）36633★；注：Humanizer-zh 此前多轮记为“已有”，实查本库去 AI 味 12 条中无其独立条目、仅章节注提及，本轮补立，去 AI 味计 12→14 条），共 138 个 skills；星数刷新：video-shotcraft 12170→13855、prompt-master 14345→15116、ai-copywriter 1207→1232、qu-ai-wei 690→700、humanizer-skill 281→291、kangarooking viral-copywriting 67→74、opus-video-skills 320→345、motion-graphics-music-video 184→187、guizang-product-video 831→872、qiaomu 6229→6399、blader/humanizer 58140→61069、sweety-handdraw-video 742→891、marketingskills 54281→56714、vivy-yi 小红书 492→506；去重/淘汰/记信号：X 信号 10 帖命中（只读无互动，@Hjn8899 登录态正常、未遇验证）：Humanizer-zh、digital-human-koubo、shuohao-skills 多帖重复出现；ZJU-REAL/Easel 4115★ 为社媒 Agent 整机（OpenClaw agent + 多平台发布链路，按 autoclaw/white0dew 一致性未收）、Panniantong/Agent-Reach 103777★ 为搜索 CLI 工具非 skill 形态未收；Diagram Design 仓库名截断无法核验 + 图表设计向章节不合未收；Grok Bot 选题玩法为方法帖、非 GitHub skill 且属另一管线未收；@leo_xiaolei 手绘口播为库内 sweety-handdraw-video 进度更新不另立；xuejoker 9 项清单中 baoyu 系/blader/humanizer 库内已有、xhs-visual-director 仓库名截断无法核验；wxg8866 6 项清单全去重（awesome-gpt-image-2 提示词合集非 skill 先例）；DTC 续 hold（27★、双 owner 同名仓来源不明、SKILL.md 默认开 analytics 上报）；chengfeng-videocut 续 hold（公开 Runtime 仍 v0.4.11，不满足新 Skill ≥0.5.9 要求）；wshuyi/remotion-video-skill 仍无 LICENSE 且与 Remotion 官方路由重叠未收；skills.sh All Time/Trending 仍老面孔为主，新冒头 uizze 系 GitHub 仅 68★（与站内 75 万 install 严重背离，防刷量铁律不收）、gencraft-labs 系刷量嫌疑延续、hyperframes/remotion-dev 系库内已有；skillhub.cn 热榜轮：下载榜前列仍编程类断层领先，视频全能创作 121.6 万、去 AI 味文章工具 81.7 万、李白 93.2 万，抽查 5 详情页均无本 skill GitHub 源码链接、无法交叉验证 0 收录；X 热度洞察一句话：数字人+短剧成片 skill 正在接管视频生产章，而去 AI 味从“改写文字”扩到“网页一眼 AI 味”——中文搞钱人群要的是装上就能出片、发前能过关的整套家伙
- 2026-10-25 晚：v2.8 追加 5 条（视频生产 5 条：browser-use/video-use 对话剪片（转写稿出发+点头后剪+切点自检+project.md 记忆）29832★、JimLiu/baocut 可编辑视频（转录/双语字幕/翻译配音/剪辑一条龙，需装 App）1471★（LICENSE 文件存在但 SPDX 未识别，已警告）、nexu-io/html-video HTML 写代码出视频（文章/仓库链接→模板→本地渲染，21 模板）4754★、ahkamboh/agent-caption 本地精准字幕（强制对齐时间轴绝不漂移）38★、Mr-funny/hbg-classical-poem-silk-video 古诗国风竖屏（逐句一景+毛笔字逐字题写，需 Docker + Gemini I2V）373★），Remotion 条目安装源更新为独立仓 remotion-dev/skills（5703★，⚠️ 该仓暂无 LICENSE，已警告），共 134 个 skills；去重/淘汰/记信号：sergebulaev/linkedin-skills 5187★ 第三次复核仍淘汰——LinkedIn 场景与中文搞钱人群需求不匹配（10-17、10-21 两轮先例延续，本轮 X 17 帖亦无任何 LinkedIn 需求信号佐证；本轮初稿误收后已回滚，计数随之修正）；X 信号 17 帖命中（只读无互动，@Hjn8899 登录态正常、未遇验证）：代码做视频成竞争主线（Remotion 官方 skills 独立仓、ffmpeg-skill、8 视频 Skill 合集、火柴人更新、BaoCut、Lemo-Opuscar、Seedance 2.5+即梦流程、video-shotcraft 均已覆盖或已入库）；合集内 ahkamboh/inkling 仅 2★、ahkamboh/scrolltape 仅 4★ 未达硬线未收；Jakeschincariol/replica-skill 5505★ 与 SawyerHood/dev-browser 6698★ 为开发向、与本库搞钱+视频受众不匹配未收；Bomx/super-video-maker-skill 322★（无 LICENSE）为跨工具编排大包，与库内 Hyperframes/Remotion/ffmpeg 覆盖重叠，按整库大包先例不另立；wx4766/html-to-video 109★ 为渲染原语、与 nexu-io/html-video 重叠不堆；enesozturk/dimensional-drawing 为 UI 尺寸图设计工具、非五章优先类未收；TermiX 赚钱 Skills 平台叙事无已验证订单证据未收；小红书起号 10 Skill 合集未列具体名字无法核验、Muse 全自动运营小红书讨论记封号风险信号；skills.sh All Time/Trending 仍为老面孔，trending 冒头的 mbfinotti 销售/RevOps/广告三包 GitHub 仅 3/1/2★、limrun-inc/skills 仅 2★，站内热度与 GitHub 背离、按防刷量铁律不收；skillhub.cn 热榜轮：下载榜前 15 仍是编程类断层领先，详情页均无 GitHub 源码链接无法交叉验证 0 收录；新需求信号：短视频爆款 8 维拆解与反向二创（3.0万）、AI 视频创作师（1.1万）、AdMapix 广告投放（53.0万）、公众号爆款封面生成器（19.6万）、小红薯轮播图（5.5万）；X 热度洞察一句话：视频 skill 的竞争已从“能不能做”转向“能不能稳定批量出片、按行业卖月包”——而获客端的新变量是 LinkedIn：英文 B2B 获客正在复制 X/TikTok 的“钩子+批准后才发”打法
- 2026-10-25：v2.7 原帖复核轮追加 8 条（营销增长 2 条：sharbelxyz/x-bookmarks X 收藏夹变行动清单（拉取→分类→行动建议→定期摘要）290★（无 LICENSE，已警告）、Jakeschincariol/x-agent-skill X 账号全流程（21 钩子公式+线程+回复+主页评分+周计划+分析审计，批准后才发）41★；去 AI 味 5 条：hardikpandya/stop-slop 删 AI 痕迹三件套 18315★、MrGeDiao/shuorenhua 中文优先说人话 2257★、jzOcb/writing-style-skill 文风自动学习模板 273★（无 LICENSE，已警告）、Anbeeld/WRITING.md 人味规则集 381★、adewale/anti-slop-writing 具体细节编辑测试 21★（刚过硬线）；提示词 1 条：alchaincyf/nuwa-skill 蒸馏任何人的思维方式 35832★），共 129 个 skills；去重/淘汰/记信号：水哥AI 8 skill 对应 7 链接（X Viral 与 X Audit 同仓 Jakeschincariol/x-agent-skill），其中 rohunvora/x-research-skill 与 sergebulaev/x-skills（Humanizer 子 skill）库内已有，tweet-md/skill 1★ 与 ceoguy/x-algorithm-skill 1★ 未达硬线（库内 twitter-algorithm-optimizer 条目源自 ComposioHQ awesome 合集，非 ceoguy），alberduris/skills x-twitter 为整仓 21★ 且 X API 发布/互动管理自动化风险 + 与库内两套 X 创作包重叠，未收；Haosen 去 AI 味清单 22 名（19 附链接、3 未附链接）：stop-slop-zh 6★ 未达硬线，chatgpt-comparison-detection（HC3 语料/检测器）与 AIGC_text_detector（ICLR 论文代码）非 skill 形态，baibanbao/qu-ai-wei 73★ 同名已有更强条目（LifelongLazyLearner 690★，原帖已提醒勿混淆）不堆同名分叉，hylarucoder/ai-flavor-remover 1189★ 但仅 README 内一段 prompt、无 SKILL.md、无 LICENSE、仅 Gemini 2.5 Pro 测试，yzhao062/agent-style 725★ 为 RULES.md 通用写作规则、非打包 skill 且无 LICENSE，dongbeixiaohuo/writing-agent 439★ 为独立 Windows 写作客户端（harness，RC 版）非 skill，iniwap/AIWriteX 2143★ 为公众号全自动工具（非 skill）+ 洗稿/多账号自动发布风险；已入库去重：blader/humanizer、op7418/Humanizer-zh（已有独立 skill 在用）、zenstory-ai/oh-story-claudecode、Leonxlnx/taste-skill（v2.2 已淘汰：前端设计向，原帖亦提醒非中文改稿工具）；未附链接无法核验 3 项：openai-detector、humanize-text、De-AI-Prompt-Enhancer（仅名称线索，不认定与库内 OUBIGFA 条目同一）；Marvin Grok Bot 10 工作流属另一管线，不入本库；X 热度洞察一句话：去 AI 味已从单点改写卷成“检测→改写→文风学习”全链条，而 X 运营 skill 的分水岭是“批准后才发”——带人工点头的才配进库
- 2026-10-25 补记（skillhub.cn 热榜轮）：下载热榜前 15 + 最近更新排序第一页 24 条共 39 条，详情页均无 GitHub 源码链接（ClawHub 来源链接不等于 GitHub 源码，已区分），无法做 star + 更新时间交叉验证，0 收录；需求信号：编程类仍占榜首（编程大神 900.7 万、搜索引擎 856.8 万、编程专家Pro 526.5 万），视频全能创作（短视频/图片/音乐/音频/配音/口播/数字人）117.2 万；最近更新页 humanizer-zh 同名不同作者出现 6 条（1.2 万–24.3 万，含 1 条 Pay Skill），中文去 AI 味是站内高频新上类目，与 X 侧去 AI 味信号一致；“最近上新”实际为按更新时间排序，非严格首发
- 2026-10-25：v2.6 X 信号轮追加 1 条（营销增长：kangarooking/x-skills X 推文创作全链路（收集→筛选→创作→草稿箱，人工点头后才真发）340★），共 121 个 skills；星数刷新：qu-ai-wei 660→690、calesthio/OpenMontage 70348→71617；X 信号 10 帖命中（只读无互动，@Hjn8899 登录态正常、未遇验证）比对：MarketerHub Vox 风格工作流（/skill-creator 库内已有 + Higgsfield Seedance 2.5，已覆盖）、Seanvon OpenMontage 帖（库内已有，仅刷新星数）、Haosen Anatomy × OpenMAIC（Anatomy 库内已有；OpenMAIC 本体为清华多智能体互动课堂教育平台、章节不匹配，未收）、Haosen 去 AI 味 3 步法（方法帖无新增可核验仓库，记需求信号）、luogo 双 skill 帖（x-create 即本次收录的 kangarooking/x-skills，qu-ai-wei 库内已有仅刷新）、月明抖音文案抓取系列（zzyong24/moonlit-douyin-transcribe 等 4 仓均 0–2★，未达硬线，未收，但记抖音文案抓取拆解需求信号）、水哥AI X 运营 8 skill 帖与 Marvin Grok Bot 10 工作流（原帖复核进行中，结果另起批次）、陈大黄变现风险讨论（skill 文件纯 Markdown 无防复制、闲鱼 1 元打包，记市场信号：卖文件难跑通，价值在装上能用的服务）、农夫求推荐帖（superpowers 系 dev 向先例，未收）；skillhub.cn 热榜轮仍进行中，结果另起批次；X 热度洞察一句话：中文搞钱人群此刻要的是“选题→成稿→草稿箱”这种人工点头的完整运营流水线，而不是单点提示词
- 2026-10-25：v2.5 追加 8 条（视频生产 6 条：xixihhhh/ai-short-drama-skill Dramake 文字到 AI 短剧成片（故事诊断→剧本→角色母版→分镜→模型与费用路线→配音→质检，父段验收门禁）71★、muxia0396/novel-to-ai-short-drama-skill 小说改编导演台本（时长账本逐镜秒数闭合）31★、YvonneMovingon/short-drama-skills 短剧 prompt 规则 7 件套（叙事拆解/情绪/动态/连贯拆分/三档润色，LuxReal 管线沉淀）95★、gnipbao/codex-whiteboard-video-skill 本地白板手绘视频（30 风格，Codex 适配本地引擎）343★、tuzhechen2005/opus-video-skills Opus 5.5 纯代码视频（水彩动画+动态字体，零生成模型）320★（LICENSE 文件存在但 SPDX 未识别，已警告）、makevoid/motion-graphics-music-video-skill Opus 5.5 音乐 MV 全流程（GPT 生图+MiniMax H3 动画，成本约 $30 Fal + 3M tokens / 3 分钟歌已注明）184★；去 AI 味 2 条：ilien-dev/quiron 量得出来的英文去 AI 味（对照人类写作实测基线测量，博客/小说/西班牙语语体）60★（AGPL-3.0 已声明）、numen-tech/slopornot 5 遍去味+声音指纹+本机检测（7 语）56★），共 120 个 skills；星数刷新：sergebulaev/tiktok-skills 69→90（库内已分拆 tt-hook-scripter / tt-trend-mapper / tt-humanizer 三条同步刷新，其余子 skill 与库内已有文案/营销条目重叠不另立）；淘汰/去重/记信号：GitHub `claude skills` 前 15 全已入库或 dev/安全/汽车向不匹配；`xiaohongshu skill` 关键词 white0dew/autoclaw（封号风险先例）/ freestylefly（付费 API 包装）/ DeliciousBuding（自动发布类）/ ibreez3（已淘汰）均未收，kiki-lgtm-dot/xiaohongshu-skill（21★，同作者 light-retro 已收不堆作者），Angiin 19★ / OnePieceLwc 18★ 未达硬线；seedance 关键词 robonuggets/LeoYeAI/alchaincyf 均已入库；营销整库大包 nowork-studio/notfair-plugin（4056★）/ ericosiu/ai-marketing-skills（3724★）/ aaron-he-zhu/aaron-marketing-skills（3012★）/ zubair-trabzada/ai-marketing-claude（2795★）/ kostja94/marketing-skills（1061★）/ LeoYeAI/openclaw-marketing-skills（1049★，LICENSE 未识别）与库内 marketingskills / irinabuht 整库重叠，不另立；zJay26/douyin-skills（59★，MIT，含发布/点赞/评论互动动作，按 white0dew/autoclaw 封号风险一致性未收）；mediastormDev/dream-to-video-skill（373★，解梦视频赛道窄+即梦网页登录自动化链路脆弱，暂缓记观察）；Agentchengfeng/chengfeng-videocut-skills（3128★，官方 README 当日仍声明公开 Runtime v0.4.11 不满足新 Skill ≥0.5.9 要求、装上不能用新工作台命令，v2.3 hold 延续）；wshuyi/remotion-video-skill（430★，无 LICENSE，与库内 Remotion 官方路由 + video-shotcraft 重叠，未收）；UnderleveledBuilder/awesome-short-drama-skills（772★，纯目录形态，按目录先例未收，但记短剧需求信号）；LearnPrompt/awesome-seedance（2266★）/ zhuyansen/awesome-claude-video-skills（886★，提示词/导航合集形态，未收）；zczjyq/de-AIGC-skill（32★）/ crabin/paper-humanizer-skill（128★，学术论文向，按 crabin 先例未收）；500bitcoins/recast 仍 0★（10-24 更新，继续记观察）、xiaolu-ai26/video-close-reading 仍 0★（继续记观察）、mcncarl/jianying-headless 已 404；skills.sh All Time/Trending 均为老面孔（vercel-labs/mattpocock/hyperframes 已入库/superpowers 分叉系/open.feishu.cn），gencraft-labs 15.2K trending 对应 GitHub 0★（刷量嫌疑再验证）、flowkit 20★ 未达 >20 硬线、autonnel 5★ / mbfinotti 3★ 未达标、antibrow 反检测浏览器 20★ 未达硬线且属规避工具；skillhub.cn 热榜轮与 X 信号轮进行中（browser task 已派，只读），结果另起批次补记；热度洞察一句话（GitHub 侧）：AI 短剧生产成套出现（Dramake/小说改编/短剧 prompt 规则三连发）+ Opus 5.5 纯代码视频路线成型，视频 skill 的主攻方向从单点生成转向“成套生产线”
- 2026-10-24：v2.4 追加 3 条（视频生产 1 条：sugarforever/boring-video-studio 视频策划全链路（选题研究→成文→节拍→口播稿→分镜→故事板→HyperFrames 成片，@verysmallwoods 日常在用、口播稿去 AI 味调教实证）184★；营销增长 2 条：kiki-lgtm-dot/light-retro-collage-xiaohongshu-skill 轻复古拼贴风小红书知识图文（选题→查证→文案→插画→动态排版→质检）25★、Irixil/xiaohongshu-skill 小红书知识图解+长文排版发布（Gate 0–5 选题严选+母稿保护+发布门）22★（无 LICENSE，已警告）），共 112 个 skills；淘汰/去重/记信号：ibreez3/xiaohongshu-skill（21★，自动发布/评论/点赞类，与 white0dew/autoclaw 同属封号风险，按一致性未收）、500bitcoins/recast（0★ 当日新建，Seedance 2.5 改视频 skill、SKILL.md 方法论真实，但零 star 按 video-close-reading 先例记观察）、kiki-lgtm-dot/xiaohongshu-skill（21★，同作者 light-retro 已收不堆作者，记信号）、Haseebi-khan/Claude-Skills（6★ 未达标）；skills.sh All Time/Trending 均为老面孔（vercel-labs/mattpocock/hyperframes/superpowers 分叉系/runcomfy/open.feishu.cn），autonnel/mbfinotti 销售类 trending 但 GitHub 仅 5★/1★（10-19 已淘汰），无新货；skillhub.cn 飙升榜（搜索引擎 799.6万/编程专家Pro 526.0万/视频全能创作 114.8万/文章去AI味 77.8万）全站内无 GitHub 源码、无法交叉验证，0 收录（新需求信号：标书写作专家 37.1万、DKnownAI Guard 10.1万）；GitHub `claude skills` 前 15 全已入库或 dev/安全/汽车向不匹配，`xiaohongshu skill` 关键词命中今日 2 条收录；X 信号 11 帖命中（只读无互动，@Hjn8899 登录态正常、未遇验证）：Seedance 2.5 改图/改视频 edit 类 skill 48h 内出现 3 个独立实现（@500altcoins 开源版、scenario.com 版、Dola 版）成最热视频趋势；中文口播稿去 AI 味是视频圈真实痛点（@verysmallwoods）；@CrazyKaomei 火柴人 skill 目标冲击 1w star（库内已有）；指定账号 9 个近 3 天无 skills 推荐帖；X 热度洞察一句话：视频制作类 skill 正在从"生成"转向"改"——Seedance 2.5 edit 让"改一个细节、其余不动"成为新刚需，而中文搞钱人群要的是"选题到发布"的完整中文流水线
- 2026-10-22：v2.3 X 信号轮追加 10 条（视频生产 4 条：rossark0/rossark-motion-skill SVG 转 60 帧专业动画方法论+小引擎 296★、Vincentwei1021/anything2explainer 黑底 MG 科普讲解视频全流程（Remotion+QC）2687★（无 LICENSE，授权警告）、garycaogan/pixel-diary 像素日记爆款复刻引擎（B 站 3 天 100 万播放实证）10★、kajisho5/ffmpeg-skill 本地视频剪辑 42 工具+MCP 2048★；文案钩子 1 条：modengsir/shangdan-post-skill 商单前置质检员（Brief 拆解+钩子）1★ 新库待观察；营销增长 4 条：dreammis/social-auto-upload 多平台一键分发 18 skills 15731★、isjiamu/gzh-design-skill 公众号排版引擎 4119★（AGPL-3.0 已声明）、geekjourneyx/md2wechat-skill 公众号创作发布 CLI 3753★（Source-Available/BSL 变体，已警告非 OSI 开源）、xianyu110/ecommerce-image-skills 12 电商出图 skills 108★；去 AI 味 1 条：yetone/kill-ai-slop vibe-coded 网页去 AI 味扫描器+field guide 1377★），共 109 个 skills；淘汰/去重/记信号：Kianzzz/xilo-opus-video（库内已有 v2.1，去重）、luongnv89/claude-howto（43348★，Claude Code 实战指南、dev 向不匹配）、perryyang/hn-ai-slop·codetips/avoid-ai-writing（404 无效）、mcncarl/jianying-headless（剪映自动化热点，但律师函存续风险，hold）、Agentchengfeng/chengfeng-videocut-skills（3119★，公开 Runtime 仍不满足新 Skill 要求、装上不能用，hold）、travisvn/awesome-claude-skills（纯目录平台，buildwithclaude 先例）、HarleyCoops/Math-To-Manim（2799★，数学动画垂类过窄，记观察）、xiaolu-ai26/video-close-reading（0★ 自荐新库，方法论真实，记观察）；skills.sh All Time/Trending 均为老面孔（mattpocock/hyperframes/superpowers 分叉系/runcomfy/open.feishu.cn），无新货；skillhub.cn 热榜仍全站内无 GitHub 源码（搜索引擎 709.7万/编程专家 521.2万/视频号爆款拆解 70.5万/文章去AI味 76.3万），无法交叉验证，0 收录；GitHub `claude skills` 前 15 全已入库或 dev/安全/汽车向不匹配，新建仓（9-10 月）最高仅 7★；X 信号 40 帖全开原帖核实（只读无互动）：内容分发/获客类 skill 成新热点（social-auto-upload/gzh-design/md2wechat/ecommerce-image）、Opus 5.5 代码渲染视频路线成体系（@yaohongan2025 长文 5 路 10 skill）、去 AI 味成独立热门品类（三帖共推）、Lemo-Opuscar 史诗级更新带动多人实测（库内已有）；X 热度洞察一句话：中文搞钱人群此刻要的是"装上就能产出内容、吃到分发红利"的交付型 skill，分发环节（上传/排版/出图）比生产环节更缺
- 2026-10-20：v2.2 追加 1 条（视频生产：calesthio/OpenMontage AI 剪辑工作室（12 条制片流水线、49 个 skills：HeyGen 一键成片/Remotion 代码成片/数字人/真实素材混剪，9K fork 13% fork 比有机验证）70348★），共 99 个 skills；淘汰/去重：sergebulaev/linkedin-skills（5007★，三维中需求匹配不过——LinkedIn 场景与中文搞钱人群不匹配，10-17 一致性先例延续）、davepoon/buildwithclaude（3661★，纯目录平台、无自有 SKILL.md）、addyosmani/agent-skills（109011★）、Leonxlnx/taste-skill（99921★）、tt-a1i/archify（86516★）、obra/superpowers（302645★）、Jakeschincariol/replica-skill（3757★）、aldegad/sprite-gen（2943★，均为 dev/coding-agent 向、与五章节不匹配；星数暴涨但场景错配）；skills.sh 榜单仍是老面孔（superpowers 分叉系/runcomfy/open.feishu.cn/microsoft-azure），无新货；skillhub.cn 热榜（视频号爆款短视频拆解 69.3万/视频号挂车爆单脚本 40.3万/文章去AI味 72.2万）仍全站内无 GitHub 源码、无法交叉验证，0 收录；X 信号 9 帖命中（只读无互动）：@leo_xiaolei sweety-handdraw-video v1.4 重大更新 571赞/5.5万浏览（库内已有，覆盖领先）、@xoyif63862452 小红书起号 7 skills 流水线（AgentReach/openCLI 无仓库、其余库内已有）、@ClaudeCodeBase（日文）视频 AI 5 选含 OpenMontage→收录；X 热度洞察一句话：中文搞钱人群此刻要的是"装上就能产出内容、吃到视频/图文补贴"的交付型 skill
- 2026-10-19：v2.1 X 信号轮追加 6 条（视频生产 5 条：HeyChengC/wallstreet-explainer 华尔街式财经解读短片（真实素材+数字可视化+钩子自选）172★、threerocks/sweety-handdraw-video 手绘口播视频（逐笔描线+配音对齐，v1.4.1）742★、Kianzzz/xilo-opus-video Opus 5.5 写代码做视频（三方案竞标+brief.md 复用）207★、chuspeeism/dashi-animationstyle 7 套风格中文知识口播动画 100★、op7418/guizang-product-video-skill 软件更新宣传片（复用真实产品组件）831★；营销增长 1 条：marswaveai/skills ListenHub 一稿多发内容复用包 79★），共 98 个 skills；淘汰/记信号：feicaiclub/ad-storyboarder（3★ 未达硬线，广告成本账方法论记信号）、LearnPrompt/ai-news-radar（1785★，SKILL.md 为项目维护用、本体是监控工具，TrendRadar 先例，记早报新闻雷达需求信号）、Vincentwei1021/mg-styles-15（1336★，风格画廊无 SKILL.md、非 skill 形态）、threeaus/creator-style-kit（2★）、maobidao/douyin-oral-script-writer（0★）、ceoniuer/liuren-writing-skills（0★，刘韧去 AI 味写作 skill 记工具化信号）、wtt-code-animation-studio/archival-doc（无相关仓库）、bojieli/agentreach（181★，SSH 远程执行工具、章节不匹配）；@boz_wave 短剧 83 仓库帖（截图无仓库链接不可验证，盲测"10 个编剧 skill 仅 5 个三局全赢"记需求信号）、@xoyif63862452 小红书 7 skills（NotebookLM/Remotion/Humanizer-zh/baoyu 库内已有，AgentReach/openCLI 无仓库，流水线方法论记信号）、Answer me with HTML（dev 向，10-18 已淘汰）、@bkdgiffug Seedance Skill OS（库内已有，去重）；指定账号 6 个近 48h 无 skills 推荐帖；X 全程只读无互动、未遇真人验证
- 2026-10-19：v2.0 追加 4 条（视频生产 4 条：higgsfield-ai/skills Higgsfield 官方 8 件套（30+ 模型生成+Marketing Studio 品牌广告+Virality Predictor 爆款打分）1326★、robonuggets/seedance-skill App/SaaS 液态玻璃宣传片（截图→成片，成本透明 $3/10秒）107★、LeoYeAI/seedance-skills 导演级 Seedance prompt OS（28 模块化 skills+6 国语言）47★、alchaincyf/seedance-skill 白模驱动几何级精确运镜（渲染前几何体检+提示词从实测几何生成）41★），共 92 个 skills；淘汰/去重：cv-cat/XhsSkills（228★，小红书爬虫 API 封装，与 white0dew/autoclaw 自动发布类同属封号风险，按一致性未收）、gencraft-labs/skills（skills.sh 24h trending 15.4K install 对应 GitHub 0★，刷量嫌疑）、autonnel/autonnel-skills（5★ 未达标）、mbfinotti/sales-skills（1★ 未达标）、noahneancy-byte/create-xiaohongshu-ai-explainers（24★，仅一句 README、无 SKILL.md）、zhangpeicheng8788-ux/xhs-skill（46★，自动发布类）、11Yuxuanyang/seedance-viral-forge（20★ 未达硬线）、zhouwei713/fpv-immersive-video-prompting（94★，同作者 seedance-prompt 已收不堆作者，先例延续）；skills.sh Trending(24h) 新面孔交叉验证：higgsfield-ai 真热门收录、gencraft-labs 刷量嫌疑淘汰；skillhub.cn 最近上新 10 条（WorkBuddy 指南 13.8万/搜索引擎 406.3万下载等）与下载热榜 10 条（编程类 400万+）均无 GitHub 源码链接、无法交叉验证，0 收录；X 热度洞察 browser task 进行中，结果另起 v2.1 批次
- 2026-10-18：v1.9 追加 3 条（视频生产 3 条：alchaincyf/huashu-art-motion 中文艺术动画（36 实做风格+16 研究配方+9 种解说动画语法：镜头表→lint→逐镜渲染→拼接→QA→交付全链路）4381★、lemomo-ai/lemo-opuscar 51 种影片风格提示词（每种配纯代码样片+OPUSCAR 98 奥斯卡百年风格库，零视频模型成本；风格为 Opus 5.5 调优已注明）3064★、echris6/motion-video-kit 商业级动态影片（28 部 SaaS 发布片提炼的动效语法+独立 critic 评审循环+可测量质量门）1139★），共 88 个 skills；star 复核：blader/humanizer 55953→58140（去AI味英文原版，持续上涨）；淘汰/去重：wheresryan22/anatomy（16094★，库内已有）、rehan-remade/universal-modder（8356★，游戏 mod 向）、QingYunA/answer-me-with-html（3704★，dev 向）、kaankiziltug/logo-design-skill（3697★，设计向）、nanaism/yomiyasu（2232★，日语改写）、oil-oil/oil-ui（1768★，UI 设计向）、mikehasa/golive-skill（1300★，部署工具）、Arekejoker/qwen21-nsfw-pose-skill（2945★，NSFW 调性不符）、alirezarezvani/claude-skills 整库（28372★，marketing 子 skills 与库内 coreyhaines31 同源重叠、video-content-strategist 为空壳）；skillhub.cn 飙升榜可读（编程专家 518万/搜索引擎 294万/视频全能创作 102.4万/视频号爆款拆解 57.5万），视频创作类下载仍旺记为需求信号，但全站无 GitHub 源码链接无法交叉验证，0 收录；skills.sh 榜单仍是老面孔（mattpocock/superpowers 分叉/runcomfy/open.feishu.cn/microsoft-azure），无新货；X 侧：2026-10-18 23:58 起浏览器环境被 X/Google 风控拦截，kk 指令 DRAFT-ONLY、禁用 browser task，本轮 X 信号缺席，改用公开网页搜索补市场洞察——近 48h 中文社区无新的 skills 推荐帖信号，站外 AI 副业文章（内容接单/AI 短剧/数字人口播/GEO 咨询）佐证"去AI味+内容生产流水线"仍是搞钱人群核心需求

- 2026-10-17：v1.8 追加 5 条（视频生产 3 条：Jakeschincariol/youtube-agent-skill YouTube 频道全链路（11 skills+6 个 Python 工具：21 钩子公式写脚本打分/标题缩略图质检/剪辑决策清单/留存分析）1583★、AirsupHQ/machine-skill 工程机械 3D 动画（一句话描述→可交互 3D→一键成片）286★、lhlGitHub/hand-drawn-storybook-animation-skill 手绘水彩动态绘本（浏览器实时作画+豆包配音+双语字幕）36★；营销增长 2 条：Jakeschincariol/instagram-agent-skill IG 账号全链路（26 钩子公式+主页诊断+自带 humanizer）1724★、Jakeschincariol/founder-skill 创业想法验证（董事会框架挑刺+100 买家代理跑购买场景）906★），共 85 个 skills；淘汰 AirsupHQ/factory-skill（20★ 未达硬线）、howardz27/poster-generator-skill（19★ 未达硬线）、Jakeschincariol/linkedin-agent-skill（2251★，LinkedIn 场景与中文搞钱人群不匹配，与 sergebulaev/linkedin-skills 一致性淘汰）、master-skills/trader-skill/promptmaster-skill（75/40/39★ 未达标）、arena-skill（702★，AI 对打 dev 玩向）；去重 @dontbesilent dbs-title-cover-intro（dbskill 库内已有）、@xl_lottie 视频动画制作（即 wheresryan22/anatomy 库内已有）；skillhub.cn 最近上新 12 个全无 GitHub 源码链接、无法做 star+更新时间交叉验证，0 收录；skills.sh 榜单仍是老面孔（vercel-labs/mattpocock/hyperframes/superpowers 系刷量嫌疑/runcomfy/open.feishu.cn/microsoft-azure），无新货；X 信号源 7 帖命中（48h 窗口，宁缺毋滥）：@HaileyAILabs 手绘绘本 32.9K 浏览（全场最高）→收录、@cywcycw machine-skill 帖→收录、@CY160909 7 设计 skills（仅 poster-generator-skill 有仓库但 19★ 淘汰）；记信号不收录：@7998l201 贴图风格包（t.co 短链截断无法验证仓库）、@krikwangcy 闲鱼 CAD skills（无公开仓库，需私信）、@xiaohu 自研视频 skill（无 skill 名/公开链接）；指定账号 10 个（@dotey/@xiaohu/@Barret_China/@jesselaunz/@rowancheung/@CrazyKaomei/@lewangx/@mranti/@op7418/@wlzh）近 48h 无 skills 推荐帖
- 2026-10-16：v1.7 X 信号轮追加 10 条（视频生产 3 条：dexhunter/seedance2-skill Seedance 2.0 提示词（中英双版）4322★、Vincentwei1021/video-shotcraft 镜头配方卡+Remotion 12170★、liyupi/ai-promo-video-maker 产品宣传片全流程 304★；文案钩子 1 条：dontbesilent2025/dbskill 选题与 Hook 诊断（4176 知识原子，CC BY-NC 4.0）10708★；营销增长 6 条：mvanhorn/last30days-skill 跨平台热源研究 64489★、helloianneo/ian-xiaohei-illustrations 小黑手绘配图 12607★、rohunvora/x-research-skill X 调研 agent 1244★、sergebulaev/x-skills X 营销工具集 137★、ponyodong2026/ponyo-cover-anchor-system 小红书封面锚点 195★、JimLiu/baoyu-skills 宝玉 20+ 效率 skills 26716★），共 80 个 skills；淘汰 aaaronmiller/create-viral-content（75★，star 太弱无热度佐证）、adrianpunk/Punk-Skill（1325★，商业用途需书面付费授权，与搞钱用途冲突）、bobobo2026/explainer-video（0★ 未达标）、TheMattBerman/x-algo-skill（68★，热度弱）、wshuyi/x-article-publisher-skill（873★，纯发布工具无方法论）、LunarXuan/image-prompt-reverse（529★，生图向，章节不匹配）、nexu-io/html-anything（9143★，HTML 生成，dev/设计向）、QianXiguaAI/video-privacy-blur（小众工具，需求弱）；X 信号源：@nicebabycat/@fhwofjow51260/@GitHub_Daily/@voidJan/@starkljm/@superfang119/@kafkaup/@b70670555886391/@Lonely__MH 等 12 帖命中（48h 窗口，宁缺毋滥）；记信号不收录：@Williamsungo 外快清单（链接截断无法验证）、@kaitoxhacker SEO 方法论（无仓库）、@xiaohu Opus 5.5 展示帖（无具体 skill）、@vista8 skill 行业讨论（无推荐）
- 2026-10-16：v1.6 追加 5 条（营销增长 3 条：vivy-yi/xiaohongshu-skills 小红书 139 技能知识库 492★、AgriciDaniel/claude-seo 全栈 SEO 审计系统（26 子 skill）19053★、zubair-trabzada/geo-seo-claude AI 搜索 GEO 专项 11067★；去 AI 味 2 条：LifelongLazyLearner/qu-ai-wei 简体中文去 AI 味改写 660★、Aboudjem/humanizer-skill 55 模式检测+5 人声 281★），共 70 个 skills；淘汰 autoclaw-cc/xiaohongshu-skills（1974★，真实账号自动发布/互动，封号风险，与 white0dew 同类）、DeliciousBuding/xiaohongshu-skill（42★，同类自动化）、freestylefly/xiaohongshu-skills（97★，付费 API 包装，本体无方法论干货）、crabin/paper-humanizer-skill（127★，学术论文向）、robpalmer99/claude-code-copywriting-skills（41★，库内已有更强同类 ai-copywriter）、jherrodthomas/automotive-skills-suite（3226★，汽车工程向，章节不匹配）、Jakeschincariol/replica-skill（2839★，应用逆向工程向，章节不匹配）；skillhub.cn 全站详情页无 GitHub 源码链接、无法交叉验证，0 收录（但去 AI 味类下载极旺：李白.Skill 88.4万、文章去AI味工具 62.4万，记为需求信号）；skills.sh 榜单仍是老面孔（open.feishu.cn/mattpocock/superpowers 分叉/runcomfy），无新货；X 热度洞察 browser task 进行中，结果另起 v1.7 批次
- 2026-10-15：v1.5 追加 15 条（视频生产 8 条：Jane-xiaoer/claude-skill-video-transcribe 视频转文字 231★、hyperframes 5 子 skill——faceless-explainer 无脸讲解视频、talking-head-recut 口播/访谈包装、motion-graphics 动态图形短片、music-to-video 音乐卡点视频、embedded-captions 特效字幕（主库 64,282★ 当日更新，双高验证）、kaomei/stickman-video-director 火柴人动画 2124★（@CrazyKaomei 推荐帖 21K 浏览）、op7418/Youtube-clipper-skill 长视频切片 2240★；文案钩子 3 条：zenstory-ai/oh-story-claudecode 网文工具箱 7605★、KKKKhazix/khazix-skills 卡兹克长文写作 21427★、claude-world/notebooklm-skill 研究转内容 471★；营销增长 4 条：Xiangyu-CAS/xiaohongshu-ops-skill 小红书全链路 2428★、op7418/guizang-social-card-skill 小红书图文 7540★、op7418/guizang-ppt-skill 杂志风演示稿 28013★、imraywang/wewrite 公众号全流程 3464★），共 65 个 skills；淘汰 superpowers 系 7 分叉 + prime-skills/runcomfy-agent-skills（skills.sh 数十万 install 对应 GitHub 0–55★，刷量嫌疑再验证）、pr-to-video（GitHub PR 转代码讲解，dev 向）、slideshow（交互式 deck 非视频形态）、hyperframes 技术参考类子 skill（keyframes/animation/creative/audio/studio/registry/media-use/figma/remotion-to-hyperframes，已有 cli/core/general-video 覆盖，不凑数）、feichanggege/pderr-short-video-skill（18★ 未达标）、white0dew/XiaohongshuSkills（3503★，自动发布/评论，SKILL.md 自带封号风险警告）、Weizhena/Deep-Research-skills（2361★，章节不匹配）、gzlliyu/generate_article（92★，纯脚本非 skill）、sansan0/TrendRadar（62924★，独立监控工具非 skill）、freestylefly/awesome-gpt-image-2（提示词库非 skill）、LangGPT/linexjlin/GPTs/lijigang/prompts（提示词合集非 skill）；去重 openakita content-research-writer / qiaomu-anything-to-notebooklm / marketingskills / Humanizer-zh（库内已有）；skillhub.cn 热榜仍为通用"专家.Skill"无 GitHub 可验证，0 收录；X 侧记信号不收录：YouMind youtube skill（平台内无公开仓库）、@HastyRick135248 网盘打包（无具体仓库名）、@densancar 广告仿写 skill（非公开仓库）
- 2026-10-13：v1.4 X 信号轮追加 2 条（wheresryan22/anatomy 概念可视化演示 7762★、jimliu/baoyu-design Claude Design 本地运行 4344★），共 50 个 skills；淘汰 vercel-labs/skills（34264★ 基础设施工具、无 SKILL.md，不符合收录标准）、101-skills/superpowers（7★）与 qu-skills/superpowers（3★，榜单高 install 均为刷量嫌疑）、travisvn/BehiSecc awesome-claude-skills（纯链接列表，库内已有两个同类）、Jeffallan/claude-skills·SnailSploit/Claude-Red·SawyerHood/dev-browser·juliusbrussee/caveman·nextlevelbuilder/ui-ux-pro-max·emilkowalski/skills·vercel-labs/agent-skills·obra/superpowers（dev/设计/安全向，与五章节需求不匹配）、designed-by-ai/skills（15★ 未达标）、scrapegraphai/just-scrape（CLI 非 skill 形态）；skillhub.cn 新上新 10 个全无 GitHub 源码不可验证、热榜通用"专家.Skill"需求不匹配，0 收录
- 2026-10-13：v1.3 X 信号轮追加 6 条（mortiflix-oss 本地动态设计 593★、xhs-account-teardown 小红书账号拆解 66★、xhs-product-picker 选品 120★、qiaomu-seo 446★、xyskill 中文商业操盘 79★、cangjie-skill 知识蒸馏 11247★），共 48 个 skills；淘汰 genmedia-labs/skills（与 runcomfy 刷量生态关联、27★ 未达双高）、flowkit-labs/skills（16★）、analyze_xhs_blogger_skill（404 无效）
- 2026-10-13：v1.2 追加 3 条（qiaomu-anything-to-notebooklm 内容转播客 6229★、irinabuht12-oss/marketing-skills 广告审计整库 4398★、hyperframes product-launch-video 产品发布视频），共 42 个 skills
- 2026-10-12：v1.1 追加 P0 三套（marketingskills 9 条、Hyperframes 4 条、Remotion 1 条），共 39 个 skills
- 2026-10-12：v1 首版，25 个 skills（12 个源仓库深读提炼），每日深度比对分析持续收录中
