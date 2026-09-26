---
kind: directive
title: Nevada declaration governing life-sustaining treatment
respondent_type: person
code: end_of_life_declaration
jurisdiction: NV
confidential: true
prompts:
  declaration_form: Which statutory declaration should the instrument use?
choices:
  declaration_form:
    direct: Direct my attending physician or advanced practice registered nurse (NRS 449A.436)
    designee: Designate a person to decide whether to withhold or withdraw treatment (NRS 449A.439)
questionnaire:
  BEGIN:
    _: person__client
  person__client:
    _: custom_single_choice__declaration_form
  custom_single_choice__declaration_form:
    _: person__treatment_designee
  person__treatment_designee:
    _: person__alternate_treatment_designee
  person__alternate_treatment_designee:
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

# Declaration

Attorney review draft — not for execution. This declaration follows the statutory form in NRS 449A.436 or 449A.439, as
selected, under the Uniform Act on Rights of the Terminally Ill. The declarant initials the artificial nutrition and
hydration box personally at signing; it is never preselected.

{{#if custom_single_choice__declaration_form=direct}}

If I should have an incurable and irreversible condition that, without the administration of life-sustaining treatment,
will, in the opinion of my attending physician or attending advanced practice registered nurse, cause my death within a
relatively short time, and I am no longer able to make decisions regarding my medical treatment, I direct my attending
physician or attending advanced practice registered nurse, pursuant to NRS 449A.400 to 449A.481, inclusive, to withhold
or withdraw treatment that only prolongs the process of dying and is not necessary for my comfort or to alleviate pain.

{{/if}}

{{#if custom_single_choice__declaration_form=designee}}

If I should have an incurable and irreversible condition that, without the administration of life-sustaining treatment,
will, in the opinion of my attending physician or attending advanced practice registered nurse, cause my death within a
relatively short time, and I am no longer able to make decisions regarding my medical treatment, I appoint
{{person__treatment_designee.name}} or, if he or she is not reasonably available or is unwilling to serve,
{{person__alternate_treatment_designee.name}}, to make decisions on my behalf regarding withholding or withdrawal of
treatment that only prolongs the process of dying and is not necessary for my comfort or to alleviate pain, pursuant to
NRS 449A.400 to 449A.481, inclusive.

(If the person or persons I have so appointed are not reasonably available or are unwilling to serve, I direct my
attending physician or attending advanced practice registered nurse, pursuant to those sections, to withhold or withdraw
treatment that only prolongs the process of dying and is not necessary for my comfort or to alleviate pain.) Strike
language in parentheses if you do not desire it.

{{/if}}

If you wish to include this statement in this declaration, you must INITIAL the statement in the box provided:

Withholding or withdrawal of artificial nutrition and hydration may result in death by starvation or dehydration.
Initial this box if you want to receive or continue receiving artificial nutrition and hydration by way of the
gastrointestinal tract after all other treatment is withheld pursuant to this declaration.

[............................................]

Signed this ______ day of __________________, ______.

Signature: ________________________________

{{person__client.name}}

Address: {{person__client.street}}, {{person__client.city}}, {{person__client.state}} {{person__client.zip}}

The declarant voluntarily signed this writing in my presence.

Witness: ________________________________

Address: ________________________________

Witness: ________________________________

Address: ________________________________

{{#if custom_single_choice__declaration_form=designee}}

Name and address of each designee.

Name: {{person__treatment_designee.name}}

Address: {{person__treatment_designee.street}}, {{person__treatment_designee.city}},
{{person__treatment_designee.state}} {{person__treatment_designee.zip}}

Name: {{person__alternate_treatment_designee.name}}

Address: {{person__alternate_treatment_designee.street}}, {{person__alternate_treatment_designee.city}},
{{person__alternate_treatment_designee.state}} {{person__alternate_treatment_designee.zip}}

{{/if}}

## Attorney review note

The declarant must be of sound mind and 18 or older, and so must any designee, who must be a natural person. The
declaration must be signed by the declarant, or another at the declarant's direction, and attested by two witnesses (NRS
449A.433(1)). Walk the client through the artificial nutrition and hydration box: for a qualified patient, tube feeding
is treated as life-sustaining treatment and is withheld or withdrawn unless the patient expressed a different desire in
writing (NRS 449A.451(3)). The declarant may revoke at any time and in any manner, without regard to mental or physical
condition (NRS 449A.445). This declaration is not a Provider Order for Life-Sustaining Treatment. A power of attorney
for health care executed under NRS 162A.790 that addresses life-sustaining treatment is itself a declaration (NRS
449A.433(3)), and an agent so authorized counts as a designee (NRS 449A.439(2)), so review this declaration with the
power of attorney for health care and make the two instruments agree. Suggest the client register it with the Nevada
Lockbox.

Authorities: NRS 449A.400 to 449A.481, inclusive, especially 449A.433, 449A.436, 449A.439, 449A.445 and 449A.451; NRS
162A.790.
