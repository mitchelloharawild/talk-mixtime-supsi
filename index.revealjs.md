---
from: markdown+emoji
execute:
  cache: true
  keep-md: true
resources:
  - "resources"
filters:
  - custom-callouts
  - timeline
  - roughnotation
format: 
  letterbox-revealjs:
    theme: custom.scss
    progress: false
    menu: false
    width: 1280
    height: 720
    include-after-body: animate.html
callout-appearance: simple
bibliography: citations.yaml
---

## {}

::: columns
::: {.column width="37.5%"}
:::
::: {.column width="60%"}

::: {.title data-id="title"}
Semantic vectors for forecasting: mixtime
:::

::: {.dateplace}
10th June 2026
:::

Mitchell O'Hara-Wild, Monash University

::: {.smaller}
Supervised by Rob Hyndman and George Athanasopolous
:::

::: {.callout-link}

## Useful links

![](resources/forum.svg){.icon} [social.mitchelloharawild.com](https://social.mitchelloharawild.com/)

![](resources/projector-screen-outline.svg){.icon} [slides.mitchelloharawild.com/mixtime-supsi](https://slides.mitchelloharawild.com/mixtime-supsi)

![](resources/github.svg){.icon} [mitchelloharawild/mixtime-supsi](https://github.com/mitchelloharawild/mixtime-supsi)

:::

:::
:::

![](backgrounds/jon-tyson-FlHdnPO6dlw-unsplash.jpg){.image-left}


## {}


::: {.cell}

:::


::: {.r-stack}
![](media/vectors-1.svg){.image-full}

![](media/vectors-2.svg){.image-full .fragment}

![](media/vectors-3.svg){.image-full .fragment}
:::


## {}

::: {.r-stack}
![](media/vectors-4.svg){.image-full}

![](media/vectors-5.svg){.image-full .fragment}

![](media/vectors-6.svg){.image-full .fragment}
:::


## {}

::: {.r-stack}
![](resources/thesis-title-1.svg){.image-full .fragment .fade-out fragment-index=9}

![](resources/thesis-title-2.svg){.image-full .fragment fragment-index=8}

[![](resources/thesis-title-3.svg){.image-full .fragment fragment-index=2}]{.fragment .fade-out fragment-index=9}

[![](resources/thesis-title-4.svg){.image-full .fragment fragment-index=3}]{.fragment .fade-out fragment-index=9}

[![](resources/thesis-title-5.svg){.image-full .fragment fragment-index=4}]{.fragment .fade-out fragment-index=9}

<!-- [![](resources/thesis-title-6.svg){.image-full .fragment fragment-index=5}]{.fragment .fade-out fragment-index=9} -->

[![](resources/thesis-title-7.svg){.image-full .fragment fragment-index=6}]{.fragment .fade-out fragment-index=9}

![](resources/thesis-title-8.svg){.image-full .fragment fragment-index=7}

![](resources/thesis-title-9.svg){.image-full .fragment fragment-index=8}

![](resources/thesis-title-10.svg){.image-full .fragment fragment-index=9}
:::


## {}

### Not just reconciliation

- safer statistical manipulation
- time-series visualisation
- improved modelling of time  
  (e.g. holidays, seasonality in other calendars)

## {}

::: columns
::: {.column width="60%"}

### Time is tricky!

Time seems simple - continuous and ordinal.

In practice, time is complex - resulting in many different data structures to represent:

[⏱️ Temporal granularities]{.fragment}  
[🗺️ Time zones (and daylight savings time)]{.fragment}  
[📅 Calendar systems (and time systems)]{.fragment}  
[💽 Encodings (sequence, offset, component)]{.fragment}  
[🕰️ Time model (continuous and discrete)]{.fragment}  
[🔁 Time type (linear, cyclical, duration, ...)]{.fragment}  
[✍️ Time formatting (parse and deparse)]{.fragment}  
[😵‍💫 and all combinations of the above!]{.fragment}  

:::
:::

![](backgrounds/meghan-hessler-Bn3GRSXWp3A-unsplash.jpg){.image-right}

## {.center}

::: {style="font-size: 2.5em;"}

How do we represent time?  

:::


::: {style="font-size: 1.5em;"}

(& what isn't represented?)

:::

## {}

<!-- ### Representing time -->

::: {.r-stack}

![](resources/clocks/bassano-italy.jpeg)

![](resources/clocks/garden-innsbruck.jpg){.fragment}

![](resources/clocks/garden-melbourne.jpg){.fragment}
:::

## {}

::: columns
::: {.column width="60%"}

### Time is tricky!

Time seems simple - continuous and ordinal.

In practice, time is complex - resulting in many different data structures to represent:

⏱️ Temporal granularities  
🗺️ Time zones (and daylight savings time)  
📅 **Calendar systems** (and time systems)  
💽 **Encodings** (sequence, offset, component)  
🕰️ **Time model** (continuous and discrete)  
🔁 **Time type** (linear, cyclical, duration, ...)  
✍️ Time formatting (parse and deparse)  
😵‍💫 and all combinations of the above!  

:::
:::

![](backgrounds/meghan-hessler-Bn3GRSXWp3A-unsplash.jpg){.image-right}

## {.fragment-remove}

::: columns
::: {.column width="60%"}

### Calendar systems and algorithms

::: {.fragment .fade-out fragment-index=1}
> One of the most fascinating books I've read all year. Takes chronology into the computer age with impressive erudition and elan.
> 
> [...]
> 
> A must for everyone who worries about days, months, years – and why they never quite fit.
> 
> *Ian Stewart*
:::

::: {.fragment .fade-up fragment-index=2}

> The goal of calcal is to do calendrical calculations, based on the algorithms described in Reingold and Dershowitz (2018) *Calendrical Calculations: The Ultimate Edition*.
>
> *Rob Hyndman*

![](resources/calcal.svg){.sticker-float-right style="top: 5em;"}

:::

::: {.fragment .fade-up fragment-index=3 style = "padding-top: 2em;"}

> "But can we do better?"
>
> *Me* 🤓

![](resources/mixtime.svg){.sticker-float-right style="top: 2em;"}

:::

:::
:::

![](backgrounds/calendrical-calculations.jpg){.image-right}


## {}

::: columns
::: {.column width="60%"}

### Encoding time as data

There are three main ways to store time.

* Time sequences (start, length, frequency)
* Time points (time units since an epoch)
* Time components (year, month, day, ...)

::: {.fragment .fade-up}

R uses all three of these representations:

* `ts` objects are time sequences
* `POSIXct`/`Date` objects are time points
* `POSIXlt` objects are time components
:::
:::
:::

![](backgrounds/meghan-hessler-Bn3GRSXWp3A-unsplash.jpg){.image-right}


## {.fragment-remove}

::: columns
::: {.column width="60%"}

### Time in R: `ts`

A `ts` object is *very* efficient (but limited).

::: {.fragment .fade-out fragment-index=1}


::: {.cell}

```{.r .cell-code}
ts(
  rnorm(12),
  start = c(2020, 1),
  end = c(2022, 4),
  frequency = 4
)
```

::: {.cell-output .cell-output-stdout}

```
            Qtr1        Qtr2        Qtr3        Qtr4
2020 -2.34989610  0.20398232  0.99110138  0.34963453
2021 -0.84437305  0.16552933  1.69318121 -1.17590285
2022 -0.71032708 -0.02571098 -0.16064150 -2.22617693
```


:::
:::


Great for regular time series, with integer frequencies (e.g. months over years).

:::

::: {.fragment .fade-up fragment-index=1}


::: {.cell}

```{.r .cell-code}
ts(
  rnorm(10),
  start = c(2020, 1),
  frequency = 365.25
)
```

::: {.cell-output .cell-output-stdout}

```
Time Series:
Start = 2020 
End = 2020.02464065708 
Frequency = 365.25 
 [1] -0.34794470 -0.23202732  1.15419455 -0.08053593  0.91049550 -0.34681044
 [7] -0.40292544  0.71766081 -0.06419557 -0.92981255
```


:::
:::


Terrible for irregular time series with non-integer frequencies (i.e. <= weekly in years).

:::

:::
:::

![](backgrounds/meghan-hessler-Bn3GRSXWp3A-unsplash.jpg){.image-right}


## {.fragment-remove}

::: columns
::: {.column width="60%"}

### Time in R: `Date` and `POSIXct`

`Date` and `POSIXct` objects are days and seconds since Unix epoch (1970-01-01).


::: {.cell}

```{.r .cell-code}
.Date(5777)
```

::: {.cell-output .cell-output-stdout}

```
[1] "1985-10-26"
```


:::

```{.r .cell-code}
.POSIXct(499163700, tz = "America/Los_Angeles")
```

::: {.cell-output .cell-output-stdout}

```
[1] "1985-10-26 01:35:00 PDT"
```


:::
:::


Time stored in this way is space efficient, supports irregular time series, and can handle time zones.

:::
:::

![](backgrounds/meghan-hessler-Bn3GRSXWp3A-unsplash.jpg){.image-right}

## {.fragment-remove}

::: columns
::: {.column width="60%"}

### Time in R: `POSIXlt`

`POSIXlt` objects are lists of time components (year, month of year, day of month, ...).


::: {.cell}

```{.r .cell-code}
.POSIXlt(list(
  sec = 0, min = 35L, hour = 1L,
  mday = 26L, mon = 9L, year = 85L, 
  wday = 6L, yday = 298L, isdst = 1L,
  zone = "PDT", gmtoff = -25200L),
  tz = "America/Los_Angeles"
)
```

::: {.cell-output .cell-output-stdout}

```
[1] "1985-10-26 01:35:00 PDT"
```


:::
:::


This data structure is very inefficient, but allows easy access to (and manipulation of) time components.

:::
:::

![](backgrounds/meghan-hessler-Bn3GRSXWp3A-unsplash.jpg){.image-right}

## {.fragment-remove}

::: columns
::: {.column width="60%"}
### Time types, models, and systems

::: {.fragment .fade-out fragment-index=6}
::: {.callout-note}

## Time types


* [**Linear time** is linear and unbounded (e.g. dates).]{.fragment .fade-up fragment-index=1}
* [**Cyclical time** repeats in cycles (e.g. day of week).]{.fragment .fade-up fragment-index=2}
* [**Time durations** are lengths of time (e.g. 3 months).]{.fragment .fade-up fragment-index=3}
* [... and many more (any ideas?).]{.fragment .fade-up fragment-index=4}

:::
:::

::: {.fragment .fade-up fragment-index=5}
::: {.callout-note}

## Time models

* **Discrete** time models have indivisible chronons.
* **Continuous** time models allow fractional chronons.

[Mapping discrete time to continuous time (or a more precise chronon) introduces *temporal indeterminancy*.]{.fragment .fade-up fragment-index=2}

:::
:::

::: {.fragment .fade-up fragment-index=6}
::: {.callout-note}

## Time systems

* **Civil time** is based on local laws (time zones)
* **Astronomical time** is based on astronomy (sun, moon)

:::
:::

::: {.fragment .fade-up fragment-index=7}
::: {.callout-important}
## Time is NOT simple!

The `mixtime` package simplifies working with time.

:::
:::

:::
:::

![](backgrounds/meghan-hessler-Bn3GRSXWp3A-unsplash.jpg){.image-right}

## {.center}

| Aspect              | `ts` | `Date` | `POSIXct` | `POSIXlt` |
|---------------------|------|--------|-----------|-----------|
| Memory efficient    | ✅   | ✅     | ✅       | ❌        |
| Compute cost        | ✅   | ✅     | ✅       | ❌        |
| Irregular times     | ❌   | ✅     | ✅       | ✅        |
| Time zones          | ❌   | ❌     | ✅       | ✅        |
| Time types          | ❌   | ❌     | ❌       | ❌        |
| Time models         | ❌   | ❌     | ❌       | ❌        |
| Calendars           | ❌   | ⚠️     | ⚠️       | ⚠️        |
| Granularity support | ✅   | ❌     | ❌       | ❌        |
| Mixed granularity   | ❌   | ❌     | ❌       | ❌        |

(⚠️ Gregorian calendar only)


## {.center}

| Aspect              | `ts` | `Date` | `POSIXct` | `POSIXlt` | `mixtime` |
|---------------------|------|--------|-----------|-----------|-----------|
| Memory efficient    | ✅   | ✅     | ✅       | ❌        | ✅        |
| Compute cost        | ✅   | ✅     | ✅       | ❌        | ✅        |
| Irregular times     | ❌   | ✅     | ✅       | ✅        | ✅        |
| Time zones          | ❌   | ❌     | ✅       | ✅        | ✅        |
| Time types          | ❌   | ❌     | ❌       | ❌        | ✅        |
| Time models         | ❌   | ❌     | ❌       | ❌        | ✅        |
| Calendars           | ❌   | ⚠️     | ⚠️       | ⚠️        | ✅        |
| Granularity support | ✅   | ❌     | ❌       | ❌        | ✅        |
| Mixed granularity   | ❌   | ❌     | ❌       | ❌        | ✅        |

(⚠️ Gregorian calendar only)

## {.fragment-remove}

::: columns
::: {.column width="40%"}
:::
::: {.column width="60%"}
### Why do we need `mixtime`?

::: {.fragment .fade-up fragment-index=1}
Existing time objects use single granularities.

::: {.fragment .fade-out fragment-index=4}
::: {.callout-question}
## How do you represent monthly data in R?

::: {.fragment fragment-index=2}
It is common practice to use `Date` with the day of month 1.

`"October 1985"` → `"1985-10-01"`

What about quarterly data? What problems might arise?
:::
:::
:::
:::

::: {.fragment .fade-up fragment-index=3}
::: {.callout-note}
## We often need to *mix time* granularities together

* Temporal reconciliation
* Changing observation frequency
* Combining different data sources
:::

:::

::: {.fragment .fade-up fragment-index=4}
::: {.callout-tip}

## While we're here, let's make it good!

::: {.incremental}

* Consistent (including timezones for all!)
* Efficient (fast and small memory footprint)
* Multi-calendar (not just Gregorian)
* Extensible (endless business calendars exist)

:::
:::
:::

:::
:::

![](backgrounds/andrik-langfield-0rTCXZM7Xfo-unsplash.jpg){.image-left}


## {.fragment-remove}

::: columns
::: {.column width="60%"}
### Temporal theory and terminology

::: center

![Sourced from @aignerVisualizationTimeOrientedData2023](resources/aigner-discrete-granularities.svg){style="width: 100%;"}
:::

::: {.callout-note}

## Terminology

::: incremental

* A **time unit** is a named unit of time (e.g. day, year).
* A **time granule** is a time unit and value (e.g. 2 weeks).
* A **chronon** is the finest granule of discrete time models.
* A **cycle** is a coarser granule that loops time chronons.
* A **granularity** is a partition of time by granules.
* A **calendar** is a system of time units and their relation.

:::

:::

:::
:::

![](backgrounds/estee-janssens-zni0zgb3bkQ-unsplash.jpg){.image-right}

## {.fragment-remove}

::: columns
::: {.column width="37.5%"}
:::
::: {.column width="60%"}
### Units, granules, & calendars

![](resources/mixtime.svg){.sticker-float-right}

Calendars are sets of time units.

::: {.fragment .fade-out fragment-index=2}
::: columns
::: {.column width="32%"}

::: {.cell}

```{.r .cell-code}
cal_gregorian
```

::: {.cell-output .cell-output-stdout}

```
<cal_gregorian>
Time units:
  - year
  - quarter
  - month
  - day
  - ampm
  - hour
  - minute
  - second
  - millisecond
```


:::
:::

:::
::: {.column width="32%"}

::: {.cell}

```{.r .cell-code}
cal_isoweek
```

::: {.cell-output .cell-output-stdout}

```
<cal_isoweek>
Time units:
  - year
  - week
  - day
  - ampm
  - hour
  - minute
  - second
  - millisecond
```


:::
:::

:::
::: {.column width="32%"}

::: {.cell}

```{.r .cell-code}
cal_sym454
```

::: {.cell-output .cell-output-stdout}

```
<cal_sym454>
Time units:
  - year
  - month
  - week
  - day
  - ampm
  - hour
  - minute
  - second
  - millisecond
```


:::
:::

:::
:::
:::

::: {.fragment .fade-up fragment-index=1}

Time units are functions that make granules.


::: {.cell}

```{.r .cell-code}
cal_gregorian$month(1L, tz = "America/Los_Angeles")
```

::: {.cell-output .cell-output-stdout}

```
<mixtime::tu_month>
 @ n : int 1
 @ tz: chr "America/Los_Angeles"
```


:::
:::

:::

::: {.fragment .fade-up fragment-index=2}

and granules are ***everything*** in mixtime.

⏱️ Time type granularities  
🗺️ Time zones (and daylight savings time)  
📅 Calendar systems (and time systems)  
✍️ Time formatting (parse and deparse)  

:::

:::
:::


![](backgrounds/jon-tyson-FlHdnPO6dlw-unsplash.jpg){.image-left}


## {}

::: columns
::: {.column width="37.5%"}
:::
::: {.column width="60%"}

### Chronons and time points

![](resources/mixtime.svg){.sticker-float-right}

`mixtime` stores time as chronons since  
an epoch (like `Date` \& `POSIXct`).

In `mixtime`, the chronon can be any granule.

::: {.callout-tip}

## Granules galore

* `cal_gregorian$second(1L)` for 1 second
* `cal_gregorian$minute(15L)` for 15 minutes
* `cal_isoweek$week(2L,tz="Asia/Tokyo")`  
  for a fortnight in Tokyo
* `cal_time_lunar$month(1L)` for a lunar cycle
* `cal_time_solar$day(1L,lat=-37.81,lon=144.96)` for a solar day (midnight boundary) in Melbourne

:::

:::
:::

![](backgrounds/jon-tyson-FlHdnPO6dlw-unsplash.jpg){.image-left}

## {.fragment-remove}

::: columns
::: {.column width="37.5%"}
:::
::: {.column width="60%"}

### Time types: `linear_time()`

![](resources/mixtime.svg){.sticker-float-right}


Linear time vectors are created with `linear_time()` in reference to a chronon.


::: {.cell}

```{.r .cell-code}
linear_time(
  5777L,
  chronon = day(1L, tz = "America/Los_Angeles")
)
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[1]>
[1] 1985-10-26 PDT
```


:::
:::


::: {.fragment .fade-up fragment-index=1}
::: {.callout-tip}
## Helper functions

::: {.fragment .fade-out fragment-index=2}

Quickly create common time points with:

::: {.columns style="width: 500px; display: inline-block;"}
::: {.column width="50%"}
* `year()`
* `yearquarter()`
* `yearmonth()`
:::
::: {.column width="50%"}
* `yearweek()`
* `date()`
* `datetime()`
:::
:::
:::

::: {.fragment .fade-up fragment-index=2}

For example...


::: {.cell}

```{.r .cell-code}
yearmonth("1985-10-26", tz = "America/Los_Angeles")
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[1]>
[1] 1985 Oct PDT
```


:::
:::


:::
:::

:::

:::
:::

![](backgrounds/jon-tyson-FlHdnPO6dlw-unsplash.jpg){.image-left}


## {.fragment-remove}

::: columns
::: {.column width="37.5%"}
:::
::: {.column width="60%"}

### Time types: `cyclical_time()`

![](resources/mixtime.svg){.sticker-float-right}

Cyclical time vectors are created with `cyclical_time()` in reference to a chronon.


::: {.cell}

```{.r .cell-code}
cyclical_time(
  "1985-10-26",
  chronon = month(1L, tz = "America/Los_Angeles"),
  cycle = year(1L, tz = "America/Los_Angeles")
)
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[1]>
[1] Oct PDT
```


:::
:::


::: {.fragment .fade-up fragment-index=1}
::: {.callout-tip}
## Helper functions

::: {.fragment .fade-out fragment-index=2}

Quickly create common cyclical time points with:

::: {.columns style="width: 500px; display: inline-block;"}
::: {.column width="50%"}
* `month_of_year()`
* `week_of_year()`
* `day_of_year()`
:::
::: {.column width="50%"}
* `day_of_month()`
* `day_of_week()`
* `time_of_day()`
:::
:::
:::

::: {.fragment .fade-up fragment-index=2}

For example...


::: {.cell}

```{.r .cell-code}
day_of_week("1985-10-26", tz = "America/Los_Angeles")
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[1]>
[1] Sat PDT
```


:::
:::


:::
:::

:::

:::
:::

![](backgrounds/jon-tyson-FlHdnPO6dlw-unsplash.jpg){.image-left}

## {.fragment-remove}

::: columns
::: {.column width="37.5%"}
:::
::: {.column width="60%"}

### Time types: `duration()`

![](resources/mixtime.svg){.sticker-float-right}

Duration vectors are created with `duration()` in reference to a chronon.


::: {.cell}

```{.r .cell-code}
duration(
  3L,
  chronon = year(1L, tz = "Australia/Melbourne"),
)
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[1]>
[1] 3 years
```


:::
:::


::: {.fragment .fade-up fragment-index=1}
::: {.callout-tip}
## Helper functions

::: {.fragment .fade-out fragment-index=2}

Quickly create common time durations with:

::: {.columns style="width: 500px; display: inline-block;"}
::: {.column width="50%"}
* `years()`
* `quarters()`
* `months()`
* `weeks()`
:::
::: {.column width="50%"}
* `days()`
* `hours()`
* `minutes()`
* `seconds()`
:::
:::
:::


::: {.fragment .fade-up fragment-index=2}

For example...


::: {.cell}

```{.r .cell-code}
months(3L, tz = "Australia/Melbourne")
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[1]>
[1] 3 months
```


:::
:::


:::
:::

:::

:::
:::

![](backgrounds/jon-tyson-FlHdnPO6dlw-unsplash.jpg){.image-left}


## {.fragment-remove}

::: columns
::: {.column width="37.5%"}
:::
::: {.column width="60%"}

### Time types: `ivs::iv()`

![](resources/mixtime.svg){.sticker-float-right}

Time intervals are no different from  
interval vectors - another type of *semantic vector* that is implemented in the `ivs` R package by @vaughanIvsIntervalVectors2022.


::: {.cell}

```{.r .cell-code}
library(ivs)
iv(
  start = date("1955-11-12", tz = "America/Los_Angeles"),
  end = date("1985-10-26", tz = "America/Los_Angeles")
)
```

::: {.cell-output .cell-output-stdout}

```
<iv<mixtime>[1]>
[1] [1955-11-12 PST, 1985-10-26 PDT)
```


:::
:::


`ivs::iv()` checks thart `start < end`. Cyclical time and durations can also be used.

:::
:::

![](backgrounds/jon-tyson-FlHdnPO6dlw-unsplash.jpg){.image-left}

## {}

::: columns
::: {.column width="37.5%"}
:::
::: {.column width="60%"}

### Time models

![](resources/mixtime.svg){.sticker-float-right}

Continuous time allows for fractional chronons, discrete time does not.


::: {.cell}

```{.r .cell-code}
date(
  "2026-04-17 09:55:00", 
  tz = "Australia/Melbourne", 
  discrete = FALSE
)
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[1]>
[1] 2026-04-17 41.3% AEST
```


:::
:::


::: {.fragment .fade-up}

::: {.callout-tip}
## Integers and doubles


All time types suport continuous \& discrete time models.

Internally, 

* discrete time is stored as integers (1 day = `1L`)
* continuous time is stored as doubles (50% of day = `0.5`)

:::
:::
:::
:::

![](backgrounds/jon-tyson-FlHdnPO6dlw-unsplash.jpg){.image-left}

## {}


::: {.r-stack}
![](resources/time_model_types_compact.svg){.image-full}
:::

## {}

::: columns
::: {.column width="60%"}

### Manipulating time

![](resources/mixtime.svg){.sticker-float-midright}

Arithmetic can manipulate time.


::: {.cell}

```{.r .cell-code}
present <- date("1985-10-26", tz = "America/Los_Angeles")
past <- date("1955-11-05", tz = "America/Los_Angeles")
present - past
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[1]>
[1] 10948.0 days
```


:::
:::



::: {.cell}

```{.r .cell-code}
past + days(7L)
```
:::



::: {.cell}
::: {.cell-output .cell-output-stdout}

```
<mixtime[1]>
[1] 1955-11-12 PST
```


:::
:::


Summary statistics can also be calculated.


::: {.cell}

```{.r .cell-code}
dates <- date(c("1955-11-05", "1985-10-26"), tz = "America/Los_Angeles")
min(dates)
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[1]>
[1] 1955-11-02 PST
```


:::

```{.r .cell-code}
max(dates)
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[1]>
[1] 1985-10-23 PDT
```


:::
:::


:::
:::

![](backgrounds/delorean-flux-capacitor-close-up.jpg){.image-right}


## {}

::: columns
::: {.column width="60%"}

### Rounding time

![](resources/mixtime.svg){.sticker-float-midright}

Time can be rounded to any granularity.


::: {.cell}

```{.r .cell-code}
day <- date("1985-10-26", tz = "America/Los_Angeles")
time_round(day, months(1L))
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[1]>
[1] 1985-11-01 PST
```


:::
:::


::: {.fragment .fade-up}

The floor and ceiling can also be calculated.


::: {.cell}

```{.r .cell-code}
time_floor(day, weeks(1L))
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[1]>
[1] 1985-10-21 PDT
```


:::

```{.r .cell-code}
time_ceiling(day, years(1L))
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[1]>
[1] 1986-01-01 PST
```


:::
:::

:::
:::
:::

![](backgrounds/delorean-flux-capacitor-close-up.jpg){.image-right}


## {}

::: columns
::: {.column width="60%"}

### Time sequences

![](resources/mixtime.svg){.sticker-float-midright}

`seq()` makes sequences by durations.


::: {.cell}

```{.r .cell-code}
seq(
  date("2020-01-31"), 
  length.out = 6,
  by = months(1L)
)
```

::: {.cell-output .cell-output-stderr}

```
Warning: The cycle offset (31 days) has produced time points that overflow the month
cycle.
! Using the nearest valid time points in the cycle, `on_invalid = "nearest"`
  (the default).
ℹ Specify `on_invalid` explicitly to suppress this warning.
```


:::

::: {.cell-output .cell-output-stdout}

```
<mixtime[6]>
[1] 2020-01-31 2020-02-29 2020-03-31 2020-04-30 2020-05-31 2020-06-30
```


:::
:::


::: {.fragment .fade-up}

::: {.callout-important}

## Invalid dates

Invalid dates can occur when adding irregular cycles to time points. `mixtime` detects these occurances.

(e.g. `"2020-01-31" + 1 month` → `"2020-02-31"`). 
:::
:::

:::
:::

![](backgrounds/delorean-flux-capacitor-close-up.jpg){.image-right}


## {.fragment-remove}

::: columns
::: {.column width="37.5%"}
:::
::: {.column width="60%"}

### Formatting time

<!-- ![](resources/mixtime.svg){.sticker-float-midright} -->

Time is usually formatted with 'strftime'.

::: {.fragment .fade-out fragment-index=3}
::: {.callout-note}
## strftime format codes

* `%Y` for year, `%m` for month, `%d` for day
* `%H` for hour, `%M` for minute, `%S` for second
* `%z` for timezone offset, `%Z` for timezone name

So we write: `"%Y-%m-%d %H:%M:%S %Z"`  
to get: `"1985-10-26 01:35:00 PDT"`.
:::
:::

::: {.fragment .fade-up fragment-index=1}
::: {.callout-question}
## How would I format an ISO-week date?

As in, YYYY-WW-D (e.g. 1985-W43-6).

::: {.fragment .fade-up fragment-index=2}
`%G` for ISO year, `%V` for ISO week, `%u` for day of week (1-7)  
So we write: `"%G-W%V-%u"` to get `"1985-W43-6"`.
:::
:::
:::

::: {.fragment .fade-up fragment-index=3}
::: {.callout-caution}
## strftime issues

* Very cryptic format codes
* Format codes vary by operating system
* Locale-dependent output (e.g. month names)
* Limited to Gregorian and ISOweek calendars
:::
:::

:::
:::

![](backgrounds/age-barros-rBPOfVqROzY-unsplash.jpg){.image-left}


## {.fragment-remove}

::: columns
::: {.column width="37.5%"}
:::
::: {.column width="60%"}

### Formatting time

![](resources/mixtime.svg){.sticker-float-right}

`mixtime` uses glue-style format strings  
with more descriptive format codes.

::: {.callout-tip}
## mixtime format codes

* Linear granules with `{lin(granule)}`
* Cyclical granules with `{cyc(granule, cycle)}`

::: {.fragment .fade-up}

Where `granule` and `cycle` are:

* time units (e.g. `month`), or
* time granules (e.g. `month(1L)`).

:::

::: {.fragment .fade-up}
The calendar is inherited from the object, but can be explicitly specified with `cal_gregorian$month(1L)`.

This also enables mixed-calendar format strings.
:::
:::

:::
:::

![](backgrounds/age-barros-rBPOfVqROzY-unsplash.jpg){.image-left}


## {.fragment-remove}

::: columns
::: {.column width="37.5%"}
:::
::: {.column width="60%"}

### Formatting time

![](resources/mixtime.svg){.sticker-float-right}

::: {.fragment .fade-out fragment-index=1}
Each chronon has a default format string.


::: {.cell}

```{.r .cell-code}
date(Sys.Date(), calendar = cal_gregorian)
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[1]>
[1] 2026-06-08
```


:::

```{.r .cell-code}
date(Sys.Date(), calendar = cal_isoweek)
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[1]>
[1] 2026-W24-Mon
```


:::

```{.r .cell-code}
date(Sys.Date(), calendar = cal_sym454)
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[1]>
[1] 2026-Jun-W2-Mon
```


:::
:::

:::

::: {.fragment .fade-up fragment-index=1}
::: {.fragment .fade-out fragment-index=2}
Custom format strings can be used, e.g.
:::


::: {.cell}

```{.r .cell-code}
# Day of year
format(
  date(Sys.Date()),
  format = "{lin(year)} D{cyc(day, year)}"
)
```

::: {.cell-output .cell-output-stdout}

```
[1] "2026 D159"
```


:::

```{.r .cell-code}
# Gregorian date (and weekday)
format(
  date(Sys.Date()), 
  format = "{lin(year)}-{cyc(month,year)}-{cyc(day,month)} ({cyc(day, cal_isoweek$week, label = TRUE)})"
)
```

::: {.cell-output .cell-output-stdout}

```
[1] "2026-06-08 (Mon)"
```


:::
:::

:::

::: {.fragment .fade-up fragment-index=2}

::: {.cell}

```{.r .cell-code}
# Gregorian date (and lunar phase emoji)
fmt_gregorian <- "{lin(year)}-{cyc(month,year)}-{cyc(day,month)}"
fmt_lunar <- "{with(cal_time_lunar, cyc(phase, month, emoji = TRUE))}"
format(
  date(Sys.Date()), 
  format = paste(fmt_gregorian, fmt_lunar)
)
```

::: {.cell-output .cell-output-stdout}

```
[1] "2026-06-08 🌗"
```


:::
:::

:::

:::
:::

![](backgrounds/age-barros-rBPOfVqROzY-unsplash.jpg){.image-left}

## {.center .fragment-remove}

::: {style="font-size: 1.5em;"}
and yes, [`mixtime` *mixes* time systems 🎉]{.fragment fragment-index=1}

::: {.fragment .fade-up fragment-index=2}

📅 Mixed granularities (and calendars)

::: {.fragment .fade-out fragment-index=4}


::: {.cell}

```{.r .cell-code}
c(
  date("1985-10-26"), 
  yearweek("1985-10-26"),
  year(1985L)
)
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[3]>
[1] 1985-10-26 1985 W43   1985      
```


:::
:::

:::
:::

::: {.fragment .fade-up fragment-index=4}
🗺️ Mixed time zones (for all granules)

::: {.cell}

```{.r .cell-code}
c(
  date("1985-10-26", tz = "America/Los_Angeles"), 
  yearweek("1985-10-26", tz = "Australia/Melbourne"),
  year(1985L, tz = "Asia/Tokyo")
)
```

::: {.cell-output .cell-output-stdout}

```
<mixtime[3]>
[1] 1985-10-26 PDT 1985 W43 AEST  1985 JST      
```


:::
:::


:::

:::



## {.fragment-remove}

::: columns
::: {.column width="60%"}
### Application - Australian CPI

::: {.fragment .fade-out fragment-index=1}
Last year, the ABS started reporting CPI **monthly** instead of **quarterly**.

Monthly records only go back to **April 2024**, while quarterly records start in **Q3 1948**.
:::

::: {.callout}

## 🦸 Mixed granularity vectors

With `mixtime`, these two data sets can be combined.
:::

::: {.fragment .fade-up fragment-index=1}
::: {.fragment .fade-out fragment-index=2}

::: columns
::: {.column width="50%"}

::: {.cell}

```{.r .cell-code}
readabs::read_abs(series_id="A2325846C") |> 
  dplyr::transmute(
    Time = yearquarter(date), 
    CPI = value
  ) -> cpi_qtr
cpi_qtr
```

::: {.cell-output .cell-output-stdout}

```
# A tibble: 311 × 2
   Time        CPI
   <mixtime> <dbl>
 1 1948 Q3    2.59
 2 1948 Q4    2.63
 3 1949 Q1    2.71
 4 1949 Q2    2.74
 5 1949 Q3    2.82
 6 1949 Q4    2.86
 7 1950 Q1    2.9 
 8 1950 Q2    3.02
 9 1950 Q3    3.05
10 1950 Q4    3.17
# ℹ 301 more rows
```


:::
:::

:::
::: {.column width="50%"}


::: {.cell}

```{.r .cell-code}
readabs::read_abs(series_id="A130393720C") |> 
  dplyr::transmute(
    Time = yearmonth(date), 
    CPI = value
  ) -> cpi_mth
cpi_mth
```

::: {.cell-output .cell-output-stdout}

```
# A tibble: 25 × 2
   Time        CPI
   <mixtime> <dbl>
 1 2024 Apr   96.4
 2 2024 May   96.2
 3 2024 Jun   96.5
 4 2024 Jul   96.8
 5 2024 Aug   96.5
 6 2024 Sep   96.5
 7 2024 Oct   96.3
 8 2024 Nov   96.7
 9 2024 Dec   97.3
10 2025 Jan   97.6
# ℹ 15 more rows
```


:::
:::

:::
:::
:::

::: {.fragment .fade-up fragment-index=2}


::: {.cell}

```{.r .cell-code}
aus_cpi <- dplyr::bind_rows(
  Quarterly = cpi_qtr,
  Monthly = cpi_mth,
  .id = "Chronon"
)
```
:::



::: columns
::: {.column width="50%"}

::: {.cell}

```{.r .cell-code}
head(aus_cpi) 
```

::: {.cell-output .cell-output-stdout}

```
# A tibble: 6 × 3
  Chronon   Time        CPI
  <chr>     <mixtime> <dbl>
1 Quarterly 1948 Q3    2.59
2 Quarterly 1948 Q4    2.63
3 Quarterly 1949 Q1    2.71
4 Quarterly 1949 Q2    2.74
5 Quarterly 1949 Q3    2.82
6 Quarterly 1949 Q4    2.86
```


:::
:::

:::
::: {.column width="50%"}


::: {.cell}

```{.r .cell-code}
tail(aus_cpi)
```

::: {.cell-output .cell-output-stdout}

```
# A tibble: 6 × 3
  Chronon Time        CPI
  <chr>   <mixtime> <dbl>
1 Monthly 2025 Nov   100.
2 Monthly 2025 Dec   101.
3 Monthly 2026 Jan   101.
4 Monthly 2026 Feb   101.
5 Monthly 2026 Mar   102.
6 Monthly 2026 Apr   103.
```


:::
:::

:::
:::

:::



:::
:::
:::


![](backgrounds/jan-sents-MT2E8NkQdWE-unsplash.jpg){.image-right}



## {.fragment-remove}

::: columns
::: {.column width="60%"}
### Application - Australian CPI

![](resources/ggtime.svg){.sticker-float-midright}


::: {.cell}

```{.r .cell-code}
library(ggplot2)
library(ggtime)
library(dplyr)
aus_cpi |> 
  filter(Time >= year(2020)) |> 
  ggplot() +
  aes(x = Time, y = CPI, group = Chronon) +
  geom_line()
```

::: {.cell-output-display}
![](index_files/figure-revealjs/unnamed-chunk-35-1.png){width=960}
:::
:::

:::
:::

![](backgrounds/jan-sents-MT2E8NkQdWE-unsplash.jpg){.image-right}


## {.fragment-remove}

::: columns
::: {.column width="60%"}
### Application - Aggregation

![](resources/tsibble.svg){.sticker-float-midright}

`tsibble::aggregate_index()`  
aggregates time to coarser granularities.

::: {.fragment .fade-out fragment-index=1}

::: {.cell}

```{.r .cell-code}
library(tsibble)
tourism
```

::: {.cell-output .cell-output-stdout}

```
# A tsibble: 24,320 x 5 [1Q]
# Key:       Region, State, Purpose [304]
   Quarter Region   State           Purpose  Trips
     <qtr> <chr>    <chr>           <chr>    <dbl>
 1 1998 Q1 Adelaide South Australia Business  135.
 2 1998 Q2 Adelaide South Australia Business  110.
 3 1998 Q3 Adelaide South Australia Business  166.
 4 1998 Q4 Adelaide South Australia Business  127.
 5 1999 Q1 Adelaide South Australia Business  137.
 6 1999 Q2 Adelaide South Australia Business  200.
 7 1999 Q3 Adelaide South Australia Business  169.
 8 1999 Q4 Adelaide South Australia Business  134.
 9 2000 Q1 Adelaide South Australia Business  154.
10 2000 Q2 Adelaide South Australia Business  169.
# ℹ 24,310 more rows
```


:::
:::

:::

::: {.fragment .fade-up fragment-index=1}

::: {.cell}

```{.r .cell-code}
library(tsibble)
tourism |> 
  aggregate_index(
    list(quarter(1L), year(1L)), 
    Trips = sum(Trips)
  )
```

::: {.cell-output .cell-output-stdout}

```
# A tsibble: 30,400 x 6 [1Q, 1Y]
# Key:       Region, State, Purpose, .granule [608]
   Quarter   Region         State              Purpose  .granule   Trips
   <mixtime> <chr>          <chr>              <chr>    <mixtime>  <dbl>
 1 1998 Q1   Adelaide       South Australia    Business 1 quarter 135.  
 2 1998 Q1   Adelaide       South Australia    Holiday  1 quarter 224.  
 3 1998 Q1   Adelaide       South Australia    Other    1 quarter  58.4 
 4 1998 Q1   Adelaide       South Australia    Visiting 1 quarter 242.  
 5 1998 Q1   Adelaide Hills South Australia    Business 1 quarter   0   
 6 1998 Q1   Adelaide Hills South Australia    Holiday  1 quarter   6.81
 7 1998 Q1   Adelaide Hills South Australia    Other    1 quarter   0   
 8 1998 Q1   Adelaide Hills South Australia    Visiting 1 quarter   2.99
 9 1998 Q1   Alice Springs  Northern Territory Business 1 quarter   7.54
10 1998 Q1   Alice Springs  Northern Territory Holiday  1 quarter   8.15
# ℹ 30,390 more rows
```


:::
:::

:::


:::
:::

![](backgrounds/jan-sents-MT2E8NkQdWE-unsplash.jpg){.image-right}


## {.fragment-remove}

::: columns
::: {.column width="60%"}
### Application - Aggregation

![](resources/tsibble.svg){.sticker-float-midright}

Combined with `aggregate_key()`,  
we can aggregate cross-temporally


::: {.cell}

```{.r .cell-code}
library(tsibble)
tourism |> 
  aggregate_key(
    (State / Region) * Purpose,
    Trips = sum(Trips)
  ) |> 
  aggregate_index(
    list(quarter(1L), year(1L)), 
    Trips = sum(Trips)
  )
```

::: {.cell-output .cell-output-stdout}

```
# A tsibble: 42,500 x 6 [1Q, 1Y]
# Key:       State, Purpose, Region, .granule [850]
```


:::

::: {.cell-output .cell-output-stdout}

```
   Quarter   State  Purpose      Region       .granule  Trips
   <mixtime> <chr*> <chr*>       <chr*>       <mixtime> <dbl>
 1 1998 Q1   ACT    Business     Canberra     1 quarter 150. 
 2 1998 Q1   ACT    Business     <aggregated> 1 quarter 150. 
 3 1998 Q1   ACT    Holiday      Canberra     1 quarter 196. 
 4 1998 Q1   ACT    Holiday      <aggregated> 1 quarter 196. 
 5 1998 Q1   ACT    Other        Canberra     1 quarter  21.7
 6 1998 Q1   ACT    Other        <aggregated> 1 quarter  21.7
 7 1998 Q1   ACT    Visiting     Canberra     1 quarter 183. 
 8 1998 Q1   ACT    Visiting     <aggregated> 1 quarter 183. 
 9 1998 Q1   ACT    <aggregated> Canberra     1 quarter 551. 
10 1998 Q1   ACT    <aggregated> <aggregated> 1 quarter 551. 
# ℹ 42,490 more rows
```


:::
:::



:::
:::

![](backgrounds/jan-sents-MT2E8NkQdWE-unsplash.jpg){.image-right}



## {}

::: columns
::: {.column width="37.5%"}
:::
::: {.column width="60%"}
### Timezones and Astronomy

![](resources/mixtime.svg){.sticker-float-right}

Two primitive time units implement timezone and astronomical properties.


::: columns
::: {.column width="48%"}

::: {.cell}

```{.r .cell-code}
mt_tz_unit
```

::: {.cell-output .cell-output-stdout}

```
<mixtime::mt_tz_unit> class
@ parent     : <mixtime::mt_unit>
@ constructor: function(n, tz) {...}
@ validator  : function(self) {...}
@ properties :
 $ n : <integer> or <double>
 $ tz: <character>          
```


:::
:::

:::
::: {.column width=482%"}

::: {.cell}

```{.r .cell-code}
mt_loc_unit
```

::: {.cell-output .cell-output-stdout}

```
<mixtime::mt_loc_unit> class
@ parent     : <mixtime::mt_unit>
@ constructor: function(n, lat, lon, alt) {...}
@ validator  : function(self) {...}
@ properties :
 $ n  : <integer> or <double>
 $ lat: <integer> or <double>
 $ lon: <integer> or <double>
 $ alt: <integer> or <double>
```


:::
:::

:::
:::

:::
:::


![](backgrounds/zoltan-tasi-CLJeQCr2F_A-unsplash.jpg){.image-left}

## {.fragment-remove}

::: columns
::: {.column width="37.5%"}
:::
::: {.column width="62%"}
### Timezones and Astronomy

![](resources/mixtime.svg){.sticker-float-right}

Calendars extend primitive time systems.

::: {.fragment .fade-out fragment-index=1}

::: columns
::: {.column width="33%"}

::: {.cell}

```{.r .cell-code}
cal_time_civil
```

::: {.cell-output .cell-output-stdout}

```
<cal_time_civil>
Time units:
  - day
  - ampm
  - hour
  - minute
  - second
  - millisecond
```


:::
:::

:::
::: {.column width="33%"}

::: {.cell}

```{.r .cell-code}
cal_time_solar
```

::: {.cell-output .cell-output-stdout}

```
<mt_calendar>
Time units:
  - day
  - ampm
  - hour
  - minute
  - second
  - degree
  - arcminute
  - arcsecond
  - illumination
```


:::
:::

:::
::: {.column width="32%"}

::: {.cell}

```{.r .cell-code}
cal_time_lunar
```

::: {.cell-output .cell-output-stdout}

```
<mt_calendar>
Time units:
  - month
  - phase
```


:::
:::

:::
:::

:::

::: {.fragment .fade-up fragment-index=1}

![](resources/calendar_primitives.svg)

These primitives time units (`mt_tz_unit` and `mt_loc_unit`) provide time zone and location based calculations.

:::

:::
:::


![](backgrounds/zoltan-tasi-CLJeQCr2F_A-unsplash.jpg){.image-left}

## {.fragment-remove}

::: columns
::: {.column width="37.5%"}
:::
::: {.column width="62%"}
### Calendrical Calculations

![](resources/mixtime.svg){.sticker-float-right}

![](resources/calendar_algebra.svg)

::: {.fragment .fade-out fragment-index=1}
Time units define their cardinality between adjacent granules.


::: {.cell}

```{.r .cell-code}
chronon_cardinality(
  cal_gregorian$hour(1L),
  cal_gregorian$day(1L)
)
```

::: {.cell-output .cell-output-stdout}

```
[1] 24
```


:::
:::

:::

::: {.fragment .fade-up fragment-index=1}
::: {.fragment .fade-out fragment-index=2}
Cardinality methods are traversed across the graph to compute all cardinality pairs.


::: {.cell}

```{.r .cell-code}
chronon_cardinality(
  cal_gregorian$second(1L),
  cal_gregorian$day(1L)
)
```

::: {.cell-output .cell-output-stdout}

```
[1] 86400
```


:::
:::

:::
:::

::: {.fragment .fade-up fragment-index=2}
Irregular cardinalities (e.g. days in month) require a time point.


::: {.cell}

:::


::: {.cell}

```{.r .cell-code}
chronon_cardinality(
  cal_gregorian$day(1L),
  cal_gregorian$month(1L),
  at = yearmonth("2020-02-01")
)
```

::: {.cell-output .cell-output-stdout}

```
[1] 29
```


:::
:::

:::

Adjacent units with irregular cardinality also require a divmod function for conversions.

:::
:::

![](backgrounds/zoltan-tasi-CLJeQCr2F_A-unsplash.jpg){.image-left}


## {.fragment-remove}

::: columns
::: {.column width="37.5%"}
:::
::: {.column width="62%"}
### Mixed granularity vectors

![](resources/vecvec.svg){.sticker-float-right}

To enable mixed-type vectors in R,  
I've created `vecvec` - vectors of vectors.


::: {.cell}

```{.r .cell-code}
library(vecvec)
vecvec(
  month.abb, 
  rnorm(10),
  0i ^ (-3:3)
)
```

::: {.cell-output .cell-output-stdout}

```
<vecvec[29]>
 [1] Jan         Feb         Mar         Apr         May         Jun        
 [7] Jul         Aug         Sep         Oct         Nov         Dec        
[13] -1.34381553 -0.97985362 -0.94409799  1.17574635 -0.54207786  0.67782851
[19]  0.76252293  0.67420766  0.07180535 -0.17553644 Inf+0i      Inf+0i     
[25] Inf+0i        1+0i        0+0i        0+0i        0+0i     
```


:::
:::


[Outside of semantic vectors, `vecvec` is a bad idea for data analysis - it's like Excel but for R.]{.fragment}

:::
:::

![](backgrounds/jon-tyson-FlHdnPO6dlw-unsplash.jpg){.image-left}


## {.fragment-remove}

::: columns
::: {.column width="37.5%"}
:::
::: {.column width="62%"}
### Mixed granularity vectors

![](resources/mixtime.svg){.sticker-float-right}

A `mixtime` is a mixed-type time vector.


::: {.cell}

```{.r .cell-code}
str(
  c(
    yearmonth("1989-10-26", tz = "America/Los_Angeles"),
    yearweek("1989-10-26", tz = "Australia/Melbourne")
  )
)
```

::: {.cell-output .cell-output-stdout}

```
<mixtime::mixtime> int [1:2] 1 2
 @ x:List of 2
 .. $ :linear<1 month> [1:1] 1989 Oct PDT
 .. $ :linear<1 week> [1:1] 1989 W43 AEST
```


:::
:::


:::
:::

![](backgrounds/jon-tyson-FlHdnPO6dlw-unsplash.jpg){.image-left}



## {.fragment-remove}

::: columns
::: {.column width="37.5%"}
:::
::: {.column width="62%"}
### Mixed shape distributions

![](media/distributional.svg){.sticker-float-right}

This idea also underpins `distributional`


::: {.cell}

```{.r .cell-code}
library(distributional)
c(
  dist_normal(0, 1),
  dist_poisson(3)
)
```

::: {.cell-output .cell-output-stdout}

```
<distribution[2]>
[1] N(0, 1) Pois(3)
```


:::
:::


::: {.fragment .fade-up}
Distributions are much simpler than time 😅
:::

:::
:::

![](backgrounds/ian-fajardo-jYg-bmeMotE-unsplash.jpg){.image-left}

## {}

::: columns
::: {.column width="40%"}
:::
::: {.column width="60%"}

### Time for ggplot2

![](resources/ggtime.svg){.sticker-float-right}

Two types of `ggtime` functions:

::: {.callout-note icon=false}
## :framed_picture: Plot helpers

Functions which are used to quickly create a specific plot.

* `autoplot()` / `autolayer()`
* `ggtime::gg_season()`
* `ggtime::gg_subseries()`

:::

::: {.fragment .fade-up}
::: {.callout-tip icon=false}
## :art: Grammar extensions

Functions which add new features to the ggplot2's grammar.

* `ggtime::geom_time_line()`
* `ggtime::scale_x_mixtime()`
* `ggtime::coord_loop()`

:::
:::


:::
:::

![](backgrounds/amjd-rdwan--MDJDYKQz6E-unsplash.jpg){.image-left}

## {.fragment-remove}

::: columns

::: {.column width="60%"}

### Geometries

* `geom_time_line()`

  ::: {.fragment .fade-out fragment-index=2}
  A time-aware version of `geom_line()`. Shows timezone offsets with dashed lines from the `[x/y]_time_offset` **aesthetic**.
  

  ::: {.cell}
  
  ```{.r .cell-code  code-fold="true"}
  library(dplyr)
  library(ggdist)
  library(ggtime)
  library(lubridate) # TODO - remove
  library(ggplot2)
  tz_shift <- as_tibble(tsibbledata::gafa_stock) |>
    filter(
      (Symbol == "AAPL" & Date <= "2014-01-15") | 
        (Symbol == "GOOG" & Date <= "2014-01-13")
    ) |>
    mutate(Date = Sys.Date() + lubridate::hours(c(1:3, 3:9, 1:2, 4:9)), DST = ifelse(Symbol == "AAPL", "DST Ends", "DST Begins")) |> 
    slice(1:3, 3:12, 12:n()) |> 
    mutate(
      open = duplicated(Open),
      closed = c(open[-1], FALSE),
      Date = Date + open*3600*((DST=="DST Begins")*2-1)
    ) 
  
  tz_shift |> 
    ggplot(aes(x = Date, y = Close)) + 
    geom_path(aes(group = cumsum(open))) + 
    geom_path(linetype = "dashed", data = filter(tz_shift, open | closed)) +
    facet_wrap(vars(DST), ncol = 2, scales = "free_y") + 
    scale_shape_manual(values = c("TRUE" = 16, "FALSE" = 1)) + 
    guides(shape = "none")
  ```
  
  ::: {.cell-output-display}
  ![](index_files/figure-revealjs/unnamed-chunk-48-1.png){width=960}
  :::
  :::

  
  :::


::: {.fragment .fade-up fragment-index=2}
* `geom_time_candle()`

  Shows value changes over time periods (e.g. daily, weekly, ...) which are calculated using the `stat_candle` **statistic**.
  

::: {.cell}

```{.r .cell-code  code-fold="true"}
tsibbledata::gafa_stock |> 
  filter(Symbol == "GOOG") |> 
  filter(tsibble::yearmonth(Date) == tsibble::yearmonth("2014 Jun")) |> 
  ggplot(aes(x = Date)) + 
  tidyquant::geom_candlestick(
    aes(open = Open, high = High, low = Low, close = Close),
    colour_up = "#1FB974", fill_up = "#1FB974", colour_down = "#F4375D", fill_down = "#F4375D"
  ) + 
  scale_x_date(date_labels = "%d %b %Y") +
  labs(y = "GOOG Stock")
```

::: {.cell-output-display}
![](index_files/figure-revealjs/unnamed-chunk-49-1.png){width=960}
:::
:::

:::


:::
:::

![](backgrounds/gglayers-1528209746.png){.image-right}

## {.fragment-remove}

::: columns

::: {.column width="60%"}

### Positions [these are now in scale]

The x/y position of time is timezone adjusted:

* `position_time_absolute()` positions time at its exact global location.

  ::: {.fragment .fade-out fragment-index=1}

  ::: {.cell}
  
  ```{.r .cell-code  code-fold="true"}
  library(tsibble)
  pedestrian |> 
    filter(Sensor == "Southern Cross Station") |> 
    filter(lubridate::year(Date_Time) == 2015) |> 
    mutate(Date_Time = force_tz(make_datetime(lubridate::year(Date), lubridate::month(Date), lubridate::day(Date), Time), "Australia/Melbourne")) |> 
    ggplot(aes(x = Date_Time - as.POSIXct(Date), y = Count, group = Date)) + 
    geom_line(alpha = 0.2) + 
    theme(axis.text.x = element_blank()) + 
    labs(x = "Time", title = "Hourly pedestrians passing Southern Cross Station")
  ```
  
  ::: {.cell-output-display}
  ![](index_files/figure-revealjs/unnamed-chunk-50-1.png){width=960}
  :::
  :::


  Timezone differences (e.g. daylight savings) misaligns seasonal patterns.
  :::

::: {.fragment .fade-up fragment-index=1}
* `position_time_civil()` positions time as it appears locally in each timezone.



  ::: {.cell}
  
  ```{.r .cell-code  code-fold="true"}
  pedestrian |> 
    filter(Sensor == "Southern Cross Station") |> 
    filter(lubridate::year(Date_Time) == 2015) |> 
    ggplot(aes(x = Time, y = Count, group = Date)) + 
    geom_line(alpha = 0.2) + 
    theme(axis.text.x = element_blank()) + 
    labs(x = "Time", title = "Hourly pedestrians passing Southern Cross Station")
  ```
  
  ::: {.cell-output-display}
  ![](index_files/figure-revealjs/unnamed-chunk-51-1.png){width=960}
  :::
  :::


:::
<!-- TODO: Add example from pedestrian counters -->

:::
:::

![](backgrounds/gglayers-1528209746.png){.image-right}


## {}

::: columns

::: {.column width="60%"}

### Scales

:::{style="font-size:80%;"}
The scales in `ggplot2` provide:

* `scale_*_date()` for `Date`, 
* `scale_*_datetime()` for `POSIXct`, 
* `scale_*_time()` for `hms`.

Extension packages (e.g. `tsibble`) add:

* `scale_*_yearquarter()` for `yearquarter`,
* `scale_*_yearmonth()` for `yearmonth`, 
* `scale_*_yearweek()` for `yearweek`.
:::

::: {.fragment .fade-up}
::: {.callout-tip style="margin-top: -1em;"}

## Unified scales for time series

`mixtime` has many calendars and granularities.

`ggtime` unifies them all with `scale_*_mixtime()`.

:::
:::

:::
:::

![](backgrounds/gglayers-1528209746.png){.image-right}


## {}

::: columns

::: {.column width="60%"}

### Scales

The mixtime scales support temporal labels and breaks, much like ggplot2:

* `time_labels` (mixtime format strings)
* `time_breaks` (duration, e.g. `months(3L)`)

::: {.fragment .fade-up}

These scales also have alignment options:

* `align_discrete` (numeric, 0-1)
* `time_warp` (duration, e.g. `months(1L)`)
  `warp` (times, e.g. `2025-01-28`)

:::

:::
:::

![](backgrounds/gglayers-1528209746.png){.image-right}


## {.fragment-remove}

::: columns

::: {.column width="40%"}
:::
::: {.column width="60%"}

### Granularity alignment

::: {.fragment .fade-out fragment-index=1}
`{ggtime}` **aligns mixed granularities**.

Imagine Australian births (annual) compared with total births by state (monthly).
:::


::: {.cell}
::: {.cell-output-display}
![](index_files/figure-revealjs/unnamed-chunk-52-1.png){width=960}
:::
:::


::: {.fragment .fade-up fragment-index=1}
::: {.callout-note icon=false}

## :date: Temporal alignment across granularities

When constrained to Date and POSIXct, left alignment is commonly used for less-frequent granularities.

e.g. `2025-01-01` can be 2025, Jan 2025, or Jan 1 2025.

Consequently, plotting is also often left-aligned.
:::
:::

:::
:::

![](backgrounds/chris-lee-70l1tDAI6rM-unsplash.jpg){.image-left}


## {.fragment-remove}

::: columns

::: {.column width="40%"}
:::
::: {.column width="60%"}

### Granularity alignment

`{ggtime}` center aligns granularities.


::: {.cell}
::: {.cell-output-display}
![](index_files/figure-revealjs/unnamed-chunk-53-1.png){width=960}
:::
:::


::: {.callout-note icon=false}

## :date: Aligning temporal granularities

Specify alignment of different granularities with `scale_x_mixtime(align_discrete = aes_nudge())`.
:::

:::
:::

![](backgrounds/chris-lee-70l1tDAI6rM-unsplash.jpg){.image-left}


## {.fragment-remove}

::: columns

::: {.column width="40%"}
:::
::: {.column width="60%"}

### Time warping

`{ggtime}` defaults to center alignment.

::: {.fragment .fade-out fragment-index=1}

Cycles are repeating patterns with an irregular duration (and shape).


::: {.cell}
::: {.cell-output-display}
![](index_files/figure-revealjs/unnamed-chunk-54-1.png){width=960}
:::
:::

:::

::: {.fragment .fade-up fragment-index=1}

Warping cycles to have the same length as "% of cycle" can help **compare cycle shapes**.

::: {.fragment .fade-out fragment-index=2}

::: {.cell}
::: {.cell-output-display}
![](index_files/figure-revealjs/unnamed-chunk-55-1.png){width=960}
:::
:::

:::
:::

::: {.fragment .fade-up fragment-index=2}

::: {.callout-note icon=false}

## :date: Temporal alignment across cycles

In `scale_x_mixtime()`, warp time with

* `warp` (stretch time between specific time points)
* `time_warp` (stretch time by duration, e.g. `"1 month"`)

:::
:::

:::
:::

![](backgrounds/chris-lee-70l1tDAI6rM-unsplash.jpg){.image-left}

## {}

::: columns

::: {.column width="60%"}

### Facets & Coordinates

Season plots loop time over seasonalities.

* `coord_loop()`

The time loop points can be specified with:

* `loops` (loop over specific time points)
* `time_loops` (over durations - `weeks(1L)`)

:::
:::

![](backgrounds/gglayers-1528209746.png){.image-right}

## Thanks for your time!

::: columns
::: {.column width="60%"}

::: {.callout-tip}
## Final remarks

* Good design makes complicated things accessible.
* Statistical software with semantic vectors is safer.
* Try mixtime (and distributional)!
:::

::: {.callout-link}

## Useful links

![](resources/forum.svg){.icon} [social.mitchelloharawild.com](https://social.mitchelloharawild.com/)

![](resources/projector-screen-outline.svg){.icon} [slides.mitchelloharawild.com/mixtime-supsi](https://slides.mitchelloharawild.com/mixtime-supsi)

![](resources/github.svg){.icon} [mitchelloharawild/mixtime-supsi](https://github.com/mitchelloharawild/mixtime-supsi)

:::

:::
:::

![](backgrounds/meric-dagli-7NBO76G5JsE-unsplash.jpg){.image-right}

## References