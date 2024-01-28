# ed-hide-code-using-js

## Disabling the right mouse click

One method to prevent users from accessing the context menu, which includes options such as viewing source, inspecting elements, and saving images, is by disabling right-clicking through event listeners or CSS properties. However, this approach is not entirely effective in hiding code, as users can still access the source code using keyboard shortcuts or browser tools.

Here's how to disable the right mouse click in javascript,

```
document.addEventListener('contextmenu', event => event.preventDefault());
```

Note: You should not disable the right click as it makes the website less accessible resulting bad User Experience.

##  Create a .env file 

Create a file with the name .env inside your project folder ( not inside the src folder) with the same path where package.json is defined and add the below code inside it: 

```
GENERATE_SOURCEMAP=false; 
```

Now build your app using npm run build or yarn run build from the terminal. It will generate a build folder without a source map, that you can deploy to the production. 
 
## Use package.json file 

Change your build command in the script object as: 

```
// For the Windows OS type the following command in cmd 
"build": "set \"GENERATE_SOURCEMAP=false\" && react-scripts build" 
 
// For Linux OS 
"build": "GENERATE_SOURCEMAP=false react-scripts build" 
```

## Use the cross-env package 

Next, you can also use a package called cross-env. It injects your environment variables and works with  Windows, Linux, and other environments. 

```
npm install --save-dev cross-env 
```

And then add the following command. 

```
"build": "cross-env GENERATE_SOURCEMAP=false react-scripts build", 
```

Set it for the multiple global variables. 

```
"scripts": { 
"build": "cross-env NODE_ENV=production OTHERFLAG=myValue webpack --config build/webpack.config.js" 
} 
```
 
## Code obfuscation 

It makes the code unreadable by humans while retaining functionality. It can be done through online tools or one can use the JavaScript obfuscator. 

Some popular obfuscators are, 

- Obsuscator.io 
- JavaScript Obfuscator 

These obfuscators offer features such as variable renaming, string extraction, and encryption, dead code injection, control flow flattering, and other code transformation techniques to confuse the human readers further. 
