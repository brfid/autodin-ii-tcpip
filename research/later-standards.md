# Later standards and the persistence of military controls

[Research overview](../research.md) · [Open questions](../questions.md) · [Sources](../sources/README.md)

This notebook records persistence and modification of military controls in later standards, alongside the implementation and routing limits. Standards presence is distinct from general implementation or deployment. Its standards account reflects the cited documents and recorded readings; this reorganization adds no new verification.

Read the [findings and limits](later-standards.md#findings-and-limits), the [supporting evidence](later-standards.md#evidence), or the [unresolved questions](later-standards.md#unresolved-questions). Recorded reading boundaries are in the [reading guide](../sources/coverage.md).

## Findings and limits

### The late-1980s Internet needed additional machinery for routing autonomy and policy

**Assessment.** Directly established.

**Evidence.** RFCs 1092, 1093, and 1105.

## Evidence

- [AUTODIN II provisions in the final IP specification](later-standards.md#autodin-ii-provisions-in-the-final-ip-specification)
- [Standards presence and implementation](later-standards.md#standards-presence-and-implementation)
- [Military controls in 1980s standards](later-standards.md#military-controls-in-1980s-standards)
- [The dated BBN distribution as a control](later-standards.md#the-dated-bbn-distribution-as-a-control)
- [What the recovered baseline establishes](later-standards.md#what-the-recovered-baseline-establishes)
- [Later changes to precedence handling](later-standards.md#later-changes-to-precedence-handling)
- [Later standards and compatibility](later-standards.md#later-standards-and-compatibility)
- [Architectural interpretation and limits](later-standards.md#architectural-interpretation-and-limits)

### AUTODIN II provisions in the final IP specification

[RFC 791, Internet Protocol, September 1981](https://www.rfc-editor.org/rfc/rfc791.html), especially pp. 12 and 16-18.

Its type-of-service discussion names AUTODIN II alongside ARPANET, SATNET, and PRNET as networks for which service mappings are supplied. Its security option carries classification, compartmentation, user-group, and handling information compatible with DoD requirements. This is a useful public source showing defense requirements in the standardized protocol, while the list of several networks also argues against exclusivity. These labels and controls are not the same thing as encryption or a complete security architecture.

### Standards presence and implementation

The strongest attribution is to **security and precedence requirements and their associated access controls**. IEN 40, p. 1, explicitly connects the added fields to AUTODIN II; IEN 98, p. 3, explicitly identifies security, precedence, and TCC in Wingfield's implementation. Those two original page images were rechecked for this follow-up. Together with the code findings above, they support a requirement-level lineage into the 1981 specifications. The September 11 inspection of SRI TCP 35938/35939 supplies the original fields and processing rules. It demonstrates changes of encoding and behavior as well as continuity of requirements; source-code descent and sole invention remain separate questions.

### Military controls in 1980s standards

| Requirement or mechanism | Evidence in the standardized protocols | What the evidence establishes |
| --- | --- | --- |
| Ranked traffic precedence | [RFC 791, p. 12](https://www.rfc-editor.org/rfc/rfc791.html#page-12) assigns three bits to precedence, including Routine, Priority, Immediate, Flash, Flash Override, and CRITIC/ECP. [RFC 1122, section 3.2.1.6](https://www.rfc-editor.org/rfc/rfc1122.html#page-33), October 1989, still identifies precedence with DoD applications and directs vendors to DCA for guidance. | A concrete defense service hierarchy remained represented in IP through the late 1980s. This does not establish that every network implemented its scheduling or preemption implications. |
| Classification, compartmentation, and handling labels | [RFC 791, pp. 17-18](https://www.rfc-editor.org/rfc/rfc791.html#page-17) defines the security option. [RFC 1038](https://www.rfc-editor.org/rfc/rfc1038.html), January 1988, publishes an approved draft revision intended for MIL-STD 1777, introducing a different representation based on classification and protection authorities. | Security labeling continued to be developed after AUTODIN II's cancellation. Its format changed. These labels do not themselves encrypt data. |
| Controlled communities of interest | RFC 791, p. 18, includes a 24-bit Transmission Control Code for traffic segregation and subscriber communities, with values assigned through DCA. IEN 98 identifies TCC among the AUTODIN II features. | A particularly specific administrative requirement reached the IP specification. The 1981 TCC field must not be equated with Wingfield's one-byte TCC or presumed to survive unchanged in later options. |
| Host authorization and per-connection consistency | [RFC 793, sections 2.9, 3.6, and 3.8](https://www.rfc-editor.org/rfc/rfc793.html) makes security and precedence part of connection handling. Its OPEN interface checks the caller's authority; connection establishment and segment processing include matching and reset rules. Section 2.9 explicitly allows implementations limited to unclassified or single-level use. | These requirements affected the transport interface and conditions for accepting communications. The earlier BBN authorization code provides a contemporary implementation counterpart, without establishing direct code inheritance into other stacks. |

RFC 1122 also says the particular link-layer service mappings referenced by RFC 791, in RFC 795, were obsolete by 1989 and should not be implemented. Thus the presence of the precedence field through the decade does not imply persistence of the original AUTODIN II service mapping.

### The dated BBN distribution as a control

Added September 12, 2026 from the Chunk 3 pass. The table above reads survival from the standards. One contemporary implementation is now traced, and it shows how far apart the two questions were already in 1981.

RFC 791 was published in September 1981. Two months later, the BBN TCP/IP 3.0 beta test distribution of November 24, 1981 carries neither of its relevant mechanisms in interpreted form. Outgoing IP options are an application-supplied byte string passed through unverified, the manual page saying so in terms; the service octet carrying IP precedence is never written on output; incoming options are stripped from every datagram before any protocol sees them, with the option loop present in the source but commented out; and the service octet is overwritten on input with a reassembly flag. The connection structure has no security, precedence, compartment, or TCC field, and no open can fail for a security, precedence, or TCC reason. The full trace, locators, and limits are in [Chunk 3](implementation-and-tests.md#the-1979-and-november-1981-authorization-paths).

Three cautions on how far this carries. It is one beta distribution on one machine class, from the DARPA-funded VAX reference implementation rather than the DCA AUTODIN II contract. The 1979 BBN code's own authorization was off by default, so the contrast is between a mechanism that existed and could be switched on and a mechanism that is not there. And the deferral was announced in advance: IEN 168 of January 1981 says precedence and security levels will be supported while placing IP option processing in a later stage of development.

What it does support is the distinction this file already draws, with an early dated instance. RFC 1108's later acknowledgement of limited implementation, and RFC 1122's 1989 restatement of precedence as a DoD concern with vendors referred to DCA for guidance, describe a gap that is visible in code within two months of RFC 791. Requirement-level lineage into the 1981 specifications, which the sections above establish from IEN 40 and IEN 98, is therefore not evidence of implementation prevalence, and should not be written as if it were.

### What the recovered baseline establishes

- **Encoding changed:** the 1976 BSL has four-bit precedence, four-bit security and an eight-bit TCC, with redundancy fields (C1). The preserved BBN IP option packs S/P/T into two value bytes. RFC 791 instead uses three precedence bits in the service octet and an eleven-octet security option containing security, compartments, handling restrictions, and a 24-bit TCC. These are related requirements in different formats.
- **Connection policy changed too:** SRI pp. 31, 82-83 permit security ceilings and, when authorization prevents equalization, unequal directional precedence. [RFC 793, section 3.6](https://www.rfc-editor.org/rfc/rfc793.html#section-3.6) specifies matching security/compartment values and reconciled precedence. The 2000 conflict concerns those later TCP rules; do not project them unchanged back onto 1976.
- **Some mechanisms disappeared before the 1980s standard:** the DSN resynchronization of SRI p. 80 was revised in IEN 5 and removed in TCP-3 in favor of a quiet period. BBN 3900 pp. 9-10 explicitly selects among AUTODIN user commands when adapting TCP-4. Neither Category I buffer recovery nor the BBN connection-abort design is established as a universal RFC 793 preemption algorithm.
- **TCC needs its own endpoint in the history:** the named 24-bit TCC is present in RFC 791. The replacement basic option in [RFC 1108, sections 2.1-2.4](https://www.rfc-editor.org/rfc/rfc1108.html) represents classification and protection authorities rather than retaining that dedicated TCC field. This is continuation of labeling/controlled distribution with a changed schema, not evidence that today's CIPSO/CALIPSO carries the original TCC unchanged. RFC 1108, section 2.7.3 (p. 11), also explicitly recognizes limited implementation/use, especially on unclassified networks. Standards presence and operational prevalence were already different questions in 1991.

### Later changes to precedence handling

[RFC 2873, June 2000](https://www.rfc-editor.org/rfc/rfc2873.html), supplies an especially useful continuation of the account's argument. The old TCP rules treated precedence as something the endpoints had to reconcile and keep consistent over a connection. Differentiated Services allowed intermediate nodes to change packet markings. The RFC explains how that could prevent a connection from opening or cause it to reset in an implementation enforcing the old rules. It directs TCP to ignore received precedence when establishing and maintaining connections.

This establishes an identified incompatibility and a standards response. It is not a measurement of how frequently the failure occurred or which commercial stacks exhibited it. The AUTODIN II connection is the historical synthesis across IEN 40/IEN 98 and the later standards; RFC 2873 itself does not attribute its problem to AUTODIN II. It nevertheless provides a more direct requirement-to-conflict sequence than the still-unproven AUTODIN II ancestry of the 1986 KI-111 interface problem.

### Later standards and compatibility

- **Generalized precedence:** [RFC 2474, sections 4.2.2 and 4.3](https://www.rfc-editor.org/rfc/rfc2474.html#section-4.2.2) redefined the IPv4 service octet and IPv6 Traffic Class for Differentiated Services. Its Class Selector codepoints preserve compatibility with earlier IP Precedence. The [current IANA DSCP registry](https://www.iana.org/assignments/dscp-registry) still lists CS0 through CS7. This is an explicit compatibility lineage; contemporary Diffserv service policies cannot be described as unchanged AUTODIN II military precedence rules.
- **Specialized security labeling:** [RFC 7126, section 4.12.2](https://www.rfc-editor.org/rfc/rfc7126.html#section-4.12.2) traces the replacement of RFC 791's security option through RFC 1038 to RFC 1108. The [current TCP specification, RFC 9293, Appendix A.1.2](https://www.rfc-editor.org/rfc/rfc9293.html#appendix-A.1.2), notes RFC 1108's Historic status while recognizing CIPSO and IPv6 CALIPSO. [Linux's NetLabel documentation](https://docs.kernel.org/netlabel/cipso_ipv4.html) describes an actual CIPSO engine applying and validating packet labels. This supports continuing implementation of the labeling tradition, not universal use or unchanged AUTODIN II formats.
- **Different treatment of transport checks:** [RFC 9293, Appendix A.1](https://www.rfc-editor.org/rfc/rfc9293.html#appendix-A.1) incorporates the removal of the old precedence logic. It permits non-MLS implementations to ignore security/compartment references, while directing MLS implementers to [RFC 5570, section 7.3.1](https://www.rfc-editor.org/rfc/rfc5570.html#section-7.3.1). That document corrects an older TCP assumption by including a sensitivity label in the identification of an MLS connection. Security support therefore survives with specialized and revised processing.

RFC 5570, section 10, also supplies an explicit later provenance link: CALIPSO derives from Mike StJohns's circa-1992 "Son of IPSO" draft, adapted for IPv6. That helps connect successive labeling designs. The recovered 1976 BSL and the 1981 IP option now establish different early representations of the related requirements. This follow-up checked standards and publicly maintained implementation documentation, not current military deployment or runtime behavior on this Mac.

### Architectural interpretation and limits

A defensible interpretation is that AUTODIN II helped make administratively assigned precedence, security classifications, and controlled subscriber communities part of the services TCP/IP could express and enforce. The 1980s specifications carried these concerns into packet formats, host authorization, and connection processing. Later development produced three outcomes: generalization, specialized continuation, and removal of conflicting behavior. This interpretation complements the DDN transition: a canceled procurement destination could leave requirements embedded in shared protocols.

The **general options mechanism** is a secondary candidate. IEN 40 expressly says the research version's options field accommodated security and priority alongside speech and diagnostic features. This supports describing extensibility as one way of reconciling requirements from overlapping projects. It does not establish that AUTODIN II alone caused the options mechanism or that today's TCP options descend from Wingfield's particular IP option.

Keep preemption separate from precedence marking: the existing code review found defects in the attempted preemption path, and DDN switch plans are not evidence for a universal TCP preemption algorithm. The AUTODIN II resynchronization mechanism was replaced and then removed during the early version history. No new evidence here attributes the reliable byte stream, retransmission, fragmentation, urgent pointer, TCP/IP split, or later routing architecture specifically to AUTODIN II.

For an article, the strongest concrete sequence is the AUTODIN II requirement, the 1981 TCP connection rule, and the 2000 response to its conflict with Diffserv, with the 1989 host requirements and current TCP appendix marking the intervening and present positions. The 1976 baseline is now inspected. The remaining gaps concern intervening revisions, implementation coverage, and operational use, rather than the existence or contents of that baseline.

## Unresolved questions

The cited standards and one dated code distribution do not establish source-specific deployment or the reasons for changing controls. A fuller technical or deployment history remains separate from this research; see [reserved topics](../research.md#further-work).
