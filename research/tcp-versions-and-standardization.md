# TCP versions, standardization, and transition timing

[Research overview](../research.md) · [Open questions](../questions.md) · [Sources](../sources/README.md)

This notebook distinguishes AUTODIN II’s specifications and contracted branch from successive research and DoD standard editions. The upgrade order and after-IOC placement are documented; the ordered analysis and explanation for that timing remain missing.

Read the [findings and limits](tcp-versions-and-standardization.md#findings-and-limits), the [supporting evidence](tcp-versions-and-standardization.md#evidence), or the [unresolved questions](tcp-versions-and-standardization.md#unresolved-questions). Recorded reading boundaries are in the [reading guide](../sources/coverage.md).

## Findings and limits

### An early TCP specification was written for AUTODIN II

**Assessment.** Directly established in the recovered specification itself.

**Evidence.** SRI TCP, July 15, 1976, preface p. i; IEN 40, p. 1; IEN 151, p. 1.

### AUTODIN II requirements changed TCP features

**Assessment.** Directly established for security and priority fields; do not generalize to every feature.

**Evidence.** IEN 40, p. 1.

### The research TCP specification deliberately deferred AUTODIN II modifications for reassessment

**Assessment.** Directly established for security and priority modifications in the March 1977 specification.

**Evidence.** IEN 5, printed p. 3 / PDF p. 4.

### DoD TCP/IP standardization was tied to a broader defense-network consolidation/interconnection program centered on AUTODIN II

**Assessment.** Strongly established.

**Evidence.** December 23, 1978 memorandum reproduced in IEN 152.

### AUTODIN II's own early TCP diverged from the emerging standard, requiring an upgrade

**Assessment.** Directly established; central evidence of the proposed tension.

**Evidence.** December 1978 memorandum in IEN 152; implementation differences in IEN 70, p. 2.

### The December 1978 order left the transition's timing open on cost and schedule grounds

**Assessment.** Directly established. It asks DCA for a cost tradeoff analysis “to determine the optimum time for this transition,” results due April 1979. This states the anticipated grounds, not a finding; the analysis itself remains missing.

**Evidence.** IEN 152, PDF p. 3, inspected.

### The April 1980 ratification states a reason for placing AUTODIN II implementation after IOC

**Assessment.** Contradicted by the document: it states the placement and no reason. Silence on the face of the order does not establish that no reason was recorded elsewhere.

**Evidence.** IEN 152, PDF p. 4, inspected.

### A finished DoD standard was available through 1979 while AUTODIN II delayed

**Assessment.** Not supported by the published-edition sequence. The order expected finals by April 1979; February IEN 81 and August IEN 112 lack the later TCP sections, December IEN 124 announces additions, and January 1980's edition was ratified in April. This does not exclude working drafts or earlier TCP/IP branches carrying related features, or establish the reason for deferral.

**Evidence.** IEN 152 p. 3; IEN 81 preface; IEN 124 and IEN 123 prefaces; IEN 129 / RFC 761 preface; IEN 134; IEN 145.

### The contracted AUTODIN II baseline had begun converging on the DoD standard by the time of ratification

**Assessment.** Not established by the retained deliverables. Western Union revised both host-protocol specifications on February 8, 1980 under DCA200-C-637, and the THP reference list, unchanged since February 1979, cites the July 1976 SRI specifications and the DCA System Performance Specification and no DoD standard document. An absent reference is not a stated reason.

**Evidence.** AD-A081757, PDF pp. 6, 7, 12, inspected.

### Western Union's February 1980 revision implemented the standard TCP/IP format

**Assessment.** Contradicted by the specification: it retains a 29-byte AUTODIN II TCP header, zero network fields, and BSL controls. Document revision 3 is not TCP version 3.

**Evidence.** Western Union, pp. 20, A1, A5-A6, E3 / PDF pp. 29, 51, 55-56, 161.

## Evidence

- [The June 1978 TCP-4 draft](tcp-versions-and-standardization.md#the-june-1978-tcp-4-draft)
- [The March 1977 reassessment of military requirements](tcp-versions-and-standardization.md#the-march-1977-reassessment-of-military-requirements)
- [The December 1978 standardization order](tcp-versions-and-standardization.md#the-december-1978-standardization-order)
- [The upgrade order, standard editions, and contracted baseline](tcp-versions-and-standardization.md#the-upgrade-order-standard-editions-and-contracted-baseline)
- [DCA record schedules and SRI contract proposals](tcp-versions-and-standardization.md#dca-record-schedules-and-sri-contract-proposals)
- [IDA P-1402: citation held, original unrecovered](tcp-versions-and-standardization.md#ida-p-1402-citation-held-original-unrecovered)
- [The adjacent NIC leaves: execution unestablished](tcp-versions-and-standardization.md#the-adjacent-nic-leaves-execution-unestablished)
- [The July 1976 SRI specification: identity](tcp-versions-and-standardization.md#the-july-1976-sri-specification-identity)
- [The SRI requirements, controls, and interfaces](tcp-versions-and-standardization.md#the-sri-requirements-controls-and-interfaces)
- [Internetting and the SRI specification’s boundary](tcp-versions-and-standardization.md#internetting-and-the-sri-specifications-boundary)
- [Western Union’s February 1980 TCP branch](tcp-versions-and-standardization.md#western-unions-february-1980-tcp-branch)

### The June 1978 TCP-4 draft

Jon Postel, *Transmission Control Protocol, Version 4*, IEN 40, June 1978, printed/PDF pp. 1-2. These pages were read from the original image-only copy as well as the OCR companion.

[Original TCP-4 draft](https://www.rfc-editor.org/ien/ien40.pdf)

The history on p. 1 distinguishes the original TCP, a specification prepared for DCA's AUTODIN II project, and a subsequent version for ARPA internetwork research. It expressly attributes the addition of security and priority fields to AUTODIN II requirements. It also describes a resynchronization mechanism in that version, followed by a different mechanism and a more general options field in the next research version.

This is the clearest evidence for an actual design influence, beyond a shared sponsor or a proposed application. The same introduction describes TCP as serving interconnected networks. Treat this as a version history with branching and revision, not one unchanged specification traveling from AUTODIN II to the Internet. In particular, the June 1978 draft contains arrangements that differ from the final 1981 standard; its version number alone does not establish identity with RFC 793.

### The March 1977 reassessment of military requirements

Vinton Cerf, *Specification of Internet Transmission Control Program, TCP (Version 2)*, IEN 5, March 1977, introduction, printed p. 3 / local PDF p. 4. The complete introduction was checked visually.

[IEN 5](https://www.rfc-editor.org/ien/ien5.pdf)

The introduction describes version 2 as descending directly from the original version 1, with only partial overlap with the AUTODIN II specification. It identifies a different resynchronization procedure and an options field intended to accommodate several kinds of service. Most directly, it says the AUTODIN II modifications for security and priority were left out pending further assessment in connection with ARPA-sponsored end-to-end security projects. It anticipates further work on speech, broadcast, graphics, security, priority, flow control, and routing.

This is direct evidence of concurrent divergence and reconsideration during protocol development. It is stronger evidence for a version-specific account than the observation that later networks required new routing protocols. It also prevents treating security and priority as permanently rejected: the text reserves room for them and anticipates further work. Read it alongside the later IEN 40 history and implementation reports.

### The December 1978 standardization order

Vint Cerf, *DoD Protocol Standardization*, IEN 152, July 1, 1980, reproduces earlier official memoranda. The December 23, 1978 Gerald P. Dinneen memorandum occupies local PDF pp. 2-3; both checked visually across the investigation. The April 3, 1980 ratification memorandum, PDF p. 4, was also inspected visually in the second September 11 batch.

[IEN 152 with its attachments](https://history.rfc-editor.org/ien/ien152.txt)

The December memorandum anticipates AUTODIN II as a common-user defense service, incorporates or interfaces other defense/intelligence networks, directs adoption of standards based on TCP/IP version 4, and includes requirements for security, precedence, and community-of-interest controls. DCA is assigned executive responsibility for the protocols. This is exceptionally strong evidence connecting standardization to a particular institutional program.

It also says the host protocol being developed for AUTODIN II evolved from an earlier TCP and was **“unsuitable for internetwork operation.”** It directs an upgrade and, separately, a **cost tradeoff analysis “to determine the optimum time for this transition.”** The 1980 memorandum ratifies TCP/IP while allowing the AUTODIN II transition after initial operational capability. This documents a procurement and protocol-development coordination problem, including the cost of bringing the operational project into alignment with the emerging standard.

The complete attachments give more precise retrieval targets. The December 23, 1978 memorandum's second page / PDF p. 3 requires the analysis **by April 1979**, and the same page sets the standard's own schedule: draft specifications in January 1979, final specifications distributed by April 1979 after working-group review and DCA/DARPA testing, and promulgation with adoption dates at that point. [upgrade chronology](tcp-versions-and-standardization.md#the-upgrade-order-standard-editions-and-contracted-baseline) measures what actually happened against that schedule. The April 3, 1980 order / PDF p. 4 places AUTODIN II implementation after initial operational capability and directs DCA to provide workshops and implementation support documents. These instructions establish the schedule decision and intended assistance, but do not supply the analysis or explain its findings.

The accompanying management plan, printed pp. 2-3 and 5 / PDF pp. 6-7 and 9, assigns technical review and testing to Systems Engineering, DCA Code 1000, assisted by the **Protocol Standards Technical Panel (PSTP)**. Operations and Readiness, Code 500, owns configuration control, assisted by the **Protocol Configuration Control Board (PCCB)**. The **Protocol Standards Steering Group (PSSG)** advises on policy. Its initial engineering chairmanship is to pass to operations when the technology matures. These original pages were inspected. The plan makes continued research, international standards monitoring, and operational control part of the same arrangement. Its paragraph 5f also gives the Executive Agent authority to approve or disapprove **waivers** requested by the Services and Defense Agencies; the AUTODIN II clause was an instruction in the ratifying memorandum rather than a waiver granted under that authority, and the two should not be conflated. No completed cost analysis, relevant panel minutes, or contractor explanation of the deferral has been recovered. The February 1980 Western Union specifications establish the continuing technical divergence, not the cause of the April schedule decision. The Chunk 2 pass of September 13, 2026 developed this finding; read [upgrade chronology](tcp-versions-and-standardization.md#the-upgrade-order-standard-editions-and-contracted-baseline) next.

The AUTODIN II host protocol, the ARPA research versions, and standard TCP/IP therefore need to be distinguished so that their interaction can be explained. The memorandum's judgment about the older AUTODIN II protocol should not be generalized to all TCP.

The current [RFC Editor IEN 152 text](https://history.rfc-editor.org/ien/ien152.txt), checked September 19, 2026, includes both substantive memoranda and the management plan. The earlier description of that URL as only a covering note is incorrect for the currently served text. Retain the complete local PDF and checked images for comparison with the original pages.

### The upgrade order, standard editions, and contracted baseline

The Chunk 2 pass of September 13, 2026 did not recover the ordered analysis or any record stating why the transition was placed after IOC. It did establish three things that bear directly on the competing explanations, and it corrected the description of the instrument the December memorandum actually ordered. The full evidence, coverage, and access failures are in the [pass record](../sources/records/upgrade-order-and-standard-editions.json).

#### The order and ratification

**What the order actually asks for.** The December 23, 1978 memorandum, PDF p. 3, reads: "Because the host-to-host protocol being developed for AUTODIN II evolved from an early version of TCP and is unsuitable for internetwork operation, the AUTODIN II TCP will have to be upgraded to the standard protocol set. **Recognizing that there may be cost and schedule impacts on the AUTODIN II program, the Defense Communications Agency should perform a cost tradeoff analysis to determine the optimum time for this transition.** DCA should provide the results of this analysis by April 1979." Two things follow. The instrument is a cost tradeoff analysis whose object is the timing, not a general cost and schedule study; earlier wording in this brief conflated them. And the timing of the transition is treated as an open variable from the first day, with cost and schedule impacts on the AUTODIN II program named as the grounds. That is a documented reason for leaving the date open. It is not evidence of what the analysis concluded, and it precedes the analysis by four months.

The April 3, 1980 memorandum, PDF p. 4, then states only that "The AUTODIN II implementation of these protocol standards will take place as soon after AUTODIN II IOC as possible," and disestablishes the OSD Protocol Standards Working Group, transferring its responsibilities to the DCA panels defined in the Executive Agent Charter. No reason is given on the face of the order. The memorandum is on Assistant Secretary of Defense (Communications, Command, Control and Intelligence) letterhead and carries a signature that appears identical to Dinneen's on the December memorandum; that page has no typed name block, so treat the attribution as read from the signature.

#### Order, standard, and implementation chronology

**A dated chronology, keeping the order, the analysis, the standard, the ratification, and the intended implementation apart.**

| Date | Event | Kind |
| --- | --- | --- |
| 23 Dec 1978 | Upgrade ordered; cost tradeoff analysis on timing tasked, results due April 1979; OSD Protocol Standards Working Group formed; AUTODIN II "expected to become operational during FY 1980"; draft specifications January 1979, finals April 1979. | Order |
| Jan 1979 | A DCEC-sponsored C TCP-4 for Unix runs at BBN, EDN, and NPS and is reported compatible with AUTODIN II security, precedence, and user-group requirements; preemption not yet added. | Reported implementation status, IEN 76 |
| Feb 1979 | TCP version 4, IEN 81. Its preface records five previous editions and no security, compartmentation, or precedence content. | Specification |
| 20 Feb 1979 | Western Union THP specification, original issue, contract DCA200-C-637, CDRL B006. | Contract specification |
| 5 Mar 1979 | Western Union TCP specification, original issue, same contract and CDRL. | Contract specification |
| **Apr 1979** | **Analysis due; final standard specifications due. Neither is recovered, and no transmittal or acknowledgement of either has been found.** | **Gap** |
| Jul, Aug 1979 | Coordinated Western Union revisions: THP Revision 1 and TCP Revision 1 on 4 July; TCP Revision 2 on 3 August. | Contract specification |
| Sep 1979 | Cerf reports the standardization "progressing," names Lyons at DCEC as Executive Agent, and describes the remaining changes as mechanisms to pass security and precedence between application, TCP, and IP, an IP option already existing. | Status report, IEN 121 |
| Dec 1979 | IEN 123 and IEN 124, the first "DOD STANDARD" IP and TCP. IEN 124's preface: "This edition incorporates the addition of security, compartmentation, and precedence concepts into the TCP specification." | Specification |
| 15 Jan 1980 / Sept 1980 | IEEE received Lyons's manuscript in January; the September publication says gateway development remains. No submitted version is held to date that wording precisely. | Receipt date / published account by the Executive Agent |
| Jan 1980 | IEN 128 / RFC 760 and IEN 129 / RFC 761, the second try at the DoD Standard versions and the texts later ratified. | Specification |
| 8 Feb 1980 | Coordinated Western Union THP Revision 2 and TCP Revision 3, delivered under DCA200-C-637 to DCA Code 450. | Contract specification |
| **3 Apr 1980** | **Ratification, and implementation placed after AUTODIN II IOC. No reason stated.** | **Order** |
| May 1980 | Cerf reports IENs 128 and 129 "now stamped as DOD standards"; DCEC to coordinate within DoD. | Status report, IEN 145 |
| Jul 1980 | An OSD review group is established to review AUTODIN II, considering cost, security, performance, and survivability, and exploring alternatives because it appeared the system might not reach IOC. | Retrospective account, ADA127476 p. 3 |
| Jul 1981 | AUTODIN II reaches a partial IOC, testing continuing on some major components. | Retrospective account, ADA127476 p. 3 |

#### Published standard editions

**The published standard evolved after the intended April 1979 completion date.** The February 1979 TCP-4, IEN 81, lacks the security/precedence processing subsequently incorporated in the DoD Standard TCP text. The intervening [August 1979 IEN 112](https://history.rfc-editor.org/ien/ien112.txt), checked during validation, likewise lacks the later precedence/security sections. [IEN 124](https://history.rfc-editor.org/ien/ien124.txt), December 1979, announces those additions in its preface. This dates their incorporation into this standardization sequence, not their first appearance in any TCP specification: the earlier AUTODIN II and research branches already discussed them. The companion IEN 123 revises related IP features, and Cerf's September 1979 report says an IP option already existed.

Postel's February 1980 summary, IEN 134, identifies December's IENs 123/124 and January's IENs 128/129 as successive attempts at the DoD Standard versions. January's [RFC 761](https://www.rfc-editor.org/rfc/rfc761.txt) repeats IEN 124's preface statement. The April 1980 order ratified that January text, about a year after the original promulgation target. These dated texts establish a later published standardization sequence; they do not prove that no suitable working draft existed between the published editions, or that standards readiness caused AUTODIN II's after-IOC placement.

#### The contracted baseline

**The contracted AUTODIN II baseline was current and unreconciled at the decision point.** [AD-A081757](https://archive.org/download/DTIC_ADA081757/DTIC_ADA081757.pdf) is Western Union's *Computer Program Development Specification, Terminal-to-Host Protocol (THP)*, CDRL B006, document DIN II-F-623-13B06-1124, issued February 20, 1979, Revision 1 July 4, 1979, **Revision 2 February 8, 1980** &mdash; the same day as the TCP Revision 3 compared in [the Western Union record](tcp-versions-and-standardization.md#western-unions-february-1980-tcp-branch). Its DD Form 1473, PDF p. 6, gives report number DCA 200-C-637-P006, contract DCA200-C-637, and controlling office **Defense Communications Agency, ATTN: Code 450**. That is a different DCA office from the ones the protocol Management Plan assigns the Executive Agent role, Systems Engineering at Code 1000 and Operations and Readiness at Code 500. The contract baseline and the standards role sat in separate parts of the same agency.

Its reference list, printed p. 4 / PDF p. 12, inspected as an image, cites the TELNET specification and ARPANET Protocol Handbook, **both July 15, 1976 SRI specifications**, the **DCA System Performance Specification (Type A) for AUTODIN II Phase I**, Western Union Proposal #U-321-1 of April 1976, the WU AUTODIN II Design Plan and its Executive Summary, and the AUTODIN II TCP and SIP Transportable Specifications. No DoD standard TCP or IP document, no IEN, no RFC, and no reference to the December 1978 memorandum appears. The page carries a 21-FEB-79 footer and is **absent from Revision 2's list of changed pages**, PDF p. 7, so the list stood unrevised through both revisions. Read this carefully: an absent reference is not a statement of a reason, and non-revision may only reflect which pages the revision touched. What it establishes is that the deliverable baseline in force two months before ratification still took its normative ancestry from 1976 and named no DoD standard.

#### The Executive Agent’s account

**The Executive Agent's own contemporaneous account.** Robert E. Lyons of DCEC, named in IEN 121 as the Executive Agent, published ["A Total AUTODIN System Architecture"](https://zenodo.org/records/1281114/files/article.pdf?download=1) in *IEEE Transactions on Communications* COM-28(9), September 1980, pp. 1467-1471, manuscript received January 15, 1980 and presented in abbreviated form at the November 1979 Data Communications Symposium. At p. 1469 he writes that AUTODIN II subnetwork hosts such as WIN and SACDIN "will use the AUTODIN II standard SIP and will also be required to use the DoD standard TCP unless they can obtain a waiver from this requirement based on the lack of need to communicate with others beyond their own subnet community of interest," and that interoperability "is required that the subscribers of internetted systems use a common standard TCP and Internet Protocol (IP). DoD policy has recently been stated which requires DoD data network subscribers having requirements for interoperability to adhere to these standards. **What remains is for the gateways themselves to be developed and implemented.**" Three things follow. The published paper treats the DoD standard requirement as operative for AUTODIN II hosts with a waiver route. It names gateway development as outstanding work in this architecture account, without establishing the readiness of every host or the Western Union system. And he is silent on the AUTODIN II TCP's unsuitability, the ordered analysis, and any transition timing. The paper uses "standard TCP" for both families in adjacent sections. Its manuscript-received date does not prove that every sentence in the September publication was fixed in January; no submitted manuscript or revision history is held.

#### Transition claims and their basis

**Claims, and what each rests on.**

| Claim | Status | Basis and limit |
| --- | --- | --- |
| Cost and schedule impacts on the AUTODIN II program were the named grounds for leaving the timing open. | Documented | The order says so, four months before the analysis. It is a statement of the concern, not of a finding. |
| The April 1980 order defers implementation past IOC and gives no reason. | Documented | The clause itself. Silence on the face of an order is not evidence that no reason was recorded elsewhere. |
| The January 1980 specifications and April ratification followed the April 1979 target; December 1979 IEN 124 announces the TCP additions. | Documented | IEN 152 p. 3 against IEN 81, IEN 124, IEN 129, IEN 134, IEN 145. Concerns the standard, not AUTODIN II; nothing links it to the DCA decision. |
| The contracted baseline was current, actively revised, and unreconciled with the standard in February 1980. | Documented | AD-A081757, PDF pp. 6, 7, 12; the coordinated same-day TCP revision. Establishes the state of the baseline, not a cause. |
| Cost was the operative reason. | Hypothesis | The order asks for a cost tradeoff; the Task Force later records growing projected costs. No figure, analysis, or recommendation connects cost to the April decision, and the Task Force's cost account concerns 1981-82. |
| Protecting the IOC milestone was the operative reason. | Supported inference, not documented | The order expected FY 1980 operation, ties implementation to IOC, and says "as soon after" as possible, which reads as sequencing behind a milestone rather than abandoning the requirement; the DSB later records a two-year program stretched to four and a half. No contemporaneous document states it. |
| Technical infeasibility of the upgrade explains it. | Not established; existing host implementations weigh against a blanket infeasibility claim | IEN 76 in January 1979, IEN 121 in September 1979, and Lyons's September 1980 publication show relevant implementations or an intended standards path, without demonstrating an upgrade of the deployed contractor system. None of them speaks to the Western Union switch, SIP, CCU/TAC firmware, or the security kernel, none of which this pass examined. |
| Contractual commitment under DCA200-C-637 explains it. | Hypothesis | The CDRL baseline was maintained on the divergent branch to February 8, 1980 under Code 450. No contract modification, engineering change proposal, or cost proposal bearing on a protocol change was recovered. |
| Compatibility divergence explains it. | Not a cause | Divergence is the problem the upgrade was ordered to fix, not an explanation of the timing chosen to fix it. |
| The July 1980 OSD review group explains the April 1980 decision. | Excluded on chronology | It postdates the ratification by three months, and no document connects it to earlier work. It remains a lead for whether the deferral was revisited. |
| ADA100788 bears on the deferral. | Screened out | AFIT/GCS/EE/80D-9, Healy and Henderson, Air Force Institute of Technology, December 1980: a backbone simulation thesis on switch control module routing and queueing. Its OCR layer contains no occurrence of TCP, host-to-host, IOC, or protocol upgrade. |

#### Missing transition decision sources

**What is still missing.** The ordered analysis; minutes or papers of the OSD Protocol Standards Working Group from its December 1978 formation through April 1980 and of the PSTP, PSSG, and PCCB; any record stating a reason for the IOC placement; the Executive Agent Charter named in the April memorandum; and any contract modification under DCA200-C-637 touching the protocols. The September 14 continuation in [record schedules and SRI proposals](tcp-versions-and-standardization.md#dca-record-schedules-and-sri-contract-proposals) ran the two public routes this pass named, closed the AD-A081756 handle, and revised the list of remaining handles; read it before reopening any of them. **LTC Wilcox** and the **Director, Information Systems, OSD**, named in the December memorandum as the Working Group's point of contact and chairman, remain unpursued, and **IDA Paper P-1402**, Bartee, Buneman, Gardner, and Marcus, *Computer Internetting: C3I Data Communications Networks*, April 1979, cited by Lyons and dated in the month the analysis was due, remains unlocated after the bounded [IDA/NTIS pass](tcp-versions-and-standardization.md#ida-p-1402-citation-held-original-unrecovered).

### DCA record schedules and SRI contract proposals

The continuation of September 14, 2026 ran the two next actions the previous pass named, and, before either, the local leg that pass had defined but could not perform. It did not recover the ordered analysis or the panel minutes. It produced one substantial negative about where those records could survive, two dated contract documents that were not in this brief, and the completed identity of AD-A081756. Coverage, fingerprints, and access failures are in the [continuation record](../sources/records/nic-proposals-and-record-schedules.json).

**No dedicated Executive Agent series was identified in the searched schedules.** All **31** records disposition schedules NARA publishes for Record Group 371 were retrieved and searched; the previous pass had worked from one of them. The strings *Executive Agent*, *Protocol Standards*, *Technical Panel*, *Configuration Control Board*, *host-to-host*, *Defense Data Network* and *standard protocol* occur in none of the 31, and no file series describes protocol standardization or a DoD standard protocol. This is a reported search result for those 31 schedules and their searchable text layers, not proof that the function was unscheduled, that no relevant series existed under another heading, or that records were destroyed. A disposition schedule is not a holdings inventory. General series and records held by other offices remain possible routes. On September 19 all 31 PDFs were reacquired with matching fingerprints, ten malformed manifest URLs corrected, and the seven phrase searches above repeated over fresh full extracts with no hits. The retained text and selected visual checks support that bounded result, not absence under other terminology or a complete holdings survey.

The first is new to this brief. [NC1-371-81-01](https://www.archives.gov/records-mgmt/rcs/schedules/departments/department-of-defense/defense-agencies/rg-0371/nc1-371-81-01_sf115.pdf), Section LXXV, **ARPANET Files**, schedules series 875-01 through 875-19 for DCA's operational management of the ARPANET. Two are Permanent, to be offered to NARS in five-year blocks at twenty years: **875-02, ARPANET Sponsors Group Files**, a DCA-chaired body of ARPANET sponsors meeting "to provide advisory services, to include review and coordination of all actions affecting services rendered by the network," whose files include "the group charter announcements, agenda, minutes, group reports (when required), recommendations"; and **875-03, ARPANET Operational Management Files**, holding "policies, procedures, and standards for operation and maintenance of the ARPANET." The other seventeen series carry destruction instructions, including event-based disposal and periods up to ten years. Those instructions do not demonstrate that disposal occurred. So a permanent, minuted, DCA-chaired network body existed alongside protocol panels for which this search identified no dedicated series. It is an operations body and not the PSTP, and its relevance to the transition decision is untested.

The second is more likely to matter. [NC1-371-78-01](https://www.archives.gov/records-mgmt/rcs/schedules/departments/department-of-defense/defense-agencies/rg-0371/nc1-371-78-01_sf115.pdf), approved in February 1978, makes **203-01 Publications Record Set Files** permanent, one copy of each publication or change issued by a DCA activity, and **203-02 Publications Background Files** permanent, covering "studies, recommendations, comments, concurrences, and similar documents that provide a basis for the publication or that contribute to its content." If the **Executive Agent Charter** was issued as a DCA publication, a record-set copy and its background file were scheduled permanent even though this search identified no dedicated subject series. That is now the best scheduled route to the Charter.

One method result belongs with this. A filename probe found only 20 of the 31 schedules; the remaining eleven, including the 1978 publications schedule that carries the finding above, use prefixes no plausible pattern would generate. Use NARA's own record-group index page for any future sweep, not a constructed filename pattern.

**A proposal revision removes the NIC's AUTODIN II transition task.** The photographs of the CHM SRI collection, searched at content level for the first time across IMG_6460 to IMG_6649, turn out to hold two SRI proposals to DCA for the Network Information Center. The first, **Proposal for Research ECU 79-99 of 21 September 1979**, contains *Task 2, Production of a Protocol Locator*, whose 1,500 copies were to carry ARPANET, AUTODIN, NSW and internet protocols to "bona fide ARPANET, NSW, or AUTODIN II users," and *Task 5, Transition of Information Services from ARPANET to AUTODIN II*. An **ADDENDUM TO PROPOSAL ECU 79-99**, inspected as an image, opens: "As a result of the discussions held between representatives of Defense Communications Agency and SRI, this addendum revises Proposal ECU 79-99 in accordance with the following." It then deletes both tasks in their entirety and substitutes a sub-task providing online access to ARPANET and FTP protocols, with selection resting on "the NWG Coordinator or other DCA-appointed representative." The addendum bears no date on its face; the revised cost estimates filed with it are headed **5 November 1979**.

This is a revision of a NIC proposal following discussions with DCA. It deletes two proposed tasks and accompanies revised cost estimates; it is not an executed contract modification. The undated addendum is associated with sheets dated November 5, 1979, rather than independently dated to that day. It supports a change in the proposed work before the April 1980 ratification, with no reason stated. A budgetary explanation remains possible, but neither the eventual contract scope nor a causal connection to the protocol deferral is established.

**The two protocol families were still separate eight months after ratification.** The second proposal, **ECU 80-149 of 18 December 1980**, for the NIC contract year 1981, proposes a NIC Protocol Repository. Its Attachment 1, "Preliminary List of Protocols to be Maintained in the NIC Protocol Repository," inspected as an image, lists two families. Under **DoD Standard Protocols**: Transmission Control Protocol, Internet Protocol, File Transfer Protocol, Mail Service, Telenet/Terminal Handling Protocols, and ten more. Under **AUTODIN II Protocols**: Segment Interface Protocol, *Transmission Control Protocol (TCP)*, Mode VI Link Protocol, Terminal to Host Protocol (THP), and Terminal Access Controller (TAC) Link Protocols. The same proposal's optional tasks ask the NIC to support the DoD standard TCP and IP and to provide configuration management of "the DoD Standard Protocol Specifications (Type A)" under DoD-STD-480A, DCA-100-50-2 and MIL-STD-483, and its narrative offers to assist DCA "in a more formal approach to protocol standardization and configuration management." Eight months after ratification, the organization DCA paid to hold the official protocols still expected to hold two transmission control protocols under two headings. This is a contractor's preliminary list of documents, not a statement of DCA policy or of the transition schedule; as corroboration of continued divergence it is contemporaneous and dated, which the argument in [upgrade chronology](tcp-versions-and-standardization.md#the-upgrade-order-standard-editions-and-contracted-baseline) otherwise supports only from the Western Union baseline.

**Coverage and what this leg did not find.** 190 photographs were OCR'd, selected by densifying the neighbourhood where the existing every-twentieth sample showed AUTODIN and DCA material rather than by extending a uniform sample. AUTODIN occurs in 27 of them. *Tradeoff*, *trade-off*, *Executive Agent*, *Dinneen*, *DCEC*, *Lyons*, *cost analysis*, *minutes* and *DCA library* occur in none. The sample and contiguous pass overlap on nine images: together they give **325 distinct photographs with recorded OCR**, leaving **2,554** against the earlier 2,879-photo inventory. See [the manifest-based correction](../sources/coverage.md); these counts describe discovery coverage, not full visual reading.

**Access limits affect negative searches.** Some earlier local collection reads failed. Those failures do not establish absent content; only the documented successfully read subset supports a bounded negative.

**DTIC access was unavailable in this pass.** September 14 requests returned 403 on the recorded network paths; September 17 requests instead reached a maintenance page. These are dated access observations, not evidence of source absence or a permanent closure, and the later response does not explain the earlier failures.

### IDA P-1402: citation held, original unrecovered

[Batch B](../sources/records/ida-p1402-retrieval.json) completed on September 26, 2026 as a **documented retrieval failure**. IDA's homepage could not be fetched through the web tool; all four permitted site-restricted queries returned no entries. The NTIS control ADA035337 returned the expected 1976 SRI TCP record on its first attempt. The four actual field-scoped target searches returned two unrelated records for each report-number form and zero results for each title phrase. No relevant link or new accession emerged; no P-1402 PDF was recovered and no PDF page was screened. This is a bounded retrieval result, not proof of absence from IDA or NTIS holdings.

The [source record](../sources/records/ida-p1402-retrieval.json) and retained responses also disclose a method error: three initial target submissions populated the general search box instead of the field filter. Their broad, truncated results support no negative. The same three terms were corrected after the fourth query exposed the proper field-filter behavior; four actual field-scoped queries were completed, with those extra mistaken submissions retained rather than hidden. No additional query terms, general web/IA sweeps, adjacent-report retrievals or inquiries were added.

The title, authors, paper number and April 1979 date remain a citation in Lyons, printed p. 1471, reference 10. No original sponsor, tasking, accession, transmittal or recommendation is authenticated. Its date still cannot connect it to Dinneen's ordered analysis. The current `deferral` and `standard-sequence` qualifications stand; no change to a historical finding follows. A new accession-specific or readable-copy lead is needed before reopening this retrieval.

### The adjacent NIC leaves: execution unestablished

The [bounded SRI reading](../sources/records/sri-adjacent-contract-leaves.json) inspected **IMG_6650–6655 only** in the CHM photograph collection. The first four images contain NIC work and deliverable continuation leaves; the last two are alternate captures of a DD Form 1423 Contract Data Requirements List, page 1 of 8. They supply neither a dated title nor a contract identifier or signed approval. IMG_6652 specifies **1 March 1983** for Resource Handbook delivery. That is a deliverable target, not the document's issue date, and does not by itself establish when the work statement was prepared.

The full form in IMG_6655 leaves the contract/PR, contractor, prepared-by/date and approved-by/date fields blank. Its reporting requirements and references to DCA Code 252 do not establish execution. Repeated protocol-repository and configuration-control work is compatible with the earlier NIC proposals, but cannot identify this item with ECU 79-99 or ECU 80-149, equate their task numbers, or prove acceptance of either proposal. The initial six therefore did not meet the condition for reading IMG_6656–6669; those photographs were not opened. The `deferral` and `western-union` footnotes need no change. The applicable NIC contract and the after-IOC timing rationale remain unestablished.

### The July 1976 SRI specification: identity

The [complete public scan](https://s3.us-west-1.wasabisys.com/chm-cms-media/media-live/_file/bulkupload/102697649-05-0001.pdf) is **Jonathan B. Postel, Larry L. Garlick, and Raphael Rom, *Transmission Control Protocol Specification*, SRI, July 15, 1976**, final deliverable under DCA100-76-C-0034. Identification preceded substantive use: PDF p. 1 carries CHM accession 102697649; p. 2 gives the title, authors, date, and contract; the preface, printed p. i / PDF p. 3, identifies the final Type A TCP for AUTODIN II. Body headers bear July 11, 1976 and **35938**. The title and report number match the previously located DDN library entry **76-0947**.

This 182-page PDF includes a separately titled appendices part at PDF p. 114, also dated July 15, with internal headers July 12 and **35939**. TCP Appendix A occupies printed pp. A1-A3 / PDF pp. 115-117. It contains the same user/TCP/BSL address roles and mappings as THP Appendix A, printed pp. A1-A3 / PDF pp. 82-84, whose internal identifier is 35941. All six appendix pages were inspected in their original images. There are minor wording differences: THP explicitly says the layers are concealed from higher protocols, a phrase absent from TCP's introduction. **The earlier possible citation-mismatch warning is withdrawn: the older manuscript's TCP Appendix A attribution has direct support.** These are shared companion-specification contents, not independent corroborating accounts of a later design decision.

### The SRI requirements, controls, and interfaces

The following locators all refer to that TCP PDF. They identify specified behavior or implementation guidance, not an executed implementation.

| Topic | Original passage and significance |
| --- | --- |
| Service requirements | Printed p. 17 / PDF p. 26, sections 4.5-4.6: transfer should be independent of packet size, routes, and packet-switch configuration/control. Security, precedence, and closed user groups are called "unique DoD common user requirements." This explicitly connects the service destination to these controls. |
| Host and switch authorization | Pp. 18-20 / PDF pp. 27-29, sections 5.1-5.5: the switch handles subscriber eligibility and simplex traffic; TCP handles individual processes, connection consistency, and full-duplex relations. An OS-maintained authorization table supplies send/receive security ranges, maximum send precedence, permitted TCCs, and privileged controls. The host can impose tighter restrictions than the switch. These are complementary checks at different scopes. |
| Security levels | Pp. 19, 31, 82 / PDF pp. 28, 40, 91: sixteen levels; an absolute level or a ceiling; the two directions can differ. With a ceiling, successive letters may carry different permitted classifications, supplied with SEND. Do not reduce this to one immutable classification for an entire bidirectional connection or identify it with RFC 793's later rules. |
| Precedence | Pp. 19, 83 / PDF pp. 28, 92: sixteen levels; only the highest, Category I, is nonblocking in the packet-switch network and invokes TCP preemption. TCP tries to reconcile the two directions at the highest authorized level, but unequal levels can remain where authority limits prevent agreement. A direction's precedence is then constant for the life of the connection. P. 18 explains why acknowledgments should receive corresponding precedence. |
| Transmission control codes | Pp. 19-20 / PDF pp. 28-29: overlapping permitted communities are checked at subscriber and user levels. Appendix C, p. C1 / PDF p. 135, assigns an eight-bit TCC and redundant copy in the Binary Segment Leader (BSL). The BSL also holds four-bit security with a redundant copy and four-bit precedence plus the Category I indicator. These are network-leader fields, not an RFC 791 security-option format. |
| Application interface | Pp. 30-31 / PDF pp. 39-40, sections 7.1.6.3-4: OPEN takes socket and S/P/T constraints, checks process authority, and returns a local connection name. This OPEN records the request without sending traffic; SEND or INTERRUPT initiates synchronization. SEND includes letter boundaries and security. Administrative controls thus enter the application/transport interface, not just a packet header. |
| SIP interface and layering | P. 12 / PDF p. 21 distinguishes switch and TCP sequencing, acknowledgments, retransmission, and flow control. P. 36 / PDF p. 45, section 7.2, defines an event interface to SIP while avoiding assumptions about SIP's implementation mechanism for modularity. Host TCP multiplexes user processes over subscriber access. This is explicit layering, with reliability functions at several levels; it is not already the later TCP/IP split. |
| Resynchronization | P. 80 / PDF p. 89, section 9.1.2.4.12: a DSN control in the old sequence space is acknowledged before SYN establishes a new sequence number. Idle connections may need this to avoid the advancing forbidden sequence-number region. This mechanism belongs to the 1976 branch; it is not modern TCP connection recovery. |
| Preemption details | P. 92 / PDF p. 101, sections 9.5.3-4: Category I should recover buffers from lower-precedence traffic. Outgoing and retransmission queues are candidates; the original letter is requeued and resegmented, potentially producing duplicates for the peer to discard. The text expressly excludes preemption within process scheduling. This buffer procedure must be distinguished from BBN 3900's later proposal to abort a lower-priority connection and from the questionable preserved code path. |

The decisive pages in this table were read visually after text discovery. A complete machine-readable extraction is preserved, but no claim is made to a line-by-line reading of all 182 pages.

### Internetting and the SRI specification’s boundary

Appendix D's header diagram, figure D1 / PDF p. 138, places network/TCP addressing and fragmentation controls within the TCP format, below the BSL. Printed p. D4 / PDF p. 139 explicitly explains that internetting is omitted from the body's treatment but that its fields were retained to permit later addition without changing the header. P. D6 / PDF p. 141 says that if internetting is removed, the source/destination network and TCP address fields can be deleted because the BSL supplies the AUTODIN II TCP address; it similarly discusses dispensing with fragmentation controls under single-network assumptions. Both pages and the diagram were checked visually.

This qualifies a categorical assertion that the 1976 design had no internetwork conception. It also leaves the 1978 upgrade order intelligible: reserving fields for a future capability is different from implementing the subsequently standardized internetwork protocol. The specification's TCP/SIP boundary and its address-role distinctions are evidence of architectural work within AUTODIN II. Derivation of Postel's August 1977 split proposal from that experience remains unproven.

### Western Union’s February 1980 TCP branch

[Western Union, *Final Computer Program Development Specification: Transmission Control Program (TCP)*](https://nsarchive.gwu.edu/document/18318-national-security-archive-western-union), [complete 163-page scan](https://nsarchive.gwu.edu/sites/default/files/documents/5793287/National-Security-Archive-Western-Union.pdf), document **DIN II-F-622-13B06-1124**, CDRL B006, contract **DCA200-C-637**. The Chunk 2 pass established that this scan is also held publicly as **DTIC AD-A081756**, and that it has a same-day companion, **[AD-A081757](https://archive.org/download/DTIC_ADA081757/DTIC_ADA081757.pdf)**, the *Terminal-to-Host Protocol (THP)* specification, document **DIN II-F-623-13B06-1124**, same CDRL and contract, issued February 20, 1979, Revision 1 July 4, 1979, **Revision 2 February 8, 1980**. The two host protocols were therefore revised in lockstep on 4 July 1979 and 8 February 1980. The THP copy's DD Form 1473 gives report number DCA 200-C-637-P006 and controlling office **DCA Code 450**, and its reference list cites the 1976 SRI specifications and the DCA System Performance Specification but no DoD standard protocol document; see [upgrade chronology](tcp-versions-and-standardization.md#the-upgrade-order-standard-editions-and-contracted-baseline). The title / PDF p. 6 identifies the original issue as **March 5, 1979**, revision 1 as **July 4, 1979**, revision 2 as **August 3, 1979**, and revision 3 as **February 8, 1980**. The title and all three changed-page lists, PDF pp. 6-9, were inspected visually. Revision 3 lists Title, 10, 18, 30, B1, C1, C44, and D4. The scan retains earlier dates and revision footers on other pages. These lists identify replacement pages, but the earlier wording cannot be reconstructed without separate editions. **Revision 3 is a document revision, not a TCP protocol-version designation.** The September 14 continuation read the DTIC copy's own front matter. Its **DD Form 1473**, PDF p. 5, inspected as an image, gives report number **DCA 200-C-637-P005**, secondary number **AD-E100 342**, type FINAL, author and performing organization Western Union Telegraph Company, Government Systems Division, McLean, Virginia, controlling and monitoring office **Defense Communications Agency, ATTN: Code 450**, report date **8 Feb 80**, 155 pages, unclassified and approved for public release, with the DTIC stamp 7 MAR 80 and the keyword AUTODIN II. The TCP deliverable and the THP deliverable therefore match on every identifying particular: same contract, same controlling office, same delivery date, adjacent report numbers.

Printed p. 4 / PDF p. 13, the reference list, was inspected as an image in the September 14 continuation and is **absent from the Revision 3 list of changed pages**, so it stood unrevised from the March 5, 1979 original issue through 8 February 1980. It names ten documents: the NIC TELNET specification, the ARPANET Protocol Handbook, **both July 15, 1976 SRI specifications**, the DCA System Performance Specification (Type A) for AUTODIN II Phase I, a Western Union proposal of April 1976, the WU AUTODIN II Design Plan and its Executive Summary, and the AUTODIN II THP and SIP Transportable Specifications. No DoD standard protocol document, IEN, or RFC appears. This reproduces the THP result exactly, on the other half of the same coordinated delivery. Two small discrepancies between the two reference lists are preserved rather than harmonized: the Western Union proposal reads **WU-301-1** on the TCP page and was read as **#U-321-1** on the THP page, and the footers are 28-FEB-79 and 21-FEB-79 respectively. Both pages are poor microfiche reproductions, so at least one proposal-number reading is an artefact; settle it by re-inspecting AD-A081757 PDF p. 12 against the retained render at [supporting/chunk2b-2026-09-14/pages](../sources/README.md#reading-and-retrieval-records). Printed p. 3 / PDF p. 12 distinguishes the network TCP-TCP protocol from CCU/TAC event interfaces and MCCU implementation examples. This establishes a declared specification relationship and intended implementation setting. It does not identify a deployed build, prove source-code inheritance from SRI or BBN, or make the CCU/TAC system identical to Wingfield's EDN host implementation.

The following decisive pages were inspected as images. SRI locators are in [the specification record](tcp-versions-and-standardization.md#the-july-1976-sri-specification-identity); BBN locators are in [implementation and tests](implementation-and-tests.md#evidence).

| Aspect | Western Union specification and locator | Comparison and implication |
| --- | --- | --- |
| Addressing | One CCU network subscriber address, with ports demultiplexing host channels/users, p. 14 / PDF p. 23. Ports contain a static/dynamic bit, eleven User ID bits, and four function bits, p. 18 / PDF p. 27. Network fields are present but set to zero, A5 / PDF p. 55. | The SRI separation of subscriber/TCP/user roles persists in a concrete CCU mapping. Reserved network fields do not establish internetwork operation. BBN's added internet leader is a different adaptation. |
| Security | The connection uses one security value; a specified value must match the incoming SYN, or an unspecified value is accepted subject to authorization, pp. 18-20 / PDF pp. 27-29. | This narrows SRI's absolute-or-ceiling service and permitted per-letter variation. It resembles later fixed connection checks without establishing adoption from the research standard. |
| Precedence | Sending and receiving precedence can remain different. An unspecified sending value is limited by authorization; the higher directional value governs preemption, p. 20 / PDF p. 29. | This retains directional distinctions available in SRI and differs from the reconciled connection precedence specified by RFC 761 and later RFC 793. |
| Authorization | TCP checks requested S/P/T for the user, but does not validate the remote subscriber/port values at OPEN, p. 19 / PDF p. 28. The user identity is extracted from the port, p. 14. | The administrative requirement persists with CCU-specific identification. BBN instead documents a privileged authorization table and a host API. Matching fields, authorization, and remote identity validation are separate operations. |
| TCC | Page 18 specifies **512 codes**. Figure E1, E3 / PDF p. 161, allocates nine bits to each BSL TCC copy; event interfaces allocate sixteen bits, C28 and C55 / PDF pp. 97 and 126. Those event tables print range **0-512**. | This differs from the eight-bit TCC in SRI's 1976 BSL and the BBN host option. The stated count and inclusive event range are inconsistent; preserve that discrepancy instead of silently normalizing it. A sixteen-bit event parameter is not a sixteen-bit wire TCC. |
| Preemption | A higher-category authorized SYN can replace a preemptible established connection to an occupied local socket. Category I is protected. Resource exhaustion can also cause connection preemption, pp. 38-39 / PDF pp. 47-48. | This closes the old connection and establishes a new one. SRI's described buffer-recovery mechanism reclaims lower-precedence buffers; BBN separately proposes aborting lower-precedence connections. These are related policies with different mechanisms and evidence levels. |
| Resynchronization and error handling | The complete control definitions, A4 and A8 / PDF pp. 54 and 58, contain no DSN operation. A new, non-retransmitted SYN in an established connection produces an error and closure, p. 10 / PDF p. 19. | SRI's DSN procedure is not retained in this defined control repertoire. The replacement-page lists do not establish when it disappeared or why. Connection establishment must not be confused with SRI's resequencing of an existing connection. |
| TCP/SIP and header boundary | SIP extracts S/P/T from the BSL and passes them to TCP, p. 20. C55 specifies the reverse Send Data event. A1 / PDF p. 51 requires a fixed **29-byte TCP header**. A6 / PDF p. 56 and E3 say the CCU/TAC/NCC TCPs do **not use the checksum field**. | This continues a local event interface around a specific AUTODIN II format. BBN 3900 inserts an internet leader. RFC 761 layers TCP over IP and specifies a TCP checksum. Similar names conceal materially different responsibilities and formats. |

OPEN initializes state and SEND begins the handshake, p. 19, continuing the SRI pattern. The standard's active OPEN instead starts synchronization immediately. Together with the zero network fields, fixed header, and unused checksum, this makes Western Union's continuing branch concrete at the time of DoD standardization. These are specified behaviors; this batch did not recover Western Union execution evidence.

The immediate standards comparator is January 1980, not only September 1981. [RFC 760, p. 17](https://www.rfc-editor.org/rfc/rfc760.html), defines a four-octet security option with **two security bits and an eight-bit TCC**, while precedence is carried in the service octet. It explicitly supports carrying AUTODIN II security/TCC information across networks lacking corresponding leaders. BBN's four-octet option has a different allocation, including four-bit security and precedence. [RFC 761, sections 1.1, 2.9, 3.1, and 3.8](https://www.rfc-editor.org/rfc/rfc761.txt), specifies IP layering, checksums, authorization, and connection matching. RFC 791 subsequently changes the security option again, including a 24-bit TCC. These comparisons establish selected continuity across different encodings and policies, rather than an unchanged AUTODIN II protocol becoming the standard.

### IDA P-1402 retrieval coverage

**P-1402: completed retrieval coverage and remaining limit.** Lyons's complete paper, [printed p. 1471, reference 10](https://zenodo.org/records/1281114/files/article.pdf?download=1), cites T. C. Bartee, O. P. Buneman, K. A. Gardner, and M. J. Marcus, *Computer Internetting: C3I Data Communications Networks*, IDA Paper P-1402, April 1979. The citation is held; the original report's identity, sponsor, accession, scope, and relationship to Dinneen's tasking are not independently established. The [September 13 record](../sources/records/upgrade-order-and-standard-editions.json) records general web and IA coverage; the [September 14 continuation](../sources/records/nic-proposals-and-record-schedules.json) records three IA title/author queries and another general web query returning no copy. The [September 17 NTIS log](../sources/README.md#reading-and-retrieval-records) enumerates AUTODIN, Western Union, SRI-contract, and other targets, but no IDA/P-1402 report-number or title query. The [September 26 record](../sources/records/ida-p1402-retrieval.json) records the IDA access failure and four empty site-restricted queries, successful NTIS accession control, four actual field-scoped searches without a matching record, and three mistaken general-box submissions corrected without new terms. No report was recovered or screened. Do not repeat these routes without a concrete new accession or readable copy. Inquiries and paid/library access remain outside the assignment.

## Unresolved questions

**After-IOC transition timing.**

**Evidence that could change the account:** The ordered cost tradeoff analysis, transmittal or contemporaneous deliberations could explain the decision; advice favoring an earlier transition would complicate the chain. P-1402's April 1979 date does not identify it as that analysis. [Batch B](tcp-versions-and-standardization.md#ida-p-1402-retrieval-coverage) recovered no original or matching record. The [current NARA access check](../questions.md) reached the native catalogue without establishing the target holding, and verified College Park Textual Consultation for an unsent custody inquiry. Reopening needs a specific holding/original, not another reading of IEN 152 or the standard editions.

**Execution of NIC proposals.**

**Evidence that could change the account:** A signed, applicable modification could establish a contractual disposition. A different date, contract or task numbering would defeat the proposed connection; retention of work proposed for deletion would qualify it. Neither proves the later timing rationale. The [initial-six SRI check](../sources/coverage.md) found undated work/deliverable leaves and a form with blank contract and approval fields; it supplies no applicable executed instrument.

## Research question

**Question:** what explains placing AUTODIN II's transition to standard TCP/IP after initial operational capability?

Use the [tasking and standardization chronology](tcp-versions-and-standardization.md#the-upgrade-order-standard-editions-and-contracted-baseline), [NIC proposal evidence](tcp-versions-and-standardization.md#dca-record-schedules-and-sri-contract-proposals), and Western Union's distinct baseline. The ordered analysis concerned transition timing and was due April 1979. Western Union DCA200-C-637, SRI DCA100-76-C-0034 and BBN DCA100-78-C-0011 are distinct contracts. The 1976–78 CHM material is background unless an explicit later connection appears.

No continuation is selected. Consult [P-1402 retrieval coverage](../sources/coverage.md) before reopening; the [SRI initial-six check](../sources/coverage.md) did not establish applicable identity or execution. Stillman/DeFiore, the Executive Agent Charter, panel proceedings and an executed NIC modification are leads, not assignments. ADA100788 was screened as a routing/queueing thesis; AD-A081756 identity and the standard editions have been checked. A new result must distinguish tasking, delivered analysis, recommendation, ratification and implementation, allowing advice contrary to the chosen timing.
