# Field R&D Services: Logger Change Log

All notable changes to this project will be documented in this file, which is written in plain text (ASCII) using the [Markdown](http://daringfireball.net/projects/markdown/syntax) lightweight markup language. This project adheres to [Semantic Versioning](http://semver.org). 

## [Unreleased][Unreleased]

## [1.4.0] - 2015-09-18
### Added
- `Configure File Extension` VI to set a file extension for log files other than `csv`.

### Changed
- Execution priority for file logging to _Background (lowest)_.
- The Preferred Execution System to _Standard_ for the file logging `Run` VI.
- The message source for errors that are masked with the `Mask Error` VI to be the VI that calls the `Mask Error` VI, not the `Mask Error` VI itself, which is relatively useless diagnostically.

## [1.3.5] - 2015-09-08
### Fixed
- Files created on rollover with the calendar folder tree disabled removing four (4) folders as the base log folder. This was causing log files to appear within the wrong folder on rollover.

## [1.3.4] - 2015-08-29
### Changed
- The _Source_ for logging an error to the VI that calls the `Catch Error.vi` instead of the error source. The error source is moved to the _Message_ column of the logging statement. The error source can be really long and cause alignment problems when looking at the statements in a text editor. This also helps indicate where the error occurred as it is not always apparent.

## [1.3.3] - 2015-08-20
### Fixed
- Pruning log files on start of file logging not working. The Maximum File Count configuration was not properly set.

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

