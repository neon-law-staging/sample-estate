---
kind: directive
title: Nevada statutory form power of attorney
respondent_type: person
code: statutory_financial_power_of_attorney
jurisdiction: NV
confidential: true
prompts:
  effective_authority: When should the agent's authority begin?
  content_authority: Should the agent have express authority over the content of electronic communications?
  signing_county: In which Nevada county will the principal's signature be acknowledged?
choices:
  effective_authority:
    immediate: Immediately on execution, and durable
    springing: Only on a licensed medical doctor's written opinion of incapacity
  content_authority:
    grant: Grant it, subject to the provider's online-tool directions
    withhold: Withhold it
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
    _: person__financial_agent
  person__financial_agent:
    _: person__first_alternate_financial_agent
  person__first_alternate_financial_agent:
    _: person__second_alternate_financial_agent
  person__second_alternate_financial_agent:
    _: custom_single_choice__effective_authority
  custom_single_choice__effective_authority:
    _: custom_single_choice__content_authority
  custom_single_choice__content_authority:
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

# Statutory Form Power of Attorney

Attorney review draft — not for execution. This instrument tracks the statutory form power of attorney in NRS 162A.620.
Every initial field below is completed by the principal at signing; none is preselected. Before release, conform each
heading and notice to the current statutory text.

THIS IS AN IMPORTANT LEGAL DOCUMENT. IT CREATES A DURABLE POWER OF ATTORNEY FOR FINANCIAL MATTERS. BEFORE EXECUTING THIS
DOCUMENT, YOU SHOULD KNOW THESE IMPORTANT FACTS:

1. THIS DOCUMENT GIVES THE PERSON YOU DESIGNATE AS YOUR AGENT THE POWER TO MAKE DECISIONS CONCERNING YOUR PROPERTY FOR
   YOU. YOUR AGENT WILL BE ABLE TO MAKE DECISIONS AND ACT WITH RESPECT TO YOUR PROPERTY (INCLUDING YOUR MONEY) WHETHER
   OR NOT YOU ARE ABLE TO ACT FOR YOURSELF.
2. THIS POWER OF ATTORNEY BECOMES EFFECTIVE IMMEDIATELY UNLESS YOU STATE OTHERWISE IN THE SPECIAL INSTRUCTIONS.
3. THIS POWER OF ATTORNEY DOES NOT AUTHORIZE THE AGENT TO MAKE HEALTH CARE DECISIONS FOR YOU.
4. THE PERSON YOU DESIGNATE IN THIS DOCUMENT HAS A DUTY TO ACT CONSISTENT WITH YOUR DESIRES AS STATED IN THIS DOCUMENT
   OR OTHERWISE MADE KNOWN OR, IF YOUR DESIRES ARE UNKNOWN, TO ACT IN YOUR BEST INTERESTS.
5. YOU SHOULD SELECT SOMEONE YOU TRUST TO SERVE AS YOUR AGENT. UNLESS YOU SPECIFY OTHERWISE, GENERALLY THE AGENT'S
   AUTHORITY WILL CONTINUE UNTIL YOU DIE OR REVOKE THE POWER OF ATTORNEY OR THE AGENT RESIGNS OR IS UNABLE TO ACT FOR
   YOU.
6. YOUR AGENT IS ENTITLED TO REASONABLE COMPENSATION UNLESS YOU STATE OTHERWISE IN THE SPECIAL INSTRUCTIONS.
7. THIS FORM PROVIDES FOR DESIGNATION OF ONE AGENT. IF YOU WISH TO NAME MORE THAN ONE AGENT YOU MAY NAME A CO-AGENT IN
   THE SPECIAL INSTRUCTIONS. CO-AGENTS ARE NOT REQUIRED TO ACT TOGETHER UNLESS YOU INCLUDE THAT REQUIREMENT IN THE
   SPECIAL INSTRUCTIONS.
8. IF YOUR AGENT IS UNABLE OR UNWILLING TO ACT FOR YOU, YOUR POWER OF ATTORNEY WILL END UNLESS YOU HAVE NAMED A
   SUCCESSOR AGENT. YOU MAY ALSO NAME A SECOND SUCCESSOR AGENT.
9. YOU HAVE THE RIGHT TO REVOKE THE AUTHORITY GRANTED TO THE PERSON DESIGNATED IN THIS DOCUMENT.
10. THIS DOCUMENT REVOKES ANY PRIOR DURABLE POWER OF ATTORNEY.
11. IF THERE IS ANYTHING IN THIS DOCUMENT THAT YOU DO NOT UNDERSTAND, YOU SHOULD ASK A LAWYER TO EXPLAIN IT TO YOU.

## 1. Designation of agent

I, {{person__client.name}}, do hereby designate and appoint:

Name: {{person__financial_agent.name}}

Address: {{person__financial_agent.street}}, {{person__financial_agent.city}}, {{person__financial_agent.state}}
{{person__financial_agent.zip}}

Telephone Number: {{person__financial_agent.phone}}

as my agent to make decisions for me and in my name, place and stead and for my use and benefit and to exercise the
powers as authorized in this document.

## 2. Designation of alternate agent

(You are not required to designate any alternative agent but you may do so. Any alternative agent you designate will be
able to make the same decisions as the agent designated above in the event that he or she is unable or unwilling to act
as your agent. Also, if the agent designated in paragraph 1 is your spouse, his or her designation as your agent is
automatically revoked by law if your marriage is dissolved.)

If my agent is unable or unwilling to act for me, then I designate the following person(s) to serve as my agent as
authorized in this document, such person(s) to serve in the order listed below:

A. First Alternative Agent

Name: {{person__first_alternate_financial_agent.name}}

Address: {{person__first_alternate_financial_agent.street}}, {{person__first_alternate_financial_agent.city}},
{{person__first_alternate_financial_agent.state}} {{person__first_alternate_financial_agent.zip}}

Telephone Number: {{person__first_alternate_financial_agent.phone}}

B. Second Alternative Agent

Name: {{person__second_alternate_financial_agent.name}}

Address: {{person__second_alternate_financial_agent.street}}, {{person__second_alternate_financial_agent.city}},
{{person__second_alternate_financial_agent.state}} {{person__second_alternate_financial_agent.zip}}

Telephone Number: {{person__second_alternate_financial_agent.phone}}

## 3. Other powers of attorney

This Power of Attorney is intended to, and does, revoke any prior Power of Attorney for financial matters I have
previously executed.

## 4. Nomination of guardian

If, after execution of this Power of Attorney, proceedings seeking an adjudication of incapacity are initiated either
for my estate or my person, I hereby nominate as my guardian or conservator for consideration by the court my agent
herein named, in the order named.

## 5. Grant of general authority

I grant my agent and any successor agent(s) general authority to act for me with respect to the following subjects:

(INITIAL each subject you want to include in the agent's general authority. If you wish to grant general authority over
all of the subjects you may initial "All Preceding Subjects" instead of initialing each subject.)

- [.....] Real Property
- [.....] Tangible Personal Property
- [.....] Stocks and Bonds
- [.....] Commodities and Options
- [.....] Banks and Other Financial Institutions
- [.....] Safe Deposit Boxes
- [.....] Operation of Entity or Business
- [.....] Insurance and Annuities
- [.....] Estates, Trusts and Other Beneficial Interests
- [.....] Legal Affairs, Claims and Litigation
- [.....] Personal Maintenance
- [.....] Benefits from Governmental Programs or Civil or Military Service
- [.....] Retirement Plans
- [.....] Taxes
- [.....] All Preceding Subjects

## 6. Grant of specific authority

My agent MAY NOT do any of the following specific acts for me UNLESS I have INITIALED the specific authority listed
below:

(CAUTION: Granting any of the following will give your agent the authority to take actions that could significantly
reduce your property or change how your property is distributed at your death. INITIAL ONLY the specific authority you
WANT to give your agent.)

- [.....] Create, amend, revoke or terminate an inter vivos, family, living, irrevocable or revocable trust
- [.....] Make a gift, subject to the limitations of NRS and any special instructions in this Power of Attorney
- [.....] Create or change rights of survivorship
- [.....] Create or change a beneficiary designation
- [.....] Waive the principal's right to be a beneficiary of a joint and survivor annuity, including a survivor benefit
  under a retirement plan
- [.....] Exercise fiduciary powers that the principal has authority to delegate
- [.....] Disclaim or refuse an interest in property, including a power of appointment

## 7. Expression of intent concerning living arrangements

- [.....] It is my intention to live in my home as long as it is safe and my medical needs can be met. My agent may
  arrange for a natural person, employee of an agency or provider of community-based services to come into my home to
  provide care for me. When it is no longer safe for me to live in my home, I authorize my agent to place me in a
  facility or home that can provide any medical assistance and support in my activities of daily living that I require.
  Before being placed in such a facility or home, I wish for my agent to discuss and share information concerning the
  placement with me.
- [.....] It is my intention to live in my home for as long as possible without regard for my medical needs, personal
  safety or ability to engage in activities of daily living. My agent may arrange for a natural person, an employee of
  an agency or a provider of community-based services to come into my home and provide care for me. I understand that,
  before I may be placed in a facility or home other than the home in which I currently reside, a guardian must be
  appointed for me.
- [.....] I desire for my agent to take the following actions relating to my care: ________________________________

## 8. Limitation on agent's authority

An agent that is not my spouse MAY NOT use my property to benefit the agent or a person to whom the agent owes an
obligation of support unless I have included that authority in the Special Instructions.

## 9. Special instructions or other or additional authority granted to agent

{{#if custom_single_choice__content_authority=grant}}

Digital assets. I expressly grant my agent authority over the content of electronic communications sent or received by
me and over my other digital assets, within the meaning of Chapter 722 of NRS, subject to any direction I have given
through a custodian's online tool and to the custodian's terms of service.

{{/if}}

{{#if custom_single_choice__content_authority=withhold}}

Digital assets. I do not grant my agent authority over the content of electronic communications sent or received by me.
This withholding does not limit any disclosure to my agent of a catalogue of my electronic communications, or of my
other digital assets, that Chapter 722 of NRS permits.

{{/if}}

Other special instructions: ________________________________

## 10. Authority of principal

Except as otherwise expressly provided in this Power of Attorney, the authority of a principal to act on his or her own
behalf continues after executing this Power of Attorney and any decision or instruction communicated by the principal
supersedes any inconsistent decision or instruction communicated by an agent appointed pursuant to this Power of
Attorney.

## 11. Durability and effective date

(INITIAL the clause(s) that applies.)

- [.....] DURABLE. This Power of Attorney shall not be affected by my subsequent disability or incapacity.
- [.....] SPRINGING POWER. It is my intention and direction that my designated agent, and any person or entity that my
  designated agent may transact business with on my behalf, may rely on a written medical opinion issued by a licensed
  medical doctor stating that I am disabled or incapacitated, and incapable of managing my affairs, and that said
  medical opinion shall establish whether or not I am under a disability for the purpose of establishing the authority
  of my designated agent to act in accordance with this Power of Attorney.
- [.....] I wish to have this Power of Attorney become effective on the following date: ____________________
- [.....] I wish to have this Power of Attorney end on the following date: ____________________

Intake election recorded for counsel's reference; it does not replace the principal's initials above:
{{custom_single_choice__effective_authority}}.

## 12. Third party protection

Third parties may rely upon the validity of this Power of Attorney or a copy and the representations of my agent as to
all matters relating to any power granted to my agent, and no person or agency who relies upon the representation of my
agent, or the authority granted by my agent, shall incur any liability to me or my estate as a result of permitting my
agent to exercise any power unless a third party knows or has reason to know this Power of Attorney has terminated or is
invalid.

## 13. Release of information

I agree to, authorize and allow full release of information, by any government agency, business, creditor or third party
who may have information pertaining to my assets or income, to my agent named herein.

## 14. Signature and acknowledgment

YOU MUST DATE AND SIGN THIS POWER OF ATTORNEY. THIS POWER OF ATTORNEY WILL NOT BE VALID UNLESS IT IS ACKNOWLEDGED BEFORE
A NOTARY PUBLIC.

I sign my name to this Power of Attorney on ____________________ (date) at ____________________ (city),
____________________ (state)

________________________________ (Signature)

{{person__client.name}}

### Certificate of acknowledgment of notary public

(You may use acknowledgment before a notary public instead of the statement of witnesses.)

State of Nevada

ss.

County of {{custom_single_choice__signing_county}}

On this ______ day of __________________, in the year ______, before me, ________________________________ (here insert
name of notary public) personally appeared {{person__client.name}}, personally known to me (or proved to me on the basis
of satisfactory evidence) to be the person whose name is subscribed to this instrument, and acknowledged that he or she
executed it.

NOTARY SEAL

________________________________ (Signature of Notary Public)

## Important information for agent

1. Agent's Duties. When you accept the authority granted under this Power of Attorney, a special legal relationship is
   created between you and the principal. This relationship imposes upon you legal duties that continue until you resign
   or the Power of Attorney is terminated or revoked. You must:
   - (a) Do what you know the principal reasonably expects you to do with the principal's property or, if you do not
     know the principal's expectations, act in the principal's best interest;
   - (b) Act in good faith;
   - (c) Do nothing beyond the authority granted in this Power of Attorney; and
   - (d) Disclose your identity as an agent whenever you act for the principal by writing or printing the name of the
     principal and signing your own name as "agent" in the following manner: (Principal's Name) by (Your Signature) as
     Agent
2. Unless the Special Instructions in this Power of Attorney state otherwise, you must also:
   - (a) Act loyally for the principal's benefit;
   - (b) Avoid conflicts that would impair your ability to act in the principal's best interest;
   - (c) Act with care, competence, and diligence;
   - (d) Keep a record of all receipts, disbursements and transactions made on behalf of the principal;
   - (e) Cooperate with any person that has authority to make health care decisions for the principal to do what you
     know the principal reasonably expects or, if you do not know the principal's expectations, to act in the
     principal's best interest; and
   - (f) Attempt to preserve the principal's estate plan if you know the plan and preserving the plan is consistent with
     the principal's best interest.
3. Termination of Agent's Authority. You must stop acting on behalf of the principal if you learn of any event that
   terminates this Power of Attorney or your authority under this Power of Attorney. Events that terminate a Power of
   Attorney or your authority to act under a Power of Attorney include:
   - (a) Death of the principal;
   - (b) The principal's revocation of the Power of Attorney or your authority;
   - (c) The occurrence of a termination event stated in the Power of Attorney;
   - (d) The purpose of the Power of Attorney is fully accomplished; or
   - (e) If you are married to the principal, your marriage is dissolved.
4. Liability of Agent. The meaning of the authority granted to you is defined in NRS 162A.200 to 162A.660, inclusive. If
   you violate NRS 162A.200 to 162A.660, inclusive, or act outside the authority granted in this Power of Attorney, you
   may be liable for any damages caused by your violation.
5. If there is anything about this document or your duties that you do not understand, you should seek legal advice.

## Attorney execution note

Section 14 of the form requires the principal's signature to be acknowledged before a notary public; NRS 162A.220(1)
presumes an acknowledged signature genuine. If, at execution, the principal resides in a hospital, residential facility
for groups, facility for skilled nursing or home for individual residential care, attach the certification of competency
that NRS 162A.220(2) requires. If the principal resides or is about to reside in a hospital, assisted living facility or
facility for skilled nursing, do not name that facility, its owner or operator, or its employee as agent, except as NRS
162A.220(4) permits. Each act listed in NRS 162A.450(1) requires an express grant; this form makes that grant only by
the principal's initials in Section 6. Content of electronic communications is disclosed to the agent only to the extent
Section 9 expressly grants it (NRS 722.360), and a custodian's online-tool direction that the principal can modify or
delete at all times overrides a contrary direction here (NRS 722.310). This form does not reach health care decisions;
execute the power of attorney for health care as a separate instrument under NRS 162A.790.

Authorities: NRS 162A.200 to 162A.660, especially 162A.210, 162A.220, 162A.450 and 162A.620; NRS 162A.790; NRS 722.310
and 722.360.
