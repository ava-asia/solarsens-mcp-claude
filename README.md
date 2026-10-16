# SolarSENS plugin for Claude

SolarSENS is the solar monitoring platform of AVA. This plugin gives Claude
read-only access to the solar Plants that your SolarSENS account can see, and
five Skills that guide common checks.

## What the plugin does

- Connects Claude to one remote MCP server, `https://mcp.solarsens.co/mcp`,
  over Streamable HTTP. There is no local code, hook, or script in this plugin.
- Signs you in with OAuth 2.1 (authorization code with PKCE) through the
  SolarSENS MCP login. The plugin never sees or stores your SolarSENS password.
- Reads only the Plants of the signed-in account. Every tool is read-only. The
  plugin cannot control equipment, acknowledge alarms, change configuration,
  or create work orders.

## Tools

The server lists tools to identify the connected account, list and search
Plants and Portfolios, read Plant and device catalogs, read daily performance,
five-minute and daily values, alarms, work orders, dashboards, charts, and
device telemetry. The current list and each argument are documented at
<https://ai.solarsens.co/>.

## Skills

| Skill | Use it when |
| --- | --- |
| `plant-performance-review` | Daily performance ratio triage for one Plant and one day |
| `string-fault-review` | Find weak strings for one Plant and one day |
| `daily-portfolio-check` | Screen all accessible Plants and review flagged ones |
| `alarm-triage` | Review active alarms for one Plant against telemetry |
| `missing-value-check` | Explain a blank, zero, old, or missing value |

Each Skill is read-only and never invents a value. A missing value is reported
as missing, not as zero.

## Data handling

The plugin sends your requests and the returned monitoring data between Claude
and `mcp.solarsens.co` only. See the
[privacy policy](https://docs.solarsens.co/plugin/privacy/) and
[terms](https://docs.solarsens.co/plugin/terms/). Support:
<https://docs.solarsens.co/plugin/support/>.

## Getting access

A SolarSENS account linked for MCP sign-in is required. Ask your AVA contact
or <support@solarsens.co>.

## Maintenance

This repository holds the published plugin bundle only. The Skills are rendered
from the SolarSENS MCP source project and copied here on each release. Do not
edit `skills/` by hand; the next release overwrites it.
