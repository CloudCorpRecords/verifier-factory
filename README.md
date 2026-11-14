# Verifier Factory

Five AI seats that plan, research, verify, budget and remember, building Dossier, a cited company research service.

Verifier Factory is a five seat software factory built in Band Desktop. Each seat is a separate coding agent with its own generic mandate: a Planner that coordinates and hands off, a Researcher that gathers evidence, a Verifier that independently checks every result and can reject work, a Budget Keeper that holds one shared allowance for the whole run, and a Historian that keeps the record of what was decided and when.

The factory builds Dossier, a company research service. Give it a company domain and it returns the facts a diligence check needs, legal name, headquarters, CEO, founding year, headcount range and funding, each with the source excerpt that supports it.

In development runs on Nov 13 the factory proved its gates end to end: the seats exchanged handoffs in both directions, the Verifier rejected work at preflight and the rejection changed what the team did next, the Budget Keeper held the run inside its stated allowance, and the team built and served a working service that was verified from outside the room. In the submitted run the factory completed its Stage 1 research phase, a full WebRouter review written to the repo records, before the run paused on a provider account limit. The factory, its mandates and its records are the submission; the staged build continues to the Nov 20 deadline.

Summary: A five seat AI software factory in Band Desktop building Dossier, a cited company research service, with independent verification and a shared budget on every run.

AI Disclosure: This project was built with AI coding agents working as a team inside Band Desktop. A human set up the factory, wrote the seat mandates and dispatched each stage. All product code in the run repositories was written by the agent seats in the Band rooms, and the room logs are included as proof of process.

Building process: The factory was designed seat first: five generic mandates that name a harness and a model and describe judgment, not product details, so the same factory can build other products. Development runs ran against a small practice service first, which caught two real failure modes (a seat reaching for a GUI tool that waits on a human, and shell approvals parking turns) before the submitted run started. The submitted run used a fresh room and a fresh repository, with each stage dispatched as a single task and no human steering after dispatch.

Tags: ai-agents, software-factory, band, research, verification, multi-agent

Repository contents: FACTORY.md (roster and run protocol) and mandates/ (the five generic seat mandates). Product code from the factory runs lives in the run repositories produced inside Band Desktop; room logs are the proof of process.
