# Snap Agent Responsibilities

This snap is now maintained by [automated-ken](https://github.com/kenvandine/automated-ken), a self-hosted agentic snap-maintenance dashboard.

## What automated-ken Handles

- **Version Detection**: Automatically polls upstream for new releases
- **Version Bump PRs**: Opens PRs to update the pinned version
- **CI Monitoring**: Monitors build workflows and asks Copilot cloud agent to fix failing builds (with follow-up PRs)
- **YARF Testing**: Runs YARF (Yet Another Release Framework) tests
- **Channel Promotion**: Manages promotion from edge -> candidate -> stable

## Important Notes for Maintainers/Agents

- **Do not hand-edit the pinned version** in snap/snapcraft.yaml
- The removed workflow's job (upstream release polling) is now automated-ken's responsibility
- All build and publish operations now follow the canonical pattern defined in `.github/workflows/automated-snap-build.yml`

This centralization ensures consistent maintenance across the entire snap fleet.