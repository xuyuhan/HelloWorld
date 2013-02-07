## tizen-app-checker ##

    Tizen-app-checker is tools to do compliance checking for Tizen Applications.
    The tools will generate report files (in HTML format by default) to show the result.
    They support platforms of Ubuntu 11.04 and later(32 or 64 bit), windows 7(64 bit).

### Dependences ###
The tools based Node.js(v0.7 or above) and python(v3.0 or above).
So, please check you environment before to use it.
Run from command line:

    node --version
    python --version

### Usage ###
'Tizen application checker'
Run from command line:

    ./bin/tizen-app-checker.js [options] <Tizen application (.wgt or .tpk) file>

Default *{name}.html* and *{name}.log* file will be generated in current directory.
You can see the details by access the content of them.

more helpful usage can be found by run: 

    cd bin
    ./tizen-app-checker.js -h

'Web application checker'
Implementd Features
 1. check widget format
 2. check package composition
 3. check config.xml
 4. check device APIs
 5. check network access
Run from command line:
./tizen-app-checker.js [options] package.wgt

for example:

    cd tizen-app-checker/bin
    ./tizen-app-checker.js ../web/test/tizenSDKSamples/Alarm.wgt

'Native application checker'
Implementd Features
 1. check widget format
 2. check package composition
 3. check manifest.xml
 4. check executable file
 5. check linked library
Run from command line:
./tizen-app-checker.js [options] package.tpk

for example:

    cd tizen-app-checker/bin
    ./tizen-app-checker.js ../native/test/616p56a741-1.0.0-i386.tpk

