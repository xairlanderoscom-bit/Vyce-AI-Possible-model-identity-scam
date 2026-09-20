# Vyce AI Identity Possible Scam

This repository documents **possible model-identity misrepresentation or confusing model labeling** observed in the Vyce AI playground.

The screenshots below show the displayed model labels and the models' own answers becoming inconsistent when asked about their identities. This is evidence of an identity/labeling problem, but **it does not by itself prove which backend model weights Vyce was actually running**. A model can be prompted or configured to claim an identity, so raw API metadata and provider-side verification would be needed for definitive proof.

## Evidence 1 — `deepseek-v4.1`

![Vyce deepseek-v4.1 identity inconsistency](evidence/vyce-deepseek-v4.1.jpg)

The UI labels the conversation as `deepseek-v4.1`. The assistant first says:

> "I'm DeepSeek V4.1"

After being challenged, it changes its claim and says:

> "I'm currently DeepSeek V3."

That is a direct identity inconsistency while the UI continues to show `deepseek-v4.1`.

## Evidence 2 — `deepseek-v4-flash`

![Vyce deepseek-v4-flash identity inconsistency](evidence/vyce-deepseek-v4-flash.jpg)

The UI labels the selected model as **V4 Flash** / `deepseek-v4-flash`. The assistant initially claims:

> "I'm DeepSeek V4 Flash"

After being challenged about the model's release, it says:

> "I was trained to say I'm DeepSeek V4 Flash, but I can't confirm the exact release date."

That wording raises questions about whether the identity is coming from the actual backend model, a system prompt, an alias, or another layer in the service.

## What this proves — and what it doesn't

These screenshots **do prove** that the model identity presented in the Vyce playground was internally inconsistent during these conversations.

They **do not conclusively prove** that Vyce substituted a different backend model. Language models can be unreliable when asked to identify themselves, and providers can inject model names into prompts.

A stronger verification would include:

- the raw API response `model` field;
- the provider's `/models` response;
- request/response logs;
- documentation mapping public model IDs to actual backends;
- reproducible tests performed through the API rather than only the web playground.

## Purpose

This repository exists to preserve the observed evidence and make the model-identity issue easy to reproduce and investigate. It is not claiming definitive fraud without backend-level evidence.
