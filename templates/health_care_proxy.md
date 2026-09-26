---
kind: directive
title: Nevada durable power of attorney for health care
respondent_type: person
code: health_care_proxy
jurisdiction: NV
confidential: true
prompts:
  life_sustaining_wishes: Which statement best describes the principal's wishes about life-sustaining treatment?
  nutrition_hydration: What instruction applies to artificial nutrition and hydration?
  anatomical_gift: What direction should the instrument carry on anatomical gifts of the principal's body or parts?
  execution_method: How will the principal's signature be validated?
  signing_county: In which Nevada county will the signature be acknowledged, if a notary is used?
choices:
  life_sustaining_wishes:
    agent_decides: I leave decisions about life-sustaining treatment to my agent, who shall apply my known desires and,
      where my desires are unknown, my best interests
    prolong: I want my life to be prolonged as long as possible within the limits of generally accepted health-care
      standards
    not_prolong: I do not want my life to be prolonged if the burdens of the treatment would outweigh the
      expected benefits
  nutrition_hydration:
    agent_decides: My agent shall decide whether I receive artificial nutrition and hydration under the same standard
      that governs other life-sustaining treatment
    continue: I want to receive artificial nutrition and hydration unless it would itself cause me suffering
    withhold_terminal: I do not want artificial nutrition and hydration if I have an incurable and irreversible
      condition and my death is imminent
  anatomical_gift:
    respect_registry: My agent shall respect any anatomical gift I have made by driver's license, donor registry or
      other record, and this instrument makes no new gift
    agent_may: My agent may make an anatomical gift of my body or any part on my behalf
    none: My agent may not make an anatomical gift of my body or any part on my behalf
  execution_method:
    witnesses: Two qualified adult witnesses
    notary: Acknowledgment before a notary public
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
    _: person__health_care_agent
  person__health_care_agent:
    _: person__alternate_health_care_agent
  person__alternate_health_care_agent:
    _: people__consultation_family
  people__consultation_family:
    _: custom_single_choice__life_sustaining_wishes
  custom_single_choice__life_sustaining_wishes:
    _: custom_single_choice__nutrition_hydration
  custom_single_choice__nutrition_hydration:
    _: custom_single_choice__anatomical_gift
  custom_single_choice__anatomical_gift:
    _: custom_single_choice__execution_method
  custom_single_choice__execution_method:
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

# Durable Power of Attorney for Health Care Decisions of {{person__client.name}}

## Warning to person executing this document

This is an important legal document. Before executing it, you should know that it creates a durable power of attorney
for health care, giving the person you designate as your agent the power to make health-care decisions for you when you
are unable to make them yourself. You may revoke this power of attorney at any time. If there is anything in this
document you do not understand, ask a lawyer to explain it to you.

## I. Designation of health-care agent

I, {{person__client.name}}, of {{person__client.street}}, {{person__client.city}}, {{person__client.state}}
{{person__client.zip}}, designate as my agent to make health-care decisions for me:

{{person__health_care_agent.name}}, of {{person__health_care_agent.street}}, {{person__health_care_agent.city}},
{{person__health_care_agent.state}} {{person__health_care_agent.zip}}; telephone {{person__health_care_agent.phone}}.

## II. Alternate agent and family consultation

If {{person__health_care_agent.name}} is not willing, able or reasonably available to make a health-care decision for
me, I designate as my alternate agent {{person__alternate_health_care_agent.name}}, of
{{person__alternate_health_care_agent.street}}, {{person__alternate_health_care_agent.city}},
{{person__alternate_health_care_agent.state}} {{person__alternate_health_care_agent.zip}}; telephone
{{person__alternate_health_care_agent.phone}}. My alternate agent has the same authority as my agent. In this document,
"my agent" means whichever of them is then acting.

I want my agent to consult, when reasonably practicable, with the following members of my family. Consultation does not
create co-agents, a family voting requirement, or a veto over my agent's lawful decision.

{{#for f in people__consultation_family}}

- {{f.name}}

{{/for}}

## III. Creation of durable power of attorney for health care

By this document I intend to create a durable power of attorney for health care. This power of attorney is not affected
by my subsequent incapacity. It becomes effective upon my incapacity, when a physician, an advanced practice registered
nurse, a psychiatrist or a licensed psychologist determines in a writing or other record that I am incapacitated and
unable to make or communicate my own health-care decisions. My agent may not act for me during any period in which I am
able to make and communicate those decisions myself.

## IV. General statement of authority granted

Subject to the limitations in this document, my agent may make health-care decisions for me to the same extent I could
if I had capacity, including consent, refusal of consent, or withdrawal of consent to any care, treatment, service or
procedure to maintain, diagnose or treat a physical or mental condition. My agent shall act consistently with my desires
as stated in this document or otherwise made known to my agent, and, where my desires are unknown, in my best interests.

As NRS 162A.850 provides, my agent may not consent to my commitment or placement in a facility for treatment of mental
illness, convulsive treatment, psychosurgery, sterilization, abortion, aversive intervention as defined in NRS 449A.203,
or experimental medical, biomedical or behavioral treatment or participation in any medical, biomedical or behavioral
research program. My agent's decisions about the use or nonuse of life-sustaining treatment must conform to my known
desires, including those stated in Article V.

## V. Statement of desires

### A. Life-sustaining treatment

{{custom_single_choice__life_sustaining_wishes}}.

### B. Artificial nutrition and hydration

{{custom_single_choice__nutrition_hydration}}.

### C. Relief from pain

Regardless of my instructions in Sections V.A and V.B, I want to receive care that keeps me comfortable and relieves
pain, even if that care may hasten my death.

## VI. Anatomical gifts

{{custom_single_choice__anatomical_gift}}. This instrument does not represent that my driver's-license designation or
donor-registry entry has been updated. The absence of a designation is not a refusal of an anatomical gift otherwise
authorized under the Revised Uniform Anatomical Gift Act, NRS 451.500 to 451.598, inclusive.

## VII. Inspection and disclosure of medical information

Subject to any limitation in this document, my agent may request, review and receive any information, oral or written,
regarding my physical or mental health, including medical and hospital records, and may execute any release or other
document required to obtain that information. For purposes of 45 C.F.R. 164.502(g), my agent is my personal
representative.

## VIII. Prior designations revoked

I revoke any prior power of attorney for health care.

## IX. Date and signature of principal

I sign this durable power of attorney for health care on ____________________, at ____________________, Nevada.

Signature: ________________________________

{{person__client.name}}, Principal

{{#if custom_single_choice__execution_method=notary}}

## X. Certificate of acknowledgment of notary public

State of Nevada

County of {{custom_single_choice__signing_county}}

This instrument was acknowledged before me on ____________________ by {{person__client.name}}.

Signature of notarial officer: ________________________________

(Seal, if any)

Title and rank (optional): ________________________________

{{/if}}

{{#if custom_single_choice__execution_method=witnesses}}

## X. Statement of witnesses

Each of us is an adult. The principal signed this power of attorney for health care in our presence and appeared to be
of sound mind and under no duress, fraud or undue influence. Neither of us is the person appointed as agent or alternate
agent by this document. If the principal resides in a nursing home, neither of us is the owner, operator or employee of
that nursing home.

Witness 1 signature, printed name, residence address and date: ________________________________

Witness 2 signature, printed name, residence address and date: ________________________________

{{/if}}

## Attorney execution note

The principal's signature must be acknowledged before a notary public or witnessed by two adult witnesses (NRS
162A.790); this draft carries only the method chosen. If the principal lives in a nursing home, neither witness may be
its owner, operator or employee. Compare the draft with the advance health-care directive form in NRS 162A.855 before
release. Because the power springs on incapacity, it takes effect only on a written determination by a physician,
advanced practice registered nurse, psychiatrist or licensed psychologist (NRS 162A.810). Under NRS 162A.840 the agent
may not be the principal's provider of health care, an employee of that provider, or the operator or an employee of a
health-care facility, unless the agent is the principal's spouse, legal guardian or next of kin. A new power of attorney
for health care revokes every earlier one, and filing for dissolution or annulment ends a spouse-agent's authority
unless the instrument says otherwise (NRS 162A.820). A power of attorney for health care that addresses life-sustaining
treatment also serves as a declaration under NRS 449A.433(3), so reconcile Article V with any separate declaration. Do
not combine this instrument with the financial power of attorney.

Authorities: NRS 162A.700 to 162A.870, inclusive, especially 162A.790, 162A.810, 162A.820, 162A.840, 162A.850 and
162A.855; NRS 449A.203 and 449A.433; NRS 451.500 to 451.598, inclusive, especially 451.556; 45 C.F.R. 164.502(g).
