# Grunt-Minify-Css-Js
Combine & Minify css &amp; js with Grunt &amp; npm

** Prerequired install grunt with npm:
npm install -g grunt-cli

B1: Create structure folder: <br/>
-- 1. css <br/>
---- bootstrap.css
---- mystyle.css
-- 2. js
---- jquery.js
---- myjs.js
-- 3. Gruntfile.js
-- 4. package.json

B2: copy following code to package.json:
{
	"name": "DEMO",
	"version": "0.0.1",
	"description": "Demo Minify CSS - JS",
	"main": "Gruntfile.js",
	"author": "The Author",
	"license": "GPL",
	"devDependencies": {
		"grunt": "~0.4.1",
		"grunt-contrib-uglify": "~0.2.2",
		"grunt-contrib-cssmin": "~0.6.1",
		"grunt-contrib-concat": "~0.3.0"
	}
}

B3: copy the following code to Gruntfile.js:
module.exports = function(grunt) {
	grunt.initConfig({
	concat: {
	gopcss: {
		src: [
			'css/bootstrap.css',
			'css/style.css',
		],
		dest: 'css/all.css'
	},
	gopjs: {
		src: [
			'js/jquery.js',
			'js/myjs.js',
		],
		dest: 'js/all.js'
	},
},
 cssmin: {
	nencss: {
		src: 'css/all.css',
		dest: 'css/all.min.css'
	},
 },
 uglify: {
	nenjs: {
		src: 'js/all.js',
		dest: 'js/all.min.js',
	}
 }
 });
grunt.loadNpmTasks('grunt-contrib-concat');
grunt.loadNpmTasks('grunt-contrib-cssmin');
grunt.loadNpmTasks('grunt-contrib-uglify');
grunt.registerTask('default', ['concat', 'cssmin', 'uglify']);
};

B4: open git bash or window powersell in this folder & run following command:
npm install

B5: continue run bellow command:
grunt concat:gopcss concat:gopjs

B6: continue run bellow command:
grunt cssmin:nencss uglify:nenjs