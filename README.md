# Logger: A Log4j-like library for LabVIEW&trade;

[Logger](http://sine.ni.com/nips/cds/view/p/lang/en/nid/215388) is a small logging utility modeled after the [Log4j](http://logging.apache.org) and similar libraries but for the [LabVIEW programming language](http://www.ni.com/labview) and environment published and distributed by [National Instruments (NI)](http://www.ni.com). 

This add-on can be used to create a robust, full-feature application logging and error-handling system for any LabVIEW-based application. Logging statements are written as Comma-Separated Values (CSV) lines to a log file. Log files are managed and organized by calendar date and file name to reduce clutter and on-disk storage space. Logging can be configured to automatically close and create a new log file based on file size. Advanced error-handling capabilities are provided by combining level-based application logging with the LabVIEW General Error Handler VI to easily catch, log, clear, and display errors based on verbosity, severity, and configuration. The library is written 100% in LabVIEW and can run on any system that can run LabVIEW.

## Dependencies

- [Caraya](http://sine.ni.com/nips/cds/view/p/lang/en/nid/215909)
- [HTML Help Workshop](https://docs.microsoft.com/en-us/previous-versions/windows/desktop/htmlhelp/microsoft-html-help-downloads) (for compiling the help documentation)
- [JKI State Machine](http://sine.ni.com/nips/cds/view/p/lang/en/nid/209025)
- LabVIEW 2010 or newer (for building)
- LabVIEW 2018 or newer (for development)
- Labricator (only for automated builds, private package)
- [OpenG Array Library](http://sine.ni.com/nips/cds/view/p/lang/en/nid/209027)
- [OpenG File Library](http://sine.ni.com/nips/cds/view/p/lang/en/nid/209027)
- [VIPM Pro](https://vipm.jki.net/get) (only for automated builds)
- [VIPM API](https://support.jki.net/hc/en-us/articles/214136183-VIPM-API) (only for automated builds)

The Caraya, JKI State Machine, OpenG Array Library, OpenG File Library, and VIPM API dependencies must be installed for all versions of LabVIEW (2010 and 2018) to avoid errors during automated builds.

## Installation

A [VI Package (VIP)](https://www.vipm.io/package/field_rnd_services_logger/) is available at [VIPM.io](https://www.vipm.io). The recommended installation instructions are to:

1. Navigate to the [Logger package](https://www.vipm.io/package/field_rnd_services_logger/) at [VIPM.io](https://www.vipm.io/).
2. Click on the _Install_ button to the right. The [VI Package Manager (VIPM)](https://www.vipm.io/download/) (freely available from [JKI](https://jki.net)) will start automatically.
3. Follow the on-screen instructions to complete the installation.

Alternatively, the toolkit can be installed by: (i) downloading the source code and building the VIP, (ii) downloading a VIP from the [releases](https://github.com/fieldrndservices/logger/releases) section of this project, or (iii) manually copying the VIs from the source code into a project.

## Build

### Packaging using VIPM Pro (recommended)

__Important__, if creating a package for LabVIEW 2010 from LabVIEW 2018, the [VI Server TCP/IP ports](http://zone.ni.com/reference/en-XX/help/371361P-01/lvhowto/configuring_the_vi_server/) must be different for each version of LabVIEW and verified with the [VIPM](https://knowledge.ni.com/KnowledgeArticleDetails?id=kA00Z000000P9YmSAK) application _before_ proceeding. An error will occur when the VIPM is started if both LabVIEW 2010 and 2018 are running at the same time. Basically, VIPM will not know which VI server to use if both versions of LabVIEW are using the same TCP/IP port.

If VIPM Pro is available, then open the `Logger.lvproj` file in any version of LabVIEW newer than 2010 and run the `Package.vi` located in the `Scripts` project library of the Project Explorer window. Ensure all dependencies are installed before running the `Package.vi` script.

Note, the version number for the package is set in the `configs\Logger.vipb` file. The version number in the VIP build specification file should be modified and saved _before_ running the `Package.vi` script.

### Packaging using VIPM Free

If VIPM Pro is _not_ available, then the following steps can be executed to do essentially the same thing as the `Package.vi` script. Ensure all dependencies, except VIPM Pro and the VIPM API, are installed before completing these steps.

1. Start LabVIEW 2018 or newer and open the `Logger.lvproj` file.
2. From the Project Explorer window, **File>>Save for Previous Version...**, a new dialog will appear.
3. Select **10.0** from the drop down menu.
4. Click **Save...**. A new dialog will open.
5. Create the `<project root>\target\10.0` folder hierarchy in the project root, i.e. the same folder as the `Logger.lvproj` file, if it does not already exists.
6. Click **Save**.
7. Close LabVIEW 2018 or newer and the `Logger.lvproj` file.
8. Navigate to `<project root>\src`.
9. Copy the `Help` folder to `<project root>\target\10.0\src`.
10. Start LabVIEW 2010.
11. Open the `<project root>\target\10.0\Logger.lvproj` file. Do NOT open the project in any other version of LabVIEW.
12. Run the `Build.vi` in the `Scripts` project library to build each Source Distribution under the "Build Specifications" tree item and the compiled help documentation file (`Logger.chm`). The output of each build will be available in `<project root>\target\10.0\builds`.
13. Open the `<project root>\target\10.0\configs\Logger.vipb` file in VIPM.
14. Build the VI package with VIPM. The output will be available at `<project root>\target\10.0\packages`. Do NOT modify anything in the package build specification, but ensure the "2010" version of LabVIEW is selected in the upper, right-hand corner of the VIPM application window.
15. Close VIPM.
16. Close LabVIEW 2010 and the `<project root>\target\10.0\Logger.lvproj` file.

## [Documentation](https://help.fieldrndservices.com/logger)

See the in-app LabVIEW Help system for more information and documentation about using the library after it has been installed. Examples are also available within the LabVIEW development environment.

## Tests

Tests are written in LabVIEW using the [Caraya](https://github.com/JKISoftware/Caraya) unit testing framework and included in the project via the `Tests.lvlib` project library and the `tests` on-disk folder. To run the tests, open the `Logger.lvproj` file found in the project root in the LabVIEW Development Environment and run the `Test.vi` script located in the `Scripts.lvlib` project library. This will run all of the tests defined in the project. 

## License

The `Logger` project is licensed under the [BSD-3-Clause license](https://opensource.org/licenses/BSD-3-Clause). See the [LICENSE](https://github.com/fieldrndservices/logger/blob/master/LICENSE) file for information about licensing and copyright.

