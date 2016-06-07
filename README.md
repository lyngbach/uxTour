# uxTour.js
UX tour guide plugin in a single plain vanilla JavaScript file.

Introduction
--------
So I was browsing around trying to find some nice feature tour overlay plugins for a project. However there was only a few who met the design criteria and even less who could actually compete with the projects needs. In fact there was zero plugins who could meet the requirements of a single page material design applikation with several fixed elements and therefor I came up with this little plugin, specifically made for 3 main purposes.

1. Avoid the dreaded z-index crap that every browser and every applikation have different ways of handling along with fixed position elements.
2. Make it work dynamically for single page applikations like with the Angular framework.
3. Make it feel more of the Material Design guidelines.

A short demo can be viewed here (link on its way).


Usage
--------
Add the javascript file to your project and include it at your index:
```html
<script src="path/to/uxTour.js"></script>
```

Next, init the plugin and prepare the tour in a JSON object:
```js
var uxTour = new uxTour();

var tour = {
	steps: [
		{element: 'idOfElement1', text: 'This will be the first step'},
		{element: 'idOfElement2', text: 'This is the second step on a fixed element', style: 'fixed'},
		{element: 'idOfElement3', text: 'And the third step.<br> With a bit of html', position: 'top'}
	]
};
```

Then you just start the tour:
```js
uxTour.start(tour);
```

If you for example want it to work with a single page applikation you just dynamically empty and add new steps to fit your applikations logic.


Options
--------
The plugin comes with some few optional properties that allow you to customize the tour a bit when your init the plugin


| Property		| Type		| Default	| Description																|
| ------------- | --------- | --------- | ------------------------------------------------------------------------- |
| padding   	| integer	| 16		| Set the padding for the highlighted area in pixels	|
| opacity   	| number	| 0.7		| Set the opacity of the overlay from 0 to 1			|
| color 		| string	| #000000	| Set the color of the overlay in a hex color		|
| buttonText	| string	| GOT IT	| Default is english Material Design text in caps. Set to fit your language needs	 	|
| frame      	| string	| circle	| Make it a square instead of a cricle to frame the element by adding the string 'box'	 	|

An example could be:
```js
var uxTour = new uxTour({
    opacity: 0.8,
    color: '#2196F3' // blue
});
```

Step options
--------
When you prepare the steps you can add a few additional steps-only properties to make it the fit your applikation even more:

| Property		| Type		| Default	| Description																|
| ------------- | --------- | --------- | ------------------------------------------------------------------------- |
| element   	| string	| null  	| Required. The id of the element. If the id cant be found the step will be skipped |
| text         	| string	| null  	| Required. Write the text for the selected step. HTML is allowed	|
| direction   	| string	| bottom	| Optional. Available options are 'bottom' or 'top'	|
| offset     	| integer	| 100		| Optional. Set the scrolling offset for each step	|
| position     	| string	| absolute	| Optional. Available options are 'fixed' or 'absolute'. This is handy for fixed elements	|

An example could be:
```js
var tour = {
    steps: [
        {
            element: 'idOfTheElement',
            text: 'Her you add some text to this step',
            position: 'fixed', // good for fixed header elements or floating action buttons
            direction: 'top' // shows the text above the highlighed area
        }
    ]
};
```


The font
--------
No specific fonts are set with this plugin. This is so each programmer can more easily adapt this plugin to their projects. If you want the truly material feel you'll have to include the 'Roboto' font your self from Google fonts.
