## Nutrition Tracker
This example illustrates how to make a semi-complex list with rich formatting using jQuery Mobile.
jQuery Mobile provides some classes to assist with making a custom list but additional css will be required.
To demonstrate how to build a custom list, we are going to create the list-view of a Nutrition Tracking application.

This is what we want to achieve when we are finished.
![Nutrition Tracking App - Final Product](https://github.com/blackberry/jQuery-Mobile-Samples/raw/master/NutritionTracker/figures/final.png)

First, we will need to create an empty list-view

```html
    <ul data-role="listview">
    </ul>
```

Next, we will add the list-divider, the blue area at the top of the page in the above figure.

```html
    <ul data-role="listview">
        <li data-role="list-divider">
            <h1> Description</h1>
            <span>Calories</span>
            <span>Carbs</span>
            <span>Fat</span>
            <span>Protein</span>
            <span>Sugar</span>
            <span>Sodium</span>
        </li>
    </ul>
```

This produces the following image, which is not quite what we were looking for.
 
![Nutrition Tracking App - list-divider 1](https://github.com/blackberry/jQuery-Mobile-Samples/raw/master/NutritionTracker/figures/list-divider.png)

To fix this we must add some custom classes.

```html
    <style type="text/css" media="screen">
        .fact {
            width: 10%;
            display: inline-block;
            text-align: center;
            text-overflow: ellipsis;
            overflow: hidden;
        }
        .fact.factDescription {
            width: 33%;
            text-align: left;
        }
    </style>
```

Both fact and factDescription use a percentage as their width. This will ensure the correct formatting on all screen resolutions.
Now apply the new classes to the elements.

```html
     <ul data-role="listview">
        <li data-role="list-divider">
            <h1 class="fact factDescription">Description</h1>
            <span class="fact">Calories</span>
            <span class="fact">Carbs</span>
            <span class="fact">Fat</span>
            <span class="fact">Protein</span>
            <span class="fact">Sugar</span>
            <span class="fact">Sodium</span>
        </li>
    </ul>
```

We now have our list-divider looking correctly. 

![Nutrition Tracking App - list-divider 2](https://github.com/blackberry/jQuery-Mobile-Samples/raw/master/NutritionTracker/figures/final-list-divider.png)

Now, we must add a list item. It will follow the same structure as our list-divider.

```html
    <li>
        <h1>Kamut Puffs</h1>
        <p class="fact factDescription">1 cup 16g</p>
        <span class="fact">50</span>
        <span class="fact">11</span>
        <span class="fact">0</span>
        <span class="fact">2</span>
        <span class="fact">0</span>
        <span class="fact">0</span>
    </li>
```

The next steps would be to add more items and ideally to template these items with your favorite template engine such as [handlebars](http://handlebarsjs.com/) or the [jquery plugin](http://api.jquery.com/category/plugins/templates/)  
