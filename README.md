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

## 文案钩子（5 个）

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

---

## 营销增长

> 8 个 skill：X/Twitter 增长、广告拆解、文案生产、YouTube 研究、TikTok 热点全覆盖。每个条目不点源链接也能拿走 80% 价值。

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

---

## 去 AI 味（2 个）

> 注：op7418/Humanizer-zh 不在本批次提炼范围（已有独立 skill 在用），以下两条均为英文原版技能的人味清单。

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

- 2026-10-12：v1 首版，25 个 skills（12 个源仓库深读提炼），每日深度比对分析持续收录中
