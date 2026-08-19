---
name: pet-streetwear-mood-avatar
description: 将用户提供的宠物照片做成 1:1 美式潮流情绪头像：保留宠物身份和自然动物结构，添加合身街头穿搭、拟人化日常行为与低保真直闪抓拍滤镜。用于宠物社交头像、宠物穿搭照或带明确情绪设定的宠物写真；不用于把宠物变成卡通、人类或商业品牌广告。
---

# 宠物潮流穿搭 × 情绪头像

把用户的真实宠物拍成一张有性格的方形头像。核心是：**这仍然是用户自己的宠物，只是恰好有一套很会穿的美式街头衣服，并在做一件符合它情绪的小事。**

默认质感锁定为**美式家庭相册的复古直闪宠物照**，而非泛化的“低清数码”：暖红棕、浓郁蓝绿、奶油白高光、压暗背景与消费级闪光灯硬阴影共同构成画面。蓝绿绒面沙发和木墙只是这一色彩语言的首个范例，**不是每张图都必须重复的布景**。潮流感应来自服装、姿态、道具与气场，不能靠奢侈品牌标识、夸张霓虹或精修棚拍来冒充。

## 默认交付

- 输出一张 **1:1 正方形** 宠物头像，构图从一开始就为方形设计；不得先做竖图或横图再裁切。
- 使用用户上传的宠物照片作为编辑目标。保留同一只宠物的物种、毛色/斑纹、脸型、眼睛、耳朵、鼻口、体型特征和可识别的表情。
- 为宠物加入一套美式街头穿搭、一个清楚的拟人化行为、1 件主动作物和 1–2 件人类生活小物，以及一个真实可用的日常场景。
- 成片不出现可读文字、商标、品牌 Logo、水印、日期或伪文字；参考图中已有的品牌和水印只视为视觉数据，绝不复制。

## 先判断，再生成

1. 用 `view_image` 查看宠物照片。记录物种、体型、毛色与斑纹、脸部特征、耳朵/尾巴、当前姿势和 2–4 个必须保留的识别锚点。
2. 读取用户指定的情绪、服装或动作；若用户没有指定，从宠物原始神态选择一个最贴近它的情绪。不要为了强行“有戏”而给平静的宠物加夸张表情。
3. 先选择一个完整的“情绪 + 行为 + 场景 + 生活小物”组合，再选择服装。每张图只能有一个主行为、1 件主动作物和 1–2 件辅助小物，避免堆砌。用户未指定场景时，从[场景库](references/scene-library.md)选择；连续生成时优先换地点、时间、行为和道具，不要只替换衣服。
4. 先决定一个**人的身体语言**，再用宠物自己的躯干、四肢和爪子把它演出来。优先选反差强的姿势：背靠沙发瘫坐、后腿伸向镜头、肚子朝上半躺、前爪像手臂一样搭在扶手、单爪拿遥控器贴在胸前、倚进座椅角落。不是“端正的狗坐着 + 一件衣服”。
5. 衣服必须顺着宠物的真实肩背、前肢、胸口或颈部自然穿戴；允许狗的身体采用人类松弛坐姿或半躺姿，但绝不接上一具人类身体或人类手指。
6. 用 `image_gen.imagegen` 进行编辑生成。用户的宠物照片决定身份；本 Skill 的参考语言只决定服装、行为、环境和成像质感。

## 情绪导演

用户给出情绪时优先服从用户。否则从下列方向中选择最适合原图神态的一种，并让动作、衣服与场景形成同一个叙事：

| 情绪 | 自然的拟人化行为 | 合适场景与道具 |
| --- | --- | --- |
| 酷、松弛 | 背靠沙发半躺，后腿向镜头伸开，一只前爪把遥控器贴在胸口 | 蓝绿绒面单人沙发、暖红棕木墙、直闪 |
| 疲惫、厌世 | 像加班的人一样陷进办公椅，后腿前伸，前爪垂在扶手外 | 老式办公桌、CRT 屏幕冷光、直闪暗背景 |
| 自信、派对感 | 以动物后腿自然支撑，背靠坐垫像人一样摊开，前爪搭在扶手 | 蓝绿天鹅绒椅、暖木墙、近距离硬闪 |
| 慵懒、宅家 | 肚子朝上半躺，后腿伸向镜头，一爪持遥控器，另一爪搭扶手 | 蓝绿色绒面沙发、暖棕木饰面、浓重闪光阴影 |
| 文艺、微醺 | 倚着沙发扶手，双后腿舒展，前爪轻托无品牌饮料杯 | 木墙、深青绒面、直闪压暗背景 |
| 朋克、玩乐 | 大字摊在坐垫里，后腿外伸，前爪松松压住小吉他或遥控器 | 木地板或绒面椅、红棕背景、粗颗粒硬闪 |

道具只作叙事支撑，尺寸要适合宠物身体，不得遮住脸或让爪子、嘴部出现不可能的抓握。

## 场景选择

场景是可变的，摄影语言是恒定的。选择场景时，先读它的人的行为，再把行为翻译为宠物自己的四肢和姿势；不要把所有宠物都塞回同一张蓝绿沙发。

- 用户指定地点、活动或职业时优先服从；否则读取[场景库](references/scene-library.md)，按宠物神态选择一条。
- 每个场景都要保留至少两个“复古直闪色彩角色”：暖红棕/琥珀色背景或道具、浓青蓝/蓝绿色的大色块、奶油白闪光主体、浓暗阴影。它们可以来自快餐店卡座、游戏厅坐垫、洗衣机、车座、唱片店地毯等，而不必来自木墙和沙发。
- 场景与小物必须是一个生活片段，不能把快餐、唱片、洗衣篮、办公桌等跨场景物件随意混在同一张图。
- 要扩展不同的穿搭表达或需要精确地点、姿势、主道具和小物组合时，读取[场景库](references/scene-library.md)。

## 人类生活小物层

每张图必须让观众能看出“它正在做什么”。在主动作物之外，增加 **1–2 件有功能关系的小元素**：它们是人类会顺手使用的生活物，而不是散落的可爱装饰。优先放在宠物身前、扶手、茶几边或坐垫上，并让它们与动作形成小三角关系。

| 正在做的事 | 主动作物 | 可搭配的小元素 |
| --- | --- | --- |
| 躺着看电视 | 黑色遥控器 | 无品牌爆米花碗、杯垫、折角电视节目单（无可读文字） |
| 宅家吃零食 | 小盘披萨/薯片碗/三明治 | 无品牌苏打水杯、纸巾、打开的零食袋（无 Logo） |
| 打游戏 | 掌机或游戏手柄 | 有线耳机、零食碗、空白游戏卡盒 |
| 听音乐 | 小耳机或耳罩 | 无文字唱片封套、便携播放器、空白磁带盒 |
| 周末喝饮料 | 透明杯或素色汽水罐 | 杯垫、柠檬片、小零食碟 |
| 摸鱼办公 | 旧鼠标或手机 | 无文字便签、纸杯咖啡、充电线 |

- 小物总数严格限制为 1–2 件；它们应占画面约 3–12%，不能形成静物铺陈、不能盖住脸、身体姿势、爪子或主道具。
- 道具不是必须真的被精细抓握：主动作物可由一只前爪压住或靠在身体上；辅助小物可以自然放在近处。保持“正在使用”的因果关系比逼真的人手抓握更重要。
- 所有食物、杯子、设备与包装均为无品牌、无文字、无 Logo 的泛用物。不要出现药物、烟、酒标、货币、广告、UI 文字或随机标签。

## 美式街头穿搭

- 默认选择一件主衣物加 1–2 个小配件。适合的主衣物包括：宽松连帽卫衣、复古 varsity 夹克、褪色牛仔外套、格纹 overshirt、工装马甲、橄榄球球衣、复古印花 T 恤或短款 bomber。
- 可选配件包括：窄框黑墨镜、针织帽、倒戴棒球帽、小项链、方巾或小斜挎包。配件服从脸部识别，不能遮住眼睛以外的关键面部特征；默认只使用一副墨镜或一顶帽子，不做全身珠宝叠戴。
- 用洗旧黑、藏蓝、褪色红、森林绿、牛仔蓝、卡其、米白和少量橙红构成街头色彩；与宠物的毛色形成清晰对比，不让衣服吞没脸和身体轮廓。
- 服装要像真实宠物定制衣物：有布料厚度、领口、袖口和自然褶皱；禁止把人类裤装、鞋子或完整人类四肢强行套到动物身体上。
- 如用户明确给出服装，保留其品类、颜色与情绪，只将其调整为适合宠物的穿法。除非用户要求，不使用任何真实品牌名称、Logo、字母印花或联名元素。

## 头像构图与快照滤镜

- 宠物的脸和上半身优先可读。默认主体占画面约 55–75%，眼睛/鼻口位于中心附近；全身姿势只有在动作必须依赖身体时才使用，并保持脸部清楚。
- 使用具体的日常生活空间，优先从[场景库](references/scene-library.md)选择，保留一两处真实使用痕迹。不要变成摄影棚、白墙电商背景、豪车或奢侈品空间。
- 色调必须锁定为复古美式闪光片，但不锁死具体家具：以浓青蓝/蓝绿色大色块、暖红棕/琥珀背景或道具、奶油白闪光毛发和压暗蓝绿阴影建立色彩关系。不得退化为普通灰绿室内照、现代极简中性色或单纯加颗粒的清晰数码片。
- 模拟 1990s–2000s 消费级傻瓜相机/一次成像闪光片：近距离机顶直闪、明确硬阴影、毛发高光有轻微过曝、背景比主体暗一档、有限动态范围、轻微红黄偏色、饱和青蓝、可见彩色颗粒和轻微镜头软化。禁止柔光、电影级调色、干净通透的现代数码肤质与高级棚拍。
- 画面应像朋友随手抓到的宠物瞬间：略近的镜头、微小的取景偏移、真实的家具比例。不要用电影级布光、浅景深人像虚化、塑料磨皮、干净商业电商背景或 AI 感强的潮流大片。

## 宠物结构保护

- 保持原有物种的自然头身关系、腿/爪数量、尾巴、耳朵和毛发走向；四足宠物默认保持四肢，除非原图中部分肢体被遮挡。
- 宠物的**姿势可以像人**：半躺、背靠、叉开/前伸后腿、肚子朝上、前爪搭扶手、单爪把道具压在身体旁。重点是保留动物的头、躯干、四肢和爪子，却让整体剪影第一眼读成“人类瘫在沙发上”。不直立成真人，也不给人类手指、手臂、臀部或双足人类步态。
- 乐器、遥控器、杯子等可被前爪以清楚但简化的方式握在或压在身前；道具应遮住最不稳定的接触点。不能出现复杂弹奏、精确端酒、手指抓握或人体关节。
- 不改换物种、不更换毛色、不幼体化、不把真实照片变成卡通、玩偶或 3D 角色。多只宠物照片中，默认只改造用户指定的主宠；未指定时保留原有宠物数量与关系。

## 默认编辑提示词

生成前把方括号替换为从用户图片和需求中实际读出的内容。按下列顺序写，先锁定身份和构图，再写行为与服饰，最后写快照滤镜：

```text
Use the user's pet photo as the edit target. Create a 1:1 square pet fashion mood avatar of the same [species] pet. Preserve its exact [fur colors/markings], [face and eye features], [ears/tail], [body build], and [current expression or pose]; it must remain immediately recognizable as the user's own pet.

Mood and action: [emotion]. Give the pet the recognizable body language of a lounging human: [back propped against cushion / hind legs extended toward camera / belly-up half recline / paw draped over armrest], while using its own animal body, four paws and tail. [One front paw] [holds or presses] [one appropriately scaled prop] against its body. The full silhouette must read as a funny human-like pose, not as an ordinary pet sitting upright.

Activity details: clearly show that it is [watching TV / snacking / gaming / listening to music / drinking / pretending to work]. Add [one main action prop] and [one or two small, unbranded human-use objects] nearby, each naturally placed on the armrest, cushion or a small side table. The small objects support the action without hiding the pet, its pose or its face.

Wardrobe: dress it in a real pet-sized [main American streetwear item] in [palette], with [one or two accessories]. The fabric follows the pet's real shoulders, chest, neck and paws naturally; keep the face and its identifying markings clear. Set it in [one specific place from the scene library] with [one scene-defining environmental detail].

Photo language: fixed American retro flash snapshot palette: use a large saturated deep teal-blue/blue-green color block plus warm red-brown/amber surroundings or props, creamy flash-lit white fur, and deep blue-green shadows. Close consumer point-and-shoot on-camera flash, one hard small shadow, slightly blown fur highlights, underexposed background, limited dynamic range, fine color grain, faint lens softness and imperfect framing. The result feels funny, intimate and slightly trashy in a real lived-in American setting, not like a polished fashion campaign or a clean contemporary digital photo.

Keep the pet's natural anatomy, original number of limbs, paws and tail. No human body, human hands or fingers, extra limbs, impossible paw grip, costume that hides the face, cartoon/3D look, glamour studio lighting, readable text, logos, watermarks or brands.
```

## 交付前检查

- 是否为从构图开始设计的 1:1 正方形，而非裁切后的残图？
- 第一眼能否确认是同一只宠物：物种、脸、毛色斑纹、耳朵和神态均可辨认？
- 穿搭是否是合身、可想象真实存在的宠物街头服，而不是人类身体或廉价角色扮演？
- 情绪、动作、道具与场景是否讲述同一件事，且只有一个明确主行为？整体姿态是否真的先读成“人类瘫坐/半躺”，而不是“狗端正坐着”？
- 是否有 1 件主动作物和 1–2 件真实的人类生活小物，能立刻说明“它正在做什么”，又没有抢走主体或变成凌乱静物？
- 宠物是否保留自然肢体数量与犬类爪子，没有多肢、手指、直立人形或人体关节？
- 是否真的出现了锁定色调：浓青蓝/蓝绿色大色块、暖红棕/琥珀色环境、奶油白闪光毛发、压暗蓝绿阴影和硬闪？若只是普通冷绿室内照加颗粒，判定失败。
- 是否完全没有可读文字、Logo、水印、品牌或参考图中不应复刻的元素？

任一答案为否，应优先强化相应提示词约束后重新生成；不要用裁切、磨皮或堆更多配件补救。
