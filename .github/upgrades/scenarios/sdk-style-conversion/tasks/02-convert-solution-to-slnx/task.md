# 02-convert-solution-to-slnx: Migrate solution container from .sln to .slnx

Create an `.slnx` representation for `BlueSteel.sln` and ensure the converted SDK-style project is correctly represented in the new solution container.

**Done when**: `BlueSteel.slnx` exists, references `src/BlueSteel.csproj`, and solution build succeeds from the updated container.

## Scope Inventory

- **Projects affected**: Solution container only (`BlueSteel.sln` -> `BlueSteel.slnx`) referencing `src/BlueSteel.csproj`
- **Distinct concerns**:
  - Generate `.slnx` format from existing solution
  - Validate project mapping remains correct
  - Validate build succeeds from the new solution container
- **Change signals**:
  - Single-project solution, low dependency complexity
  - Prior task already converted project file to SDK-style and build validated
- **Execution approach**:
  - Use `dotnet sln migrate` from repository root to produce `BlueSteel.slnx`
  - Verify resulting solution XML includes `src/BlueSteel.csproj`
  - Build solution after migration to validate no regressions

## Files and Artifacts to Touch

- `BlueSteel.slnx`
- `.github/upgrades/scenarios/sdk-style-conversion/tasks/02-convert-solution-to-slnx/progress-details.md`
