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
  - [Chapter 6: Workflow: scripts](#chapter-6-workflow-scripts)
    - [6.3](#63)
  - [Chapter 7: Exploratory Data Analysis](#chapter-7-exploratory-data-analysis)
    - [7.3.4](#734)
    - [7.4.1](#741)
    - [7.5.1.1](#7511)
    - [7.5.2.1](#7521)
    - [7.5.3.1](#7531)

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

1. Answers:
    1. ```filter(flights, arr_delay >= 120)```
    1. ```filter(flights, dest == "IAH" | dest == "HOU")```
    1. ```filter(flights, carrier == "UA" | carrier == "AA" | carrier == "DL")```
    1. ```filter(flights, month %in% c(7, 8, 9))```
    1. ```filter(flights, arr_delay >= 120, dep_delay <= 0)```
    1. ```filter(flights, dep_delay >= 60, dep_delay - arr_delay > 30)```
    1. ```filter(flights, dep_time >=0, dep_time <= 600)```
1. ```filter(flights, month %in% c(7, 8, 9))``` goes to ```filter(flights, between(month, 7, 9))```
1. 8,255; 
1. Answers:
    1. Anything to power of 0 is 1
    1. Because it has an or with true
    1. Becuase it has an and with false
    1. Anything with operations is NA unless you raise it to power 0. With conditionals, the value associated with NA is looked at depending on the rest of the expression.

### 5.3.1

1. ```arrage(flights, !is.na(VAR_NAME))```
1. ```arrange(flights, desc(arr_delay))``` and ```arrange(flights, dep_delay)```
1. ```arrange(flights, air_time)```
1. ```arrange(flights, desc(distance))``` and ```arrange(flights, distance)```

### 5.4.1

1. Answers:
    1. ```select(flights, dep_time, dep_delay, arr_time, arr_delay)```
    1. ```select(flights, starts_with("dep"), starts_with("arr"))```
    1. ```select(flights, one_of(c("dep_time", "dep_delay", "arr_time", "arr_delay")))```
1. It is ignored and only shown once.
1. It matches the vars defined in the vector.
1. It matcheds regarless of case by default. You can set ignore.case = FALSE.

### 5.5.2

1. ```mutate(flights, sched_dep_time_min = (sched_dep_time %/% 100) * 60 + sched_dep_time %% 100, dep_time_min = (dep_time %/% 100) * 60 + dep_time %% 100)```
1. They are not equal becuase the times have not be converted like above. We need to convert to minutes.
1. dep_time should be equal to the delay plus scheduled departure time if the vars are converted.
1. mutate(flights, delayed = min_rank(desc(arr_delay)))
1. Answers: 
    1. ```test <- mutate(flights, delayed = min_rank(desc(arr_delay)))``` then ```arrange(test, delayed)```
    1. The ties.method is set to min so if something is equal they will have the same rank.
1. cos(x), sin(x), tan(x), acos(x), asin(x), atan(x), atan2(y, x), cospi(x), sinpi(x), tanpi(x)

### 5.6.7

1. Answers:
    1. ```flights %>% group_by(flight) %>% summarise(early = sum(arr_delay <= -15, na.rm = TRUE) / n(), late = sum(arr_delay >= 15, na.rm = TRUE) / n()) %>% filter(early == .5, late == .5)```
    1. ```flights %>% group_by(flight) %>% summarise(late = sum(arr_delay == 10, na.rm = TRUE) / n()) %>% filter(late == 1)```
    1. ```flights %>% group_by(flight) %>% summarise(early = sum(arr_delay <= -30, na.rm = TRUE) / n(), late = sum(arr_delay >= 30, na.rm = TRUE) / n()) %>% filter(early == .5, late == .5)```
    1. ```flights %>% group_by(flight) %>% summarise(ontime = sum(arr_delay == 0, na.rm = TRUE) / n(), late = sum(arr_delay >= 120, na.rm = TRUE) / n()) %>% filter(ontime == .99, late == .01)```
    1. The type of delay is subjective so I'm not sure you could say one is more important than the other.
1. Answers:
    1. ```not_cancelled %>% group_by(dest) %>% summarise(n = n())```
    1. ```not_cancelled %>% group_by(tailnum) %>% summarise(n = sum(distance, na.rm = TRUE))```
1. ```cancelled <- flights %>% filter(is.na(dep_delay))```
1. It looks like as the avg delay goes up there are more canceled flights that day.
    1. ```flights %>% group_by(day) %>% filter(is.na(dep_delay)) %>% summarise(n = n())```
    1. ```flights %>% group_by(day) %>% summarise(n = n(), cancelled = sum(is.na(dep_delay)) / n(), delay = mean(dep_delay, na.rm = TRUE))```
1. F9 has the worst delays ```flights %>% group_by(carrier) %>% summarise(avgDelay = mean(dep_delay, na.rm = TRUE)) %>% arrange(desc(avgDelay))```
1. Sorts is count results in desc order.

### 5.7.1

1. Not sure what section.
1. ```flights %>% group_by(tailnum) %>% summarise(overTime = mean(arr_delay, na.rm = TRUE), flights = n()) %>% arrange(flights, desc(overTime))```
1. It is better to fly in the morning so there is no delay. ```flights %>% group_by(hour) %>% summarise(delay = sum(arr_delay > 1, na.rm = TRUE) / n()) %>% arrange(., delay)```
1. Answers:
    1. ```flights %>% group_by(dest) %>% summarise(totalDelay = sum(arr_delay, na.rm = T)) %>% arrange(desc(totalDelay))```
    1. ```flights %>% group_by(dest) %>% filter(!is.na(arr_delay), arr_delay > 0) %>% mutate(destDelay = sum(arr_delay), propDelay = arr_delay / destDelay) %>% arrange(desc(propDelay))```
1. todo
1. todo
1. ```flights %>% group_by(dest) %>% filter(n_distinct(carrier) > 2) %>% group_by(carrier) %>% summarise(n = n_distinct(dest)) %>% arrange(desc(n))```
1. ```flights %>% group_by(tailnum) %>% mutate(row = row_number()) %>% filter(arr_delay >= 60) %>% summarize(hourDelay = first(row) - 1)```

## Chapter 6: Workflow: scripts

### 6.3

1. I checked out the twitter.
1. You enable several different types of repoting/warnings for R code. It also will show output for other languages like JavaScript. 

## Chapter 7: Exploratory Data Analysis

### 7.3.4

1. The x and the y most likely represnet the length and width of the top of the diamond, while  the z represnets the depth.
1. There are more diamonds at lower prices and less at higher prices. Also, there are a very low quantity be sold around $1500.
1. There are many more diamonds at 1 carat than .99. This is probably due to demand of 1 carat, and people like whole numbers.
1. xlim removes the dataset. coord_cartesian still uses the data. If binwidth is not set you it will split the data into 30 bins.

### 7.4.1

1. Histograms will omit the values. Bar charts will plot them as their own category.
1. It removes the missing vars from the calculation.

### 7.5.1.1

1. ```flights %>% mutate(cancelled = is.na(dep_time), sched_hour = sched_dep_time %/% 100, sched_min = sched_dep_time %% 100, sched_dep_time = sched_hour + sched_min / 60 ) %>% ggplot(aes(x = cancelled, y = sched_dep_time)) + geom_boxplot()```
1. Carat is the most important predictor for price. The lower quality diamond will be a larger carat leading to a higher price.
1. The order of the variables are flipped.
1. it looks like the width of the shape drawn repensents the frequency of cut at the price. You can see there are a lot less higher prices diamonds at every cut type.
1. With violin and greqpoly you have all the info in the same plot. It's harder to determine the count at each for each of those plots though. I like the faceted histogram becuase it is very easy to see the difference across the different cuts.
1. Answers:
    1. geom_quasirandom: Uses a van der Corput sequence or Tukey texturing (Tukey and Tukey "Strips displaying empirical distributions: I. textured dot strips") to space the dots to avoid overplotting.
    1. geom_beeswarm: Uses the beeswarm library to do point-size based offset.

### 7.5.2.1

1. You would take the proportion of color and cut over the total count, then fill the geomtile with that proportion.
1. The amount of destinations on the y axis make it hard to read.
1. When there are more categories, it is better to have them on the y axis.

### 7.5.3.1

1. cut_width will give you plots of the same width regardless of how many observations in each bin. cut_number will create bins of different width so they contain the correct number of bins provided.
1. ```ggplot(data = diamonds, mapping = aes(x = price, y = carat)) + geom_boxplot(mapping = aes(group = cut_number(price, 10))) + coord_flip()```
1. No, as size/price goes up the other factors of diamond quality proabaly affect the price more that at smaller sizes.
1. ```ggplot(diamonds, aes(x = cut, y = price, color = cut_number(carat, 10))) + geom_boxplot()```
1. So you can see the outliers easier.