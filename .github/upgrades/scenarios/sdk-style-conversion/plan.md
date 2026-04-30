# SDK-style Project Conversion Plan

## Overview

**Target**: Convert the BlueSteel VSIX project from legacy csproj format to SDK-style while keeping .NET Framework 4.7.2.
**Scope**: Single-project solution with VSIX-specific build settings and one custom publish target.

## Tasks

### 01-convert-bluesteel-csproj: Convert BlueSteel project file to SDK-style

Convert `src/BlueSteel.csproj` using SDK-style project structure while preserving VSIX packaging behavior, generated manifest handling, and the custom `PublishToMarketplace` target. Keep project output semantics and extension assets unchanged.

**Done when**: `src/BlueSteel.csproj` uses SDK-style format, VSIX-specific settings are preserved, target framework remains .NET Framework 4.7.2, and the project builds successfully.

---

### 02-convert-solution-to-slnx: Migrate solution container from .sln to .slnx

Create an `.slnx` representation for `BlueSteel.sln` and ensure the converted SDK-style project is correctly represented in the new solution container.

**Done when**: `BlueSteel.slnx` exists, references `src/BlueSteel.csproj`, and solution build succeeds from the updated container.
