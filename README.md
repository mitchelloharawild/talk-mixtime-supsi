

<!-- README.md is generated from README.qmd. Please edit that file -->

# Semantic vectors for forecasting

<!-- badges: start -->

<!-- badges: end -->

Slides and notes for a mixtime presentation to a research group at IDSIA SUPSI on 10 June 2026 in Lugano, Switzerland.

### Abstract

The `mixtime` R package provides a principled framework for representing time across multiple time zones, mixed granularities, and many calendar systems. Existing data structures for time are very limited, forcing analysts to misrepresent temporal semantics in order to use analysis and forecasting tools. For example, it is common to encode monthly data as dates using the first day of the month, which introduces silent downstream errors in analysis. Often it is too tricky to accurately encode time points, so time is ignored completely and numeric indices are used instead. The `mixtime` system treats granules as first-class extensible objects, connected via calendar algebra into a traversable graph that supports arithmetic and comparisons across granularities while preserving time zone characteristics. The result is a single vector representation of mixed-granularity time series that maintains full temporal semantics, suitable for use in time series analysis and forecasting temporal hierarchies.

### Structure

- Background / motivation
  - Semantic vectors for forecasting with fable
    - cross-temporal reconciliation
    - time-series visualisation
    - better modelling of time (e.g. holidays)
  - Representing time
    - Physically (astronomical, sound, civil,)
    - Artistically (indulgent garden clocks)
    - Computationally?
  - Inadequate representations of time
    - POSIXt/Date tz inconsistency
    - Data across multiple time zones
    - Observations at coarser granules
    - Representing multiple granules (e.g. temporal hierarchies)
    - Non-gregorian calendars
    - Mixed calendar systems
    
- Computational representations of time
  - Encoding types
    - Sequence-based
    - Offset-based
    - Component-based
  - Time types
    - Linear time
    - Cyclical time
    - Time durations
  - Time models
    - Discrete
    - Continuous
- Demonstration of mixtime
  - Calendars and time units - civil and astronomical time
  - Linear time, cyclical time, durations, and intervals
  - Continuous and discrete time
  - Arithmetic and comparisons
  - Floor/round/ceiling time
  - Sequences
  - Time formatting (the hardest part!)
- Applications of mixtime:
  - Australian CPI (quarterly -\> monthly)
  - Temporal hierarchies (`tsibble::aggregate_index()`)
  - Cross-temporal hierarchies (`tsibble::aggregate_index()` and
    `tsibble::aggregate_key()`)
- How it works
  - Time systems (civil / astronomical)
  - Calendar systems (extending time systems)
  - {vecvec} vectors of vectors
    - {mixtime} mixed granularity
    - {distributional} mixed shape
    - ...
- Overview of ggtime (time permitting bonus slides)
  - `scale_*_mixtime()`
  - `coord_loop()` / `coord_calendar()`
  - `geom_time_line()`
  - `position_time_civil()` / `position_time_absolute()`

### Format

1 hour block, aiming for 45 minute presentation with discussion.
