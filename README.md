# gohighlevel database reactivation: how to build the campaign, price it, and stop losing replies after the first text

Somewhere in your GoHighLevel account there's a smart list of contacts who filled out a form, booked once, no-showed, or bought something two years ago and never came back. They cost you money to acquire. Nobody has texted them since. A reactivation campaign is the cheapest revenue available to most service businesses, and it's also one of the easiest things to get half-right: the sending part works fine, then a wave of replies hits an inbox with nobody watching it, and the whole thing quietly dies.

This covers the parts that actually decide whether the campaign makes money — the GoHighLevel setup, the compliance steps you can't skip, what a reply costs you in human attention, and what it costs to put software on the other end of the conversation instead of your phone.

## What database reactivation means in practice

Database reactivation is texting and emailing the contacts you already own to win back bookings, instead of buying new leads. No ad spend, no new landing page, no lead magnet. You filter your CRM for people who went cold, write one short message that sounds like a person, and run it through a workflow.

GoHighLevel ships templates for exactly this and lists database reactivation campaigns among its built-in automation use cases. The mechanics are documented well enough by HighLevel itself, and there are dozens of tutorial videos. So the interesting question isn't *how do I send a text from a workflow*. It's what happens between the first reply and a booked appointment.

## The GoHighLevel setup, step by step

The order matters here. Skip step one and carriers will silently swallow your messages while your workflow reports success.

**1. Register for A2P 10DLC first.** In the US, brand and campaign registration is required before any SMS goes out through GoHighLevel. Approval can take a few days, so start it before you build anything else. Unregistered traffic gets blocked — not throttled, blocked.

**2. Import or filter the old list, then tag it.** Build a smart list of contacts you haven't talked to in 90 days or more, or import a CSV of past customers. Tag the batch with something dated, like `reactivation-sept`, so you never text the same person twice from two campaigns.

Before you send, check consent status. Contacts who opted in to your messages years ago and never opted out are one thing; a purchased list is another, and it's the fastest route to a 10DLC campaign getting flagged.

**3. Write one short first message.** Under two sentences, human, and it should ask a question so the contact has a reason to reply. Something like "Hey Marcus, it's Dana from Ridgeline — are you still looking for help with the gutters this year?" beats any clever hook. Include an opt-out path and honor STOP immediately.

**4. Build the workflow around the first message.** Trigger on the tag. Add a wait and a follow-up message for people who don't reply, then one more a day later. Cap the sequence — three total touches is enough; four starts feeling like harassment.

Two settings do most of the work:

- **Business-hours gate.** Only send between roughly 9am and 5pm in the contact's timezone.
- **Throttle.** One message every one to two minutes, spread across a daily cap. CloseBot's own team dripped their own 15,000-contact reactivation at 50 messages per day, 1 every 2 minutes, Monday through Saturday, and said they'd be cautious about going above 500 per day.

**5. Stop the sequence the moment someone replies.** This is the step people forget. If the workflow keeps dripping follow-ups into a live conversation, the contact gets "haven't heard from you!" while they're actively typing. Add a reply condition that removes the contact from the workflow and routes them somewhere a human — or something — answers.

**6. Send in batches and watch the numbers.** A few hundred at a time. Watch reply rate, opt-out rate, and how long replies sit unanswered. If opt-outs spike, your message reads like spam or your list is too cold. Both are fixable at the message level.

## The part most campaigns fail at: who answers when 80 people text back

Here's the structural problem with reactivation. Sending is instant and scales. Answering doesn't.

A list of 2,000 cold contacts sent in small batches will produce replies spread across days, in bursts, at unpredictable hours. Each reply needs someone to read it, figure out whether it's a real interest or a "stop texting me," ask the qualifying questions, and get a time on the calendar. If a human handles that, you have two bad options: answer slowly, which is how leads go cold a second time, or stop the campaign after 300 contacts because you can't keep up.

You can see this in how people run reactivation campaigns in practice — the workflow gets built, the first batch goes out, and the campaign is "paused until we catch up." Then it never restarts.

The alternative is putting an AI agent on the reply layer. That's where CloseBot enters this conversation, and it's worth being precise about what it does and doesn't do.

## How CloseBot fits into a GoHighLevel reactivation campaign

CloseBot is a conversational AI platform that connects natively to GoHighLevel (and HubSpot, or a custom CRM) and takes over the text-based conversations already flowing through the CRM inbox. It doesn't replace HighLevel. It sits on top of the channels HighLevel already has connected — SMS, email, Facebook Messenger, Instagram DMs, WhatsApp.

### It never sends the first message, and that's fine

CloseBot's own documentation is blunt about this: the platform is responsive. Aside from follow-ups, it will not initiate a conversation with your list. You send the first text from a GoHighLevel workflow, and the agent is there the moment a contact replies.

For reactivation, that's actually a reasonable division of labor. The outbound message is a compliance-sensitive, campaign-level decision — throttle, quiet hours, consent, opt-out — and HighLevel handles that properly. The reply is a conversation, and that's the part a workflow can't do.

### Job flows and objectives instead of scripts

Inside CloseBot you build a job flow: a sequence of objectives the agent works through. For a reactivation campaign, the shape is usually:

1. Determine whether the contact is interested.
2. If yes, collect whatever's blank in the record — timezone, service address, the thing they originally asked about.
3. Book an appointment conversationally, straight onto the calendar.
4. Continue the conversation after booking so the appointment doesn't get cold before it happens.

The agent reasons through this rather than matching keywords, which is why it survives the messy replies real lists produce ("who is this", "how much is it now", "we moved").

### Disqualification and the angry ones

Two scenarios deserve their own handling, and both are standard in CloseBot setups:

- **Not interested.** A custom scenario watches for signs of disinterest wherever the conversation is, adds a `not interested` tag, and stops responding. Without a stop-responding action, the agent loops back into the main flow and keeps pitching.
- **Aggression.** CloseBot references an aggression-detected scenario: if a contact is clearly annoyed at being contacted, the agent tags them `ai off` and `not interested` and goes silent. For a reactivation list specifically, this is not optional. Old leads are allowed to be irritated; the campaign shouldn't argue with them.

### CloseBot re-ran this on its own list

Worth noting because it's the closest thing to a documented production run: CloseBot ran a database reactivation campaign on 15,000 of its own old leads, with the agent tagging contacts as they replied so HighLevel could move opportunities through stages — Attempting Contact, Engaged, Demo Booked, Not Interested. Replies pulled a `ai responded` tag, which triggered the pipeline update. The agent's job was answering questions and steering toward a demo calendar.

The company also documents Smart FAQ, which watches conversations for questions the agent can't answer confidently and flags them instead of inventing something. When a human answers once, the platform can follow up with every lead who asked the same question — a neat fit for reactivation, where the same three objections show up over and over.

On the results side, CloseBot's site claims 1M+ booked appointments, roughly 150k messages a day, and 1,000+ agencies on the platform. Those are vendor numbers, not audited ones. The testimonials are vendor-published too, though one is more specific than most:

> "We added about $1k in recurring revenue in 10 days from CloseBot reaching out to dead leads... yeah, this works."
> — Eric McAvoy, Co-Founder, Freedom Pro (published on CloseBot's homepage)

### The limits you should know before buying

- **You still need a CRM.** CloseBot answers conversations inside HighLevel, HubSpot, or a custom source. If you don't run one, you're buying two products.
- **Knowledge base upkeep is real.** An agent that gives a stale price on a reactivation list is worse than no agent. Someone has to keep the knowledge current.
- **No bring-your-own API key.** CloseBot states this is a security decision, so you can't plug in your own model key to cut spend.
- **No refunds.** There's a free-forever tier under 100 messages a month and a 7-day trial of any paid plan. Test during the trial.
- **High-ticket negotiation still needs a human.** Agents qualify and book. They don't write custom proposals.

## What CloseBot costs

Pricing below is from CloseBot's plans page. Every plan runs month to month with no contract.

| Plan | What's included | Price | Billing | Get started |
| --- | --- | --- | --- | --- |
| Free | 100 monthly messages, 1 agent, 1 user seat, 1 MB knowledge storage, unlimited account connections | $0 | Always free | [Start free with 100 messages](https://app.closebot.com/register?fpr=li87) |
| Core (Business) | Message costs included in the base price, 15+ templates, human support, additional seats at $5 each, add-on storage and agents | from $64/mo USD | Monthly; price scales with monthly reply volume; annual billing available | [Start the 7-day business trial](https://app.closebot.com/register?fpr=li87) |
| Core (Agency) | Unlimited client agents, white-label client portal, rebill all costs, messages at $0.012 each (rebillable) | $397/mo USD flat | Monthly | [Start the 7-day agency trial](https://app.closebot.com/register?fpr=li87) |
| Growth | 50+ templates, HIPAA compliance, quarterly audits, 99.99% priority uptime, priority support | Custom quote | Via sales call | [Talk to CloseBot about a custom plan](https://app.closebot.com/a?fpr=li87) |

Two details worth understanding before you pick a row:

**The business tier scales with reply volume.** The plans page has a slider for monthly AI replies (100 up to 100K+) and the price moves with it. That's the honest way to think about reactivation volume: a 2,000-contact reactivation might produce a few hundred replies, which is a different tier than an inbound-heavy operation doing 20,000.

**"Message" means segment.** One message equals one segment normally. If you switch on the Agent Node's expanded mode — many tools, unlimited instruction size — billing shifts to token costs, and a single message can consume several segments. Budget conservatively if you build heavy agents.

### The full cost stack, honestly

CloseBot is rarely your only subscription, and a reactivation campaign has its own line items:

- **GoHighLevel:** Starter at $97/mo, Unlimited at $297/mo, Agency Pro at $497/mo, depending on how many sub-accounts you run.
- **CloseBot:** $0, from $64, $397, or custom.
- **A2P 10DLC and SMS usage:** registration plus per-message carrier and platform fees, billed by HighLevel.
- **Set-up time:** building the workflow, the job flow, the questions the agent must collect, and testing it against real replies.

A single business running its own reactivation at modest volume lands somewhere around $161/mo before SMS costs — $97 for GoHighLevel Starter plus $64 for the entry business tier. That number only makes sense if the campaign books work. Which is why the next section matters more than the price table.

## If you're selling reactivation as an agency service

Database reactivation is one of the easier offers to sell to a local business because the asset already exists. You're not asking them to spend on ads; you're asking to monetize a list they've been ignoring.

The pricing spread in this market is wide and everyone quotes their own numbers. CloseBot's own page states that some agencies charge as little as $100/month for AI services while others report $10k+ monthly from a single client, and that CloseBot agencies bill an average of $500 per client per month. Treat that as the company describing its customers, not as a benchmark you can copy.

What's verifiable is the mechanics on the agency plan: $397/mo, unlimited client agents, a white-labeled client portal, and messages at $0.012 each that you rebill at your own markup. Storage is billed at $0.006 per MB per day, also rebillable. Your clients top up a wallet that pays you through your Stripe account; you pay CloseBot from yours. The margin is the gap you set.

A practical way to package it: a one-time reactivation campaign fee, then a monthly retainer for the agent handling ongoing replies and follow-up. The campaign is the proof; the retainer is the business.

👉 [See how the agency rebilling setup works](https://app.closebot.com/a?fpr=li87)

## Where this approach falls short

Three honest caveats, because the failure modes are predictable.

**List quality beats message quality.** A list of people who opted in and had a real interaction will outperform a scraped list every time, no matter how good the agent's texting style is. Response rates for reactivation vary enormously by list and industry — you'll see confident numbers from vendors in either direction, and none of them describe your list.

**Consent and compliance aren't optional.** A2P 10DLC registration, opt-out handling, quiet hours, and an honest answer to "did these people ever agree to hear from us" come before optimization. An agent that replies beautifully to a non-compliant campaign doesn't help anyone.

**The agent is a setter, not a closer.** It qualifies, follows up, books, and handles objections well enough to get a call on the calendar. The call itself is still a human job, and pretending otherwise is how agencies lose clients in month two.

## Quick answers

**Do I need a separate tool for reactivation, or does GoHighLevel do it?** GoHighLevel handles the campaigning layer — lists, templates, SMS workflows, throttling, pipeline stages. It also has its own Conversation AI. CloseBot is the alternative when you want the reply conversation handled by a purpose-built agent that books appointments and re-bills cleanly across client accounts.

**How long does setup take?** The sending workflow is an afternoon. A first agent in CloseBot can go live the same day using templates; expect longer if you're wiring industry-specific tools or a serious knowledge base.

**Can I run reactivation for multiple clients on one plan?** On the agency plan, one agent can serve unlimited accounts within a single niche. Different industries need additional agents.

**What happens to contacts who say "not interested"?** They get tagged and the agent stops responding. In a paired GoHighLevel workflow, that tag can also move the opportunity out of the active pipeline so nobody calls them twice.

Set up the sending side properly, keep the batches small, and put something on the reply side that doesn't sleep.

👉 [Start on CloseBot's free plan and build your first reactivation agent](https://app.closebot.com/register?fpr=li87)
