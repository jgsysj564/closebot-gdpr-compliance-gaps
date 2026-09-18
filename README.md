# closebot gdpr: what the platform actually documents, where the gaps sit, and what your agency still has to handle

People who type "closebot gdpr" into a search bar are rarely asking whether the company has heard of European data protection law. They're usually asking one of three more specific things: can I put EU or UK leads through this platform, what paperwork exists if a client's procurement person asks, and who is on the hook when a lead complains.

Those three questions have three different answers, and only one of them is about CloseBot at all.

Short version: CloseBot states GDPR compliance on its homepage and industry pages, publishes a privacy policy that is more detailed than most tools in this category, hosts on Microsoft Azure in the United States with standard contractual clauses for the AI providers, and puts its security posture in a Trust Center. What it cannot do is make your agency compliant, because in most deployments you are the data controller and CloseBot is your processor. That distinction drives everything else.

## What CloseBot's own documentation actually says

The privacy policy is version 2.0, effective and last updated 10 February 2026. It's the document worth reading if you are doing diligence, because it answers most of the questions a client questionnaire will throw at you.

**Legal bases.** For EEA, UK and Swiss users, CloseBot lists contract performance (Article 6(1)(b)) for account creation, conversation processing, CRM sync and billing; legitimate interests (6(1)(f)) for security, service improvement, marketing and analytics; consent (6(1)(a)) for non-essential cookies, marketing email and targeted advertising; legal obligation (6(1)(c)) for tax and regulatory recordkeeping; and vital interests for emergencies. That is a normal, defensible spread. Whether each purpose is correctly mapped is a lawyer's question, not a marketing page's.

**Sub-processors.** The policy publishes tables rather than a vague sentence. Stripe handles payments, Clerk handles authentication, Microsoft Azure hosts the platform. For AI, it names OpenAI, Anthropic, Google (Gemini) and Grok, and states that data is processed through CloseBot's API keys "with appropriate data processing agreements in place." CRM partners HighLevel/LeadConnector and HubSpot are listed separately, and the policy points out that when you connect a CRM, that CRM becomes the primary storage location for lead data.

**Where the data lives.** All platform data sits on Azure infrastructure in the United States. For transfers out of the EEA, UK and Switzerland, the policy says it primarily relies on SCCs, applies AES-256 encryption at rest and TLS 1.3 in transit, uses role-based access with MFA, and commits to notifying users of government data requests where legally permitted. It also discloses the shape of the team: 10 US employees with production access, a Canadian contractor, a UK team member, roughly 20 remote team members globally, all under confidentiality obligations.

**Rights and deletion.** Access, rectification, erasure, restriction, portability and objection are all listed with the relevant GDPR article numbers and a 30-day response window (extendable by two months for complex requests). Requests go to support@closebot.ai. On account deletion, the policy says data is removed instantly, with two carve-outs: backups may retain deleted data for up to 30 days, and tax or accounting records can be kept longer, up to seven years. Disconnecting a CRM integration removes the lead data tied to that connection immediately.

**Training.** The policy is explicit that your conversations do not train third-party AI models, and that when you use your own provider keys on an Agency plan, processing follows your provider's retention policy. It does say CloseBot may use conversation data to improve its own product: prompt optimisation, agent configuration, interface refinement. Read that sentence twice before you tell a client "nothing is ever used." Prompt improvement is not model training, but it is still processing, and it should appear in your own record of processing activities.

**Article 22.** The policy states CloseBot does not make solely automated decisions with legal or similarly significant effects, and adds that lead qualification performed by your agents is your responsibility as the controller. That is the honest position, and it is the reason Article 22 stays your problem even though the software is the thing making the decision.

## The line in the transfer table worth reading twice

The AI provider transfer section lists OpenAI, Anthropic and Google with SCCs in place. Then the Grok entry reads: "[Specify location – likely China] (appropriate safeguards required)."

That is their own placeholder text, still sitting in the live policy. Maybe it gets cleaned up in a revision, and maybe Grok is optional enough that nobody notices. But if a regulated client in Germany asks you to document every country their lead data can touch, "likely China" with an unresolved bracket is not a transfer story you want to be defending. Ask before you deploy a persona on that provider for EU traffic, or pick one of the three providers with a documented location.

## Who is the controller when you use CloseBot for clients

This is the part that gets skipped in most "is X GDPR compliant" discussions, and it is the part that decides your actual exposure.

CloseBot's policy says it plainly: if you are an agency using CloseBot for clients, you are typically the controller for end-user lead data and CloseBot acts as your processor. You remain responsible for complying with privacy law regarding your clients' data. The policy also flags the awkward cases. Leads may include people under 18, and CloseBot neither controls nor verifies their age. If your bot collects information from a minor, parental consent obligations under COPPA and GDPR Article 8 land on you, not on the vendor.

Practically, that means three documents and two relationships to keep straight:

- You ↔ your client: usually a processor agreement, plus whatever the client's own privacy notice says about AI.
- You ↔ CloseBot: an Article 28 processor arrangement. CloseBot's published DPAs are with its AI sub-processors and infrastructure providers. The compliance documentation is in its Trust Center, and support@closebot.ai is the route for data subject requests and questions about terms.
- You ↔ AI provider, when you bring your own keys.

That last one is the detail most people miss about the plan structure. On Business and Free plans, conversations are processed using CloseBot's own provider accounts, with data logically separated across customers. On Agency plans, you connect your own OpenAI, Anthropic, Gemini or Grok credentials, and the policy says those conversations are processed through your provider account under that provider's privacy policy and data processing agreement. Same end result for the lead, completely different paper trail for you. If your compliance officer wants to be the one holding the DPA with the model provider, that is an Agency plan conversation.

One more product detail with privacy consequences: HIPAA accounts are pushed to Anthropic by default. CloseBot states it is currently HIPAA compliant with Anthropic, which is why every HIPAA account is routed to that provider for messages and agent processing. GDPR and HIPAA are separate regimes and you need both if you sell into US healthcare and the EU, but it does show the provider choice is tied to the compliance tier.

## The question CloseBot cannot answer for you: EU AI Act disclosure

GDPR compliance and AI Act compliance are different laws, and if you are running AI conversations with anyone in the EU, the second one now has a hard date attached.

Article 50 of the EU AI Act became enforceable on 2 August 2026. The Digital Omnibus on AI, published in the Official Journal on 24 July 2026 as Regulation (EU) 2026/1744, pushed the high-risk obligations to December 2027. It did not delay transparency. CloseBot's own write-up on the topic is blunt about the confusion, and for good reason: a lot of agencies read "the AI Act got delayed" in June and moved on.

The scope rule is the one that matters for a US-based agency: it follows the person, not the company. A US agency with US clients is in scope for any conversation where the output lands on someone in the EU, including a prospect who happens to fill out a form while visiting Lisbon. The company also flags the domestic angle: California's SB 1001 (the B.O.T. Act, in force since 2019), Maine's chatbot disclosure act (enforceable since September 2025), New Jersey, Utah's SB 226, Colorado, and the FTC Act's deception baseline all impose some form of disclosure on commercial bots. Maine's is the broadest and is enforced under its Unfair Trade Practices Act, which carries a private right of action.

The good news is that one well-written sentence satisfies all of them.

### The three tests your disclosure has to pass

Article 50 does not prescribe wording. It requires that the person be informed they are interacting with an AI system, clearly and distinguishably, no later than the first interaction. CloseBot's guidance boils that into three tests:

1. It has to be clear. The word "AI" or "automated" needs to appear. "Virtual assistant," "smart assistant" and "digital assistant" fail, because those terms have described human beings for twenty years and the Commission reads the "it was obvious" exemption narrowly.
2. It has to attach to this conversation. A line in your terms, your privacy policy, or your About page does not count. It has to be perceivable inside the interaction itself.
3. It has to arrive no later than the first message.

"Hi, this is Sarah, Vertex Realty's AI assistant" passes. "You're chatting with our smart assistant" does not.

### Where the disclosure physically goes

Here is the counterintuitive bit that saves most agencies about fifteen minutes and one rebuild: in the most common CloseBot setup, CloseBot never sends the first message. A lead fills out your form, your GoHighLevel or HubSpot workflow sends the first text, and the bot takes over from the reply onward. So the fix often isn't in CloseBot at all.

| Who speaks first | The first AI interaction is | Where the disclosure lives |
| --- | --- | --- |
| You do (form fill triggers outbound SMS or email) | Your own workflow message | Your CRM message template |
| The lead does (inbound SMS, Instagram DM, WhatsApp) | CloseBot's first reply | Job Flow Settings global instructions |
| The lead opens your web chat widget | The widget greeting | Chat Widget welcome message |

Two of those three are static configuration, which is good news: they are deterministic and don't depend on a language model deciding to comply. Only the inbound scenario routes through model instructions, so that is the one worth testing in the portal before you publish. Open a fresh inbound conversation and confirm the line actually shows up in the first reply, every time.

Long-gap reactivation is the exception to "once at the start is enough." If a bot re-opens a conversation 60 or 90 days later, treat it as a fresh first interaction and disclose again.

### The trap that costs more than a missing disclosure

There's an escalation worth knowing about. If a lead asks "is this a real person?" and your bot says yes, you have moved from Article 50 (fines up to €15M or 3% of global turnover, and for SMEs the lower of the two figures) into Article 5, which prohibits deceptive techniques and carries up to €35M or 7%.

CloseBot's Persona settings deliberately include Response Delay and Frequency AI Typos, both of which exist to make replies feel less machine-generated. That's fine as conversion design. It becomes a problem if humanisation is the disclosure strategy, meaning the plan is that the lead never figures it out. The fix is a plain-language truthfulness rule in your global instructions: if the contact asks whether they're talking to a human, confirm honestly that you're an AI assistant, never claim to be human, and offer to connect them with a team member. Then go ask your own bot, in three different phrasings, and see what it says.

## The four operational details that bite after launch

Compliance documents get signed once. These are the things that go wrong in month four.

**Transcripts are personal data, and they don't sit in one place.** CloseBot stores conversation logs and syncs them to your CRM, which becomes the primary storage location. When you count your retention obligations, count both.

**Retention versus evidence.** If a complaint arrives, the timestamped transcript showing your disclosure in message one is the artifact that resolves it. But GDPR pushes you toward deleting data you no longer need. Those pull in opposite directions, so make the retention window a deliberate decision rather than a default nobody chose. Note that outbound-first flows mean the disclosing message lives in your client's CRM, and you may lose access to that sub-account long before the complaint window closes.

**Analytics cookies on the marketing site.** CloseBot's policy lists HubSpot, Google Tag Manager, ContentSquare and Facebook Pixel, plus FirstPromoter for affiliate attribution, and states that it does not currently honour browser Do-Not-Track signals. That's a website-consent question, not a lead-data question, but it's the kind of thing that shows up in a vendor review.

**No self-serve DPA download.** The policy confirms DPAs exist between CloseBot and its sub-processors and points to the Trust Center for the security posture. If you need something countersigned in your own entity's name, budget time for a conversation rather than a click. Worth knowing before a deal is signed, not after.

## What the plans include, and which ones matter for compliance

Current pricing from CloseBot's plans page, which was last updated in June 2026, plus the help centre article on plan structure. Note the help centre still quotes an older $0.006 per message rate in places while the plans page states $0.012 for agencies; go with the plans page.

| Plan | Price | Billing | What you get | Compliance-relevant notes |
| --- | --- | --- | --- | --- |
| Free | $0 | Free forever | 1 agent, 1 user seat, 100 messages/month, 1 MB knowledge storage, unlimited account connections; overage at $0.08/message | Platform-level GDPR posture applies; conversations run through CloseBot's provider accounts |
| Core (Business) | From $64/mo, or $53/mo effective on annual billing ($640/yr) | Monthly or annual, month-to-month, no contract | Message costs included up to your monthly ceiling (entry ceiling is 500 messages), 15+ templates, human support, extra seats at $5/user/mo, storage add-ons from $0.10 to $3.00 per MB/mo, overage at 2x rate from wallet | Best fit for running your own pipeline rather than clients'; no white-label or rebilling |
| Agency | $397/mo flat | Monthly; third-party pricing walkthroughs put the annual equivalent around $331/mo | Unlimited agents and sources, white-label client portal, re-bill all costs, usage at $0.012/message rebillable, storage $0.006/MB/day, seats $5/user/mo rebillable | The only tier where you can bring your own OpenAI, Anthropic, Gemini or Grok keys, which changes who holds the provider DPA |
| Growth | Custom quote | Annual or custom terms | HIPAA compliance, quarterly audits, 99.99% priority uptime, priority support, 50+ templates | HIPAA and signed BAAs live here; ask sales for GDPR processor terms and anything your client's legal team needs countersigned |

A 7-day trial of any paid plan exists, there is no refund policy, and the free plan stays free under 100 messages a month. Full details and the current numbers are on the pricing page.

👉 [Compare CloseBot's current plans and pricing](https://app.closebot.com/a?fpr=li87)

## A practical checklist for agencies with EU or UK leads

Six things, in order of how much they reduce your exposure.

1. Find out whether you actually have EU contacts. Most agencies have never checked, and paid traffic makes "we're US-only" a hope rather than a fact.
2. Put the disclosure in the opening message of every workflow that sends the first touch, and in your inbound global instructions and widget welcome message.
3. Add the truthfulness rule to global instructions, then test it by asking your own bot whether it's human.
4. Decide your retention period on purpose, and make sure it outlives a realistic complaint window.
5. Map your sub-processors once, including which AI provider each persona uses, and hand that list to any client who asks.
6. Keep your own copy of the templates and a sample of conversations, because outbound-first evidence lives in a CRM you may not control forever.

## Who this fits, and who should look elsewhere

If you're an agency already running client accounts on GoHighLevel or HubSpot, CloseBot's positioning fits the compliance work you're being asked to do. The platform claim is on the site, the privacy policy is unusually specific, the sub-processors are named rather than gestured at, and the AI Act disclosure guidance is written as instructions rather than marketing. Third-party sentiment lines up with the product matching its billing: G2 shows 4.8 out of 5 across 191 reviews, with reviewers consistently crediting ease of use and setup speed, and a Reddit thread in r/automation sums up the migration case in one line — "way better than GHL chat AI. you can conversationally book appointments and reschedule."

For balance, one competitor comparison (Fin, formerly Intercom) makes the argument that CloseBot does not document its own SOC 2 or ISO certifications, while noting CloseBot's HIPAA coverage sits on the enterprise tier. That's a competitor's framing rather than an audit, but it's the kind of point that surfaces in enterprise procurement, so pull the Trust Center documents before you promise a client anything. CloseBot's privacy policy states that Azure carries SOC 2 Type II and ISO 27001, which is a statement about the infrastructure provider, not about CloseBot's own certifications.

Where the platform genuinely isn't the right answer: if you're a solo operator whose leads all arrive as Instagram DMs and you don't run a CRM, you'd be buying a CRM to run an agent, and the total cost of ownership doubles before the first conversation happens. Same if you want a fixed all-in price with nothing metered underneath it, or if you need to see a signed DPA before you can demo anything.

For everyone else, the realistic starting point is the free tier. 100 messages a month is enough to build an agent, run the disclosure tests in the portal, and find out whether the conversations hold up before you put a single EU lead through it.

👉 [Start on CloseBot's free plan and test your setup first](https://app.closebot.com/a?fpr=li87)

One last thing worth repeating, because it's the sentence that gets lost in every vendor review: CloseBot being GDPR compliant does not make you GDPR compliant. The controller obligations — lawful basis, retention, your own record of processing, the Article 50 disclosure wording, and the truthfulness rule when a lead asks if they're talking to a person — are yours. The vendor's job is to give you documents that hold up when someone asks. On the evidence of what's published, this one mostly does, with a couple of loose threads worth pulling before you scale EU traffic.
