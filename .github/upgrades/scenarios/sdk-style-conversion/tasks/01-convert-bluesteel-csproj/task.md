# 01-convert-bluesteel-csproj: Convert BlueSteel project file to SDK-style

Convert `src/BlueSteel.csproj` using SDK-style project structure while preserving VSIX packaging behavior, generated manifest handling, and the custom `PublishToMarketplace` target. Keep project output semantics and extension assets unchanged.

**Done when**: `src/BlueSteel.csproj` uses SDK-style format, VSIX-specific settings are preserved, target framework remains .NET Framework 4.7.2, and the project builds successfully.

## Scope Inventory

- **Projects affected**: `src/BlueSteel.csproj` (single VSIX project)
- **Distinct concerns**:
  - Project format conversion from legacy MSBuild to SDK-style
  - Preserve VSIX manifest generation and deployment settings
  - Preserve custom `PublishToMarketplace` target and content inclusion
- **Change signals from assessment**:
  - No `packages.config` migration needed (already `PackageReference`)
  - Legacy imports present (`Microsoft.Common.props`, `Microsoft.CSharp.targets`, `Microsoft.VsSDK.targets`)
  - Legacy `TargetFrameworkVersion` must become SDK-style `TargetFramework` while keeping .NET Framework 4.7.2 semantics (`net472`)
- **Skill-guided constraints**:
  - Use SDK root (`<Project Sdk="Microsoft.NET.Sdk">`)
  - Add VSIX capability (`CreateVsixContainer`) and modern VSIX properties
  - Keep generated file metadata using `Compile Update` for `source.extension.cs`
  - Remove old imports and validate with full build

## Files and Artifacts to Touch

- `src/BlueSteel.csproj`
- `.github/upgrades/scenarios/sdk-style-conversion/tasks/01-convert-bluesteel-csproj/progress-details.md`
