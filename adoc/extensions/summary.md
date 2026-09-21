# SYCL and Vulkan extension development: summary

A condensed view of the two analyses in [`table.md`](table.md) (SYCL `KHR`
extensions and the `intel/llvm` vendor extension backlog) and
[`vulkan_table.md`](vulkan_table.md) (the Vulkan registry), with the focus on how
the two compare and what the data suggests could be improved in the SYCL flow.
All figures are as of 2026-09-21; derivations and caveats stay in the two source
documents.

## The numbers side by side

| | Vulkan | SYCL |
| --- | ---: | ---: |
| Window of public extension history | 10.6 years | 2.0 years |
| Extensions ever published | 504 | 9 |
| Publication rate, all extensions | 47.6/yr | 4.9/yr |
| Publication rate, Khronos (`KHR`) only | **15.6/yr** (12.7/yr since 2018) | **4.9/yr** |
| Khronos extensions published in the last 2 years | 30 | 9 |
| Khronos share of the whole extension surface | 165 of 504 (**33%**) | 9 of 106 (**8.5%**) |
| Khronos share of the last 2 years' new extensions | 30 of 99 (**30%**) | 9 of 31 (**29%**) |
| Extension tiers | vendor → `EXT` → `KHR` → core | `KHR` only |
| Median extension document | 52 lines (`KHR` 60) | 103 lines published, 148 across all 15 |
| Proposals visible in public pull requests | 14, **0 accepted** | 15, **9 accepted** |
| Observable proposal → acceptance latency | none (extensions arrive fully designed) | mean 232 days, median 237 |
| Unfinished work visible as | 229 reserved registry slots (32% of 715) | 5 open pull requests |
| Ratified share of Khronos extensions | 92% | not published per extension |
| Promotion into the core specification | 63 (5.9/yr), median 312 days after publication | n/a |

## Seven facts that matter

1. **SYCL standardises about the same fraction of new work as Vulkan.** Over the
   last two years the Khronos share of newly published extensions was 30% for
   Vulkan and 29% for SYCL. The governance balance is not the difference between
   the two projects.

2. **The difference is stock, not flow.** Vulkan has been 33% Khronos for a
   decade and never dipped below 31%, because it shipped `KHR` extensions from
   the 1.0 release. SYCL's `KHR` process is two years old and sits on seven years
   of accumulated vendor extensions, so its surface is 8.5% Khronos and 91.5%
   vendor (79 `sycl_ext_oneapi_*`, 16 `sycl_ext_intel_*`, 2
   `sycl_ext_codeplay_*`).

3. **The absorption balance currently has the wrong sign.** `intel/llvm` ships 97
   supported/experimental extensions. Six have been absorbed into five published
   `KHR` extensions, five are in flight, one was abandoned, and **85 have never
   been proposed**. Absorption runs at 3.3/yr against net pool growth of
   +4.5/yr, so the backlog does not drain at all: the estimate is not a long
   number, it is "never". Frozen-pool arithmetic gives ~28 years (2054) for the
   91 remaining, or ~14 years in the most favourable case consistent with the
   data.

4. **Matching Vulkan's `KHR` rate flips that sign.** At 12.7–15.6 `KHR`/yr (a
   2.6–3.2× increase) absorption reaches 8.5–10.4/yr, exceeds growth by 4.0–5.9/yr
   and the backlog clears in **15–23 years including all future arrivals**, or
   9–11 years if `intel/llvm` stopped adding extensions. The Khronos share then
   converges to 54–59% and passes Vulkan's 33% around 2030–2031.

5. **Size predicts stalling.** Of the 9 SYCL proposals at or below 200 lines, 7
   are published; of the 6 above 200 lines, only 2 are. Published extensions
   average 256 lines, open ones 832. The two largest efforts are the slowest:
   `sycl_khr_launch` (1287 lines, 75 commits, open 704 days) and
   `sycl_khr_properties` (2377 lines, draft). The abandoned
   `sycl_khr_command_graph` was 1201 lines. Vulkan's median `KHR` extension is 60
   lines.

6. **Unpublished specification text outweighs published text 2.3×** — 5360 lines
   in flight or abandoned against 2304 published. SYCL publishes 104 lines of
   specification per month; Vulkan's `KHR` output is 2.6–3.2× that.

7. **Absorption does not shrink the pool.** All six absorbed extensions are still
   in `intel/llvm`'s `supported`/`experimental` directories. Vulkan records the
   equivalent relationship explicitly (`promotedto`, `deprecatedby`), and 12
   vendor extensions have been promoted that way; SYCL records it nowhere — the
   six correspondences in [`table.md`](table.md) had to be reconstructed by
   comparing APIs.

## How the two pipelines differ

**Vulkan extensions reach the repository in a mature state.** By the time a
Vulkan extension appears, its design is settled: 148 of 153 proposal documents
land on the same day as the extension they describe, the repository contains no
rejected or stalled specification, and 76% of extensions are never revised after
publication. The 14 extension pull requests opened from forks were likewise not
the route by which any extension arrived. Vulkan's 47.6/yr therefore measures the
throughput of publishing agreed designs, not the throughput of reaching agreement.

**SYCL places the design conversation after the pull request rather than before
it.** Its extensions converge in the repository, across a mean of 19 commits each
and 232 days to merge. The same design work is done either way, but this
arrangement holds it as work in progress: five proposals are open at a mean age of
282 days, one for 704 days, and 5360 lines of specification sit in flight or
abandoned against 2304 published. How much convergence a document still needs when
it arrives is visible in the churn: the fastest extension to merge took 58 days and
2 commits, while the two longest-running proposals have accumulated 75 and 12
commits against 1287 and 2377 lines, and document size correlates with
time-to-merge (r = 0.43). Every recommendation below follows from that — the aim is
to move convergence earlier, not to move it out of public view. The open route is
worth keeping on its own terms: proposals from forks do get merged, which is how
`sycl_khr_free_function_kernels` entered the pipeline.

One consequence is methodological. Because SYCL's design conversation is in the
repository, it has a measurable acceptance ratio (9 of 10 resolved proposals, 90%)
and a measurable time-to-merge; Vulkan has neither, so every latency comparison in
this document is between a SYCL figure that includes design convergence and a
Vulkan figure that does not.

**Vulkan's tiering absorbs disagreement; SYCL's does not.** 67% of Vulkan
extensions begin below `KHR`, and the `EXT` tier is where designs wait for
cross-vendor agreement — 17 `EXT` extensions were later re-published as `KHR`, and
no vendor extension has ever gone straight to core. SYCL has one jump, from a
vendor namespace to `KHR`, with nothing in between, and that jump takes a mean of
1159 days (3.2 years).

## Propositions for the SYCL flow

Ordered by expected effect on the two rates that actually determine the outcome —
`KHR` publication throughput, and the visibility of intent.

1. **Split large extensions before proposing them.** This is the cheapest change
   with the clearest evidence behind it: 78% of proposals under 200 lines are
   published, against 33% above it. `sycl_khr_properties` (2377 lines) and
   `sycl_khr_launch` (1287 lines) are 12–24× Vulkan's median `KHR` extension and
   together hold 3664 of the 5360 unpublished lines. Decomposing them into
   separately mergeable extensions converts two stalled efforts into a stream of
   small ones.

2. **Adopt vendor text with mechanical renaming rather than rewriting.** The five
   absorbed extensions produced 590 lines of `KHR` text from 662 lines of vendor
   text — a 0.89× ratio, meaning the work was substantially a rename, yet it took
   a mean of 1159 days. Treating a vendor extension as a submission to be edited,
   rather than a specification to be redrafted, attacks the largest single latency
   in the pipeline.

3. **Record standardisation intent in `intel/llvm`, and the reverse link in the
   `KHR` document.** Vulkan's 229 reserved registry slots (32% of all slots) make
   in-progress and abandoned work publicly countable, and `promotedto` /
   `deprecatedby` make the vendor→Khronos relationship machine-readable. SYCL has
   neither: nothing distinguishes the 85 never-proposed extensions that nobody
   intends to standardise from those merely waiting, and no document in either
   repository states that `sycl_ext_oneapi_prod` became
   `sycl_khr_queue_flush`. A one-line status field in each vendor specification
   would make the backlog a triaged queue rather than a pile.

4. **Triage the 45 extensions already older than the mean successful wait.** The
   median never-proposed extension is 3.2 years old — already older than the
   average extension that made it through — so age no longer signals anything. Each
   should be explicitly classified as "intended for `KHR`", "vendor-permanent" or
   "obsolete". The 23 that are vendor- or backend-scoped by construction reduce the
   real target from 91 to 68 immediately.

5. **Deprecate vendor extensions when their `KHR` replacement lands.** Otherwise
   the vendor surface only grows, the 8.5% Khronos share improves more slowly than
   the work justifies, and the same API is specified twice. Vulkan does this
   routinely; SYCL has done it zero times in six absorptions.

6. **Use a scheduled publication cadence and batch merges.** Vulkan publishes 2.2
   extensions per release, roughly every 40 days. Batching amortises the fixed cost
   of a release and turns "when is it ready" into "which train does it catch";
   SYCL's own history shows the capacity exists in bursts — 10 proposals were open
   concurrently on 2025-05-05 — but merges arrive one at a time.

7. **Introduce a provisional or experimental `KHR` status.** Vulkan's provisional
   mechanism has finalised 7 extensions (median 391 days) with 5 still open, and
   its retired `KHX` tier shows the escape hatch working even when it is later
   withdrawn. `sycl_khr_command_graph` was closed unmerged after 32 days with 1201
   lines of specification written; a provisional status is the difference between
   that outcome and a published extension carrying a stability warning.

8. **Consider a tier between vendor and `KHR`.** This is the structural version of
   item 7 and the largest change proposed here. SYCL's single jump from a vendor
   namespace to ratified `KHR` gives contested designs nowhere to sit, which is
   part of why the median wait is over three years. A multi-vendor tier requiring
   agreement but not ratification would need at least two independent SYCL
   implementations to be meaningful, which is why it is listed last rather than
   first.

9. **Either raise concurrency or cut turnaround — pick one explicitly.** At the
   measured mean latency of 232 days, sustaining Vulkan's 15.6/yr needs 8–10
   proposals in flight (Little's Law), against the 4.8 average observed; holding
   concurrency at 4.8 instead needs median time-to-merge to fall from 237 days to
   about 112. Both are feasible readings of the data, but they imply different
   investments, and the current pipeline is drifting rather than choosing: arrivals
   run at 0.62/month and resolutions at 0.41/month, so work in progress grows by
   one extension every five months.

## What not to conclude

* **Matching Vulkan's rate as a count is not the same as matching its pace.**
  Vulkan's 15.6 `KHR`/yr is set against 504 published extensions, so it
  standardises 15.6 / 504 = **3.1% of its own extension surface per year**. SYCL's
  4.9 `KHR`/yr against a 106-extension surface (9 `KHR` plus the 97 `intel/llvm`
  vendor extensions) is 4.9 / 106 = **4.6% per year**, so
  in proportional terms SYCL is already ahead by a factor of 1.5. Vulkan's pace
  applied to a surface SYCL's size would be 3.1% × 106 = **3.3 extensions/yr**,
  below what SYCL does today; SYCL's pace applied to a surface Vulkan's size would
  be 4.6% × 504 = 23/yr, above what Vulkan does. The absolute count is
  nevertheless the right target here, because the backlog is 91 specific documents
  and 91 documents need the same number of `KHR` merges whatever the size of the
  surface they sit in. Read the 2.6–3.2× increase as the size of the job to be
  done, not as evidence that SYCL is standardising more slowly than Vulkan for its
  size.
* **Raising throughput shortens the waiting, not the work — these are two
  different quantities.** Throughput is how many extensions are published per year;
  latency is how long one takes. For an absorbed extension the latency splits into
  the time its vendor document sits in `intel/llvm` before anyone opens a `KHR`
  pull request, and the time that pull request then takes. For the five absorbed so
  far the total averaged 1159 days (3.2 years), of which the pull request accounted
  for only **137 days on average (12%)**; the other **1022 days (2.8 years, 88%)
  was the document waiting to be started**. Throughput governs that waiting: at
  2.6–3.2× the current rate the queue shrinks proportionally and the average
  vendor-spec-to-`KHR` wait would fall from 3.2 years to roughly **1.2–1.5 years**,
  which is a real improvement. What throughput cannot compress is the pull request
  itself — drafting, review and ratification take what they take, so no individual
  extension arrives sooner than the observed 137-day average (best case 58 days,
  and 232 days across all nine published extensions). Two practical consequences:
  the estimates in [`table.md`](table.md) are about clearing a queue, not about any
  one extension appearing sooner; and by Little's Law, tripling throughput without
  tripling the number of proposals in flight would require the pull-request phase to
  get *faster*, so if neither concurrency nor review time changes, higher throughput
  is not available at all.
* **All projections here are linear extrapolations** from small samples — 6
  absorptions over 22 months, 9 merges over 24 — and the split of the vendor pool
  into "portable" and "vendor-scoped" is a judgement made for this analysis, not a
  position held by either project. See the caveats in
  [`table.md`](table.md#caveats) and
  [`vulkan_table.md`](vulkan_table.md#caveats).
