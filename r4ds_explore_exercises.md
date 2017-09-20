# R for Data Science: Introduction and Explore

<!-- TOC -->

- [R for Data Science: Introduction and Explore](#r-for-data-science-introduction-and-explore)
  - [Chapter 3: Data Visualisation](#chapter-3-data-visualisation)
    - [3.2.4](#324)
    - [3.3.1](#331)
    - [3.5.1](#351)
    - [3.6.1](#361)
    - [3.7.1](#371)
    - [3.8.1](#381)
    - [3.9.1](#391)
  - [Chapter 4: Workflow: basics](#chapter-4-workflow-basics)
    - [4.4](#44)
  - [Chapter 5: Data Transformation](#chapter-5-data-transformation)
    - [5.2.4](#524)
    - [5.3.1](#531)
    - [5.4.1](#541)
    - [5.5.2](#552)
    - [5.6.7](#567)
    - [5.7.1](#571)

<!-- /TOC -->

## Chapter 3: Data Visualisation

### 3.2.4

1. An empty graph
1. 234x11 -- dim(mpg)
1. The car's drivetrain type (fwd, rwd, 4wd)
1. ```ggplot(data = mpg) + geom_point(mapping = aes(x = cyl, y = hwy))```
1. The scatterplot overlaps so you can't infer anything. They overlap because they are categorical variables.

### 3.3.1

1. Color is on the inside of aes instead of an argument ```ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy), color = "blue")```
1. Categorical: manufacturer, model, trans, drv, fl, class. Continuous: displ, cyl, year, cty, hwy. Categorical variables are usually type ```<chr>```
1. The aesthic is a range (for size and color) since it's a continuous variable as opposed to being set to a specific instance of a size or color. For shape, we get an error because it would require some type of shape range, which doesn't make sense.
1. It still works, and both the aesthics are applied to the variable.
1. Stroke increases the thickness of the shape used in mapping
1. We get a True/False color represtation for each instace that elvaluates against ```displ > 5```

### 3.5.1

1. You will get a plot/facet for each value of the continuous variable. This creates a lot of graph and is hard to decipher the data.
1. It tells us there are no vechicles at that intersection. For the formula provided, there are no 5 cylinder and 4wd/rwd combinations.
1. ```facet_grid(drv ~ .)``` this shows us the hwy mpg in relation to displ with facet rows separated by drv. ```facet_grid(. ~ cyl)``` this shows us the hwy mpg in relation the displ with facet columns. The ```.``` is a placeholder for no variable, so we get rows are columns instead of a X by X grid.
1. Faceting will split the data into separate grids to see outliers/commonality within each grid. However, this takes away the ability to really compare the relations between the entire dataset since you are splitting out. Using a color aesthetic will work, but once you have a large enough data set the readability will decrease dramatically without facets.
1. ```nrow``` and ```ncol``` set how rows and columns the faceted plot with have respectively. Both ```as.table``` ```dir``` can both controll the layout.
1. You should use it as a columns so the plots are not compact. Using it as a columns allows for more room on the y axis.

### 3.6.1
1. Answers:
    1. Line - geom_line()
    1. Boxplot - geom_boxplot()
    1. Histogram - geom_histogram()
    1. Area - geom_area()
1. Ummmm?
1. It removes the key that describes the aeshetic mappings. I don't know why you would remove it.
1. Displays confidence interval around smooth line. It is true by default.
1. No, they are the same because the arguments are passed down from ggplot.
1. Answers:
    1. ```ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + geom_point() + geom_smooth(se = FALSE)```
    1. ```ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + geom_smooth(aes(group = drv), se = FALSE) + geom_point()```
    1. ```ggplot(data = mpg, mapping = aes(x = displ, y = hwy, color = drv)) + geom_point() + geom_smooth(se = FALSE)```
    1. ```ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + geom_point(aes(color = drv)) + geom_smooth(se = FALSE)```
    1. ```ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + geom_point(aes(color = drv)) + geom_smooth(aes(linetype = drv), se = FALSE)```
    1. ```ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + geom_point(size = 4, colour = "white") + geom_point(aes(color = drv))```

### 3.7.1

1. pointrange; ```ggplot(data = diamonds) + geom_pointrange(mapping = aes(x = cut, y = depth), stat = "summary", fun.ymin = min, fun.ymax = max, fun.y = median)```
1. geom_col uses the identity stat, but geom_bar uses the count stat.
1. TODO
1. Answers:
    1. y
    1. ymin
    1. ymax
    1. se
1. The proportion is calculated over the whole set of data, instead of each group of cut.

### 3.8.1

1. Many of the points overlap, so we should use geom_jitter().
1. The width and height
1. Jitter adds randomness to represent stacked points where count will add weight/size to each point to represent the stacked points.
1. The defauly position is dodge; ```ggplot(data = mpg, mapping = aes(x = class, y = hwy, color = drv)) + geom_boxplot()```

### 3.9.1

1. ```ggplot(data = diamonds, mapping = aes(x = 1, fill = clarity)) + geom_bar() + coord_polar(theta = "y")```
1. Labs allows you to modify axis, legend, and plot labels.
1. coord_map projects a portion of the earth, which is approximately spherical, onto a flat 2D plane using any projection defined by the mapproj package. Map projections do not, in general, preserve straight lines, so this requires considerable computation. coord_quickmap is a quick approximation that does preserve straight lines. It works best for smaller areas closer to the equator.
1. The mapping of cty vs hwy is linear and that hwy is usually higher than cty miles. coord_fixed makes sure that the a unit on the x and y axes are the same length. You can see this by changing ratio to 2. geom_abline adds reference lines (sometimes called rules) to a plot, either horizontal, vertical, or diagonal (specified by slope and intercept). These are useful for annotating plots.

## Chapter 4: Workflow: basics

### 4.4

1. my_variable is not spelled correctly when printing to the screen.
1. Answers
    1. This is correct.
    1. ```ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy))```
    1. ```filter(mpg, cyl = 8)```
    1. ```filter(diamonds, carat > 3)```
1. A list of keyboard shortcuts is displayed. Help > Keyboard Shortcuts Reference.

## Chapter 5: Data Transformation

### 5.2.4

### 5.3.1

### 5.4.1

### 5.5.2

### 5.6.7

### 5.7.1