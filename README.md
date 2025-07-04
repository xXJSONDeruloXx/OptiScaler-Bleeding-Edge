# OptiScaler-Bleeding-Edge

An automated release pipeline that monitors the [OptiScaler](https://github.com/optiscaler/OptiScaler) repository for successful builds and creates bleeding-edge releases with additional complementary tools.

## What This Does

1. **Monitors OptiScaler builds**  
   Checks the [OptiScaler build workflow](https://github.com/optiscaler/OptiScaler/actions/workflows/just_build.yml) for successful runs every 6 hours.
2. **Downloads all build artifacts**  
   Retrieves all OptiScaler build artifacts from successful builds.
3. **Fetches complementary tools**  
   Downloads the latest versions of:
   - **dlssg-to-fsr3**: [GitHub](https://github.com/xXJSONDeruloXx/dlssg-to-fsr3) (standard edition only)
   - **fakenvapi**: [GitHub](https://github.com/FakeMichau/fakenvapi)
   - **Streamline SDK**: [GitHub](https://github.com/NVIDIA-RTX/Streamline) (for `nvngx.dll`)
   - **FSR4 DLL**: Downloads `amdxcffx64.dll` directly from AMD's CDN  
     <sub>FSR4 DLL build pipeline inspired by [kellerbraune/amd-fsr4](https://github.com/kellerbraune/amd-fsr4)</sub>

4. **Creates consolidated releases**  
   Packages all components together with detailed release notes and multiple download options:
   - **Bundled 7z package**: All components in one convenient file
   - **Individual files**: Download specific components separately
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

Each release contains both bundled and individual download options:

### Bundled Package
- **BUNDLED_OptiScaler_*.7z**: All components packaged together for convenience

### Individual Components
- **OptiScaler**: All build artifacts from the latest successful build (original 7z files)
- **dlssg-to-fsr3**: `dlssg_to_fsr3_amd_is_better.dll` (standard edition, excludes Universal and DLSSTweaks variants)
- **fakenvapi**: `nvapi64.dll` and `fakenvapi.ini`
- **Streamline SDK**: `nvngx.dll` (renamed from `nvngx_dlss.dll`)
- **AMD FSR 4 DLL**: `amdxcffx64.dll`

## Release Features

- **Multiple download options**: Bundled 7z package or individual files
- **Detailed release notes**: Including component versions and commit information
- **SHA256 verification**: File hashes provided for security verification
- **Build traceability**: Links back to original OptiScaler commit and workflow run
- **Component versioning**: Shows exact versions of all included components
- **File size information**: Detailed file information in JSON format
