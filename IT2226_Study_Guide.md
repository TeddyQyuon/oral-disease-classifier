# IT2226 Study Guide

This guide covers the six uploaded course files and their speaker notes. It follows the work you will do in IT2226, from researching a real problem to defending an integrated AI application. Examples marked as practice illustrate how to apply the course material.

## 1. Project Guidebook

### What the project requires

IT2226 is a team project in AI Innovation and Deep Learning. Build an ethical AI application that addresses a real problem benefiting people in Singapore. The available themes are Business, Education, Healthcare, Logistics, Smart Nation, Sustainability and Transport. The guidebook encourages researching Singapore challenges, hackathons or competitions for problem statements and using design thinking to find out what users need.

The five learning outcomes cover explaining AI constraints, describing AI-enabled enterprise cloud services, applying appropriate ML platforms and tools, planning and delivering iteratively in a team, and justifying and verifying AI-assisted work you submit.

Teams have three to four students and elect a leader. The leader assigns and coordinates work, tracks deadlines and compliance, arranges meetings, liaises with the tutor and external parties when needed, and ensures members commit under their own accounts. Members participate, attend meetings punctually, own assigned work and take responsibility for the code they submit. The supervisor advises on design, tools and allocation, provides a user or management perspective, and conducts individual technical assessment. The uploaded guidebook names Mr Wee Chee Hong as LU leader and tutor on p. 9.

**Each team member** is expected to collect, understand and prepare data, train a classical or deep supervised model, tune hyperparameters, evaluate with suitable metrics, and document the experiments. Each member also develops a Gen AI capability with a defined use case, integrates the model and Gen AI into an application, develops additional features that enhance the solution, and can explain and modify their work. Possible Gen AI routes include RAG, fine-tuning, or a single- or multi-agent capability. Additional features might include user management, Maps API integration, or a mobile interface.

### Milestones and marks

| Guidebook §6 | What to prepare | Individual | Group |
|---|---|---:|---:|
| Week 2 | Form team, draft problem statement, set up shared repository with individual accounts, start individual AI Use Logs | — | — |
| Week 3 | Idea presentation, individual technical spec, group slides | — | — |
| Week 5 | Progress Review 1, supervised model, code interrogation and live task, AI Use Log, team progress | 15% | 5% |
| Week 14 | Progress Review 2, Gen AI or agentic capability, code interrogation and live debug, AI Use Log | 25% | 5% |
| Week 18 | Final presentation, report, slides, source code and version history, individual defence, final AI Use Log, peer review, Ethical AI Checklist | 35% | 5% |
| Total | Mock interview accounts for the other 10% | 75% | 15% |

**Check dates and policy with your tutor.** The Week 18 final in the schedule differs from Week 19 in the final rubric heading. The Resource Planning Guide places the idea presentation in Week 5 and Progress Review 1 in Week 8. The guidebook table places them in Weeks 3 and 5 respectively. Its cover says 2026 S2 while most footers say 2026/S1. Section 7.5 refers to an Annex C for the applicable AI tool policy, but the attached copy ends after the rubrics without that annex. The guidebook says the tutor confirms policy in Week 2. Section 7.4 also refers to an Individual Contribution Evidence criterion at the final, while the printed final rubric has no separate row by that name.

### How the assessment works

- **Artefact:** The trained model, Gen AI capability and application demonstrate the solution functions.
- **Process:** The repository and AI Use Log show who did what, when, and how the work evolved. Commit frequently in small units under your own account. Separate bulk imports of generated code from your own edits so reviewers can see the difference.
- **Live defence:** Guidebook §7 estimates roughly 30% of the LU total comes from criteria earned in person. At the reviews and final, expect an individual walkthrough, a tutor-set modification, a seeded-fault debug exercise and questions about two or three log entries. During that portion, close notes, scripts and AI assistants. Your normal editor is allowed for the live task. The individual session may take place on a separate date.

For a walkthrough, explain what the file does, why it exists, what depends on it and what breaks if it disappears. For a modification, find the affected code, make the change, verify it and explain side effects. For debugging, reproduce the symptom, isolate it, state a hypothesis, test that hypothesis and verify the fix. Typical tasks include changing a metric, adding a field or supporting another input case.

High-scoring AI practice means writing precise specifications, verifying generated work against tests, data or documentation, catching substantive errors, rejecting or rewriting unsuitable outputs and explaining what you would hesitate to deploy. Examples include invalid API calls, wrong dataset splits, leakage and broken dataset links. Unverified generated code on a critical path or a log inconsistent with Git history can put the criterion in the Inadequate band. The guidebook identifies misrepresenting what you did and claiming another person's or team's contribution as your own as academic misconduct.

### Rubrics and deliverables

| Checkpoint | Individual criteria | Group criteria | What the Excellent band looks for |
|---|---|---|---|
| Review 1, pp. 12–13 | Input data 5, supervised model 5, source code and code review 5 | Plan and presentation 5 | Relevant, substantial, coherent data and insightful visual EDA. Custom training with evidence of optimisation. In-depth, correct interpretation of metrics. Logical modular code with helpful comments or markdown and a strong explanation of all critical components. Revised plan that addresses scope changes and a coordinated presentation. |
| Review 2, pp. 14–15 | Supervised model 5, Gen AI 5, application 10, source code and code review 5 | Presentation 5 | Systematic, iterative optimisation and remote hosting of the supervised model. Clear Gen AI objectives, extensive research, complete implementation and detailed explanation. Both capabilities work through an intuitive UI and their outputs demonstrate the user problem is addressed. |
| Final, pp. 16–17 | Presentation and Q&A 5, app demo and UX 10, Ethical AI 5, reflection 10, peer review 5 | Presentation 5 | Confident delivery and insightful Q&A. Integrated features show relevance, technical proficiency and impact. Human-centred usability throughout. Relevant checklist answers for at least 90% of items. Broad, in-depth reflection with feasible improvements. Peer reviews raise no issues. Group slides are coherent, extensive and well coordinated. |

For 5-mark criteria, the F/D/C/B/A bands start at 0/2.5/3/3.5/4 respectively. For 10-mark criteria, they start at 0/5/6/7/8. Review 2's model optimisation row lists accuracy cutoffs of 50%, 60%, 70% and 80% for D/C/B/A, with an industry benchmark alternative in the B and A bands. These are rubric descriptors. Explain which metrics fit your task and why. The Ethical AI rubric gives F for relevant answers to under 50% of items and D/C/B/A thresholds of 50%/60%/75%/90%.

Annex A suggests individual project plan content covering supervised learning, Gen AI, milestones, deliverables and research references. Group idea slides cover the problem statement, research, individual components and schedule. Review or final reports cover the solution, both AI capabilities, features, UX and reflection.

### AI Use Log

Keep your own record while working and submit it at each review. Record meaningful code blocks, design decisions and resources from AI. The columns are date, tool, what you asked for, accepted/changed/rejected, and why. The last column is graded and should name the check, finding and action.

| Task from the guidebook | Decision | What makes the entry verifiable |
|---|---|---|
| Generate a FastAPI endpoint for a classifier | Changed | The endpoint accepted arbitrary JSON. A Pydantic schema now rejects bad input before it reaches the model. |
| Suggest evaluation code | Rejected | The proposed metric used the training split. Rewrote it to evaluate on held-out test data. |
| Find a labelled triage dataset | Rejected two of three | Two links returned 404. Downloaded the remaining dataset and checked its label distribution. |

## 2. Design Thinking Worked Example

Design thinking establishes who needs the solution and what evidence supports the concept. The deck uses Year 2 IT diploma students missing practical deadlines despite timely LMS postings. The constraint is to work within the existing LMS setup without a new institutional software purchase. The longer-term outcome is a measurable reduction in late submissions.

| Stage and slide range | Deliverable | What the next stage inherits |
|---|---|---|
| Empathise, 5–7 | Empathy Synthesis Sheet | Quotes, observed behaviour and a contradiction worth explaining |
| Define, 8–9 | Problem Statement Card | A point of view (POV), focused How Might We (HMW) question and constraints |
| Ideate, 10–11 | Ranked Concept Shortlist | A selected idea and reasons grounded in impact, feasibility and behaviour |
| Prototype, 12–13 | Prototype Package | A cheap test of the riskiest assumption with a measurement plan and thresholds |
| Test, 14–16 | Verdict and Solution Brief | Results, qualitative feedback, scope for iteration and next decision |

1. **Empathise.** The example uses five interviews with on-time and late submitters plus a month of LMS access logs. The composite persona Wei Jie says he knows deadlines, thinks he can start later, opens the LMS mostly for grades, checks class chats and feels overwhelmed by five modules. The logs showed 68% of late submitters opened the assignment page within 24 hours of the deadline. On-time students often set their own reminders. The deck interprets the mismatch as a visibility and tracking problem. The logs document page-opening behaviour, while the interviews help explain it.
2. **Define.** The POV names the user, need and insight. Year 2 IT students need reminders in a channel they already check because they use the LMS for grades and rarely use it to plan. The selected HMW asks how to reach students where they already pay attention within the institutional constraint. Redesigning the LMS was parked because it requires institutional change. Teaching students to plan backward was parked because it requires more behaviour change.
3. **Ideate.** Crazy 8s means eight ideas in eight minutes, one per panel. The deck proposes a WhatsApp forwarding bot, browser extension, peer buddy, shared calendar, streak app, SMS, Telegram countdown bot and printed weekly list. Dot voting on impact and feasibility narrows the field. The Telegram bot pushes into an existing habit. A calendar still requires students to check it, and the gamified app violates the new-app constraint.
4. **Prototype.** A Wizard of Oz prototype simulates automation. A team member manually posts realistic bot messages in a real Telegram group over one week, using two real deadlines and 15 students. The package specifies reminders at 72, 24 and 3 hours before the deadline. The example mock message says 48 hours. The package timings describe the pilot plan. Track clicks or reactions and compare late submissions with the module's historical average. Pass requires a drop of at least 15 percentage points and at least 60% engagement. Failure conditions include no measurable change or most students muting or ignoring within three days. A result between these cases would warrant further investigation.
5. **Test.** Thirteen of fifteen students reacted to a reminder, about 87%. Late submissions went from 34% historically to 11%, a 23-percentage-point drop. Both pre-set thresholds were met. One student muted the chat after two days and still submitted on time. Two asked for summaries of assignment requirements. The brief recommends real LMS-to-Telegram integration, cohort-scale retesting and possible later summaries. A one-class historical comparison supports trying the concept at scale. It leaves open how much of the change was caused by the reminders.

Slides 17–19 ask you to trace the final brief back to the first evidence and practise with another problem. Write what users say and do, state the contradiction, write a POV and draft one HMW. Keep the HMW focused enough to guide ideas and open enough to admit multiple solutions.

## 3. Spec Driven Development

The deck's quick payment-parser prototype checks for the word paid and a dollar amount, then asks the model to handle SGD and USD. This shows why conversational coding is useful for exploration. A keyword check can also match a message such as “not paid,” which illustrates why a durable feature needs agreed rules and test cases. Without a shared spec, generated behaviour can vary, include invented edge-case logic, and leave design decisions trapped in chat.

| File | What belongs in it | Review question |
|---|---|---|
| requirements.md | User stories, numbered acceptance criteria, non-functional targets, constraints, assumptions and glossary | Can each condition and result be tested? |
| design.md | Context diagram, component responsibilities, stack rationale, schemas, APIs and error formats, authentication, authorisation, performance and test strategy | Which requirement justifies this component or decision? |
| tasks.md | Ordered units of work, scope, acceptance criteria, dependencies and requirement IDs | Can someone complete and verify this unit independently once its dependencies are ready? |

Use the story form “As a [role], I want [capability], so that [benefit].” EARS means Easy Approach to Requirements Syntax. The slide introduces **WHEN** for a trigger, **IF** for a condition, **WHILE** for a state and **WHERE** for an applicable context. **SHALL** states mandatory behaviour. For example, “WHEN a user submits a malformed payment amount, the system SHALL return a validation error.” To make the example executable, define the exact malformed inputs and response code or schema.

Design then specifies implementation contracts. For a payment parser, write down recognised currencies and message formats, output fields and the validation error structure. Organise tasks from setup and core logic through API, UI, integration, testing and deployment. The deck suggests tasks of one to two days, each traceable to a requirement ID. Review the spec before implementation, then verify code and tests against it. If intended behaviour changes, update the version-controlled spec and linked tests.

| Depth | Documents | Course guidance |
|---|---|---|
| Full Spec | Requirements, design and tasks | Standard feature work that needs thorough documentation |
| Quick Spec | Requirements and tasks | Small features taking roughly one to three days |
| Micro Spec | Minimal record of intent and checks | Small changes taking under a day |

Choose by risk, lifespan and coordination needs. Slides 1–6 establish the motivation and compare exploratory and specification-first workflows. Slides 7–11 teach the full process and traceability. Slides 12–14 cover depth, the spec as source of truth, and the course references, including the Caleb Del template library, GitHub Spec Kit, Claude Code and EARS.

## 4. Resource Planning Guide

Plan people-hours, data, compute and tools before building. Sample the dataset or knowledge base early. Check labels, volume, quality, relevance and availability before committing to an architecture. Give model components stable input and output contracts so models can be swapped as evidence improves. Budget for data preparation and evaluation alongside training and integration.

| Development area | Plan for | What to verify |
|---|---|---|
| Supervised ML/DL | Labelled data, cleaning and EDA, training and tuning, notebook or compute access, metrics | Dataset access, class balance, leakage-safe splits, reproducible training, evaluation and app-compatible inference |
| Gen AI | Scoped use case, hosted LLM access, vetted documents for RAG or examples for fine-tuning, output checks | Whether answers follow references, handle missing evidence, stay in scope and serve the user's task |
| Agentic AI | Hosted LLM, orchestration, tool and API access, validated outputs, debugging time | Invalid calls, missing tools, repeated loops, runaway latency or cost, safe fallback and escalation |

The planning example is a **hypothetical polyclinic triage assistant**. Week 5 proof of concept uses a validated pain point, sample dataset, vetted FAQs and a first spec. Week 8 MVP trains an urgency classifier and interprets precision and recall, especially missed urgent cases, while narrowing the chatbot to administrative FAQs. Week 14 adds and evaluates a RAG pipeline, introduces escalation for out-of-scope questions and containerises the application. Week 18 integrates and demos both components and completes the ethics checklist. These are worked-example dates.

**What the evaluation terms mean.** Accuracy is the share of correct predictions. Precision is the share of predicted positives that are truly positive. Recall is the share of actual positives detected. If urgent cases are rare, overall accuracy can conceal poor urgent-case recall. Tune using validation data and reserve test data for final evaluation. For RAG, faithfulness checks whether claims are supported by retrieved context. Answer relevancy checks whether the answer addresses the question. Check both alongside the quality of retrieval. RAG retrieves evidence at inference time. Fine-tuning adapts behaviour using examples. An agent decides which steps or tools to use, so its tool actions need tests as well as its text.

| Need | Starting points named by the course |
|---|---|
| Local problems and industry cases | Deloitte AI Dossier, CodeGeeks industrial automation, LeewayHertz, data.gov.sg, LTA DataMall, Smart Nation Singapore |
| Datasets and compute | Kaggle Datasets, Hugging Face Datasets, data.gov.sg, LTA DataMall, Colab, Kaggle Notebooks |
| Hosting and inference | Hugging Face Spaces, Anthropic and OpenAI hosted APIs, Docker, ONNX Runtime |
| Physical simulation | Webots for robotics, Gazebo for robot design and controls, CARLA for autonomous driving, Unity ML-Agents for simulated 3D environments. The guide flags AirSim as archived. |
| LLM engineering | LangChain and LlamaIndex for RAG, Chroma/FAISS/Pinecone for retrieval, RAGAs for evaluation, Hugging Face PEFT for LoRA/QLoRA |
| Agent engineering | LangGraph, CrewAI, AutoGen, MCP for tool exposure, Pydantic or JSON Schema for validation, NeMo Guardrails or Llama Guard |
| Tutorial | The planning guide links the video with YouTube ID hedBZ_ViAGo and suggests checking its relevance with the tutor. |

The guide's start checklist asks for a one-sentence problem backed by a real source, sampled data, team-accessible tooling, a working simulator if needed, a chosen Gen AI approach and confirmed access, a first technical spec and version control from day one.

## 5. Responsible AI

### Principles and governance

**AI ethics** supplies the values, such as human rights, inclusion, social benefit and environmental protection. **Responsible AI** turns those values into choices about design, testing and deployment. **AI governance** assigns decision rights and responsibilities and establishes the rules, procedures and oversight that make those practices repeatable. The deck connects these ideas to stakeholder trust, reputation and readiness for regulatory expectations (slides 1–6).

| Principle | Meaning and project evidence |
|---|---|
| Fairness and inclusion | Look for unequal errors or access, especially when historical data reflects discrimination. Check the population, label definitions and relevant group metrics. Fairness can involve different outcomes for different legitimate circumstances. |
| Transparency | Disclose AI use, its role, limitations and how affected users can question an outcome. |
| Explainability and interpretability | The deck distinguishes why a particular prediction was made from how the model generally works. Document training, feature selection and how a prediction feeds the decision. Saliency or layer-wise relevance propagation can help investigate which image regions influenced an output. Treat these explanations as evidence about the model's behaviour. |
| Robustness and veracity | Robustness is dependable behaviour on unusual or adversarial inputs. Veracity is factual accuracy. Use validation, anomaly detection, adversarial tests and fact checks against reliable references. The deck names RefChecker as an example. |
| Accountability | Name who owns the system and decisions. Version data, models and approvals so incidents can be reconstructed. Review risks throughout the lifecycle. |
| Privacy and security | Minimise sensitive data, control access, protect confidentiality and integrity, and give people meaningful information or control over collection and use. Consider leakage through model outputs as well as through storage. |
| Safety and avoidance of harm | Identify who could be harmed, how severe the harm could be and how likely it is. Test safeguards at the decision points where they matter. |

Slides 7–9 put the principles in context. ISO takes a standards and audit-oriented approach. The OECD principles group inclusive growth and well-being, human rights and fairness, transparency and explainability, robustness/security/safety, and accountability. The OECD material also points to public policy on research, capacity and cooperation. The REAIM 2024 military example brings together ethical compliance, human oversight, bias mitigation, transparency and robustness, with the lecture reporting 61 endorsers of the blueprint.

Slides 15–21 describe practices for making AI trustworthy. Bring in technical, policy, ethics and affected-user perspectives. Train staff, set up clear review and escalation, and incorporate diverse use cases and feedback during design. AI governance can extend corporate, IT, data, enterprise architecture and risk structures. AI systems introduce concerns about data provenance, opaque model behaviour and changing input patterns. The governance diagram links leadership and risk oversight with the AI centre of excellence, architecture, data governance and development teams.

### Singapore Model AI Governance Framework

Slides 22–24 identify the 2019 launch, the 2020 refresh and the 2024 generative AI framework. The two guiding principles are that AI decisions should be explainable, transparent and fair, and that AI systems should be human-centred. Four areas translate those principles into practice.

| Area | What to implement |
|---|---|
| Internal governance | Assign roles, approval authority, training and procedures for identifying, managing and escalating risk. |
| Human involvement | Determine the right oversight for the exact decision step and specify when a person must review or intervene. |
| Operations management | Govern data, bias, model choice, explainability, testing, monitoring and regular tuning. |
| Stakeholder interaction and communication | Make AI use and policies understandable, and provide feedback or review channels where appropriate. |

The Mastercard case (slides 25–28) uses initial risk scoring and mitigation planning. High-risk cases go to a governance council with the AI centre, data, privacy, security, data science and business representatives. Data and privacy officers check fitness for purpose, ethics and impact. Security leadership oversees security by design. Data scientists build, implement and share governance information. For a student team, the same role clarity can be demonstrated with named owners and documented reviews.

### Choose human involvement for a specific decision

| Mode | Who takes the action | Course example or interpretation |
|---|---|---|
| Human-in-the-loop | A human must actively approve or take the action. AI supplies information or a recommendation. | A person with authority reviews evidence and signs off before a consequential decision. |
| Human-over-the-loop | AI normally acts and a human monitors with authority to intervene or take over. | An operator reviews exceptions and can reverse or halt an automatic process. |
| Human-out-of-the-loop | AI executes the defined step with no operational human checkpoint. | The deck treats ordinary product recommendations, automated route generation and the Suade regulatory calculation step this way. |

Use probability and severity of harm together (slides 29–37). Consider what happens when a decision is wrong and whether the harm is reversible. Distinguish the route recommendation from the driver's action, or the production of a report from its approval. The SELENA+ notes describe the screening step as potentially autonomous and discuss clinician oversight at later decision points. Their lesson is to define the stage being classified. For safety-critical use, specify what evidence the operator receives, when takeover happens and how it is tested.

### Data, models and monitoring

Slides 38–49 describe three useful diagnoses of data bias.

- **Omission bias** is a coverage gap. A facial recognition dataset containing only Asian faces omits other populations it may encounter.
- **Stereotype bias** is skewed representation. Weekday vehicle counts from the central business district can underrepresent cyclists if generalised to all of Singapore.
- **Measurement bias** is systematic distortion in collection. A changed camera setting can introduce a colour pattern the model learns as a shortcut.

Check provenance, coverage and relevance. Evaluate proxies such as names, addresses and location, and whether labels or success metrics represent the underlying problem. Compare subgroup errors. The IBM AI Fairness 360 example uses COMPAS and reweighting. It compares metrics such as statistical parity difference, equal opportunity difference, average odds difference, disparate impact and the Theil index. Statistical parity focuses on selection rates and equal opportunity focuses on true-positive rates. Choose measures based on what kind of harm your application could cause. An aggregate score can conceal large group differences.

The deck's privacy lesson lists consent, purpose limitation, protection, retention limitation, transfer limitation and accuracy as selected PDPA topics. These are the topics discussed in the slides. In project terms, record what data you need, where it came from, who can see it, how it is secured and when it is removed.

When choosing a model, weigh explainability, repeatability, robustness, reproducibility, traceability, auditability and maintenance. Heatmaps may reveal background shortcuts, such as snow being used to distinguish wolves from dogs. The adversarial examples include a panda misclassified after a small perturbation and altered road signs used to illustrate physical attacks. Prioritise red teaming based on risk. Assign a monitoring owner and schedule reviews as data, user behaviour, objectives or risk tolerance change.

### Communication and sector context

Slides 50–55 distinguish three kinds of stakeholder interaction. Disclosure tells people whether and how AI is used, its benefits, safeguards and effects. Feedback lets users report concerns or inaccuracies. Decision review lets affected users request reconsideration of a specific material outcome. Consider opt-out by looking at harm, reversibility, cost, feasibility and the complexity of keeping parallel workflows. The Facebook slide illustrates disclosing both data collected and how it is used. The deck names MAS FEAT as the financial-sector example of Fairness, Ethics, Accountability and Transparency. ISAGO accompanies Singapore's Model Framework with self-assessment questions and examples.

### Generative AI risks and safeguards

| Risk in slides 56–61 | Evidence to collect in a project |
|---|---|
| Hallucinations | Compare claims and citations with vetted documents. Test for abstention when retrieval supplies insufficient evidence. |
| Privacy and confidentiality | Check whether prompts, logs, retrieved documents or outputs expose sensitive content. The deck highlights memorisation, membership inference and possible reconstruction of training data. |
| Disinformation, toxicity and cyber misuse | Test prompts likely to elicit harmful outputs and confirm controls work at the intended points. |
| Copyright concerns | Record sources and permissions for training or retrieval content and consider how generated material will be used. |
| Embedded bias | Test relevant users, dialects and scenarios in the final application. Foundation-model biases can propagate into many downstream systems. |
| Alignment and values | Define both useful in-scope answers and unsafe out-of-scope responses. Test for inappropriate answers and unnecessary refusals. |

Slides 62–66 list nine dimensions of the 2024 Model Governance Framework for Generative AI. **Accountability** assigns responsibilities across the supply chain. **Data** covers quality and responsible sourcing. **Trusted Development and Deployment** covers safety practices and disclosures. **Incident Reporting** establishes monitoring and reporting. **Testing and Assurance** includes common standards and independent assessment. **Security** adapts protections to new risks. **Content Provenance** helps people inspect origins through techniques such as watermarking and cryptographic provenance. **Safety and Alignment R&D** calls for investment and cooperation. **AI for Public Good** includes access, public-sector adoption, upskilling and sustainable development.

### Case discussion practice

| Slides | Case | Question to answer and evidence to discuss |
|---|---|---|
| 67 | Lavender, as presented in the lecture's discussion of investigative reporting | What does reported aggregate accuracy tell you about false positives, and where should independent verification occur when a decision is irreversible? Specify the population, denominator, error types and authority to stop action. |
| 68 | CCTV surveillance | How much footage is necessary? Discuss clear notices, retention, access auditing, privacy masking and human confirmation of alerts. |
| 69 | DBS anti-money-laundering filtering | How do you reduce false-positive alerts while continuing to surface suspicious transactions? Compare both error types, look for subgroup effects, define escalation and balance auditability with exposure of evasion details. |
| 70 | AI-assisted hiring or promotion | How might historical decisions and proxies disadvantage candidates? Evaluate subgroup results, test job relevance, name the accountable owner and define human review and recourse. |
| 71 | Unmanned retail | The example charges customers within 10 seconds of exit after tracking items taken or returned. Explain how they discover an incorrect charge, dispute it and get it corrected, and how the store handles notice, footage and retention. |

## 6. Ethical AI Implementation Guidelines

The student form adapts 11 of ISAGO's 64 questions. Fill in team number, admin number, student name and a project description. For every row, mark Yes, No or NA and use Remarks to document what you did, what evidence exists and any gap or applicability decision. Initiation means problem definition. Implementation covers model prototyping, testing and application development. The prompts below are paraphrased. Use the original form for submission.

| # | Stage | Guiding question | Evidence you could cite |
|---:|---|---|---|
| 1 | Initiation | Have you defined a clear purpose for using this AI solution? | Problem statement, user group and measurable objective |
| 2 | Implementation | Is the degree of human involvement appropriate to the decision? | Risk assessment, flow diagram, review or escalation test |
| 3 | Implementation | For a safety-critical system, can relevant personnel take over and see enough information to act? | Takeover protocol, evidence displayed to operators, test results or scope-based NA rationale |
| 4 | Initiation | Did you use appropriate data management and protection for customer or project-owner data? | Source permissions, access controls, retention and storage decisions |
| 5 | Implementation | Is the dataset relevant to the problem? | Coverage of target users, labels and deployment conditions |
| 6 | Implementation | If personal data is involved, was it collected for the intended purpose? | Documented collection purpose and permitted use, or NA rationale |
| 7 | Implementation | Is the data structured and machine understandable? | Schema, types, missing-value rules, preprocessing and validation |
| 8 | Implementation | If datasets were joined, were extraction, transformation and joining performed correctly? | Join keys, unmatched and duplicate counts, cardinality checks and examples |
| 9 | Implementation | Did you identify unintended biases and propose mitigation, especially omission and stereotype bias? | Coverage and subgroup analysis, sourcing or weighting decisions, results and remaining gaps |
| 10 | Implementation | Did you use distinct training, validation and test data? | Split code, overlap checks and record of when the test set was evaluated |
| 11 | Implementation | Can you explain how the deployed model functions and reaches a prediction? | Model selection and feature rationale, traced example and explanation of how the app uses the result |

The form groups Q1 under deployment objectives, Q2–3 under human involvement, and Q4–11 under operations management. In the remarks, a justified NA documents why a scenario does not apply. A No can identify a real gap and the action needed to close it. Tie any Yes to evidence a reviewer could inspect.

## 7. Practice Putting It Together

Use the hypothetical polyclinic example to connect the documents. Keep the ML and Gen AI acceptance tests separate so each failure has an identifiable cause.

| Step | Practice example |
|---|---|
| Research | Interview relevant users and observe enquiry patterns. Record which questions people can resolve through clinic information and which require staff. |
| Define | Draft a POV and HMW around helping users find administrative information or reach staff. Record the difference between observed evidence and a hypothesis. |
| Specify | Give the FAQ assistant a numbered requirement. WHEN the retrieved clinic material does not support an answer, the assistant SHALL return the agreed fallback and offer the defined human contact path. |
| Design | Keep the supervised classifier and FAQ RAG capability behind clear interfaces. Document vetted sources, acceptable outputs, error handling and where staff review applies. |
| Verify | Check supervised-model split integrity and errors by class. For Gen AI, run supported, unsupported, ambiguous and out-of-scope test questions. For the app, verify both capabilities through the normal UI. |
| Document | Commit the requirement, implementation and test evidence under your own account. Record significant AI suggestions and decisions in your AI Use Log. Link safeguards and verification to the checklist remarks. |
| Defend | Explain the training split, one failure mode, why you chose the acceptance test, and where in the code to change the fallback. Practise reproducing and isolating a seeded defect. |

### Self check

1. What evidence changed the deadline reminder problem from one of awareness to one of visibility and tracking?
2. Why were both engagement and late-submission rates measured? What would 87% engagement alone tell you?
3. Can you trace an observed user need through a numbered requirement, design choice, task, test and commit?
4. Which data split can guide hyperparameter choices? What can go wrong if you repeatedly tune against the held-out test split?
5. What is the difference between a faithful RAG answer and a relevant one?
6. Where is human intervention required in your own application, and which specific decision does it govern?
7. How would you detect omission bias, a proxy feature and measurement bias?
8. Which of the eleven ethics questions can you answer with project evidence today?
9. Pick one AI Use Log entry. Can you show what changed in Git and explain how you verified it?
10. Which checkpoint dates and AI-use rules require tutor confirmation?

### Source map

- IT2226 Project Guidebook v1.1, §§1–8, Annexes A and B, and rubrics.
- Design Thinking Worked Example, slides 1–19 and speaker notes.
- Spec-Driven Development, slides 1–14 and speaker notes.
- IT2226 Project Development and Resource Planning Guide, §§1–5.
- Responsible AI, slides 1–71, speaker notes and selected embedded diagrams.
- Ethical AI System Implementation Guidelines, instructions and eleven-question form.
