# AUTODIN II and TCP/IP: research overview

This record distinguishes established findings, contrary evidence, and missing decision records.

## Topic notebooks

| Subject | Start here |
| --- | --- |
| The intended defense service, ARPANET plans, and concurrent research and operational use | [Service and ARPANET plans](research/service-and-arpanet-plans.md) |
| Priority, contracting, host/backbone boundaries, and limits on attribution of the split | [Priority and network boundaries](research/priority-and-network-boundaries.md) |
| SRI and Western Union specifications, successive standards, and the 1978–80 upgrade | [TCP versions and standardization](research/tcp-versions-and-standardization.md) |
| Preserved BBN code, DTI design, reported tests, and their limits | [Implementation and tests](research/implementation-and-tests.md) |
| The competing plans, evaluation accounts, cost estimates, recommendation, and authorization | [DDN selection](research/ddn-selection.md) |
| Uneven persistence of military controls in standards and implementation | [Later standards](research/later-standards.md) |
| The later keying/address dispute, missing guide, and edition comparison; later historical work | [BLACKER interface](research/blacker-interface.md) |

Each notebook owns its findings, evidence and qualifications. [Sources](sources/README.md) owns provenance and availability; [reading coverage](sources/coverage.md) owns exact inspection boundaries.

## Findings and limits

- **Direct feature influence is established.** AUTODIN II requirements affected security and priority provisions in TCP. The [version record](research/tcp-versions-and-standardization.md#findings-and-limits) distinguishes the recovered 1976 specification, the March 1977 reassessment, later research versions, and Western Union’s contracted branch. Feature influence does not establish that AUTODIN II caused the TCP/IP split.
- **The allocation of responsibilities was argued explicitly.** The committee tied technical boundaries to contracting, performance assessment, priority, interconnection, and encryption. The [priority record](research/priority-and-network-boundaries.md#findings-and-limits) distinguishes its recommendation from a later specification that agrees with it. The intervening adoption decision remains missing.
- **Implementation and test evidence is bounded.** Contemporary reports, preserved code, a dated BBN distribution, and reported EDN tests establish different things. The [implementation record](research/implementation-and-tests.md#findings-and-limits) keeps static inspection, planned experiments, reported results, missing logs, and deployment separate. Absence from the November 1981 distribution does not establish a policy to abandon controls.
- **An upgrade was ordered, and timing remained consequential.** The December 1978 order tasked a cost tradeoff analysis; the April 1980 ratification placed AUTODIN II implementation after initial operational capability without stating a reason. The [transition record](research/tcp-versions-and-standardization.md#unresolved-questions) retains the standard’s actual edition sequence and missing analysis. Document revision 3 is not TCP protocol version 3.
- **The DDN choice has recorded reasons and unresolved weighting.** The [selection record](research/ddn-selection.md#findings-and-limits) distinguishes the proponent’s plan, DCA evaluation, concurrent Task Force review, modeling, public rationale, and Carlucci’s April 2, 1982 authorization. Cost comparisons existed and favored REPLICA. Model outputs and estimates do not establish measured superiority, realized savings, a decisive factor, or the evaluation’s final weights. Stenbit’s qualification and the thesis’s relayed AUTODIN II large-transfer advantage remain part of the record.
- **Requirements persisted unevenly through changed designs.** The [later-standards record](research/later-standards.md) distinguishes specification presence, implementation, and later changes. The DDN backbone and the larger internetwork remain separate analytical objects.

The interaction ran in both directions: internetting research informed AUTODIN II work, and AUTODIN II requirements influenced protocol development. The evidence supports an account of overlapping operational and research projects, divergent commitments, and efforts at reconciliation. It establishes neither an exclusive original purpose nor a single cause for later architectural choices. The [interpretive limits](research/priority-and-network-boundaries.md#limits-on-institutional-and-economic-interpretation) retain the separate evidentiary demands for funding strategy, institutional support, and wider economic or political effects.

## Further work

[Open questions](questions.md) owns current priorities and links the detailed gaps. Retrieval failure does not establish that a record never existed. Broader routing, procurement and security questions require their own evidence.

## Earlier question identifiers

Dated source records retain these earlier identifiers. These links locate the current evidence and question boundaries; they do not assign work. Completed verification files retain the paths and hashes they actually checked.

### Chunk 1: Priority and sequencing

[Priority question and boundaries](research/priority-and-network-boundaries.md#research-question).

### Chunk 2: The 1978-80 upgrade and deferral

[Transition question and boundaries](research/tcp-versions-and-standardization.md#research-question).

### Chunk 3: One requirement in 1980s code

[Completed BBN comparison and reopening boundary](research/implementation-and-tests.md#research-question).

### Chunk 4: The 1981-82 AUTODIN II-to-DDN selection

[Selection question and boundaries](research/ddn-selection.md#research-question).

### Chunk 5: The 1986-89 security-interface change

[Reserved BLACKER question and boundaries](research/blacker-interface.md#research-question).
