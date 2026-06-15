# (SOL) Potential Yield

**Purpose:** To give a projected solar energy yield based on effective solar panel area, solar irradiation, system efficiency, and derate factor.

---

## Formula

*`E = A × S × η × D`*

* *E* — Solar energy yield (kWh)
* *A* — Solar panel area (m²)
* *S* — Solar irradiation over modeled time period (kWh/m²)
* *η* — System efficiency
* *D* — Derate factor

---

## Interface Specification

```text
potential_yield(
    float panel_area_m2,
    float solar_irradiation_kwh_m2,
    float efficiency,
    float derate_factor
) -> float energy_yield_kwh
```

**Inputs:**

* `panel_area_m2` — a float representing effective solar panel area in squared meters
* `solar_irradiation_kwh_m2` — a float representing the cumulative solar energy received per square meter over the modeled time period in kWh
* `efficiency` — a float representing a ratio of useful electrical output to incoming solar energy
* `derate_factor` — a float representing multiplier used to adjust from theoretical DC power to real-world AC and various loss

> See [*Notes*](#notes) for further elaboration on *efficiency* and *derate factor*.

**Outputs:**

* `energy_yield_kwh` — a float representing the total energy yield in kWh

---

## Computational Definition

```text
potential_yield(
    float panel_area_m2,
    float solar_irradiation_kwh_m2,
    float efficiency,
    float derate_factor
) -> float energy_yield_kwh

    return (
        panel_area_m2
        * solar_irradiation_kwh_m2
        * efficiency
        * derate_factor
    )

```

---

## Assumptions

* `panel_area_m2` receives maximal sunlight exposure
* Storage capacity is not a limiting factor
* `solar_irradiation_kwh_m2` implies time period (see [*Notes*](#notes) for example)

---

## Units

* `panel_area_m2` — squared meters
* `solar_irradiation_kwh_m2` — kilowatt-hours per squared meter
* `energy_yield_kwh` — kilowatt-hours

---

## Constraints

* `panel_area_m2` must be greater than or equal to 0
* `solar_irradiation_kwh_m2` must be greater than or equal to 0
* `efficiency`:
  * must be greater than or equal to 0
  * must be less than or equal to 1
* `derate_factor`:
  * must be greater than or equal to 0
  * must be less than or equal to 1

---

## Notes

**Efficiency Formula**

*`η = Electrical Energy Output / Solar Energy Input`*

---

**Derate Factor**

A standard derate factor is *0.84* (though typically between *0.75* and *0.85* generally).

The overall derate factor is calculated by multiplying individual loss factors for:

* Temperature: Panels lose efficiency as heat rises (approx. 0.3–0.4% per °C above 25°C). 
* Soiling: Dust and dirt accumulation (typically 1–5% loss). 
* Shading: Obstructions reducing sunlight (variable, often 1–5%). 
* Inverter Efficiency: DC-to-AC conversion losses (typically 2–5%). 
* Wiring/Mismatch: Cable resistance and panel mismatch (typically 1–3%).

---

**Temporality Example**

Time is implicit in the solar irradiation variable (i.e., *solar energy accrued* kWh/m² *over modeled time period*):

Assuming the following solar irradiation benchmarks:

* 5 kWh/m² (daily)
* 200 kWh/m² (monthly)

Where:

* `panel_area_m2` — 100
* `efficiency` — 0.8
* `derate_factor` — 0.84

Daily yield:

```text
potential_yield(100, 5, 0.8, 0.84) -> 33.6
```

Monthly yield:

```text
potential_yield(100, 200, 0.8, 0.84) -> 13440
```
