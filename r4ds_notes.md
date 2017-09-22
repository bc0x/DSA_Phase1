# Chapter 3 Notes

Mapping Template

    ggplot(data = <DATA>) + 
      <GEOM_FUNCTION>(mapping = aes(<MAPPINGS>))

A variable is a quantity, quality, or property that you can measure.

A variable is categorical if it can only take one of a small set of values. In R, categorical variables are usually saved as factors or character vectors

A variable is continuous if it can take any of an infinite set of ordered values. Numbers and date-times are two examples of continuous variables

A value is the state of a variable when you measure it. The value of a variable may change from measurement to measurement.

An observation is a set of measurements made under similar conditions (you usually make all of the measurements in an observation at the same time and on the same object). An observation will contain several values, each associated with a different variable. I’ll sometimes refer to an observation as a data point.

Tabular data is a set of values, each associated with a variable and an observation. Tabular data is tidy if each value is placed in its own “cell”, each variable in its own column, and each observation in its own row.

Covariation is the tendency for the values of two or more variables to vary together in a related way. The best way to spot covariation is to visualise the relationship between two or more variables.