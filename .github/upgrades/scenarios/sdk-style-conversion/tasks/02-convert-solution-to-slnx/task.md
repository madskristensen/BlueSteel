# 02-convert-solution-to-slnx: Migrate solution container from .sln to .slnx

Create an `.slnx` representation for `BlueSteel.sln` and ensure the converted SDK-style project is correctly represented in the new solution container.

**Done when**: `BlueSteel.slnx` exists, references `src/BlueSteel.csproj`, and solution build succeeds from the updated container.
