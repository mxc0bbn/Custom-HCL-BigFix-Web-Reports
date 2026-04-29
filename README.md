# Custom HCL BigFix Web Reports

A collection of custom Web Reports for HCL BigFix. Each report is a standalone
`.beswrpt` XML file that can be imported into the BigFix Web Reports server.
Some reports rely on a companion `.bes` analysis that must be activated in the
BigFix console for the report to display data.

## Reports

| Report | Description | Companion analysis |
|---|---|---|
| `MAG_Deployment_Status.beswrpt` | Deployment results for Multi-Action-Groups [Baselines / Patch Policies], on-demand per-group fetching, filtering, CSV export, and print. | — |
| `MDM-Correlation-Status.beswrpt` | Native-agent vs. MDM-agent correlation across Windows devices with multi-filter dropdowns, clickable computer drill-downs, and CSV export. | — |
| `Relay_Cache_File_Analysis-v2.beswrpt` | Matched vs. orphaned relay cache files across servers/relays with multi-server and date-range filters, pagination, and on-demand loading. | `RelayCacheInventory.bes` |
| `Windows Patch Compliance.beswrpt` | Windows patch compliance broken down by severity (Critical/Important/Moderate/Low) with OS and severity-range filters, pagination, and print/export. | `Relevant_Patches_Information_v3.bes` |

## Installing a report

1. Sign in to your BigFix Web Reports server as a user with permission to
   create custom reports.
2. Go to **Report List → New Report → Import**.
3. Upload the desired `.beswrpt` file from this repository.
4. Save, then open the report from your Report List.

## Activating a companion analysis

If a report has a companion `.bes` file (see the table above), the report will
not populate data until that analysis is imported into the BigFix console and
activated against the relevant computer group.

1. Open the BigFix console.
2. **File → Import** the `.bes` file.
3. Activate the analysis on the appropriate site / target group.
4. Allow the next report cycle to complete, then open the corresponding
   Web Report.

## File format

A `.beswrpt` file is an XML document (`<BESWebReport>`) whose `<Data>` element
contains the HTML, CSS, and JavaScript that renders the report inside Web
Reports. BigFix relevance and session-relevance queries are embedded in the
HTML/JS and evaluated by the Web Reports server at runtime.

## Contributing

New reports welcome. Please:

- Keep each report self-contained in a single `.beswrpt` file.
- Use a descriptive filename (e.g. `Patch_Compliance_By_Site.beswrpt`).
- If your report depends on a companion analysis, include the `.bes` file
  and add an entry under **Reports** above noting the pairing.

## License

Released under the MIT License — see [LICENSE](LICENSE).

"HCL BigFix" and "BigFix" are trademarks of HCL Technologies. This project is
not affiliated with or endorsed by HCL Technologies.
