---
kind: onboarding
title: Onboarding Letter
respondent_type: person_and_entity
code: onboarding
jurisdiction: NV
confidential: true
output: letter
prompts:
  letter_date: What date should the letter carry?
  flat_fee: What is the total flat fee?
  initial_payment: How much is due on signing this letter?
  signing_payment: How much is due at the notarized signing?
questionnaire:
  BEGIN:
    _: person__client
  person__client:
    _: project__engagement
  project__engagement:
    _: person__firm_attorney
  person__firm_attorney:
    _: custom_datetime__letter_date
  custom_datetime__letter_date:
    _: custom_usd__flat_fee
  custom_usd__flat_fee:
    _: custom_usd__initial_payment
  custom_usd__initial_payment:
    _: custom_usd__signing_payment
  custom_usd__signing_payment:
    _: END
  END: {}
workflow:
  BEGIN:
    draft_created: lawyer_review
  lawyer_review:
    reviewed: END
  END: {}
---

{{custom_datetime__letter_date}}

{{person__client.name}}

{{person__client.street}}

{{person__client.city}}, {{person__client.state}} {{person__client.zip}}

Re: {{project__engagement.name}}

Dear {{person__client.name}}:

Thank you for engaging Neon Law. "Neon Law" is the service name under which Shook Law PLLC (the "Firm") provides legal
services. This letter (the "Onboarding Letter") is the agreement under which the Firm will prepare your estate plan. It
sets out what the Firm will do, what it will cost, and how you and the Firm will work together. It is not itself your
estate plan: no will, trust, or power of attorney takes effect until you sign that document separately, in the way
Nevada law requires.

In this letter, "you" and the "Client" mean the person to whom this letter is addressed. The "Matter" means the
estate-planning engagement named above.

What happens next: read this letter and, if its terms are acceptable, sign it electronically in Section X. The first
payment described in Section II is due when you sign.

## I. Client and scope of the engagement

For this engagement, {{person__client.name}} is the Firm's client. Unless the Firm agrees in a separate signed writing,
this engagement does not make any affiliate, stockholder, investor, officer, director, employee, or other related person
or entity a client of the Firm.

The Firm will provide estate-planning services for this Matter, including preparing estate-planning instruments and
providing related counseling. The engagement includes unlimited lifetime edits to the estate-planning documents prepared
under this engagement.

The Firm's representation is limited to the estate planning described above and any additional work that the Firm and
the Client later agree to in writing. Work outside this scope requires a separate written engagement or an amendment
signed by both parties.

Unless separately agreed in writing, this engagement does not include tax, accounting, financial, investment, valuation,
insurance-coverage, or public-relations advice and does not extend to a matter unrelated to this estate-planning
engagement.

## II. Fees, costs, and invoices

The total flat fee for this engagement is {{custom_usd__flat_fee}}. {{custom_usd__initial_payment}} is due when you sign
this letter. The remaining {{custom_usd__signing_payment}} is due at the notarized signing of your estate-planning
documents.

The flat fee does not include filing fees, recording fees, or other third-party costs that the Client authorizes or that
are reasonably necessary for the engagement. The Firm seeks your approval in advance for a material outside cost when
that is practical.

Every invoice carries its own payment instructions. Use the instructions on the invoice you are paying, not those from
an earlier invoice, because they can change from one invoice to the next.

This letter contains no bank account, routing, or other payment account details.

## III. Staffing and accountability

Each side has one responsible person for the Matter. {{person__firm_attorney.name}} is the Firm's responsible attorney.
{{person__client.name}} is the Client's responsible individual, who gives the Firm instructions and receives advice on
the Client's behalf.

The Firm may use lawyers, contract lawyers, paralegals, administrative personnel, or outside vendors where appropriate.
The Firm remains responsible for their work and for safeguarding the Client's confidences as law and the applicable
professional rules require.

## IV. Reaching us and reading your own files

Write to contact@neonlaw.com for questions, documents, status updates, or complaints about how the Matter is going.

The Firm makes your documents available to you through its online portal while the Firm shares them with you on this
Matter. The portal is a convenience, not the Firm's complete file: internal notes and drafts are working papers and are
not all posted there. You may ask for a copy of anything in your file at any time, without explaining why.

The Firm's current Privacy Policy and Terms of Service address use of the Firm's website and services and apply as
additional terms of this engagement.

The Client consents to electronic communication and electronic delivery of invoices and correspondence about the Matter
at the addresses the Client gives the Firm.

## V. Conflicts, other clients, and advance waiver

The Firm represents other clients and may represent more in the future. If a potential conflict arises, the Firm
addresses it under the applicable rules of professional conduct. The Firm is not agreeing to represent the Client in
every matter or against every potential adverse party; it represents the Client in an additional matter only if both
agree to that in a signed writing.

The Firm treats a conflict for any one of its lawyers as a conflict for the whole Firm. Before taking on a new matter,
the Firm checks it against its current and former matters. If that check turns up a conflict the Firm cannot properly
take on, the Firm will tell the Client promptly, decline the matter rather than wall it off internally, refer the Client
to outside counsel, and return any materials shared with the Firm. The Firm neither pays nor accepts a referral fee on a
matter it refers out. By engaging the Firm, the Client acknowledges that the Firm's lawyers share matter information
among themselves for this purpose.

The Client agrees that the Firm may represent other clients, including clients whose interests are adverse to the Client
or the Client's affiliates, in transactional, corporate, commercial, licensing, regulatory, counseling, and other non-
litigation matters, provided that the matter is not substantially related to this engagement and the Firm protects the
Client's confidential information as the applicable professional rules require. By signing this letter, the Client gives
informed written consent to those transactional representations and acknowledges the opportunity to consult independent
counsel about this waiver.

This advance waiver is limited to transactional and other non-litigation matters. The Client does not waive, and the
Firm does not request, advance consent for litigation, arbitration, or another contested adversarial proceeding.

## VI. What we each do

The Client agrees to provide accurate and complete information, respond to reasonable requests, make the decisions the
estate plan requires, and tell the Firm when relevant circumstances change. The Client agrees to pay fees and authorized
expenses when due. The Firm's advice depends on the information available to it when the advice is given.

The Firm has not made and cannot make any promise, assurance, or guarantee about the outcome of the estate plan or any
other legal matter.

## VII. Confidentiality, the Client's file, and technology

The Firm maintains the Client's confidences as required by law and the applicable professional rules. The Firm may use
secure cloud, document-management, research, communication, automation, and artificial-intelligence tools in providing
legal services, subject to its professional obligations, attorney supervision, and commercially reasonable security and
confidentiality safeguards. Where a technology vendor offers the option, the Firm selects settings that do not permit
the Client's information to be used to train the vendor's public or generally available models.

No AI output substitutes for counsel's professional judgment. A lawyer reviews material AI-assisted work before it is
relied on for legal advice, an instrument, or a substantive external communication. The Firm remains responsible for the
accuracy, confidentiality, and professional review of its work. The Client's consent to that use waives no privilege and
does not release the Firm from responsibility for selecting, configuring, supervising, or using the technology.

The Firm keeps the Client's complete file for the Matter for ten years after the Matter closes. The Client may request a
copy at any point in that period.

## VIII. Governing law and arbitration of disputes

Nevada law governs this letter. Except for a fee dispute the Client elects to submit to the State Bar of Nevada's fee
dispute arbitration program, any controversy or claim arising out of or relating to this engagement or its breach shall
be settled by final and binding arbitration administered by the American Arbitration Association (AAA) in accordance
with its Commercial Arbitration Rules. The arbitration will be before a single arbitrator, conducted confidentially, and
decided under Nevada law. The AAA's rules and fee schedule govern administrative fees and arbitrator compensation, and
judgment on the award may be entered in any court of competent jurisdiction.

The arbitrator applies the same law and may award the same remedies a court would. This Section selects the forum for a
dispute and does not limit, cap, or waive the Firm's responsibility for its own work. Nothing in this Section waives or
overrides any non-waivable statutory or regulatory right applicable to a fee dispute.

By signing this letter, the Client and the Firm each give up the right to a jury trial and to have a covered dispute
decided in court. Because this agreement addresses future disputes, the Client may consult independent counsel before
agreeing to it.

## IX. Ending the engagement

The Client may end this engagement at any time by telling the Firm. The Firm may withdraw as permitted or required by
law and the applicable professional rules, including for nonpayment, a conflict, a failure to cooperate, or other good
cause. Fees and authorized expenses incurred before the engagement ends remain due.

## X. Signatures

The Client and the Firm sign this letter electronically as of the dates below.

Client: {{person__client.name}}

Signature: ____________________________________

Date: _________________________________________

Client initials: _______________________________

Shook Law PLLC, doing business as Neon Law

By: ___________________________________________

Date: _________________________________________
