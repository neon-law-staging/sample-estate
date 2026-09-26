---
kind: directive
title: Nevada designation of person to order disposition of remains
respondent_type: person
code: disposition_of_remains
jurisdiction: NV
confidential: true
prompts:
  disposition_method: What disposition of the remains does the declarant direct?
  signing_county: In which Nevada county will the signature be acknowledged?
choices:
  disposition_method:
    burial: Burial
    religious_burial: Burial according to the rites of my faith, as my designee understands them
    cremation: Cremation
    designee_decides: Burial or cremation, as my designee decides in light of my known wishes
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
    _: person__remains_agent
  person__remains_agent:
    _: person__successor_remains_agent
  person__successor_remains_agent:
    _: custom_single_choice__disposition_method
  custom_single_choice__disposition_method:
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

# Affidavit Authorizing Another Person to Order the Burial or Cremation of My Remains

State of Nevada

ss.

County of {{custom_single_choice__signing_county}}

(Date) ____________________

I, {{person__client.name}}, of {{person__client.street}}, {{person__client.city}}, {{person__client.state}}
{{person__client.zip}}, do hereby designate {{person__remains_agent.name}}, of {{person__remains_agent.street}},
{{person__remains_agent.city}}, {{person__remains_agent.state}} {{person__remains_agent.zip}}, to order the disposition
of my human remains upon my death.

If {{person__remains_agent.name}} dies, declines to act, or is not reasonably available or is unable to act, I designate
{{person__successor_remains_agent.name}}, of {{person__successor_remains_agent.city}},
{{person__successor_remains_agent.state}}, to order the disposition of my human remains upon my death.

I revoke any prior designation of a person to order the burial or cremation of my human remains.

## Directions

Disposition: {{custom_single_choice__disposition_method}}.

My designee shall carry out these directions to the extent lawful and practicable, considering the financial resources
available for disposition. This affidavit does not certify that any arrangement has been purchased or funded.

Pre-need funeral contract and funeral establishment, if any: ________________________________

## Signature

Signature: ________________________________

{{person__client.name}}

Subscribed and sworn to before me this ______ day of the month of __________________ of the year ______.

Signature: ________________________________ (Notary Public)

## Acceptance by designee

I accept this designation and have no reason to believe it has been revoked.

Designee signature and date: ________________________________

## Attorney execution note

NRS 451.024(9) lets a person 18 or older authorize another to order the burial or cremation of the person's remains in a
validly executed will or durable power of attorney, or by an affidavit executed before a notary public in substantially
the statutory form. This affidavit follows that form; the successor designation and directions supplement it, so confirm
they do not take it out of "substantially" the statutory form. A designee under subsection 9 ranks first in the priority
NRS 451.024(1) sets. If the designee is not reasonably available or is unable to act, the statute passes the right to
the next person or category in that priority (NRS 451.024(10)), and the designee is presumed unavailable after 30 days
of unsuccessful contact or inaction (NRS 451.024(11)); confirm that the successor designated here takes ahead of the
spouse and other family. A crematory still needs its own signed written authorization, on the operator's form, before
cremation (NRS 451.660(1)); this affidavit does not supply it.

Authorities: NRS 451.024 and 451.660.
