# Home Assistant dashboard handoff

Updated: 2026-10-01. Historical status below has not been revalidated against live HA during repository setup.

Continue an existing Home Assistant dashboard project from either Mac or Windows. Read AGENTS.md first. The actual dashboard and Pyscript live on the Home Assistant NUC, not on the previous Mac.

## Connection
- Home Assistant: http://192.168.1.10:8123
- Draft: http://192.168.1.10:8123/home-draft/home
- Connect Windows to the home network or a Tailscale route that reaches that address.
- Configure HA-MCP as a Streamable HTTP MCP server using the current private connection URL from HA-MCP. Credentials are deliberately not included here.

## Scope and preferences
- Work on Home · Draft (url_path home-draft). Preserve original Home (home-2) and Overview (lovelace).
- Priority: iPhone, computer, iPad. No wall tablet.
- Read live dashboard config before editing; it may have changed since this handoff.
- Follow HA-MCP dashboard best practices; obtain a fresh acknowledgment key if required. Use config-hash guarded edits and verify saved config.

## Current draft
- Home: conditional alerts, everyday lights and thermostat, energy snapshot, energy controls, temperatures, door/garage status, weather.
- Energy: power-flow-card-plus, 24-hour history, Solcast estimates, auto-entities SPAN circuit power list.
- Rooms with subviews: living, office, bedroom, bathrooms, doors.
- Responsive sections were visually checked on iPhone, iPad, desktop.

## Lighting behavior
These tiles have no sliders, both card and icon single/double tap call light.action with data.entity_id set to the light and data.action single or double. Hold opens more-info:
- light.david_bedside (Home and Bedroom)
- light.julia_bedside (Home and Bedroom)
- light.living_room_reading_lamp (Living)
- light.office_lighting (Home and Office)
The user says their behavior is controlled by Pyscript at /config/pyscript/apps/light_button_control. Do not replace that logic with ordinary toggles.
Julia's desk light, light.julias_desk_light, is different: retains brightness slider and standard controls.

## Energy controls on Home
- input_boolean.enable_grid_discharge — Grid discharge
- switch.garage_c3_1_charger_enable — Car charger (user-confirmed existing control despite its device name)
- input_boolean.charge_at_midnight — Charge at midnight
- sensor.grid_delivery_bank_balance — Distribution credit bank, USD

## Pending work
User paused to physically test single/double taps at home. Configuration was verified, but physical light behavior was not tested by the agent. Ask for their results and continue refining the draft. Do not switch the default dashboard without a request.

## Earlier cleanup context
Removed four unavailable Motion Sensor Plus ESPHome entries; retained Garage Motion Sensor eec6e0. Removed retired SONOFF Back Door Wi-Fi device, but its entities later appeared again; do not assume permanent removal. Zigbee Back Door retained. Hid 12 SPAN unmapped-tab sensors (tabs 3, 23, 30, 32) and GFE Override: Grid Connected button. Do not redo cleanup without checking current state and scope.

## Repository setup
The user chose a notes-only repository, codex-home-assistant, for continuity across computers. AGENTS.md contains durable guidance; this file contains progress and pending work. HA configuration remains on the NUC. Repository setup did not change any HA devices or dashboard configuration. These notes must be committed and pushed before they are available through Git on another machine.
