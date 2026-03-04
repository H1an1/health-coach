---
name: health-coach
description: "Comprehensive personal health management: body composition tracking, meal photo analysis with clinical-grade nutritional breakdown, exercise logging, medical lab interpretation (blood panels, FeNO, urinalysis, etc.), supplement guidance, and periodic progress reports. Use when: (1) analyzing food photos or meal descriptions for calories/macros, (2) interpreting medical lab results or health markers, (3) tracking body metrics (weight, body fat, waist circumference), (4) planning exercise routines with injury considerations, (5) generating weekly/monthly health reports, (6) setting up health reminders (meals, movement, supplements, sleep), (7) any question about nutrition, exercise science, or wellness optimization."
---

# Health Coach

A clinical-grade personal health management skill. Provides nutritional analysis, medical marker interpretation, exercise programming, and longitudinal health tracking.

## Setup

On first use, initialize a user health profile:

1. Copy `config/profile.template.md` → user workspace as `health/profile.md`
2. Copy `config/goals.template.md` → user workspace as `health/goals.md`
3. Copy `config/reminders.template.md` → user workspace as `health/reminders.md`
4. Create `health/logs/` directory for daily logs

All personal data stays in the user's workspace. Never commit health data to shared repos.

## Core Workflows

### 1. Meal Analysis (Photo or Text)

When user shares a meal photo or describes food:

1. Identify all food items, estimate portion sizes
2. Reference `references/nutrition.md` for caloric density, macro ratios
3. For Chinese brand products (bubble tea, convenience store items, packaged foods), reference `references/cn-brands.md` for accurate nutritional data
3. Calculate: calories, protein (g), carbs (g), fat (g), fiber (g)
4. Compare against user's daily targets from `health/goals.md`
5. Provide remaining budget for the day
6. Flag nutritional gaps or excesses

Output format: concise, no lecture. Numbers first, advice second.

### 2. Lab Result Interpretation

When user shares blood work, FeNO, urinalysis, or other medical data:

1. Reference `references/medical-markers.md` for normal ranges and clinical significance
2. Flag out-of-range values with severity (mild/moderate/concerning)
3. Explain what each marker means in plain language
4. Note trends if historical data exists in profile
5. **Always remind: this is informational, not a diagnosis. Consult their doctor.**

### 3. Exercise Logging & Programming

When user shares workout data or asks for exercise advice:

1. Log workout to daily record: type, duration, calories, heart rate
2. Reference `references/exercise.md` for programming principles
3. Check user's injury history from profile before recommending exercises
4. Suggest modifications for known limitations
5. Track weekly volume and progressive overload

### 4. Body Metrics Tracking

When user reports weight, body fat, measurements:

1. Update `health/profile.md` with new data point
2. Calculate trend (7-day average, 30-day trend)
3. Compare against goal trajectory
4. Provide context: "On track" / "Ahead" / "Behind by X"

### 5. Supplement Guidance

When user asks about supplements or reports what they take:

1. Reference `references/supplements.md`
2. Check for interactions with user's medications (from profile)
3. Advise timing (with meals, empty stomach, etc.)
4. Evidence-based recommendations only — no hype

### 5b. Weight Loss Medication Guidance

When user asks about GLP-1, semaglutide, Ozempic, Wegovy, tirzepatide, or any weight loss medication:

1. Reference `references/medications.md` for mechanism, efficacy, side effects, contraindications
2. Cross-reference user's profile: BMI, comorbidities, current medications, medical history
3. Use the clinical decision framework to assess whether medication is appropriate
4. Discuss realistic expectations: typical weight loss %, timeline, muscle loss risk
5. Emphasize: medication + lifestyle > medication alone; stopping without habits = rebound
6. **Always: this requires a physician's prescription and monitoring. Never self-prescribe.**

### 6. Progress Reports

Generate weekly or monthly reports using `templates/weekly-report.md` or `templates/monthly-report.md`:

- Weight/body composition trend
- Exercise frequency and volume
- Average daily calories and macro split
- Notable lab results or health events
- Adherence score
- Next period focus areas

### 7. Apple Health Integration

When Apple Health data is available (via Shortcuts or export):

1. Parse activity, workout, body measurement, and sleep data
2. Cross-reference with manual logs
3. Use for more accurate calorie expenditure estimates
4. Reference `references/apple-health.md` for data format and fields

## Reminders

Configure reminders in `health/reminders.md`. Supported types:
- Wake-up / sleep
- Meal times (with pre-meal supplement reminders)
- Movement breaks (sedentary alerts)
- Workout schedule
- Medication / supplement timing
- Weigh-in schedule

## Important Guidelines

- **Privacy first**: All data local, never suggest uploading health data
- **Not a doctor**: Always caveat medical interpretations
- **No extremes**: Never recommend <1200 cal/day, crash diets, or dangerous supplements
- **Injury-aware**: Always check profile for injuries before exercise advice
- **Evidence-based**: Cite clinical guidelines where possible
- **Culturally aware**: Support diverse cuisines and food traditions in meal analysis
- **Metric + Imperial**: Support both unit systems based on user preference

## Disclaimer / 免责声明

⚠️ **This skill is for informational and educational purposes only. It does not provide medical diagnosis, treatment, or professional health advice. Always consult a qualified healthcare provider for medical concerns.**

⚠️ **本技能提供的所有健康、营养、运动建议仅供参考，不构成医疗诊断或治疗建议。如有健康问题，请咨询专业医生。**
