---
kind: trust
title: Nevada certification of trust
respondent_type: person
code: certification_of_trust
jurisdiction: NV
confidential: true
prompts:
  trust_date: On what date was the trust instrument signed?
  trustee_signatures: How many trustees must sign to exercise the power in question?
  proposed_transaction: What transaction is this certification being used for?
  signing_county: In which Nevada county will the trustee's signature be acknowledged?
choices:
  trustee_signatures:
    sole: The sole acting trustee alone
    any_one: Any one acting trustee
    all: All acting trustees together
  proposed_transaction:
    bank_account: Opening or retitling a bank or brokerage account
    real_property: Conveying, encumbering or taking title to real property
    digital_asset: Requesting disclosure of a digital asset from a custodian
    other: Another transaction counsel will describe
  signing_county:
    carson_city: Carson City
    churchill: Churchill
    clark: Clark
    douglas: Douglas
    elko: Elko
    esmeralda: Esmeralda
    eureka: Eureka
    humboldt: Humboldt
    lander: Lander
    lincoln: Lincoln
    lyon: Lyon
    mineral: Mineral
    nye: Nye
    pershing: Pershing
    storey: Storey
    washoe: Washoe
    white_pine: White Pine
questionnaire:
  BEGIN:
    _: person__client
  person__client:
    _: entity__trust
  entity__trust:
    _: custom_datetime__trust_date
  custom_datetime__trust_date:
    _: person__successor_trustee
  person__successor_trustee:
    _: custom_single_choice__trustee_signatures
  custom_single_choice__trustee_signatures:
    _: custom_single_choice__proposed_transaction
  custom_single_choice__proposed_transaction:
    _: custom_single_choice__signing_county
  custom_single_choice__signing_county:
    _: END
  END: {}
workflow:
  BEGIN:
    intake_submitted: lawyer_review
  lawyer_review:
    reviewed: generate_pdf
  generate_pdf:
    generated: END
  END: {}
---

# Certification of Trust (Affidavit)

Attorney review draft — not for execution or institutional delivery. Complete the factual certifications from the
executed trust and existing file, not from an unsigned draft.

## I. Trust identity

I, {{person__client.name}}, being first duly sworn, depose and certify in my capacity as trustee that the
{{entity__trust.name}}, dated {{custom_datetime__trust_date}} (the "Trust"), exists and was established by
{{person__client.name}} as settlor under a written instrument governed by Nevada law.

Amendments affecting this certification: None.

## II. Current status and authority

The Trust is presently in existence. I am the currently acting trustee under Article I of the Trust. On my death,
resignation or incapacity, {{person__successor_trustee.name}} succeeds as trustee under Article IV.

Signature authority: {{custom_single_choice__trustee_signatures}} may exercise the powers relevant to the transaction.

The Trust is revocable. The person holding the power to revoke is {{person__client.name}}, as settlor, while the settlor
has capacity, by the signed and delivered writing Article II of the Trust requires.

## III. Transaction and relevant powers

Transaction: {{custom_single_choice__proposed_transaction}}.

Relevant powers and restrictions: ________________________________

Title to trust assets is to be taken as: {{person__client.name}}, trustee of the {{entity__trust.name}}, dated
{{custom_datetime__trust_date}}. This certification does not convey property, change a beneficiary designation or
establish that a listed asset is already held by the Trust.

Provide any taxpayer identification number separately through the receiving institution's secure process; do not place a
Social Security number in this document.

## IV. Reliance and limits

This certification is presented in place of a copy of the trust instrument. It need not contain the dispositive
provisions of the Trust, but the person to whom it is presented may require copies of excerpts from the trust instrument
that designate the trustee or confer on the trustee the power to act in the pending transaction. A person who acts in
reliance on this certification without knowledge that its representations are incorrect is not liable to any person for
so acting.

If this certification is used for a digital-asset request under Chapter 722 of NRS, furnish the separate written request
and any account-linking evidence the custodian requires.

## V. Certification and signature

The Trust has not been revoked or amended to make any representations contained in this certification incorrect, and the
signature below is that of all the currently acting trustees.

Trustee signature: ________________________________

{{person__client.name}}, trustee

Date: ________________________________

## Jurat and certificate of acknowledgment

Subscribed and sworn to before me on ____________________ by {{person__client.name}}.

State of Nevada

County of {{custom_single_choice__signing_county}}

This instrument was acknowledged before me on ____________________ by {{person__client.name}} as trustee of the
{{entity__trust.name}}.

Signature of notarial officer: ________________________________

(Seal, if any)

Authorities: NRS 164.400, 164.410, 164.420, 164.430 and 164.440; Chapter 722 of NRS; NRS 240.1665.
