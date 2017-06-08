# Version Ranges & Locks

Taking full advantage of semantic versioning, the API serves plugin updates using semantic version ranges.

Sketchpacks provides four simple, _yet_ powerful semantic ranges to automate the process of maintaining your ideal Sketch plugin toolchain:

* **Patch-level Locks** restrict your plugin updates to only versions that are less than the next minor level version. For example, lets say we have version 0.1.2, only versions less than 0.2.0 will be downloaded.

* **Minor-level Locks** restrict your plugin updates to only versions that are less than the next major level version. For example, if we had the version 1.2.3, then only versions less than 2.0.0 would be downloaded.

* **Unlocked** plugins automatically download and apply all updates. For example, if we had the version 1.2.3, then any version greater than 1.2.3 will be downloaded.

* **Locked** plugins are considered frozen at the given version. No updates will be applied.

---

###### Caught a mistake or what to contribute to the documentation? [Edit this page on Github](https://github.com/sketchpacks/docs/blob/master/manage/version-ranges-and-locks.md).
