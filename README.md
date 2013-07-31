LESS Mixin: Automatic Multi-Resolution Images
======

A set of LESS mixins for automatically calling resolution appropriate images from either a data-uri or a url/path. It basically does what [retina.js](http://retinajs.com/) does, but uses only LESS.



Features
--------

- Customizable resolution breakpoints.
- Customizable fileype support.
- Uses @2x filename convention.
- Looks for image as a data-uri first, then fallsback to URL or filepath if not found.
- Ready for LESS 1.4.0. 


Download
--------

The source is hosted on github:

[github.com/eightygrit/less-auto-multi-resolution-images](http://github.com/eightygrit/less-auto-multi-resolution-images)

Usage
-------

Set up a `.less` file with all your data-uri encoded images in the following format: 
   
    // Standard resolution
    .get_dui_data('arrow-right',1){ @dui_data: 'data:image/gif;base64,R0lGO...'; }
    
    // 2x Resolution
    .get_dui_data('arrow-right',2){ @dui_data: 'data:image/gif;base64,R0lGO...'; }

    // 3x Resolution
    .get_dui_data('arrow-right',3){ @dui_data: 'data:image/gif;base64,R0lGO...'; }


Import that file and the library into your main `.less` file.

    // In main.less (for example)
    @import url(auto-multi-resolution-images.less);
    @import url(data-uri-images.less);

Then just call the mixins by the same name as the CSS Property:

	#div1{
		.background-image('arrow-right', gif);
	}
	#div2{
		// PNG is default, so no need to specify the extension.
		.background-image('texture-pattern');
	}
	#div3{
		// Since there is no data-uri for this
		// image, it will output the url to the
		// file based on the @base_url variable.
		.background-image('pleeease',jpg);
	}

See the **/example/** directory for more thorough explaination. 


Requirements
------------

A LESS preprocessor of some kind. 
See the [LESS website](http://lesscss.org/) for more information.

TODO
-----
 - Adjust the data-uri location so that all images at all resolutions are not downloaded. 
 - Set better default media queries.
 - Add mixins for `border-image`, `list-style-image`, etc.


License
-------
Copyright 2013 Eighty Grit

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at:

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.