## Dev Guidances

### Purpose
This repository aims to develop a set of guidelines, standards, norms, and processes for the daily operations of development teams, based on past experiences. These are continuously improved in practice to create a comprehensive, executable system covering all aspects of work.

In addition to serving as a reference for daily development tasks, the content of this repository can also be used as a guide for other technical teams such as research and ops teams.

----

### Concepts
In the following explanations, we attempt to distinguish the strictness of requirements using `MAY`, `SHOULD`, `MUST`, `SHOULD NOT`, and `MUST NOT`.

#### Checklist
A checklist is a list of things, usually used to verify if tasks have been completed or items exist.

When compiling a checklist, the following should be followed:

- Each item should be a concise noun or verb, avoiding unnecessary adjectives, adverbs, or other modifying elements.
- Optional items may be included, but clear conditions should be noted.
- Items can have a hierarchical relationship, avoiding branches and dependencies.

#### Norms
Norms are a collection of suggestions and practices that can improve quality for a specific scenario. Here, we primarily take the meaning of `proposal`, to avoid overlap and conflict with `standards`.

When compiling norms, the following should be followed:

- Suggestions and practices should be based on practical experience.
- Some tolerance can be included; suggestions can be gradually downgraded from the highest standards, and practices can be gradually upgraded from the lowest standards. However, measurement scales and analysis of usage scenarios should be provided to avoid a simple list.
- The implementation, scope, and strictness of norms should be decided by the team.


#### Standards
Standards are the refined and more enforceable version of some norms.

When compiling standards, the following should be followed:

- Each standard should include precise preconditions.
- Each standard must include evaluation rules, which should yield a simple binary result regarding compliance.
- The implementation of standards must be mandatory and should include handling methods for non-compliance.


#### Process
A process is the result of breaking down a complete action into multiple steps.

When compiling a process, the following should be followed:

- There should be only one "entry" step and a few "termination" steps.
- Each step should involve at least one action.
- Each step should be associated with at least one `checklist`, `norm`, `standard`, or other `process`.
- When there are branching or dependency relationships between two steps, precise preconditions should be included.

----

### Definition of Concepts

#### Process and Checklist
- A process can be derived from a checklist, norm, or standard; this transformation should still follow the requirements for compiling a process. For example, if a standard does not involve the execution of other checklists, norms, standards, or processes, it should remain in standard form and avoid being elevated to a process.
- Conversely, a process can be downgraded to a checklist, norm, or standard; for example, if a process can be simplified and most branches and dependencies removed, it can be reduced to a checklist.

#### Norms and Standards
- Upgrading norms to standards requires at least three months of execution and reaching consensus within the team on the details of execution.
- Standards that lack enforcement power or cannot be judged should first be downgraded to norms.
