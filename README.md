# Control4 (maintained fork)

> **Fork of [lawtancool/hass-control4](https://github.com/lawtancool/hass-control4) (v1.7.0).**
> Upstream has been dormant since February 2026, so this fork carries the fixes
> needed for current Home Assistant versions. Changes from upstream 1.7.0:
>
> - Use `via_device_id` instead of the deprecated `via_device` tuple in both
>   `device_info` blocks (builds on upstream PR
>   [#86](https://github.com/lawtancool/hass-control4/pull/86) by @gadgetbazza).
> - Use `async_get_device_by_identifier` instead of the deprecated
>   `async_get_device`, which stops working in Home Assistant 2027.8.0.
> - Versioned with CalVer (`YYYY.MM.DD.N`) so fork releases never collide with
>   upstream version numbers. Example: `2026.11.24.0` = first build on 2026-11-24.
>
> Fixes are offered back upstream as PRs; this fork exists so the fixes are
> installable while upstream is unmaintained.
>
> Install via HACS as a custom repository:
> HACS -> three-dot menu -> Custom repositories -> add
> `https://github.com/vrizopoulos/hass-control4` as type **Integration**.

---

# hass-control4

This custom integration for Home Assistant allows control of Control4 lights, locks (only locks that are relay-based in Control4), alarm control panels, door/window/motion sensors (as binary sensors), thermostats, fans, relay devices (as switches), and blinds/shades (as covers, stateless open/close/stop).

## Installation

First, add this repository as a [custom repository](https://www.hacs.xyz/docs/faq/custom_repositories/) in HACS. 

Then, you can use the link below to install the integration through HACS:

[![Open your Home Assistant instance and open a repository inside the Home Assistant Community Store.](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=vrizopoulos&repository=hass-control4)

Once installed, follow the same setup instructions as the default integration: https://www.home-assistant.io/integrations/control4

### Alarm control panel

Arm types are discovered from Control4 (`arm_types` / `arm_states` capabilities and `C4SecurityPanel.get_arm_types()`). On first load, Stay/Away (and other common modes) are auto-mapped to Home Assistant arm home/away when options are still `(not set)`.

Use **Security System** (the partition with `PARTITION_STATE`) as the primary entity. The companion **Security Panel** UI item is disabled by default when it is not a usable partition.

Entity services:

- `control4.send_alarm_keystrokes` — virtual keypad keystrokes
- `control4.trigger_emergency` — Fire, Medical, Panic, or Police (when supported)

You can still adjust mode mapping under **Configure** on the Control4 integration entry.

## Disclaimer

This integration is essentially a newer version of the Control4 integration that is included in Home Assistant by default, and will receive new updates faster than the default integration.

This means, however, that this custom integration may not be as stable as the default integration, as the code has not gone through Home Assistant's review process and contains the newest, bleeding-edge features.

This integration is not affiliated with or endorsed by Control4.
