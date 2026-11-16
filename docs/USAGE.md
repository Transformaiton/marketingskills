# Use the marketing skills

Install first, using [INSTALL.md](INSTALL.md). Then talk to the agent the way you would brief a careful marketer. The skill supplies the checklist. You supply the facts about the business.

These instructions were written by Corey Haines and are published here by [Transformaiton.com](https://transformaiton.com/). Transformaiton.com is not affiliated with Corey Haines and is not endorsed by him.

## What happens when you ask

1. You describe the job, ideally with the skill name.
2. The agent reads that skill. On a new project it should also look for a business brief at `.agents/product-marketing.md`.
3. It asks for anything it cannot already see: the offer, the city, the page, the numbers.
4. It returns a recommendation, a draft, or a prioritized list. Claims it cannot support should be left out or marked as unknown.
5. You edit the result and decide what goes live. The skill does not publish the page, send the email, or turn on the ad.

If the answer is generic, the usual cause is a thin brief. Add who the customer is, what they can buy, and what a good result looks like, then ask again.

## Write the business brief once

Start here on a new project:

```text
Use the product-marketing skill. Interview me and write .agents/product-marketing.md. We are a [what you do] in [city or area]. Customers find us by [how they find you]. A good lead is [the enquiry or purchase you want]. Our tone is [how the owner actually talks]. Do not invent reviews, prices, or years in business.
```

Answer the follow-up questions. Later skills reuse that file, so you do not re-explain the business every time. When the offer or the audience changes, ask the agent to update the file.

## How to ask

- Name the skill when you know it: "Use the emails skill."
- In Claude Code, a leading slash works when the skill is installed: `/emails`, `/cro`, `/seo-audit`.
- Give the constraint that matters: budget, city, what you will not claim, how soon you need it.
- Paste the page, the current email, or the numbers. A URL is enough when the agent can open it.
- Ask for a decision and the reason, not only a draft. "What should we change first, and why?"
- Tell it what it must not invent. Reviews, rankings, revenue, and awards are the usual risks.

You do not have to use the catalog's words. "Why is the contact page not getting form fills?" is enough for the cro skill to be the right match. Naming the skill helps when the agent starts answering from general knowledge.

## Four jobs

The prompts use sample businesses. Replace them with yours. Each one tells the agent which skill to use so the result follows that skill's checks.

### Landing page review

Have the URL, or the headline, the offer, and the form. Say what the page is supposed to get: a call, a booking, a purchase.

```text
Look at our homepage and tell me why a visitor might leave without asking for a quote. We are a three-person plumbing company. We want more booked calls. Use the cro skill. Do not rewrite the whole page until you have listed the problems in priority order.
```

A useful answer names the first change, why it is first, and what you would look at afterward (calls, form completions). It does not hand you a new homepage before that list exists. When you want new words, ask for the copywriting skill in a second step and point it at the problems just listed.

Related skills: [cro](../skills/cro/), [copywriting](../skills/copywriting/), [copy-editing](../skills/copy-editing/).

### Email sequence

Have the reason people joined the list, what you will not promise, and who the email is from.

```text
Write a short welcome series for people who joined our bakery's email list to get a coupon: a free coffee with a pastry. Sound like the owner. Tell me how many emails, when each one sends, and the subject line and body for each. Use the emails skill.
```

A useful answer includes timing, a subject line, and a body for each email, written as one person. It should not pretend the message is a reply (`Re:`) and it should not send anything. You copy the approved emails into the tool you already use (your inbox provider, not this repository).

Cold outreach to people who did not sign up is a different skill: [cold-email](../skills/cold-email/).

### Local SEO

Have the business name, the address as it should appear everywhere, the phone number, the hours, and the services. Mention if you have one location or several.

```text
We are a family dental practice with one office. Review our local SEO: Google Business Profile, the pages on our site, and what to fix first. Use the seo-audit skill. Do not invent reviews or rankings. Say what you could not check.
```

A useful answer separates what it could see from what it could not (it often cannot see your Google Business Profile unless you paste it or grant access). Expect items such as the name-address-phone being consistent, a page that matches the real services, and the profile's categories and hours. "You rank number one" is not a result this skill can know without data you provide.

The local checks live in the seo-audit skill, including its local-search reference. Structured business data on the site is the [schema](../skills/schema/) skill.

### Ad copy

Have the offer, who it is for, where the ad will run, and the claims you are willing to make. If a discount has an end date, say so. If it does not, tell the agent not to invent one.

```text
Write three Google search ads for a mobile dog-grooming van that serves a 15-mile radius. The offer is $20 off the first visit. Do not claim we are the highest rated. Tell me which headline to test first and what to measure. Use the ad-creative skill.
```

A useful answer is a few ads you could paste into Google Ads, plus which headline is the test and which number you would watch (calls, booking-page visits, cost per booking). Campaign structure, budget, and whether ads are worth running are the [ads](../skills/ads/) skill. Making sure those calls show up in the ad account is [conversion-tracking](../skills/conversion-tracking/).

## After the draft

- Read every claim against something you can prove. Delete the rest.
- Keep the owner's voice. If a sentence sounds like a brochure, ask the agent to rewrite that sentence only. Point it at the copy-editing skill for a pass over finished text.
- Put the approved work in your own tools: the website, the email provider, Google Business Profile, Google Ads. The skill stops at the recommendation.
- If you want the agent to read analytics or an ad account, connect that account with [tools/SETUP.md](../tools/SETUP.md). Skip that until a draft would be better with real numbers.

## When the result is off

| What happened | What to say next |
|---------------|------------------|
| The draft could be for any business | "Use the product-marketing brief. Our customers are [who]. The only offer is [what]." |
| It invented a rating, a ranking, or a revenue number | "Remove anything you cannot point to. List those as unknown." |
| It rewrote the page when you asked for a review | "Stop. Give me the prioritized problems only. Use the cro skill." |
| It used the wrong channel | Name the skill from the [catalog](../README.md#skill-catalog). |
| The advice assumes a software company and you run a local service | "We are a local service business with [one office / a service area]. Drop tactics that need an app or a free trial." |

## What this repository does not do

- It does not host your website or store customer lists.
- It does not see prompts you type into Claude, Codex, Cursor, or any other product.
- It does not replace a person checking the work before it goes out.
- It is not a support line for your ad account, your domain, or your email deliverability. Those stay with the companies you pay for them.

Questions about using this copy: [info@transformaiton.com](mailto:info@transformaiton.com), or [transformaiton.com](https://transformaiton.com/).
