# Word Atlas 全词库动画制作

## 授权与目标
用户明确要求完成 go1app/word-atlas 全词库的精美 SVG 动画，并上传该仓库；额度不足时每5小时尝试续做，直到全量完成。此范围不包含改应用功能、付费模型 API、购买额度、修改系统电源设置或下载全套现有图片/音频。
自动化 ID：svg；本聊天已有 active goal。

## 唯一进度来源
本地 progress.json 与仓库 public/atlas/animations/production-progress.json 对照，仓库实际文件和提交为准。每批开始先读取远端 index.json 与最新 main，避免覆盖或重复。7298 为当前索引 count；不要只画高频、容易或列表中的前几个就宣告完成。难词标待重做并写原因，最终仍需完成。
本地 atlas-index 位于 ../atlas-index.json；词条按 words 的索引每100条对应 public/atlas/entries/{floor(index/100)}.json，取条目 ex[0]（第一条日常例句），不可凭空写例句、不可用雅思例句替代。取最少文字数据，每个分片仅缓存一份。

## 文件与风格
- public/atlas/animations/{wordId}.svg：纯 SVG，无 script、外链图像、可见答案、猜词提示或字幕。可直接 img 嵌入，约10秒循环。
- index.json 保留原项目其他记录，添加 wordId、src（相对应用根）、durationSeconds、exampleIndex:0、dailyExample、posterTimeSeconds、attribution、license。
- 每个词先写自己的分镜：例句对象、主体动作、地点、三层构图、专属配色、细节、循环接缝。画面只在恰当时复用基础图元，不可将一个场景改颜色、换名字批量冒充独立创作。
- 手绘插画感：细致轮廓、材质纹理、自然形状、层次光影；避免廉价图标拼贴、几何小人占据全部画面、文字解释取代画面。
- 具体名词表现典型对象，动词显示清楚动作前后关系，抽象词将原例句中的具体关系画出来。星期、语法词等难题也需真实设计，不能随意贴无关图。
- 保留例句来源与 CC BY 4.0 署名、修改说明，不直接重用不明来源美术。

## 检查与完成定义
1. 实际 ex[0] 与动画内容相符，画面主要动作能支持词义猜测。
2. XML 可解析，所有引用存在，动画 values/keyTimes 数量和范围正确，所有动作循环接缝自然，主要时间轴约10秒。
3. 渲染并查看关键时刻，检查遮挡、比例、出框、层次、空白和颜色对比。离线抽样只是画面检查，不得冒称已真实浏览器完整播放验证。
4. 只有本地文件生成不算上传完成。用 GitHub 回执与远端 blob SHA 确认每个文件。
5. 不合格回修；无法核验写 needs_revision。uploaded 状态不代表“用户已批准每张”。主观“非常精美”必须逐张保持并诚实说明，不能承诺绝对质量。
6. 每批保留画面审查记录，不无限堆积大型预览/重复缓存。只留必要小型SVG与文字。

## 现成素材和工具
首批6词：abandon、migrate、volcano、lighthouse、telescope、festival。已有静态画面审查，但集成时仍要浏览器检查。
现有绘制逻辑在 work/make_asset.py、work/make_five.py；抽样渲染 work/sample_svg.py。导入 make_five.py 会重写旧文件，应先提取所需函数而不要将其当库直接导入。
离线 PNG 渲染可用 Node sharp：
/Users/jiale/.cache/codex-runtimes/codex-primary-runtime/dependencies/node/bin/node
包 /Users/jiale/.cache/codex-runtimes/codex-primary-runtime/dependencies/node/node_modules/sharp
用 view_image 检查渲染图。不得借测试绕过浏览器访问限制。
GitHub MCP 可读但写入曾403；本机 gh 已登录 go1app 且成功写入，必要时用 exec require_escalated 联网，不输出 token。不要重新完整 git clone。
现有 work/upload_five.py 可参考原子创建 blobs/tree/commit 再非force更新 main 的流程；从最新main起，遇冲突重新读取并合并，不强推。

## 续做节奏
从 progress.json 恢复未完成词，下一批优先 library/bedroom/clothes/strong/paint（均在 entries-0.json），随后覆盖全部其余词。不因批次完成就停止总目标。额度不足保存断点，heartbeat每5小时尝试恢复；不能自行重置或绕过账户限制。只有新的有效批次、全部完成、失败或需用户行动才通知；状态不变安静。全部7298均有实际检查与上传证据才标总目标complete并停用svg自动化。

## 最新美术优先要求（覆盖批次数量偏好）
用户明确强调：不要求快，要求出图唯美、动画精美。没有每轮最低产量。先把一张精修到更高基准，再扩展；已有11张保留上传记录，但不能因此自动判定通过新标准。
- 当前 batch-004 五张只是草稿，尚未上传；其人形和平涂还过于简化。先精修 born，柔和有方向的晨光、织物/木材细节、自然手臂姿态和人物比例、暖室与冷雪的空间对比。
- 禁止几何小人批量换衣、大片空洞平涂、无动机摆动。每词有自己的美术分镜与动作节奏。
- 分开记录 uploaded（远端文件存在）与 qualityApproved（按最新美术标准评审）；未达标保留 draft/needs_revision，不为数字好看上架。
- 至少检查起始、动作中段、关键接触/转折、收尾及循环接缝多个时刻；离线抽样与真正浏览器播放是不同证据，不得混称。
- 质量评审须写具体发现和修正，不可只填 passed。


## 最新统一画风（2026-10-28，覆盖冲突美术要求）
用户明确要求后续所有单词SVG使用早期 abandon 雪地汽车动画的画风：柔和低饱和扁平绘本、北欧童书与纸片剪贴画气质、简洁几何造型、少量纸张纹理与阴影、分层留白、舒缓动作。详见同目录 STYLE.md。不要继续以复杂写实人物、密集细节或电影光影为目标。保留原日常例句、隐藏答案、点击揭晓、重播暂停。批量目标与自动任务仍暂停，未获恢复指令。

## 最新恢复指令（2026-10-28）
用户明确说“现在开始啊”，恢复全词库制作与每5小时自动续做。按 STYLE.md 的早期 abandon 绘本画风执行；此前暂停说明为历史状态。
