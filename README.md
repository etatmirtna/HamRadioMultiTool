FCC Callsign Lookup & Radar Map
A professional-grade amateur radio application featuring comprehensive FCC license database search with an interactive azimuthal equidistant radar-style map for distance and bearing visualization.
Show Image
Professional azimuthal equidistant projection centered on operator's QTH
✨ Features
🗂️ Comprehensive FCC Database Integration

1.67 million amateur radio licenses with full historical tracking
Type 2 Slowly Changing Dimensions for license history analysis
Advanced search capabilities with multiple criteria filtering
QRZ.com integration for grid squares and foreign callsign data
Real-time distance and bearing calculations from your QTH to any callsign
Configurable result limits from 100 to 1,000,000 records

🗺️ Professional Radar-Style Mapping

True azimuthal equidistant projection showing accurate distances and bearings
Interactive projection re-centering - pan anywhere on Earth and see the world from that perspective
Multi-layer Geographic Information System with Natural Earth datasets
Automatic Level of Detail (LOD) switching between 1:50m and 1:10m scales based on zoom level
Database-driven layer management with real-time toggle capabilities
12,000-mile boundary visualization with precise bearing markers every 10°

🛠️ Advanced Technical Architecture

Cross-platform native application built with Avalonia UI for Linux, Windows, and macOS
High-performance SkiaSharp rendering with custom geometric projection algorithms
SQLite database backend with optimized spatial indexing
US Census Bureau geocoding integration for 255K+ unique address locations
Shapefile (.shp) support with automatic polygon and polyline handling
Memory-efficient caching for instant layer switching and search results

🎯 Professional UI/UX

Comprehensive toolbar with zoom, pan, home, and layer controls
Interactive layer management dialog with grouped checkbox controls
Real-time status feedback with progress indicators for long operations
Keyboard and mouse shortcuts for efficient operation
Professional dark theme optimized for extended use

🚀 Quick Start
Prerequisites

.NET 9.0 Runtime or later
Linux Mint 22 (or compatible Linux distribution)
4GB+ RAM recommended for optimal performance
2GB+ disk space for full dataset installation

Installation

Clone the repository

bash   git clone https://github.com/yourusername/fcc-callsign-radar.git
   cd fcc-callsign-radar

Build the application

bash   dotnet build --configuration Release

Download FCC database (automated on first run)

bash   dotnet run --project FccCallSignTool.UI

Configure your QTH coordinates

Navigate to Settings → QTH Configuration
Enter your station's latitude and longitude
Save and restart for optimal distance/bearing calculations



📋 System Requirements
Minimum Requirements

OS: Linux (Ubuntu 20.04+, Fedora 32+, openSUSE 15+)
RAM: 2GB
Storage: 1GB free space
Display: 1024x768 minimum resolution

Recommended Requirements

OS: Linux Mint 22 or Ubuntu 22.04+
RAM: 8GB
Storage: 4GB free space (includes full geographic datasets)
Display: 1920x1080 or higher resolution
Network: Broadband connection for initial data download

🗃️ Database Architecture
FCC License Data
sql-- Core license tracking with historical changes
AmateurLicenses (EntityId, Callsign, OperatorClass, LicenseStatus, ...)
Entities (EntityId, Name, StreetAddress, City, State, ZipCode, ...)
History (EntityId, FieldName, OldValue, NewValue, ChangedAt, ...)
Geographic Data
sql-- Optimized spatial lookups
CallsignGridXref (EntityId, Callsign, Latitude, Longitude, GridSquare, DistanceTo, BearingTo, ...)
GeocodedLocationCache (CacheKey, Latitude, Longitude, GeocodedAt, ...)
geo_layer (geo_layer_id, geo_layer_source_path, geo_layer_ui_name, geo_layer_scale, ...)
🎛️ User Interface Guide
Main Search Interface

Callsign Search: Exact callsign lookup with wildcard support
Name Search: Search by license holder name
Geographic Search: City, state, or ZIP code filtering
Advanced Filters: Combine multiple search criteria
Result Management: Configurable limits and export capabilities

Radar Map Controls

🎯 Home: Return to your QTH coordinates
🔍+ / 🔍-: Zoom in/out with automatic LOD switching
✋ Pan Mode: Click to toggle projection re-centering mode
⟲ Reset: Return to default view and original projection center
Scale Selector: Choose UI scale (1:10m, 1:50m, 1:110m)
🗂 Layers: Open layer management dialog

Layer Management

Default Layers: Coastlines, land masses, country borders
Physical Layers: Lakes, rivers, ocean boundaries
Cultural Layers: Population centers, urban areas
Toggle Visibility: Real-time layer enable/disable
Group Organization: Layers organized by geographic type

📊 Performance Characteristics
Database Performance

Search Speed: <100ms for typical callsign queries
Geographic Lookup: <50ms for distance/bearing calculations
Layer Loading: <2s for 50m scale, <5s for 10m scale
Memory Usage: ~200MB base + ~50MB per active layer

Rendering Performance

Map Rendering: 60fps at typical zoom levels
Layer Switching: Instantaneous for loaded layers
Projection Updates: <1s for complete re-centering
Zoom Operations: Smooth animation with LOD switching

🔧 Configuration
Database Configuration
json{
  "DatabaseSettings": {
    "FccDatabasePath": "~/.fcc-callsign-tool/fcc-licenses.db",
    "GeoDatabasePath": "~/.fcc-callsign-tool/geodata.db",
    "AutoUpdateEnabled": true,
    "UpdateIntervalDays": 7
  }
}
Map Configuration
json{
  "MapSettings": {
    "DefaultScale": 50,
    "EnableAutoLOD": true,
    "LODSwitchThreshold": 0.15,
    "MaxZoomLevel": 2.0,
    "EnableBearingLines": true,
    "EnableDistanceRings": true
  }
}
QTH Configuration
json{
  "QTHSettings": {
    "Callsign": "WD8TA",
    "Latitude": 39.970600793756,
    "Longitude": -82.824398202544,
    "GridSquare": "EN80nx",
    "EnableGridSquareValidation": true
  }
}
🛡️ Data Sources & Licensing
FCC Data

Source: FCC Universal Licensing System
License: Public domain
Update Frequency: Weekly automated downloads
Coverage: Complete US amateur radio license database

Geographic Data

Source: Natural Earth
License: Public domain
Scales Available: 1:10m (detailed), 1:50m (standard), 1:110m (simplified)
Coverage: Global coastlines, borders, populated places

Geocoding Service

Source: US Census Bureau Geocoding Service
License: Public domain
Accuracy: Street-level address resolution
Coverage: United States addresses only

🤝 Contributing
We welcome contributions to improve the FCC Callsign Lookup & Radar Map application!
Development Setup
bash# Clone and build
git clone https://github.com/yourusername/fcc-callsign-radar.git
cd fcc-callsign-radar
dotnet restore
dotnet build

# Run tests
dotnet test

# Run application in development mode
dotnet run --project FccCallSignTool.UI
Contribution Guidelines

Bug Reports: Use the issue tracker with detailed reproduction steps
Feature Requests: Describe use cases and technical requirements
Pull Requests: Include tests and documentation updates
Code Style: Follow Microsoft C# coding conventions

📧 Support & Community
Getting Help

Documentation: Check the Wiki
Issues: GitHub Issue Tracker
Discussions: GitHub Discussions

Amateur Radio Community

QRZ.com Integration: Seamless integration with existing QRZ workflows
Contest Logging: Distance and bearing data perfect for contest preparation
VHF/UHF DX: Optimized for weak signal work and grid square hunting
Antenna Planning: Precise bearing calculations for directional antennas

📜 License
This project is licensed under the MIT License - see the LICENSE file for details.
🙏 Acknowledgments

Natural Earth for providing high-quality, public domain geographic datasets
FCC for maintaining the Universal Licensing System and making license data publicly available
US Census Bureau for providing free, high-accuracy geocoding services
QRZ.com for grid square data and amateur radio community integration
Avalonia UI team for creating an excellent cross-platform UI framework
Amateur radio community for feedback, testing, and feature suggestions


73 de WD8TA - Built by hams, for hams. Enjoy exploring the world of amateur radio with accurate distance and bearing visualization!
Current Version: 1.0.0 | Build Status: ✅ Stable | Platform: Linux/Windows/macOS
