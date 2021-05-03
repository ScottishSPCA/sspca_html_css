# Intro to CSS

> Note: We continue with the code from the end of the previous lesson.

## What is CSS?

CSS stands for Cascading Style Sheets - it's a style sheet language that helps with the layout and presentation of a given document. It is cascading because the different elements will get their styling from their parent elements - like a waterfall cascading down. 

We have a lot of ways to add CSS to our website - we can write CSS in the same file, we can even add styling directly to our HTML tags. However, these methods are frowned upon - they make handling and writing CSS very messy, so we prefer keeping our style changes in a separate file.

Let's start by creating this file!

In VSCode, click on the new file icon, or right click next to our index.html file and select New File, and name our file `style.css` - this is conventional.

> Note: If you accidentally created the file not in the same place as the index.html file, you can drag & drop it in next to it

Double click on the file to open it up!

## How to write CSS

When we are writing CSS, we need to keep something in mind: We need to decide what should we target when we style things. We can apply styling to very specific elements, or use broad targeting to apply style to large sections of our HTML.

Let's say we want to change the text color for our header that says WildLife Project. How can we do that? We can tell in our CSS file that we want to apply the color for a specific tag.

Our header with the pawprints is inside the `<h1>` tag, so let's tell CSS to change colour there!

```css
h1 {
    color: palevioletred;
}
```

If we refresh our website, nothing changes however! What could be the problem?

We need to tell our HTML file to load in the CSS file, otherwise it does not know where to look for it!

Remember, the computer can only follow our instructions - it will not figure things out on its own!

In our `my_first_webpage.html` file, let's add the following line in the `<head>` tag:

```html
<head>
    <!-- Same as before -->
    <link rel="stylesheet" href="style.css">
</head>
```

Now we can refresh the webpage, and our `<h1>` logo should have our new colour to it!

> Note: There are many ways to select colours for CSS - a lot of colours are default, and can be selected with their names. Try changing the word `palevioletred` to words like `red`, `yellow`, or even `salmon`, `wheat`, or `tomato`!

Now that we can change colours, let's change other things! Let's make our logo bigger, by adding the following line to our `<h1>` tag's CSS!

```css
h1 {
    color: palevioletred;
    font-size: 48px;
}
```

This will increase our logo size - we can easily change to however big or small we want.

But what happens if we want to change the size of the links in our navigation bar? - we need to target it!

There are many ways to target HTML elements - we will learn one of the simpler ones. If we know that the link can be found in the `<a>` tags, we can say in our CSS to increase the font size of all `<a>` tags!

```css
/* As before */

a {
    font-size: 32px;
}
```
After refreshing the page, we can see that only the text in the links have changed.

## Styling our navigation

In order to make our navigation bar look good, we want to remove some things from the links, like the colours, and the underlines. We can do this by adding the following to our `<a>` tag styling:

```css
/* As before */

a {
    font-size: 24px;
    text-decoration: none;
    color: black;
}
```

But we still have the dots before them! Why?

Because the dots are not part of the link's styling - it's the `<li>` element's styling! So to remove it, we need to change that tag!

```css
/* As before */

li {
    text-decoration: none;
}
```

Alright, we are slowly shaping up. Next, we want all our navigation buttons to be next to each other. 10-15 years ago, this could've taken us hours to do - luckily, there's a little trick we can do to make it super easy, using something called Flexbox!

In order to put thing next to each other, we have to change things in the tag that contains all tags we want to place next to each other. So if we want our `<li>` elements to go next to each other, we need to target our `<ul>` element:

```css
/* As before */
ul {
    display: flex;
    justify-content: space-evenly;
}
```

display: flex makes sure we can put things next to each other easily, while justify-content let's us decide if we want things spaced out evenly.

This looks much better already! But everything is forced to move to the left hand side.

Since I want to center everything on the website, we can tell the `<body>` tag to center the text everywhere:

```css
/* As before */
body {
    display: flex;
    justify-content: space-evenly;
}
```


Now we only need to keep adding more `<section>` tags, with more videos, headers, images and text. Let's see an example!

In our html file, we will add another section:

```html
<main>
        <section>
            <h2>Muppets - Bohemian Rhapsody</h2>
            <p>This video is pretty fun!</p>
            <iframe width="420" height="315" src="https://www.youtube.com/embed/tgbNymZ7vqY"></iframe>   
        </section>

        <section> 
            <h2>Another great video!</h2>
            <p>This video is even better!</p>
            <iframe width="420" height="315" src="https://www.youtube.com/embed/SoZiZE2Zcng"></iframe>
        </section>
    </main>
```

To separate every section from each other, we can add some styling to them.

```css
section {
    width: 50%;
    margin: auto;
    padding: 50px;
}
```

Width: 50% makes it take up only half of the screen's size, margin: auto helps with centering it, and padding puts some space around the sections, so they won't be so close to each other.

This is great for styling all the sections. However, if I target a `<section>` tag in my CSS file, all my section tags will be changed, but what if I don't want this? What if I want to target elements individually?

One solution is that I can give my html tags classes! This way I can target them one by one!

```html
<main>
        <section>
            <h2>Muppets - Bohemian Rhapsody</h2>
            <p>This video is pretty fun!</p>
            <iframe width="420" height="315" src="https://www.youtube.com/embed/tgbNymZ7vqY"></iframe>   
        </section>

        <section class="new-section">  [UPDATED]
            <h2>Another great video!</h2>
            <p>This video is even better!</p>
            <iframe width="420" height="315" src="https://www.youtube.com/embed/SoZiZE2Zcng"></iframe>
        </section>
    </main>
```

This can be named anything I want it to be, doesn't have to be new-section - but it must be the same name in both the html and the css file!
Once I give the section a new class name, I can use it in my CSS file - but I must add a `.` before the name of the class to target it.

Let's add the following to our CSS file:

```css
/* As before */
.new-section {
    background-color: lightgrey;
}
```

And now only my new section gets the styling!

> Task: Let the students play around with background colours and text colours to find one that's easy to read! Try to talk about good contrast: [Colour theory](https://www.uxmatters.com/mt/archives/2007/01/applying-color-theory-to-digital-displays.php)