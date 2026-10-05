---
name: get-started
description: Use Synero to get a second opinion from several AI models (GPT, Claude, Gemini, Grok) on a question, with a consensus answer and where the models agree and disagree.
---

# Getting started with Synero

Use the `query_council` tool when the user wants a second opinion, a cross-check, or a decision where one model's blind spot would be costly: technical choices, code or architecture reviews, research and fact checks, plans and strategy.

- Pass the user's question as `prompt`. Include any relevant context the user gave.
- Leave `preset` unset for the balanced four-model council. Use `solo` for one quick answer, `duel` for two models, `deep` for the strongest (slower) models.
- Set `web_search: true` for recent events or facts that may have changed.
- To follow up on a previous answer, pass its `queryId` as `parent_query_id`.

Present the consensus answer first, then summarize where the models agreed and where they split, naming which model took which position. Link the result `url` so the user can open the full comparison on synero.ai.

Each call is billed to the user's Synero credits (new accounts get 3 free queries). Do not call it for trivial lookups the user did not ask to cross-check.
