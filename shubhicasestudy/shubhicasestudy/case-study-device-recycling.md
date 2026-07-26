# Circular Electronics Platform

**Role:** Product Designer (Freelance)
**Client:** [Client name — confirm if you want it named or kept generic]
**Scope:** End-to-end UX for a three-sided web platform (Donor, Technician, Admin)
**Timeline:** ~40 hours (UX scope)

---

## Context & Challenge

Electronic waste is one of the fastest-growing waste streams globally. While many donated devices still retain real value, the organizations responsible for processing them often rely on fragmented workflows — spreadsheets, paper records, emails, and disconnected systems. This led to inconsistent device evaluations, poor traceability through the refurbishment lifecycle, heavy manual admin work, limited transparency for donors, and slow turnaround before devices were resale-ready.

My client operates within the circular economy — maximizing the usable life of electronics before recycling them, rather than following the traditional purchase → use → dispose model. Instead:

```
Donate → Evaluate → Reuse / Refurbish / Harvest Components → Resell → Recycle (only when necessary)
```

The platform I designed doesn't just manage donations — it manages the entire lifecycle of an electronic asset, from the moment it's handed over to the moment it's resold.

## Goals

1. Help donors donate devices with confidence and visibility into what happens next.
2. Standardize technician evaluation workflows to reduce subjective, inconsistent decision-making.
3. Give administrators the tools to manage users, operational settings, and system configuration.
4. Maintain complete traceability of every device throughout its lifecycle.
5. Generate structured product listings ready to publish directly to Shopify.

## Understanding the Ecosystem

Rather than designing three isolated user journeys, I started by mapping the device itself — the one entity every persona interacts with at a different stage of its life:

```
Donation → Collection → Registration → Evaluation → Reuse/Refurbish/Harvest → Testing → Listing Creation → Shopify → Buyer
```

This reframing mattered: instead of three disconnected products, I was really designing one system — the device's journey — viewed through three different lenses.

**Donor** — wants to donate with confidence and see what happens after. Pain points: no visibility once the device leaves their hands, uncertainty around data handling, low trust in the process.

**Technician** — wants a consistent, guided way to evaluate a device and route it to the right outcome. Pain points: manual documentation, inconsistent evaluations between technicians, disconnected tools, poor traceability.

**Admin** — wants operational consistency across the org: users, permissions, questionnaire configuration, donation centers, couriers, device categories. Pain points: administrative overhead, inconsistent processes, juggling too many operational settings.

## Research & Design Principles

I researched how organizations in refurbishment and reverse logistics typically manage devices, and rather than benchmarking against direct competitors (there weren't clean equivalents), I studied interaction patterns from enterprise products solving structurally similar problems:

| Product | Pattern applied |
|---|---|
| Shopify Admin | Product management, publishing workflows, inventory patterns |
| Jira | Status-driven workflows, progress tracking |
| ServiceNow | Enterprise dashboards, tables, filters, operational management |
| Back Market | Refurbished product presentation, buyer trust signals |
| Amazon Renewed | Product information hierarchy, certification display |

This research, combined with mapping the org's existing paper-and-spreadsheet process, surfaced four principles that guided every design decision going forward:

- **Standardize decision-making** — guide technicians through consistent evaluation, rather than leaving it subjective.
- **Reduce operational complexity** — break long workflows into manageable, guided steps.
- **Design around the device** — every interface revolves around the lifecycle of a single device, not an isolated user journey.
- **Build trust through transparency** — visibility for donors, traceability for internal teams.

## Deep Dive: The Technician Experience

The technician workflow became my primary design focus — it's the most operationally complex part of the system, and the decisions made here directly determine whether a device gets reused, refurbished, harvested for parts, or resold. Getting this workflow right had the most leverage on the entire business.

I designed a single guided flow that walks a technician through:

```
Scan QR Code → Device Overview → Triage Questionnaire → Lifecycle Decision
(Reuse / Refurbish / Harvest) → Device Processing → Finalization → Listing Preview → Publish to Shopify
```

**Why a guided, linear flow rather than a dashboard of disconnected tools:** the existing process — manual inspection, paper notes, spreadsheet updates, email handoffs — meant every technician evaluated devices slightly differently, and there was no single record of what actually happened to a device. A structured, step-by-step flow does two things at once: it reduces cognitive load on the technician (one decision at a time, not a wall of fields), and it guarantees the same information gets captured for every device, which is what makes downstream traceability and Shopify listing generation possible at all.

### Standardizing Device Evaluations

One of the key challenges identified during discovery was ensuring that every technician evaluated devices consistently. Without a standardized process, assessments could vary depending on individual experience, making it difficult to maintain quality and traceability across refurbishment centers.

To address this, I designed a centrally managed, rule-based triage system. Instead of allowing technicians to create their own inspection criteria, administrators configure the questionnaire for each device category, and every question includes a predefined passing condition — establishing a consistent evaluation framework across the organization. For example:

| Question | Expected Passing Answer |
|---|---|
| Does the device power on? | Yes |
| Is the display functioning correctly? | Yes |
| Is there evidence of liquid damage? | No |
| Battery Health | Good or Excellent |

This allows the organization to update evaluation standards without changing the technician experience — every device is assessed against the same criteria, regardless of who's evaluating it.

### Lifecycle Recommendation

After the technician completes the questionnaire, the system compares the responses against the administrator-defined rules to determine the device's overall condition, and recommends one of three lifecycle paths:

- **Reuse** — the device is fully functional and ready for resale with minimal intervention.
- **Refurbish** — the device requires repair, upgrades, or maintenance before it can be resold.
- **Harvest** — the device isn't economically repairable, but functional components can be salvaged for future repairs.

The recommendation serves as decision support, helping technicians evaluate devices more consistently while reducing manual interpretation.

### Preserving Human Expertise

Although the platform generates a recommended lifecycle, the final decision always remains with the technician. Technicians can review the recommendation alongside their physical inspection and either accept it, or override it when their professional assessment indicates a more appropriate outcome.

**Design principle: support decisions — don't replace them.** Rather than automating refurbishment decisions, the platform gives technicians a standardized recommendation based on configurable business rules. This reduces variability across evaluations while preserving the technician's role as the final decision-maker — the system handles consistency, the technician handles judgment, especially for edge cases automated logic can't fully capture.

This is what ties all three personas together into one coherent system, rather than three disconnected products: the Admin defines the evaluation standards, the system applies those standards consistently, the Technician makes the final judgment call, and the device moves into the appropriate lifecycle. It's a clear example of a human-in-the-loop decision-support pattern — a genuinely valuable approach in enterprise product design, and one that echoes the same "AI surfaces evidence, human decides" principle from my Moderation case study, applied to a very different domain.

## Donor & Admin: Supporting the Same Ecosystem

**Donor.** The donor-facing experience prioritizes simplicity and trust: register, donate a device, answer a short questionnaire, schedule a pickup, track the device, and receive a sustainability certificate once it's processed. The certificate matters most here — it closes the loop by showing the donor tangible proof of what happened to their device, directly addressing the trust and visibility gap that existed in the org's prior process.

**Admin.** The admin experience is a management layer rather than a linear journey — a dashboard for monitoring the system, plus tools for managing users, roles, donation centers, courier services, questionnaires, and device categories. Its main job is keeping the other two experiences consistent: the questionnaire an admin configures is what a technician sees during triage, and the categories an admin defines shape how listings get structured for Shopify.

## Information Architecture

```
Platform
├── Donor        → Register · Donate Device · Schedule Courier · Track Device · View Certificate
├── Technician    → Scan QR · Device Details · Triage Evaluation · Lifecycle Selection ·
│                   Processing · Finalization · Publish to Shopify
└── Admin         → Dashboard · Users · Roles · Donation Centres · Courier Services ·
                    Questionnaires · Device Categories
```

## Expected Outcomes

By digitizing the refurbishment workflow, the platform aimed to:

- Standardize device evaluations across technicians.
- Improve operational efficiency and reduce manual documentation.
- Increase traceability across the full device lifecycle.
- Improve donor confidence through transparency.
- Enable faster creation of resale-ready listings.

## Reflection

This platform hasn't shipped yet — the outcomes above are the goals the design was built to achieve, not results I've measured. That's worth stating plainly rather than implying otherwise.

If I extended this further, the most interesting next step would be closing the loop on the Lifecycle Recommendation itself: right now the rules are static, defined once by an admin. Over time, technician override patterns are a valuable signal — if technicians consistently override a "Refurbish" recommendation to "Harvest" for a specific device category, that's a sign the underlying rules need to be revisited, not just the individual device's evaluation. Designing a way to surface that feedback loop back to admins would make the whole system get smarter with use, rather than staying fixed at launch.

---

*Note: this case study leads with Technician as the primary deep-dive per your direction — it has the clearest end-to-end story and the most business-critical decisions. Donor and Admin are intentionally lighter, framed as "the same ecosystem, different lens," which should keep this from reading as three shallow case studies stitched together.*
