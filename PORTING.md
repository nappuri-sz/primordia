# Minecraft 26.3 port

Maintainer of this adaptation: nappuri-sz. Original author: Jacob Szczepaniak.
Original repository: https://github.com/Zeyphers/Primordia
Original commit: b8479660f1fbcc6aa204f63c2d564977db862043
License: Creative Commons Attribution-NonCommercial 4.0 International; see LICENSE.
This adaptation is independent and does not imply endorsement by the original author.

## Target

Minecraft 26.3, Java 25, Fabric Loader 0.20.1, Fabric API 0.166.2+26.3.
Build-time optional integrations: Mod Menu 21.0.1, LambDynamicLights 4.13.0+26.3,
Controlify 3.5.3+mc26.3. Versions were checked against their Modrinth publications.

## Changes

- Updated Minecraft and Fabric dependency pins and mod metadata.
- Updated optional integration dependency pins for Minecraft 26.3.
- Marked the artifact as an experimental port, version 2.15.4-26.3-port.1.
- Added an official Gradle 9.6.1 wrapper with its distribution SHA-256 pinned.
- Migrated keyboard bindings and guide navigation away from removed GLFW APIs.
- Migrated quaternion rotations to PoseStack.rotate without changing geometry or rotation order.
- Updated server item drops, posed-creature invulnerability and procedural sound event access.
- Migrated gene-lab fuel to COOKING_FUEL with vanilla container loot-context evaluation;
  quick-transfer accepts stacks with the fuel component, as the vanilla furnace menu does.
- Corrected the published Controlify Fabric capability name.

## Build

Set `JAVA_HOME` to a JDK 25 and run `./gradlew build`. The wrapper downloads the
official Gradle distribution and checks its SHA-256. `ci/build.yml` is a CI template;
it is not active because the current GitHub OAuth session lacks the `workflow` scope.
The upstream agent notes about a missing wrapper no longer apply to this fork.

## Validation

Local validation on macOS arm64, Java 25.0.1 and Gradle 9.6.1 (2026-11-16):

- Unmodified upstream 26.2 baseline: build successful, 265 tests, 0 failures/errors/skips.
- 26.3 port: build successful, 265 tests, 0 failures/errors/skips; access widener validated.
- SkeletonWeatheringTest uses the renamed quaternion API; assertions remain unchanged.
- Client startup: in progress; first launch needs Minecraft assets.

The CI file is only a template, not an executed GitHub Actions check.
No claim is made about live rendering, world persistence, multiplayer or interoperability
with other mods until those checks are recorded here.
