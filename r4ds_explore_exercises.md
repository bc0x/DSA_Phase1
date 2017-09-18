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

### 3.7.1

### 3.8.1

### 3.9.1