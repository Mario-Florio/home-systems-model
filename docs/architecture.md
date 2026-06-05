# Model Architecture

Architecture serves to keep abstractions organized and coherent so that it may be applied consistently across use cases. It provides the means for moving from theory to practice.

---

## Architectural Principle

Architecture is organized by orthogonal viewpoints defined by stakeholder concerns.

---

### Stakeholders

**Developers:** Anyone engaged in the act of building or design model infrastructure.

**Consumers:** Anyone interested in using the model with the goal of analyzing home systems.

---

## Viewpoints

### Domain

**Concern:** How can resource sets be partitioned into analyzable subsets?

By identifying target domains, *demand* and *capacity* can be partitioned into subsets.

Example domains:

* Food
* Water
* Power

Example of derived subsets:

```text
Capacity = {
    Caloric Yield,
    Water Availability,
    Power Generation,
    ...
}

Demand = {
    Caloric Requirements,
    Hydration Needs,
    Power Usage,
    ...
}
```

> These examples are neither exhaustive nor prescriptive. Domains may be defined as use cases demand.

---

### Modal Types

**Concern:** In what state should resource sets be modeled?

Sets need context for their value to be interpreted practically. Applying modes of existence (or state) reduces abstraction ambiguity of select sets.

> The following examples are non-exhaustive.

---

#### Potential vs Actual

Resource sets can be understood as being possible or realized.

Example for land capacity:

| | Potential | Actual |
|--- |--- |--- |
| Food | Capacity to produce crops | Capacity of crops produced |
| Water | Capacity to capture water | Capacity of available water |
| Power | Capacity to produce power | Capacity of stored power |

---

### Temporality

**Concern:** How do capacity and demand evolve over time?

Introducing time allows sets to be modeled dynamically, permitting the analysis of time-based performance and projections.

Example notation:

*`Capacity(t) + Storage(t) ≥ Demand(t)`*

Example time frames:

* Seasonal
* Annual
* Long term

---

#### Stocks & Flows

Time also introduces the distinction between *stocks* and *flows*.

**Stock:** Quantity existing at any moment (state).

**Flow:** Rate at which quantity increases/decreases over time (process).

Examples:

| | Stock | Flow |
|--- |--- |--- |
| Food | Pantry | Crop growth rate |
| Water | Reservoir volume | Rainfall per day |
| Power | Battery charge | Solar generation rate |

---

### Evaluative Metrics

**Concern:** How can system states be mapped to evaluative metrics?

From the relation of above views we can derive metrics for certain uses cases.

---

#### Optimality

Represents how efficiently a system realizes its theoretical productive potential in practice. Measures the percentage of potential capacity that is realized as actual capacity.

*`optimality% = actual_capacity / potential_capacity * 100`*

---

#### Feasibility

Represents the degree to which a system can satisfy required demand under its available capacity constraints. Measures the percentage of demand that can be satisfied by available capacity.

*`feasibility% =  ((potential_capacity - overhead_loss) / demand) * 100`*

| Value | Meaning                  |
| ----- | ------------------------ |
| 50%   | insufficient             |
| 100%  | exact sufficiency        |
| 200%  | double required capacity |

---

#### Sustainability

Represents the degree to which a system can sustain its own productive capacity without self-exhaustion. Measures the percentage of potential capacity that remains after sustaining the system itself.

*`sustainability% = (1 - overhead_loss / potential_capacity) * 100`*

| Value | Meaning                         |
| ----- | ------------------------------- |
| 100%  | no sustaining overhead          |
| 80%   | efficient                       |
| 50%   | half output consumed internally |
| 0%    | entirely self-consuming         |
| <0%   | unsustainable                   |
