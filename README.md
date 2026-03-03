# health-coach 💪

A comprehensive, open-source personal health management skill for AI agents.

Clinical-grade nutritional analysis, medical marker interpretation, exercise programming, and longitudinal health tracking — all running locally with zero data leakage.

## Features

- 🍽️ **Meal Analysis** — Photo or text → calories, macros, nutritional assessment
- 🏥 **Lab Interpretation** — Blood panels, FeNO, thyroid, lipids, urinalysis
- 💪 **Exercise Programming** — Injury-aware training plans, heart rate zones
- 📊 **Body Tracking** — Weight, body fat, waist trends over time
- 💊 **Supplement Guidance** — Evidence-based, interaction-aware
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
| `apple-health.md` | HealthKit data types, interpretation guidelines |

## Privacy

All health data stays 100% local in your workspace. Nothing is uploaded, shared, or transmitted. The skill operates entirely through local files and your AI agent's context.

## Structure

```
health-coach/
├── SKILL.md                    # Skill entry point
├── config/                     # User config templates
│   ├── profile.template.md
│   ├── goals.template.md
│   └── reminders.template.md
├── references/                 # Clinical knowledge base
│   ├── nutrition.md
│   ├── medical-markers.md
│   ├── exercise.md
│   ├── supplements.md
│   └── apple-health.md
├── templates/                  # Report templates
│   ├── daily-log.md
│   ├── weekly-report.md
│   └── monthly-report.md
└── scripts/
    ├── init.sh                 # First-time setup
    ├── report.sh               # Generate reports
    └── apple_health.py         # Apple Health XML parser
```

## Contributing

PRs welcome! Areas that need help:

- More cuisine databases (Japanese, Korean, Indian, etc.)
- Garmin/Fitbit data import
- Workout plan generators
- Localization (currently Chinese + English)

## License

MIT

---

# health-coach 💪 中文说明

一个开源的 AI 健康管理技能，让你的 AI agent 变成专业的私人健康教练。

临床级营养分析、医学指标解读、运动编程、身体数据追踪——所有数据 100% 本地存储，零上传。

## 功能

- 🍽️ **饮食分析** — 拍照或文字描述 → 热量、宏量素、营养评估（内置中国菜热量数据库）
- 🏥 **医学指标解读** — 血常规、生化全套、血脂、甲功、FeNO、激素、尿检
- 💪 **运动指导** — 伤病感知的训练计划、心率区间分析、动作库
- 📊 **体重追踪** — 体重/体脂/腰围趋势，7天均值，进度预测
- 💊 **补剂建议** — 三级证据分类、药物交互提醒
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
| `apple-health.md` | HealthKit 数据类型、解读标准 |

## 隐私

所有健康数据 100% 存储在本地工作目录，不上传、不分享、不传输。技能完全通过本地文件和 AI agent 上下文运行。

## 贡献

欢迎 PR！特别需要：

- 更多菜系热量数据（日料、韩餐、印度菜等）
- Garmin/Fitbit 数据导入
- 训练计划生成器
- 更多语言支持

## 许可

MIT
