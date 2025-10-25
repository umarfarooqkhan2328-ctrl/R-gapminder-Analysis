# R-gapminder-Analysis
# 🌍 Gapminder Data Analysis in R

## 📘 Project Overview
This project explores the **Gapminder dataset**, which includes data about countries' **life expectancy, GDP per capita, population**, and **continent** over time.  
The goal is to analyze global development trends, visualize relationships, and perform basic statistical tests using **R**.

---

## Packages Used
```R
install.packages("gapminder")
install.packages("dplyr")
install.packages("ggplot2")
library(gapminder)
library(dplyr)
library(ggplot2)
```
## Data Exploration

```R
data("gapminder")
head(gapminder)
summary(gapminder)

x <- mean(gapminder$gdpPercap)
attach(gapminder)
median(pop)
```
- head() displays the first few rows of the dataset.

- summary() gives statistical summaries of all variables.

- mean() and median() compute average GDP per capita and median population.

## Data Visualization

```R
hist(lifeExp)
hist(log(pop))

boxplot(lifeExp ~ continent)
plot(lifeExp ~ log(gdpPercap))
```

- Histograms show the distribution of life expectancy and population.

- Boxplot compares life expectancy across continents.

- Scatter plot shows how life expectancy relates to GDP per capita (log-scaled).

## Statistical Test:

```R
df1 <- gapminder %>%
  select(country, lifeExp) %>%
  filter(country == "South Africa" | country == "Ireland")

t.test(data = df1, lifeExp ~ country)
```

- Filters data for South Africa and Ireland.

- Performs a t-test to compare average life expectancy between the two countries.

## Advanced Visualization:

```R
gapminder %>%
  filter(gdpPercap < 50000) %>%
  ggplot(aes(x = log(gdpPercap), y = lifeExp, col = year, size = pop)) +
  geom_point(alpha = 0.3) +
  geom_smooth(method = lm) +
  facet_wrap(~continent)
```
- Filters out countries with very high GDP per capita.

- Creates a scatter plot with regression lines for each continent.

- Color indicates year, and point size represents population.


## Regression Model:
```R
summary(lm(lifeExp ~ gdpPercap + pop))
```
Builds a linear regression model to predict life expectancy from GDP per capita and population.

## Key Insights:

- Life expectancy generally increases with GDP per capita.

- African countries show lower life expectancy on average.

- Economic growth and health outcomes are closely related but vary by region.
