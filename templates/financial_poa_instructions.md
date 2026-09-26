---
kind: memo
title: Nevada financial power-of-attorney instructions
respondent_type: person
code: financial_poa_instructions
jurisdiction: NV
confidential: true
prompts:
  nominations_ready: Have the financial agent and successor agents been selected?
  effective_authority: When should the financial power take effect?
  coagent_action: If co-agents are selected, how should they act?
  content_authority: What authority over the content of electronic communications should the agent have during life?
choices:
  nominations_ready:
    'yes': Selections recorded privately; confirm willingness to serve
    'no': Selections are still needed
    not_on_file: Not yet on file
  effective_authority:
    immediate: Immediately, subject to applicable execution requirements
    contingency: On a licensed medical doctor's written opinion of incapacity (springing)
    not_on_file: Not yet on file
  coagent_action:
    single: Only one acting agent is intended
    together: Together
    separately: Separately
    not_on_file: Not yet on file
  content_authority:
    allow: Express authority, subject to documented limits
    withhold: Withhold authority
    limited: Account-specific instructions require drafting
    not_on_file: Not yet on file
questionnaire:
  BEGIN:
    _: person__client
  person__client:
    _: project__engagement
  project__engagement:
    _: custom_single_choice__nominations_ready
  custom_single_choice__nominations_ready:
    _: custom_single_choice__effective_authority
  custom_single_choice__effective_authority:
    _: custom_single_choice__coagent_action
  custom_single_choice__coagent_action:
    _: custom_single_choice__content_authority
  custom_single_choice__content_authority:
    _: END
  END: {}
workflow:
  BEGIN:
    intake_submitted: lawyer_review
  lawyer_review:
    reviewed: END
    changes_requested: reask__client
  reask__client:
    intake_resubmitted: lawyer_review
  END: {}
---

# Nevada financial power-of-attorney instructions

Client: {{person__client.name}}

Matter: {{project__engagement.name}}

This questionnaire collects the client's instructions for a Nevada financial power of attorney. It grants no authority
and is not an instrument ready for signing. Counsel reviews each answer and records any unknown fact as Not yet on file.

## Recorded choices

Nominations ready: {{custom_single_choice__nominations_ready}}

Effective authority: {{custom_single_choice__effective_authority}}

Co-agent action: {{custom_single_choice__coagent_action}}

Content authority: {{custom_single_choice__content_authority}}

## Interview prompts

- Identify the proposed agent and successor agents through Person records. Confirm each one's willingness, suitability
  and conflicts; a nomination is not an executed appointment.
- If authority is to spring on a future event, define the event, the evidence and who decides it has occurred. Discuss
  how authority will operate during incapacity.
- Review banking, investment, real estate, business, tax, retirement and digital-asset powers. Ask about paying hosting
  bills and renewing domains.
- Ask separately about gifts, permissible recipients, self-benefit, beneficiary changes and trust-related powers. Record
  explicit limits and any monitoring or accounting requirements.
- Ask about access to the content of electronic communications separately from other digital assets. Identify every
  account or category to be excluded or restricted.
- Coordinate each provider's online-tool directions with the proposed instrument. Confirm the current statutory form and
  Nevada execution requirements during drafting: the form requires the principal's signature to be acknowledged before a
  notary public; a principal who resides in a hospital, residential facility for groups, facility for skilled nursing or
  home for individual residential care needs a certification of competency attached; and a principal who resides or is
  about to reside in a hospital, assisted living facility or facility for skilled nursing generally may not name the
  facility, its owner or operator, or its employee as agent.

## Authority for drafting

NRS 162A.200 to 162A.660, especially NRS 162A.210 (durable unless it expressly provides otherwise), 162A.220
(execution), 162A.450 (acts that require an express grant: trusts, gifts, survivorship, beneficiary designations,
delegation, survivor-annuity waivers, delegable fiduciary powers and disclaimers) and 162A.620 (statutory form); and
Chapter 722 of NRS, especially NRS 722.310 and 722.360. Unless the power of attorney otherwise provides, an agent who is
not the principal's spouse may not use those powers to create an interest in the principal's property for the agent or
for anyone the agent must support. Consult the current authority before drafting the operative instrument.

## Recordkeeping and limits

The structured walk records the choices above. Counsel records the detailed interview answers and supporting documents
in the private Matter file; these prompts are not additional automated fields. Use the existing Person and other
glossary records for nominations and identity. Never collect passwords, seed phrases, recovery codes or private keys. A
completed questionnaire is not an executed legal instrument or a verified ownership record.
