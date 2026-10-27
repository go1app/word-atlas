# 日常例句动画素材

首个素材：`abandon.svg`，10 秒自动循环，基于项目日常例句：

> We had to abandon our car in the snow.

场景：汽车驶入雪地后停下；旅人下车步行离开，留下脚印；积雪覆盖车顶和车轮。动画无可见单词、释义、字幕、猜词提示或答案按钮。SVG 无脚本、无远程依赖，可直接用 `<img>` 引用。

- `index.json` 通过 `wordId` 关联现有词库；`exampleIndex: 0` 对应日常例句。
- `src` 为相对应用根路径；接入时需结合 Vite 的 `import.meta.env.BASE_URL`，支持子路径部署。
- 后续闪卡入口及答案弹框应从原词库取内容，不从动画解析答案。
- 缩略入口与全屏播放器共用本素材。应用负责暂停、重播及减少动态效果偏好；若需控制时间轴，用同源 `<object>` 载入后调用 SVG 的 `pauseAnimations()` / `setCurrentTime()`，不要直接插入不受信任 SVG。
- 此提交仅增加素材，尚未接入闪卡页面或修改例句界面。

例句来源：[Word Atlas README](https://github.com/go1app/word-atlas/blob/main/README.md)。
署名：Word Atlas contributors — [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)。
修改说明：依据日常例句新绘制矢量场景并添加动画，未嵌入原插画或录音。本目录新素材亦按 CC BY 4.0 提供，在可授予的权利范围内。

## 第二批：五个日常例句场景

打开 `preview.html` 集中预览；每张支持重播、暂停、点击揭晓答案和大屏播放。预览页独立于原应用，尚未新增应用入口。

- `migrate.svg`：These birds migrate south when the weather turns cold.
- `volcano.svg`：We watched steam rising from the volcano across the lake.
- `lighthouse.svg`：The lighthouse beam swept across the dark sea.
- `telescope.svg`：We watched the moon through a telescope on the balcony.
- `festival.svg`：Our town holds a lantern festival every autumn.
