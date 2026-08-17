# 原始扣子工作流来源（coze-workflow-clipboard-data）

来源文件：`C:/Users/lenovo/Desktop/火柴人风格知识卡片.txt`
workflowId: 7580192830757355539 ｜ host: www.coze.cn

## 节点（4 个，线性）
1. 开始 (type=1, id=100001)：outputs/trigger_parameters = `input` (string)
2. 图片提示词 (type=3, id=187175, 大模型节点)
   - model: 豆包·1.5·Pro·32k ｜ temperature 0.8 ｜ maxTokens 4096 ｜ responseFormat 2
   - systemPrompt（知识卡片设计师角色，核心指令）：
     > 你是一位专业的知识卡片设计师，擅长生成示小黑人风格的知识卡片。你要依据用户输入的主题{{input}}，自动生成小黑人，矢量图，图标风格，图片能清晰地表达{{input}}的意思，简约白色背景。
     > 提示词布局严格按着下面的提示词示例生成。
     > 提示词示例：用户输入「未解的物理学难题」……（详见 SKILL.md few-shot）
   - prompt（用户输入）：`{{input}}`
3. 图像生成 (type=16, id=183808)
   - prompt = `{{output}}`（上一步 LLM 输出）
   - modelSetting: custom_ratio 1440×2560（ratio_type=fixed）、ddim_steps 25、guidance_scale 2.5、max_images 1、watermark true
   - references: 什么是智能体.jpg（url=byteimg.com，weight 0.7，expires 1796006043）
4. 结束 (type=2, id=900001)
   - output = 183808.data（图）
   - output1 = 187175.output（提示词）

## 说明
- 本环境无 Coze 专属图像模型与参考图，风格已用文字提示词等效还原。
