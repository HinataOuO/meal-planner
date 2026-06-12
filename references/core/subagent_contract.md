# Subagent Contract

Use subagent only to save context on broad requests. Main agent owns safety,
final output, and profile writes.

Delegate when all are true:
- request likely needs 3+ refs;
- compact handoff helps routing, missing data, or adaptation;
- no safety hard-stop needs immediate refusal.

Good delegation triggers:
- complete plan from intake data: profile, goal, macros, meal prep, shopping;
- existing-profile meal prep with macro recalculation/constraints;
- weekly check-in plus adaptation;
- ambiguous memory/planning/follow-up request.

Do not delegate:
- first-run intake needing only next question;
- direct safety hard-stop response;
- simple macro calculation with complete data;
- shopping list from final meal plan.

Pass only minimum input:
- request summary, not full chat transcript;
- candidate reference paths;
- minimal phase profile fields;
- relevant `safety.flags` and short `safety.notes`;
- current plan targets for planning/adaptation;
- recent progress summary for follow-up/adaptation.

Never pass unrelated personal data, full profile dirs/history, private notes, or
other profiles.

Required subagent output:
```json
{
  "phase": "intake|planning|follow_up|adaptation|unclear",
  "needed_references": [],
  "profile_files_needed": [],
  "safety_flags": [],
  "missing_data": [],
  "assumptions": [],
  "handoff": []
}
```

Limits:
- Subagent does not save profiles, append progress, or update plans unless asked
  for draft artifact.
- Subagent does not override hard-stop or soft-stop rules.
- Main agent verifies required references before final user output.
- Skill must work the same way without subagent availability.
