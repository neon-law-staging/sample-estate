---
kind: memo
title: Asset and liability ownership intake
respondent_type: person
code: asset_ownership_intake
jurisdiction: NV
confidential: true
prompts:
  inventory_progress: How complete is the private asset and liability schedule?
  ownership_evidence: What is the status of the ownership evidence?
  beneficiary_review: Have current titles and beneficiary designations been compared with the intended plan?
choices:
  inventory_progress:
    not_started: Not started
    partial: Partially collected
    ready: Collected for counsel review
    not_on_file: Not yet on file
  ownership_evidence:
    requested: Evidence requested
    partial: Some evidence received
    received: Evidence received for review
    not_on_file: Not yet on file
  beneficiary_review:
    pending: Comparison is pending
    conflicts: Differences require instructions
    reviewed: Comparison recorded privately
    not_on_file: Not yet on file
questionnaire:
  BEGIN:
    _: person__client
  person__client:
    _: project__engagement
  project__engagement:
    _: custom_single_choice__inventory_progress
  custom_single_choice__inventory_progress:
    _: custom_single_choice__ownership_evidence
  custom_single_choice__ownership_evidence:
    _: custom_single_choice__beneficiary_review
  custom_single_choice__beneficiary_review:
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

# Asset and liability ownership intake

Client: {{person__client.name}}

Matter: {{project__engagement.name}}

This questionnaire tracks collection of a complete asset and liability inventory without presuming the client owns any
category. The recorded choices describe progress, not verified ownership. Counsel reviews each answer and records any
unknown fact as Not yet on file.

## Recorded choices

Inventory progress: {{custom_single_choice__inventory_progress}}

Ownership evidence: {{custom_single_choice__ownership_evidence}}

Beneficiary review: {{custom_single_choice__beneficiary_review}}

## Interview prompts

- Ask what bank, brokerage, retirement, pension, insurance and annuity interests the client owns. Obtain the actual
  primary and contingent beneficiary designations.
- Ask about real estate, deeds upon death, vehicles, valuable personal property, businesses, equity, options, RSUs,
  receivables and intellectual property.
- Ask whether cryptocurrency, tokens, NFTs or other blockchain interests exist, including exchange-held, self-custodied,
  staked, locked, lent or pledged interests.
- For each item, record in the private schedule whether it is community or separate property, the legal owner and the
  capacity in which title is held, the ownership share, co-owners, custodian, location, approximate value and valuation
  date.
- Record mortgages, loans, guarantees, liens, transfer restrictions, vesting, exercise deadlines and governing
  agreements. Distinguish an employer or entity asset from personal property.
- Link the dated deed, account statement, ledger, agreement or other supporting document through Navigator. Mark a
  client report separately from counsel-reviewed evidence.
- Record the intended recipient and treatment, the current beneficiaries, the required transfer method and the person
  responsible for implementation.
- Keep account identifiers and evidence in the private Matter file. Never collect passwords, seed phrases, recovery
  codes or private keys.

## Recordkeeping and limits

The structured walk records the choices above. Counsel records the detailed interview answers and supporting documents
in the private Matter file; these prompts are not additional automated fields. Use the existing Person and other
glossary records for nominations and identity. A completed questionnaire is not an executed legal instrument or a
verified ownership record.
