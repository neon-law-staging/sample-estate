---
kind: memo
title: Nevada estate-planning intake
respondent_type: person
code: estate_intake
jurisdiction: NV
confidential: true
prompts:
  existing_plan: Does the client have existing estate-planning documents?
  family_review: Has counsel reviewed the client's family circumstances and backup beneficiaries?
  planning_priorities: Which planning topic should counsel address first?
  plan_structure: Should the plan rest on a will alone, or on a revocable living trust with a pour-over will?
  trustee: Who will serve as initial trustee of the revocable living trust?
  health_directives: Which health-care documents should counsel prepare?
  execution_plan: How should the signing be arranged?
choices:
  existing_plan:
    'yes': Yes; counsel will obtain the signed originals or copies
    'no': No known existing documents
    not_on_file: Not yet on file
  family_review:
    complete: Reviewed; instructions are recorded in the private Matter file
    pending: Review still needed
    not_on_file: Not yet on file
  planning_priorities:
    financial: Financial decisions during the client's life
    succession: Who inherits, and who administers the estate and trust
    digital: Digital access and privacy
    health: Health-care decisions
    ownership: A dated ownership attestation
    not_on_file: Not yet on file
  plan_structure:
    will: A will alone; the estate is probated in district court
    trust: A revocable living trust with a pour-over will
    undecided: Still undecided
    not_on_file: Not yet on file
  trustee:
    client_sole: The client alone; no one else signs the trust
    client_and_co: The client with a co-trustee, who also signs the trust
    other: Someone other than the client, who also signs the trust
    not_on_file: Not yet on file
  health_directives:
    full: >-
      Power of attorney for health care, declaration governing life-sustaining treatment, medical-records authorization
      and remains affidavit
    proxy_only: The power of attorney for health care only
    excluded: None; health-care documents are outside this engagement
    not_on_file: Not yet on file
  execution_plan:
    two_sittings: Two sittings, the client first and any co-trustee or other signer after
    one_sitting: One sitting, with any other signer signing later
    pending: Not yet arranged
    not_on_file: Not yet on file
questionnaire:
  BEGIN:
    _: person__client
  person__client:
    _: project__engagement
  project__engagement:
    _: custom_single_choice__existing_plan
  custom_single_choice__existing_plan:
    _: custom_single_choice__family_review
  custom_single_choice__family_review:
    _: custom_single_choice__planning_priorities
  custom_single_choice__planning_priorities:
    _: custom_single_choice__plan_structure
  custom_single_choice__plan_structure:
    _: custom_single_choice__trustee
  custom_single_choice__trustee:
    _: custom_single_choice__health_directives
  custom_single_choice__health_directives:
    _: custom_single_choice__execution_plan
  custom_single_choice__execution_plan:
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

# Nevada estate-planning intake

Client: {{person__client.name}}

Matter: {{project__engagement.name}}

This questionnaire records the client's choices so counsel can decide which estate-planning documents to prepare. It
does not create a will, trust, or power of attorney, and it is not legal advice by itself. Counsel reviews every answer,
then either asks follow-up questions or begins drafting. Record any fact not yet known as "Not yet on file."

## Recorded choices

Existing plan: {{custom_single_choice__existing_plan}}

Family review: {{custom_single_choice__family_review}}

Planning priorities: {{custom_single_choice__planning_priorities}}

Plan structure: {{custom_single_choice__plan_structure}}

Trustee: {{custom_single_choice__trustee}}

Health-care instruments: {{custom_single_choice__health_directives}}

Execution plan: {{custom_single_choice__execution_plan}}

## Interview prompts

- Confirm the client's domicile, current residence, intended signing location, and any planned move. Record them in the
  Person, Address, and Jurisdiction records.
- Ask about marriage, domestic partnership, separation, divorce, marital or premarital agreements, children, dependents,
  and support obligations. Obtain any relevant agreement or order through the private Matter channel.
- Identify existing wills, trusts, financial powers of attorney, powers of attorney for health care, deeds upon death,
  beneficiary designations, and amendments. Confirm where each signed original is held.
- Ask who should receive specific gifts and the remainder, who takes if a beneficiary dies first, and whether any
  beneficiary needs protective planning, such as a supplemental-needs share.
- Ask the client to choose a personal representative (executor) and alternate, a financial agent and successor, and a
  health-care agent and alternate. If a role is undecided, record it as undecided; do not supply a nominee.
- Ask about guardian nominations for any minor child, who should order the disposition of remains, and whether a funded
  trust would serve a specific objective.
- Ask whether the dispositive terms should stay private. A will admitted to probate becomes a public court record; a
  revocable living trust does not. That, not any tax saving, is the choice behind the plan-structure question.
- Ask whether each asset is community or separate property. Nevada is a community-property state. Transferring an asset
  into the trust does not change its character; a change of character needs a separate writing signed by both spouses.
- Ask what the estate is worth in round terms. Nevada imposes no estate or inheritance tax, but the federal estate tax
  and the limits for summary administration and set-aside proceedings still turn on value.
- Confirm who signs, when, and in whose presence. The revocable living trust is signed at or before the will and
  acknowledged before a notary. The will needs two competent witnesses who take nothing under it; their self-proving
  affidavit is sworn before a notary. The financial power of attorney and the remains affidavit need a notary. The power
  of attorney for health care needs a notary or two adult witnesses, and a declaration needs two witnesses.
- Before selecting final documents, confirm that the engagement letter is signed, and confirm the scope, the immediate
  priorities, and who is responsible for each follow-up item.

## Recordkeeping and limits

The structured questions record only the choices above. Counsel records the detailed interview answers and supporting
documents in the private Matter file; the interview prompts are not additional automated fields. Use the existing Person
and other glossary records for nominations and identity. A completed questionnaire is not an executed legal instrument
or a verified ownership record.
