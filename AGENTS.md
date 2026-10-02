# Home Assistant project

## Start here
Read HANDOFF.md at the start of each task. Treat its progress notes as historical context; inspect live Home Assistant state and configuration before making changes.

## Repository scope
This repository contains project instructions and handoff notes only. Home Assistant configuration, dashboards, automations, and Pyscripts remain on the HA NUC. Do not export the full HA configuration or add configuration snapshots unless the user asks to expand the repository's scope.

Never put tokens, passwords, private HA-MCP connection URLs, or credential-bearing configuration in this repository. Configure HA-MCP separately on each computer. Do not assume a Mac-specific or Windows-specific local path.

## Connection and working scope
- Home Assistant: http://192.168.1.10:8123
- Draft dashboard: http://192.168.1.10:8123/home-draft/home
- Each computer needs home-network access or a working Tailscale route and its own HA-MCP setup.
- Work on Home · Draft (home-draft). Preserve original Home (home-2) and Overview (lovelace), unless the user requests otherwise.
- Do not change the default dashboard without a user request.
- Read applicable HA-MCP best-practice guidance before changes. Fetch fresh configuration, use config-hash guarded updates when supported, and read back saved changes.

## Dashboard preferences
Prioritize iPhone, then computer, then iPad. No wall tablet. Keep everyday controls easy to reach. Verify responsive layouts and distinguish visual/configuration checks from physical device tests.

## Lighting behavior to preserve
Bedside lights, living-room reading light, and office lighting use Pyscript at /config/pyscript/apps/light_button_control. Single and double taps call light.action with data.entity_id and data.action set to single or double. Preserve both card and icon actions where applicable; do not substitute standard toggles or add sliders for these controls. Hold opens more-info.

Julia's desk light is an exception and uses standard light controls. See HANDOFF.md for known entity IDs; verify them against live HA before editing.

## Continuing across computers
Check Git status before editing and preserve existing work. When switching machines, synchronize committed notes through Git. Do not discard local changes to reconcile branches.

Update HANDOFF.md after meaningful work with changes, verification results, unresolved issues, and next steps. Keep this file for durable guidance. Commit and push when requested; do not claim notes have synchronized until that succeeds.
