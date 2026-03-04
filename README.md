# health-coach 💪

一个开源的 AI 健康管理技能，让你的 AI agent 变成专业的私人健康教练。

临床级营养分析、医学指标解读、运动编程、身体数据追踪——所有数据 100% 本地存储，零上传。

## 功能

- 🍽️ **饮食分析** — 拍照或文字描述 → 热量、宏量素、营养评估（内置中国菜热量数据库）
- 🏥 **医学指标解读** — 血常规、生化全套、血脂、甲功、FeNO、激素、尿检
- 💪 **运动指导** ��� 伤病感知的训练计划、心率区间分析、动作库
- 📊 **体重追踪** — 体重/体脂/腰围趋势，7天均值，进度预测
- 💊 **补剂建议** — 三级证据分类、药物交互提醒
- 💉 **减重药物指南** — GLP-1（司美格鲁肽/替尔泊肽）临床数据、副作用、中国市场可获得性、个性化用药建议
- 📱 **Apple Health 导入** — 一键解析 iPhone 健康数据（体重、运动、步数、心率、睡眠）
- 📈 **进度报告** — 每日记录、周报、月报自动生成

## 快速开始

### 安装

```bash
npx skills add H1an1/health-coach -g -y
```

### 初始化个人档案

```bash
cd 你的工作目录
bash ~/.agents/skills/health-coach/scripts/init.sh .
```

交互式填写身高体重年龄，自动计算 BMR/TDEE/目标热量，生成个人档案。

### 导入 Apple Health 数据

1. iPhone → 健康 → 头像 → 导出所有健康数据
2. 把 `export.zip` 传到电脑
3. 解压后运行：

```bash
python3 ~/.agents/skills/health-coach/scripts/apple_health.py export/apple_health_export/export.xml --output health/ --days 30
```

### 生成报告

```bash
bash ~/.agents/skills/health-coach/scripts/report.sh . --weekly   # 周报
bash ~/.agents/skills/health-coach/scripts/report.sh . --monthly  # 月报
```

## 知识库

`references/` 目录包含临床级参考资料：

| 文件 | 内容 |
|------|------|
| `nutrition.md` | BMR/TDEE 公式、宏量素标准、中国菜热量表、照片估算法 |
| `medical-markers.md` | 血常规、生化、血脂、甲功、FeNO、激素、维生素、尿检 |
| `exercise.md` | 训练原则、心率区间、伤病处理、动作库、训练模板 |
| `supplements.md` | 补剂三级分类（强证据/中等/忽悠）、交互作用 |
| `medications.md` | 减重药物：GLP-1 临床数据、副作用、中国市场价格、决策框架、案例分析 |
| `apple-health.md` | HealthKit 数据类型、解读标准 |

## 隐私

所有健康数据 100% 存储在本地工作目录，不上传、不分享、不传输。技能完全通过本地文件和 AI agent 上下文运行。

## 项目结构

```
health-coach/
├── SKILL.md                    # 技能入口
├── config/                     # 用户配置模板
│   ├── profile.template.md
│   ├── goals.template.md
│   └── reminders.template.md
├── references/                 # 临床知识库
│   ├── nutrition.md
│   ├── medical-markers.md
│   ├── exercise.md
│   ├── supplements.md
│   └── apple-health.md
├── templates/                  # 报告模板
│   ├── daily-log.md
│   ├── weekly-report.md
│   └── monthly-report.md
└── scripts/
    ├── init.sh                 # 初始化脚本
    ├── report.sh               # 报告生成
    └── apple_health.py         # Apple Health 数据解析
```

## 更新日志

### v0.2.0 — 2026-03-05

#### 🆕 新增
- **中国品牌食品热量数据库** (`references/cn-brands.md`) — 611行，覆盖中国市场常见食品
  - 🧋 奶茶：乐乐茶、喜茶、霸王茶姬、瑞幸、星巴克、奈雪、茶百道（含少糖/缓糖版本）
  - 🍶 酒类：盒马果酒、啤酒(8品牌)、威士忌、伏特加、白酒、红酒 + 减脂饮酒排名
  - 🍡 甜品/烘焙：糖葫芦、好利来、鲍师傅、泸溪河
  - 🏪 便利店：全家、7-Eleven、便利蜂
  - 🛒 超市：山姆会员店（烘焙/熟食/冷冻/零食）、Costco开市客、盒马
  - 🥡 快餐：麦当劳、肯德基、汉堡王、赛百味、必胜客、吉野家、真功夫
  - 🥘 中式菜品：家常菜27道、粥粉面9种、外卖套餐8类
  - 🍢 火锅：19种食材 + 5种蘸料热量对比
  - 🔥 烧烤：11种常见串
  - 🌅 早餐：煎饼果子、油条、包子等13种
  - 🍮 甜品饮品：8种甜品 + 碳酸饮料/果汁/功能饮料26种
  - 🍫 零食品牌：良品铺子、三只松鼠、百草味
  - 🥛 乳制品：牛奶5品牌、酸奶5品牌、蛋白粉4品牌
  - 🍜 方便食品：11种（螺蛳粉、自热锅、拉面说等）
- **免责声明** — 中英双语免责声明（SKILL.md + README.md）
- **模型兼容性说明** — 标注基于 Claude Opus 4.6 开发测试

#### 🔧 改进
- SKILL.md 饮食分析workflow增加 cn-brands.md 引用

### v0.1.0 — 2026-03-03
- 初始版本发布
- 完整知识库：nutrition、medical-markers、exercise、supplements、medications、apple-health
- 脚本：init.sh、report.sh、apple_health.py
- 支持中英双语

## 贡献

欢迎 PR！特别需要：

- 📦 **食品数据** — 更多品牌/菜系（日料、韩餐、印度菜、东南亚菜等）
- 🔗 **数据源集成** — FatSecret API、Open Food Facts 等开放数据库对接
- 🏋️ **训练计划生成器**
- 📱 **Garmin/Fitbit 数据导入**
- 🌍 **更多语言支持**

### 如何贡献食品数据

1. Fork 本仓库
2. 编辑 `references/cn-brands.md`，按现有格式添加数据
3. 数据来源请优先使用**产品包装营养标签**
4. 提交 PR，注明数据来源

## 许可

MIT

---

# English

A comprehensive, open-source personal health management skill for AI agents.

Clinical-grade nutritional analysis, medical marker interpretation, exercise programming, and longitudinal health tracking — all running locally with zero data leakage.

## Features

- 🍽️ **Meal Analysis** — Photo or text → calories, macros, nutritional assessment
- 🏥 **Lab Interpretation** — Blood panels, FeNO, thyroid, lipids, urinalysis
- 💪 **Exercise Programming** — Injury-aware training plans, heart rate zones
- 📊 **Body Tracking** — Weight, body fat, waist trends over time
- 💊 **Supplement Guidance** — Evidence-based, interaction-aware
- 💉 **Weight Loss Medications** — GLP-1 agonists (semaglutide, tirzepatide), clinical trial data, side effects, China market availability, personalized assessment
- 📱 **Apple Health Import** — Parse full XML export (weight, workouts, steps, HR, sleep)
- 📈 **Progress Reports** — Daily logs, weekly & monthly summaries

## Quick Start

### Install as a Skill

```bash
npx skills add H1an1/health-coach -g -y
```

### Initialize Your Profile

```bash
cd your-workspace
bash ~/.agents/skills/health-coach/scripts/init.sh .
```

This creates a `health/` directory with your personal profile, goals, and reminder config.

### Import Apple Health Data

1. iPhone → Health → Profile → Export All Health Data
2. Transfer `export.zip` to your computer
3. Unzip and run:

```bash
python3 ~/.agents/skills/health-coach/scripts/apple_health.py export/apple_health_export/export.xml --output health/ --days 30
```

### Generate Reports

```bash
bash ~/.agents/skills/health-coach/scripts/report.sh . --weekly
bash ~/.agents/skills/health-coach/scripts/report.sh . --monthly
```

## Knowledge Base

The `references/` directory contains clinical-grade knowledge:

| File | Contents |
|------|----------|
| `nutrition.md` | BMR/TDEE formulas, macro targets, Chinese food calorie database, portion estimation |
| `medical-markers.md` | CBC, metabolic panel, lipids, thyroid, FeNO, hormones, vitamins, urinalysis |
| `exercise.md` | Training principles, exercise database with injury notes, HR zones, programming templates |
| `supplements.md` | 3-tier evidence classification, interactions, special populations |
| `medications.md` | Weight loss drugs: GLP-1 clinical data, side effects, China pricing, decision framework, case studies |
| `apple-health.md` | HealthKit data types, interpretation guidelines |

## Privacy

All health data stays 100% local in your workspace. Nothing is uploaded, shared, or transmitted. The skill operates entirely through local files and your AI agent's context.

## Changelog

### v0.2.0 — 2026-03-05

#### 🆕 New
- **Chinese Brand Food Nutrition Database** (`references/cn-brands.md`) — 600+ entries covering the Chinese market
  - Bubble tea (LELECHA, HEYTEA, CHAGEE, Luckin, Starbucks, Nayuki, ChaPanda)
  - Alcohol (craft beers, whisky, vodka, baijiu, wine + fat-loss ranking)
  - Supermarkets (Sam's Club, Costco, FRESHIPPO/Hema)
  - Fast food (McDonald's, KFC, Burger King, Subway, Pizza Hut, Yoshinoya)
  - Chinese dishes (27 home-style, 9 noodle/congee, 8 takeout combos)
  - Hotpot ingredients (19 items + 5 dipping sauces with calorie comparison)
  - BBQ, breakfast, desserts, snack brands, beverages
  - Dairy, protein powders, convenience store items, instant foods
- **Disclaimer** — Bilingual (CN/EN) disclaimer in SKILL.md and README.md
- **Model Compatibility Notice** — Developed and tested on Claude Opus 4.6

#### 🔧 Improved
- SKILL.md meal analysis workflow now references cn-brands.md

### v0.1.0 — 2026-03-03
- Initial release

## Contributing

PRs welcome! Areas that need help:

- 📦 **Food data** — More brands/cuisines (Japanese, Korean, Indian, SEA, etc.)
- 🔗 **Data source integration** — FatSecret API, Open Food Facts
- 🏋️ **Workout plan generators**
- 📱 **Garmin/Fitbit data import**
- 🌍 **Localization**

### How to contribute food data

1. Fork this repo
2. Edit `references/cn-brands.md` following the existing format
3. Prefer **product packaging nutrition labels** as data source
4. Submit a PR with source noted

## Disclaimer / 免责声明

⚠️ **This skill is for informational and educational purposes only. It does not provide medical diagnosis, treatment, or professional health advice. Always consult a qualified healthcare provider for medical concerns.**

⚠️ **本技能提供的所有健康、营养、运动建议仅供参考，不构成医疗诊断或治疗建议。如有健康问题，请咨询专业医生。**

### Model Compatibility / 模型兼容性

This skill was developed and tested on **Claude Opus 4.6**. Different models may vary in accuracy — particularly for image-based tasks like meal photo analysis and lab result interpretation. If you're using a different model, please verify outputs and adjust prompts as needed for your setup.

本技能基于 **Claude Opus 4.6** 开发和测试。不同模型的分析能力可能存在差异，尤其是图像识别类功能（如食物照片分析、化验单解读）。使用其他模型时，请结合自身情况验证结果，必要时调整提示词。

## License

MIT
