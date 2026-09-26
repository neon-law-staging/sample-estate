---
kind: trust
title: Nevada revocable living trust
respondent_type: person
code: revocable_living_trust
jurisdiction: NV
confidential: true
prompts:
  trust_date: On what date will the trust instrument be signed?
  marital_status: What is the settlor's marital status?
  specific_gift: Does the trust make a specific gift of real property?
  specific_gift_debt: How should secured debt on the specific-gift property be borne?
  supplemental_needs_share: Should one residuary share pass to a third-party supplemental needs trust?
  lapse: If a residuary beneficiary does not survive the settlor, where does that share go?
  signing_county: In which Nevada county will the settlor's signature be acknowledged?
choices:
  marital_status:
    unmarried: Unmarried
    married: Married
  specific_gift_debt:
    subject_to: The recipient takes subject to the debt, without exoneration
    exonerated: The trustee pays the debt from the remaining trust property
  lapse:
    descendants: To that beneficiary's descendants who survive, by right of representation
    others: To the other residuary shares, in proportion to their sizes
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
    _: custom_single_choice__marital_status
  custom_single_choice__marital_status:
    _: person__successor_trustee
  person__successor_trustee:
    _: person__second_successor_trustee
  person__second_successor_trustee:
    _: custom_yes_no__specific_gift
  custom_yes_no__specific_gift:
    _: address__specific_gift
  address__specific_gift:
    _: person__specific_gift_beneficiary
  person__specific_gift_beneficiary:
    _: custom_single_choice__specific_gift_debt
  custom_single_choice__specific_gift_debt:
    _: people__residuary_beneficiaries
  people__residuary_beneficiaries:
    _: custom_yes_no__supplemental_needs_share
  custom_yes_no__supplemental_needs_share:
    _: entity__supplemental_needs_trust
  entity__supplemental_needs_trust:
    _: person__supplemental_needs_beneficiary
  person__supplemental_needs_beneficiary:
    _: custom_single_choice__lapse
  custom_single_choice__lapse:
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

# Revocable Living Trust of {{person__client.name}}

## I. Establishment and identification

I, {{person__client.name}}, of {{person__client.city}}, {{person__client.state}}, establish the {{entity__trust.name}},
dated {{custom_datetime__trust_date}} (the "Trust"). I am the settlor, the lifetime beneficiary and the initial trustee.

{{#if custom_single_choice__marital_status=married}}

I am married. Community property that my spouse and I transfer to the Trust retains its character as community property
while the Trust is revocable, and separate property retains its character as separate property. The trustee shall keep
records sufficient to trace the character of each asset. This instrument does not transmute property from one character
to another; a transmutation requires a separate writing signed by both spouses.

{{/if}}

The trustee accepts property actually transferred to the Trust and shall hold and administer it under this instrument. A
recital or Schedule A entry alone does not transfer title. The trustee shall maintain evidence of each completed
transfer separately from the list of assets considered for funding.

## II. Revocation and amendment

While I have capacity, I reserve the right to amend or revoke this Trust, in whole or in part, and to withdraw its
property. I may do so only by a writing, other than a will, that I sign, that identifies this Trust, and that I deliver
to the trustee, or to each other acting trustee if I am not the sole trustee. That method is exclusive. No agent is
given a power to amend or revoke this Trust merely by being my financial agent.

An amendment must identify the provisions changed. On revocation, the trustee shall return the remaining property to me
after providing for lawful administration expenses and obligations. The Trust becomes irrevocable at my death.

## III. Administration during my lifetime

While I have capacity, the trustee shall distribute income and principal to me or as I direct in writing. During my
incapacity, the trustee shall use income and principal for my care, support and benefit, taking account of my needs and
other reasonably known resources. My interests take priority over preservation of a remainder gift. This paragraph does
not authorize gifts to the trustee or changes to my beneficiaries.

I am incapacitated for this purpose when a licensed physician who has personally examined me certifies in writing that I
am unable to manage my property and financial affairs, or when a court so finds. I regain capacity on a like
certification or finding.

## IV. Trustee succession

If I die, resign or become incapacitated, I appoint {{person__successor_trustee.name}} as successor trustee. If that
person is unable or unwilling to serve or to continue to serve, I appoint {{person__second_successor_trustee.name}}.
Neither has any right or power as trustee until that person's appointment takes effect under this Article, and neither
signs this instrument.

A successor accepts by signed writing and receives the property and records of the Trust. Resignation, removal and
filling any unprovided vacancy remain subject to Nevada law. No provision of this instrument permits a trustee who is
also a beneficiary to change beneficial shares or to confer an additional benefit on that trustee.

## V. Administration after death

The trustee shall identify the property actually held by the Trust, coordinate with the duly appointed personal
representative of my estate, and provide for lawful obligations, expenses and taxes before final distribution. The
trustee shall not assume that an account payable directly to a named beneficiary is available to discharge estate or
Trust debts.

## VI. Distributions after death

{{#if custom_yes_no__specific_gift}}

### Specific gift of real property

I give my entire interest held by this Trust in the real property at {{address__specific_gift.street}},
{{address__specific_gift.city}}, {{address__specific_gift.state}} {{address__specific_gift.zip}}, to
{{person__specific_gift_beneficiary.name}}. This is a separate specific gift; it is not included in the division of the
remaining property below.

Treatment of secured debt: {{custom_single_choice__specific_gift_debt}}.

If a consent required to transfer the property is withheld, the trustee may sell the interest and distribute the net
proceeds to {{person__specific_gift_beneficiary.name}} in its place, or take any other step the governing documents
allow to carry out this gift. The proceeds bear secured debt to the same extent the property would have.

{{/if}}

### Remaining Trust property

After any specific gift and the properly allocated obligations of the Trust, the trustee shall divide the remaining
Trust property into equal shares, one for each of the following residuary beneficiaries who survives me:

{{#for b in people__residuary_beneficiaries}}

- {{b.name}}

{{/for}}

{{#if custom_yes_no__supplemental_needs_share}}

One additional equal share passes to the trustee of {{entity__supplemental_needs_trust.name}}, to be added to that trust
and administered under its terms for the benefit of {{person__supplemental_needs_beneficiary.name}}. No part of that
share is to be paid to {{person__supplemental_needs_beneficiary.name}} outright, and it is not to be counted as a
resource of that beneficiary for any means-tested public benefit.

{{/if}}

This Article applies only to property administered under the Trust. It does not change a beneficiary designation on file
with a custodian or assert that an account subject to one has been transferred to the Trust.

### Survival and substitute takers

A beneficiary who does not survive me by 120 hours is treated as having predeceased me. If a residuary beneficiary
predeceases me, that beneficiary's share passes as follows: {{custom_single_choice__lapse}}. Any property not otherwise
disposed of passes to my heirs determined under Nevada law as though I had died intestate.

## VII. Trustee powers and duties

The trustee may collect and safeguard property, invest and reinvest under the prudent investor rule, sell or lease
property, pay lawful expenses, insure assets, compromise claims, employ professional assistance and distribute in cash
or in kind, together with the powers listed in NRS 163.265 to 163.410, which NRS 163.260 incorporates into this
instrument. Those powers are fiduciary powers, subject to duties of loyalty, prudence and impartiality and to applicable
restrictions on the assets involved.

The trustee shall keep adequate records and provide information and accountings required by law. This instrument does
not waive mandatory accountability or excuse breach of trust. A trustee's interest as a beneficiary does not authorize
unrestricted self-dealing, distributions to satisfy the trustee's own obligations, or unilateral amendment of beneficial
interests. A trustee other than me is entitled to reasonable compensation and to reimbursement of proper expenses.

## VIII. Digital assets

The trustee may administer digital assets in which the Trust has a right or interest, subject to Chapter 722 of NRS,
applicable federal law and enforceable terms of service. Authority to administer a digital asset does not itself change
title to an underlying asset, convey employer property, or displace an existing intellectual-property license.

A direction given through a custodian's online tool takes priority over a contrary direction here, as NRS 722.310
provides.

## IX. Certification, spendthrift protection and governing law

An acting trustee may furnish a certification of trust under NRS 164.400 to 164.440 in place of a copy of this
instrument. A certification does not enlarge the trustee's powers or establish funding.

After my death, no beneficiary may voluntarily or involuntarily transfer an interest in the income or principal of the
Trust before its actual receipt, to the extent Chapter 166 of NRS permits.

Nevada law governs the validity, construction and administration of this Trust.

## X. Execution

Settlor and trustee signature: ________________________________

{{person__client.name}}, as settlor and as initial trustee

Date: ________________________________

## Certificate of acknowledgment

State of Nevada

County of {{custom_single_choice__signing_county}}

This instrument was acknowledged before me on ____________________ by {{person__client.name}}.

Signature of notarial officer: ________________________________

(Seal, if any)

## Schedule A — funding record

No completed transfer is certified by this draft. Keep the private funding record asset-specific, stating the
description, legal owner, character as community or separate property, recipient trustee and exact trust name and date,
required transfer steps, evidence of completion and completion date. Record proposed transfers separately from completed
transfers. Do not list a nominal cash contribution as delivered unless it actually was delivered.

## Attorney review note

Chapter 135 of NRS sets no 120-hour survival period, and under NRS 135.080 it does not apply where a living trust
provides otherwise, so the 120-hour clause in Article VI governs. Chapter 163 of NRS does not say whether a revocation
method the trust specifies is exclusive, so confirm current case law before relying on Article II. Divorce revokes gifts
to and trustee appointments of a former spouse under NRS 163.565. Never let the client give passwords, recovery codes,
secret keys or seed phrases to the Firm or put them in this instrument.

Authorities:

- NRS 163.002, 163.003, 163.004 and 163.008 (creation and revocability)
- NRS 163.260 to 163.410 (trustee powers) and 163.565 (effect of divorce)
- NRS 164.400 to 164.440 (certification of trust) and 164.745 (prudent investor)
- NRS 165.1207 (accounts while revocable)
- NRS 123.220 (community property) and 135.080 (survival clauses)
- NRS 722.310 (online tools) and 240.166 (acknowledgment)
- Chapter 166 of NRS (spendthrift trusts)
