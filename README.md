# Logger: A Log4j-like library for LabVIEW&trade;

[Logger](http://sine.ni.com/nips/cds/view/p/lang/en/nid/215388) is a small logging utility modeled after the [Log4j](http://logging.apache.org) and similar libraries but for the [LabVIEW programming language](http://www.ni.com/labview) and environment published and distributed by [National Instruments (NI)](http://www.ni.com). 

This add-on can be used to create a robust, full-feature application logging and error-handling system for any LabVIEW-based application. Logging statements are written as Comma-Separated Values (CSV) lines to a log file. Log files are managed and organized by calendar date and file name to reduce clutter and on-disk storage space. Logging can be configured to automatically close and create a new log file based on file size. Advanced error-handling capabilities are provided by combining level-based application logging with the LabVIEW General Error Handler VI to easily catch, log, clear, and display errors based on verbosity, severity, and configuration. The library is written 100% in LabVIEW and can run on any system that can run LabVIEW.

This repository is just a mirror of the source code and project files to make it publicly and freely available for modification if needed. See the [Installation](#installation) section for information about installing and using the library.

## Installation

A VI Package (VIP) is available on the NI's [LabVIEW Tools Network](http://www.ni.com/labview-tools-network/). It is recommended to use the [VI Package Manager](https://vipm.jki.net/) published by [JKI](http://jki.net/) to install and update the library.

## [Documentation](https://help.fieldrndservices.com/logger)

See the in-app LabVIEW Help system for more information and documentation about using the library after it has been installed. Examples are also available within the LabVIEW development environment.

## License

The `Logger` project is licensed under the [BSD license](https://opensource.org/licenses/BSD-3-Clause). See the [LICENSE](https://github.com/fieldrndservices/logger/blob/master/LICENSE) file for information about licensing and copyright.

