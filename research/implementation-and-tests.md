# Implementation and test evidence

[Research overview](../research.md) · [Open questions](../questions.md) · [Sources](../sources/README.md)

This notebook separates implementation reports, preserved static source, proposed experiments, and reported test results. The dated BBN comparison is bounded to the inspected distributions; it establishes neither runtime behavior nor general deployment or a policy to remove controls.

Read the [findings and limits](implementation-and-tests.md#findings-and-limits), the [supporting evidence](implementation-and-tests.md#evidence), or the [unresolved questions](implementation-and-tests.md#unresolved-questions). Recorded reading boundaries are in the [reading guide](../sources/coverage.md).

## Findings and limits

### TCP implementations and related applications were being built for AUTODIN II

**Assessment.** Directly established, with differing implementation stages.

**Evidence.** Cerf's 1976 SCCU/MCCU note; IEN 68, pp. 5-6; IEN 76, p. 1.

### Preserved BBN source contains executable logic for the AUTODIN II features described by Wingfield

**Assessment.** Established by static source inspection and the contemporary implementation report. Runtime behavior remains unchecked, and the snapshot is still not tied to a particular dated build; the comparison version is now identified, which the earlier entry left open.

**Evidence.** IEN 98, pp. 2-3; local BBN `auth.c`, `psipin.c`, `psipout.c`, and `tcp.c`.

### A dated 1980s BBN distribution retains the security/precedence authorization path

**Assessment.** Contradicted by the source. The November 24, 1981 BBN TCP/IP 3.0 beta test distribution has no authorization table, no security, precedence, compartment, or TCC field in its connection structure, no check on receipt, and no unauthorized failure value; outgoing IP options are passed through unverified and incoming options are stripped, with the option loop commented out. Established for this distribution only, and not as a decision or a policy.

**Evidence.** `tape1-files` LABEL; `bbnnet/con.h`, `netuser.c`, `ip_output.c`, `ip_input.c`, `tcp_input.c`, `tcp.h`; `include/errno.h`; `doc/net.5.n`.

### The 1981 absence was a deliberate removal of an AUTODIN II requirement

**Assessment.** Not established, and the one contemporary statement points the other way: IEN 168 of January 1981 says precedence and security levels will be supported and defers IP option processing to a later stage. The intermediate connection structure carrying precedence, security level, and compartment is documented on the tape and not held.

**Evidence.** IEN 168, section 2.1.2; `doc/net.5.P`, struct included from `/usr/src/sys.4/h/con.h`, which is not on the tape.

### DTI combined a research TCP version with access controls from the AUTODIN II specification

**Assessment.** Explicit in its May 1978 program design, which also names the responsible routines. This is design documentation, not recovered DTI code.

**Evidence.** DTI, *INFE Program Design Specifications*, p. 7 and pp. 11-12.

### AUTODIN II-associated host controls were exercised in an implementation

**Assessment.** Reported EDN TCP test results include security, precedence, and TCC checks, with an input-truncation exception. Separate test logs are missing from this copy.

**Evidence.** BBN 3664, August 1979, pp. 1-3, 13-15, C-1, F-1/G-1.

## Evidence

- [Implementation reports in the TCP meeting minutes](implementation-and-tests.md#implementation-reports-in-the-tcp-meeting-minutes)
- [December 1978 incompatibility and accommodation](implementation-and-tests.md#december-1978-incompatibility-and-accommodation)
- [Wingfield’s contemporary implementation report](implementation-and-tests.md#wingfields-contemporary-implementation-report)
- [Mechanisms in the preserved early BBN source](implementation-and-tests.md#mechanisms-in-the-preserved-early-bbn-source)
- [Early specifications as comparison targets](implementation-and-tests.md#early-specifications-as-comparison-targets)
- [DTI’s front-end program design](implementation-and-tests.md#dtis-front-end-program-design)
- [Code provenance and comparison boundaries](implementation-and-tests.md#code-provenance-and-comparison-boundaries)
- [The 1979 and November 1981 authorization paths](implementation-and-tests.md#the-1979-and-november-1981-authorization-paths)
- [BBN 3900: a documented adaptation of TCP-4](implementation-and-tests.md#bbn-3900-a-documented-adaptation-of-tcp-4)
- [BBN 3664: reported TCP results on the EDN](implementation-and-tests.md#bbn-3664-reported-tcp-results-on-the-edn)
- [BBN 4129: the proposed host-to-switch experiment](implementation-and-tests.md#bbn-4129-the-proposed-host-to-switch-experiment)
- [BBN 4471: AUTODIN II FTP software over experimental facilities](implementation-and-tests.md#bbn-4471-autodin-ii-ftp-software-over-experimental-facilities)
- [Subsequent progress reports as a control on attribution](implementation-and-tests.md#subsequent-progress-reports-as-a-control-on-attribution)
- [BBN source availability and test records](implementation-and-tests.md#bbn-source-availability-and-test-records)

### Implementation reports in the TCP meeting minutes

Jon Postel, *TCP Meeting Notes, 15 & 16 June 1978*, IEN 68, dated June 27, 1978, printed/PDF pp. 5-6; p. 5 visually checked, p. 6 read in extracted text.

[IEN 68](https://www.rfc-editor.org/ien/ien68.pdf)

Mike Wingfield's BBN project planned to use TCP-4 with AUTODIN II security and precedence features and to implement terminal-to-host and file-transfer protocols. Gary Grossman's DTI report describes a front end for WWMCCS hosts and terminals connecting to AUTODIN II. Its TCP-3 implementation was working but still awaited integration and final debugging; the report describes extra internet-header octets to simulate AUTODIN II security and precedence.

IEN 76, *Internet Meeting Notes*, January 1979, p. 1, further reports a DCEC-sponsored Unix TCP-4 implementation compatible with AUTODIN II security, precedence, and user-group requirements, while noting that preemption remained to be added. This corroborates ongoing development, not universal or finished deployment.

[IEN 76](https://www.rfc-editor.org/ien/ien76.pdf)

### December 1978 incompatibility and accommodation

Jon Postel, *Internet Meeting Notes*, IEN 70, December 1978, printed/PDF p. 2, visually checked.

[IEN 70](../sources/unique/ien70-1978.pdf)

Gary Grossman's DTI implementation is reported as unable to interact with the TCP-4 implementations because it uses version 3 and has AUTODIN II security features. On the same page, Mike Wingfield's BBN TCP-4 for the Experimental Data Network carries AUTODIN II security features in the internet-header options field and is ready for testing against the others.

The juxtaposition is useful: specific version and feature combinations produced incompatibility, while another implementation sought accommodation within the newer format. The report attributes the DTI mismatch to both version and security features; it does not isolate the independent effect of each. Read this alongside the December standardization memorandum, rather than treating all implementations called TCP as interchangeable.

### Wingfield’s contemporary implementation report

Jon Postel et al., *TCP Implementation Status*, IEN 98, May 3, 1979, contains Michael A. Wingfield's BBN Unix report on printed pp. 2-3, local PDF pp. 3-4. Both complete pages were inspected visually.

[Local IEN 98](https://history.rfc-editor.org/ien/ien98.txt)

Wingfield identifies DCA contract DCA100-78-C-0011, C on a PDP-11 with Unix and BBN IPC additions, and completion since March 15, 1979. He explicitly identifies AUTODIN II security, precedence, and TCC features from the SRI TCP report. He also reports file transfers between Unix systems on ARPANET and RCCNET, availability at BBN-Unix and EDN-Unix, and a gateway test facility that deliberately damages or loses packets. This places the same project within both operational requirements and internetwork testing. It does not establish which authorization setting was used for any particular transfer.

The implementation name in the sources is Wingfield.

### Mechanisms in the preserved early BBN source

The code inspected is the BBN PDP-11 C TCP distribution identified by its accompanying description as coming from Noel Chiappa. The description attributes most TCP code to Wingfield, with possible assistance from Jon Dreyer. Its public counterpart is the [TUHS BBN-V6 collection](https://www.tuhs.org/cgi-bin/utree.pl?file=BBN-V6).

- [Local distribution description](../sources/README.md#bbn-source-distributions)
- [Preserved archive](../sources/README.md#bbn-source-distributions)
- [Extracted source tree](https://www.tuhs.org/cgi-bin/utree.pl?file=BBN-V6)

The inspected source files and accompanying `doc/tcp` were compared byte for byte with their entries in `jnc_bbn.tar.gz`; they match. The archive SHA-256 is `00f1b98bdabc60429622b410b46fb52748bc1d08d226de898e67b635cd999365`. Individual fingerprints and archive-member paths are in the code-evidence index linked below. This establishes that the local inspection used unchanged archived files. It does not establish that this snapshot is precisely the March 15, 1979 build, or that it is identical to the separately preserved UCLA printout.

| Mechanism | Exact source locator | Historical evidence |
| --- | --- | --- |
| Application-facing connection controls | [tcpstru.h, line 194](https://www.tuhs.org/cgi-bin/utree.pl?file=BBN-V6/tcp/tcpstru.h#194), `MOpen`, lines 194-209 | Opening a connection includes `SendPrec`, `RecvPrec`, `MaxSecur`, `AbsSecur`, `NumbTcc`, and `OTcc`. The requirements affect the application interface, not just packet labels. |
| Authorization against a user table | [auth.c, line 4](https://www.tuhs.org/cgi-bin/utree.pl?file=BBN-V6/tcp/auth.c#4), `Authorize`, lines 4-209; `GetFields`, line 239 onward | The routine checks security ranges, limits requested send precedence, and checks TCC membership against `authtable`. Invalid requests can return `EUNAUTH`. `tcp.c`, lines 1013-1029, calls it using the user identity supplied by the IPC port header and handles refusal. |
| An Internet option carrying security, precedence, and TCC | [psipout.c, line 253](https://www.tuhs.org/cgi-bin/utree.pl?file=BBN-V6/tcp/psipout.c#253), lines 253-265; [tcp.c, line 1227](https://www.tuhs.org/cgi-bin/utree.pl?file=BBN-V6/tcp/tcp.c#1227) | `OPTSPT` is 2, the option length is 4, security occupies the low four bits of its value byte, precedence the high four bits, and TCC the next byte. The incoming parser reverses this packing. This is a specific wire-format feature to compare with specification revisions. |
| Mandatory option under authorization | [psipin.c, line 182](https://www.tuhs.org/cgi-bin/utree.pl?file=BBN-V6/tcp/psipin.c#182), lines 182-213 | With `Auth == 1`, an incoming segment without the S/P/T option returns immediately and is ignored. This gives an explicit mechanism by which compatible TCP endpoints could still face an additional acceptance requirement. |
| Incoming connection policy checks | [psipin.c, line 265](https://www.tuhs.org/cgi-bin/utree.pl?file=BBN-V6/tcp/psipin.c#265), lines 265-311 | After matching the connection, authorization mode validates incoming security, precedence, and TCC. An unacceptable value cancels the match. |
| Configurable enforcement | [tcp.c, line 153](https://www.tuhs.org/cgi-bin/utree.pl?file=BBN-V6/tcp/tcp.c#153), lines 153-180 | `Auth` defaults to zero and is read from the third command-line argument. The enforcement behavior is configurable within the same program. This alone does not identify a particular setting as "research mode" or prove why the switch was introduced. |

The most compact possible code exhibit is the missing-option check, within the `Auth == 1` block of `psipin.c`, lines 199-201:

```c
      if (SptOpt == 0)
      {  return(2);    /* ignore segment */
       }
```

Read it together with the option parser, the enclosing authorization condition, and IEN 98. The historical force comes from that chain: named AUTODIN II requirements, a documented implementation, and source that makes those requirements conditions of acceptance. The code supports the argument that the projects' requirements had to be accommodated within protocol processing. Calling the switch a deliberate response to a specific compatibility incident would require another source.

These are findings from static inspection. There are apparent defects in the preserved snapshot. For example, the attempted precedence-based preemption loop in `tcp.c`, lines 953-989, does not advance its traversal pointer, and its comparison does not match the comment about selecting the lowest precedence. Treat this as a lead for checking the original listing and other revisions, not proof that preemption worked. Do not silently repair historical code and then attribute the repaired behavior to the original implementation.

Two reading traps also matter. `TCPVERNO` is defined as 6 but is assigned to the Internet `Protocol` field; it is the TCP protocol identifier, not evidence of "TCP version 6." Also, the four-byte `OPTSPT` format is not automatically identical to the security option eventually standardized in RFC 791. Verify the applicable specification before claiming format continuity.

### Early specifications as comparison targets

[TCP version 3, IEN 21, January 1978](https://www.rfc-editor.org/ien/ien21.pdf), preface printed p. iii / PDF p. 4, attributes the added security and priority fields to AUTODIN II and distinguishes its resynchronization mechanism from the research version's. It then describes a broader options mechanism and the removal of resynchronization in version 3 in favor of a quiet period. This page was checked in the original image-only copy. Together with [IEN 5 and IEN 40](tcp-versions-and-standardization.md#evidence), it provides a feature-level comparison plan: trace fixed fields, option formats, acceptance checks, and connection recovery separately.

The same local TCP-3 copy, printed p. 62 / PDF p. 67, explicitly lists Secure Open and Secure Close options for the BCR security system, kinds 102 and 103 **in octal**. The whole page was inspected. These are useful comparison targets for code associated with the parallel end-to-end security research. Their existence must not be folded into AUTODIN II attribution simply because they involve security. No implementation of these BCR-specific options was located or validated in this follow-up.

The July 15, 1976 SRI specification cited by IEN 98 and DTI is recovered and examined in the [SRI specification record](tcp-versions-and-standardization.md#the-july-1976-sri-specification-identity). Its BSL fields and detailed processing rules establish a comparison baseline; they do not make the preserved BBN IP option an identical encoding.

### DTI’s front-end program design

Steven F. Holmgren, David C. Healy, and David A. Willcox, *INFE Program Design Specifications*, Document 6, May 15, 1978, DTIC accession ADA060668. The local filename is [unix autodin frontend.pdf](https://archive.org/download/DTIC_ADA060668/DTIC_ADA060668.pdf). The cover at PDF p. 3 and printed pp. 7, 11-12 / PDF pp. 14, 18-19 were inspected visually.

Page 7 specifies TCP version 3, January 1978, together with connection access controls from the July 15, 1976 SRI specification. It anticipates modifying the module again when a final AUTODIN II specification becomes available. This is an unusually explicit description of combining a moving research specification with an existing operational requirement.

Pages 11-12 identify `NET_SECURITY` and `U_SECURITY` as routines implementing or enforcing AUTODIN II security, precedence, and transmission control code conventions. They also name `NETIN`, `NET_TCB`, `USER_IN`, `OPARAM`, and `OPEN_ITT`, giving precise search terms for a recovered DTI tree. The current evidence is a program design document. The DTI routines themselves were not recovered or inspected here. Keep this implementation distinct from the BBN code above and from the NCP Unix code also present in the local Unix collection.

### Code provenance and comparison boundaries

The current [UCLA finding aid for the Michael Allen Wingfield papers](https://oac.cdlib.org/findaid/ark:/13030/c8t1592t), Collection 2327, confirms a series containing TCP/IP Unix source printouts. A useful next step is to compare that printout and Ruizendaal's transcription with the Noel Chiappa/TUHS distribution inspected here. Preserve the distinct provenance of each copy.

A later BBN distribution is also already local: [the VAX Unix distribution description](../sources/README.md#bbn-source-distributions) and [tape1.tgz](../sources/README.md#bbn-source-distributions). It is not an audited continuation of Wingfield's source, and it belongs to a different sponsor and machine class. The [authorization comparison](implementation-and-tests.md#the-1979-and-november-1981-authorization-paths) identifies it from the archive's own label, traces the authorization path through it, and states what it does and does not establish.

The completed code comparison is a narrow trace of one requirement: who supplies a connection's security/precedence/TCC values, who authorizes them, how they are encoded, and what happens when a peer omits or violates them. The `Auth` and S/P/T paths offer a manageable exhibit, and that trace is recorded for both identified versions in the [authorization comparison](implementation-and-tests.md#the-1979-and-november-1981-authorization-paths). Runtime questions remain separate; historical execution is outside the authorized scope of these research chunks.

### The 1979 and November 1981 authorization paths

This subsection records the Chunk 3 pass of September 12, 2026. Its question was how security/precedence authorization at connection opening changed between the inspected early BBN implementation and a dated 1980s distribution, following TCC where it participates in the same path. No compilation, emulation, or execution was performed.

**The dated distribution's release identity, established from the archive's own documentation.** The local `tape1.tgz` contains a file named `LABEL`, which transcribes the physical tape label:

```
BBN TCP/IP3.0 BETA-TEST Distribution
1600 BPI	File 1 - Tar of /usr/src/sys
		File 2 - Tar of /usr/netsrc

November 24, 1981		#4
```

Three qualifications travel with that. `LABEL` itself carries the archive timestamp 1992-11-30, so it is a preservation-era transcription of the label, not a 1981 file. The accompanying `tape1.txt` is a modern secondary description; the release string and the date above come from the archive, and "BBN TCP/IP 3.0 beta test, November 24, 1981" is the identification this file should use. And the distribution is a beta, which is a statement about its own completeness.

Two internal controls agree with the label. The kernel change log `tape1-files/history` runs from 30 Nov 79 to 11 Aug 81 across tree generations sys.2 to sys.5, and dates the networking work directly: "vmu4.1.test rfg 5 Jan 81 Added TCP network code to kernel" and "vmu4.3.tcp rfg 2 March 81 first production tcp kernel." File timestamps inside the archive run from 1981-05 to 1981-11, the latest being `bbnnet/ip_input.c` at 1981-11-20, four days before the label date.

**One directory on the tape is not from the tape.** `bbnnet-oct82` carries its own README saying "This directory was not on the original beta distribution tape," attributing it to the Stanford AI Laboratory online archives, and all 31 of its files carry the uniform timestamp 1982-10-07. It is separately provenanced and is excluded from the comparison below; it is noted as the next lead instead.

**The archive is already extracted and the extraction is faithful.** `tape1-files` is a byte-identical extraction of `tape1.tgz`: a recursive comparison of all 740 files reported no differences. Nothing was re-extracted into the tree, and the inspection copy was made in scratch space. Archive SHA-256 `82b968169c70f8672779ecef33d56683c00b24f59a1403d25e65baeb25f44ff8`.

**The design document names the deferral in advance.** [IEN 168](https://history.rfc-editor.org/ien/ien168.txt), Robert F. Gurwitz, BBN, *VAX-UNIX Networking Support Project Implementation Description*, January 1981, is the design document the archive description points to, and it describes this system: "The implementation is designed for the VAX, running VM/UNIX, the modified version of UNIX 32/V developed at the University of California, Berkeley." Its section 2.1.2 states the intention, "Thus, on the TCP level, features such as the flow control mechanism (windows), precedence, and security levels will be supported," and in the same section defers the mechanism that would carry them: "it is anticipated that some of these features (such as handling IP gateway-host routing updates, and IP option processing) will be implemented in later stages of development, after more basic features (such as TCP flow control and IP fragmentation/reassembly) are debugged." Its section 2.2.2 describes the user interface the code implements, "In the case of open, for example, use of the call's mode field will be extended to accommodate a pointer to a parameter structure."

**Source locators for the 1981 column.** All paths are under [tape1-files](../sources/README.md#bbn-source-distributions): [LABEL](../sources/extracts/bbn-vax-1981/LABEL.txt), [history](../sources/extracts/bbn-vax-1981/history.txt), [conf/files](../sources/extracts/bbn-vax-1981/conf/files.txt), [include/con.h](../sources/extracts/bbn-vax-1981/include/con.h.txt), [include/errno.h](../sources/extracts/bbn-vax-1981/include/errno.h.txt), [doc/net.5.n](../sources/extracts/bbn-vax-1981/doc/net.5.n.txt), [doc/net.5.P](../sources/extracts/bbn-vax-1981/doc/net.5.P.txt), and in [bbnnet](../sources/README.md#bbn-source-distributions): [con.h](../sources/extracts/bbn-vax-1981/bbnnet/con.h.txt), [ip.h](../sources/extracts/bbn-vax-1981/bbnnet/ip.h.txt), [tcp.h](../sources/extracts/bbn-vax-1981/bbnnet/tcp.h.txt), [netuser.c](../sources/extracts/bbn-vax-1981/bbnnet/netuser.c.txt), [ip_input.c](../sources/extracts/bbn-vax-1981/bbnnet/ip_input.c.txt), [ip_output.c](../sources/extracts/bbn-vax-1981/bbnnet/ip_output.c.txt), [tcp_input.c](../sources/extracts/bbn-vax-1981/bbnnet/tcp_input.c.txt), [tcp_prim.c](../sources/extracts/bbn-vax-1981/bbnnet/tcp_prim.c.txt). Per-file sizes, timestamps, and SHA-256 values are in the code evidence index.

**The traced path, in both identified versions.** The early column is the BBN PDP-11 C TCP already recorded above, which runs as a user-level daemon. The 1981 column is the tape's `bbnnet`, which is kernel source compiled into the system (`conf/files`, fourteen `optional bbnnet` entries).

| Step | 1979 BBN PDP-11 daemon | November 1981 BBN TCP/IP 3.0 beta |
| --- | --- | --- |
| Caller identity | `tcp.c`, lines 1013-1029, passes `PortHdr.RealUserID` to `Authorize` | Not consulted for these attributes. `netopen` has the calling process (`netuser.c`, line 88) and uses its pid only to seed a unique local port (line 237). `suser()` is applied in the same ioctl switch to other commands (`netuser.c`, lines 736, 765, 824) and is not applied to options |
| Requested attributes at open | `struct MOpen`, `tcpstru.h`, lines 194-209: `SendPrec`, `RecvPrec`, `MaxSecur`, `AbsSecur`, `NumbTcc`, `OTcc[]` | `struct con` has no security, precedence, compartment, or TCC field (`include/con.h`; `bbnnet/con.h`). `netopen` reads mode, buffer counts, raw link or protocol range, timeout, ports, and addresses only (`netuser.c`, lines 29-197) |
| Authorization | `Authorize`, `auth.c`, lines 4-209, with `GetFields` from line 239 reading a per-user record from the file `authtable`: security ceiling and floor in each direction, a maximum send precedence, and a TCC membership list | No authorization table exists anywhere in the distribution, and no per-user attribute record is read. IP options enter through the `NETTCPOPT` ioctl as an opaque string of at most 40 bytes, copied to `t_opts`/`t_optlen` without inspection (`netuser.c`, lines 788-820). The distribution's own manual page says so: "The options are specified in the Internet Protocol description, and are sent as is, with no verification" (`doc/net.5.n`, NETTCPOPT) |
| Outgoing encoding | `psipout.c`, lines 253-265, with the option kind and length set in `tcp.c`, lines 1227-1229: `OPTSPT` is 2, length 4, security in the low four bits of the value byte, precedence in the high four, TCC in the next byte | `ip_output`, lines 45-62, copies the caller's option string verbatim behind the fixed header and sets `ip_hl` accordingly. It never sets `ip_tos`, and no file in the tape's own source assigns `ip_tos` at all (the single assignment anywhere in the bundle is in the separately provenanced October 1982 copy), so the service octet that carries RFC 791 precedence is not written on output |
| Incoming checks | `psipin.c`, lines 151-180, parse the option into `SptOpt`, `InSec`, `InPrec`, `InTcc`; lines 182-213, under `Auth == 1`, ignore a segment with no such option; lines 265-311 cancel an otherwise successful TCB match on an out-of-range security level, an out-of-range receive precedence, or a TCC outside the connection's list | None. `ip_input`, line 80, overwrites the service octet with the more-fragments boolean before dispatch (`ip.h`: `#define ip_mff ip_tos`), and `ip_opt`, lines 365-396, strips every option from the header for every protocol, TCP, GGP, ICMP, and raw IP alike (called at lines 97 and 251). `tcp_input`, lines 85-110, matches on local port, foreign port, and source address only. `tcp_opt`, `tcp_prim.c`, lines 425-455, handles end-of-list, no-op, and maximum segment size |
| Failure behavior | `EUNAUTH` or `EBADPARAM` returned to the user through `CmdOut(Handle, OERR, ...)`, `tcp.c`, lines 1015-1027; incoming failures drop the segment silently | The network error set has no unauthorized value: `ENETSTAT`, `ENETDOWN`, `ENETCON`, `ENETBUF`, `ENETPARM`, `ENETRNG`, `ENETDED`, `ENETERR`, `ENETREF`, `ENETUNR`, `ENETTIM` (`include/errno.h`, lines 43-54). No open can fail for a security, precedence, or TCC reason |
| Defaults and conditional support | `Auth` defaults to 0 and is set from the third command-line argument (`tcp.c`, lines 153-180); independently corroborated by BBN 3664, Appendix C, p. C-1 | No equivalent switch. The only conditional is the disabled block below |

**Disabled code, which is not the same as absence.** The incoming option loop is present in the source and commented out, and the live path removes the options instead. `bbnnet/ip_input.c`, lines 375-397:

```c
	if ((i = hlen - sizeof(struct ip)) > 0) {       /* any options */

/*      *** IP OPTION PROCESSING ***

		while (i > 0)

			switch (*q++) {
			case 0:
			case 1:
				i--;
				break;

			default:
				i -= *q;
				q += *q;
			}
*/              q += i;
		m = dtom(q);
		len = (int)m + m->m_off + m->m_len - (int)q;
		bcopy((caddr_t)q, (caddr_t)p, len);    /* remove options */
		m->m_len -= i;
	}
```

Note what the commented block would and would not have done. It is an option walker with no case for the security option and no check of any kind; even enabled it would only have skipped options rather than acting on them. It is evidence of a deferred mechanism, in the exact place IEN 168 said the mechanism was deferred, not of an authorization feature that was switched off.

**Documentation that outran the code, and the one unresolved identity.** The tape's formatted manual page includes its structure definition by reference, `.so /usr/src/sys.4/h/con.h` (`doc/net.5.n`), and the formatted copy on the tape therefore prints a `struct con` that the tape's own headers do not have:

```
            unsigned char c_prec;           /* precedence */
     #define c_lo c_prec                     /* low raw link or proto # */
            unsigned char c_sec;            /* security level */
     #define c_hi c_sec                      /* hi raw link or proto # */
            unsigned char c_compt;          /* compartment */
```

That is precedence, classification, and compartment, the shape of the RFC 791 security option, rather than the four-bit security and precedence and one-byte TCC of the earlier `OPTSPT` encoding. In the shipped `include/con.h` and `bbnnet/con.h` the two aliased slots have become `c_lo` and `c_hi` outright, `c_compt` is gone, and `c_mode` has widened from `char` to `short`, absorbing the freed byte.

A renamed symbol does not establish removal, so the test applied was whether the slots are still carried into the connection. They are not. `c_lo` and `c_hi` reach only `raw_range` for IP and raw connections (`netuser.c`, line 179); the TCP open path ignores them; and `struct tcb` holds no security, precedence, or TCC field at all, only `t_opts` and `t_optlen` (`bbnnet/tcp.h`). The manual page's prose likewise describes `c_hi` and `c_lo` only as a protocol or link range and never mentions precedence, security, or compartments.

What is not established is when the change happened. `/usr/src/sys.4/h/con.h` is not on the tape, only the sys.5 tree is, so the printed page is evidence that a sys.4 header had those fields, not evidence of the date they left. The formatted page carries the archive timestamp 1981-10-26 and the footer "Printed 9/1/81"; neither dates the header it included. Record this as unresolved identity rather than as a dated transition.

**Conclusions, separated by kind.**

- **Retained requirement.** None of the AUTODIN II-derived mechanisms survives in executable form in this distribution. What survives is a general carrier: an arbitrary IP option string, applied to outgoing segments of one connection, with the length limit the only rule enforced.
- **Revised implementation.** The same requirement's transport changed completely. In 1979 the values were requested at open, checked against a per-user table, clamped, stored in the connection, encoded by the protocol code itself, and required on every incoming segment. In 1981 the values, if sent at all, are composed by the application, passed through unverified, and never read on receipt by anyone.
- **Disabled code.** Incoming IP option processing exists as a commented-out block, with the live path removing options instead.
- **Unresolved identity.** The intermediate `sys.4` connection structure with precedence, security level, and compartment is documented on the tape and not held; the point at which the AUTODIN II encoding gave way to an RFC 791-shaped triple, and the point at which that triple gave way to nothing, are both outside the held versions.
- **A structural observation, offered as interpretation.** The implementation moved from a user-level daemon that could open a file to kernel code whose only identity primitive in this path is `suser()`. That is a plausible reason why a per-user attribute table did not come across, and the source does not state a reason. Do not present it as one.

**Limits on what this comparison can carry.** This is one beta distribution, for one machine class, from the DARPA-funded VAX reference implementation described in IEN 168, not from the DCA AUTODIN II contract that produced the 1979 code. Their sponsorship is different, and the 1979 code's own authorization was off by default. The comparison establishes what this distribution does; it does not establish a decision to drop the requirement, a policy, or the behavior of operational defense hosts in the 1980s. A failed text search establishes nothing on its own, so each conclusion above rests on the open path, the connection structure, and the dispatch path being traced end to end.

**Next leads, if this is reopened.** The October 1982 SAIL copy bundled beside the tape is the nearest later version and has its own provenance to check. The UCLA Wingfield printout remains the comparison for the 1979 side. `/usr/src/sys.4/h/con.h` is the exact missing artifact for the intermediate structure.

### BBN 3900: a documented adaptation of TCP-4

Michael A. Wingfield, [*TCP/PSIP Protocol Development Report*, August 1, 1978](../sources/unique/bbn3900-1978.pdf), DCA100-78-C-0011. The cover/title abbreviates the title to *TCP/PSIP Development Report*; the documentation page supplies the fuller form and date. This is the report cited by BBN 3664 as its implementation description, despite that report's shorter title. PDF p. 2 and printed pp. 8-10, 53-55 / PDF pp. 12-14, 57-59 were inspected visually.

P. 8 says the old AUTODIN specification has performance limitations and protocol ambiguities, while later TCP versions address internetting and fragmentation more fully. It explicitly proposes a cross between TCP-4 and AUTODIN TCP, incorporating IEN 44, with TCP-4 as the baseline and retained AUTODIN security and precedence. This corroborates the adaptation described in IEN 70 without proving every promised compatibility property.

Pp. 9-10 make the selection concrete: add the per-user authorization table, S/P/T parameters, connection MOVE, and STOP/RESUME; discard Retract Receive Buffers as unsuitable for Unix/RAND ports; replace FLUSH and INTERRUPT with TCP-4's Urgent mechanism. Nonblocking traffic may obtain resources by aborting a lower-priority connection under load. These are design commitments expressed in future tense. They neither demonstrate successful preemption nor establish AUTODIN II as the origin of Urgent or general flow control.

Pp. 53-55 explain why EDN tests need careful description. ARPANET-style IMPs substitute for AUTODIN switches. PSIP maps their messages to the form expected by TCP and is designed to be replaceable by SIP. One proposed mode removes the Internet Leader for single-network tests and reconstructs it on receipt; another retains that leader, removes the redundant BSL, and permits gateway experiments and communication with research TCP-4. The latter can carry S/P/T across a network lacking corresponding transport-leader fields. This is direct evidence of modular adaptation and two intended uses. It does not establish which filter was selected in every subsequent test.

### BBN 3664: reported TCP results on the EDN

Joanne Levin, *TCP Test Report*, August 1979, DCA100-78-C-0011. Source: [the 3664 photograph folder](../sources/README.md#reading-and-retrieval-records). Its 92 photographs were processed for discovery. The introduction, results, functional-test discussion, and implementation material below were read, with decisive pages checked visually.

| Locator | Reported result or limit |
| --- | --- |
| [introduction](../sources/unique/bbn-3664/bbn-3664-p1.jpg) | P. 1: TCP tests used three Unix hosts on DCEC's EDN, expanded here as Exploratory Data Communications Network; IEN 70 and the DDN plan use Experimental Data Network. The author reports all legal commands and many illegal ones, including illegal security, precedence, and TCC practices, were exercised. P. 2, [results](../sources/unique/bbn-3664/bbn-3664-p2.jpg), reports correct operation under the tested conditions based on log analysis. This moves the evidence beyond specification and static source inspection. |
| [test configuration](../sources/unique/bbn-3664/bbn-3664-p6.jpg) | P. 6: three H316 IMPs, standard ARPANET protocol and 64-kbit/s links, Unix V6 with RAND-port additions; NCP, Telnet, and FTP were disabled during TCP testing. This is an experimental substrate, not an AUTODIN II backbone acceptance test. |
| [functional tests](../sources/unique/bbn-3664/bbn-3664-p14.jpg) | P. 14: OPEN modes, CLOSE, ABORT, MOVE, STATUS, SEND/RECEIVE, STOP/RESUME, URGENT, and abnormal conditions. Multiple concurrent connections were exercised. P. 13, [authorization-table details](../sources/unique/bbn-3664/bbn-3664-p13.jpg), prints the per-user security-range, precedence, and TCC table used by the implementation. |
| [TCC exception](../sources/unique/bbn-3664/bbn-3664-p15.jpg) | P. 15, F1.4e: a requested TCC greater than 255 was truncated modulo 256 at the one-byte user/TCP interface, allowing a connection where the plan expected rejection. This is an explicit qualification to the broad success statement. It does not establish that TCP accepted a TCC outside the user's authorized membership after truncation. |
| [performance summary](../sources/unique/bbn-3664/bbn-3664-p3.jpg) | P. 3: the highest total bandwidth reported for any host was 22 kilobits/s on the PDP-11/70. Per-connection bandwidth declined with additional connections. This measures that host/software/test arrangement, not the capacity of the planned AUTODIN II network. |
| [startup options](../sources/unique/bbn-3664/bbn-3664-pC-1.jpg) | Appendix C, p. C-1: startup argument three enables or disables S/P/T checking, and defaults to zero. This independently corroborates the preserved source's configurable authorization. It does not prove why the option was introduced or the setting for each measurement. |
| [functional-log cover](../sources/unique/bbn-3664/bbn-3664-pF-1.jpg) | Appendix F, p. F-1, and G, p. G-1, [performance-log cover](../sources/unique/bbn-3664/bbn-3664-pG-1.jpg), say their functional and performance log files are "Bound under separate cover." Those logs are absent here. The findings are the report's account of execution, not an independent reconstruction from its raw logs. |

**Revision caveat:** p. 1 identifies the implementation with version 3 and prints the reference date as January 1968, whereas BBN 3900 explicitly plans a TCP-4 baseline and the later BBN 4129/4471 reports identify TCP4/IP4. The January date appears erroneous, but it has not been silently corrected. These inconsistent labels prevent using the reports as proof of one exact unchanged build. They do not negate the reported S/P/T tests. Successful resource preemption has not been established by the inspected results.

### BBN 4129: the proposed host-to-switch experiment

Michael A. Wingfield, *AUTODIN II Host Test Plan*, October 1979, [source photograph folder](../sources/README.md#reading-and-retrieval-records). All 31 photographs were processed for discovery; the following original pages were inspected.

P. 1, [introduction](../sources/unique/bbn-4129/bbn-4129-p1.jpg), proposes connecting DCEC's EDN PDP-11/70 to an AUTODIN II packet switch over a 56-kbit/s leased circuit, using TCP4, IP4, SIP, and Mode VI ADCCP. The diagram and description on pp. 2-3, [layer diagram](../sources/unique/bbn-4129/bbn-4129-p2-3.jpg), explicitly separate these modules. TCP handles process-to-process reliability and flow; SIP manages segment exchange with the switch; ADCCP handles reliable link exchange. The planned tests are:

- **Link:** pp. 14-15, [link tests](../sources/unique/bbn-4129/bbn-4129-p14-15.jpg), coordinate with Western Union personnel, establish the ADCCP link, observe reset/ready/not-ready frames, and bring it down. These supplement the self-test procedures discovered on pp. 12-13.
- **SIP:** pp. 20-21, [SIP transitions](../sources/unique/bbn-4129/bbn-4129-p20-21.jpg), exercise inoperable, busy, operable, READY, and zero-window transitions, with segment and link logs to check the exchanges.
- **TCP and authorization:** pp. 4-5, [scope and authorization fixtures](../sources/unique/bbn-4129/bbn-4129-p4-5.jpg), define four test series and specify that only this 11/70 and the switch participate. Switch limits are assumed to be precedence 10, security 8, and TCC 3; these are test fixtures adjustable with Western Union, not universal network policy. F4-F6, pp. 26-28, [F4-F5](../sources/unique/bbn-4129/bbn-4129-p26-27.jpg) and [F6 and performance design](../sources/unique/bbn-4129/bbn-4129-p28-29.jpg), expect rejection of unauthorized precedence, security, and TCC. F5 deliberately lets the host authorize a level above the switch's limit, isolating switch enforcement.
- **Performance:** p. 29, [F6 and performance design](../sources/unique/bbn-4129/bbn-4129-p28-29.jpg), compares TCP loopback, ADCCP self-test, and self-addressed traffic through the switch to attribute overhead and delay to individual components.

Its assertions that results "will" show correct rejection remain expected outcomes. The EDN software results in BBN 3664 do not execute this subsequent plan. No completion report for this host/SIP/ADCCP-to-AUTODIN-switch series was identified in the inspected records.

### BBN 4471: AUTODIN II FTP software over experimental facilities

John S. Quarterman, *AUTODIN-II FTP Test Report*, August 29, 1980, [source photograph folder](../sources/README.md#reading-and-retrieval-records). The 20 local photographs contain identifying/contents pages and body pp. 1-29. The [contents, p. ii](../sources/unique/bbn-4471/bbn-4471-pii-iii.jpg), list section 5, Results, beginning on p. 48 (functional results p. 48, performance results p. 49; references p. 59). Those concluding results, the later performance procedures, and appendices are absent. The [last photograph](../sources/unique/bbn-4471/bbn-4471-p28-29.jpg) ends during P2 on p. 29. Targeted local filename and public title/author/report-number searches did not locate a fuller copy. **The requested concluding results could not be read.** The findings here use the actual summary on pp. 2-3 and available detailed procedures, not a reconstruction of the missing conclusions.

- **What was tested:** p. 1, [introduction](../sources/unique/bbn-4471/bbn-4471-p1.jpg), calls this the first implementation of the AUTODIN II File Transfer Protocol, under Unix, tested on EDN hosts and EDN-UNIX/BBN-UNIX as ARPANET hosts. The Unix command is `fcp`, because `ftp` already names the NCP program. The purpose was to demonstrate an implementable protocol and measure this implementation, not validate the entire AUTODIN II system.
- **What carried it:** p. 9, [gateway and protocol stack](../sources/unique/bbn-4471/bbn-4471-p8-9.jpg), describes a PDP-11/40 gateway used for some tests between EDN and ARPANET, and TCP-4 incorporating PSIP. FTP needs a duplex byte stream and is insulated from lower-layer details, although its performance depends on them. This is observed application use of the modular strategy described in BBN 3900. Calling it a test of the AUTODIN II physical backbone would be wrong.
- **Reported successes:** pp. 2-3, [summary](../sources/unique/bbn-4471/bbn-4471-p2-3.jpg), report normal file transfers using one, two, and three hosts, user aborts, printer/text formatting, user-error handling, and status reports, using protocol logs and file comparisons. Text transfer was slower than binary. The reported range is 157 to over 14,000 "baud," retaining the source's unit; the highest result bypassed the network. Kernel-interface speed and disk swapping limited other runs, so it is not a backbone-throughput figure.
- **Qualification of the summary:** p. 3 says the network-induced transfer-failure test was "not passed." P. 27, [F9 and performance-test status](../sources/unique/bbn-4471/bbn-4471-p26-27.jpg), says F9 "was not performed." Treat this as an untested recovery property, not an observed recovery failure. P. 25, [memory failure](../sources/unique/bbn-4471/bbn-4471-p24-25.jpg), separately documents an actual repeated failure: the active process ran out of memory and died, resetting its connection; the server was made smaller for later tests.
- **An implementation gap affecting the interface:** p. 12, [user-ID and host limitations](../sources/unique/bbn-4471/bbn-4471-p12-13.jpg), says the TCP user-ID feature had not been implemented, requiring separate login to active and passive FTP components even when colocated. This concerns identity support between these components; it does not contradict the local OS-user authorization table in BBN TCP or establish that S/P/T enforcement was absent.

### Subsequent progress reports as a control on attribution

The local BBN combined quarterly excerpts 3722, 3824, 3911, 3984, 4068, 4133, and 5345 were searched as follow-up leads. Their sponsorship and implementations must not be collapsed into the DCA project. In [BBN 4068, *Combined Quarterly Technical Report No. 12*, February 1979](../sources/README.md#bbn-4068-excerpt), printed pp. 44-45 / PDF pp. 6-7, checked visually, the author explicitly identifies the **ARPA-sponsored** TCP-4 effort, reports a functioning version tested at ISI in late January, and still lists fragment reassembly among subsequent work. It discusses secure/nonsecure parameterization and logical subhosts for running multiple TCP versions on one machine. This is evidence of contemporaneous parallel implementations and incremental completion, not proof that all security work or address modularity came from AUTODIN II. No exact source-revision identity between this effort and the DCA EDN test build is established here.

### BBN source availability and test records

The September 11 continuation has now read substantive portions of the three reports below and followed BBN 3664 to BBN 3900. Their evidence and exact page locators appear in the expanded BBN section. This supersedes the earlier title/contents-only coverage. BBN 3664's separately bound logs and BBN 4471's later results/conclusions are still unavailable in these local copies.

| Local report | Current evidence and remaining gap |
| --- | --- |
| [BBN 3664, Joanne Levin, *Transmission Control Protocol (TCP) Test Report*, August 1979](../sources/unique/bbn-3664/bbn-3664-capture-01.jpg) | Examined report describes completed EDN functional and performance tests, including security, precedence, and TCC checks and the input-truncation exception. Its separately bound logs remain missing, and inconsistent contemporary version labels remain unresolved. Do not infer the date from the report number. |
| [BBN 4129, Michael A. Wingfield, *AUTODIN II Host Test Plan*, October 1979](../sources/unique/bbn-4129/bbn-4129-capture-01.jpg) | Planned tests connecting a Unix PDP-11/70 to an AUTODIN II packet switch, including SIP, Mode VI ADCCP, and TCP traffic measurements. It specifies future tests, so seek execution records before claiming success. |
| [BBN 4471, John S. Quarterman, *AUTODIN-II FTP Test Report*, August 29, 1980](../sources/unique/bbn-4471/bbn-4471-capture-01.jpg) | Application behavior and performance across named Exploratory Data Network hosts. The available summary and procedures now establish reported application tests over EDN/ARPANET, including an omitted recovery test and host-memory limitations. The later Results section, pp. 48-58, is absent locally. |

All three identify **DCA100-78-C-0011**, giving a shared retrieval key for reports and correspondence. Keep that BBN contract distinct from SRI's specification contract and Western Union's system contract.

For the deeper security architecture question, [BBN 4767, Voydock and Kent, *Security in Higher Level Protocols: Approaches, Alternatives, and Recommendations*, November 1981](../sources/README.md#reading-and-retrieval-records), is another prospective comparison. Its title and contents were read through OCR. Its sponsorship is NBS; an AUTODIN II-specific connection has not been established. Sampling BBN 3747 instead identified a TRW network-requirements discussion, so it is a lower priority for this argument.

## Unresolved questions

Separate BBN 3664 logs, the remainder of BBN 4471 after p. 29, execution records for the BBN 4129 plan, DTI routines, intermediate BBN source identity, and source-specific deployment remain open. The source sections below retain the exact limits. Reopening requires a selected question and an identified source; historical execution remains separately authorized.

## Research question

**Answered within scope:** how did security/precedence authorization at connection opening differ between the inspected early BBN implementation and the November 24, 1981 BBN TCP/IP 3.0 beta? The [source comparison](implementation-and-tests.md#the-1979-and-november-1981-authorization-paths) and [implementation consequences](later-standards.md#the-dated-bbn-distribution-as-a-control) establish a bounded static-source result, not execution or general deployment. The inspected `tape1-files` matched `tape1.tgz`; `bbnnet-oct82` has separate provenance.

No continuation is selected. Reopening requires a new historical question, one identified distribution and the same authorization path or a justified new path. The `nosc-files` and `clem-cole` trees are outside the comparison. Originals remain under `retained source: network-unix-v6`; no historical build or execution is proposed.
