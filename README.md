# OptiScaler-Bleeding-Edge

An automated release pipeline that monitors the [OptiScaler](https://github.com/optiscaler/OptiScaler) repository for successful builds and creates bleeding-edge releases.

## What This Does

1. Monitors the [OptiScaler build workflow](https://github.com/optiscaler/OptiScaler/actions/workflows/just_build.yml) for successful runs
2. Downloads the build artifacts from successful OptiScaler builds
3. Additionally fetches the latest releases from:
   - [dlssg-to-fsr3](https://github.com/xXJSONDeruloXx/dlssg-to-fsr3)
   - [fakenvapi](https://github.com/FakeMichau/fakenvapi)
   - [Streamline SDK](https://github.com/NVIDIA-RTX/Streamline)
4. Creates a consolidated release with all components
5. Tags and names the release based on the OptiScaler build artifact name

## Releases

Releases are automatically created and tagged with the same version as the OptiScaler build, for example:
`OptiScaler_v0.7.7-pre12_20250625`

## Components Included

Each release contains:
- The latest successful OptiScaler build artifacts
- Latest dlssg-to-fsr3 DLL (excluding Universal and DLSSTweaks editions)
- Latest fakenvapi (nvapi64.dll and fakenvapi.ini)
- Latest Streamline SDK's nvngx_dlss.dll (renamed to nvngx.dll)
