versions-maven-plugin
=====================
As the [Versions Maven Plugin](http://www.mojohaus.org/versions-maven-plugin/index.html) requires version number rules to be available via a URI, and file URIs
must be absolute making per-repo rules unworkable, this repo is used to host a shared [rule set](maven-version-rules.xml). These rules help
`versions:display-dependency-updates` display and `versions:use-latest-releases` update dependencies while ignoring prerelease versions.

References
==========
- [Version number rules](http://www.mojohaus.org/versions-maven-plugin/version-rules.html)
