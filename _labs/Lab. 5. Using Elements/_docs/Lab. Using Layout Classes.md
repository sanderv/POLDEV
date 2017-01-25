## Lab 1. Basic Setup
In this lab you will create a better page layout using the application we've just built. 
> duration: 30 minutes

### Step 1. Add iron-layout-classes
Open file 'index.html' inside your current folder. If the exercise was not completed successfully in the last
lab, you can copy and paste a version from the _solution folder from the last exercise.

Download and add iron-elements to the project using the following command:
```
$ bower install iron-elements
```

Add the iron-layout-classes html import to the head of the page:
```
<head>
    ...
    <link rel="import" href="./bower_components/iron-flex-layout/iron-flex-layout-classes.html">
</head>
```

Give the body tag of your page a class with the value fullbleed". This takes care
of deleting the margins of the body.

Add a global container and three sub containers to the template of your app and
give them class qualifiers that make up a solid page layout. Here is an example
of how you COULD implement this layout:

```html
<div class="layout vertical">
    <div class="header">...header ...</div>
    <div class="content flex">...candidates and votes ...</div>
    <div class="footer">...election results ...</div>
</div>
```

Note that to get the benefits of the flexible sized content, you need to specify
that the body or container spans the whole height of the page (height:100%).

Save your files. Run 'lite-server' with the following command:
```
$ lite-server
```

If all went well, you should see a better layout for your application.


### Step 2. Fix minor css issues
The applation works and has a better layout, but what happens when the vote-list gets to long?
Try to make the application better and better looking using CSS and theming. 

Some hints:
- get rid of the page scrolling and make the content pane scroll when overflown.
- give the header and the footer a different background

### Extra Exercise (only for the 5-day course)
Go to the site https://www.materialpalette.com/ and apply your styles to the site.
Refactor the application to implement variables for styling and use the shared style you've just downloaded
to supply the theme values for the application.

The final solution in the _solution folder contains a fully working example, compare your 
results with the  files from the solution.

### Summary
We've used iron-layout-classes to define a page layout. 
The app works but is not accoring to material-design specs, does not persist its data and is not
offline capable. We still have work to do.


-= End of lab =-
  
