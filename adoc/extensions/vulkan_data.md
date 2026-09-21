# Vulkan extensions: creation dates and development velocity

Generated from the `git` history of `/home/dvrogozh/git/Vulkan-Docs` (`main` at
`7d39c89`, 2026-09-18) and from the extension registry `xml/vk.xml`, as of
2026-09-21. This is the Vulkan counterpart of the SYCL analysis in
[`table.md`](table.md); see [Methodology](#methodology) for what "created"
means here and why it differs from the SYCL numbers. [`summary.md`](summary.md)
condenses both documents into key facts and suggestions for the SYCL flow, and
[`summary2.md`](summary2.md) covers the SYCL absorption timeline.

## Summary

* **504 extensions have been published** in the 10.6 years since Vulkan 1.0
  (2016-02-16), of which **483 are live** today and 21 were withdrawn.
* Publication runs at **47.6 extensions per year** (3.96 per month) across the
  whole period, and has been remarkably stable at ~45/year since 2018.
* **Khronos (`KHR`) extensions are published at 15.6 per year** over the whole
  period and 12.7 per year since 2018 — about one a month, in bursts of 2.2 every
  40 days — while 5.9 per year are folded into core.
* The registry holds 715 extension slots; **229 (32%) are reserved but were
  never published** — the closest Vulkan analogue to an unfinished proposal.
* Vendor extensions are the largest group by count, Khronos extensions dominate
  promotion into core, and no vendor extension has ever gone straight to core.

## Overall velocity

| Metric | Value |
| --- | --- |
| Window | 2016-02-16 → 2026-09-21 = 3870 days (10.6 years) |
| Extensions ever published | **504** |
| Live today | **483** |
| Withdrawn after publication | 21 (4%) |
| Publication rate | **47.6 per year** (3.96 per month) |
| Rate 2018–2025 (excluding the launch surge) | 44.0 per year |
| Rate 2021–2025 | 45.4 per year |
| Releases that published at least one extension | 232 (median 14 days apart) |
| Extensions per such release | 2.2 |
| Age of a live extension | mean 5.4 years, median 5.3 years |
| Appendix size | 35080 lines total, median 52, mean 72, max 772 |
| Spec revisions per extension | mean 1.9, median 1, max 70; 76% never revised |
| Registry slots reserved but never published | **229** |

Vulkan publishes on a fortnightly spec-update cadence (1189 public commits,
112 per year), and about 2.2 extensions ship per publishing release.

## By extension type

Extensions are grouped the way the specification itself groups them: Khronos
(`KHR`, plus the retired experimental `KHX`), multi-vendor (`EXT`), and
single-vendor (everything else).

| Class | Published | Share | Live | Withdrawn | Rate | Ratified | Promoted | → core | → other ext | Deprecated/obsoleted |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| Khronos | 165 | 33% | 151 | 14 | 15.6/yr | 152 (92%) | 63 (38%) | 63 | 0 | 0 |
| Multi-vendor | 157 | 31% | 153 | 4 | 14.8/yr | 129 (82%) | 40 (25%) | 23 | 17 | 7 |
| Vendor | 182 | 36% | 179 | 3 | 17.2/yr | 0 (0%) | 12 (7%) | 0 | 12 | 14 |

| Class | Total lines | Median lines | Mean revisions | Share revised | Median promotion latency | Reserved, never published |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| Khronos | 12427 | 60 | 2.8 | 23% | 312 days | 29 |
| Multi-vendor | 10444 | 51 | 1.5 | 24% | 878 days | 64 |
| Vendor | 12209 | 48 | 1.4 | 25% | 1096 days | 136 |

Reading the two tables together:

* **Khronos (`KHR`) extensions are the road into core.** 38% of them have been
  promoted, every one of those into a core version, at a median of 312 days
  after publication. 92% are ratified.
* **Multi-vendor (`EXT`) extensions are the staging area.** A quarter get
  promoted, but only 23 of 40 promotions go to core — the other 17 are
  re-published as `KHR` extensions first. Median latency is 878 days, roughly
  three times the `KHR`→core figure.
* **Vendor extensions almost never move.** 7% are promoted, **none directly to
  core**, all 12 via an `EXT` or `KHR` re-publication, at a median of 1096 days
  — three years. None is ratified, and they carry most of the deprecations.
* Document size and revision churn barely differ between classes (median 48–60
  lines, ~24% ever revised), so the class differences are governance, not effort.

### Khronos (`KHR`) publication rate

| Window | Length | `KHR`+`KHX` published | Rate | Share of all extensions published |
| --- | ---: | ---: | ---: | ---: |
| All time (2016-02-16 →) | 10.60 y | 165 | **15.6/yr** (1.30/month) | 32.7% |
| 2018-01-01 → (excluding the launch and `KHX` surge) | 8.72 y | 111 | **12.7/yr** (1.06/month) | 28.5% |
| Last 5 years | 5.00 y | 64 | **12.8/yr** (1.07/month) | 27.8% |
| Last 2 years | 2.00 y | 30 | **15.0/yr** (1.25/month) | 30.3% |
| Last 1 year | 1.00 y | 13 | **13.0/yr** (1.08/month) | 24.1% |

The steady-state figure is **12–15 `KHR` extensions per year, about one per
month**, and it has barely moved in eight years: 12.7/yr since 2018, 12.8/yr over
the last five years, 15.0/yr over the last two. The all-time 15.6/yr is inflated
by the first two years — 11 at the 1.0 launch, then 31 `KHR` plus 12 `KHX` during
2017. Of the 165, 153 are `KHR` and 12 are the retired `KHX` experimental set.

Publication is bursty rather than continuous. The 165 extensions appeared on only
**76 distinct dates, 2.2 at a time**, with a median of 40 days between
`KHR`-publishing releases (mean 51, longest gap 328 days, from 2016-02-24 to
2017-01-17). The largest batches were 18 on 2017-07-11, 14 on 2017-02-26 (the
`KHX` set), 10 at the 1.0 launch, and 9 on 2024-01-25 ahead of Vulkan 1.4.

Against that inflow, the outflow into core runs at **5.9 per year** — 63
promotions in 10.6 years, distributed 23 into Vulkan 1.1, 18 into 1.2, 9 into
1.3 and 13 into 1.4. Roughly two `KHR` extensions are published for every one
that is folded into a core version.

### By vendor tag

| Tag | Class | Published | Live | First | Latest | Promoted | Median lines | Revised >1 | Reserved, unpublished |
| --- | --- | ---: | ---: | --- | --- | ---: | ---: | ---: | ---: |
| `EXT` | Multi-vendor | 157 | 153 | 2016-02-16 | 2026-08-07 | 40 | 51 | 36 | 64 |
| `KHR` | Khronos | 153 | 151 | 2016-02-16 | 2026-09-04 | 63 | 60 | 35 | 29 |
| `NV` | Vendor | 70 | 70 | 2016-03-03 | 2026-08-28 | 7 | 62 | 20 | 26 |
| `AMD` | Vendor | 24 | 24 | 2016-04-29 | 2026-05-08 | 1 | 36 | 4 | 33 |
| `QCOM` | Vendor | 21 | 21 | 2020-03-06 | 2026-05-08 | 2 | 61 | 6 | 7 |
| `ARM` | Vendor | 15 | 15 | 2021-11-23 | 2026-06-26 | 1 | 45 | 3 | 8 |
| `KHX` | Khronos | 12 | 0 | 2017-02-26 | 2017-02-26 | 0 | 0 | 0 | 0 |
| `VALVE` | Vendor | 6 | 6 | 2020-12-07 | 2026-09-04 | 1 | 38 | 0 | 3 |
| `NVX` | Vendor | 5 | 3 | 2016-11-26 | 2021-05-10 | 0 | 93 | 3 | 1 |
| `GOOGLE` | Vendor | 5 | 5 | 2017-03-10 | 2021-12-20 | 0 | 27 | 1 | 8 |
| `IMG` | Vendor | 4 | 4 | 2016-03-10 | 2026-06-12 | 0 | 38 | 0 | 5 |
| `FUCHSIA` | Vendor | 4 | 4 | 2018-10-07 | 2021-09-28 | 0 | 40 | 1 | 2 |
| `HUAWEI` | Vendor | 4 | 4 | 2021-06-19 | 2024-11-01 | 0 | 164 | 2 | 7 |
| `SEC` | Vendor | 4 | 4 | 2022-08-04 | 2026-05-01 | 0 | 69 | 0 | 5 |
| `INTEL` | Vendor | 3 | 3 | 2019-05-22 | 2026-09-18 | 0 | 77 | 1 | 1 |
| `OHOS` | Vendor | 3 | 2 | 2025-06-13 | 2025-10-30 | 0 | 34 | 0 | 0 |
| `MVK` | Vendor | 2 | 2 | 2017-02-26 | 2017-02-26 | 0 | 44 | 2 | 1 |
| `ANDROID` | Vendor | 2 | 2 | 2018-03-17 | 2023-09-29 | 0 | 92 | 1 | 1 |
| `GGP` | Vendor | 2 | 2 | 2019-03-19 | 2019-03-19 | 0 | 36 | 0 | 6 |
| `QNX` | Vendor | 2 | 2 | 2021-02-24 | 2023-06-15 | 0 | 35 | 0 | 0 |
| `AMDX` | Vendor | 2 | 2 | 2023-07-28 | 2025-08-01 | 0 | 40 | 1 | 0 |
| `NN` | Vendor | 1 | 1 | 2017-01-17 | 2017-01-17 | 0 | 52 | 0 | 0 |
| `LUNARG` | Vendor | 1 | 1 | 2022-12-01 | 2022-12-01 | 0 | 27 | 0 | 0 |
| `MSFT` | Vendor | 1 | 1 | 2023-07-19 | 2023-07-19 | 0 | 31 | 0 | 0 |
| `MESA` | Vendor | 1 | 1 | 2024-05-10 | 2024-05-10 | 0 | 46 | 0 | 5 |

Three vendors account for 115 of the 182 vendor extensions (NVIDIA 70, AMD 24,
Qualcomm 21). `KHX` is a closed chapter: all 12 experimental Khronos extensions
from 2017 were withdrawn and re-published as `KHR`. AMD has reserved 33
registry slots and published 24 extensions — the only tag with more reservations
than publications at that scale.

## Cadence by year

| Year | Khronos | Multi-vendor | Vendor | Total | Cumulative |
| --- | ---: | ---: | ---: | ---: | ---: |
| 2016 | 11 | 3 | 17 | 31 | 31 |
| 2017 | 43 | 21 | 19 | 83 | 114 |
| 2018 | 14 | 14 | 19 | 47 | 161 |
| 2019 | 12 | 20 | 14 | 46 | 207 |
| 2020 | 11 | 12 | 9 | 32 | 239 |
| 2021 | 13 | 21 | 14 | 48 | 287 |
| 2022 | 6 | 26 | 13 | 45 | 332 |
| 2023 | 11 | 13 | 26 | 50 | 382 |
| 2024 | 16 | 7 | 9 | 32 | 414 |
| 2025 | 18 | 12 | 22 | 52 | 466 |
| 2026 (partial) | 10 | 8 | 20 | 38 | 504 |

2017 is the outlier: 83 extensions, half of them `KHR`, as the experimental
`KHX` set was reissued and the 1.1 feature set was assembled. From 2018 onward
the total is strikingly steady — between 32 and 52 every year, mean 44.0 — while
the mix rotates: `EXT` peaked in 2022 (26), vendor extensions in 2023 (26), and
`KHR` has been climbing again since 2024 (16, 18, 10 so far).

## Lifecycle

Vulkan has no public proposal→acceptance transition to measure (see
[Methodology](#methodology)), but it does have three observable post-publication
transitions, and these are the nearest equivalent of a latency metric.

| Transition | n | Median | Mean | Range |
| --- | ---: | ---: | ---: | --- |
| Published → promoted into a core version | 86 | **361 days** | 456 | 0–2836 |
| Published → re-published as a higher-tier extension | 29 | **1107 days** | 1182 | 198–2849 |
| Provisional → final | 7 | **391 days** | 491 | 250–979 |

Longest waits into core:

* `VK_KHR_push_descriptor` → Vulkan 1.4, 2836 days (7.8 years)
* `VK_KHR_sampler_mirror_clamp_to_edge` → Vulkan 1.2, 1420 days (3.9 years)
* `VK_EXT_inline_uniform_block` → Vulkan 1.3, 1231 days (3.4 years)
* `VK_KHR_global_priority` → Vulkan 1.4, 1046 days (2.9 years)
* `VK_EXT_pipeline_creation_feedback` → Vulkan 1.3, 1041 days (2.9 years)

Longest vendor/`EXT` → higher-tier re-publications:

* `VK_NV_shader_subgroup_partitioned` → `VK_EXT_shader_subgroup_partitioned`, 2849 days (7.8 years)
* `VK_NV_compute_shader_derivatives` → `VK_KHR_compute_shader_derivatives`, 2176 days (6.0 years)
* `VK_EXT_vertex_attribute_divisor` → `VK_KHR_vertex_attribute_divisor`, 2102 days (5.8 years)
* `VK_QCOM_render_pass_shader_resolve` → `VK_EXT_custom_resolve`, 2028 days (5.6 years)
* `VK_EXT_calibrated_timestamps` → `VK_KHR_calibrated_timestamps`, 1882 days (5.2 years)

5 extensions are still provisional: `VK_AMDX_dense_geometry_format`, `VK_AMDX_shader_enqueue`, `VK_KHR_portability_subset`, `VK_NV_cuda_kernel_launch`, `VK_NV_displacement_micromap`.

### Withdrawals (21)

| Published | Extension | Note |
| --- | --- | --- |
| 2016-02-16 | `VK_KHR_mir_surface` | Mir WSI support dropped |
| 2016-11-26 | `VK_NVX_device_generated_commands` | superseded by `VK_NV_device_generated_commands` |
| 2017-02-26 | `VK_KHX_device_group` | reissued as `VK_KHR_device_group` |
| 2017-02-26 | `VK_KHX_device_group_creation` | reissued as `VK_KHR_device_group_creation` |
| 2017-02-26 | `VK_KHX_external_memory` | reissued as `VK_KHR_external_memory` |
| 2017-02-26 | `VK_KHX_external_memory_capabilities` | reissued as `VK_KHR_external_memory_capabilities` |
| 2017-02-26 | `VK_KHX_external_memory_fd` | reissued as `VK_KHR_external_memory_fd` |
| 2017-02-26 | `VK_KHX_external_memory_win32` | reissued as `VK_KHR_external_memory_win32` |
| 2017-02-26 | `VK_KHX_external_semaphore` | reissued as `VK_KHR_external_semaphore` |
| 2017-02-26 | `VK_KHX_external_semaphore_capabilities` | reissued as `VK_KHR_external_semaphore_capabilities` |
| 2017-02-26 | `VK_KHX_external_semaphore_fd` | reissued as `VK_KHR_external_semaphore_fd` |
| 2017-02-26 | `VK_KHX_external_semaphore_win32` | reissued as `VK_KHR_external_semaphore_win32` |
| 2017-02-26 | `VK_KHX_multiview` | reissued as `VK_KHR_multiview` |
| 2017-02-26 | `VK_KHX_win32_keyed_mutex` | reissued as `VK_KHR_win32_keyed_mutex` |
| 2018-09-15 | `VK_NVX_raytracing` | renamed `VK_NV_ray_tracing` |
| 2020-03-17 | `VK_KHR_ray_tracing` | split into `VK_KHR_acceleration_structure` / `VK_KHR_ray_tracing_pipeline` |
| 2021-04-13 | `VK_EXT_video_decode_h264` | reissued as `VK_KHR_video_decode_h264` |
| 2021-04-13 | `VK_EXT_video_decode_h265` | reissued as `VK_KHR_video_decode_h265` |
| 2021-04-13 | `VK_EXT_video_encode_h264` | reissued as `VK_KHR_video_encode_h264` |
| 2021-10-13 | `VK_EXT_video_encode_h265` | reissued as `VK_KHR_video_encode_h265` |
| 2025-10-24 | `VK_OHOS_native_buffer` | withdrawn 2025 |

Withdrawal is overwhelmingly renaming rather than failure: 12 of the 21 are the
2017 `KHX` experimental set reissued as `KHR`, 4 are the provisional
`VK_EXT_video_*` codecs reissued as `KHR`, and 2 more are ray-tracing
restructurings. Only `VK_KHR_mir_surface` and `VK_OHOS_native_buffer` were
genuinely dropped.

## Externally proposed extensions (fork pull requests)

Repeating the SYCL fork-PR scan on Vulkan-Docs: 778 pull-request heads were
fetched and searched for extension documents whose names never entered the
registry. 14 such proposals were found in PRs, plus one that lived on `main`.

| Extension | State | Opened | Age / resolved | PR(s) |
| --- | --- | --- | --- | --- |
| `VK_EXT_occlusion_extents` | open | 2023-07-05 | 1174 days | [#2163](https://github.com/KhronosGroup/Vulkan-Docs/pull/2163) |
| `VK_MESA_legacy_dma_buf_drm_format_modifier_query` | open (draft) | 2025-03-06 | 564 days | [#2505](https://github.com/KhronosGroup/Vulkan-Docs/pull/2505) |
| `VK_EXT_external_semaphore_drm_syncobj` | open | 2026-03-02 | 203 days | [#2692](https://github.com/KhronosGroup/Vulkan-Docs/pull/2692) |
| `VK_EXT_ycbcr_3plane_16bit_lsb_formats` | open | 2026-04-01 | 173 days | [#2709](https://github.com/KhronosGroup/Vulkan-Docs/pull/2709) |
| `VK_EXT_fragment_coverage_mask` | open (draft) | 2026-05-06 | 138 days | [#2724](https://github.com/KhronosGroup/Vulkan-Docs/pull/2724) |
| `VK_EXT_image_2d_array_of_3d` | abandoned | 2022-04-05 | proposal deleted from `main` 2026-03-13, after 1438 days | — |
| `VK_EXT_acquire_wl_display` | closed | 2019-07-11 | closed 2021-07-06 (726 days) | [#1001](https://github.com/KhronosGroup/Vulkan-Docs/pull/1001), [#1450](https://github.com/KhronosGroup/Vulkan-Docs/pull/1450) |
| `VK_EXT_calibrated_queue_timestamps` | closed | 2021-04-28 | closed 2021-05-03 (5 days) | [#1517](https://github.com/KhronosGroup/Vulkan-Docs/pull/1517) |
| `VK_EXT_wl_drm_lease_display` | closed | 2021-05-06 | closed 2021-05-11 (1 and 4 days) | [#1524](https://github.com/KhronosGroup/Vulkan-Docs/pull/1524), [#1525](https://github.com/KhronosGroup/Vulkan-Docs/pull/1525) |
| `VK_MESA_rect_list` | closed | 2021-11-16 | closed 2021-11-17 (1 day) | [#1688](https://github.com/KhronosGroup/Vulkan-Docs/pull/1688) |
| `VK_EXT_forced_multisample` | closed | 2021-11-18 | closed 2021-12-20 (32 days) | [#1695](https://github.com/KhronosGroup/Vulkan-Docs/pull/1695) |
| `VK_FOOL_printed_surface` | closed | 2022-03-31 | closed 2022-04-04 (4 days) | [#1816](https://github.com/KhronosGroup/Vulkan-Docs/pull/1816) |
| `VK_EXT_disable_wayland_color_management` | closed | 2024-08-16 | closed 2025-06-18 (306 days) | [#2410](https://github.com/KhronosGroup/Vulkan-Docs/pull/2410) |
| `VK_KHR_indexed_vkformat` | closed | 2024-08-31 | closed 2024-10-09 (39 days) | [#2427](https://github.com/KhronosGroup/Vulkan-Docs/pull/2427) |
| `VK_EXT_swapchain_colorspace2` | closed | 2026-01-04 | closed 2026-01-26 (22 days) | [#2649](https://github.com/KhronosGroup/Vulkan-Docs/pull/2649) |

**None of the 10 resolved proposals on this route was ever published** — a 0%
acceptance rate, against 90% for SYCL fork PRs. That is a difference in process,
not in quality: Vulkan-Docs is a read-only mirror of a Khronos-internal
repository, so a fork PR is a request for the working group to take an idea up,
not a merge candidate. Several ideas did reach the spec by the internal route
under different names. Closure is usually fast (median 22 days), with two
exceptions left open for 726 and 306 days. `VK_FOOL_printed_surface` was an
April Fools' submission and is listed only for completeness.

The larger unfinished-work signal in Vulkan is not pull requests but the
registry itself: **229 extension slots are reserved with `supported="disabled"` and
have never been published** — 136 vendor, 64 `EXT`, 29 `KHR`. Vulkan reserves an
extension number publicly at the start of development, so these are visible
abandoned or in-progress efforts, in roughly the ratio 1 reserved slot for
every 2.2 published extensions.

## Comparison with the SYCL KHR extensions

| Metric | Vulkan | SYCL |
| --- | --- | --- |
| Window | 10.6 years (2016-02-16 →) | 2.0 years (2024-09-17 →) |
| Published extensions | 504 | 9 |
| Publication rate, all extensions | 3.96/month (47.6/yr) | 0.41/month (4.9/yr) |
| Publication rate, Khronos (`KHR`) only | 1.30/month (15.6/yr); 1.06/month since 2018 | 0.41/month (4.9/yr) |
| Proposals visible in public PRs | 14 (0 accepted) | 15 (9 accepted) |
| Unfinished work visible as | 229 reserved registry slots | 5 open pull requests |
| Observable proposal→acceptance latency | not observable (private development) | mean 232 days |
| Nearest latency analogue | 312 days `KHR`→core promotion | — |
| Median document size | 52 lines | 103 lines |
| Extension tiers | vendor → `EXT` → `KHR` → core | `KHR` only |
| Khronos share of all extensions | 165 of 504 (**33%**) | 9 of 106 (**8.5%**) |
| Khronos share of the last 2 years' new extensions | 30 of 99 (**30%**) | 9 of 31 (**29%**) |
| Khronos extensions published in the last 2 years | 30 (15.0/yr) | 9 (4.5/yr) |

The SYCL rows count the 97 vendor extensions shipped by `intel/llvm` alongside
the 9 published `sycl_khr_*` extensions, treating `oneapi`, `intel` and
`codeplay` all as vendor; see [Composition: Khronos versus vendor
extensions](table.md#composition-khronos-versus-vendor-extensions) for that
derivation.

Vulkan publishes about 10 extensions for every one SYCL publishes; restricted to
Khronos extensions, where the governance work is comparable, the gap narrows to
**3.2×** (15.6/yr against 4.9/yr, or 2.6× using Vulkan's post-2018 12.7/yr). But
the comparison flatters neither process: Vulkan achieves that rate by doing the
contested work in private and publishing only finished extensions, so its public
history contains no rejected or stalled specifications to count. SYCL does the
opposite — every draft, revision and abandonment is in the open repository.

Two figures are directly comparable. The first is the tiering: SYCL has a single
`KHR` tier, whereas 67% of Vulkan extensions start below `KHR` and only 10% of
those ever climb. The second is composition, and it separates cleanly into stock
and flow. Vulkan's accumulated stock is 33% Khronos and has never been below 31%
at any point in its history — it had `KHR` extensions from the first release, and
its Khronos share was 33% after one year and 47% after two. SYCL's stock is 8.5%
Khronos, because its `KHR` process is two years old and sits on seven years of
accumulated vendor extensions. But over the last two years the two projects
standardised almost the same fraction of their new extensions: 30% for Vulkan,
29% for SYCL. The difference is entirely the backlog, not the balance of current
effort.

## Methodology

**"Created" means published.** For each extension, the date recorded is the
first appearance in `vk.xml` with a `supported` attribute other than
`disabled` — that is, the spec release in which the extension became public.
Every historical revision of `vk.xml` on `main` (528 blobs, across its former
path `src/spec/vk.xml`) was streamed through `git cat-file --batch` and parsed:

```sh
git log --format='%H|%cd' --date=short main -- xml/vk.xml src/spec/vk.xml
# then, per revision, extract <extension name=... supported=...>
```

Appendix file dates were *not* used as creation dates. The per-extension
appendix files were introduced by a documentation restructure in August 2016, so
`git log --follow appendices/VK_KHR_surface.adoc` reports 2016-08-28 for an
extension that shipped with Vulkan 1.0 on 2016-02-16. Appendix files are used
only for document sizes.

Pull-request heads were made visible with the same refspec trick as the SYCL
analysis:

```sh
git config --add remote.origin.fetch '+refs/pull/*/head:refs/remotes/origin/pr/*'
git fetch origin   # 778 PR heads
```

PR states and dates were read from the GitHub PR pages; the REST API was
unavailable (unauthenticated rate limit). Core version dates come from the first
commit introducing each `VK_VERSION_1_x` token: 1.0 2016-02-16, 1.1 2018-03-07,
1.2 2020-01-14, 1.3 2022-01-21, 1.4 2024-12-02.

### Caveats

* **No submission→acceptance latency exists in this data.** Vulkan extensions
  are developed in a Khronos-internal repository and appear in Vulkan-Docs
  already finished; the public repository squashes each spec release into a
  single commit (1189 commits for 504 extensions). The SYCL figures for time to
  merge, work in progress and acceptance ratio therefore have no counterpart,
  and the promotion and provisional latencies above are substitutes measured
  *after* publication.
* Proposal documents in `proposals/` do not help: 153 of 504 published
  extensions have one, and 144 of those were added on the same day the
  extension was published (the directory itself only starts in July 2021).
* Dates are **committer** dates, not author dates. 190 of the 1189 commits on
  `main` carry a backdated author date — commit `86de8ac8`, for instance, was
  pushed 2018-07-09 with an author date of 2017-10-28 — which would place 17
  extensions in the wrong year. The committer date is when a revision actually
  became public.
  Conversely, a release commit typically lands one day before the date in its
  own change-log subject (the Vulkan 1.2 commit is dated 2020-01-14 and reads
  "Change log for January 15, 2020"), so dates here can run a day early. Core
  version dates are taken from git the same way, so the promotion latencies
  are internally consistent.
* Publication dates are public-repository dates. A Khronos press announcement
  may precede the vk.xml change by days; `VK_NV_ray_tracing` is dated
  2018-11-03 here because it reached the registry under that name then, having
  first appeared as `VK_NVX_raytracing` on 2018-09-15.
* Vulkan SC-only extensions (`supported="vulkansc"`) are included in the counts.
* Withdrawn extensions retain the publication date of their withdrawn name;
  their replacements count as separate publications. This inflates 2017 (the
  `KHX`→`KHR` reissue) by about 12.
* 2026 is a partial year, and the reserved-slot count is a snapshot: a slot may
  be published tomorrow.

## Appendix: all published extensions by date

`Rev` is the current `SPEC_VERSION`; `Lines` is the current appendix size.
`Promoted to` is the `promotedto` attribute from `vk.xml`.

| # | Extension | Class | Published | Rev | Lines | Status | Promoted to |
| ---: | --- | --- | --- | ---: | ---: | --- | --- |
| 1 | `VK_EXT_debug_report` | Multi-vendor | 2016-02-16 | 10 | 212 | live, deprecated | — |
| 2 | `VK_KHR_android_surface` | Khronos | 2016-02-16 | 6 | 74 | live | — |
| 3 | `VK_KHR_display` | Khronos | 2016-02-16 | 23 | 347 | live | — |
| 4 | `VK_KHR_display_swapchain` | Khronos | 2016-02-16 | 10 | 137 | live | — |
| 5 | `VK_KHR_mir_surface` | Khronos | 2016-02-16 | 4 | — | withdrawn | — |
| 6 | `VK_KHR_surface` | Khronos | 2016-02-16 | 25 | 234 | live | — |
| 7 | `VK_KHR_swapchain` | Khronos | 2016-02-16 | 70 | 772 | live | — |
| 8 | `VK_KHR_wayland_surface` | Khronos | 2016-02-16 | 6 | 92 | live | — |
| 9 | `VK_KHR_win32_surface` | Khronos | 2016-02-16 | 6 | 122 | live | — |
| 10 | `VK_KHR_xcb_surface` | Khronos | 2016-02-16 | 6 | 78 | live | — |
| 11 | `VK_KHR_xlib_surface` | Khronos | 2016-02-16 | 6 | 78 | live | — |
| 12 | `VK_KHR_sampler_mirror_clamp_to_edge` | Khronos | 2016-02-24 | 3 | 88 | live | `VK_VERSION_1_2` |
| 13 | `VK_NV_glsl_shader` | Vendor | 2016-03-03 | 1 | 62 | live | — |
| 14 | `VK_IMG_filter_cubic` | Vendor | 2016-03-10 | 1 | 52 | live | — |
| 15 | `VK_AMD_rasterization_order` | Vendor | 2016-04-29 | 1 | 98 | live | — |
| 16 | `VK_EXT_debug_marker` | Multi-vendor | 2016-05-06 | 4 | 178 | live | `VK_EXT_debug_utils` |
| 17 | `VK_AMD_gcn_shader` | Vendor | 2016-05-31 | 1 | 33 | live | — |
| 18 | `VK_AMD_shader_explicit_vertex_parameter` | Vendor | 2016-05-31 | 1 | 34 | live | — |
| 19 | `VK_AMD_shader_trinary_minmax` | Vendor | 2016-05-31 | 1 | 34 | live | — |
| 20 | `VK_NV_dedicated_allocation` | Vendor | 2016-07-10 | 1 | 108 | live, deprecated | — |
| 21 | `VK_IMG_format_pvrtc` | Vendor | 2016-08-12 | 1 | 39 | live | — |
| 22 | `VK_AMD_draw_indirect_count` | Vendor | 2016-08-28 | 2 | 41 | live | `VK_KHR_draw_indirect_count` |
| 23 | `VK_NV_external_memory` | Vendor | 2016-08-28 | 1 | 73 | live, deprecated | — |
| 24 | `VK_NV_external_memory_capabilities` | Vendor | 2016-08-28 | 1 | 65 | live, deprecated | — |
| 25 | `VK_NV_external_memory_win32` | Vendor | 2016-08-28 | 1 | 214 | live, deprecated | — |
| 26 | `VK_NV_win32_keyed_mutex` | Vendor | 2016-08-28 | 2 | 171 | live | `VK_KHR_win32_keyed_mutex` |
| 27 | `VK_AMD_negative_viewport_height` | Vendor | 2016-09-16 | 1 | 42 | live, obsolete | — |
| 28 | `VK_EXT_validation_flags` | Multi-vendor | 2016-09-16 | 3 | 40 | live, deprecated | — |
| 29 | `VK_AMD_gpu_shader_half_float` | Vendor | 2016-09-24 | 2 | 41 | live, deprecated | — |
| 30 | `VK_AMD_shader_ballot` | Vendor | 2016-09-24 | 1 | 35 | live | — |
| 31 | `VK_NVX_device_generated_commands` | Vendor | 2016-11-26 | 3 | — | withdrawn | — |
| 32 | `VK_EXT_acquire_xlib_display` | Multi-vendor | 2017-01-17 | 1 | 58 | live | — |
| 33 | `VK_EXT_direct_mode_display` | Multi-vendor | 2017-01-17 | 1 | 53 | live | — |
| 34 | `VK_EXT_display_control` | Multi-vendor | 2017-01-17 | 1 | 58 | live | — |
| 35 | `VK_EXT_display_surface_counter` | Multi-vendor | 2017-01-17 | 1 | 32 | live | — |
| 36 | `VK_EXT_shader_subgroup_ballot` | Multi-vendor | 2017-01-17 | 1 | 101 | live, deprecated | — |
| 37 | `VK_EXT_shader_subgroup_vote` | Multi-vendor | 2017-01-17 | 1 | 115 | live, deprecated | — |
| 38 | `VK_EXT_swapchain_colorspace` | Multi-vendor | 2017-01-17 | 5 | 66 | live | — |
| 39 | `VK_KHR_get_physical_device_properties2` | Khronos | 2017-01-17 | 2 | 102 | live | `VK_VERSION_1_1` |
| 40 | `VK_KHR_maintenance1` | Khronos | 2017-01-17 | — | 87 | live | `VK_VERSION_1_1` |
| 41 | `VK_KHR_shader_draw_parameters` | Khronos | 2017-01-17 | 1 | 91 | live | `VK_VERSION_1_1` |
| 42 | `VK_NN_vi_surface` | Vendor | 2017-01-17 | 1 | 52 | live | — |
| 43 | `VK_EXT_discard_rectangles` | Multi-vendor | 2017-02-26 | 2 | 57 | live | — |
| 44 | `VK_KHR_descriptor_update_template` | Khronos | 2017-02-26 | 1 | 49 | live | `VK_VERSION_1_1` |
| 45 | `VK_KHR_push_descriptor` | Khronos | 2017-02-26 | 2 | 39 | live | `VK_VERSION_1_4` |
| 46 | `VK_KHX_device_group` | Khronos | 2017-02-26 | — | — | withdrawn | — |
| 47 | `VK_KHX_device_group_creation` | Khronos | 2017-02-26 | — | — | withdrawn | — |
| 48 | `VK_KHX_external_memory` | Khronos | 2017-02-26 | — | — | withdrawn | — |
| 49 | `VK_KHX_external_memory_capabilities` | Khronos | 2017-02-26 | — | — | withdrawn | — |
| 50 | `VK_KHX_external_memory_fd` | Khronos | 2017-02-26 | — | — | withdrawn | — |
| 51 | `VK_KHX_external_memory_win32` | Khronos | 2017-02-26 | — | — | withdrawn | — |
| 52 | `VK_KHX_external_semaphore` | Khronos | 2017-02-26 | — | — | withdrawn | — |
| 53 | `VK_KHX_external_semaphore_capabilities` | Khronos | 2017-02-26 | — | — | withdrawn | — |
| 54 | `VK_KHX_external_semaphore_fd` | Khronos | 2017-02-26 | — | — | withdrawn | — |
| 55 | `VK_KHX_external_semaphore_win32` | Khronos | 2017-02-26 | — | — | withdrawn | — |
| 56 | `VK_KHX_multiview` | Khronos | 2017-02-26 | — | — | withdrawn | — |
| 57 | `VK_KHX_win32_keyed_mutex` | Khronos | 2017-02-26 | — | — | withdrawn | — |
| 58 | `VK_MVK_ios_surface` | Vendor | 2017-02-26 | 3 | 44 | live, deprecated | — |
| 59 | `VK_MVK_macos_surface` | Vendor | 2017-02-26 | 3 | 44 | live, deprecated | — |
| 60 | `VK_NVX_multiview_per_view_attributes` | Vendor | 2017-02-26 | 1 | 93 | live | — |
| 61 | `VK_NV_clip_space_w_scaling` | Vendor | 2017-02-26 | 1 | 153 | live | — |
| 62 | `VK_NV_geometry_shader_passthrough` | Vendor | 2017-02-26 | 1 | 168 | live | — |
| 63 | `VK_NV_sample_mask_override_coverage` | Vendor | 2017-02-26 | 1 | 55 | live | — |
| 64 | `VK_NV_viewport_array2` | Vendor | 2017-02-26 | — | 89 | live | — |
| 65 | `VK_NV_viewport_swizzle` | Vendor | 2017-02-26 | 1 | 213 | live | — |
| 66 | `VK_EXT_hdr_metadata` | Multi-vendor | 2017-03-10 | 3 | 71 | live | — |
| 67 | `VK_GOOGLE_display_timing` | Vendor | 2017-03-10 | 1 | 57 | live | — |
| 68 | `VK_KHR_incremental_present` | Khronos | 2017-03-31 | 2 | 98 | live | — |
| 69 | `VK_KHR_get_surface_capabilities2` | Khronos | 2017-05-12 | 1 | 74 | live | — |
| 70 | `VK_KHR_shared_presentable_image` | Khronos | 2017-05-12 | 1 | 128 | live | — |
| 71 | `VK_AMD_texture_gather_bias_lod` | Vendor | 2017-05-20 | 1 | 92 | live | — |
| 72 | `VK_AMD_gpu_shader_int16` | Vendor | 2017-06-26 | 2 | 42 | live, deprecated | — |
| 73 | `VK_EXT_blend_operation_advanced` | Multi-vendor | 2017-06-26 | 2 | 110 | live | — |
| 74 | `VK_EXT_sampler_filter_minmax` | Multi-vendor | 2017-06-26 | 2 | 48 | live | `VK_VERSION_1_2` |
| 75 | `VK_NV_fill_rectangle` | Vendor | 2017-06-26 | 1 | 29 | live | — |
| 76 | `VK_NV_fragment_coverage_to_color` | Vendor | 2017-06-26 | 1 | 34 | live | — |
| 77 | `VK_NV_framebuffer_mixed_samples` | Vendor | 2017-06-26 | 1 | 61 | live | — |
| 78 | `VK_KHR_16bit_storage` | Khronos | 2017-07-11 | 1 | 68 | live | `VK_VERSION_1_1` |
| 79 | `VK_KHR_dedicated_allocation` | Khronos | 2017-07-11 | 3 | 144 | live | `VK_VERSION_1_1` |
| 80 | `VK_KHR_external_fence` | Khronos | 2017-07-11 | 1 | 46 | live | `VK_VERSION_1_1` |
| 81 | `VK_KHR_external_fence_capabilities` | Khronos | 2017-07-11 | 1 | 41 | live | `VK_VERSION_1_1` |
| 82 | `VK_KHR_external_fence_fd` | Khronos | 2017-07-11 | 1 | 38 | live | — |
| 83 | `VK_KHR_external_fence_win32` | Khronos | 2017-07-11 | 1 | 51 | live | — |
| 84 | `VK_KHR_external_memory` | Khronos | 2017-07-11 | 1 | 247 | live | `VK_VERSION_1_1` |
| 85 | `VK_KHR_external_memory_capabilities` | Khronos | 2017-07-11 | 1 | 105 | live | `VK_VERSION_1_1` |
| 86 | `VK_KHR_external_memory_fd` | Khronos | 2017-07-11 | 1 | 59 | live | — |
| 87 | `VK_KHR_external_memory_win32` | Khronos | 2017-07-11 | 1 | 63 | live | — |
| 88 | `VK_KHR_external_semaphore` | Khronos | 2017-07-11 | 1 | 66 | live | `VK_VERSION_1_1` |
| 89 | `VK_KHR_external_semaphore_capabilities` | Khronos | 2017-07-11 | 1 | 39 | live | `VK_VERSION_1_1` |
| 90 | `VK_KHR_external_semaphore_fd` | Khronos | 2017-07-11 | 1 | 44 | live | — |
| 91 | `VK_KHR_external_semaphore_win32` | Khronos | 2017-07-11 | 1 | 73 | live | — |
| 92 | `VK_KHR_get_memory_requirements2` | Khronos | 2017-07-11 | 1 | 44 | live | `VK_VERSION_1_1` |
| 93 | `VK_KHR_storage_buffer_storage_class` | Khronos | 2017-07-11 | 1 | 36 | live | `VK_VERSION_1_1` |
| 94 | `VK_KHR_variable_pointers` | Khronos | 2017-07-11 | 1 | 86 | live | `VK_VERSION_1_1` |
| 95 | `VK_KHR_win32_keyed_mutex` | Khronos | 2017-07-11 | 1 | 32 | live | — |
| 96 | `VK_EXT_depth_range_unrestricted` | Multi-vendor | 2017-07-21 | 1 | 54 | live | — |
| 97 | `VK_AMD_mixed_attachment_samples` | Vendor | 2017-07-31 | 1 | 36 | live | — |
| 98 | `VK_EXT_post_depth_coverage` | Multi-vendor | 2017-07-31 | 1 | 52 | live | — |
| 99 | `VK_KHR_relaxed_block_layout` | Khronos | 2017-07-31 | 1 | 37 | live | `VK_VERSION_1_1` |
| 100 | `VK_EXT_shader_viewport_index_layer` | Multi-vendor | 2017-08-14 | 1 | 89 | live | `VK_VERSION_1_2` |
| 101 | `VK_EXT_shader_stencil_export` | Multi-vendor | 2017-08-20 | 1 | 34 | live | — |
| 102 | `VK_AMD_shader_fragment_mask` | Vendor | 2017-09-04 | 1 | 87 | live | — |
| 103 | `VK_EXT_sample_locations` | Multi-vendor | 2017-09-04 | 1 | 67 | live | — |
| 104 | `VK_EXT_validation_cache` | Multi-vendor | 2017-09-04 | 1 | 35 | live | — |
| 105 | `VK_KHR_bind_memory2` | Khronos | 2017-09-14 | 1 | 39 | live | `VK_VERSION_1_1` |
| 106 | `VK_KHR_image_format_list` | Khronos | 2017-09-14 | 1 | 45 | live | `VK_VERSION_1_2` |
| 107 | `VK_KHR_maintenance2` | Khronos | 2017-09-14 | — | 110 | live | `VK_VERSION_1_1` |
| 108 | `VK_KHR_sampler_ycbcr_conversion` | Khronos | 2017-09-14 | 14 | 91 | live | `VK_VERSION_1_1` |
| 109 | `VK_AMD_shader_image_load_store_lod` | Vendor | 2017-10-06 | 1 | 32 | live | — |
| 110 | `VK_EXT_global_priority` | Multi-vendor | 2017-10-12 | 2 | 57 | live | `VK_KHR_global_priority` |
| 111 | `VK_AMD_shader_info` | Vendor | 2017-10-20 | 1 | 98 | live | — |
| 112 | `VK_EXT_external_memory_dma_buf` | Multi-vendor | 2017-11-27 | 1 | 59 | live | — |
| 113 | `VK_EXT_external_memory_host` | Multi-vendor | 2017-11-27 | 1 | 91 | live | — |
| 114 | `VK_EXT_queue_family_foreign` | Multi-vendor | 2017-11-27 | 1 | 50 | live | — |
| 115 | `VK_EXT_conservative_rasterization` | Multi-vendor | 2018-01-05 | 1 | 83 | live | — |
| 116 | `VK_AMD_buffer_marker` | Vendor | 2018-02-19 | 1 | 36 | live | — |
| 117 | `VK_EXT_debug_utils` | Multi-vendor | 2018-03-07 | 2 | 343 | live | — |
| 118 | `VK_EXT_vertex_attribute_divisor` | Multi-vendor | 2018-03-07 | 3 | 88 | live | `VK_KHR_vertex_attribute_divisor` |
| 119 | `VK_KHR_device_group` | Khronos | 2018-03-07 | 4 | 85 | live | `VK_VERSION_1_1` |
| 120 | `VK_KHR_device_group_creation` | Khronos | 2018-03-07 | 1 | 69 | live | `VK_VERSION_1_1` |
| 121 | `VK_KHR_maintenance3` | Khronos | 2018-03-07 | — | 40 | live | `VK_VERSION_1_1` |
| 122 | `VK_KHR_multiview` | Khronos | 2018-03-07 | 1 | 75 | live | `VK_VERSION_1_1` |
| 123 | `VK_ANDROID_external_memory_android_hardware_buffer` | Vendor | 2018-03-17 | 5 | 147 | live | — |
| 124 | `VK_AMD_shader_core_properties` | Vendor | 2018-04-05 | 2 | 99 | live | — |
| 125 | `VK_EXT_descriptor_indexing` | Multi-vendor | 2018-04-05 | 2 | 88 | live | `VK_VERSION_1_2` |
| 126 | `VK_NV_shader_subgroup_partitioned` | Vendor | 2018-04-05 | 1 | 43 | live | `VK_EXT_shader_subgroup_partitioned` |
| 127 | `VK_KHR_draw_indirect_count` | Khronos | 2018-05-25 | 1 | 48 | live | `VK_VERSION_1_2` |
| 128 | `VK_KHR_get_display_properties2` | Khronos | 2018-05-25 | 1 | 63 | live | — |
| 129 | `VK_EXT_conditional_rendering` | Multi-vendor | 2018-07-07 | 2 | 58 | live | — |
| 130 | `VK_KHR_8bit_storage` | Khronos | 2018-07-07 | 1 | 62 | live | `VK_VERSION_1_2` |
| 131 | `VK_KHR_create_renderpass2` | Khronos | 2018-07-07 | 1 | 56 | live | `VK_VERSION_1_2` |
| 132 | `VK_NV_device_diagnostic_checkpoints` | Vendor | 2018-07-30 | 2 | 35 | live | — |
| 133 | `VK_EXT_astc_decode_mode` | Multi-vendor | 2018-09-08 | 1 | 100 | live | — |
| 134 | `VK_EXT_inline_uniform_block` | Multi-vendor | 2018-09-08 | 1 | 102 | live | `VK_VERSION_1_3` |
| 135 | `VK_KHR_vulkan_memory_model` | Khronos | 2018-09-08 | 3 | 66 | live | `VK_VERSION_1_2` |
| 136 | `VK_NVX_raytracing` | Vendor | 2018-09-15 | — | — | withdrawn | — |
| 137 | `VK_NV_compute_shader_derivatives` | Vendor | 2018-09-15 | 1 | 62 | live | `VK_KHR_compute_shader_derivatives` |
| 138 | `VK_NV_corner_sampled_image` | Vendor | 2018-09-15 | 2 | 96 | live | — |
| 139 | `VK_NV_fragment_shader_barycentric` | Vendor | 2018-09-15 | 1 | 122 | live | `VK_KHR_fragment_shader_barycentric` |
| 140 | `VK_NV_mesh_shader` | Vendor | 2018-09-15 | 1 | 146 | live | — |
| 141 | `VK_NV_representative_fragment_test` | Vendor | 2018-09-15 | 2 | 100 | live | — |
| 142 | `VK_NV_scissor_exclusive` | Vendor | 2018-09-15 | 2 | 57 | live | — |
| 143 | `VK_NV_shader_image_footprint` | Vendor | 2018-09-15 | 2 | 217 | live | — |
| 144 | `VK_NV_shading_rate_image` | Vendor | 2018-09-15 | 3 | 144 | live | — |
| 145 | `VK_KHR_driver_properties` | Khronos | 2018-09-29 | 1 | 41 | live | `VK_VERSION_1_2` |
| 146 | `VK_KHR_shader_atomic_int64` | Khronos | 2018-09-29 | 1 | 48 | live | `VK_VERSION_1_2` |
| 147 | `VK_FUCHSIA_imagepipe_surface` | Vendor | 2018-10-07 | 1 | 30 | live | — |
| 148 | `VK_EXT_calibrated_timestamps` | Multi-vendor | 2018-10-13 | 2 | 40 | live | `VK_KHR_calibrated_timestamps` |
| 149 | `VK_EXT_image_drm_format_modifier` | Multi-vendor | 2018-10-13 | 2 | 410 | live | — |
| 150 | `VK_EXT_pci_bus_info` | Multi-vendor | 2018-10-13 | 2 | 40 | live | — |
| 151 | `VK_EXT_transform_feedback` | Multi-vendor | 2018-10-13 | 1 | 99 | live | — |
| 152 | `VK_GOOGLE_decorate_string` | Vendor | 2018-10-13 | 1 | 27 | live | — |
| 153 | `VK_GOOGLE_hlsl_functionality1` | Vendor | 2018-10-13 | — | 27 | live | — |
| 154 | `VK_AMD_memory_overallocation_behavior` | Vendor | 2018-11-03 | 1 | 32 | live | — |
| 155 | `VK_NV_ray_tracing` | Vendor | 2018-11-03 | 3 | 116 | live, deprecated | — |
| 156 | `VK_EXT_scalar_block_layout` | Multi-vendor | 2018-11-18 | 1 | 46 | live | `VK_VERSION_1_2` |
| 157 | `VK_EXT_separate_stencil_usage` | Multi-vendor | 2018-11-18 | 1 | 34 | live | `VK_VERSION_1_2` |
| 158 | `VK_EXT_fragment_density_map` | Multi-vendor | 2018-11-25 | 3 | 177 | live | — |
| 159 | `VK_KHR_swapchain_mutable_format` | Khronos | 2018-11-25 | 1 | 63 | live | — |
| 160 | `VK_KHR_shader_float16_int8` | Khronos | 2018-12-03 | 1 | 61 | live | `VK_VERSION_1_2` |
| 161 | `VK_KHR_shader_float_controls` | Khronos | 2018-12-03 | 4 | 132 | live | `VK_VERSION_1_2` |
| 162 | `VK_EXT_buffer_device_address` | Multi-vendor | 2019-01-05 | 2 | 62 | live, deprecated | — |
| 163 | `VK_EXT_memory_budget` | Multi-vendor | 2019-01-05 | 1 | 48 | live | — |
| 164 | `VK_EXT_memory_priority` | Multi-vendor | 2019-01-05 | 1 | 32 | live | — |
| 165 | `VK_EXT_validation_features` | Multi-vendor | 2019-01-05 | 6 | 54 | live, deprecated | — |
| 166 | `VK_KHR_depth_stencil_resolve` | Khronos | 2019-01-05 | 1 | 71 | live | `VK_VERSION_1_2` |
| 167 | `VK_EXT_filter_cubic` | Multi-vendor | 2019-02-04 | 3 | 43 | live | — |
| 168 | `VK_NV_dedicated_allocation_image_aliasing` | Vendor | 2019-02-04 | 1 | 30 | live | — |
| 169 | `VK_EXT_depth_clip_enable` | Multi-vendor | 2019-02-15 | 1 | 35 | live | — |
| 170 | `VK_NV_cooperative_matrix` | Vendor | 2019-02-15 | 1 | 61 | live | — |
| 171 | `VK_EXT_metal_surface` | Multi-vendor | 2019-03-03 | 1 | 28 | live | — |
| 172 | `VK_EXT_ycbcr_image_arrays` | Multi-vendor | 2019-03-03 | 1 | 26 | live | — |
| 173 | `VK_NVX_image_view_handle` | Vendor | 2019-03-03 | 4 | 38 | live | — |
| 174 | `VK_AMD_display_native_hdr` | Vendor | 2019-03-17 | 1 | 45 | live | — |
| 175 | `VK_EXT_full_screen_exclusive` | Multi-vendor | 2019-03-17 | 4 | 117 | live | — |
| 176 | `VK_EXT_host_query_reset` | Multi-vendor | 2019-03-17 | 1 | 35 | live | `VK_VERSION_1_2` |
| 177 | `VK_EXT_pipeline_creation_feedback` | Multi-vendor | 2019-03-17 | 1 | 46 | live | `VK_VERSION_1_3` |
| 178 | `VK_KHR_surface_protected_capabilities` | Khronos | 2019-03-17 | 1 | 44 | live | — |
| 179 | `VK_GGP_frame_token` | Vendor | 2019-03-19 | 1 | 29 | live | — |
| 180 | `VK_GGP_stream_descriptor_surface` | Vendor | 2019-03-19 | 1 | 42 | live | — |
| 181 | `VK_EXT_headless_surface` | Multi-vendor | 2019-04-16 | 1 | 43 | live | — |
| 182 | `VK_KHR_uniform_buffer_standard_layout` | Khronos | 2019-05-13 | 1 | 41 | live | `VK_VERSION_1_2` |
| 183 | `VK_NV_coverage_reduction_mode` | Vendor | 2019-05-13 | 1 | 51 | live | — |
| 184 | `VK_INTEL_shader_integer_functions2` | Vendor | 2019-05-22 | 1 | 42 | live | — |
| 185 | `VK_INTEL_performance_query` | Vendor | 2019-05-24 | 2 | 174 | live | — |
| 186 | `VK_EXT_fragment_shader_interlock` | Multi-vendor | 2019-06-02 | 1 | 61 | live | — |
| 187 | `VK_NV_shader_sm_builtins` | Vendor | 2019-06-02 | 1 | 65 | live | — |
| 188 | `VK_EXT_shader_demote_to_helper_invocation` | Multi-vendor | 2019-06-29 | 1 | 51 | live | `VK_VERSION_1_3` |
| 189 | `VK_EXT_texel_buffer_alignment` | Multi-vendor | 2019-06-29 | 1 | 41 | live | `VK_VERSION_1_3` |
| 190 | `VK_KHR_imageless_framebuffer` | Khronos | 2019-07-07 | 1 | 39 | live | `VK_VERSION_1_2` |
| 191 | `VK_EXT_subgroup_size_control` | Multi-vendor | 2019-07-20 | 2 | 89 | live | `VK_VERSION_1_3` |
| 192 | `VK_EXT_index_type_uint8` | Multi-vendor | 2019-07-28 | 1 | 33 | live | `VK_KHR_index_type_uint8` |
| 193 | `VK_EXT_line_rasterization` | Multi-vendor | 2019-07-28 | 1 | 49 | live | `VK_KHR_line_rasterization` |
| 194 | `VK_EXT_texture_compression_astc_hdr` | Multi-vendor | 2019-07-28 | 1 | 70 | live | `VK_VERSION_1_3` |
| 195 | `VK_AMD_pipeline_compiler_control` | Vendor | 2019-08-11 | 1 | 38 | live | — |
| 196 | `VK_AMD_shader_core_properties2` | Vendor | 2019-08-11 | 1 | 32 | live | — |
| 197 | `VK_KHR_pipeline_executable_properties` | Khronos | 2019-08-11 | 1 | 57 | live | — |
| 198 | `VK_AMD_device_coherent_memory` | Vendor | 2019-08-25 | 1 | 33 | live | — |
| 199 | `VK_GOOGLE_user_type` | Vendor | 2019-09-15 | 1 | 27 | live | — |
| 200 | `VK_KHR_shader_subgroup_extended_types` | Khronos | 2019-09-15 | 1 | 44 | live | `VK_VERSION_1_2` |
| 201 | `VK_KHR_shader_clock` | Khronos | 2019-10-06 | 1 | 43 | live | — |
| 202 | `VK_KHR_timeline_semaphore` | Khronos | 2019-10-06 | 2 | 149 | live | `VK_VERSION_1_2` |
| 203 | `VK_KHR_spirv_1_4` | Khronos | 2019-10-13 | 1 | 118 | live | `VK_VERSION_1_2` |
| 204 | `VK_KHR_separate_depth_stencil_layouts` | Khronos | 2019-11-03 | 1 | 39 | live | `VK_VERSION_1_2` |
| 205 | `VK_KHR_performance_query` | Khronos | 2019-11-17 | 1 | 325 | live | — |
| 206 | `VK_KHR_buffer_device_address` | Khronos | 2019-11-24 | 1 | 106 | live | `VK_VERSION_1_2` |
| 207 | `VK_EXT_tooling_info` | Multi-vendor | 2019-12-07 | 1 | 92 | live | `VK_VERSION_1_3` |
| 208 | `VK_KHR_shader_non_semantic_info` | Khronos | 2020-02-15 | 1 | 33 | live | `VK_VERSION_1_3` |
| 209 | `VK_QCOM_render_pass_transform` | Vendor | 2020-03-06 | 5 | 192 | live | — |
| 210 | `VK_EXT_pipeline_creation_cache_control` | Multi-vendor | 2020-03-17 | 3 | 120 | live | `VK_VERSION_1_3` |
| 211 | `VK_KHR_deferred_host_operations` | Khronos | 2020-03-17 | 4 | 189 | live | — |
| 212 | `VK_KHR_pipeline_library` | Khronos | 2020-03-17 | 1 | 30 | live | — |
| 213 | `VK_KHR_ray_tracing` | Khronos | 2020-03-17 | — | — | withdrawn | — |
| 214 | `VK_NV_device_diagnostics_config` | Vendor | 2020-03-17 | 2 | 33 | live | — |
| 215 | `VK_NV_device_generated_commands` | Vendor | 2020-03-17 | 3 | 326 | live | — |
| 216 | `VK_QCOM_render_pass_store_ops` | Vendor | 2020-04-06 | 2 | 49 | live | — |
| 217 | `VK_EXT_robustness2` | Multi-vendor | 2020-04-26 | 1 | 69 | live | `VK_KHR_robustness2` |
| 218 | `VK_QCOM_render_pass_shader_resolve` | Vendor | 2020-04-26 | 4 | 92 | live | `VK_EXT_custom_resolve` |
| 219 | `VK_EXT_custom_border_color` | Multi-vendor | 2020-05-03 | 12 | 135 | live | — |
| 220 | `VK_EXT_private_data` | Multi-vendor | 2020-05-03 | 1 | 71 | live | `VK_VERSION_1_3` |
| 221 | `VK_EXT_extended_dynamic_state` | Multi-vendor | 2020-06-20 | 1 | 60 | live | `VK_VERSION_1_3` |
| 222 | `VK_EXT_directfb_surface` | Multi-vendor | 2020-06-28 | 1 | 29 | live | — |
| 223 | `VK_EXT_fragment_density_map2` | Multi-vendor | 2020-07-03 | 1 | 96 | live | — |
| 224 | `VK_EXT_image_robustness` | Multi-vendor | 2020-07-19 | 1 | 60 | live | `VK_VERSION_1_3` |
| 225 | `VK_EXT_shader_atomic_float` | Multi-vendor | 2020-07-19 | 1 | 42 | live | — |
| 226 | `VK_EXT_4444_formats` | Multi-vendor | 2020-08-03 | 1 | 46 | live | `VK_VERSION_1_3` |
| 227 | `VK_KHR_copy_commands2` | Khronos | 2020-09-20 | 1 | 48 | live | `VK_VERSION_1_3` |
| 228 | `VK_KHR_portability_subset` | Khronos | 2020-09-20 | 1 | 65 | live, provisional | — |
| 229 | `VK_EXT_shader_image_atomic_int64` | Multi-vendor | 2020-09-27 | 1 | 43 | live | — |
| 230 | `VK_EXT_device_memory_report` | Multi-vendor | 2020-10-04 | 2 | 162 | live | — |
| 231 | `VK_KHR_fragment_shading_rate` | Khronos | 2020-10-18 | 2 | 66 | live | — |
| 232 | `VK_KHR_shader_terminate_invocation` | Khronos | 2020-10-18 | 1 | 51 | live | `VK_VERSION_1_3` |
| 233 | `VK_QCOM_rotated_copy_commands` | Vendor | 2020-11-01 | 2 | 65 | live | — |
| 234 | `VK_NV_fragment_shading_rate_enums` | Vendor | 2020-11-08 | 1 | 100 | live | — |
| 235 | `VK_KHR_acceleration_structure` | Khronos | 2020-11-22 | 13 | 547 | live | — |
| 236 | `VK_KHR_ray_query` | Khronos | 2020-11-22 | 1 | 137 | live | — |
| 237 | `VK_KHR_ray_tracing_pipeline` | Khronos | 2020-11-22 | 1 | 393 | live | — |
| 238 | `VK_NV_acquire_winrt_display` | Vendor | 2020-12-07 | 1 | 128 | live | — |
| 239 | `VK_VALVE_mutable_descriptor_type` | Vendor | 2020-12-07 | 1 | 45 | live | `VK_EXT_mutable_descriptor_type` |
| 240 | `VK_KHR_workgroup_memory_explicit_layout` | Khronos | 2021-01-24 | 1 | 54 | live | — |
| 241 | `VK_KHR_zero_initialize_workgroup_memory` | Khronos | 2021-01-24 | 1 | 41 | live | `VK_VERSION_1_3` |
| 242 | `VK_KHR_synchronization2` | Khronos | 2021-02-14 | 1 | 101 | live | `VK_VERSION_1_3` |
| 243 | `VK_QNX_screen_surface` | Vendor | 2021-02-24 | 1 | 29 | live | — |
| 244 | `VK_FUCHSIA_external_memory` | Vendor | 2021-03-21 | 1 | 37 | live | — |
| 245 | `VK_FUCHSIA_external_semaphore` | Vendor | 2021-03-21 | 1 | 43 | live | — |
| 246 | `VK_EXT_color_write_enable` | Multi-vendor | 2021-04-13 | 1 | 39 | live | — |
| 247 | `VK_EXT_vertex_input_dynamic_state` | Multi-vendor | 2021-04-13 | 2 | 40 | live | — |
| 248 | `VK_EXT_video_decode_h264` | Multi-vendor | 2021-04-13 | — | — | withdrawn | — |
| 249 | `VK_EXT_video_decode_h265` | Multi-vendor | 2021-04-13 | — | — | withdrawn | — |
| 250 | `VK_EXT_video_encode_h264` | Multi-vendor | 2021-04-13 | — | — | withdrawn | — |
| 251 | `VK_EXT_ycbcr_2plane_444_formats` | Multi-vendor | 2021-04-13 | 1 | 38 | live | `VK_VERSION_1_3` |
| 252 | `VK_KHR_video_decode_queue` | Khronos | 2021-04-13 | 8 | 70 | live | — |
| 253 | `VK_KHR_video_encode_queue` | Khronos | 2021-04-13 | 12 | 127 | live | — |
| 254 | `VK_KHR_video_queue` | Khronos | 2021-04-13 | 8 | 102 | live | — |
| 255 | `VK_NV_inherited_viewport_scissor` | Vendor | 2021-04-13 | 1 | 90 | live | — |
| 256 | `VK_EXT_extended_dynamic_state2` | Multi-vendor | 2021-04-18 | 1 | 40 | live | `VK_VERSION_1_3` |
| 257 | `VK_EXT_provoking_vertex` | Multi-vendor | 2021-04-25 | 1 | 85 | live | — |
| 258 | `VK_NVX_binary_import` | Vendor | 2021-05-10 | 2 | 159 | live | — |
| 259 | `VK_EXT_global_priority_query` | Multi-vendor | 2021-06-06 | 1 | 53 | live | `VK_KHR_global_priority` |
| 260 | `VK_KHR_shader_subgroup_uniform_control_flow` | Khronos | 2021-06-06 | 1 | 39 | live | — |
| 261 | `VK_EXT_acquire_drm_display` | Multi-vendor | 2021-06-17 | 1 | 32 | live | — |
| 262 | `VK_EXT_physical_device_drm` | Multi-vendor | 2021-06-17 | 1 | 48 | live | — |
| 263 | `VK_EXT_multi_draw` | Multi-vendor | 2021-06-19 | 1 | 46 | live | — |
| 264 | `VK_HUAWEI_subpass_shading` | Vendor | 2021-06-19 | 3 | 264 | live | — |
| 265 | `VK_NV_ray_tracing_motion_blur` | Vendor | 2021-06-19 | 1 | 60 | live | — |
| 266 | `VK_NV_external_memory_rdma` | Vendor | 2021-07-05 | 1 | 97 | live | — |
| 267 | `VK_EXT_shader_atomic_float2` | Multi-vendor | 2021-07-20 | 1 | 61 | live | — |
| 268 | `VK_HUAWEI_invocation_mask` | Vendor | 2021-07-20 | 1 | 75 | live | — |
| 269 | `VK_KHR_present_id` | Khronos | 2021-07-20 | 1 | 37 | live | — |
| 270 | `VK_KHR_present_wait` | Khronos | 2021-07-20 | 1 | 82 | live | — |
| 271 | `VK_EXT_load_store_op_none` | Multi-vendor | 2021-08-10 | 1 | 52 | live | `VK_KHR_load_store_op_none` |
| 272 | `VK_EXT_primitive_topology_list_restart` | Multi-vendor | 2021-08-29 | 1 | 33 | live | — |
| 273 | `VK_KHR_shader_integer_dot_product` | Khronos | 2021-08-29 | 1 | 64 | live | `VK_VERSION_1_3` |
| 274 | `VK_EXT_pageable_device_local_memory` | Multi-vendor | 2021-09-06 | 1 | 74 | live | — |
| 275 | `VK_FUCHSIA_buffer_collection` | Vendor | 2021-09-28 | 2 | 63 | live | — |
| 276 | `VK_EXT_rgba10x6_formats` | Multi-vendor | 2021-10-05 | 1 | 48 | live | — |
| 277 | `VK_KHR_format_feature_flags2` | Khronos | 2021-10-05 | 2 | 79 | live | `VK_VERSION_1_3` |
| 278 | `VK_KHR_maintenance4` | Khronos | 2021-10-05 | 2 | 77 | live | `VK_VERSION_1_3` |
| 279 | `VK_EXT_border_color_swizzle` | Multi-vendor | 2021-10-13 | 1 | 46 | live | — |
| 280 | `VK_EXT_video_encode_h265` | Multi-vendor | 2021-10-13 | — | — | withdrawn | — |
| 281 | `VK_KHR_dynamic_rendering` | Khronos | 2021-11-02 | 1 | 52 | live | `VK_VERSION_1_3` |
| 282 | `VK_EXT_image_view_min_lod` | Multi-vendor | 2021-11-16 | 1 | 40 | live | — |
| 283 | `VK_ARM_rasterization_order_attachment_access` | Vendor | 2021-11-23 | 1 | 46 | live | `VK_EXT_rasterization_order_attachment_access` |
| 284 | `VK_EXT_depth_clip_control` | Multi-vendor | 2021-11-23 | 1 | 65 | live | — |
| 285 | `VK_GOOGLE_surfaceless_query` | Vendor | 2021-12-20 | 2 | 42 | live | — |
| 286 | `VK_NV_linear_color_attachment` | Vendor | 2021-12-20 | 1 | 43 | live | — |
| 287 | `VK_QCOM_fragment_density_map_offset` | Vendor | 2021-12-20 | 3 | 108 | live | `VK_EXT_fragment_density_map_offset` |
| 288 | `VK_KHR_global_priority` | Khronos | 2022-01-21 | 1 | 85 | live | `VK_VERSION_1_4` |
| 289 | `VK_VALVE_descriptor_set_host_mapping` | Vendor | 2022-03-08 | 1 | 105 | live | — |
| 290 | `VK_KHR_portability_enumeration` | Khronos | 2022-03-15 | 1 | 39 | live | — |
| 291 | `VK_EXT_graphics_pipeline_library` | Multi-vendor | 2022-03-29 | 1 | 41 | live | — |
| 292 | `VK_EXT_primitives_generated_query` | Multi-vendor | 2022-03-29 | 1 | 78 | live | — |
| 293 | `VK_EXT_image_2d_view_of_3d` | Multi-vendor | 2022-04-05 | 1 | 37 | live | — |
| 294 | `VK_EXT_image_compression_control` | Multi-vendor | 2022-05-10 | 1 | 41 | live | — |
| 295 | `VK_EXT_image_compression_control_swapchain` | Multi-vendor | 2022-05-10 | 1 | 32 | live | — |
| 296 | `VK_EXT_pipeline_properties` | Multi-vendor | 2022-05-10 | 1 | 81 | live | — |
| 297 | `VK_EXT_subpass_merge_feedback` | Multi-vendor | 2022-05-10 | 2 | 33 | live | — |
| 298 | `VK_KHR_ray_tracing_maintenance1` | Khronos | 2022-05-10 | 1 | 83 | live | — |
| 299 | `VK_AMD_shader_early_and_late_fragment_tests` | Vendor | 2022-05-17 | 1 | 35 | live | — |
| 300 | `VK_KHR_fragment_shader_barycentric` | Khronos | 2022-05-24 | 1 | 92 | live | — |
| 301 | `VK_EXT_metal_objects` | Multi-vendor | 2022-06-09 | 2 | 52 | live | — |
| 302 | `VK_EXT_non_seamless_cube_map` | Multi-vendor | 2022-06-09 | 1 | 30 | live | — |
| 303 | `VK_EXT_multisampled_render_to_single_sampled` | Multi-vendor | 2022-06-30 | 1 | 87 | live | — |
| 304 | `VK_EXT_shader_module_identifier` | Multi-vendor | 2022-06-30 | 1 | 57 | live | — |
| 305 | `VK_EXT_pipeline_robustness` | Multi-vendor | 2022-07-14 | 1 | 47 | live | `VK_VERSION_1_4` |
| 306 | `VK_QCOM_image_processing` | Vendor | 2022-07-21 | 1 | 69 | live | — |
| 307 | `VK_QCOM_tile_properties` | Vendor | 2022-07-21 | 1 | 29 | live | — |
| 308 | `VK_EXT_attachment_feedback_loop_layout` | Multi-vendor | 2022-08-04 | 2 | 38 | live | — |
| 309 | `VK_SEC_amigo_profiling` | Vendor | 2022-08-04 | 1 | 77 | live | — |
| 310 | `VK_EXT_rasterization_order_attachment_access` | Multi-vendor | 2022-08-18 | 1 | 34 | live | — |
| 311 | `VK_EXT_depth_clamp_zero_one` | Multi-vendor | 2022-09-01 | 1 | 36 | live | `VK_KHR_depth_clamp_zero_one` |
| 312 | `VK_EXT_mesh_shader` | Multi-vendor | 2022-09-01 | 1 | 92 | live | — |
| 313 | `VK_EXT_legacy_dithering` | Multi-vendor | 2022-09-08 | 2 | 47 | live | — |
| 314 | `VK_EXT_mutable_descriptor_type` | Multi-vendor | 2022-09-15 | 1 | 45 | live | — |
| 315 | `VK_EXT_device_address_binding_report` | Multi-vendor | 2022-09-28 | 1 | 137 | live | — |
| 316 | `VK_EXT_device_fault` | Multi-vendor | 2022-09-28 | 2 | 44 | live | `VK_KHR_device_fault` |
| 317 | `VK_EXT_extended_dynamic_state3` | Multi-vendor | 2022-09-28 | 2 | 49 | live | — |
| 318 | `VK_EXT_opacity_micromap` | Multi-vendor | 2022-09-28 | 2 | 199 | live | `VK_KHR_opacity_micromap` |
| 319 | `VK_EXT_pipeline_protected_access` | Multi-vendor | 2022-09-28 | 1 | 37 | live | `VK_VERSION_1_4` |
| 320 | `VK_NV_optical_flow` | Vendor | 2022-09-28 | 1 | 115 | live | — |
| 321 | `VK_NV_present_barrier` | Vendor | 2022-09-28 | 1 | 50 | live | — |
| 322 | `VK_ARM_shader_core_builtins` | Vendor | 2022-10-13 | 2 | 59 | live | — |
| 323 | `VK_NV_copy_memory_indirect` | Vendor | 2022-11-03 | 1 | 31 | live | `VK_KHR_copy_memory_indirect` |
| 324 | `VK_NV_memory_decompression` | Vendor | 2022-11-03 | 1 | 27 | live | `VK_EXT_memory_decompression` |
| 325 | `VK_NV_ray_tracing_invocation_reorder` | Vendor | 2022-11-03 | 1 | 180 | live | `VK_EXT_ray_tracing_invocation_reorder` |
| 326 | `VK_EXT_descriptor_buffer` | Multi-vendor | 2022-11-17 | 1 | 51 | live, deprecated | — |
| 327 | `VK_LUNARG_direct_driver_loading` | Vendor | 2022-12-01 | 1 | 27 | live | — |
| 328 | `VK_QCOM_multiview_per_view_viewports` | Vendor | 2022-12-01 | 1 | 61 | live | — |
| 329 | `VK_EXT_surface_maintenance1` | Multi-vendor | 2022-12-08 | 1 | 53 | live | `VK_KHR_surface_maintenance1` |
| 330 | `VK_EXT_swapchain_maintenance1` | Multi-vendor | 2022-12-08 | 1 | 68 | live | `VK_KHR_swapchain_maintenance1` |
| 331 | `VK_KHR_video_decode_h264` | Khronos | 2022-12-18 | 9 | 79 | live | — |
| 332 | `VK_KHR_video_decode_h265` | Khronos | 2022-12-18 | 8 | 69 | live | — |
| 333 | `VK_HUAWEI_cluster_culling_shader` | Vendor | 2023-01-19 | 3 | 254 | live | — |
| 334 | `VK_EXT_pipeline_library_group_handles` | Multi-vendor | 2023-01-26 | 1 | 58 | live | `VK_KHR_pipeline_library_group_handles` |
| 335 | `VK_ARM_shader_core_properties` | Vendor | 2023-02-16 | 1 | 32 | live | — |
| 336 | `VK_EXT_application_parameters` | Multi-vendor | 2023-02-16 | 1 | 74 | live | — |
| 337 | `VK_EXT_image_sliced_view_of_3d` | Multi-vendor | 2023-02-16 | 1 | 33 | live | — |
| 338 | `VK_KHR_object_refresh` | Khronos | 2023-02-16 | 1 | 77 | live | — |
| 339 | `VK_NV_external_memory_sci_buf` | Vendor | 2023-02-16 | 2 | 74 | live | — |
| 340 | `VK_NV_external_sci_sync` | Vendor | 2023-02-16 | 2 | 81 | live, deprecated | — |
| 341 | `VK_NV_external_sci_sync2` | Vendor | 2023-02-16 | 1 | 121 | live | — |
| 342 | `VK_NV_private_vendor_info` | Vendor | 2023-02-16 | 2 | 36 | live | — |
| 343 | `VK_QCOM_multiview_per_view_render_areas` | Vendor | 2023-02-16 | 1 | 92 | live | — |
| 344 | `VK_NV_low_latency` | Vendor | 2023-02-26 | 2 | 126 | live, deprecated | — |
| 345 | `VK_KHR_map_memory2` | Khronos | 2023-03-17 | 1 | 39 | live | `VK_VERSION_1_4` |
| 346 | `VK_NV_displacement_micromap` | Vendor | 2023-03-24 | 2 | 57 | live, deprecated, provisional | — |
| 347 | `VK_EXT_shader_object` | Multi-vendor | 2023-03-31 | 1 | 353 | live | — |
| 348 | `VK_EXT_shader_tile_image` | Multi-vendor | 2023-03-31 | 1 | 79 | live | — |
| 349 | `VK_KHR_ray_tracing_position_fetch` | Khronos | 2023-04-27 | 1 | 60 | live | — |
| 350 | `VK_EXT_attachment_feedback_loop_dynamic_state` | Multi-vendor | 2023-05-04 | 1 | 30 | live | — |
| 351 | `VK_EXT_dynamic_rendering_unused_attachments` | Multi-vendor | 2023-05-28 | 1 | 40 | live | — |
| 352 | `VK_EXT_external_memory_acquire_unmodified` | Multi-vendor | 2023-06-02 | 1 | 31 | live | — |
| 353 | `VK_QNX_external_memory_screen_buffer` | Vendor | 2023-06-15 | 1 | 41 | live | — |
| 354 | `VK_EXT_depth_bias_control` | Multi-vendor | 2023-06-16 | 1 | 41 | live | — |
| 355 | `VK_KHR_cooperative_matrix` | Khronos | 2023-06-23 | 2 | 58 | live | — |
| 356 | `VK_MSFT_layered_driver` | Vendor | 2023-07-19 | 1 | 31 | live | — |
| 357 | `VK_EXT_host_image_copy` | Multi-vendor | 2023-07-21 | 1 | 108 | live | `VK_VERSION_1_4` |
| 358 | `VK_NV_device_generated_commands_compute` | Vendor | 2023-07-21 | 2 | 35 | live | — |
| 359 | `VK_AMDX_shader_enqueue` | Vendor | 2023-07-28 | 2 | 43 | live, provisional | — |
| 360 | `VK_KHR_maintenance5` | Khronos | 2023-07-28 | 1 | 91 | live | `VK_VERSION_1_4` |
| 361 | `VK_QCOM_filter_cubic_clamp` | Vendor | 2023-08-25 | 1 | 46 | live | — |
| 362 | `VK_QCOM_filter_cubic_weights` | Vendor | 2023-08-25 | 1 | 41 | live | — |
| 363 | `VK_QCOM_image_processing2` | Vendor | 2023-08-25 | 1 | 140 | live | — |
| 364 | `VK_QCOM_ycbcr_degamma` | Vendor | 2023-08-25 | 1 | 88 | live | — |
| 365 | `VK_NV_descriptor_pool_overallocation` | Vendor | 2023-09-02 | 1 | 37 | live | — |
| 366 | `VK_EXT_frame_boundary` | Multi-vendor | 2023-09-08 | 1 | 35 | live | — |
| 367 | `VK_ANDROID_external_format_resolve` | Vendor | 2023-09-29 | 1 | 38 | live | — |
| 368 | `VK_NV_low_latency2` | Vendor | 2023-09-29 | 3 | 60 | live | — |
| 369 | `VK_EXT_nested_command_buffer` | Multi-vendor | 2023-10-06 | 1 | 45 | live | — |
| 370 | `VK_NV_extended_sparse_address_space` | Vendor | 2023-10-06 | 1 | 33 | live | — |
| 371 | `VK_ARM_scheduling_controls` | Vendor | 2023-10-20 | 2 | 45 | live | — |
| 372 | `VK_NV_cuda_kernel_launch` | Vendor | 2023-10-20 | 2 | 66 | live, provisional | — |
| 373 | `VK_IMG_relaxed_line_rasterization` | Vendor | 2023-11-10 | 1 | 38 | live | — |
| 374 | `VK_ARM_render_pass_striped` | Vendor | 2023-12-01 | 1 | 35 | live | — |
| 375 | `VK_EXT_layer_settings` | Multi-vendor | 2023-12-01 | 2 | 113 | live | — |
| 376 | `VK_KHR_calibrated_timestamps` | Khronos | 2023-12-08 | 1 | 31 | live | — |
| 377 | `VK_KHR_vertex_attribute_divisor` | Khronos | 2023-12-08 | 1 | 38 | live | `VK_VERSION_1_4` |
| 378 | `VK_KHR_maintenance6` | Khronos | 2023-12-18 | 1 | 62 | live | `VK_VERSION_1_4` |
| 379 | `VK_KHR_video_encode_h264` | Khronos | 2023-12-18 | 14 | 181 | live | — |
| 380 | `VK_KHR_video_encode_h265` | Khronos | 2023-12-18 | 14 | 169 | live | — |
| 381 | `VK_KHR_video_maintenance1` | Khronos | 2023-12-18 | 1 | 45 | live | — |
| 382 | `VK_NV_per_stage_descriptor_set` | Vendor | 2023-12-18 | 1 | 46 | live, deprecated | — |
| 383 | `VK_KHR_dynamic_rendering_local_read` | Khronos | 2024-01-25 | 1 | 63 | live | `VK_VERSION_1_4` |
| 384 | `VK_KHR_index_type_uint8` | Khronos | 2024-01-25 | 1 | 33 | live | `VK_VERSION_1_4` |
| 385 | `VK_KHR_line_rasterization` | Khronos | 2024-01-25 | 1 | 52 | live | `VK_VERSION_1_4` |
| 386 | `VK_KHR_load_store_op_none` | Khronos | 2024-01-25 | 1 | 41 | live | `VK_VERSION_1_4` |
| 387 | `VK_KHR_shader_expect_assume` | Khronos | 2024-01-25 | 1 | 40 | live | `VK_VERSION_1_4` |
| 388 | `VK_KHR_shader_float_controls2` | Khronos | 2024-01-25 | 1 | 46 | live | `VK_VERSION_1_4` |
| 389 | `VK_KHR_shader_maximal_reconvergence` | Khronos | 2024-01-25 | 1 | 43 | live | — |
| 390 | `VK_KHR_shader_quad_control` | Khronos | 2024-01-25 | 1 | 39 | live | — |
| 391 | `VK_KHR_shader_subgroup_rotate` | Khronos | 2024-01-25 | 2 | 42 | live | `VK_VERSION_1_4` |
| 392 | `VK_KHR_video_decode_av1` | Khronos | 2024-02-01 | 1 | 39 | live | — |
| 393 | `VK_EXT_map_memory_placed` | Multi-vendor | 2024-02-14 | 1 | 32 | live | — |
| 394 | `VK_NV_shader_atomic_float16_vector` | Vendor | 2024-02-16 | 1 | 39 | live | — |
| 395 | `VK_NV_raw_access_chains` | Vendor | 2024-03-01 | 1 | 33 | live | — |
| 396 | `VK_NV_ray_tracing_validation` | Vendor | 2024-03-08 | 1 | 26 | live | — |
| 397 | `VK_EXT_legacy_vertex_attributes` | Multi-vendor | 2024-05-05 | 1 | 47 | live | — |
| 398 | `VK_MESA_image_alignment_control` | Vendor | 2024-05-10 | 1 | 46 | live | — |
| 399 | `VK_EXT_shader_replicated_composites` | Multi-vendor | 2024-05-31 | 1 | 27 | live | — |
| 400 | `VK_KHR_shader_relaxed_extended_instruction` | Khronos | 2024-06-14 | 1 | 33 | live | — |
| 401 | `VK_KHR_maintenance7` | Khronos | 2024-06-28 | 1 | 65 | live | — |
| 402 | `VK_AMD_anti_lag` | Vendor | 2024-07-19 | 1 | 33 | live | — |
| 403 | `VK_NV_command_buffer_inheritance` | Vendor | 2024-08-16 | 1 | 62 | live | — |
| 404 | `VK_KHR_pipeline_binary` | Khronos | 2024-08-23 | 1 | 41 | live | — |
| 405 | `VK_KHR_compute_shader_derivatives` | Khronos | 2024-08-30 | 1 | 71 | live | — |
| 406 | `VK_EXT_depth_clamp_control` | Multi-vendor | 2024-09-26 | 1 | 71 | live | — |
| 407 | `VK_EXT_device_generated_commands` | Multi-vendor | 2024-09-26 | 1 | 143 | live | — |
| 408 | `VK_EXT_present_mode_fifo_latest_ready` | Multi-vendor | 2024-10-04 | 1 | 50 | live | `VK_KHR_present_mode_fifo_latest_ready` |
| 409 | `VK_NV_cooperative_matrix2` | Vendor | 2024-10-25 | 1 | 56 | live | — |
| 410 | `VK_HUAWEI_hdr_vivid` | Vendor | 2024-11-01 | 1 | 34 | live | — |
| 411 | `VK_EXT_vertex_attribute_robustness` | Multi-vendor | 2024-11-20 | 1 | 44 | live | `VK_KHR_maintenance9` |
| 412 | `VK_KHR_video_encode_av1` | Khronos | 2024-11-20 | 1 | 40 | live | — |
| 413 | `VK_KHR_video_encode_quantization_map` | Khronos | 2024-11-20 | 2 | 49 | live | — |
| 414 | `VK_NV_display_stereo` | Vendor | 2024-11-20 | 1 | 34 | live | — |
| 415 | `VK_ARM_pipeline_opacity_micromap` | Vendor | 2025-01-17 | 1 | 56 | live | — |
| 416 | `VK_KHR_depth_clamp_zero_one` | Khronos | 2025-01-17 | 1 | 31 | live | — |
| 417 | `VK_KHR_maintenance8` | Khronos | 2025-01-17 | 1 | 60 | live | — |
| 418 | `VK_EXT_external_memory_metal` | Multi-vendor | 2025-01-24 | 1 | 30 | live | — |
| 419 | `VK_KHR_video_maintenance2` | Khronos | 2025-01-24 | 1 | 48 | live | — |
| 420 | `VK_NV_cluster_acceleration_structure` | Vendor | 2025-01-30 | 4 | 64 | live | — |
| 421 | `VK_NV_cooperative_vector` | Vendor | 2025-01-30 | 4 | 61 | live | — |
| 422 | `VK_NV_partitioned_acceleration_structure` | Vendor | 2025-01-30 | 1 | 38 | live | — |
| 423 | `VK_NV_ray_tracing_linear_swept_spheres` | Vendor | 2025-01-30 | 1 | 59 | live | — |
| 424 | `VK_NV_present_metering` | Vendor | 2025-02-07 | 1 | 33 | live | — |
| 425 | `VK_EXT_fragment_density_map_offset` | Multi-vendor | 2025-03-20 | 1 | 31 | live | — |
| 426 | `VK_KHR_shader_bfloat16` | Khronos | 2025-03-20 | 1 | 42 | live | — |
| 427 | `VK_NV_external_compute_queue` | Vendor | 2025-04-04 | 1 | 87 | live | — |
| 428 | `VK_QCOM_tile_shading` | Vendor | 2025-04-04 | 2 | 118 | live | — |
| 429 | `VK_QCOM_tile_memory_heap` | Vendor | 2025-04-18 | 1 | 57 | live | — |
| 430 | `VK_KHR_robustness2` | Khronos | 2025-05-01 | 1 | 59 | live | — |
| 431 | `VK_EXT_zero_initialize_device_memory` | Multi-vendor | 2025-05-09 | 1 | 51 | live | — |
| 432 | `VK_ARM_format_pack` | Vendor | 2025-05-30 | 1 | 61 | live | — |
| 433 | `VK_ARM_tensors` | Vendor | 2025-06-06 | 2 | 90 | live | — |
| 434 | `VK_EXT_shader_float8` | Multi-vendor | 2025-06-06 | 1 | 45 | live | — |
| 435 | `VK_KHR_maintenance9` | Khronos | 2025-06-06 | 1 | 60 | live | — |
| 436 | `VK_KHR_present_id2` | Khronos | 2025-06-06 | 1 | 39 | live | — |
| 437 | `VK_KHR_present_wait2` | Khronos | 2025-06-06 | 1 | 136 | live | — |
| 438 | `VK_KHR_unified_image_layouts` | Khronos | 2025-06-06 | 1 | 52 | live | — |
| 439 | `VK_KHR_video_decode_vp9` | Khronos | 2025-06-06 | 1 | 38 | live | — |
| 440 | `VK_OHOS_surface` | Vendor | 2025-06-13 | 1 | 34 | live | — |
| 441 | `VK_VALVE_fragment_density_map_layered` | Vendor | 2025-06-13 | 1 | 31 | live | — |
| 442 | `VK_ARM_data_graph` | Vendor | 2025-06-20 | 1 | 79 | live | — |
| 443 | `VK_KHR_present_mode_fifo_latest_ready` | Khronos | 2025-07-04 | 1 | 46 | live | — |
| 444 | `VK_KHR_surface_maintenance1` | Khronos | 2025-07-04 | 1 | 43 | live | — |
| 445 | `VK_KHR_swapchain_maintenance1` | Khronos | 2025-07-04 | 1 | 60 | live | — |
| 446 | `VK_KHR_video_encode_intra_refresh` | Khronos | 2025-07-04 | 1 | 33 | live | — |
| 447 | `VK_SEC_pipeline_cache_incremental_mode` | Vendor | 2025-07-04 | 1 | 61 | live | — |
| 448 | `VK_AMDX_dense_geometry_format` | Vendor | 2025-08-01 | 1 | 37 | live, provisional | — |
| 449 | `VK_KHR_shader_untyped_pointers` | Khronos | 2025-08-08 | 1 | 42 | live | — |
| 450 | `VK_VALVE_video_encode_rgb_conversion` | Vendor | 2025-09-19 | 1 | 28 | live | — |
| 451 | `VK_KHR_copy_memory_indirect` | Khronos | 2025-09-25 | 1 | 38 | live | — |
| 452 | `VK_KHR_shader_fma` | Khronos | 2025-10-10 | 1 | 38 | live | — |
| 453 | `VK_EXT_memory_decompression` | Multi-vendor | 2025-10-24 | 1 | 46 | live | — |
| 454 | `VK_EXT_shader_64bit_indexing` | Multi-vendor | 2025-10-24 | 1 | 33 | live | — |
| 455 | `VK_EXT_shader_uniform_buffer_unsized_array` | Multi-vendor | 2025-10-24 | 1 | 52 | live | — |
| 456 | `VK_KHR_maintenance10` | Khronos | 2025-10-24 | 1 | 55 | live | — |
| 457 | `VK_OHOS_native_buffer` | Vendor | 2025-10-24 | 1 | 31 | withdrawn | — |
| 458 | `VK_ARM_performance_counters_by_region` | Vendor | 2025-10-30 | 1 | 65 | live | — |
| 459 | `VK_OHOS_external_memory` | Vendor | 2025-10-30 | 1 | 34 | live | — |
| 460 | `VK_QCOM_data_graph_model` | Vendor | 2025-11-07 | 1 | 36 | live | — |
| 461 | `VK_EXT_custom_resolve` | Multi-vendor | 2025-11-14 | 1 | 55 | live | — |
| 462 | `VK_EXT_ray_tracing_invocation_reorder` | Multi-vendor | 2025-11-14 | 2 | 51 | live | — |
| 463 | `VK_EXT_present_timing` | Multi-vendor | 2025-11-26 | 3 | 235 | live | — |
| 464 | `VK_NV_compute_occupancy_priority` | Vendor | 2025-12-12 | 1 | 92 | live | — |
| 465 | `VK_EXT_shader_long_vector` | Multi-vendor | 2025-12-18 | 1 | 42 | live | — |
| 466 | `VK_EXT_texture_compression_astc_3d` | Multi-vendor | 2025-12-18 | 1 | 35 | live | — |
| 467 | `VK_EXT_descriptor_heap` | Multi-vendor | 2026-01-22 | 1 | 103 | live | — |
| 468 | `VK_EXT_shader_subgroup_partitioned` | Multi-vendor | 2026-01-22 | 1 | 40 | live | — |
| 469 | `VK_KHR_internally_synchronized_queues` | Khronos | 2026-01-22 | 1 | 34 | live | — |
| 470 | `VK_NV_push_constant_bank` | Vendor | 2026-01-22 | 1 | 81 | live | — |
| 471 | `VK_QCOM_cooperative_matrix_conversion` | Vendor | 2026-01-30 | 1 | 42 | live | — |
| 472 | `VK_SEC_ubm_surface` | Vendor | 2026-02-06 | 1 | 49 | live | — |
| 473 | `VK_VALVE_shader_mixed_float_dot_product` | Vendor | 2026-02-19 | 1 | 36 | live | — |
| 474 | `VK_ARM_shader_instrumentation` | Vendor | 2026-03-05 | 1 | 31 | live | — |
| 475 | `VK_KHR_device_address_commands` | Khronos | 2026-03-13 | 1 | 54 | live | — |
| 476 | `VK_KHR_device_fault` | Khronos | 2026-03-20 | 1 | 67 | live | — |
| 477 | `VK_KHR_shader_abort` | Khronos | 2026-03-20 | 1 | 32 | live | — |
| 478 | `VK_KHR_shader_constant_data` | Khronos | 2026-03-20 | 1 | 35 | live | — |
| 479 | `VK_ARM_data_graph_instruction_set_tosa` | Vendor | 2026-04-03 | 1 | 40 | live | — |
| 480 | `VK_EXT_primitive_restart_index` | Multi-vendor | 2026-04-03 | 1 | 29 | live | — |
| 481 | `VK_QCOM_queue_perf_hint` | Vendor | 2026-04-03 | 1 | 36 | live | — |
| 482 | `VK_ARM_data_graph_optical_flow` | Vendor | 2026-04-10 | 1 | 29 | live | — |
| 483 | `VK_ARM_data_graph_neural_accelerator_statistics` | Vendor | 2026-05-01 | 1 | 37 | live | — |
| 484 | `VK_KHR_maintenance11` | Khronos | 2026-05-01 | 1 | 65 | live | — |
| 485 | `VK_SEC_throttle_hint` | Vendor | 2026-05-01 | 1 | 92 | live | — |
| 486 | `VK_AMD_gpa_interface` | Vendor | 2026-05-08 | 1 | 31 | live | — |
| 487 | `VK_EXT_shader_split_barrier` | Multi-vendor | 2026-05-08 | 1 | 44 | live | — |
| 488 | `VK_KHR_opacity_micromap` | Khronos | 2026-05-08 | 1 | 257 | live | — |
| 489 | `VK_QCOM_elapsed_timer_query` | Vendor | 2026-05-08 | 1 | 57 | live | — |
| 490 | `VK_QCOM_image_processing3` | Vendor | 2026-05-08 | 1 | 69 | live | — |
| 491 | `VK_QCOM_shader_multiple_wait_queues` | Vendor | 2026-05-08 | 1 | 35 | live | — |
| 492 | `VK_NV_cooperative_matrix_decode_vector` | Vendor | 2026-05-15 | 1 | 43 | live | — |
| 493 | `VK_EXT_multisampled_render_to_swapchain` | Multi-vendor | 2026-06-05 | 1 | 30 | live | — |
| 494 | `VK_KHR_extended_flags` | Khronos | 2026-06-05 | 1 | 77 | live | — |
| 495 | `VK_KHR_video_encode_feedback2` | Khronos | 2026-06-05 | 1 | 36 | live | — |
| 496 | `VK_IMG_filter_linear_2d` | Vendor | 2026-06-12 | 1 | 34 | live | — |
| 497 | `VK_ARM_tensor_controls` | Vendor | 2026-06-26 | 1 | 41 | live | — |
| 498 | `VK_EXT_shader_ocp_microscaling_types` | Multi-vendor | 2026-07-03 | 1 | 60 | live | — |
| 499 | `VK_EXT_image_tiling_control` | Multi-vendor | 2026-07-31 | 1 | 50 | live | — |
| 500 | `VK_EXT_cooperative_matrix_maintenance1` | Multi-vendor | 2026-08-07 | 1 | 59 | live | — |
| 501 | `VK_NV_private_data_base_handle` | Vendor | 2026-08-28 | 1 | 43 | live | — |
| 502 | `VK_KHR_pipeline_library_group_handles` | Khronos | 2026-09-04 | 1 | 52 | live | — |
| 503 | `VK_VALVE_buffer_device_address_allocation_alignment` | Vendor | 2026-09-04 | 1 | 40 | live | — |
| 504 | `VK_INTEL_device_info` | Vendor | 2026-09-18 | 1 | 77 | live | — |

*504 extensions. Generated 2026-09-21.*
