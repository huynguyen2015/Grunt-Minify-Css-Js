# Grunt-Minify-Css-Js
Combine & Minify css &amp; js with Grunt &amp; npm

** Prerequired install grunt with npm:
npm install -g grunt-cli

B1: Create structure folder: <br/>
-- 1. css <br/>
---- bootstrap.css <br/>
---- mystyle.css <br/>
-- 2. js <br/>
---- jquery.js <br/>
---- myjs.js <br/>
-- 3. Gruntfile.js <br/>
-- 4. package.json <br/>

B2: copy following code to package.json:						<br/>
{																<br/>
&emsp;	"name": "DEMO",												<br/>
&emsp;	"version": "0.0.1",											<br/>
&emsp;	"description": "Demo Minify CSS - JS",						<br/>
&emsp;	"main": "Gruntfile.js",										<br/>
&emsp;	"author": "The Author",										<br/>
&emsp;	"license": "GPL",											<br/>
&emsp;	"devDependencies": {										<br/>
&emsp;&emsp;		"grunt": "~0.4.1",										<br/>
&emsp;&emsp;		"grunt-contrib-uglify": "~0.2.2",						<br/>
&emsp;&emsp;		"grunt-contrib-cssmin": "~0.6.1",						<br/>
&emsp;&emsp;		"grunt-contrib-concat": "~0.3.0"						<br/>
&emsp;	}															<br/>
}																<br/>

B3: copy the following code to Gruntfile.js:					<br/>
module.exports = function(grunt) { 								<br/>
&emsp;	grunt.initConfig({ 											<br/>
&emsp;	concat: { 													<br/>
&emsp;&emsp; 		gopcss: { 													<br/>
&emsp;&emsp;&emsp;			src: [ 													<br/>
&emsp;&emsp;&emsp;&emsp;				'css/bootstrap.css',								<br/>
&emsp;&emsp;&emsp;&emsp;				'css/style.css', 									<br/>
&emsp;&emsp;&emsp;			], 														<br/>
&emsp;&emsp;&emsp;			dest: 'css/all.css' 									<br/>
&emsp;&emsp;		}, 															<br/>
&emsp;&emsp;		gopjs: { 													<br/>
&emsp;&emsp;			src: [ 													<br/> 
&emsp;&emsp;&emsp;				'js/jquery.js', 									<br/>
&emsp;&emsp;&emsp;				'js/myjs.js', 										<br/>
&emsp;&emsp;			], 														<br/>
&emsp;&emsp;			dest: 'js/all.js' 										<br/>
&emsp;&emsp;		},	 														<br/>
&emsp;	}, 																<br/>
&emsp;	cssmin: { 														<br/>
&emsp;&emsp;		nencss: { 													<br/>
&emsp;&emsp;&emsp;			src: 'css/all.css', 									<br/>
&emsp;&emsp;&emsp;			dest: 'css/all.min.css' 								<br/>
&emsp;&emsp;		}, 															<br/>
&emsp;	 }, 															<br/>
&emsp;	 uglify: { 														<br/>
&emsp;&emsp;		nenjs: { 													<br/>
&emsp;&emsp;&emsp;			src: 'js/all.js', 										<br/>
&emsp;&emsp;&emsp;			dest: 'js/all.min.js', 									<br/>
&emsp;&emsp;		} 															<br/>
&emsp;	 } 																<br/>
 }); 															<br/>
grunt.loadNpmTasks('grunt-contrib-concat'); 					<br/>
grunt.loadNpmTasks('grunt-contrib-cssmin'); 					<br/>
grunt.loadNpmTasks('grunt-contrib-uglify'); 					<br/>
grunt.registerTask('default', ['concat', 'cssmin', 'uglify']); 	<br/>
};

B4: open git bash or window powersell in this folder & run following command: <br/>
npm install

B5: continue run bellow command: <br/>
grunt concat:gopcss concat:gopjs 

B6: continue run bellow command: <br/>
grunt cssmin:nencss uglify:nenjs 