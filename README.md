# To the Reviewer:
You may view a live version of the page at the following link: https://markhorvath.github.io/weboptimization/
You may also review it using ngrok.

##OPTIMIZATION STEPS:

###INDEX.HTML:

1. Moved `<script async src="http://www.google-analytics.com/analytics.js"></script>` to the bottom after `</body>` and added `async`.
2. Added `<style>` tag in the `<head>` and moved style.css markup instead of linking to it using `<link href>`.
3. Used `@font-face` in `<style>` to call on specific google API fonts.

###MAIN.JS:

1. changePizzaSizes function was simplified to remove for loop bottlenecks and unnecessarily complex determineDx function.  This reduced the pizza resize time to under 5ms.
2. Reduced the number of iterations in the for loop to 40 for the pizza animations while scrolling.
3. Created a variable for the ID movingPizzas1 and used it in the for loop instead of using querySelector each time.
4. Cached items variable outside of updatePositions() so it doesn't have to access the DOM each time and used getElementByClassName instead of querySelectorAll.
5. Reduced the number of pizzas on page load to 48.
6. Created variable for scroll position outside of for loop to avoid repeated calculation.
7. Created phases array and pushed the 5 possible values for it outside of the "position change" for-loop in updatePositions().
8. Created length variable to calculate items.length outside of the "position change" for-loop in updatePositions().
9. Calculate phases[(i%5)] instead of creating a new phase variable
