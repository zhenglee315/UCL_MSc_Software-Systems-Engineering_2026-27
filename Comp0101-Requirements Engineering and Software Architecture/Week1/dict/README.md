# COMP0101 — Week 1: Foundations of Requirements Engineering

[繁體中文版](../README.md) · [Coursework, reading and my Quiz answers](../coursework/dict/README.md) · [Moodle Week 1](https://moodle.ucl.ac.uk/course/section.php?id=1379384)

This English version combines the **morning and afternoon classes on 8 October 2026**. The central sequence is to identify stakeholders' goals in the real world, define the machine boundary, distinguish phenomena, requirements and assumptions, and then check whether implementing the specification is sufficient to solve the problem. Personal answers and completion records refer to the repository owner, not to every reader.

## 1. Weekly Summary

**Requirements Engineering (RE)** is a set of activities throughout the software lifecycle: discovering, analysing and communicating stakeholder needs, context, and desired externally visible software behaviours and qualities, while handling trade-offs and changes. It takes place beyond the beginning of development and involves more than recording requested features as user stories.

The central reasoning this week is **`Req, Dom ⊢ Goals`**: if the machine satisfies its requirements and the world's domain assumptions hold, stakeholder goals can be deduced to hold. Code conforming to its specification therefore does not guarantee the success of the whole system. The aircraft ground-braking and London Ambulance Service examples show how invalid environmental assumptions can produce system failure even when software conforms to its requirements.

The lecturer emphasises modelling and precise communication: describing behaviour as users see it externally, separating real states from sensor data, and assigning responsibilities clearly to actors. In an English exam answer, explain classifications through concrete scenarios rather than simply recalling terms.

**Required independent reading this week** includes Requirements in the Software Lifecycle and the Wider Context. These topics were not covered fully in class, and Moodle explicitly says that Chapters 5 and 6 **could be assessed**. The concepts below are supplemented from the available Foundations slides; this does not claim that the full lecture-notes book behind the unavailable link was obtained or read.

## 2. Scope of Requirements Engineering

| Key idea | Meaning and practical implications |
|---|---|
| Stakeholder needs | Expectations about software's effects on people's lives, work and businesses. Stakeholders extend beyond the paying client and direct users. |
| Context | The real operating environment, existing processes, other actors, technologies and constraints. Poor understanding of context encourages invalid assumptions. |
| Software requirements | The **externally visible** behaviours and qualities needed to satisfy stakeholder needs in a given context. |
| Trade-offs | Stakeholders' needs can conflict, and demands may exceed technological, budget or time capabilities. Priorities require agreement. |
| Change management | Needs, context and behaviour change; versions and product-family variants must be managed. |
| Lifecycle activities | RE continues throughout development. Developers also make requirements decisions when filling gaps in undocumented behaviour. |

**Class examples:** Industrial requirements may appear in PRDs, user stories, email, PowerPoint, Word, DrawIO, Excel, API specifications or microservice interaction diagrams. No single document template replaces understanding the requirements.

**The lecturer's analogy: restaurant waiter vs medical doctor.** RE involves investigating the problem and its causes, understanding the real purpose, and proposing alternatives and trade-offs. Simply implementing a client's order is insufficient. A student described a client requesting a custom-trained LLM; the suggested approach was to establish the intended business value and evaluate whether other options could deliver it before choosing the technology.

Quality requirements also need **testable criteria**. “Fast” alone is insufficient: specify which response must occur within which time bound, under which inputs, workload and environment. This is a study synthesis of the performance-requirements discussion.

## 3. World, Machine and Phenomena

### 3.1 Define the Machine Boundary First

- **Machine:** The product or software-to-be that the development team is responsible for building or improving.
- **World:** The relevant application domain, environment or context associated with and affected by the machine.
- **Phenomenon:** An observable **state** or **event**. An ambulance being at a location is a state; its arrival at an incident is an event.
- An **entity** or **property** is not itself a phenomenon. “An ambulance” is an entity; “response time must be less than 14 minutes” is a property constraining behaviours.

| Type | Definition | Questions to ask |
|---|---|---|
| World phenomenon (W) | A state or event in the World. In classification exercises, use the most specific category; W usually denotes a world phenomenon outside the machine interface. | Is this what actually happens externally, or information received by the machine? |
| Machine input (I) | A shared phenomenon controlled by the World. | Does it occur at the machine boundary and fall under an external actor's control? |
| Machine output (O) | A shared phenomenon controlled by the Machine. | Is it controlled by the machine and externally visible or sent into the world? |
| Internal machine phenomenon (M) | A state or event within the machine. | Is it an internal function, variable or computation that does not cross the boundary? |

**Essential distinction: actual state ≠ information about that state.** An ambulance's real location and the GPS location message sent to CAD are different phenomena. The ambulance may be in a tunnel, while the message is missing or inaccurate. Similarly, **wheels turning** and **sensor signals that wheels are turning** must be distinguished.

### 3.2 CAD Classification Exercise from Class

The machine here is the **Computer Aided Dispatch (CAD) software** in the class context diagram. MDT, GPS and the call handler are external. These classifications summarise that discussion and must not be applied unchanged to a different boundary.

| Phenomenon | Type | Reason |
|---|---|---|
| An incident occurs. | W | An event in the world that does not directly cross the CAD interface. |
| A person calls emergency services. | W | In this diagram, the public calls the call handler; CAD does not directly receive the call. |
| A call handler encodes incident details into CAD. | I | An external actor enters information through the CAD interface. |
| An ambulance is at Buckingham Palace. | W | This is its actual location; the GPS location update is a separate input. |
| An ambulance is available. | W | Actual availability differs from availability reported by paramedics or sent by MDT. |
| `findNearestAvailableAmbulance()` returns an ID internally. | M | An internal method return. Displaying a list on screen would instead be an output event. |
| CAD sends mobilisation instructions to MDT. | O | Information sent from CAD to an external component. |
| Ambulance crew accepts mobilisation on MDT. | W | The crew interacts with an external MDT; MDT subsequently sending an acceptance message to CAD is CAD's input. |
| An ambulance arrives at the incident scene. | W | An arrival event in the real world. |

At approximately 81–99 minutes of the morning recording, the lecturer repeatedly stresses that **input/output is always relative to a particular actor, component or machine**. A context diagram helps expose responsibility boundaries and communication misunderstandings, beyond being a drawing exercise.

### 3.3 Actors vs Stakeholders

| Term | Meaning | Common pitfalls |
|---|---|---|
| Actor | An entity that can initiate an event, change a state or perform an action: a person, organisation, device or software system. | The machine itself is an actor; actors are not restricted to users. |
| Stakeholder | A person or group with an interest in, or affected by, the machine. | Non-human actors are not stakeholders. People affected without operating the system can also be stakeholders. |

A sensor can be an actor but is not a stakeholder. A safety regulator may be a stakeholder; whether it is an actor in a particular model depends on its participation in the system's actions.

## 4. Behaviours, Properties, Goals, Requirements and Assumptions

A **behaviour / scenario** is a sequence of phenomena over time. A **behavioural property** is a condition on behaviours, classifying many possible scenarios as conforming or non-conforming without listing every scenario individually.

| Property type | Definition | Example |
|---|---|---|
| Domain goal (G) | A desired property of the World, usually the outcome stakeholders care about; it can require several actors' cooperation. | An ambulance arrives within 14 minutes after the first emergency call. |
| Machine requirement (R) | A desired property of the Machine at its interface with the World, expressed using shared input/output phenomena and guaranteed by the machine. | A handler enters incident details → CAD displays the nearest available ambulances based on its information. |
| Domain assumption (D) | An assumed property of the World, such as a physical condition or expected behaviour of other actors. | GPS sends correct locations; the call handler correctly enters incident details. |

**Classification method — study synthesis:** Identify the property's phenomena, locate them relative to the machine boundary, and decide whether the statement requires machine behaviour, describes a desired world outcome, or assumes external behaviour. Words such as `must`, `should` or `will` are insufficient for classification by themselves.

**Goal identified ≠ goal necessarily satisfied.** Identify stakeholder goals first, then address conflicts, scope, responsibility and feasibility. Listing a goal does not guarantee its satisfaction.

### 4.1 Requirements Correctness: `Req, Dom ⊢ Goals`

`⊢` denotes **logical deduction**: a conclusion can be deduced from the premises.

The simplified ground-braking example from class:

```text
D1: MovingOnRunway → WheelsTurning
D2: WheelsTurning → WheelsPulseOn
R1: WheelsPulseOn → BrakingEnabled
--------------------------------------
G1: MovingOnRunway → BrakingEnabled
```

If D1 and D2 hold and the software satisfies R1, G1 follows. Skidding on a wet runway can invalidate D1, so this reasoning alone does not guarantee safety in the real world.

**Program correctness** is relative to requirements. **Requirements correctness** is relative to domain goals and requires valid domain assumptions. `Dom` cannot be omitted.

In practice, identifying Goals, Dom and Req involves mutual influence and repeated revision. In the afternoon discussion around 14–17 minutes, the lecturer explains that starting with goals and decomposing them is typical, but known technologies or requirements can also support bottom-up reasoning. There is no compulsory sequence of finishing all goals, then all assumptions, then all requirements.

**Goal modelling — this week's preview:** Decompose a parent goal into subgoals, progressively identify actor responsibilities, requirements and assumptions, and organise a satisfaction argument. Detailed techniques are taught later.

### 4.2 Limitations of the Theory

The formula does not fully address when requirements are good enough, goal conflicts, alternative designs, partial goal satisfaction, uncertainty, or technology, budget and time constraints.

In practice, we care about how well goals are satisfied and whether the risk of building the wrong system is sufficiently controlled. Safety, privacy and reliability often have degrees of satisfaction; a target may require a particular proportion of incidents to meet a response threshold.

## 5. Requirements Errors and Failures

| Term | Definition / distinction |
|---|---|
| Failure | A situation in which a product does not work as intended. |
| Defect | A flaw in the product that may lead to failure. |
| Error | A human mistake contributing to a defect. |
| Machine failure | The machine does not satisfy its requirements. |
| System failure | The machine and surrounding world actors do not achieve an essential stakeholder goal. |
| Implementation error | A coding mistake: the program does not behave as its developer intended. |
| Requirements error | A mistake in the definition, communication or understanding of requirements. |

**Machine failure does not necessarily cause system failure; system failure can occur without machine failure.** Software may execute its specification precisely, yet fail to achieve a safety goal because the specification relies on invalid assumptions.

Developers who correctly implement their own mistaken interpretation of requirements can still make a **requirements error**. An error does not become an implementation error simply because it occurs while coding. Vague, incomplete or hard-to-read requirements can also induce misunderstandings and defects.

`Req, Dom ⊢ Goals` suggests three types of requirements errors:

1. **Misunderstanding stakeholder goals:** G does not reflect the essential, agreed stakeholder goals.
2. **Invalid domain assumptions:** Some assumptions in D do not hold in reality.
3. **Inadequate requirements due to incorrect reasoning:** Even when D holds, R is insufficient to achieve G.

### 5.1 Aircraft Ground Braking — Warsaw, 1993

The course materials describe two safety goals: disable ground braking during flight and enable it immediately after landing. Human errors, sensor failures and different landing scenarios must be considered.

The simplified class example illustrates an **invalid domain assumption**: “moving on the runway implies wheels turning” can fail during skidding on a wet runway. The actual case also involves one-sided landing-gear contact, shock-absorber compression and wheel-speed information. The slides describe delayed activation of ground spoilers and reverse thrust. The learning focus is requirements-level reasoning; the simplified formula is not a complete aircraft safety specification.

**Summary correction:** The Asksia morning summary joined the two activation conditions with `AND`. Slide 11 says **at least one** condition, meaning `OR` between the two main conditions; each condition itself requires both main landing gears to satisfy it. The original slides take precedence.

### 5.2 London Ambulance Service — 1992

The course materials describe a new CAD system relying on GPS locations, MDT status and crew behaviour. Several assumptions proved invalid:

- GPS always provides correct, up-to-date locations: locations can actually be inaccurate or missing.
- Crews always drive the allocated ambulance: they may take a different vehicle.
- Crews always report status correctly and in sequence: they may press the wrong button or omit an update.

Treating imperfect information as perfect can cause incorrect availability decisions or repeated allocations. The whole system can fail while software follows its design. The slides also list ambitious scope, an impossible timeline, low-cost procurement, ignored risk advice, deployment in one phase, insufficient user involvement, and inadequate testing and resilience. The event should not be reduced to a single “coding bug”.

## 6. Requirements in the Software Lifecycle — Independent Reading

This section is checked primarily against **Foundations slides 70–80** and corresponds to this week's Lifecycle Quiz.

| Topic | Concepts to explain | Meaning |
|---|---|---|
| Waterfall | Upfront detailed requirements; formal change requests | Assumes goals, assumptions and requirements are initially clear and do not change during development, delaying value and validation and making changes more expensive. |
| Agile | **Iterative + incremental** | Iterative development improves existing content; incremental development adds new content. There is still an initial vision and plan. |
| RE in agile | Prioritisation; just-in-time testable requirements | Choose the next valuable work, analyse and communicate testable requirements when needed, and learn and adjust through delivery. |
| Twin Peaks model | Requirements and architecture are developed together | Requirements guide architecture; architecture reveals costs, trade-offs, omissions and opportunities. Both develop through feedback. |
| V-Model | Tests and verification are with respect to requirements | Different levels of requirements provide the basis for corresponding levels of testing. |
| Ultimate quality criterion | Extent to which stakeholder goals are satisfied | Performance, few bugs and maintainability are evaluated in relation to purpose and context. |

**Book analogy:** Adding a new chapter = Incremental; revising an existing chapter = Iterative.

**Agile assumptions:** Useful small increments can be delivered; business, safety and security risks in initial iterations are acceptable; customer collaboration is sufficient; and the team has capabilities such as CI, automated testing, modularity and refactoring. “Writing code without a plan” is not the intended answer.

**V-Model study mapping:** Stakeholder goals ↔ acceptance tests; machine requirements ↔ system tests; component requirements ↔ integration tests; unit requirements ↔ unit tests. Successful testing must still be considered alongside the validity of requirements and assumptions.

## 7. Requirements in the Wider Context — Reading and Class Discussion

Checked against **slides 81–96**. Commercial contexts are introduced after approximately 73 minutes of the afternoon recording; discussion focuses more on AI from approximately 76 minutes.

| Context | Effects on RE |
|---|---|
| Client project | Development for a specific client. Tenders, proposals, contracts and change requests shape requirements. Fixed scope/price and time-and-materials create different constraints on changes. |
| Product development | Development for a market. Product owners, backlogs and stakeholder feedback shape priorities; iterative and incremental delivery fits more naturally. |
| Greenfield | Developing new software from scratch. |
| Brownfield | Modifying or replacing an existing system; requires deeper understanding of legacy constraints, surrounding systems and established processes. |
| Regulated environment | Comprehensive documentation and traceability from regulations to requirements, code, tests and test results. |
| Social responsibility | Consider safety, security, privacy, environmental sustainability, fairness and the interests of everyone affected. |
| Wicked problem | No single universally agreed problem definition. Groups disagree about benefits and harms, and impacts are difficult to predict or measure. |

### 7.1 Requirements and AI

An AI component is part of a larger system. Stakeholder goals, expected business value, functional requirements and quality requirements still need to be understood. AI's uncertainty, non-determinism and opacity increase the importance of trade-offs, risk analysis, fairness, accountability and transparency.

**AI alignment problem:** An objective function or reward can differ from actual stakeholder goals. Increasing a surrogate metric is not automatically success.

**AI for RE** can support requirements-quality analysis, user-feedback analysis and process mining. However, an apparently complete AI-generated PRD does not establish the correctness of its goals, assumptions and requirements. This records the lecturer's judgement, rather than an independent evaluation of tool performance.

### 7.2 Spec-Driven Development (SDD)

Asksia misrecognised the term as speculative or spectral development. **Slide 93** confirms **Spec-Driven Development**.

| Level | Meaning |
|---|---|
| Spec-first | The spec guides AI for one task and is not maintained afterwards. |
| Spec-anchored | The spec is retained and updated as the feature evolves. |
| Spec-as-source | Only the spec is edited; tools generate the code and humans do not directly modify it. |

The lecturer considers this to be in its early days, especially because complex behaviour is difficult to express precisely using only natural language. Whatever tools are used, separate **Goals, Dom, Req and implementation constraints**, identify potentially missing requirements, check `Req, Dom ⊢ Goals`, and find obstacles that could invalidate assumptions. Coding agents make good functional and quality requirements and acceptance tests more important.

## 8. Instructor Warnings and Common Mistakes

| Common mistake | Better reasoning |
|---|---|
| Treating RE as a fixed first phase | It continues throughout the lifecycle, including developers' gap-filling during implementation. |
| Treating a client's wish list as complete requirements | Investigate the problem, affected stakeholders, alternatives and trade-offs. |
| Classifying input/output without defining a boundary | First identify the component that constitutes the machine. |
| Confusing real states with sensor/database messages | Identify separate phenomena and scenarios involving inaccurate, delayed or missing information. |
| Treating every function return as output | Check whether it crosses the machine interface; an internal return can be M. |
| Using only “what vs how” to separate requirements and implementation | This week uses the more precise **where** distinction: the world-visible interface versus machine internals. |
| Assuming software matching its spec means success | Check goals and domain assumptions; distinguish machine and system failures. |
| Interpreting unmarked as optional or unnecessary | Make genuine attempts at weekly exercises; some are exam-like or were exam questions. |
| Assuming understanding a model answer means being able to solve the problem | Attempt first, then compare and correct. Blank submissions create false confidence. |
| Treating summary exam-relevance labels as the lecturer's view | Asksia's automatic assessments are not syllabus or assessment instructions. |

## 9. Actual Classroom Q&A

The English questions below **paraphrase actual exchanges**, rather than quoting them verbatim. Timestamps locate the discussion in Asksia. Additional study questions are not presented as student questions.

| Question | Answer / interpretation | Recording reference |
|---|---|---|
| How do we check whether a performance requirement is feasible? | Make the response target and conditions explicit, then consider technology, cost/time and alternatives and negotiate feasible requirements with stakeholders. | AM, approximately 9–14 min |
| Are product variants the same as development versions or configurations? | This course emphasises concurrent product-family variants. Configuration can implement variants, but variants do not simply mean all development branches. | AM, approximately 46–51 min |
| Is the ambulance's real location an input? | Not with this CAD boundary. The real location is W; the location message sent by AVLS to CAD is I. | AM, 81:54–83:57 |
| Why is a function returning an ambulance ID internal rather than input/output? | The example is an internal CAD function call/return. Boundary and external visibility determine input/output, not whether this is the first time some information becomes known. | AM, 86:34–96:46 |
| Are inputs only given by actors? | An input is a World-controlled shared phenomenon. A person, device or another software actor can produce it; it is not restricted to human operations. | AM, 92:03–93:24 |
| Is accepting a mobilisation on the MDT an input to CAD? | It is an input to MDT. For CAD, the crew's interaction with MDT is W; MDT's message to CAD is I. | AM, 97:31–99:36 |
| Should we identify requirements or domain assumptions first? | Usually start with goals and decompose them, while allowing bottom-up reasoning. The three activities are concurrent and iterative, rather than strictly sequential. | PM, 14:13–17:06 |
| Isn't the call handler's work a requirement? | It may be a job requirement for the handler, but in the CAD specification it is D: CAD does not perform the handler's action of entering correct information. | PM, 36:45–37:56 |

## 10. Exam Preparation

**The lecturer's explicit statement:** COMP0101 is assessed **100% through a three-hour written examination**. Weekly exercises are **not marked**, but many questions are exam-like and some were exam questions. There is no evidence that all exam questions are selected from these exercises. See AM 19:12, 19:32, 19:37 and 23:16–24:20.

**Different meanings of optional:** The Martin Fowler talk is optional but highly recommended. The RTC temporal-logic subquestion is explicitly optional, and formal specification is not assessed. These are separate from the whole RTC exercise being unmarked. Required lifecycle and wider-context content can still be assessed.

**My revision questions — not past-paper questions:**

1. Define Requirements Engineering and explain why it is not merely the first phase of development.
2. Given a machine boundary, classify W/I/O/M and justify each answer.
3. Distinguish domain goals, machine requirements and domain assumptions.
4. Explain `Req, Dom ⊢ Goals` with an example and an invalid-assumption counterexample.
5. Explain how system failure can occur without machine failure.
6. Classify a misunderstanding during coding as a requirements or implementation error, with reasons.
7. Explain iterative vs incremental, Twin Peaks, and requirements-based testing.
8. Explain how brownfield, regulation and AI affect RE.

**Where to find past papers:** [Moodle General](https://moodle.ucl.ac.uk/course/view.php?id=56463) → Library links → **COMP0101 Past exam papers** → [UCL Library exam-paper search](https://ucl.primo.exlibrisgroup.com/discovery/search?query=any%2Ccontains%2Ccomp0101&tab=Exampapers&search_scope=Exampapers&vid=44UCL_INST%3AUCL_VU2&offset=0). The entry point was checked; contents of unread past papers have not been incorporated into these notes.

## 11. Sources and Coverage

| Source | Scope of this review |
|---|---|
| [Asksia COMP0101 session](https://app.asksia.ai/pro/session?id=32744d41-52e6-4ccd-847e-d63797c258a3) — `Recording_20261008_0800` | The visible Origin English transcript was read from start to bottom. Morning teaching ends around 100:19; later material is mainly departure/conversation. The transcript reaches 107:30 while the player shows 103:32, so timestamps serve only as location aids. |
| Same session — `Recording_20261008_1609` | All visible Origin text was read to the bottom at 95:59; the player shows 114:51. The transcript begins during a properties discussion and contains misrecognitions and missing sentences. Missing audio has not been reconstructed. |
| Asksia existing summary / Sia Note | Used for a second check, correcting AND/OR, wheels/wings and SDD. Break-time ID/age conversation was labelled as an exam trap by the summary and has been excluded from course knowledge. |
| [Foundations slides](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8513321) | Text from all 101 slides of the downloaded `1. Foundations.pptx` was read to check definitions, cases and independent-reading topics. |
| [Moodle Week 1](https://moodle.ucl.ac.uk/course/section.php?id=1379384), [9 October announcement](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1316380#p2355911) | Required/optional reading, exam relevance, assignment steps and completion before class were checked. |
| [RTC assignment](https://moodle.ucl.ac.uk/mod/assign/view.php?id=8513326) | The exercise DOCX was read. No submission was made and the submission-restricted solution sheet was not obtained. |
| [Lifecycle Quiz](https://moodle.ucl.ac.uk/mod/quiz/view.php?id=8513324) | The existing Finished attempt was checked read-only on 12 October 2026: 4/4. All five answers are recorded in the coursework file. |

The old lecture-notes book link on Moodle, `http://www0.cs.ucl.ac.uk/staff/E.Letier/book/`, could not be opened. The [Reading activity](https://moodle.ucl.ac.uk/mod/url/view.php?id=8513323) is retained for reference. These notes do not claim to have read the unavailable book or infer its original chapter titles from slide section titles.

Checked on **12 October 2026, Europe/London**. The original Chinese explanations are study notes; the technical terms and reasoning should also be expressible independently in English.
