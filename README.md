# Veeam-One-VRO-Scoping-Guide
Veeam ONE & Recovery Orchestrator Scoping Guide

A browser-based scoping tool that turns a short set of environment answers into a statement of work draft for a Veeam ONE or Veeam Recovery Orchestrator deployment. It produces a task-by-task effort estimate with hour ranges, a prerequisites list, and an assumptions and exclusions section, all written out as prose you can put in front of a client.

please visit https://m365admintools.com for more information and IT engineering tools.

One HTML file. No installation, no server, no sign-up, no internet connection required. Nothing you type leaves the browser.

Built for consultants and MSPs who quote this work often enough to want a consistent starting point, and who would rather adjust a draft than write the same SOW from scratch every time.

<!-- Add a screenshot of the tool with the report pane here, then uncomment:
![Scoping guide](docs/images/scoping-guide.png)
-->

<!-- Add a screenshot of the exported scoping summary here, then uncomment:
![Exported summary](docs/images/exported-summary.png)
-->

## What it produces

The output is a scoping summary document, not a number. It contains:

1. **Engagement summary.** Products in scope and the environment the work applies to.
2. **Environment profile.** Infrastructure, workload, and the platform decisions that drive the estimate.
3. **Scope of work per product.** Every task with a description written in client-facing language, the requirements attached to it, an hour range, and an optional cost range.
4. **Effort summary.** Hours and cost per product, with a total.
5. **Prerequisites and client responsibilities.** Generated from the choices made, so it lists what this specific engagement needs rather than a generic checklist.
6. **Assumptions and exclusions.** Including the boundaries most often argued about after the fact: VBR remediation, extra recovery plans, extra reports, live failover, and training.

Each task description changes with the inputs. Choosing an existing SQL instance rather than SQL Express, for example, rewrites the install task text and adds a client DBA responsibility to the prerequisites.

## Quick start

1. Download `Veeam-One-VRO-Scoping-Guide.html` from this repository.
2. Open it in any modern browser by double-clicking it.
3. Enter the customer name and your name in the top bar.
4. Select which products are in scope. Either, or both.
5. Fill in the environment profile and the scope decisions.
6. The document on the right rewrites itself as you type.
7. Click **Export HTML** for a self-contained file, or **Print / PDF** for a PDF.

There is nothing to install. The file can be opened from a USB drive, an email attachment, or a network share.

## Inputs

**Products in scope**

Veeam ONE, Veeam Recovery Orchestrator, or both. Deselecting one removes its section, its tasks, its prerequisites, and its exclusions from the document.

**Environment profile**

VBR servers, sites, Hyper-V hosts, ESXi hosts, protected VMs, and backup jobs. These appear in the environment summary and support the complexity rating. They do not change the hour arithmetic on their own.

**Common scope decisions**

| Decision | Options | Effect |
|---|---|---|
| Server provisioning | Client provides, or consultant builds | Adds a server build task per product and rewrites the install description and the prerequisites |
| SQL platform | New SQL Express, or existing instance | Rewrites the install description and swaps the SQL prerequisite |
| Site complexity | Simple, Moderate, Complex | Multiplies configuration hours by 1.0, 1.25, or 1.5. Install hours are not affected |

**Veeam ONE scope**

Scheduled report count, custom alarm tuning, business views, and editable hour ranges for install, configure, and validate.

**Veeam Recovery Orchestrator scope**

Recovery plans to build, plans to test, custom pre and post scripting, and editable hour ranges for install, initial configuration, per-plan build, and per-plan test.

**Rate**

An optional hourly rate. Leave it at 0 and every cost column disappears from the document, which is the right setting when the estimate goes to a partner or internal reviewer rather than to the client.

## Default hour ranges

Defaults are a starting point from real deployments, not a standard. Every one of them is editable in the interface, so adjust them to your own delivery experience and the numbers follow through the whole document.

| Task | Default range |
|---|---|
| Server build, each | 2 to 4 hours |
| Veeam ONE install | 4 to 8 hours |
| Veeam ONE configure | 8 to 16 hours |
| Veeam ONE validate and handoff | 1 to 2 hours |
| VRO install | 4 to 8 hours |
| VRO initial configuration | 8 to 12 hours |
| VRO recovery plan build, per plan | 4 to 8 hours |
| VRO test failover, per plan | 2 to 4 hours |

Plan build and plan test hours multiply by the plan counts, which is what makes the VRO estimate scale. Configuration hours multiply by the complexity rating.

## How the complexity multiplier works

It applies to configuration tasks only, not to install or per-plan work, and the report states the base range and the multiplier alongside the adjusted figure so the client can see the arithmetic rather than a single unexplained number.

Use Moderate for multiple sites, mixed hypervisors, or an existing SQL instance under someone else's control. Use Complex for restricted network environments, change-controlled infrastructure, or a client whose approvals move slowly.

## Output file

```
Veeam-One-VRO-Scoping-<CustomerName>.html
```

Self-contained with inline styling, so it can be emailed as one attachment or printed to PDF. The **Reset** button returns every input to its default.

## Limitations

- This produces a draft for a statement of work. It is not a statement of work. Legal terms, payment schedule, change control process, and signature blocks are yours to add.
- Hour ranges are estimates. The generated assumptions section states that actuals are billed as worked unless the SOW says otherwise. Change that line if your commercial terms differ.
- The environment profile fields are recorded and displayed but do not drive the hour calculation. Effort scales with plan counts, report counts, and the complexity multiplier, not with VM count.
- Input is not saved. Closing or refreshing the page returns the defaults, so export before closing.
- Licensing, subscription cost, and hardware are out of scope. The tool estimates professional services effort only.

## Privacy

The file contains no tracking, no analytics, and no external requests. All calculation happens in the browser. The exported document is generated locally and never uploaded.

## Related

- Free Microsoft 365, Active Directory, and Veeam tools at [m365admintools.com](https://m365admintools.com)

## Author

Charles Arconi, [m365admintools.com](https://m365admintools.com)

Not affiliated with, endorsed by, or supported by Veeam Software. Veeam is a trademark of Veeam Software Group GmbH.

## License

MIT. See [LICENSE](LICENSE).
