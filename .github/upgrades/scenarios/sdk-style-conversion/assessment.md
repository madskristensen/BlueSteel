# Assessment: SDK-style Conversion

## Projects to Convert
| Project | Path | packages.config | Custom Imports | Special Type | Risk |
|---------|------|----------------|----------------|-------------|------|
| BlueSteel | src/BlueSteel.csproj | No | `Microsoft.Common.props`, `Microsoft.CSharp.targets`, `Microsoft.VsSDK.targets` | VSIX extension (.NET Framework 4.7.2) | Medium |

## Already SDK-style (no action needed)
- none

## Baseline
- Solution builds: Yes
- Warning count: 0 (build output reported successful build)

## Key Findings
- Project is legacy non-SDK-style (`<Project ToolsVersion="15.0" ...>`), with explicit imports and legacy property groups.
- `PackageReference` is already in use, so no `packages.config` migration is needed.
- Includes custom target `PublishToMarketplace` that must be preserved.
- VSIX-specific settings and manifest generation (`source.extension.vsixmanifest`, generated `source.extension.cs`) must be preserved during conversion.
- Project targets **.NET Framework 4.7.2** and should remain unchanged per scenario constraints.
