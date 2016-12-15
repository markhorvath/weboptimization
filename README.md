# To the Reviewer:
You may view a live version of the page at the following link: https://markhorvath.github.io/weboptimization/
You may also review it using the following steps:
1. Download or clone the github repo at https://github.com/markhorvath/weboptimization
2. If you need to download and install ngrok, a guide can be found here https://ngrok.com/download
3. In your terminal, make your way to the top level of the frontend-nanodegree-mobile-portfolio-master directory.
4. Create a simple server using Python by typing "python -m SimpleHTTPServer 8080"
5. In a new terminal tab and in the same top level of the directory, type "./ngrok http 8080"
6. Copy and paste the url provided by ngrok onto Google PageSpeed Insights at https://developers.google.com/speed/pagespeed/insights/.
7. To test the pizza slider and animation time, you can navigate using the "Cam's Pizzeria" link in index.html, or open the page directly by add views/pizza.html at the end of url.

##OPTIMIZATION STEPS:

###INDEX.HTML:

1. Moved `<script async src="http://www.google-analytics.com/analytics.js"></script>` to the bottom after `</body>` and added `async`.
2. Added `<style>` tag in the `<head>` and moved style.css markup instead of linking to it using `<link href>`.
3. Used `@font-face` in `<style>` to call on specific google API fonts.
4. Reduced pizzeria.jpg and created two versions: a 30KB one for index.html and a 120KB 360x270 one for views/pizza.html.

###MAIN.JS:

1. changePizzaSizes function was simplified to remove for loop bottlenecks and unnecessarily complex determineDx function.  This reduced the pizza resize time to under 5ms.
2. Determined the number of moving pizzas based on the user's screen height and applied it to page load function.
3. Created a variable for the ID movingPizzas1 and used it in the for loop instead of using querySelector each time.
4. Cached items variable outside of updatePositions() so it doesn't have to access the DOM each time and used getElementByClassName instead of querySelectorAll.
5. Created variable for scroll position outside of for loop to avoid repeated calculation.
6. Created phases array and pushed the 5 possible values for it outside of the "position change" for-loop in updatePositions().
7. Created length variable to calculate items.length outside of the "position change" for-loop in updatePositions().
8. Calculate phases[(i%5)] instead of creating a new phase variable
9. Created pizzaSizeElem inside resizePizzas and outside of changeSliderLabel function and used getElementById method instead of querySelector.
