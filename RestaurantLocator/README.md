## Restaurant Locator
This example is to illustrate how to make a semi-complex list with rich formatting using jQuery Mobile. jQuery Mobile provides some classes to assist with making a custom list but additional css will be required. To demonstrate how to build a custom list we are going to create the list-view of a Restaurant Locator application.

The idea behind this Restaurant Locator is that we want to present the user
with a list of nearby restaurants to which they may like to go.

```html
    <ul data-role='list-view'>
        <li><a>Maman's Bakery</a></li>
        <li><a>West-End Deli</a></li>
    </ul>
```

We can just leave it like this and force the user to click each item to find out more.
Instead, lets present the user with more information to make a better decision.

Information needed for a Restaurant Locator

* Rating
* Price
* Distance
* Type of cuisine
* Name
* Address

The order of importance may be different for all users but these are the main factors we will use to help them choose.
This may seem like a lot of information for a list item on a mobile screen but fortunately jQuery Mobile gives us some tools to help display it in a usable way.
Lets put all of the information elements we are using into a semantic order.

```html
    <ul data-role='listview'>
        <li>
            <h1>Maman's Bakery</h1>
            <p>This french style bakery will leave you dreaming of Paris</p>
            <p>1523 Main St., Toronto</p>
            <p>Categories: French, Bakery, Pastries</p>
            <p>3.1 km N</p>
            <p>$</p>
            <p>3 stars</p>
            <span>50 reviews</span>
        </li>
    </ul>
```

To any ```h1, h2, h3, h4, h5``` that jQuery Mobile finds inside the ```li```, it will apply ```ui-li-heading```.
Also, to any ```p```, jQuery Mobile will apply ```ui-li-desc```.

This produces the below image which has all the information we have but but no visual appeal.

![Restaurant Locator App - Semantic List Item](https://github.com/blackberry/jQuery-Mobile-Samples/raw/master/RestaurantLocator/figures/list-item-noFormatting.png)

Lets change things by moving the distance, price, rating and reviews information to the right.
We do that placing each of them in a ```div``` with the class ```ui-li-aside```.

```html
    <ul data-role='listview'>
        <li>
            <h1>Maman's Bakery</h1>
            <p>This french style bakery will leave you dreaming of Paris</p>
            <p>1523 Main St., Toronto</p>
            <p>Categories: French, Bakery, Pastries</p>
            <div class='ui-li-aside'>
                <p>3.1 km N</p>
                <p>$</p>
                <p>3 stars</p>
                <span>50 reviews</span>
            </div>
        </li>
    </ul>
```
Already looking better, but still more work to do.

![Restaurant Locator App - aside](https://github.com/blackberry/jQuery-Mobile-Samples/raw/master/RestaurantLocator/figures/list-item-aside.png)

Next we will replace "3 stars" with 3 actual stars.
This will only work in jQuery Mobile 1.1.1+
For this we will make use of the star icon that can be applied to buttons.
Since we do not want a button, we will only make use of its css classes ```ui-icon-star``` and  ```ui-icon```.
We will create an empty ```span``` for each star in the restaurant's rating.
So our code should look like this for our 3 star bakery:

css:

```css
    .ui-li-aside span {
        float: right;
    }
```
html:

```html
    <ul data-role='listview'>
        <li>
            <h1>Maman's Bakery</h1>
            <p>This french style bakery will leave you dreaming of Paris</p>
            <p>1523 Main St., Toronto</p>
            <p>Categories: French, Bakery, Pastries</p>
            <div class='ui-li-aside'>
                <p>3.1 km N</p>
                <p>$</p>
                <span>50 reviews</span>
                <span class="ui-icon-star ui-icon"></span>
                <span class="ui-icon-star ui-icon"></span>
                <span class="ui-icon-star ui-icon"></span>
            </div>
        </li>
    </ul>
```

![Restaurant Locator App - stars](https://github.com/blackberry/jQuery-Mobile-Samples/raw/master/RestaurantLocator/figures/list-item-withStars.png)

Currently the list item is read-only and not selectable.
Next, we will make the list items selectable so that the user can get more information about the restaurant.
To do this, we wrap the entire contents of the list item with an ```a```.

```html
    <ul data-role='listview'>
        <li><a href='#'>
            <h1>Maman's Bakery</h1>
            <p>This french style bakery will leave you dreaming of Paris</p>
            <p>1523 Main St., Toronto</p>
            <p>Categories: French, Bakery, Pastries</p>
            <div class='ui-li-aside'>
                <p>3.1 km N</p>
                <p>$</p>
                <span>50 reviews</span>
                <span class="ui-icon-star ui-icon"></span>
                <span class="ui-icon-star ui-icon"></span>
                <span class="ui-icon-star ui-icon"></span>
            </div>
        </a></li>
    </ul>
```

![Restaurant Locator App - Clickable](https://github.com/blackberry/jQuery-Mobile-Samples/raw/master/RestaurantLocator/figures/list-item-clickable.png)

That is it for jQuery Mobile specific tricks for this tutorial. Lets clean the rest up with standard html and css.

Todo:

* Make the Distance and Price larger
* Add color to the different categories
* Fix spacing

```css
    div.ui-li-aside {
        float: right;
        margin: 0 1em;
    }
    .ui-li-aside span {
        float: right;
    }
    .address {
        margin-left: 1em;
        margin-bottom: 1.5em;
    }
    .categories {
        color: coral;
    }
    .rating {
        margin-left: .3em;
    }
    .divider {
        margin-top: .1em;
    }
```

```html
    <ul data-role="listview">
        <li><a href="#">
            <h1>Maman's Bakery<hr class='divider'></h1>
            <p>This french style bakery will leave you dreaming of Paris</p>
            <p class="address">1523 Main St, Toronto</p>
            <p>Categories: <span class='categories'>French, Bakery, Pastries</span></p>
            <div class="ui-li-aside">
                <h3>3.1 km NW</h3>
                <h4>$</h4>
                <span class='rating'>50 reviews</span>
                <span class="ui-icon-star ui-icon"></span>
                <span class="ui-icon-star ui-icon"></span>
                <span class="ui-icon-star ui-icon"></span>
            </div>
        </a></li>
    </ul>
```

Our final product:

![Restaurant Locator App - Clickable](https://github.com/blackberry/jQuery-Mobile-Samples/raw/master/RestaurantLocator/figures/list-item-final.png)

The full complete source is available at https://github.com/blackberry/jQuery-Mobile-Samples/tree/master/RestaurantLocator

