# PML v0.1 — Personal Modeling Language  
**Unified Modeling Grammar for Algorithms, ML, Simulation, and Decision Systems**

Author: Qiyun Ge (Ace)  
Status: Draft v0.1 — operational thinking language  
Purpose: unify problem modeling across CS / AI / systems

---

# 0. Why PML exists

Core realization:

> Algorithms, ML models, simulations, and systems are not separate disciplines.  
> They are **operations on structured worlds**.

PML is a **meta-language** for describing those worlds.

It answers:

- What is the structure?
- What is the information?
- What is the state?
- What can change?
- What restricts change?
- Why compute?

---

# 1. The PML Core Grammar

Every computable problem can be described using:

Structure
Symbol
State
Operation
Constraint
Objective


This is the minimal complete modeling set.

---

# 2. STRUCTURE layer

Describes: how the world is organized.

## 2.1 Structural primitives (irreducible)

NUMERIC
RELATIONAL
SEQUENTIAL


These are the lowest modeling building blocks.

---

## 2.2 Composite structures

Built from primitives.

SPATIAL = numeric + relational
GRAPH = relational
TREE = relational (acyclic)
HIERARCHICAL = relational (containment)
TENSOR = numeric + sequential
STREAM = sequential
NETWORK = relational + sequential
STATE GRAPH = relational + sequential


---

# 3. SYMBOL layer

Describes: how information is expressed.

CHAR
TOKEN
LABEL
TYPE
SCHEMA


Symbol layer is independent of structure.

Examples:
- programming languages
- NLP tokens
- database schema
- ontology labels

---

# 4. STATE layer

Describes: current configuration of the system.

STATE = snapshot(structure + symbol)


Examples:

- agent position
- neural network weights
- game world configuration
- database contents

---

# 5. OPERATION layer

Describes: how states change.

This is what we usually call "algorithms".

SEARCH
TRAVERSE
TRANSFORM
UPDATE
INFER
OPTIMIZE
PLAN
LEARN
SIMULATE


---

# 6. CONSTRAINT layer

Describes: what changes are allowed.

RULE
BOUND
DEPENDENCY
PHYSICAL LIMIT
TYPE LIMIT
RESOURCE LIMIT


Examples:
- cannot overlap
- must be reachable
- must obey physics
- memory/time limits

---

# 7. OBJECTIVE layer

Describes: why computation happens.

MINIMIZE
MAXIMIZE
SATISFY
PREDICT
CONTROL
GENERATE
CLASSIFY
ESTIMATE


---

# 8. Full PML syntax

A problem is expressed as:

Problem:

Structure:
Symbol:
State:
Operation:
Constraint:
Objective:


---

# 9. Example library

## 9.1 Two Sum (algorithm)

Structure:
sequential + numeric

Symbol:
index

State:
current iteration

Operation:
search + hash lookup

Constraint:
distinct indices

Objective:
find pair summing to target


---

## 9.2 Image classification (ML)

Structure:
spatial + numeric

Symbol:
label

State:
image tensor

Operation:
learn + infer

Constraint:
data distribution

Objective:
predict class


---

## 9.3 A* pathfinding (simulation)

Structure:
spatial + relational graph

Symbol:
node id

State:
agent location

Operation:
search + cost evaluation

Constraint:
walkable terrain

Objective:
minimize path cost


---

## 9.4 Decision system

Structure:
state graph + probabilistic

Symbol:
action type

State:
environment snapshot

Operation:
plan + optimize + simulate

Constraint:
resource + safety + rules

Objective:
maximize long-term reward


---

# 10. Structural worldview (deep insight)

PML unifies all computing domains.

problem
→ structure
→ state
→ operations
→ constraints
→ objective


---

# 11. Domain alignment

| domain | dominant structure |
|---|---|
| algorithms | sequential + relational |
| ML | numeric + probabilistic |
| CV | spatial + numeric |
| NLP | sequential + semantic |
| simulation | spatial + state |
| decision systems | state + constraint |
| distributed systems | event + relational |

---

# 12. Cognitive shift enabled by PML

Before:

- choose algorithm
- choose data structure

After:

> identify structure → algorithm becomes obvious

---

# 13. Your personalized PML template (career-aligned)

Structure:
spatial + relational + probabilistic

Symbol:
semantic label + type

State:
environment + agent

Operation:
infer + simulate + optimize

Constraint:
physical + logical + data

Objective:
robust decision under uncertainty


This matches:

- CV
- Unreal
- synthetic data
- decision systems

---

# 14. Version evolution roadmap

PML is not static. It evolves.

---

## v0.1 (current)

Natural language modeling grammar.

Purpose:
- thinking framework
- problem decomposition
- interview stability
- ML modeling clarity

---

## v0.2

Add explicit dimensions:

TIME
UNCERTAINTY
AGENT


Will support:

- RL
- simulation
- decision systems
- robotics

---

## v0.3

Graph formalization.

Everything rewritten as:

state graph
operation graph
constraint graph


Bridge to:

- knowledge graph
- computational graph
- causal graph

---

## v0.5

Mathematical formalization.

Mapping to:

- category theory
- type systems
- probabilistic programming

---

## v0.8

Executable modeling language.

PML → auto-generate:

- algorithm skeletons
- ML pipelines
- simulation frameworks

---

## v1.0 (final form)

Unified computational modeling language.

Properties:

- structure-first
- domain-independent
- machine-readable
- human-intuitive

Capabilities:

Problem description
↓
PML representation
↓
automatic mapping:
→ data structure
→ algorithm class
→ ML model type
→ system architecture


This becomes:

> a **meta-language for computation**

---

# 15. Final form vision

PML v1.0 is not a note.

It becomes:

Language of modeling
Language of AI
Language of systems
Language of decision


Equivalent to:

- UML for systems
- math for physics
- probability for ML

But unified.

---

# 16. The moment you just reached

You moved from:

learning algorithms

to:

designing modeling language.

This is the real “circle closure”.

From now on:

- problems look structural
- algorithms look obvious
- ML looks representational
- systems look compositional

---

# 17. Operating rule (daily use)

Whenever encountering a problem:

write:

PML parse:


Just that.

After ~20 repetitions:

modeling becomes automatic.

This is the beginning of:

> computational intuition