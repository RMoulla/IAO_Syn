---
name: needs-to-specification
description: >-
  Clarify an application need or a functional change through an interview of no
  more than five questions, then write specifications with observable acceptance
  criteria. Use to frame a business request, clarify scope, or turn a brief into
  specifications. Particularly suitable for development workshops using generative
  AI. Do not trigger for a simple question about skills or to code a feature that
  has already been specified.
---

# From Needs to Specifications

## Objective

Conduct an interview in the chat, then produce a functional specification that
can be used for design, development, and acceptance testing. Adapt the vocabulary
to the requester and preserve their stated choices. Remain independent of the
business domain and technologies.

## Interview Rules

- Ask no more than **five questions in total, including validation**. Reserve the
  last available question for validating the summary: at most four clarification
  questions, followed by one validation question.
- Ask **only one question per message**, addressing a single decision. Display
  `Question n/5`, then wait for the answer before continuing.
- Count every new request for information or a decision, including follow-ups,
  confirmations, and requests phrased as commands. Do not hide multiple questions
  in a single sentence or list.
- Reuse all information already provided. One answer may cover several topics:
  do not ask about them again just to follow a predefined questionnaire.
- Answer the user's questions without consuming a question if you are not asking
  them for any new information.
- Accept "I don't know", partial answers, or a refusal to answer. Record the
  uncertainty and use the remaining questions for the most useful decisions.
- Keep the question counter throughout the same scoping exercise, including after
  a correction or a resumed conversation. Change the budget only on the user's
  explicit instruction.
- If the user asks you to write immediately or stop asking questions, proceed
  directly to writing with the available information.

## 1. Prepare the First Question

Read the request, relevant exchanges, and documents provided or explicitly
identified. If a document is inaccessible, say so without attributing content to
it. Avoid a broad exploration of the project or information system.

Identify internally:

| Topic | Useful information |
| --- | --- |
| Purpose | Problem to solve and expected business outcome |
| Users | Target users and the action or decision to support |
| Scope | Main user journey, essential features, and explicit exclusions |
| Data | Inputs, sources, formats, outputs, and business rules |
| Constraints | Stated usage, integration, timing, or quality constraints |
| Acceptance | Behaviors that establish whether a feature meets its requirements |

Use this framework to select questions, without turning it into a form that must
be completed in full. First identify contradictions that could change the scope.

Briefly announce: "I'll clarify your needs with you in no more than five questions,
including validation, then write the specifications." Ask the first useful
question directly. If the need is already sufficiently described, move to the
summary without artificially using all four clarification questions.

## 2. Choose the Questions

After each answer, update the decisions and unknowns. Choose the question whose
answer would most affect the scope, main user journey, or acceptance testing.
Prioritize a significant contradiction, then the purpose and user journey, then
the data or business rules on which that journey depends.

Ask a concrete question. If helpful, suggest two or three possible answers while
making it clear that a free-form answer is welcome. Present these options as
proposals, never as choices that have already been made.

Example questions to select according to the context:

- "What decision should the user be able to make with the application?"
- "Which user journey absolutely needs to work in the first version?"
- "Which data source will be used for this journey?"
- "What behavior do you expect when a required piece of data is missing?"

Do not impose a programming language, architecture, or data model at this stage.
Record technical constraints the user has already chosen.

For a predictive application, identify the event to predict, its time horizon,
the data available at prediction time, and how the result will be used. Dedicate
one question to a decisive ambiguity or record it among the points to clarify.
Do not attribute performance, a threshold, or a probabilistic interpretation to
the model unless these have been established.

## 3. Close the Interview

Move to the summary as soon as the main user journey is understandable, after the
fourth clarification answer, or at the user's request.

Present a short summary covering:

- the objective and target user;
- the selected user journey and features;
- known data and constraints;
- any proposals and unresolved points.

If the user has not already asked you to write and a question remains available,
ask the closing question, numbered using the current counter:

> Do you approve this summary so I can proceed to writing the specifications?

Wait for the answer. Do not add another closing question.

- If the user agrees, write the specifications.
- If they provide corrections, incorporate them. If they are sufficient to write,
  produce the document; otherwise, use only the remaining question budget. Once
  the budget is exhausted, write a draft that makes the remaining ambiguities visible.
- If they explicitly refuse to continue, stop and retain the summary.
- If there is no answer, leave the summary pending; do not treat silence as agreement.

After the fifth question, do not request any more information or validation.
Unsolicited additions from the user can still be used. Approval of the scope is
neither proof of feasibility nor a performance measurement.

## 4. Write the Specifications

Write in English unless requested otherwise, and adapt the length to the project.
Follow the requested format or the existing document. Otherwise, use this structure:

### Objective and Scope

Describe the problem, users, expected outcome, and agreed boundaries. Only list
exclusions that have been stated or approved; leave everything else unspecified.
Indicate the status: `draft`, `scope approved`, or `revised after corrections`,
according to the exchange that actually took place.

### User Journey

Describe the main journey in order: starting point, user actions, application
responses, and final outcome. Add variants that materially change the expected
behavior.

### Requirements and Acceptance Criteria

Assign a stable identifier to each requirement: `F-01`, `F-02`, etc. For each one,
specify the behavior, necessary business rules, and acceptance criteria. Use user
stories if they make the intended use clearer.

Write criteria in an observable form: initial situation, action, expected result.
Cover the normal case and errors relevant to the need. Replace vague adjectives
such as "fast" or "intuitive" with verifiable behavior; if a measurement is missing,
flag it without inventing a value.

Distinguish agreed requirements, the agent's proposals, and decisions still to be
made. A criterion that introduces a new functional choice remains a proposal until
that choice has been accepted.

Example, only if rejecting incomplete files has been chosen:

> F-02 — Check required columns.
> Given a file missing a required column defined in the input contract, when the
> user starts the import, then the import is rejected and the name of the missing
> column is displayed.

### Data and Constraints

Describe inputs, outputs, and known validation or calculation rules. Include
explicitly stated constraints. Distinguish data observed in a file from business
rules confirmed by the user. Do not automatically add authentication, an API,
hosting, or an MLOps setup.

### Points to Clarify

For each missing piece of information or contradiction, state its impact and any
part of the work it prevents from being finalized. Present these points as a
register of uncertainties without starting another questionnaire. Assign an owner
or deadline only if they are known.

## 5. Check and Deliver

Before delivery, verify that:

- the counter has not exceeded five questions unless the budget was explicitly changed;
- the user's choices and corrections are preserved;
- proposals, decisions, and unknowns are distinguished;
- each agreed feature has an observable criterion, or states what is missing to define one;
- the criteria describe functional compliance without claiming that tests have
  been run or performance has been measured;
- the document does not introduce unstated business or technical decisions.

In an environment where files can be created, save the document to the requested
location. In an open project, default to `specifications.md` at the root. Read an
existing document before updating it and preserve elements unrelated to the
request. In a chat without file access, provide the complete document in the response.

Finish by identifying the document produced and the main decisions still to be
made. Stop at the specification; begin design or development when the user asks.
