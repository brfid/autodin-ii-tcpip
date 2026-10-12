# The intended defense service and ARPANET plans

[Research overview](../research.md) · [Open questions](../questions.md) · [Sources](../sources/README.md)

This notebook establishes the intended service, conditional ARPANET plans, concurrent research and operational commitments, and limits on retrospective interpretation. Plans and contemporary reports remain distinct from completed migration or a documented funding strategy.

Read the [findings and limits](service-and-arpanet-plans.md#findings-and-limits), the [supporting evidence](service-and-arpanet-plans.md#evidence), or the [unresolved questions](service-and-arpanet-plans.md#unresolved-questions). Recorded reading boundaries are in the [reading guide](../sources/coverage.md).

## Findings and limits

### AUTODIN II figured in plans to replace ARPANET's long-haul service

**Assessment.** Directly established as a plan, not a completed migration.

**Evidence.** IEN 65, printed p. 14; ARPANET Newsletter 1, July 1980.

### Early gateway routing was designed with a much smaller expected population than the later Internet

**Assessment.** Directly established for the IEN 30 routing design. This is not a TCP/IP hard limit.

**Evidence.** IEN 30, pp. 7-8.

### Separate institutional control was absent from 1978 gateway design

**Assessment.** Contradicted as a general claim.

**Evidence.** IEN 30, pp. 9-10 and 14.

### AUTODIN II alone caused the early routing architecture or the later AS architecture

**Assessment.** Not established by this review.

**Evidence.** Temporal overlap and technical compatibility are insufficient evidence of exclusive causation.

## Evidence

- [Program chronology and institutional context](service-and-arpanet-plans.md#program-chronology-and-institutional-context)
- [Cerf’s July 1976 access-equipment study](service-and-arpanet-plans.md#cerfs-july-1976-access-equipment-study)
- [Plans for ARPANET’s long-distance service](service-and-arpanet-plans.md#plans-for-arpanets-long-distance-service)
- [Early gateway scale and institutional plurality](service-and-arpanet-plans.md#early-gateway-scale-and-institutional-plurality)
- [Concurrent research and operational use before cancellation](service-and-arpanet-plans.md#concurrent-research-and-operational-use-before-cancellation)
- [Late-1980s routing and policy](service-and-arpanet-plans.md#late-1980s-routing-and-policy)
- [Origins and retrospective interpretations](service-and-arpanet-plans.md#origins-and-retrospective-interpretations)

### Program chronology and institutional context

The [source record](../sources/records/program-chronology-source-checks.json) preserves the chronology sources, retrieval limits and exact visual coverage.

- **Early research and implementation:** RFC 675, December 1974, specifies an internetwork TCP. RFC 694, June 18, 1975, TCP entry, printed p. 10, reports under May 30 that BBN's implementation was running at BBN-TENEXA, while Stanford's was being debugged and UCL's coded. IEN 151, April 1, 1980, pp. 1–2, dates the Stanford contract to July 1973–September 1976 and describes BBN's earlier participation. These sources establish early implementations and collaboration; they do not rank TCP against every competing approach or establish a 1976 transfer of previously independent BBN work into a newly created program.
- **Availability and adoption:** Cerf's Internet Society participant account identifies both public-domain and commercial implementations in the 1980s. Leiner et al.'s 1997 participant history describes BBN, Berkeley, and BSD distribution. RFC 801, November 1981, pp. 2–3, supplies the planned January 1, 1983 ARPANET transition deadline. Open specifications, free implementations, operating-system licensing, and government adoption requirements should not be collapsed into a single claim that the entire system was given away.
- **Wider design setting:** Cerf and Kahn's May 1974 paper, conclusion, acknowledgments, and references, explicitly identifies contributions by participants in British and French networking and cites ARPANET, CYCLADES, and British designs. PDF pp. 12–13 of the retained 13-page Princeton-hosted reprint were inspected visually. Its pagination is not the journal's printed pp. 637–648. This supports the design conversation, not a feature-by-feature attribution to each project.
- **AUTODIN II's status and dates:** DSB report AD-A127476, printed p. 3 / PDF p. 11, visually checked, dates the undertaking to 1976 after a 1975 study and reports partial initial operational capability in July 1981, with major-component testing continuing. The opening's “never lived” formulation was too absolute. Earlier committee and BBN records still establish planning in 1975. The December 23, 1978 upgrade order and April 2, 1982 termination remain distinct events.
- **ARPANET and its users:** IEN 65, printed p. 14 / PDF p. 19, visually rechecked, supplies the July 1977 regional-cluster proposal. ANEWS-1, July 1, 1980, opening and “Access Policy,” anticipates some subscriber transfers from 1983, includes residual ARPANET and commercial networks, and directs users with no ARPANET communication requirement toward commercial service. It does not establish a blanket removal of civilian university or contractor users. RFC 827, October 1982, §1, pp. 1–3, describes the ARPANET/SATNET core gateway system; RFC 820, January 1983, p. 11, assigns AS 1 to the BBN gateways, not to the ARPANET switching backbone alone.
- **DDN plan authorship:** The retained program plan's foreword, p. iii, and p. 1 were visually rechecked. They identify DCA's September 1981 tasking and a joint DCA/CCTC and industry team. BBN's foundational ARPANET work does not make the plan solely a BBN proposal.
- **Present standards:** RFC 9293, August 2022, Appendix A.1–A.1.2, and RFC 2474, December 1998, §§4.2.1–4.2.2, distinguish obsolete TCP precedence processing from Class Selector compatibility. The opening's surviving “shades” refer to requirements and compatibility history, not unchanged AUTODIN II behavior in general Internet use.

### Cerf’s July 1976 access-equipment study

Vinton G. Cerf, *SCCU/MCCU Characteristics for AUTODIN II*, Technical Note 92, July 1976; body revised July 10, 1976. Title/abstract PDF p. 2; introduction printed p. 1 / PDF p. 3. Both checked visually.

[Cerf's SCCU/MCCU report](https://archive.org/download/DTIC_ADA037214/DTIC_ADA037214.pdf)

The report estimates interfaces that let existing hosts connect to AUTODIN II with little alteration. The proposed components include SIP, TCP, and a host-specific interface. The abstract says ARPANET internetting research supplies its basis, and the introduction describes prototypes connected to ARPANET and packet radio.

This supports a concrete AUTODIN II engineering destination. It also shows why an exclusive origin story is misleading: earlier internetting work was being applied to that destination. The presence of prototypes on ARPANET is not evidence of completed AUTODIN II deployment.

### Plans for ARPANET’s long-distance service

Jon Postel, *TCP Meeting Notes, 14 & 15 July 1977*, IEN 65, notes timestamped August 5, 1977; printed p. 14 / local PDF p. 19, visually checked.

[IEN 65](https://www.rfc-editor.org/ien/ien65.pdf)

The minutes attribute to Cerf a plan to replace ARPANET's cross-country sections with AUTODIN II, retaining regional ARPANETs connected through gateways. This is strong evidence of the intended infrastructure around which research was being discussed. Postel's introductory note also warns that the minutes may incompletely or inaccurately report speakers; describe the passage as the minutes' account of Cerf's proposal.

The July 1, 1980 *ARPANET Newsletter*, ANEWS-1, independently describes future subscriber transfers to AUTODIN II and an ARPANET II virtual network using AUTODIN II, residual ARPANET, and commercial networks. Its technical section announces replacement of NCP by DoD TCP/IP.

[ARPANET Newsletter 1](https://ftp.ripe.net/rfc/museum/ddn-news/ddn-news.n1.1)

The commercial-network component matters: even this defense-led plan cannot be reduced to an exclusively military set of physical networks. Also keep its projection of about 100 ARPANET **nodes** separate from IEN 30's expectation of fewer than 100 **networks**.

### Early gateway scale and institutional plurality

Virginia Strazisar and Radia Perlman, *Gateway Routing: An Implementation Specification*, IEN 30, 1978. Printed/PDF pp. 7-10 and 14 are the relevant passages; pp. 7, 8, 10, and 14 were checked visually.

[IEN 30](https://www.rfc-editor.org/ien/ien30.pdf)

Pages 7-8 expect fewer than 100 networks because new networks are expensive to develop. That estimate informs the proposed routing algorithm; the authors explicitly allow operation outside that range while saying substantially different sizes might have led to another strategy. It is not a 100-network field-size limit, and it is not a statement that TCP or IP inherently cannot scale.

Pages 9-10 reject a centralized routing control scheme. They describe networks and gateways under different organizations with different goals, and favor a distributed algorithm that lets each organization manage its gateways. Page 14 makes separate control a reason to support dynamic addition of gateways.

The limitation relevant to the later Internet is more precise: p. 14, footnote 6, says different adaptive routing algorithms in the same catenet cannot guarantee proper delivery because their interactions can create undetectable loops. Multiple organizations already existed in the design; safe routing between domains with different internal algorithms remained a problem. This distinction is a stronger route into the later autonomous-system story than a claim that one institution necessarily controlled everything.

### Concurrent research and operational use before cancellation

BBN proposal P82-CSY-10, *Internet Systems: Maintenance and Development*, **July 1981**, submitted to DARPA. The proposal number does not make it a 1982 document.

[Dated cover](../sources/unique/bbn-internet-proposal-1981/bbn-internet-proposal-1981-capture-01.jpg), [introduction, p. 1](../sources/unique/bbn-internet-proposal-1981/bbn-internet-proposal-1981-capture-02.jpg). Both checked visually.

The introduction says Internet protocols were being implemented in both military and research operational environments. The research community itself depended on the Internet as an operational communications medium while continuing to investigate the communications system. Later passages propose better gateway maintenance, monitoring, and separation of operational use from experiments, with feedback to and from the ARPANET Routing Study contract; those passages were read in OCR and should be checked visually before quotation.

This establishes overlapping development and use before the replacement decision. It is a proposal describing the working environment and seeking further work; it does not prove that all proposed improvements were delivered or that AUTODIN II caused each operational difficulty.

The Chunk 4 pass sharpens the date's significance. The Director of DCA tasked the two design teams in September 1981, so this July 1981 proposal describes concurrent research and operational Internet use before the reassessment began, not merely before the April 1982 cancellation. The recommendation that produced that cancellation, and the modeling that supported both design teams, are recorded in [DSB report](ddn-selection.md#the-defense-science-board-task-force-report) and [DCEC modeling account](ddn-selection.md#dcecs-fly-off-modeling-account) below.

### Late-1980s routing and policy

[RFC 827, Exterior Gateway Protocol, October 1982](https://www.rfc-editor.org/rfc/rfc827.html), introduction, pp. 1-6, identifies the costs of having diverse gateways participate in one common routing algorithm and proposes autonomous systems with private internal protocols. Its near-term design uses a core and stubs, while its discussion also anticipates coequal systems. EGP should not be presented as already solving all later interdomain routing problems.

[RFC 1092, EGP and Policy Based Routing in the New NSFNET Backbone, February 1989](https://www.rfc-editor.org/rfc/rfc1092.html), pp. 1-3, supplies a concrete contemporary contrast: redundant regional paths, problems with EGP's tree model, autonomy and trust, and rules determining which regional networks may advertise a destination. Its proposed policy machinery includes agreements and a routing-policy database. It treats EGP as an interim solution.

[RFC 1093, The NSFNET Routing Architecture, February 1989](https://www.rfc-editor.org/rfc/rfc1093.html), pp. 1-2, describes NSFNET's relationships with regional networks and peer backbones, including ARPANET and NASA's network, and the use of filtering and distinct trust relationships. The late-1980s Internet still had backbones and hierarchies; it was not a flat network of equal peers.

[RFC 1105, A Border Gateway Protocol, June 1989](https://www.rfc-editor.org/rfc/rfc1105.html), p. 1, explicitly builds on EGP and NSFNET experience and exchanges AS-path information for loop avoidance and policy decisions. It reports implementations for Cisco routers and NSFNET switching systems. This establishes a design and specific implementations, not universal deployment by 1989.

Together these sources support an argument about additional technical and institutional construction. They do not support portraying the 1990s commercial Internet or the Web as already complete in the late 1980s.

### Origins and retrospective interpretations

[RFC 675, December 1974](https://www.rfc-editor.org/rfc/rfc675.html), pp. 1-3, already specifies internetwork TCP and gateways. Cerf's [IEN 151 final report](https://history.rfc-editor.org/ien/ien151.txt), April 1, 1980, p. 1, visually checked, locates the Stanford effort in 1973-76 and identifies the 1976 AUTODIN II specification as an intermediate version. These are evidence against an exclusive original-purpose claim.

David Clark's [1988 design-philosophy paper](https://groups.csail.mit.edu/ana/Publications/PubPDFs/The design philosophy of the DARPA internet protocols.pdf), pp. 106-107 and 110, is a useful participant retrospective. It explicitly discusses military priorities, but also describes integrating separately administered networks as an ambition. It supports the importance of changing priorities; it does not identify AUTODIN II as the exclusive origin. Contemporaneous specifications should carry more weight for the precise scope of a 1970s design.

## Unresolved questions

The cited ARPANET plans do not establish completed migration, exclusive protocol purpose, or a funding strategy. A broader account of origins, funding, or later commercial effects requires its own question and evidence.
