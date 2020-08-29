# My project for Google Summer of Code 2020
I worked with Open Printing (under The Linux Foundation) for Google Summer of Code 2020. My project was titled [Common Print Dialog Backends (CPDB) Qt Implementation](https://summerofcode.withgoogle.com/projects/#6705486251950080).

## About the project
### Common Print Dialog Backends
CPDB is one of the main projects of Open Printing. It aims to separate the development of print dialogs and the support for different print technologies. I idea is to have a unified library ([cpdb-libs](https://github.com/OpenPrinting/cpdb-libs)) which the applications can use to check available printers, check the various options supported by those printers, and send print jobs with specified settings. This way, when new printing technologies are developed, all the applications won't have to be updated to use those technologies. Only the CPDB libraries need to be updated, and all the applications that use CPDB will automatically support the new technologies. Currently, the cpdb-libs has backends to support printing to [a file](https://github.com/OpenPrinting/cpdb-backend-file), on [CUPS](https://github.com/OpenPrinting/cpdb-backend-cups) and on [Google Cloud Print](https://github.com/OpenPrinting/cpdb-backend-gcp).

### Qt Print Support
[Qt](https://www.qt.io/) is a popular cross-platform application development framework. Applications built using Qt can support cros platform printing through [Qt Print Support](https://doc.qt.io/qt-5/qtprintsupport-index.html). However, on Linux, Qt Print Support can only print to CUPS and to a file. Further, to support any new features, Qt Print Support would need to be updated.

### My job
My job was to make Qt Print Support use the Common Print Dialog Backends. This would not change anything for the developer building an application - they would use the existing QPrintDialog API. However, the end user would see the difference. If the Common Print Dialog Backends are not installed on the user's system, the Qt Print Support would fall back to its original implementation. But if the beckends are installed, the user would see the new print dialog perhaps with more printers (from non-CUPS backends) and more supported options.
