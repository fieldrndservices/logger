# Field R&D Services: Logger Change Log

All notable changes to this project will be documented in this file, which is written in plain text (ASCII) using the [Markdown](http://daringfireball.net/projects/markdown/syntax) lightweight markup language. This project adheres to [Semantic Versioning](http://semver.org). 

## [Unreleased][Unreleased]

## [1.3.2] - 2015-08-19
### Fixed
- File name not including the day in the ISO 8601 string.

## [1.3.1] - 2015-08-19
### Fixed
- `Configure Maximum File Count` VI not included in palettes.

## [1.3.0] - 2015-08-19
### Added
- Configuration to disable the calendar folder tree creation. A `YYYY/MM/DD` calendar folder tree is created in the Root folder, but this can be disabled using the `Configure Calendar Folder Tree` VI. 

### Fixed
- `Configure File` VI not also configuring the _Enable Calendar Folder Tree_ configuration.

## [1.2.0] - 2015-07-25
### Added
- `Configure Root Folder` to the API. This VI configures the root folder for the file log separately from the file size limit.
- `Configure File Size Limit` to the API. This VI configures the file size limit (rollover limit) for the file log separately from the root folder.
- `Create Temporary Root Folder` to the API. This is a Utility VI that creates a folder path within the user's temporary directory.
- `Start` to the API. This is an Action-Status VI that starts the file logging in the background. There is no need to explicitly call the `Run.vi` when using this VI.

## [1.1.0] - 2015-07-24
### Added
- This CHANGELOG

### Fixed
- Safely shutting down all components

### Removed
- "Application Name" feature. It is never used, and its functionality is confusing and undocumented.

## [1.0.1] - 2015-07-24
### Added
- VI Tree for additional documentation of API.

### Fixed
- `Initialize.vi` missing from the Functions palette.
- `Shutdown.vi` missing from the Functions palette.

### Changed
- Refactored `Private` virtual folder to use sub-project libraries for namespace organization.

