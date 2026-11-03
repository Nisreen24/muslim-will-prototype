# Muslim Will · v40 restructure (free-first)

Source of truth: client meeting brief, 3 Nov 2026. Prototype: `design/simulator-v40.html` (`node serve.mjs` → http://localhost:3000). v39 is unchanged; all v40 changes are one layer at the end of the file.

---

## v41 update: aligned with the live web funnel

Prototype: `design/simulator-v41.html` (index opens it). The Figma file couldn't be opened (connector not connected), so the web funnel screenshots were the structural reference. Changes on top of v40:

| Area | v41 |
|---|---|
| Value experience | Faraid calculator, 5 steps: you → spouse → children (sons / daughters) → parents (brothers and sisters only when they can inherit) → result. Result = Faraid % vs Ontario-without-a-Will %, plus "Biggest gap". Then "Let's fix this for your family": 1 wrong shares → free Will, 2 estate no one can find → My Vault (optional). Answers prefill Chapter 2. |
| Account | One consent checkbox + "Review all 10 acknowledgements" (read view). CTA "Create account and start my Will". No acknowledgement gate before Chapter 1. |
| After the draft | New "Choose how to protect it": Basic Will (free) / Will + My Vault / Notarized Will. Default = Basic. Payment only for the two paid options. |
| Free Will | "Your Islamic Will is ready" → print → sign at home. No review stages. |
| Notarized | Scholar review → Legal review → Ready for attestation → Completed, then book Zoom or a partner office. |
| Colour | Burgundy removed from progress, selection, info and links (now gold / navy). Kept for errors, warnings, destructive actions. The red notification dot on the bell stays (client-approved). |
| Config | `API.products` (Vault $7.99/mo; Notarized $350, $275 with Vault, both as on the website) and `API.config` (`reviewIncludedIn`, `printBeforeReview`, `ontarioPreferential`). |

Demo buttons: Entry: free Will funnel · Entry: My Vault · Will in progress · Will drafted · choose · Free Will ready · Notarized · in review · Ready for attestation · Will done · no Vault · Will + Vault · Vault only.

## A. Sitemap

```
Logged out
├─ Onboarding: Welcome → Islamic Will → My Vault (optional) → Start where it makes sense
├─ Value experience (5): Your situation → Inheritance difference → Hard-to-find information → Your result → Start your free Will
├─ Create account: Google / Apple / Email (name → email → password) · Sign in · Forgot password
└─ Vault discovery (entry from a Vault campaign)

Logged in (tab bar)
├─ Home: status card · shortcuts for owned products · one recommendation
├─ Will
│   ├─ Your Will (6 chapters) → Acknowledgements (once) → Ch1–Ch6 → Will created
│   ├─ Status: Submitted → Scholar review → Legal review → Ready for signature → Completed
│   └─ Signing: Sign at home (free) | Notarized attestation (paid) → method → time → booked → executed
├─ Vault: not subscribed → Vault discovery → Payment · subscribed → Vault hub → 4 registers
└─ Profile: Personal info · Security · My products · Billing · Family access · Documents · Support
```

## B. End-to-end flows

| User | Flow |
|---|---|
| New, from the Will campaign | Value 1–5 → Create account → Your Will → Acknowledgements → Ch1…Ch6 → **Will created (print free)** → Reminders → Home → (optional) Vault / Attestation |
| New, opens the app | Onboarding 1–4 → Value 1–5 → same as above |
| New, from a Vault campaign | Vault discovery → Start My Vault → Create account → Payment → My Vault active → Home |
| Returning | Sign in → Home → status card's CTA continues the right task |
| Will only | Home → Will status/shortcuts → one Vault discovery banner |
| Vault only | Home → Vault status + modules → "Ready to create your Islamic Will?" (free) |
| Will + Vault | Home → both shortcut rows → contextual recommendation (assets, family, maintenance) |

## C. Screen inventory

**Keep:** sign in, forgot / reset password, biometric lock, family invite, ch1–ch5 and their sub-screens, chapter-saved cards, attestation method / time / partner office / booked / cancel / reschedule, executed, docs upload, all Vault registers + add / edit / view, personal info, security, change email, delete account, payment method, family roster, support chat, reminders.

**Modify:**

| Screen | Change |
|---|---|
| Welcome, ob1–ob3 | Client copy; "I already have an account" on Welcome; Skip and last CTA go to the value experience |
| su0 Create account | Merged with the old gateway: Google / Apple / email + Sign in link + the only legal line |
| su1–su3 | 3 steps (was 4); password step creates the account; verification by emailed link |
| suname | Creates the account directly |
| su4 Acknowledgements | Moved out of sign-up; shown once right before Chapter 1 |
| bridge | "Your Will, step by step"; free; rows for Print / Review / Signature |
| Will tab | Rebuilt: status card + chapters + print / review / signature (old 7-section mock removed) |
| ch6 Review | Check badge per chapter, "View / Edit", Preview my Will, CTA "Create my Will" |
| submitted → Will created | Print free now; reviews run in the background |
| status | 5 client stages; gold in-progress, burgundy only for "Action needed" |
| Home | State-aware; no chooser gate; one recommendation from a priority engine |
| Vault discovery | Price from API |
| Vault hub | Concise hero, plan card with old prices removed |
| Payment / Paid | Only for a chosen product (Vault or Attestation); prices from API |
| Profile, My products, Billing, Family access | No packages or old prices; Billing shows "No payments yet" when free |
| Vault filters | 38px pills, 8px gap, neutral inactive / navy active, horizontal scroll |
| Wasiyyah budget | Quick fill hidden when no allowance is left |

**Remove:** auth gateway (`gate`), starting-point chooser (`begin`), plan picker (`plans`), family package count (`family`), email-code step (`su5`), path, previous dashboard (`dash`), old Will-tab questions (`q1`, `q2`, `done`), parked name screen (`ob4`). Links to them are redirected.

**New:** value experience `val1`–`val4`, `fwill`; `signhow` (choose how to sign); `selfsign` (free signing guide).

## D. CTA / navigation map (main CTAs)

| Screen | CTA → destination |
|---|---|
| Welcome | Get started → ob1 · I already have an account → Sign in · Skip → val1 |
| ob1 / ob2 | Continue → next · ob3 Get started → val1 |
| val1–val4 | Continue → next step (val1 needs both answers) |
| fwill | Start my free Will → Create account (or Your Will if signed in) · Start with My Vault → Vault discovery |
| Create account | Google / Apple → Confirm name → account · Email → name → email → password → account · Sign in → Sign in |
| Account created | Will entry → Your Will · Vault entry → Payment (My Vault) |
| Your Will | Start chapter 1 → Acknowledgements (first time) → Ch1 |
| Chapter saved | Continue to next chapter · Back to Home |
| Ch6 | Create my Will → Will created |
| Will created | Download / Email (free) · Continue → Reminders (first time) → Home |
| Status | Ready for signature → How to sign · Completed → My documents |
| How to sign | Sign it myself → Sign at home · Choose attestation → Payment (or method if paid) |
| Sign at home | Mark as signed → Home ("Your Islamic Will is ready.") |
| Vault tab | Not subscribed → Vault discovery · subscribed → Vault hub |
| Vault discovery | Start My Vault → Payment (or Create account if signed out) |
| Payment | Pay → Paid · Vault: Open My Vault / Back to Home · Attestation: Choose a time → method |

## E. User-state logic

| State | Source |
|---|---|
| `authed` | account created / signed in |
| `will` active | starting the free Will (no payment) |
| Will stage | chapters done → submitted → reviewed → booked (paid) → executed |
| `vault` | My Vault subscription paid |
| `attestPaid` | notarized attestation purchased |
| `entry` | campaign intent (`will` / `vault`); decides post-signup routing, so nobody is asked to choose twice |

## F. Payment logic

- Payment appears only after the user taps a paid option: Start My Vault, Choose attestation, or Add in My products.
- No card is ever asked for the Will. No card "just in case".
- Product, price, currency and interval come from the product config (`API.products` in the prototype). Old prices ($350, $40.99, $315, $6.99) are removed.
- The prototype's Vault ($7.99 CAD / month) and Attestation ($149 CAD one-time) values are **placeholders in the mock config**, to be replaced by the live API.

## G. Home state matrix

| State | Status card (primary) | Shortcuts | Recommendation (one) |
|---|---|---|---|
| Signed in, nothing started | Start your Islamic Will → Your Will | — | See how My Vault works |
| Will in progress | Continue your Will · x of 6 · "Continue Family" | — | Vault discovery (below) |
| Will in review | Your Will is being reviewed → Status | Print · Status · Beneficiaries · Guardians | Vault discovery |
| Ready for signature | Your Will is ready to sign → How to sign | same | Vault discovery |
| Will done, no Vault | Your Islamic Will is ready. → View my Will | Beneficiaries · Guardians · Documents · Update Details | "There's more you can keep protected." → Vault discovery |
| Will + Vault | Will status | Will row + Vault row | Add your assets → Invite family → "Your plan is in good shape." |
| Vault only | My Vault status | Vault row | "Ready to create your Islamic Will?" → free Will |

Recommendation priority: urgent issue (scholar question) → Will for Vault-only users → missing estate data → family access → Vault discovery → maintenance. It never repeats the status card and never sells something the user already owns.

## H. Vault state matrix

| State | Vault tab | Home | Profile › My products |
|---|---|---|---|
| Not subscribed | Discovery: navy hero, 4 modules, API price, Start My Vault | No Vault modules shown; one discovery banner | My Vault · Add |
| Subscribed, empty | Hub: concise hero, stats, 4 registers | "Keep organizing My Vault" (Vault-only) or "Add your assets" banner | Active · Cancel My Vault |
| Subscribed, in use | Hub with values | Vault shortcut row; contextual banner | Active |
| Cancelled | Hub until period end | as subscribed | Ends <date> · Keep My Vault |

## I. Prototype implementation

- `design/simulator-v40.html`; `index.html` now opens v40.
- Demo buttons: Entry: free Will funnel · Entry: My Vault · Will in progress · Will in review · Ready to sign · Will done · no Vault · Will + Vault · Vault only.
- URL helpers: `?entry=will|vault`, `?tool=<demo button id>`, `?seq=step|step` (headless walkthroughs), `?still=1` (no animation, for screenshots).

**Open points for the client:**
1. Is scholar and legal review included with the free Will, or part of a paid tier? The prototype assumes it is free and runs in the background.
2. Live prices for My Vault and Attestation.
3. Should the free Will PDF be printable before the reviews finish (prototype: yes, "keep a copy while we review it")?
4. Family plan / shared Vault: hidden until it ships; only "Family access" invites remain.
