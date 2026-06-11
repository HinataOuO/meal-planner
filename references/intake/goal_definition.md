# Goal Definition

Classify goal:
- dimagrimento
- ricomposizione
- massa
- performance
- mantenimento

Capture:
- target weight or visual/performance target
- deadline, if any
- priority order: fat loss, muscle gain, performance, adherence
- acceptable pace

Output:
```json
{
  "goal_type": "fat_loss|recomposition|muscle_gain|performance|maintenance",
  "target_weight": null,
  "timeframe_weeks": null,
  "priority": []
}
```

If target is aggressive, flag risk and propose slower pace.
