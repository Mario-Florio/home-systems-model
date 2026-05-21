# Home Systems Model Overview

*Home Systems Model* is an analysis framework for determining optimality and performance constraints of household systems.

---

**Index:**
- [Home Systems Model Overview](#home-systems-model-overview)
  - [Home](#home)
  - [Land Capacity (Capacity)](#land-capacity-capacity)
  - [Inhabitant Demand (Demand)](#inhabitant-demand-demand)
  - [Ideal Home](#ideal-home)

---

## Home

**Home:** The system(s) which emerge when an *inhabitant* takes up residence on a piece of *land* for a significant period of time.

---

## Land Capacity (Capacity)

An aspect of land or its improvements which contributes to satisfying *inhabitant demand*.

**Formal definition:**

```text
Land Capacity = {
    x | x is an aspect of land or its improvements which contributes to satisfying inhabitant demand
}
```

Or:

```text
Capacity = {
    x | x participates in the support of inhabitants
}
```

---

## Inhabitant Demand (Demand)

Any support required by persons on a plot of land.

**Formal Definition:**

```text
Demand = {
    x | x is required for inhabitant support
}
```

---

## Ideal Home

A system in which the land is capable of providing support for the demand of *n* inhabitant(s).

> The *ideal home* serves as a benchmark for assessment, not necessarily a success criterion.

**Formal Definition:**

*`Demand ⊆ Capacity`*

Also:

*`Demand ≤ Capacity`*

---
