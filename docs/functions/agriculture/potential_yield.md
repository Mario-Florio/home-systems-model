# (AGR) Potential Yield

**Purpose:** To give a projected caloric yield of a single mature harvest cycle for a select crop based on arable area.

---

## Formula

*`Y = A × D × K`*

* *Y* — Caloric yield (kcal)
* *A* — Arable area (sqft)
* *D* — Yield density (lb/sqft)
* *K* — Crops kilocaloric density (kcal/lb)

---

## Interface Specification

```text
potential_yield(
    float arable_area_sqft,
    CROP_PROFILE crop_profile
) -> int caloric_yield_kcal
```

> This function prioritizes immediate utility over agricultural precision.

**Inputs:**

* `arable_area_sqft` — a float representing the arable area of land in square footage
* `crop_profile` — an object containing relevant crop benchmarks
  * `yield_per_sqft_lb` — a float representing the amount crop yield per square foot in pounds
  * `kcal_per_lb` — an integer representing the amount of kilocalories per pound of select crop

**Outputs:**

* `caloric_yield_kcal` — an integer representing the total caloric yield in kilocalories

---

## Computational Definition

```text
potential_yield(
    float arable_area_sqft,
    CROP_PROFILE crop_profile
) -> int caloric_yield_kcal

    int caloric_yield_kcal

    float crop_yield_lb = arable_area_sqft * crop_profile.yield_per_sqft_lb

    caloric_yield_kcal = crop_yield_lb * crop_profile.kcal_per_lb

    return caloric_yield_kcal
```

> See [*Notes*](#notes) for an example implementation of Crop Profile.

---

## Assumptions

* `arable_area_sqft` has viable soil profile
* Climate is suitable for selected crop (via `crop_profile`)
* Sunlight and water availability are sufficient for viable growth
* Available arable area is fully utilized by the selected crop
* Crop reaches full mature harvest caloric yield

---

## Units

* `arable_area_sqft` — square feet
* `caloric_yield_kcal` — kilocalories

---

## Constraints

* `arable_area_sqft` must be greater than 0

---

## Notes

**Crop Profile Implementation Example**

```text
CROP_PROFILE {
    float yield_per_sqft_lb,
    int kcal_per_lb
}

# Use in a compiled benchmark data set

CROP_PROFILE[] crop_benchmarks = [

    potato: {
        yield_per_sqft_lb: 2.0,
        kcal_per_lb: 350
    },

    carrot: {
        yield_per_sqft_lb: 1.5,
        kcal_per_lb: 186
    },
    ...
]
```

> The above example is for demonstrating data structure. Benchmark examples are not based on authoritative data sets.

---
