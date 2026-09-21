# Absorbing the `intel/llvm` backlog: when, and how to make it sooner

A focused answer to two questions: when will the vendor extensions that DPC++
ships become Khronos extensions, and what would actually move that date. Figures
are as of 2026-09-21 and derive from [`table.md`](table.md); the Vulkan
comparison lives in [`summary.md`](summary.md) and
[`vulkan_table.md`](vulkan_table.md).

Throughout, **every published `sycl_khr_*` extension is credited with retiring one
`intel/llvm` extension**, so the absorption rate is simply the `KHR` publication
rate. Historically 6 of the 9 published extensions did that, so the estimates below
are optimistic by about a third.

## The short answer

**At today's rates the backlog does not clear.** `intel/llvm` adds 4.5 extensions
per year net to the pool that needs standardising; Khronos publishes 4.9 `KHR`
extensions per year. The margin is 0.4 per year against a backlog of 91, which
works out at over two centuries. Restricted to the 68 that could plausibly be
portable, the margin is 1.5 per year and the answer is 45 years.

The backlog is therefore not a queue being worked off slowly — it is a queue that
is being very nearly kept pace with, and nothing more. Two things change that:
**publish more `KHR` extensions per year**, or **stop the target moving.** The rest
of this document sizes both.

## The arithmetic

| Symbol | Meaning | Today |
| --- | --- | ---: |
| **R** | `sycl_khr_*` extensions published, and pool extensions retired, per year | **4.9** |
| **G** | net growth of the pool per year | **+4.5** |
| **REM** | extensions still to absorb | **91**, or **68** portable |

The backlog drains in **REM / (R − G)** years, and not at all when R ≤ G. The 68
figure excludes the 23 extensions that are vendor- or backend-scoped by
construction and would never become Khronos extensions under any name; for that
reduced target the matching growth figure is +3.4/yr.

Where the numbers come from: R is 9 merges over the 22.2 months since the first
one; G is the pool going from 89 at the end of 2024 to 97 now.

## Drain times

| Publication rate R | All 91 (G = +4.5) | 68 portable (G = +3.4) |
| --- | ---: | ---: |
| **4.9/yr** (today) | 227 yr | 45 yr (2071) |
| **6.5/yr** (+33%) | 46 yr (2071) | 22 yr (2047) |
| **9.8/yr** (2×) | 17 yr (2043) | **11 yr (2036)** |
| **12.7/yr** (Vulkan since 2018, 2.6×) | 11 yr (2037) | 7 yr (2033) |
| **15.6/yr** (Vulkan all time, 3.2×) | 8 yr (2034) | 6 yr (2031) |

The table is steeply non-linear at the top because R and G are nearly equal there.
Going from 4.9 to 6.5 — a 33% increase — cuts the 91-extension estimate from 227
years to 46, not because absorption improved much but because the margin over
growth quadrupled. **Near the current rate the estimate is dominated by the gap
between two similar numbers, which is also why it is so uncertain.**

## Lever 1: publish more `KHR` extensions per year

Inverted, the entry price for each horizon:

| Finish by | Rate needed, all 91 | Rate needed, 68 portable |
| --- | ---: | ---: |
| 2036 (10 years) | 13.6/yr (**2.8×**) | 10.2/yr (**2.1×**) |
| 2041 (15 years) | 10.6/yr (2.2×) | 7.9/yr (1.6×) |
| 2046 (20 years) | 9.1/yr (1.8×) | 6.8/yr (1.4×) |

A volume cross-check, which does not depend on how documents are counted, agrees.
The 62 portable never-proposed extensions are 27154 lines; at the measured 0.89×
rewrite ratio that is about 24200 lines of `KHR` text, and `main` has gained
published extension text at 104 lines per month — **19 years of output**. Hitting
2036 requires about 200 lines per month, a **1.9× increase**. For all 85
never-proposed documents (37318 lines) it is 27 years at the current rate, and 2.7×
to reach a decade.

Two count-independent estimates landing on 1.9–2.1× is the most robust figure in
this document.

What a 2–3× increase would take, from the pipeline's own numbers: at the observed
232-day mean time-to-merge, Little's Law puts the required work in progress at 6–10
concurrent proposals against the 4.8 average observed — and SYCL has already held
10 open at once, on 2025-05-05, so peak capacity has been demonstrated. The
alternative is faster turnaround: sustaining 15.6/yr at today's average concurrency
needs median time-to-merge to fall from 237 days to about 112. The constraint is
more plausibly sustained review attention than peak capacity.

What it would *not* fix: the wait an individual extension faces. Of the mean 1159
days from vendor document to `KHR` merge for the five absorbed so far, only 137
days was the pull request; the other 1022 days (88%) was the document waiting for
someone to start. Higher throughput compresses that waiting — at 2.6–3.2× the mean
wait falls to roughly 1.2–1.5 years — but no extension arrives faster than a pull
request takes.

## Lever 2: stop the target moving

The pool grew 89 → 97 over the last 1.8 years. Every new vendor extension written
today is a document that will need standardising in three to five years, at which
point it is indistinguishable from the rest of the backlog. G is not background
noise; it is a second source of the same work, and at +4.5/yr it currently consumes
92% of the absorption rate.

If new APIs went to Khronos as `KHR` proposals from the start — G = 0 — the present
backlog drains on its own arithmetic:

| Publication rate R | All 91, **G = 0** | 68 portable, **G = 0** |
| --- | ---: | ---: |
| 4.9/yr (today) | 19 yr (2044) | 14 yr (2039) |
| 6.5/yr (+33%) | 14 yr (2040) | **10 yr (2036)** |
| 9.8/yr (2×) | 9 yr (2035) | 7 yr (2032) |

Compare with the previous table: **eliminating growth is worth more than doubling
throughput, and costs no review capacity.** At today's publication rate it turns
"227 years" into 19. It is nevertheless the harder change to adopt, because it asks
for an API to be settled in the working group before it ships in DPC++ — the
opposite of how all 97 existing extensions were produced — and it slows the
vendor's own delivery.

A partial version is cheap and available now: **triage every new extension on
creation** into "intended for `KHR`", "vendor-permanent" and "experiment". That
slows nothing down, and without it the pool cannot be distinguished from the
backlog. 45 of the 85 never-proposed extensions are already older than the mean
successful absorption, and nothing in either repository records which of them
anybody intends to standardise.

## What would put the date inside ten years

| Combination | All 91 | 68 portable |
| --- | ---: | ---: |
| R = 9.8/yr (2×), growth unchanged | 17 yr | **11 yr (2036)** |
| R = 13.6/yr (2.8×), growth unchanged | **10 yr (2036)** | 7 yr (2032) |
| R = 6.5/yr (+33%) and G = 0 | 14 yr | **10 yr (2036)** |
| R = 9.8/yr (2×) and G = 0 | **9 yr (2035)** | 7 yr (2032) |
| R = 15.6/yr (Vulkan's rate), growth unchanged | 8 yr (2034) | 6 yr (2031) |

The pattern: **a decade is reachable for the portable subset by doubling throughput
alone, or by a modest 33% increase combined with an end to pool growth. The full 91
inside a decade needs roughly a tripling, or a doubling plus zero growth. Nothing
at today's rate reaches any useful date.**

## Recommendations, in order of value for effort

1. **Triage the pool, and record the result in `intel/llvm`.** One status field per
   vendor specification — intended for `KHR`, vendor-permanent, or experimental —
   plus the reverse link in the `KHR` document. It costs nothing, it is the
   prerequisite for every other decision here, and without it the 23
   vendor-permanent extensions cannot be subtracted with confidence and
   correspondences have to be reconstructed by comparing APIs, as all six in
   [`table.md`](table.md) were.
2. **Start sooner rather than finish faster.** 88% of the 3.2-year mean wait is the
   document sitting untouched before a `KHR` pull request exists. Picking items off
   the pool earlier is a scheduling decision, not a capacity increase, and it is
   where the time actually goes.
3. **Adopt vendor text rather than redrafting it.** The five absorbed extensions
   produced 590 lines of `KHR` text from 662 lines of vendor text — a 0.89× ratio,
   so the work was substantially a rename — yet each took a mean of 1159 days end
   to end.
4. **Deprecate vendor extensions when their `KHR` replacement lands.** All six
   absorbed extensions are still in `supported`/`experimental`. This does not change
   the absorption count, but it stops the vendor surface growing monotonically and
   makes progress legible.
5. **Propose new APIs as `KHR` extensions where the design is not vendor-specific.**
   The full version of lever 2, and the only change that stops the target moving.
   At today's throughput it is worth more than any plausible increase in throughput.
6. **Raise throughput toward 2×, deliberately.** The figures above put 1.9–2.1× as
   the entry price for a ten-year horizon on the portable subset. Decide explicitly
   whether it comes from more proposals in flight or shorter time-to-merge, because
   the two imply different investments and the pipeline is currently drifting:
   proposals arrive at 0.62/month and resolve at 0.41/month.
7. **Split large proposals before opening them.** Not an absorption lever as such,
   but the pipeline's main failure mode: 7 of 9 proposals at or below 200 lines are
   published, against 2 of 6 above it, and `sycl_khr_properties` (2377 lines) and
   `sycl_khr_launch` (1287 lines) between them hold 3664 of the 5360 unpublished
   lines.

## Caveats

* Crediting every `KHR` extension with one absorption is optimistic. Four of the
  nine published so far had no counterpart in the pool
  (`sycl_khr_split_headers`, `sycl_khr_group_interface`) or came from elsewhere in
  `intel/llvm`, so the measured absorption rate is 3.3/yr rather than 4.9/yr. On
  that basis the pool does not drain at all today, and each estimate above should be
  read as a floor.
* Every figure is a linear extrapolation from a small sample: 6 absorptions over 22
  months, 9 merges over 24, 5 usable latency measurements. One extra absorption per
  year moves a frozen-pool estimate by about 7 years, so treat the dates as orders
  of magnitude rather than forecasts. Near the current rate they are especially
  unstable, being the ratio of a fixed backlog to the small difference between two
  similar rates.
* The split of the pool into 68 portable and 23 vendor-scoped is a judgement made
  for this analysis, not a position held by Intel or Khronos, and an extension not
  yet proposed may be one nobody intends to propose.
* G = +4.5/yr is net growth of the two directories; gross arrivals of new vendor
  specifications run at about 11 per year, the difference being documents that moved
  to `deprecated`, `removed` or `proposed`.
* Counting documents is a crude measure of work — a 5-line document and a 2853-line
  document both count as one absorption — which is why the line-volume cross-check
  above matters. The two agree to within 10% on the required increase.
* See [`table.md`](table.md#caveats) for the full list, including the committer-date
  handling and the reconstruction of the vendor → `KHR` correspondences.
