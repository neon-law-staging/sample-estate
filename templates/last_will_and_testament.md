---
kind: will
title: Nevada last will and testament
respondent_type: person
code: last_will_and_testament
jurisdiction: NV
confidential: true
prompts:
  trust_date: On what date is the trust instrument signed (on or before the date this will is signed)?
  marital_status: What is the testator's marital status?
  minor_children: Does the testator have a minor child who may need a guardian?
  signing_county: In which Nevada county will the self-proving affidavit be sworn?
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
    _: custom_single_choice__marital_status
  custom_single_choice__marital_status:
    _: people__family
  people__family:
    _: entity__trust
  entity__trust:
    _: custom_datetime__trust_date
  custom_datetime__trust_date:
    _: person__executor
  person__executor:
    _: person__alternate_executor
  person__alternate_executor:
    _: custom_yes_no__minor_children
  custom_yes_no__minor_children:
    _: person__guardian
  person__guardian:
    _: person__alternate_guardian
  person__alternate_guardian:
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

# Last Will and Testament of {{person__client.name}}

I, {{person__client.name}}, of {{person__client.city}}, {{person__client.state}}, declare this instrument to be my last
will and testament, and I revoke every will and codicil I have previously made. I intend by this will to dispose of all
of my property, real and personal, including my share of any community property.

## I. Family

My marital status is: {{custom_single_choice__marital_status}}. The members of my family are:

{{#for p in people__family}}

- {{p.name}}

{{/for}}

## II. Survivorship

A person who does not survive me by 120 hours is treated, for all purposes of this will, as having predeceased me. This
Article does not limit the effectiveness of the nomination of my personal representative.

## III. Tangible Personal Property

I give all of my tangible personal property to the trustee of the Trust defined in Article IV, to be held, administered,
and distributed under the terms of the Trust.

## IV. Residuary Estate

### A. Gift to the Trust

I give all the rest, residue, and remainder of my estate to the trustee of the {{entity__trust.name}}, dated
{{custom_datetime__trust_date}} (the "Trust"), to be added to the principal of the Trust and held, administered, and
distributed under the terms of the Trust instrument, including any amendment made before my death, whether made before
or after I sign this will.

I make this gift under NRS 163.230. The Trust is identified in this paragraph, its terms are set forth in a written
instrument other than a will that was signed before or at the same time as this will, and this gift is effective
regardless of the existence, size, or character of the Trust property at my death.

### B. Savings Clause

If the gift in paragraph A is inoperative or invalid for any reason, including because the Trust was revoked or
terminated before my death, I incorporate by reference the terms of the Trust instrument as signed before or at the same
time as this will, without giving effect to any later amendment, and I give my residuary estate to the trustee named in
that instrument, to be held, administered, and distributed as that instrument provides.

### C. Contingent Disposition

If my residuary estate is not disposed of by paragraph A or paragraph B, I give my residuary estate to the persons who
would take it, and in the shares they would take, under the Nevada law of intestate succession had I died intestate.

## V. Digital Assets

### A. Authority Over Digital Assets

My personal representative has the fullest authority over my digital assets that Chapter 722 of NRS allows, including
the authority to access, use, control, transfer, archive, and delete them, to receive the content of my electronic
communications, and to receive from a custodian the catalogue of my electronic communications and my digital assets
other than content.

### B. Priority of an Online-Tool Direction

Under NRS 722.310, a direction I have given through a custodian's online tool, where that tool lets me modify or delete
the direction at all times, overrides a contrary direction in this will. This Article governs every account for which I
have given no such direction.

## VI. Fiduciaries

### A. Personal Representative

I nominate {{person__executor.name}} as the personal representative of my estate. If {{person__executor.name}} does not
survive me, or is unable or unwilling to serve or to continue to serve, I nominate {{person__alternate_executor.name}}
in that person's place.

### B. Bond and Independent Administration

No personal representative or ancillary fiduciary shall be required to file a bond or give other security in any
jurisdiction, unless a law or court rule requires it. This waiver of bond also applies to an administrator with the will
annexed. I request that my personal representative be granted letters without bond and full authority to administer my
estate under the Independent Administration of Estates Act, NRS 143.300 to 143.815, inclusive.

### C. Ancillary Fiduciary

I nominate as ancillary fiduciary the person or corporation that my personal representative appoints by a writing filed
in the court of the ancillary jurisdiction in which my estate is administered. Unless a law or court rule prohibits it,
my personal representative may appoint itself as ancillary fiduciary.

{{#if custom_yes_no__minor_children}}

### D. Guardian of a Minor Child

If a child of mine is a minor at my death and no parent of that child is living and able to act, I nominate
{{person__guardian.name}} as guardian of the person and estate of that child. If {{person__guardian.name}} is unable or
unwilling to serve, I nominate {{person__alternate_guardian.name}}. I request that no guardian be required to post bond.

{{/if}}

## VII. Debts, Expenses, and Taxes

### A. Debts and Administration Expenses

I direct my personal representative to pay from my residuary estate the expenses of my last illness and funeral, the
expenses of administering my estate, and my legally enforceable debts, other than a debt secured by property that passes
subject to that security.

### B. Taxes

I direct that every estate, inheritance, and succession tax payable by reason of my death, including any such tax on
property passing outside this will, be paid from my residuary estate without apportionment and without a right of
recovery against any recipient.

## VIII. Definitions

### A. Personal Representative and Ancillary Fiduciary

"Personal representative" means the person or persons, the institution, or any combination of them holding letters in my
estate. "Ancillary fiduciary" means any representative of my estate needed to administer it in a jurisdiction other than
the one in which I am domiciled at my death.

### B. Tangible Personal Property

"Tangible personal property" means corporeal personal property of any kind, including any insurance on it and the
proceeds of that insurance. It excludes cash, other intangible personal property, and property used by me in a trade,
business, or profession.

### C. Residuary Estate

"Residuary estate" means all of my estate, of whatever nature and wherever situated, in which I have any interest and
which is not otherwise effectively disposed of by a provision of this will other than Article IV.

### D. Digital Asset Terms

"Digital asset", "custodian", "content of an electronic communication", "catalogue of electronic communications", and
"online tool" have the meanings given in Chapter 722 of NRS.

## IX. Powers of Personal Representative

In addition to the powers given by Nevada law and by other provisions of this will, my personal representative has the
following powers, exercisable as often as my personal representative considers advisable and until final distribution,
to the extent the court having jurisdiction permits their exercise without further order.

### A. Specific Powers

1. To hold, retain, invest, reinvest, and manage property without diversification as to kind, amount, risk, or
   productivity, in realty or personalty.
2. To partition, sell, exchange, grant, convey, deliver, assign, transfer, lease, option, mortgage, pledge, abandon,
   borrow against, contract for, or distribute any property of my estate.
3. To distribute in cash or in kind, or partly in each, at fair market value on the date of distribution.
4. To continue, sell, or wind up any business interest, and to carry out agreements binding on my estate.
5. To abandon, settle, or contest claims in favor of or against my estate.
6. To make the tax elections available to my estate, without compensating adjustment between principal and income.
7. To employ counsel, accountants, appraisers, and other agents, and to pay their reasonable compensation.
8. To hold the property of my estate in the name of a nominee.

### B. Distribution to a Minor or a Person Under a Disability

To distribute any property of my estate that vests outright in a minor, or in a person who in my personal
representative's opinion is under a disability or unable to administer a distribution properly, to a custodian under
Nevada's Uniform Act on Transfers to Minors, Chapter 167 of NRS, or the comparable law of another state, or to the
trustee of the Trust to be held for that beneficiary. A receipt for a distribution so made fully discharges my personal
representative.

## X. Miscellaneous Provisions

### A. No Contest

If a beneficiary contests the validity of this will or any of its provisions, that beneficiary's right to take any
interest under this will shall be determined as though the beneficiary had predeceased me without surviving descendants.
This condition does not apply to any action that NRS 137.005 excepts from enforcement of a no-contest clause, including
an action to invalidate this will that is instituted and maintained in good faith and based on probable cause.

### B. Partial Invalidity

If a provision of this will is unenforceable, the remaining provisions are nonetheless carried into effect.

### C. Interpretation

The masculine, feminine, and neuter, and the singular and plural, each include the others as appropriate. A reference to
a section of a code, statute, or regulation includes any successor to it and any amendment of it.

### D. Intentional Omission

I have intentionally omitted to provide in this will for any person not mentioned in it who, had I died intestate, would
have been entitled to share in my estate as an heir at law or otherwise.

### E. Governing Law

The law of the State of Nevada governs this will and the construction of its terms.

## Execution

I sign this will on the date written below, in the presence of the two witnesses who sign below.

Signature: ____________________________________

{{person__client.name}}, Testator

Date: _________________________________________

## Attestation

The instrument above was signed on the date written above by {{person__client.name}}, the testator, in the presence of
each of us. The testator declared to each of us that the instrument is the testator's last will and testament, and asked
each of us to sign as an attesting witness. We now sign our names below, in the testator's presence and in the presence
of each other. The testator appeared to us to be of sound mind and under no constraint or undue influence.

Witness signature: ____________________________________

Print name and residence address: _____________________

Witness signature: ____________________________________

Print name and residence address: _____________________

## Affidavit of Attesting Witnesses

STATE OF NEVADA

COUNTY OF {{custom_single_choice__signing_county}}

(Date) ____________________

Then and there personally appeared ____________________ and ____________________, who, being duly sworn, depose and say:
That they witnessed the execution of the foregoing will of the testator, {{person__client.name}}; that the testator
subscribed the will and declared it to be his or her last will and testament in their presence; that they thereafter
subscribed the will as witnesses in the presence of the testator and in the presence of each other and at the request of
the testator; and that the testator at the time of the execution of the will appeared to them to be of full age and of
sound mind and memory. Each affiant further states that the testator appeared to be under no constraint or undue
influence, and that the affiant is a competent adult and is not a devisee under the will.

Affiant: ____________________________________

Print name and residence address: _____________________

Affiant: ____________________________________

Print name and residence address: _____________________

Subscribed and sworn to before me this ______ day of the month of ____________ of the year ______.

Signature of notarial officer: ________________________________

(Seal, if any)

This affidavit is written on or attached to the will, as NRS 133.050 requires.

## Attorney Execution Note

At least two competent witnesses must subscribe in the testator's presence. Use disinterested witnesses: a devise to a
subscribing witness is void unless two other competent witnesses subscribed. Have the witnesses sign in each other's
presence, as the affidavit recites. The court keeps discretion over bond despite the waiver. Chapter 135 of NRS sets no
120-hour survival period, and under NRS 135.080 it does not apply where a will provides otherwise, so Article II
governs. The guardian nomination in Article VI takes effect only when the nominee petitions and is appointed. Sign the
Trust instrument before or together with this will.

Authorities:

- NRS 133.040, 133.050, 133.055 and 133.060 (execution and witnesses)
- NRS 135.080 (survival clauses) and 137.005 (no-contest clauses)
- NRS 138.090 and 142.020 (bond)
- NRS 143.300 to 143.815 (independent administration)
- NRS 159A.062 (guardian nomination) and 163.230 (pour-over devise)
- NRS 722.310 (online tools)
- Chapter 167 of NRS (transfers to minors)
