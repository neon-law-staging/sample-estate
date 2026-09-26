---
kind: trust
title: Nevada assignment of identified property to trust
respondent_type: person
code: general_transfer_to_trust
jurisdiction: NV
confidential: true
prompts:
  trust_date: On what date was the trust instrument signed?
  trust_property: Describe with particularity each item of personal property being assigned.
  marital_status: What is the assignor's marital status?
  signing_county: In which Nevada county will the signatures be acknowledged?
choices:
  marital_status:
    unmarried: Unmarried
    married: Married
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
    _: person__spouse
  person__spouse:
    _: custom_text__trust_property
  custom_text__trust_property:
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

# Assignment of Identified Property to Trust

Attorney review draft — not for execution. A general wish to plan an estate is not a completed transfer. Schedule A must
describe each asset with particularity before release.

## I. Parties and trust

I, {{person__client.name}}, as assignor, assign to {{person__client.name}}, as trustee of the {{entity__trust.name}},
dated {{custom_datetime__trust_date}} (the "Trust"), only my transferable interest in the assets individually described
in Schedule A, subject to existing liens, restrictions and required consents.

The trustee accepts those assets to the extent lawfully transferred and shall administer them under the Trust. This is a
separate assignment instrument; the Trust's own recital of receipt or asset schedule does not establish that a transfer
occurred.

{{#if custom_single_choice__marital_status=married}}

To the extent an asset on Schedule A is community property, {{person__spouse.name}}, my spouse, joins in this
assignment. The asset retains its character as community property in the Trust. Neither this assignment nor the spouse's
joinder transmutes community property into separate property or separate property into community property.

{{/if}}

## II. Assets and transfer methods

No item is assigned by a blank row, an unsupported description or a general reference to all present and future
property.

For assets capable of registration, complete the required title or registration change and retain evidence of it. This
assignment does not substitute for recording a deed with the county recorder, retitling a bank or brokerage account,
transferring registered shares, retitling a vehicle through the Nevada Department of Motor Vehicles, or obtaining an
institution's required forms and consents. A transfer of Nevada real property requires a separately recorded deed and
declaration of value.

## III. Exclusions and limits

This instrument does not change a payable-on-death, transfer-on-death or deed-upon-death designation, transfer ownership
of a retirement plan or IRA, name a retirement beneficiary, or change a life-insurance policy. Those actions require
their own reviewed custodian or provider procedures. Existing beneficiary designations must be reconciled before
retitling; an assignment does not redirect them automatically.

This assignment transfers no employer property, restricted business interest, nontransferable contract right or licensed
intellectual property beyond the interest I actually own and may lawfully assign. Digital access authority and the
transfer of an underlying asset are distinct matters.

This assignment does not transfer later-acquired property. Add a later asset through an appropriate separate transfer or
a signed supplemental assignment identifying it with particularity.

## IV. Schedule A — assets actually assigned

{{custom_text__trust_property}}

## V. Signatures

Assignor signature: ________________________________

{{person__client.name}}

Date: ________________________________

Accepting trustee signature: ________________________________

{{person__client.name}}, trustee of the {{entity__trust.name}}

Date: ________________________________

{{#if custom_single_choice__marital_status=married}}

Consenting spouse signature: ________________________________

{{person__spouse.name}}

Date: ________________________________

{{/if}}

## VI. Certificate of acknowledgment

State of Nevada

County of {{custom_single_choice__signing_county}}

This instrument was acknowledged before me on ____________________ by {{person__client.name}}.

{{#if custom_single_choice__marital_status=married}}

This instrument was also acknowledged before me on ____________________ by {{person__spouse.name}}.

{{/if}}

Signature of notarial officer: ________________________________

(Seal, if any)

Authorities: NRS 163.002, 163.003 and 163.008; NRS 123.220 and 123.125; NRS 240.166.
