# OptiScaler-Bleeding-Edge

An automated release pipeline that monitors the [OptiScaler](https://github.com/optiscaler/OptiScaler) repository for successful builds and creates bleeding-edge releases with additional complementary tools.

## What This Does

1. **Monitors OptiScaler builds**: Checks the [OptiScaler build workflow](https://github.com/optiscaler/OptiScaler/actions/workflows/just_build.yml) for successful runs every 6 hours
2. **Downloads all build artifacts**: Retrieves all OptiScaler build artifacts from successful builds
3. **Fetches complementary tools**: Downloads the latest releases from:
   - [dlssg-to-fsr3](https://github.com/xXJSONDeruloXx/dlssg-to-fsr3) (standard edition only)
   - [fakenvapi](https://github.com/FakeMichau/fakenvapi)
4. **Creates consolidated releases**: Packages all components together with detailed release notes
5. **Smart release management**: Avoids duplicate releases for the same OptiScaler commit (scheduled runs only)

## Automation Schedule

- **Scheduled runs**: Every 6 hours, with duplicate prevention
- **Manual triggers**: Can be triggered manually via workflow dispatch
- **Intelligent tagging**: Manual runs include timestamps to ensure unique tags

## Release Naming

Releases are tagged based on the OptiScaler build artifact name:
- **Scheduled**: `OptiScaler_v0.7.7-pre12_20250625`
- **Manual**: `OptiScaler_v0.7.7-pre12_20250625-20250625-143022`

## Components Included

Each release contains individual files (not zipped):
- **OptiScaler**: All build artifacts from the latest successful build
- **dlssg-to-fsr3**: `dlssg_to_fsr3_amd_is_better.dll` (standard edition, excludes Universal and DLSSTweaks variants)
- **fakenvapi**: `nvapi64.dll` and `fakenvapi.ini`

## Release Features

- **Detailed release notes**: Including component versions and commit information
- **Individual file downloads**: Files are uploaded separately for selective downloading
- **Build traceability**: Links back to original OptiScaler commit and workflow run
- **Component versioning**: Shows exact versions of all included components
