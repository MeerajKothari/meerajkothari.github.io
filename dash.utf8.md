---
title: "Instacart Dashboard"
output: 
  flexdashboard::flex_dashboard:
    orientation: columns
    vertical_layout: fill
    theme: journal
---



Column {data-width=650}
-----------------------------------------------------------------------

### Distribution of order time for each department


```r
data(instacart)
x <- list(
  title = "Department"
)
y <- list(
  title = "Order Hour of Day"
)

instacart %>% 
  group_by(department) %>%
  plot_ly(x = ~department, y = ~order_hour_of_day, color = ~department, type = "box") %>%
  layout(xaxis = x, yaxis = y)
```

```
## Warning in RColorBrewer::brewer.pal(N, "Set2"): n too large, allowed maximum for palette Set2 is 8
## Returning the palette you asked for with that many colors

## Warning in RColorBrewer::brewer.pal(N, "Set2"): n too large, allowed maximum for palette Set2 is 8
## Returning the palette you asked for with that many colors
```

preservebdd6ec1ae354c9b7

Column {data-width=350}
-----------------------------------------------------------------------

### Number of items ordered in each department


```r
x <- list(
  title = "Department"
)
y <- list(
  title = "Count"
)

instacart %>% 
  count(department) %>%
  mutate(department = fct_reorder(department, -n)) %>%
  plot_ly(x = ~department, y = ~n, color = ~department) %>%
  layout(xaxis = x, yaxis = y)
```

```
## No trace type specified:
##   Based on info supplied, a 'bar' trace seems appropriate.
##   Read more about this trace type -> https://plot.ly/r/reference/#bar
```

```
## Warning in RColorBrewer::brewer.pal(N, "Set2"): n too large, allowed maximum for palette Set2 is 8
## Returning the palette you asked for with that many colors

## Warning in RColorBrewer::brewer.pal(N, "Set2"): n too large, allowed maximum for palette Set2 is 8
## Returning the palette you asked for with that many colors
```

preserve9bf749480ced898b

### Number of items ordered during each day of the week


```r
x <- list(
  title = "Order Hour of Day"
)
y <- list(
  title = "Count"
)

instacart %>% 
  mutate(order_dow = factor(order_dow, c(0, 1, 2, 3, 4, 5, 6), c("Day 0", "Day 1", "Day 2", "Day 3", "Day 4", "Day 5", "Day 6"))) %>%
  group_by(order_dow) %>%
  count(order_hour_of_day) %>% 
  plot_ly(x = ~order_hour_of_day, y = ~n, color = ~order_dow, type = "scatter", mode = "lines") %>%
  layout(xaxis = x, yaxis = y)
```

preserved1a354f9071dd73e

