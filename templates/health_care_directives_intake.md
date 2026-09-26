---
kind: memo
title: Nevada health-care directives intake
respondent_type: person
code: health_care_directives_intake
jurisdiction: NV
confidential: true
prompts:
  agent_nominations: Have the health-care agent and alternate been selected?
  nutrition_wishes: Are the client's wishes about artificial nutrition and hydration settled?
  living_will: Should counsel draft a separate declaration governing life-sustaining treatment under NRS 449A.400 to
    449A.481, inclusive?
  records_access: Who should be authorized to receive the client's protected health information?
  remains_agent: Has a designee to order the burial or cremation of the client's remains been selected?
  donation_direction: What direction should the documents carry on organ, eye and tissue donation?
choices:
  agent_nominations:
    'yes': Agent and alternate selected and recorded privately; confirm each is willing and eligible to serve
    'no': Agent or alternate still to be selected
    not_on_file: Not yet on file
  nutrition_wishes:
    stated: Settled; counsel will state them in writing in the instruments
    spoken: Discussed orally with the agent only; no written statement yet
    pending: Still to be settled
    not_on_file: Not yet on file
  living_will:
    draft: Draft a separate declaration, on the NRS 449A.436 or 449A.439 form
    proxy_only: No separate declaration; state the instructions in the power of attorney for health care only
    undecided: Still open
    not_on_file: Not yet on file
  records_access:
    agent_only: The health-care agent and alternate only, through the power of attorney for health care
    wider: The agents and others the client will name privately, in a separate HIPAA authorization
    pending: Still to be decided
    not_on_file: Not yet on file
  remains_agent:
    'yes': Designee selected and recorded privately; the designee signs the acceptance on the affidavit
    'no': Designee still to be selected
    not_on_file: Not yet on file
  donation_direction:
    consent: Donate, subject to documented limits; confirm a registry, license or other gift record, because the power
      of attorney for health care makes no new gift
    withhold: Do not donate; the power of attorney for health care bars the agent from making a gift
    agent: Leave the decision to the health-care agent
    not_on_file: Not yet on file
questionnaire:
  BEGIN:
    _: person__client
  person__client:
    _: project__engagement
  project__engagement:
    _: custom_single_choice__agent_nominations
  custom_single_choice__agent_nominations:
    _: custom_single_choice__nutrition_wishes
  custom_single_choice__nutrition_wishes:
    _: custom_single_choice__living_will
  custom_single_choice__living_will:
    _: custom_single_choice__records_access
  custom_single_choice__records_access:
    _: custom_single_choice__remains_agent
  custom_single_choice__remains_agent:
    _: custom_single_choice__donation_direction
  custom_single_choice__donation_direction:
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

# Nevada health-care directives intake

Client: {{person__client.name}}

Matter: {{project__engagement.name}}

This intake gathers the client's instructions for the health-care side of the estate plan so counsel can draft the
instruments. It appoints nobody and grants no authority. Record any fact not yet known as "Not yet on file."

## Recorded choices

Agent nominations: {{custom_single_choice__agent_nominations}}

Nutrition wishes: {{custom_single_choice__nutrition_wishes}}

Living will: {{custom_single_choice__living_will}}

Records access: {{custom_single_choice__records_access}}

Remains agent: {{custom_single_choice__remains_agent}}

Donation direction: {{custom_single_choice__donation_direction}}

## Purpose

In Nevada, the power of attorney for health care, the declaration governing life-sustaining treatment, a records
authorization and the affidavit designating who orders the burial or cremation of remains are separate instruments. Each
choice above feeds one of them; confirm the instruments agree with one another before release.

## Interview prompts

- Identify the proposed agent and alternate through Person records. Confirm willingness and suitability. The agent may
  not be the client's provider of health care, that provider's employee, or the operator or an employee of a health-care
  facility, unless the agent is the client's spouse, legal guardian or next of kin.
- Record the client's wishes about artificial nutrition and hydration in the client's own words. For a qualified
  patient, tube feeding is treated as life-sustaining treatment and is withheld or withdrawn unless the patient
  expressed a different desire in writing, so walk through the initial box on the statutory declaration form.
- Ask which treatments the client would want limited or refused and under which conditions, and whether the client wants
  a declaration that directs the attending physician or advanced practice registered nurse, or one that designates a
  decision-maker.
- Ask who may receive medical records, separately from who may decide. Decision authority and records access are
  different grants.
- Identify who should order the burial or cremation of the client's remains and any successor, and ask about a pre-need
  funeral contract. A standalone designation is an affidavit executed before a notary public; it may instead go in a
  validly executed will or durable power of attorney.
- Record organ, eye and tissue donation wishes once, then confirm every instrument agrees. Silence is not a refusal
  of donation and must not be drafted as one. Unless the power of attorney for health care prohibits it, the agent may
  make an anatomical gift.
- Confirm how the power of attorney for health care will be executed: before a notary public, or before two adult
  witnesses. If the client lives in a nursing home, no witness may be its owner, operator or employee.
- Confirm the declaration will be attested by two witnesses. Suggest registering the executed instruments with the
  Nevada Lockbox.

## Authority for drafting

NRS 162A.700 to 162A.870, inclusive, especially 162A.790 (execution), 162A.840 (who may not be agent), 162A.850 (acts an
agent may not consent to) and 162A.855 (advance health-care directive form); NRS 449A.400 to 449A.481, inclusive,
especially 449A.433, 449A.436, 449A.439 and 449A.451; NRS 451.024 (burial or cremation of remains); NRS 451.556 (gift by
an agent); 45 C.F.R. 164.502(g) (personal representatives) and 164.508 (authorizations). Consult the current authority
before drafting the operative instruments.

## Relationship to the digital-asset instruments

A health-care agent reaches no digital asset under this appointment. Under chapter 722 of NRS, a power of attorney may
allow or prohibit an agent's access to the principal's digital assets (NRS 722.310), and the content of electronic
communications is disclosed only under an express grant (NRS 722.360). Keep that grant in the financial power of
attorney and do not draft the health-care power of attorney as though it reached an account.

## Recordkeeping and limits

The structured walk records the choices above. Counsel records the detailed interview answers and supporting documents
in the private Matter file; these prompts are not additional automated fields. Use the existing Person and other
glossary records for nominations and identity. A completed questionnaire is not an executed legal instrument or a
verified ownership record.
