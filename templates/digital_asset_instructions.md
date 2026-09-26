---
kind: memo
title: Digital-assets and access instructions
respondent_type: person
code: digital_asset_instructions
jurisdiction: NV
confidential: true
prompts:
  online_tools_review: Have existing provider online-tool directions been reviewed?
  death_content_direction: After death, should message content be disclosed to the personal representative?
  recovery_plan: Is there a recovery procedure the authorized fiduciary can use?
  succession_review: Have maintainers and account-disposition preferences been selected?
choices:
  online_tools_review:
    pending: Review is pending
    partial: Some providers reviewed
    complete: All identified providers reviewed
    not_on_file: Not yet on file
  death_content_direction:
    allow: Consent, subject to documented limits
    withhold: Withhold consent
    limited: Account-specific instructions require drafting
    not_on_file: Not yet on file
  recovery_plan:
    pending: Procedure still needs to be established
    untested: Procedure exists but has not been tested
    tested: Client reports a tested procedure; counsel must confirm scope
    not_on_file: Not yet on file
  succession_review:
    pending: Selections are pending
    partial: Some selections recorded
    complete: Selections recorded for each identified account or project
    not_on_file: Not yet on file
questionnaire:
  BEGIN:
    _: person__client
  person__client:
    _: project__engagement
  project__engagement:
    _: custom_single_choice__online_tools_review
  custom_single_choice__online_tools_review:
    _: custom_single_choice__death_content_direction
  custom_single_choice__death_content_direction:
    _: custom_single_choice__recovery_plan
  custom_single_choice__recovery_plan:
    _: custom_single_choice__succession_review
  custom_single_choice__succession_review:
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

# Digital-assets and access instructions

Client: {{person__client.name}}

Matter: {{project__engagement.name}}

This questionnaire records how each provider's online-tool directions stand before counsel drafts any will, trust or
power-of-attorney clause on digital assets. It does not change provider settings or confer access rights. Counsel
reviews each answer and records any unknown fact as Not yet on file.

## Recorded choices

Online tools review: {{custom_single_choice__online_tools_review}}

Death content direction: {{custom_single_choice__death_content_direction}}

Recovery plan: {{custom_single_choice__recovery_plan}}

Succession review: {{custom_single_choice__succession_review}}

## Interview prompts

- For each provider, identify the online tool, the current designated recipient and disclosure directions, the review
  date, and whether the user can modify or delete the directions at all times.
- Ask separately about access during life and disclosure after death. Record choices for the content of electronic
  communications, the catalogue of electronic communications and other digital assets, including exclusions, account by
  account.
- Identify domain registrar, renewal dates, payment dependencies, email, cloud storage, devices, backups and any
  self-hosted services. Do not infer assets from a public profile.
- Record preservation, archiving, memorialization, closure or permitted transfer preferences. Identify who decides and
  who performs the technical work.
- Ask about private repositories, joint authors, licenses, employer rights, package namespaces and successor
  maintainers. Separate access, copyright ownership and maintainer responsibilities.
- Record where the client keeps their password manager and recovery procedure and how an authorized fiduciary locates
  them. Never collect passwords, seed phrases, recovery codes or private keys, and do not enter any credential into this
  questionnaire or any document counsel holds.
- Identify single points of failure and urgent renewals. Keep the detailed schedule and instructions in the private
  Matter file.

## Authority for drafting

Chapter 722 of NRS, the Revised Uniform Fiduciary Access to Digital Assets Act of 2015. Under NRS 722.310, a direction
given through an online tool that the user can modify or delete at all times overrides a contrary direction in a will,
trust, power of attorney or other record. Where the user has given no such direction, or the custodian offers no online
tool, the user may allow or prohibit disclosure to a fiduciary in a will, trust, power of attorney or other record.
Under NRS 722.360, a custodian discloses the content of electronic communications to an agent only to the extent the
power of attorney expressly grants the agent that authority.

## Recordkeeping and limits

The structured walk records the choices above. Counsel records the detailed interview answers and supporting documents
in the private Matter file; these prompts are not additional automated fields. Use the existing Person and other
glossary records for nominations and identity. A completed questionnaire is not an executed legal instrument or a
verified ownership record.
