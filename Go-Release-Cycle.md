## Schedule

The current cycle is to make a major release every six months.

* Three months of general development.
* Three months of release testing, known as the "feature freeze".

During the freeze, only bug fixes and doc updates are accepted. Changes that were mailed before the freeze can be submitted if they are reviewed after the freeze.

On occasion new work may be done during the freeze, but only in exceptional circumstances and typically only if the work was proposed and approved before the cutoff. Such changes should be low risk.

The releases fall on Feb 1 and Aug 1, so the schedule is:

* Feb 1: Go 1.x released; work begins on Go 1.x+1
* May 1: Feature freeze for Go 1.x+1
* Aug 1: Go 1.x+1 released; work begins on Go 1.x+2
* Nov 1: Feature freeze for Go 1.x+2

One or more release candidates are cut during the freeze for the community to test before each major release.

## Minor releases

Minor releases (1.x.y) may be issued between major releases to address critical issues (typically stability or security issues). Only fixes for which there is no workaround (usually the issues that motivated the release) will be cherry-picked for minor releases.