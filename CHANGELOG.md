# Changelog

## v1.0.0 (2026-03-03)

### 🚀 Initial Release

**health-coach** — 一个临床级的 AI 健康管理技能，从零到开源。

#### 知识库 (references/)

- **nutrition.md** — Mifflin-St Jeor BMR 公式、TDEE 计算、宏量素目标（按体重分级）、中国菜热量数据库（50+ 常见菜品）、照片估算法、微量营养素缺乏表、GI 值参考
- **medical-markers.md** — 血常规（CBC）、生化全套（代谢面板）、血脂四项、甲状腺功能、炎症标志物、FeNO + 鼻部 NO（气道/鼻腔炎症）、性激素、维生素/矿物质、尿常规，每项含正常范围 + 临床意义
- **exercise.md** — 渐进超负荷原则、SAID 原则、恢复指南、脂肪流失运动层级、心率区间（5区）、游泳各泳姿卡路里消耗、伤病处理（肩/膝/腰）、康复动作库、初级/中级训练模板
- **supplements.md** — 三级证据分类：Tier 1（维D/鱼油/肌酸/蛋白粉/镁/纤维）、Tier 2（咖啡因/褪黑素/锌/铁/B12/益生菌/胶原蛋白）、Tier 3（BCAA/谷氨酰胺/CLA/脂肪燃烧器——别买）、药物交互表、特殊人群建议（减脂期/关节/睡眠/呼吸系统）
- **medications.md** — GLP-1 全家族（司美格鲁肽/利拉鲁肽/替尔泊肽）临床数据、STEP/SURMOUNT 试验结果、剂量递增方案、副作用发生率、禁忌症、停药反弹数据；其他减重药（奥利司他/纳曲酮安非他酮/芬特明托吡酯）；在研新药（retatrutide/survodutide/orforglipron）；中国市场可获得性 + 价格；临床决策框架 + 3 个案例分析
- **apple-health.md** — HealthKit 数据类型映射、Shortcuts 导出方案、步数/静息心率/HRV/睡眠解读标准

#### 配置模板 (config/)

- **profile.template.md** — 用户健康档案模板（基本信息、体测数据、病史、用药、保健品、体检历史、运动背景、生活方式）
- **goals.template.md** — 目标配置（热量/宏量素/运动频率/行为目标/里程碑）
- **reminders.template.md** — 提醒时间表配置

#### 报告模板 (templates/)

- **daily-log.md** — 每日记录模板（体重、三餐明细、运动、补剂、睡眠、评分）
- **weekly-report.md** — 周报模板（体重趋势、营养汇总、运动汇总、睡眠、补剂依从性、本周亮点/改进/下周计划）
- **monthly-report.md** — 月报模板（4周趋势、月度均值、医疗更新、计划调整、长期进度）

#### 脚本 (scripts/)

- **init.sh** — 一键初始化：创建 `health/` 目录结构，交互式填写身高体重年龄，自动计算 BMR/TDEE/目标热量/蛋白质目标，生成个人档案
- **report.sh** — 周报/月报生成：自动汇总 `health/logs/` 中的每日记录，填入报告模板，支持 `--weekly` / `--monthly` / `--date` 参数
- **apple_health.py** — Apple Health XML 解析器：支持 2GB+ 大文件、自动清洗非法 XML 字符、提取体重/运动/步数/心率/HRV/睡眠数据、输出 Markdown + JSON、支持 `--days` 过滤

#### 其他

- **SKILL.md** — 技能入口，定义 7 大核心工作流 + 安全准则
- **README.md** — 双语文档（中文优先 + English）
- **LICENSE** — MIT
- **.gitignore** — 排除用户健康数据

---

*从需求到开源，一个晚上。*
