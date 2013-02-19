#!/usr/bin/env node

var fs = require('fs'),
    fileList = [];

(function() {
    var arguments = process.argv.splice(2);

    console.log("Input Path:");
    console.log(arguments);

    arguments.forEach(function(arg){
        if (!fs.existsSync(arg)) {
            console.log('\"' + arg + '\"' + ' is not exist.');
            console.log("Check failed!");
            process.exit(0);
        }
        walk(arg);
    });

    fs.writeFileSync("nativeLib.list", fileList.join(",")) ;
    console.log("Check succeed!");
    console.log("Output: " + '\"' + "./nativeLib.list" + '\"');
})();


function walk(path){
    var dirList = fs.readdirSync(path);
    var testRule = /(.a|.so)$|(\.so)+(\.\d+)+/;

    dirList.forEach(function(item){
        if(testRule.test(item)
            && fs.statSync(path + '/' + item).isFile()
            && !fs.lstatSync(path + '/' + item).isSymbolicLink()){
            if (fileList.indexOf(item) < 0)  {
                fileList.push(item);
            }

        }
    });

    dirList.forEach(function(item){
        if(fs.statSync(path + '/' + item).isDirectory()){
            walk(path + '/' + item);
        }
    });
}



desktop:~/Desktop/script$ node get_native_lib.js ./tizen-device-2.0.cpp/ ./tizen-device-2.0/
Input Path:
[ './tizen-device-2.0.cpp/', './tizen-device-2.0/' ]
Check succeed!
Output: "./nativeLib.list"
