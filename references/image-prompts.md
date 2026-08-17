# 火柴人知识卡片 · 插图生成提示词（已验证可用）

> 经验：文生图模型对**中文会乱码**，所以卡片里的所有**文字/标题/标签一律用 SVG/HTML 矢量渲染**。
> 但**纯图形、无中文的插图**（大脑、图标、场景简图）模型画得比手绘 SVG 好 —— 这部分用 ImageGen 生成。
> 关键约束：**每次只画一个居中图标**，否则图生图模式会复制整张卡片。用「纯文生图（不传参考图）」+ 强制 "Draw ONLY ONE thing: ... NO other objects"。

## 通用画风指令（每条提示词开头固定加上）
```
black ink line art on pure white background, clean minimalist doodle / stick-figure illustration style like a xiaohongshu (小红书) knowledge card. NO text, NO border, NO background pattern, NO other objects, NO fill, NO color, NO watermark. Centered in the image.
```

## 1. 大脑 + 齿轮（定义栏主插图，示范图同款）
用「图生图」(input_fidelity=high)，参考图 = 用户给的示范卡片，提示词：
```
A clean hand-drawn line art illustration of a human brain in side view (left profile). Classic walnut/bean-shaped outline (rounded frontal lobe at left, tapering to occipital lobe at right). Surface covered with winding serpentine gyri/sulci lines like topographic contours. Below the brain a separate smaller cerebellum section with 3-4 horizontal striation lines. At bottom right two interlocking gear wheels of different sizes with teeth. A small brainstem extends downward. Clean black lines only, minimalist editorial doodle style.
```
尺寸 1024×1024，quality=high，style=line art。

## 2. 大火柴人 / 小火柴人（特点栏 / 定义栏）
**建议直接用模板里内联的 SVG 简笔（勿用图模型）**，风格最统一、零成本。
若要换画风才用图模型，纯文生图提示词：
```
Draw ONLY ONE thing: a simple hand-drawn stick figure person, black ink line art on pure white background. Round head (outline circle), a few hair lines on top, thin straight-line body, one arm raised waving, legs apart standing. Centered, no other objects.
```

## 3. 特点三图标（自主性 / 反应性 / 社会性）
纯文生图，每条单独生成（512×512）：
- 自主性：
  `Draw ONLY ONE thing: a tiny stick figure or robot standing independently inside a thin black circle outline, arms at sides, representing autonomy. Centered, no other elements.`
- 反应性：
  `Draw ONLY ONE thing: a bold zigzag lightning bolt symbol representing reactivity/response. Black ink line art, centered, no other objects.`
- 社会性：
  `Draw ONLY ONE thing: two small stick figures facing each other with a speech bubble between them, representing social interaction. Centered, no text in bubble, no other elements.`

## 4. 应用场景四图标（按主题替换）
纯文生图，每条单独生成（512×512），把 subject 换成对应主题：
- 通用模板：
  `Draw ONLY ONE thing: a <SUBJECT> icon, black ink line art on pure white background, clean simple doodle. Centered, no text, no border, no other objects.`
- 示例 subjects：small car in side view（智能家居车）/ ticket vending machine kiosk（自助购票）/ robot with antenna and buttons（自动驾驶机器人）/ customer-service bot wearing headset with microphone（客服机器）。
- **若主题与「智能体」无关**，请为当前名称重新想 3~4 个真实应用场景，各生成一张图标。

## 成本与取舍建议
- **必须生成**：定义栏主插图（1 张）、应用场景图标（按主题 3~4 张）。
- **可复用（不重复生成）**：大火柴人、小火柴人用内联 SVG；若新主题的特征仍是「自主性/反应性/社会性」这类通用特质，特点三图标可直接复用已生成的图。
- 平均每卡约 4~5 张图，消耗约 20~35 积分。
