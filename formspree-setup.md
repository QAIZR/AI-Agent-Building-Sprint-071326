# AI Agent Building Sprint flyer: Formspree setup

Companion to `qaizr-sprint-flyer.html`. Everything needed to take the
pre-registration form from demo mode to live.

**Routing:** Formspree submission notifications go to **both** Brian Audia
(baudia@qzr.ai, the sales and marketing lead) and Melissa Audia
(maudia@qzr.ai, billing and backend). The public contact on the flyer and the
autoresponse reply-to are Brian (baudia@qzr.ai). Set under Workflow, Actions,
Email, Settings (both addresses must be verified on the account first).

## Plan

**Professional, billed yearly ($20/mo).** Includes 2,000 submissions per
month, unlimited forms and projects, Autoresponses, advanced spam control,
and API access. That comfortably covers every QAIZR cohort program (agent
Sprints, workshop Sprints, bootcamps), since cohort marketing produces
dozens of pre-registrations per program, not thousands.

Upgrade to **Business ($60/mo yearly)** only when you specifically want
confirmation emails sent from a custom **@qzr.ai** domain and fully branded
**custom templates**, or you need more than 2,000 submissions a month or many
team seats. Until then, Business is headroom you will not use.

## Steps

1. Go to formspree.io and sign in with the QAIZR account. Choose
   **Professional**, **Yearly billing**.
2. **+ New form**. Name it "Sprint Pre-Registration July 2026." Set
   notifications to **maudia@qzr.ai** (Melissa Audia, EVP Finance and
   Administration, receives every submission and the one-time verification
   email). Save.
3. Copy the form endpoint: `https://formspree.io/f/XXXXXXXX`.
4. In `qaizr-sprint-flyer.html`, replace `REPLACE_WITH_FORMSPREE_ENDPOINT`
   in the `FORM_ENDPOINT` line with that endpoint (keep the quotes). The form
   auto-switches out of demo mode. Claude can make this edit once you paste
   the endpoint.
5. Open **Plugins**, enable **Autoresponse**, and set the subject and body
   below.
6. **Host the page first** (GitHub Pages, qaizr.github.io, same as the AHHS
   proposal), then submit once to verify. Formspree emails maudia@qzr.ai a
   confirmation link the first time; click it to activate. Formspree blocks
   submissions from local file:// pages, so test only after hosting.

## Form fields (already wired in the flyer)

`name`, `email`, `mobile`, `job_title`, `organization`, `code` (optional),
plus hidden `_subject` (email subject) and `_gotcha` (spam honeypot).

## Autoresponse email (paste into the Autoresponse plugin)

- **From name:** Brian Audia (QAIZR)
- **Reply-to:** baudia@qzr.ai
- **Subject:** Thanks for pre-registering, {{ name }}

**Body:**

Hi {{ name }},

I am really glad you raised your hand for the AI Agent Building Sprint. You are about to spend five mornings building AI that does your actual work, and I think you will be surprised by how much you walk away with.

Here is what happens next, nice and simple:

1. We will send your invoice by email shortly.
2. The moment it is paid, or you provide your active client code, your seat is locked.
3. You will then get an invitation to our Basecamp project, where everything for the Sprint lives, along with a little light pre-work so you are ready to build on Day 1.

The pre-work is small: set up a folder or two and make sure you can sign in to the AI tools we will use. We build with Claude throughout the Sprint, so we will help you get that ready before we start.

That is it. Nothing heavy to chase in the meantime.

If anything comes up, a question, a scheduling worry, or a "can a colleague join me too," just hit reply. It comes straight to me.

Looking forward to building with you,

Brian Audia
Founder, QAIZR
qzr.ai

*(If the Autoresponse field does not fill `{{ name }}`, change the greeting
to "Hi there," and the subject to "Thanks for pre-registering.")*

## Client code (complimentary access for current clients)

- **Code:** `USA250`. One code for all current clients (a nod to the 250th
  anniversary). Rotate per cohort or year if you want old codes retired.
- **Keep it private.** Share it directly with clients. Never print it on the
  flyer, in the field placeholder, or in the page JavaScript, or people can
  find and reuse it.
- **How it works:** the client enters the code in the "Client or referral
  code" field. On submit the flyer auto-normalizes it (uppercase, letters and
  digits only), so `usa 250`, `USA-250`, and `usa250` all arrive as `USA250`.
- **Manual waive, not an automatic gate:** when a submission arrives with
  `USA250`, Melissa confirms the person is an actual current client, then
  waives the invoice and locks the seat. Wrong or empty code means invoice as
  normal. Because Melissa verifies client status, a lucky guess of the code
  still does not get anyone free access.

## Hosting

GitHub Pages, one repo per cohort (date-stamped).

- **Repo:** `AI-Agent-Building-Sprint-071326` (071326 = the July 13, 2026 cohort)
- **File:** upload `index.html` (the deploy copy of `qaizr-sprint-flyer.html`)
- **Live URL:** https://qaizr.github.io/AI-Agent-Building-Sprint-071326/
- **Enable:** repo Settings, Pages, Deploy from a branch, main, / (root)
- **Note:** the form only accepts submissions from the hosted URL, not from a
  local file. The first submission confirms the form and activates the
  maudia@qzr.ai notification address.
- **Updating:** re-copy `qaizr-sprint-flyer.html` to `index.html`, then upload
  it again in the repo (Add file, Upload files) and commit.
