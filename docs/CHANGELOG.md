# Field R&D Services: Logger Change Log

All notable changes to this project will be documented in this file, which is written in plain text (ASCII) using the [Markdown](http://daringfireball.net/projects/markdown/syntax) lightweight markup language. This project adheres to [Semantic Versioning](http://semver.org). 

## [Unreleased][Unreleased]

## [1.5.1] - 2016-03-19
### Removed
- Leading underscore from private VI names.

## [1.5.0] - 2016-02-18
### Added
- _Clear_ control to the `Catch Error` VI. This indicates whether to clear the error on "catching" it or to pass the error along the Error Out indicator.
- _Run_ control to the `Start` VI. This is TRUE by default. If TRUE, then the `Run` VI is started and executed using the VI Server, i.e. in the background. If FALSE, then the `Run` VI must be explicitly called or placed in the block diagram of the "main" VI of the application. If already using the `Start` VI, everything should work as before.

### Changed
- Running the logger explicitly, i.e. placing the `Run` VI on the block diagram, requires a call to the `Start` VI before execution.

## [1.4.4] - 2016-02-11
### Fixed
- _Source_ of messages. Since changing the logging VIs, (WARN, DEBUG, TRACE, etc.), to inline sub-VIs, the source of the logging statements was incorrect.

## [1.4.3] - 2016-02-05
### Changed
- Re-entrant type from Shared to Pre-allocated. The Pre-allocated is better for Real-Time systems to reduce jitter.
- Private Sub-VIs to inline. This provides a small improvement in performance that might be needed on Real-Time systems.
- Logging Public VIs (WARN, DEBUG, ERROR, etc.) to inline. These are small, simple VIs that are used throughout an application. Inlining the VIs may improve performance.
- Palette location from _Addons_ to _User Libraries_.

## [1.4.2] - 2015-12-11
### Added
- Surrounding double quotes to Comma-Separated Values (CSV) statements created from logging messages to properly escape commas in message text/descriptions. Message text/description can sometimes contain commas that do _not_ delimit a column. Commas inside the text can be interpreted as a new column by CSV decoders. Surrounding the text in double quotes is a common mechanism for indicating to decoders to escape commas or other column delimiters.

## [1.4.1] - 2015-10-23
### Added
- `Write Period` control for running the file logging. This allows the user to balance frequency of logging statements to a file with CPU load and resources.

### Fixed
- File logging running continuously even if no logging statements are available. This would cause excessive CPU load and resource usage.
- Shutdown procedure to ensure file logging is always stopped, the file listener is unregistered, and the file manager is shutdown properly.

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

