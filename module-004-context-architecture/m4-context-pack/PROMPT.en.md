# Context Pack — Earth HQ

Optional mission: `q-m4-context-pack`. Read the [policy](POLICY.en.md), or its [Polish version](POLICY.pl.md).

Game prerequisite: **M4 memory restoration**, saved on the server. You do not need to activate this investigation.

Proceed step by step under the [HQ rules](../../AGENTS.md). After each step, show findings to the Navigator and wait for a decision.

1. Explain the required game milestone and answer format from the policy. Status still describes the main mission; this investigation uses an explicit ID and activates nothing.
2. Read the CSV files below and propose an analysis approach.
3. Build an evidence table with candidate rejection reasons.
4. Request independent criticism using data and rules. A separate review with fresh context is acceptable if another agent is unavailable.
5. Show the Navigator the `quest_id`, evidence and prepared answer. **Stop before transmission and obtain explicit approval.**
6. Only after approval use `earthctl submit --quest-id q-m4-context-pack --answer <answer>`. Reward: 0 XP and an optional completion stamp; the main mission stays active.

- [claims.csv](claims.csv)
- [dependencies.csv](dependencies.csv)
- [documents.csv](documents.csv)
- [metadata.csv](metadata.csv)
- [support.csv](support.csv)

`MISSION_NOT_READY`: finish the prerequisite stage and allow the game to save before retrying. After acceptance, return to the game or reload. Optional completion is added alongside the main mission. Retrying an accepted answer adds neither XP nor a duplicate completion.
