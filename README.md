# Home Systems Model

A formal modeling framework for analyzing household systems in terms of demand, capacity, and their temporal and modal relationships.

---

## Overview

The Home Systems Model is a conceptual framework for representing a home as a system of interacting resource capacities and inhabitant demands. It supports structured decomposition of resources across domains (e.g., food, water, power), along with analysis across state, time, and evaluative dimensions.

The model is currently in early-stage development and is focused on establishing a stable conceptual architecture.

---

## Core Concepts

* **Demand:** Requirements necessary to support inhabitants.
* **Capacity:** Land resources that satisfy demand.
* **Ideal Home:** Benchmark for assessing home systems (I.e., *Demand ⊆ Capacity*).
* **Domain Decomposition:** Partitioning of demand and capacity into resource categories (e.g., food, water, power).
* **Modal Structure:** Representation of resources in different states (e.g., potential vs actual).
* **Temporality:** Time-based evolution of demand and capacity.
* **Evaluative Metrics:** Derived measures such as optimality, feasibility, and sustainability.

---

## Current Status

This project is currently in the conceptual modeling phase. The focus is on defining a coherent and extensible architecture rather than implementation or simulation.

Formalization, stochastic modeling, and optimization layers are not yet included.

---

## Documentation

* [**Model Overview**](./docs/model-overview.md) — An overview of major concepts and definitions
* [**Architecture**](./docs/architecture.md) — A breakdown of model architecture in terms of viewpoints
* [**(AGR) *Potential Yield***](./docs/functions/agriculture/potential_yield.md) — Function for projecting a select crops caloric yield over a single mature harvest cycle based on arable area
* [**(AGR) *Crop Benchmarks***](./docs/data/agriculture/crop-benchmarks.md) — Normalized crop benchmarks relevant to potential yield (*AGR*) usage

