# (PRCP) Potential Yield

**Purpose:** To give a projected water yield based on precipitation trends, catchment area, and system efficiency estimates.

---

## Formula

*`Y = A × P × E × C`*

* *Y* — Water yield (gallons)
* *A* — Catchment area (sqft)
* *P* — Precipitation (inches)
* *E* — System efficiency
* *C* — Conversion factor (gallons)

---

## Interface Specification

```text
potential_yield(
    float catchment_area_sqft,
    float precipitation_in
    float efficiency
) -> float water_yield_gal
```

**Inputs:**

* `catchment_area_sqft` — a float representing the effective catchment area in square footage
* `precipitation_in` — a float representing total projected precipitation over a defined time period in inches
* `efficiency` — a float representing system efficacy (e.g., runoff, splash loss, etc.)

> See [*Notes*](#notes) for examples of *efficiency* ratings and their meanings.

**Outputs:**

* `water_yield_gal` — a float representing the total volume of water yielded in gallons

---

## Computational Definition

```text
potential_yield(
    float catchment_area_sqft,
    float precipitation_in,
    float efficiency
) -> float water_yield_gal

    return (
        catchment_area_sqft
        * precipitation_in
        * efficiency
        * 0.623 # conversion factor
    )
```

> The value *0.623* represents an established *conversion factor* for precipitation yield — for every *1 inch* of precipitation over *1 square foot* of catchment area, *0.623 gallons* is accrued.

---

## Assumptions

* Storage capacity is not a limiting factor
* Water quality is not a concern
* `precipitation_in` implies time period (see [*Notes*](#notes) for example)

---

## Units

* `catchment_area_sqft` — square feet
* `precipitation_in` — inches
* `water_yield_gal` — gallons

---

## Constraints

* `catchment_area_sqft` must be greater than or equal to 0
* `precipitation_in` must be greater than or equal to 0
* `efficiency`:
  * must be less than or equal to 1
  * must be greater than or equal to 0

---

## Notes

---

**Efficiency Semantics**

| Rating | Meaning |
|--- |---|
| 1.0 | Ideal / no loss |
| 0.9 | Highly effective system |
| 0.8 | Conservative / realistic |
| <0.8 | Ineffective system |

> Note: Since *efficiency* represents system wide efficacy, sloped catchment areas should assume at most an efficiency of *0.9* to account for runoff loss. 

---

**Temporality Example**

Time is implicit in the precipitation variable (e.g., inches per month or per year).

Assuming the following precipitation benchmarks:

* 5 inches per month
* 50 inches per year

Where:

* `catchment_area_sqft` — 2000
* `efficiency` — 0.8

Monthly yield:

```text
potential_yield(2000, 5, 0.8) -> 4984
```

Annual yield:

```text
potential_yield(2000, 50, 0.8) -> 49840
```
