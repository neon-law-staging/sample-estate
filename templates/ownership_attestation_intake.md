---
kind: memo
title: Dated ownership-attestation intake
respondent_type: person
code: ownership_attestation_intake
jurisdiction: NV
confidential: true
prompts:
  attestation_scope: Is the proposed scope a statement of ownership at a specified time?
  evidence_readiness: Is dated ownership evidence available for every selected interest?
  public_key_readiness: Can the client provide a public key and sign on their own device?
  public_record_direction: Has the proposed public commitment and its privacy implications been discussed?
  signer_configuration: What signer configuration should counsel evaluate?
choices:
  attestation_scope:
    dated: Dated ownership statement only
    clarify: Scope requires further discussion
    not_on_file: Not yet on file
  evidence_readiness:
    pending: Evidence is pending
    partial: Some evidence is available
    ready: Evidence is available for lawyer review
    not_on_file: Not yet on file
  public_key_readiness:
    ready: Client reports readiness; proof of control remains required
    help: Client needs setup guidance
    not_on_file: Not yet on file
  public_record_direction:
    pending: Discussion and client instructions are pending
    private: Client wants the record kept private
    consider: Client is considering a public commitment; consent is not yet established
    not_on_file: Not yet on file
  signer_configuration:
    two: Client and lawyer
    third: A third signer is proposed; identify their role privately
    not_on_file: Not yet on file
questionnaire:
  BEGIN:
    _: person__client
  person__client:
    _: project__engagement
  project__engagement:
    _: custom_single_choice__attestation_scope
  custom_single_choice__attestation_scope:
    _: custom_single_choice__evidence_readiness
  custom_single_choice__evidence_readiness:
    _: custom_single_choice__public_key_readiness
  custom_single_choice__public_key_readiness:
    _: custom_single_choice__public_record_direction
  custom_single_choice__public_record_direction:
    _: custom_single_choice__signer_configuration
  custom_single_choice__signer_configuration:
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

# Dated ownership-attestation intake

Client: {{person__client.name}}

Matter: {{project__engagement.name}}

This questionnaire collects instructions for a separate client statement of ownership and a lawyer attestation. It does
not attest ownership, transfer property, establish wallet control or submit a blockchain transaction. Counsel reviews
each answer and records any unknown fact as Not yet on file.

## Recorded choices

Attestation scope: {{custom_single_choice__attestation_scope}}

Evidence readiness: {{custom_single_choice__evidence_readiness}}

Public key readiness: {{custom_single_choice__public_key_readiness}}

Public record direction: {{custom_single_choice__public_record_direction}}

Signer configuration: {{custom_single_choice__signer_configuration}}

## Interview prompts

- Identify each selected asset and the exact ownership interest in a private schedule. State the ownership as-of date,
  time and time zone separately from the signature and chain-recording times.
- Link dated supporting records and identify gaps, co-ownership, liens, restrictions and possible intervening transfers.
  Historical evidence does not establish unchanged ownership at signing.
- Identify the client and reviewing lawyer through Person records. The lawyer statement defines the evidence reviewed,
  the conclusion that evidence supports and every qualification.
- The client and lawyer must each sign the same final package revision. A changed schedule, statement or as-of time
  requires fresh signatures.
- Accept only a public key or public address, and only through a supported future verification flow. The client signs on
  their own wallet or device. Never collect passwords, seed phrases, recovery codes or private keys, including a
  secret-key export.
- Verify possession with an expiring, single-use signed challenge tied to the authenticated client. A public-key upload
  alone proves neither identity nor possession.
- If a third signer is requested, identify the person, evidentiary role and whether their signature is required. Do not
  invent a witness or treat the lawyer as an asset custodian.
- Obtain specific client instructions before publishing any commitment. Keep descriptions, evidence, account identifiers
  and Matter information private; discuss wallet and timing linkability.
- Define correction, supersession, lost-key handling and record retention. Start technical testing with fictional assets
  and test keys.

## Implementation dependency

Navigator has no shipped Solana attestor or verified public-key intake flow for this purpose. This workflow stops at
lawyer review and has no signature or chain step. Any future implementation must use Navigator's supported command and
workflow boundary, verify both signatures and confirm finalized chain read-back before claiming a recorded attestation.

## Recordkeeping and limits

The structured walk records the choices above. Counsel records the detailed interview answers and supporting documents
in the private Matter file; these prompts are not additional automated fields. Use the existing Person and other
glossary records for nominations and identity. A completed questionnaire is not an executed legal instrument or a
verified ownership record.
