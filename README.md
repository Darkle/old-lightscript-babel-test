
	* Babel setup:

		* I dont really need to bundle the js, so I dont really need webpack or rollup, I could use babel (with all the lightscript stuff and babel-preset-flow if lightscript doesnt take it out) -
		* `npx babel --out-dir ./ --watch **/*.lsc -x .lsc`
		* note: babel will auto convert ESM imports/exports to commonjs
		* Make sure to ignore the node_modules dir in the babelrc
		* I will need to use a codemod to change the imports, cause my imports will be `import foo from './bar.lsc'` and I need to change them to `import foo from './bar.js'`

			* Could maybe just do it as a regex replace, cause they would always be a string and start with ./ and end with .lsc
			* Use These:

				* https://github.com/alanshaw/babel-plugin-import-rename
				* https://github.com/laat/babel-plugin-transform-rename-import
				* https://github.com/avajs/babel-plugin-detective
			* Prolly not this: https://github.com/Velenir/babel-plugin-import-redirect
		* Then for production you would minify- maybe kust use gulp and uglifyjs for that
			* Or can I do it in babel with this? https://babeljs.io/docs/en/babel-preset-minify
				* Yeah, it looks like it does what this does: https://github.com/babel/minify
			* IF I have to fall back to using a bundler, use rollup;
				* https://github.com/wcjohnson/lightscript-minimal-node/blob/4.0/rollup.config.js
				* https://github.com/rollup/rollup/issues/1343
				* https://github.com/rollup/rollup-plugin-node-resolve/issues/77
				* https://github.com/webpack/webpack/issues/2873

