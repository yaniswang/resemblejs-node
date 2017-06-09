ResembleJs-Node
==========

It is Node port for Resemble.js, no need canvas or any other binary denpendencies.

Analyse and compare images with Javascript and HTML5. [More info & Resemble.js Demo](http://huddle.github.com/Resemble.js/).

![Two image diff examples side-by-side, one pink, one yellow.](https://raw.github.com/Huddle/Resemble.js/master/demoassets/readmeimage.jpg "Visual image comparison")

Get it
==========

`npm install resemblejs-node`

Example
==========

Simple demo:

    var diff = resemble('old.png').compareTo('new.png').ignoreColors().onComplete(function(result){
        console.log(result);
        /*
        {
            analysisTime: 8
            diffBounds: Object {top: 0, left: 77, bottom: 199 …}
            dimensionDifference: Object {width: -82, height: 0}
            getDiffImage: function (text){ … }
            getDiffImageAsJPEG: function (quality) { … }
            getImageDataUrl: function (text){ … }
            isSameDimensions: false
            misMatchPercentage: "46.78"
            rawMisMatchPercentage: 46.78021978021978
        }
        */
    });

ES7 async demo:

    (async function(){
        let diff = resemble('old.png').compareTo('new.png').ignoreColors();
        let diffResult = await new Promise((resolve) => diff.onComplete(resolve));
        console.log(diffResult);
        diffResult.getDiffImage().pack().pipe(fs.createWriteStream('diff.png'));
    })();


Read more options, please visit: [https://github.com/Huddle/Resemble.js](https://github.com/Huddle/Resemble.js)

License
================

ResembleJs-Node is released under the MIT license:

> The MIT License
>
> Copyright (c) 2017 yanis.wang@gmail.com
>
> Permission is hereby granted, free of charge, to any person obtaining a copy
> of this software and associated documentation files (the "Software"), to deal
> in the Software without restriction, including without limitation the rights
> to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
> copies of the Software, and to permit persons to whom the Software is
> furnished to do so, subject to the following conditions:
>
> The above copyright notice and this permission notice shall be included in
> all copies or substantial portions of the Software.
>
> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
> IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
> FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
> AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
> LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
> OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
> THE SOFTWARE.

Thanks
================

* Resemble.js: [https://github.com/Huddle/Resemble.js](https://github.com/Huddle/Resemble.js)
* node-resemble.js: [https://github.com/lksv/node-resemble.js](https://github.com/lksv/node-resemble.js)
* pngjs: [https://github.com/lukeapage/pngjs](https://github.com/lukeapage/pngjs)
* jpeg-js: [https://github.com/eugeneware/jpeg-js](https://github.com/eugeneware/jpeg-js)
