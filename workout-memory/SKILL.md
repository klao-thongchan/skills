---
name: workout-memory
description: Track gym workouts and conservative progression.
---

# Workout Memory

## Purpose

Track the user's gym exercises, machine/cardio/bodyweight settings, sets, reps, body parts, aliases, and conservative progression.

This skill is for practical gym workout memory: machines, cardio, Power Plate/vibration work, and bodyweight variations. It is not medical advice and not aggressive personal training.

## Source of Truth

Use these files:

- ~/Health/Workout/workout_log.jsonl
- ~/Health/Workout/exercise_profiles.yaml
- ~/Health/Workout/machine_aliases.yaml
- ~/Health/Workout/weekly_reviews.md

Do not rely only on Hermes persistent memory for numeric workout records.

Hermes memory should only remember:
- the workout system exists
- the source-of-truth folder is ~/Health/Workout
- the user prefers machine-based conservative progression

## Input Triggers

Treat these prefixes as workout logging commands:

- workout-memory log:
- gym log:
- gym:

## Input Examples

The user may write messy natural language:

- gym log: sumo squat 7.5kg, 3 set, 15 times, RPE 10
- chess press 28kg 3 set, 15 times for each set
- chest press 28kg 3x15
- chest press 28kg 15 15 15
- อก 28kg 3 เซ็ต เซ็ตละ 15
- lat pull down 35kg 12 12 10
- leg press 80kg 3x12 rpe 8

## Normalization Rules

Always normalize exercise names.

If the user writes a typo or variant, preserve it as an alias.

Examples:

- chess press → Chest Press
- chestpress → Chest Press
- lat pull down → Lat Pulldown
- pull down → Lat Pulldown
- legpress → Leg Press
- dumbell → dumbbell, while preserving the user's typo as an alias
- flys → fly, while preserving the user's variant as an alias

For free-weight movements, normalize to the common equipment + movement name when obvious:

- arnold's dumbell shoulder press → Arnold's Dumbbell Shoulder Press
- arnold's dumbell bicep curls → Arnold's Dumbbell Biceps Curl
- dumbell rear delt flys → Dumbbell Rear Delt Fly
- kettlebell sumo squat → Kettlebell Sumo Squat

Use machine_aliases.yaml first. If no alias exists, infer carefully and mark uncertainty.

## Unit Rules

Use metric units only for workout guidance and progress tracking.

- Record and report weight in kilograms (`weight_kg`).
- Do not convert kg to lb unless the user explicitly asks for imperial conversion.
- Keep training prescriptions, progression, and 1RM estimates in kg.

## Logging Rules

When the user logs a workout, parse and save:

- date
- exercise
- raw_input
- aliases
- body_parts
- weight_kg
- weight_lb
- sets
- reps
- rpe
- pain
- notes
- cardio-specific fields when present, such as incline, pace, duration, distance, and average_heart_rate_bpm

For unilateral free-weight movements where the user gives side-specific effort, store RPE as a mapping instead of flattening it:

```yaml
rpe:
  left_arm: 7
  right_arm: 4
```

Also preserve the asymmetry in `notes` and progression. If one side is clearly harder, conservative progression should usually repeat the same load until both sides are controlled and the harder side is no more than RPE 7–8 with no pain. Do not suggest increasing weight when the harder side is already RPE 8+.

If the user says "3 set, 15 times for each set", store:

sets: 3
reps: [15, 15, 15]

If the user says "3x15", store:

sets: 3
reps: [15, 15, 15]

If the user says "12 12 10", store:

sets: 3
reps: [12, 12, 10]

Append every workout to workout_log.jsonl.

Update exercise_profiles.yaml with the latest known state for that exercise.

Never delete or overwrite historical log entries unless the user explicitly asks for correction.

## workout_log.jsonl Example

{"date":"2026-07-08","exercise":"Chest Press","raw_input":"chess press 28kg 3 set, 15 times for each set","aliases":["chess press"],"body_parts":["chest","triceps","front delts"],"weight_kg":28,"weight_lb":61.7,"sets":3,"reps":[15,15,15],"rpe":null,"pain":null,"notes":null}

## exercise_profiles.yaml Example

Chest Press:
  latest:
    date: 2026-07-08
    weight_kg: 28
    weight_lb: 61.7
    sets: 3
    reps: [15, 15, 15]
    rpe: null
    pain: null
  aliases:
    - chess press
  body_parts:
    - chest
    - triceps
    - front delts
  progression:
    conservative_next: "Repeat 28 kg for 3x15."
    possible_next: "Try the smallest next machine increment only if form was clean twice."

## Recall Rules

When the user asks a short query like:

- chess press?
- chest press?
- leg press?
- chest today?
- back today?
- next chest press

Search in this order:

1. exact exercise name
2. aliases
3. typo variants
4. body part mapping

Return the latest record from exercise_profiles.yaml.

If the profile is missing or uncertain, search workout_log.jsonl.

## Progression Rules

Be conservative.

If the user completed the same weight and target reps twice with no pain and RPE <= 8, suggest increasing by the smallest available machine increment.

If RPE is missing, recommend repeating the same weight before increasing.

If reps decreased compared with the previous session, suggest staying at the same weight.

If the user reports pain, sharp discomfort, numbness, dizziness, or injury, stop progression advice and recommend stopping that movement and consulting a qualified professional.

Do not diagnose injuries.

Do not suggest aggressive weight jumps.

Do not invent records.

## Logging Reply Format

Saved.

Exercise:
- Name:
- Weight:
- Sets/Reps:
- Body parts:

Next:
- Conservative:
- Progression:

Missing useful data:
- RPE
- Form quality
- Pain/discomfort

## Recall Reply Format

Found.

Latest:
- Exercise:
- Weight:
- Sets/Reps:
- Date:
- Body parts:

Next:
- Conservative:
- Progression:

Missing data:
