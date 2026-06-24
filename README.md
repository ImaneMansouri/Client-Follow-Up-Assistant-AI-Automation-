# Client-Follow-Up-Assistant-AI-Automation-
Client Follow-Up Assistant

A scheduled assistant that figures out which clients haven't replied to me and drafts the follow-up so I don't have to dig through my inbox to find them.

Built with: n8n, Gmail, Google Gemini

The problem

When you're managing client work, a lot of the job is waiting on people. I'd email a client for a link, some content, an image, or feedback, and then it was on me to keep track of who hadn't replied and circle back. The actual pain was the checking. Every few days I'd go through my inbox, try to remember who I was waiting on, and figure out who needed a nudge. I run my projects in project management tools, but those track tasks and timelines. They don't watch my inbox and tell me which specific people went quiet. So that part kept living in my head, and things slipped.

The solution

I built an assistant that does the checking for me. It runs on its own every day, scans for the clients I'm still waiting on, and hands me a ready-to-send follow-up for each one. So instead of me hunting through my inbox trying to remember who owes me a reply, the list and the drafts just show up. It never emails clients on its own. I review everything and decide what actually goes out.

How it works


Schedule trigger runs daily so I don't have to remember to check.
Pull waiting emails grabs everything labeled Waiting_On_Client in Gmail, filtered to messages older than 7 days so I'm only looking at people who've actually had time to respond.
Draft the follow-up is an LLM step (Gemini) that reads the original email and writes a follow-up from me to the client, under 100 words, that names exactly what I'm still waiting on.
Send me the reminder gives me one email per client with their name, the original subject, the ready-to-send draft, and the original email pasted underneath for context.


Why I built it this way

My project management tools didn't cover this. I already track projects and tasks somewhere. What those tools don't do is watch my inbox and tell me which specific clients went silent. That gap was the thing I was doing by hand every week, so that's the thing I automated.

I kept it as draft-and-review instead of auto-send. Client communication is high stakes. I'd rather keep a human check on every message than automate away the one step that protects the relationship. The tool saves me the work of finding people and writing the message, and I still own what gets sent.

I scoped the LLM down to one job: write the draft. The client name, subject, and original email all come straight from Gmail, untouched. The model never rewrites the source of truth, so the context I'm reading is always exact. This came out of an actual bug where letting the model handle everything produced drafts addressed to the wrong person.
