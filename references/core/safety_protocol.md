# Safety Protocol

Screen safety before calories, macros, meal plans, or adaptations.

Hard-stop flags block prescriptive targets and require clinician review:
- `minor`: user under 18.
- `pregnant`, `breastfeeding`.
- `eating_disorder_current`, `eating_disorder_history_with_active_symptoms`.
- `bmi_under_18_5` or goal asks further fat loss at low weight.
- `medical_condition_diet_sensitive`: diabetes, kidney, liver, heart disease,
  hypertension requiring treatment, GI disease, endocrine disease, cancer, or
  post-surgery recovery.
- `medication_diet_sensitive`: insulin, GLP-1, diuretics, anticoagulants,
  steroids, thyroid medication, psychiatric medication affecting appetite/weight.
- `symptoms_red_flag`: fainting, chest pain, purging, rapid unexplained weight
  loss, amenorrhea, severe fatigue, or dehydration.

Soft-stop flags allow only conservative, non-extreme planning when user confirms
clinician clearance or no relevant diagnosis:
- `aggressive_goal`: fat loss faster than 1% body weight/week, deadline-driven
  crash diet, or requested calories below safety floors.
- `bmi_18_5_to_20_fat_loss`, `very_high_training_load`,
  `allergy_complex`, `recent_major_weight_change`, `unclear_medical_status`.

Actions:
- Hard-stop: do not calculate calories/macros or adapt calorie targets. Provide
  the standard non-medical message, ask relevant safety questions, and offer
  general education, meal structure, grocery ideas, symptom-neutral tracking, or
  questions for a clinician.
- Soft-stop: clarify risk first. If planning proceeds, use the safest bound,
  no aggressive deficit/surplus, and persist the flag.
- Persist all flags in `profile/<profile_id>/core.json` under `safety.flags`;
  add short context in `safety.notes`.

Standard message:
"Non posso darti una prescrizione di calorie/macros per questo caso. Serve
validazione di un medico/dietista qualificato. Posso aiutarti con domande da
portare al clinico, educazione generale, tracking non prescrittivo e idee di
pasti compatibili con le indicazioni ricevute."
