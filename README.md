## JADX

[![Build Status](https://travis-ci.org/skylot/jadx.png?branch=master)](https://travis-ci.org/skylot/jadx)
[![Gitlab CI](https://gitlab.com/skylot/jadx/badges/master/build.svg)](https://gitlab.com/skylot/jadx/builds)
[![Jadx Core Coverage](https://gitlab.com/skylot/jadx/badges/master/coverage.svg)](https://gitlab.com/skylot/jadx/builds)
[![Code Coverage](https://codecov.io/gh/skylot/jadx/branch/master/graph/badge.svg)](https://codecov.io/gh/skylot/jadx)
[![Coverity Scan Build Status](https://scan.coverity.com/projects/2166/badge.svg)](https://scan.coverity.com/projects/2166)
[![SonarQube Bugs](https://sonarcloud.io/api/badges/measure?key=jadx&metric=bugs)](https://sonarcloud.io/dashboard?id=jadx)
[![Latest release](https://img.shields.io/github/release/skylot/jadx.svg)](https://github.com/skylot/jadx/releases/latest)
[![Latest release downloads](https://img.shields.io/github/downloads/skylot/jadx/latest/total.svg)](https://github.com/skylot/jadx/releases/latest)
[![License](http://img.shields.io/:license-apache-blue.svg)](http://www.apache.org/licenses/LICENSE-2.0.html)

**jadx** - Dex to Java decompiler

Command line and GUI tools for produce Java source code from Android Dex and Apk files

![jadx-gui screenshot](https://i.imgur.com/h917IBZ.png)


### Downloads
- [unstable](https://gitlab.com/skylot/jadx/builds/artifacts/master/browse/build?job=build)
- from [github](https://github.com/skylot/jadx/releases)
- from [sourceforge](http://sourceforge.net/projects/jadx/files/)


### Building from source
Java 8 JDK or higher must be installed:

    git clone https://github.com/skylot/jadx.git
    cd jadx
    ./gradlew dist

(on Windows, use `gradlew.bat` instead of `./gradlew`)

Scripts for run jadx will be placed in `build/jadx/bin`
and also packed to `build/jadx-<version>.zip`


### Run
Run **jadx** on itself:

    cd build/jadx/
    bin/jadx -d out lib/jadx-core-*.jar
    # or
    bin/jadx-gui lib/jadx-core-*.jar


### Usage
```
jadx[-gui] [options] <input file> (.dex, .apk, .jar or .class)
options:
 -d,  --output-dir           - output directory
 -ds, --output-dir-src      - output directory for sources
 -dr, --output-dir-res      - output directory for resources
 -j,  --threads-count        - processing threads count
 -r,  --no-res               - do not decode resources
 -s,  --no-src               - do not decompile source code
 -e,  --export-gradle        - save as android gradle project
      --show-bad-code        - show inconsistent code (incorrectly decompiled)
      --no-imports           - disable use of imports, always write entire package name
      --no-replace-consts    - don't replace constant value with matching constant field
      --escape-unicode       - escape non latin characters in strings (with \u)
      --deobf                - activate deobfuscation
      --deobf-min            - min length of name
      --deobf-max            - max length of name
      --deobf-rewrite-cfg    - force to save deobfuscation map
      --deobf-use-sourcename - use source file name as class name alias
      --cfg                  - save methods control flow graph to dot file
      --raw-cfg              - save methods control flow graph (use raw instructions)
 -f,  --fallback             - make simple dump (using goto instead of 'if', 'for', etc)
 -v,  --verbose              - verbose output
 -h,  --help                 - print this help
Example:
 jadx -d out classes.dex
```

### Troubleshooting
##### Out of memory error:
  - Reduce processing threads count (`-j` option)
  - Increase maximum java heap size:
    * command line (example for linux):
      `JAVA_OPTS="-Xmx4G" jadx -j 1 some.apk`
    * edit 'jadx' script (jadx.bat on Windows) and setup bigger heap size:
      `DEFAULT_JVM_OPTS="-Xmx2500M"`


### Contribution

To support this project you can:
  - Post thoughts about new features/optimizations that important to you
  - Submit bug using one of following patterns:
    * Java code examples which decompiles incorrectly
    * Error log and link to _public available_ apk file or app page on Google play

---------------------------------------
*Licensed under the Apache 2.0 License*

*Copyright 2018 by Skylot*
