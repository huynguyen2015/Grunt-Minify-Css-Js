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
&#09;	"name": "DEMO",												<br/>
&#09;	"version": "0.0.1",											<br/>
&#09;	"description": "Demo Minify CSS - JS",						<br/>
&#09;	"main": "Gruntfile.js",										<br/>
&#09;	"author": "The Author",										<br/>
&#09;	"license": "GPL",											<br/>
&#09;	"devDependencies": {										<br/>
&#09;&#09;		"grunt": "~0.4.1",										<br/>
&#09;&#09;		"grunt-contrib-uglify": "~0.2.2",						<br/>
&#09;&#09;		"grunt-contrib-cssmin": "~0.6.1",						<br/>
&#09;&#09;		"grunt-contrib-concat": "~0.3.0"						<br/>
&#09;	}															<br/>
}																<br/>

B3: copy the following code to Gruntfile.js:					<br/>
module.exports = function(grunt) { 								<br/>
&#09;	grunt.initConfig({ 											<br/>
&#09;	concat: { 													<br/>
&#09;&#09; 		gopcss: { 													<br/>
&#09;&#09;&#09;			src: [ 													<br/>
&#09;&#09;&#09;&#09;				'css/bootstrap.css',								<br/>
&#09;&#09;&#09;&#09;				'css/style.css', 									<br/>
&#09;&#09;&#09;			], 														<br/>
&#09;&#09;&#09;			dest: 'css/all.css' 									<br/>
&#09;&#09;		}, 															<br/>
&#09;&#09;		gopjs: { 													<br/>
&#09;&#09;			src: [ 													<br/> 
&#09;&#09;&#09;				'js/jquery.js', 									<br/>
&#09;&#09;&#09;				'js/myjs.js', 										<br/>
&#09;&#09;			], 														<br/>
&#09;&#09;			dest: 'js/all.js' 										<br/>
&#09;&#09;		},	 														<br/>
&#09;	}, 																<br/>
&#09;	cssmin: { 														<br/>
&#09;&#09;		nencss: { 													<br/>
&#09;&#09;&#09;			src: 'css/all.css', 									<br/>
&#09;&#09;&#09;			dest: 'css/all.min.css' 								<br/>
&#09;&#09;		}, 															<br/>
&#09;	 }, 															<br/>
&#09;	 uglify: { 														<br/>
&#09;&#09;		nenjs: { 													<br/>
&#09;&#09;&#09;			src: 'js/all.js', 										<br/>
&#09;&#09;&#09;			dest: 'js/all.min.js', 									<br/>
&#09;&#09;		} 															<br/>
&#09;	 } 																<br/>
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