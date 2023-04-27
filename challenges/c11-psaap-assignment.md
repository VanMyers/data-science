Regression Case Study: PSAAP II
================
Van Myers
2020-04-24

- <a href="#grading-rubric" id="toc-grading-rubric">Grading Rubric</a>
  - <a href="#individual" id="toc-individual">Individual</a>
  - <a href="#due-date" id="toc-due-date">Due Date</a>
- <a href="#orientation-exploring-simulation-results"
  id="toc-orientation-exploring-simulation-results">Orientation: Exploring
  Simulation Results</a>
  - <a href="#q1-perform-your-initial-checks-to-get-a-sense-of-the-data"
    id="toc-q1-perform-your-initial-checks-to-get-a-sense-of-the-data"><strong>q1</strong>
    Perform your “initial checks” to get a sense of the data.</a>
  - <a
    href="#q2-visualize-t_norm-against-x-note-that-there-are-multiple-simulations-at-different-values-of-the-input-variables-each-simulation-result-is-identified-by-a-different-value-of-idx"
    id="toc-q2-visualize-t_norm-against-x-note-that-there-are-multiple-simulations-at-different-values-of-the-input-variables-each-simulation-result-is-identified-by-a-different-value-of-idx"><strong>q2</strong>
    Visualize <code>T_norm</code> against <code>x</code>. Note that there
    are multiple simulations at different values of the Input variables:
    Each simulation result is identified by a different value of
    <code>idx</code>.</a>
  - <a href="#modeling" id="toc-modeling">Modeling</a>
    - <a
      href="#q3-the-following-code-chunk-fits-a-few-different-models-compute-a-measure-of-model-accuracy-for-each-model-on-df_validate-and-compare-their-performance"
      id="toc-q3-the-following-code-chunk-fits-a-few-different-models-compute-a-measure-of-model-accuracy-for-each-model-on-df_validate-and-compare-their-performance"><strong>q3</strong>
      The following code chunk fits a few different models. Compute a measure
      of model accuracy for each model on <code>df_validate</code>, and
      compare their performance.</a>
    - <a
      href="#q4-use-a-combination-of-eda-and-train-validation-error-to-build-a-model-by-selecting-reasonable-predictors-for-the-formula-argument-document-your-findings-under-observations-below-try-to-build-the-most-accurate-model-you-can"
      id="toc-q4-use-a-combination-of-eda-and-train-validation-error-to-build-a-model-by-selecting-reasonable-predictors-for-the-formula-argument-document-your-findings-under-observations-below-try-to-build-the-most-accurate-model-you-can"><strong>q4</strong>
      Use a combination of EDA and train-validation error to build a model by
      selecting <em>reasonable</em> predictors for the <code>formula</code>
      argument. Document your findings under <em>observations</em> below. Try
      to build the most accurate model you can!</a>
  - <a href="#contrasting-ci-and-pi"
    id="toc-contrasting-ci-and-pi">Contrasting CI and PI</a>
    - <a
      href="#q5-the-following-code-will-construct-a-predicted-vs-actual-plot-with-your-model-from-q4-and-add-prediction-intervals-study-the-results-and-answer-the-questions-below-under-observations"
      id="toc-q5-the-following-code-will-construct-a-predicted-vs-actual-plot-with-your-model-from-q4-and-add-prediction-intervals-study-the-results-and-answer-the-questions-below-under-observations"><strong>q5</strong>
      The following code will construct a predicted-vs-actual plot with your
      model from <em>q4</em> and add prediction intervals. Study the results
      and answer the questions below under <em>observations</em>.</a>
- <a href="#case-study-predicting-performance-ranges"
  id="toc-case-study-predicting-performance-ranges">Case Study: Predicting
  Performance Ranges</a>
  - <a
    href="#q6-you-are-consulting-with-a-team-that-is-designing-a-prototype-heat-transfer-device-they-are-asking-you-to-help-determine-a-dependable-range-of-values-for-t_norm-they-can-design-around-for-this-single-prototype-the-realized-value-of-t_norm-must-not-be-too-high-as-it-may-damage-the-downstream-equipment-but-it-must-also-be-high-enough-to-extract-an-acceptable-amount-of-heat"
    id="toc-q6-you-are-consulting-with-a-team-that-is-designing-a-prototype-heat-transfer-device-they-are-asking-you-to-help-determine-a-dependable-range-of-values-for-t_norm-they-can-design-around-for-this-single-prototype-the-realized-value-of-t_norm-must-not-be-too-high-as-it-may-damage-the-downstream-equipment-but-it-must-also-be-high-enough-to-extract-an-acceptable-amount-of-heat"><strong>q6</strong>
    You are consulting with a team that is designing a prototype heat
    transfer device. They are asking you to help determine a <em>dependable
    range of values</em> for <code>T_norm</code> they can design around for
    this <em>single prototype</em>. The realized value of
    <code>T_norm</code> must not be too high as it may damage the downstream
    equipment, but it must also be high enough to extract an acceptable
    amount of heat.</a>
- <a href="#references" id="toc-references">References</a>

*Purpose*: Confidence and prediction intervals are useful for studying
“pure sampling” of some distribution. However, we can combine CI and PI
with regression analysis to equip our modeling efforts with powerful
notions of uncertainty. In this challenge, you will use fluid simulation
data in a regression analysis with uncertainty quantification (CI and
PI) to support engineering design.

<!-- include-rubric -->

# Grading Rubric

<!-- -------------------------------------------------- -->

Unlike exercises, **challenges will be graded**. The following rubrics
define how you will be graded, both on an individual and team basis.

## Individual

<!-- ------------------------- -->

| Category    | Needs Improvement                                                                                                | Satisfactory                                                                                                               |
|-------------|------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| Effort      | Some task **q**’s left unattempted                                                                               | All task **q**’s attempted                                                                                                 |
| Observed    | Did not document observations, or observations incorrect                                                         | Documented correct observations based on analysis                                                                          |
| Supported   | Some observations not clearly supported by analysis                                                              | All observations clearly supported by analysis (table, graph, etc.)                                                        |
| Assessed    | Observations include claims not supported by the data, or reflect a level of certainty not warranted by the data | Observations are appropriately qualified by the quality & relevance of the data and (in)conclusiveness of the support      |
| Specified   | Uses the phrase “more data are necessary” without clarification                                                  | Any statement that “more data are necessary” specifies which *specific* data are needed to answer what *specific* question |
| Code Styled | Violations of the [style guide](https://style.tidyverse.org/) hinder readability                                 | Code sufficiently close to the [style guide](https://style.tidyverse.org/)                                                 |

## Due Date

<!-- ------------------------- -->

All the deliverables stated in the rubrics above are due **at midnight**
before the day of the class discussion of the challenge. See the
[Syllabus](https://docs.google.com/document/d/1qeP6DUS8Djq_A0HMllMqsSqX3a9dbcx1/edit?usp=sharing&ouid=110386251748498665069&rtpof=true&sd=true)
for more information.

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
    ## ✔ ggplot2 3.4.0      ✔ purrr   1.0.1 
    ## ✔ tibble  3.1.8      ✔ dplyr   1.0.10
    ## ✔ tidyr   1.3.0      ✔ stringr 1.5.0 
    ## ✔ readr   2.1.3      ✔ forcats 0.5.2 
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
library(modelr)
library(broom)
```

    ## 
    ## Attaching package: 'broom'
    ## 
    ## The following object is masked from 'package:modelr':
    ## 
    ##     bootstrap

``` r
library(ppcor)
```

    ## Warning: package 'ppcor' was built under R version 4.2.3

    ## Loading required package: MASS
    ## 
    ## Attaching package: 'MASS'
    ## 
    ## The following object is masked from 'package:dplyr':
    ## 
    ##     select

``` r
library(randomForest)
```

    ## Warning: package 'randomForest' was built under R version 4.2.3

    ## randomForest 4.7-1.1
    ## Type rfNews() to see new features/changes/bug fixes.
    ## 
    ## Attaching package: 'randomForest'
    ## 
    ## The following object is masked from 'package:dplyr':
    ## 
    ##     combine
    ## 
    ## The following object is masked from 'package:ggplot2':
    ## 
    ##     margin

``` r
library(leaps)
```

    ## Warning: package 'leaps' was built under R version 4.2.3

``` r
select <- dplyr::select


## Helper function to compute uncertainty bounds
add_uncertainties <- function(data, model, prefix = "pred", ...) {
  df_fit <-
    stats::predict(model, data, ...) %>%
    as_tibble() %>%
    rename_with(~ str_c(prefix, "_", .))

  bind_cols(data, df_fit)
}
```

# Orientation: Exploring Simulation Results

*Background*: The data you will study in this exercise come from a
computational fluid dynamics (CFD) [simulation
campaign](https://www.sciencedirect.com/science/article/abs/pii/S0301932219308651?via%3Dihub)
that studied the interaction of turbulent flow and radiative heat
transfer to fluid-suspended particles\[1\]. These simulations were
carried out to help study a novel design of [solar
receiver](https://en.wikipedia.org/wiki/Concentrated_solar_power),
though they are more aimed at fundamental physics than detailed device
design. The following code chunk downloads and unpacks the data to your
local `./data/` folder.

``` r
## NOTE: No need to edit this chunk
## Download PSAAP II data and unzip
url_zip <- "https://ndownloader.figshare.com/files/24111269"
filename_zip <- "./data/psaap.zip"
filename_psaap <- "./data/psaap.csv"

curl::curl_download(url_zip, destfile = filename_zip)
unzip(filename_zip, exdir = "./data")
df_psaap <- read_csv(filename_psaap)
```

    ## Rows: 140 Columns: 22
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## dbl (22): x, idx, L, W, U_0, N_p, k_f, T_f, rho_f, mu_f, lam_f, C_fp, rho_p,...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

![PSAAP II irradiated core flow](./images/psaap-setup.png) Figure 1. An
example simulation, frozen at a specific point in time. An initial
simulation is run (HIT SECTION) to generate a turbulent flow with
particles, and that swirling flow is released into a rectangular domain
(RADIATED SECTION) with bulk downstream flow (left to right).
Concentrated solar radiation transmits through the optically transparent
fluid, but deposits heat into the particles. The particles then convect
heat into the fluid, which heats up the flow. The false-color image
shows the fluid temperature: Notice that there are “hot spots” where hot
particles have deposited heat into the fluid. The dataset `df_psaap`
gives measurements of `T_norm = (T - T0) / T0` averaged across planes at
various locations along the RADIATED SECTION.

### **q1** Perform your “initial checks” to get a sense of the data.

``` r
## TODO: Perform your initial checks
df_psaap %>%
  glimpse
```

    ## Rows: 140
    ## Columns: 22
    ## $ x      <dbl> 0.25, 0.25, 0.25, 0.25, 0.25, 0.25, 0.25, 0.25, 0.25, 0.25, 0.2…
    ## $ idx    <dbl> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, …
    ## $ L      <dbl> 0.1898058, 0.1511218, 0.1693629, 0.1348453, 0.2009348, 0.159982…
    ## $ W      <dbl> 0.03421154, 0.04636061, 0.03982547, 0.03252195, 0.04407102, 0.0…
    ## $ U_0    <dbl> 1.859988, 2.232010, 2.037526, 2.445058, 1.697920, 1.964563, 2.3…
    ## $ N_p    <dbl> 1600067, 2215857, 1707729, 2076161, 1945272, 1822635, 2364952, …
    ## $ k_f    <dbl> 0.08322124, 0.11122740, 0.08674231, 0.12083851, 0.09041236, 0.0…
    ## $ T_f    <dbl> 300.1695, 243.2194, 289.8267, 357.6900, 251.8989, 279.8404, 260…
    ## $ rho_f  <dbl> 1.1627025, 1.1319406, 1.1019925, 1.2267571, 1.4408823, 0.963726…
    ## $ mu_f   <dbl> 1.519285e-05, 1.840742e-05, 2.177345e-05, 2.230214e-05, 2.28436…
    ## $ lam_f  <dbl> 0.03158350, 0.02590530, 0.03487354, 0.03700987, 0.03557159, 0.0…
    ## $ C_fp   <dbl> 1062.3567, 1113.6519, 951.6687, 997.6194, 936.8270, 1223.7923, …
    ## $ rho_p  <dbl> 8415.812, 10648.082, 10805.811, 10965.876, 7819.270, 7372.629, …
    ## $ d_p    <dbl> 1.073764e-05, 1.100549e-05, 1.244840e-05, 9.729835e-06, 1.14198…
    ## $ C_pv   <dbl> 467.6986, 382.8730, 528.5409, 462.5276, 413.8601, 505.5510, 552…
    ## $ h      <dbl> 6279.242, 4666.593, 6147.515, 4920.612, 6018.550, 5356.113, 529…
    ## $ I_0    <dbl> 7876978, 6551358, 6121350, 6363488, 8512473, 7011572, 8268366, …
    ## $ eps_p  <dbl> 0.4426710, 0.3247988, 0.4027115, 0.3890929, 0.4388801, 0.336167…
    ## $ avg_q  <dbl> 689522.7, 684218.2, 619206.2, 1070186.0, 577245.1, 648248.9, 70…
    ## $ avg_T  <dbl> 485.0239, 291.3887, 401.6959, 447.3889, 392.5981, 401.3814, 360…
    ## $ rms_T  <dbl> 7.613507, 4.185764, 5.612525, 4.475737, 6.945722, 7.579457, 4.1…
    ## $ T_norm <dbl> 0.6158335, 0.1980487, 0.3859864, 0.2507726, 0.5585543, 0.434322…

**Observations**:

- Most of the variables are simulation conditions.
- Four variables are simulation results.
- `idx` is relative to each `x` value (`0.25`, `0.50`, `0.75`, and
  `1.00`)
- There are 35 simulations for each location `x`.

The important variables in this dataset are:

| Variable | Category | Meaning                           |
|----------|----------|-----------------------------------|
| `x`      | Spatial  | Channel location                  |
| `idx`    | Metadata | Simulation run                    |
| `L`      | Input    | Channel length                    |
| `W`      | Input    | Channel width                     |
| `U_0`    | Input    | Bulk velocity                     |
| `N_p`    | Input    | Number of particles               |
| `k_f`    | Input    | Turbulence level                  |
| `T_f`    | Input    | Fluid inlet temp                  |
| `rho_f`  | Input    | Fluid density                     |
| `mu_f`   | Input    | Fluid viscosity                   |
| `lam_f`  | Input    | Fluid conductivity                |
| `C_fp`   | Input    | Fluid isobaric heat capacity      |
| `rho_p`  | Input    | Particle density                  |
| `d_p`    | Input    | Particle diameter                 |
| `C_pv`   | Input    | Particle isochoric heat capacity  |
| `h`      | Input    | Convection coefficient            |
| `I_0`    | Input    | Radiation intensity               |
| `eps_p`  | Input    | Radiation absorption coefficient  |
| `avg_q`  | Output   | Plane-averaged heat flux          |
| `avg_T`  | Output   | Plane-averaged fluid temperature  |
| `rms_T`  | Output   | Plane-rms fluid temperature       |
| `T_norm` | Output   | Normalized fluid temperature rise |

The primary output of interest is `T_norm = (avg_T - T_f) / T_f`, the
normalized (dimensionless) temperature rise of the fluid, due to heat
transfer. These measurements are taken at locations `x` along a column
of fluid, for different experimental settings (e.g. different dimensions
`W, L`, different flow speeds `U_0`, etc.).

### **q2** Visualize `T_norm` against `x`. Note that there are multiple simulations at different values of the Input variables: Each simulation result is identified by a different value of `idx`.

``` r
## TODO: Visualize the data in df_psaap with T_norm against x;
##       design your visual to handle the multiple simulations,
##       each identified by different values of idx
df_psaap %>%
  ggplot(aes(x = x, y = T_norm)) +
    geom_line(
      data = .%>%
        group_by(x) %>%
        summarise(mean_T_norm = mean(T_norm)),
        aes(y = mean_T_norm),
      color = "red",
      size = 3
    ) +
    geom_line(aes(group = idx), color = "black")
```

    ## Warning: Using `size` aesthetic for lines was deprecated in ggplot2 3.4.0.
    ## ℹ Please use `linewidth` instead.

![](c11-psaap-assignment_files/figure-gfm/q2-task-1.png)<!-- -->

``` r
df_psaap <-
df_psaap %>%
  mutate(x_factor = factor(.$x, levels = c(0.25, 0.50, 0.75, 1.00)))

df_psaap %>%
  ggplot(aes(x = T_norm, group = x, fill = x_factor)) +
    geom_density(alpha = 0.5)
```

![](c11-psaap-assignment_files/figure-gfm/q2-task-2.png)<!-- -->

## Modeling

The following chunk will split the data into training and validation
sets.

``` r
## NOTE: No need to edit this chunk
# Addl' Note: These data are already randomized by idx; no need
# to additionally shuffle the data!
df_psaap <- select(df_psaap, -x_factor)
df_train <- df_psaap %>% filter(idx %in% 1:20)
df_validate <- df_psaap %>% filter(idx %in% 21:36)
```

One of the key decisions we must make in modeling is choosing predictors
(features) from our observations to include in the model. Ideally we
should have some intuition for why these predictors are reasonable to
include in the model; for instance, we saw above that location along the
flow `x` tends to affect the temperature rise `T_norm`. This is because
fluid downstream has been exposed to solar radiation for longer, and
thus is likely to be at a higher temperature.

Reasoning about our variables—at least at a *high level*—can help us to
avoid including *fallacious* predictors in our models. You’ll explore
this idea in the next task.

### **q3** The following code chunk fits a few different models. Compute a measure of model accuracy for each model on `df_validate`, and compare their performance.

``` r
## NOTE: No need to edit these models
fit_baseline <- 
  df_train %>% 
  lm(formula = T_norm ~ x)

fit_cheat <- 
  df_train %>% 
  lm(formula = T_norm ~ avg_T)

fit_nonphysical <- 
  df_train %>% 
  lm(formula = T_norm ~ idx)

## TODO: Compute a measure of accuracy for each fit above;
##       compare their relative performance

rsquare(fit_baseline, df_validate)
```

    ## [1] 0.4746546

``` r
rsquare(fit_cheat, df_validate)
```

    ## [1] 0.6374051

``` r
rsquare(fit_nonphysical, df_validate)
```

    ## [1] 0.001898415

**Observations**:

- Which model is *most accurate*? Which is *least accurate*?
  - `fit_cheat` is most accurate and `fit_nonphysical` is least
    accurate.
- What *Category* of variable is `avg_T`? Why is it such an effective
  predictor?
  - `avg_T` is an output of the simulation so it is an effective
    predictor because it likely is impacted by the same factors as
    `T_norm` instead of being one of many variables. If one input
    variable were to describe all variation in `T_norm` it would mean
    the rest have to have no impact on the simulation.
- Would we have access to `avg_T` if we were trying to predict a *new*
  value of `T_norm`? Is `avg_T` a valid predictor?
  - We would not have access to `avg_T` because it requires running the
    simulation. If we have done that we would know `T_norm` already so
    it is not a valid predictor.
- What *Category* of variable is `idx`? Does it have any physical
  meaning?
  - `idx` is metadata. It is a randomized identifier with no physical
    basis.

### **q4** Use a combination of EDA and train-validation error to build a model by selecting *reasonable* predictors for the `formula` argument. Document your findings under *observations* below. Try to build the most accurate model you can!

``` r
## TODO: Fit a model for T_norm using only *principled* predictors, try to
##       optimize your validation error.

## designate input and output variables

df_inputs <-
  df_train %>% 
  select(c(-avg_q, -avg_T, -rms_T, -idx, -T_norm)) %>%
  scale() %>%
  as.data.frame()


df_output <-
  df_train %>% 
  select(T_norm)

df_train %>%
  select(c(-avg_q, -avg_T, -rms_T, -idx)) %>%
  scale() %>%
  as.data.frame() %>%
  pivot_longer(
    cols = -T_norm,
    names_to = "var",
    values_to = "value"
  ) %>%
  ggplot() +
  geom_smooth(aes(
    x = T_norm,
    y = value
  )) +
  facet_wrap(facets = vars(var), scales = "free")
```

    ## `geom_smooth()` using method = 'loess' and formula = 'y ~ x'

![](c11-psaap-assignment_files/figure-gfm/q4-initial-exploration-1.png)<!-- -->

``` r
## linear correlations

linear_correlations <- cor(df_inputs, df_output)
  

## partial correlations


partial_correlations <- numeric(length(df_inputs))

for (i in 1:length(df_inputs)) {
  x_i <- df_inputs[, i, drop = FALSE]
  x_other <- df_inputs[, -i, drop = FALSE]
  result <- pcor.test(x_i, df_output, x_other)
  partial_correlations[i] <- result$estimate
}


df_correlations <-
  data.frame(
    linear_correlations,
    partial_correlations
  )

## use all parameters
input_names <- names(df_inputs)
formula <-
  paste(
    "T_norm ~",
    paste(input_names, collapse = " + ")
  ) %>%
  as.formula()

rf_all <- randomForest(formula = formula, data = df_train)

lm_all <- lm(formula = formula, data = df_train)

## test model

print_model_rsquare <-
  function(
    model,
    train_data,
    validate_data
  ) {
  model_name <- attr(model, "name")
  cat(
    "Model: ", model_name, ", ",
    "Training R^2: ", round(rsquare(model, train_data), 4), ", ",
    "Validation R^2: ", round(rsquare(model, validate_data), 4),
    "\n"
  )
}

print_model <- function(model) {
  model_name <- deparse(substitute(model))
  attr(model, "name") <- model_name
  print_model_rsquare(model, df_train, df_validate)
}

print_model(rf_all)
```

    ## Model:  rf_all ,  Training R^2:  0.9023 ,  Validation R^2:  0.4117

``` r
print_model(lm_all)
```

    ## Model:  lm_all ,  Training R^2:  0.9345 ,  Validation R^2:  0.7867

``` r
n <- 10

cov_mat <- cov(df_inputs)
cov_mat[lower.tri(cov_mat)] <- NA 
diag(cov_mat) <- 0
top_n <- head(sort(abs(cov_mat), decreasing = TRUE), n)

for (i in 1:n) {
  loc <- which(abs(cov_mat) == top_n[i], arr.ind = TRUE)
  row_name <- rownames(cov_mat)[loc[1]]
  col_name <- colnames(cov_mat)[loc[2]]
  print(paste0("Top ", i, " value: ", top_n[i], " (", row_name, ", ", col_name, ")"))
}
```

    ## [1] "Top 1 value: 0.636822701572841 (rho_f, d_p)"
    ## [1] "Top 2 value: 0.63020593834115 (U_0, h)"
    ## [1] "Top 3 value: 0.540897498031685 (W, I_0)"
    ## [1] "Top 4 value: 0.510863219862231 (N_p, d_p)"
    ## [1] "Top 5 value: 0.504415998078139 (U_0, N_p)"
    ## [1] "Top 6 value: 0.492563206733339 (lam_f, C_fp)"
    ## [1] "Top 7 value: 0.444780816771076 (C_pv, h)"
    ## [1] "Top 8 value: 0.443776742473919 (C_fp, I_0)"
    ## [1] "Top 9 value: 0.436544681230901 (W, C_pv)"
    ## [1] "Top 10 value: 0.433752623280202 (T_f, d_p)"

``` r
df_inputs %>%
  cov() %>%
  replace(., diag(nrow(.)) == 1, 0) %>%
  as.data.frame() %>%
  rownames_to_column(var = "variable1") %>%
  pivot_longer(
    cols = -variable1,
    names_to = "variable2",
    values_to = "covariance"
  ) %>%
  ggplot(aes(variable1, variable2, fill = covariance)) +
    geom_tile() +
    scale_fill_gradient2(low = "blue", mid = "white", high = "red", midpoint = 0) +
    theme_minimal() +
    theme(axis.text.x = element_text(angle = 45, hjust = 1))
```

![](c11-psaap-assignment_files/figure-gfm/q4-correlation-plot-1.png)<!-- -->

``` r
## order variables
names_ordered_pcor <-
  df_correlations %>%
  arrange(desc(abs(partial_correlations))) %>%
  rownames()

names_ordered_cor <-
  df_correlations %>%
  arrange(desc(abs(linear_correlations))) %>%
  rownames()

names_ordered_cov <-
  df_inputs %>%
  cov() %>%
  as.data.frame() %>%
  mutate(var = rownames(.)) %>%
  pivot_longer(cols = -var, names_to = "covar", values_to = "covar_val") %>%
  filter(var != covar) %>%
  group_by(var) %>%
  summarise(total_covar_mag = sum(abs(covar_val))) %>%
  arrange(total_covar_mag) %>%
  pull(var)


model_types <- tibble(
  model_name = c("Linear Regression", "Random Forest"),
  model_function = list(lm, randomForest)
)


rank_types <- tibble(
  rank_name = c("cor", "pcor", "cov"),
  ordered_names = list(names_ordered_cor, names_ordered_pcor, names_ordered_cov)
)
```

``` r
models_from_ranking <-
  function(
    model,
    variable_ranking,
    train_data
  ) {
  models_list <- vector("list", length(variable_ranking))
  models_df <- data.frame(n = 1:length(variable_ranking))
  for (i in 1:length(variable_ranking)) {
    formula <-
      paste(
        "T_norm ~",
        paste(variable_ranking[1:i], collapse = " + ")
      ) %>%
      as.formula()
    models_list[[i]] <- model(formula, data = train_data)
  }
  models_df$model <- models_list
  return(models_df)
  }


add_error_column <-
  function(
    models_df,
    error_func,
    train_data,
    validate_data
  ) {
  col_train <- "training"
  col_val <- "validation"
  models_df[, col_train] <- NA
  models_df[, col_val] <- NA
  
  for (i in seq_len(nrow(models_df))) {
    model <- models_df$model[[i]]
    models_df[i, col_train] <-
      error_func(model, train_data)
    models_df[i, col_val] <- 
      error_func(model, validate_data)
  }
  return(models_df)
  }



all_models_df <-
  function(
    model_types,
    rank_types,
    train_data,
    validate_data,
    error_func
  ) {
    
  result_df <-
    data.frame(
      n = numeric(),
      model = list(),
      model_name = character(),
      rank_type = character(),
      training = numeric(),
      validation = numeric()
      )
  
  for (i in seq_along(model_types$model_function)) {
    for (j in seq_along(rank_types$ordered_names)) {
      df_new_models <-
        models_from_ranking(
          model_types$model_function[[i]],
          rank_types$ordered_names[[j]],
          train_data
        ) %>%
        add_error_column(
          error_func,
          train_data,
          validate_data
        ) %>%
        mutate(
          model_name = model_types$model_name[[i]],
          rank_type = rank_types$rank_name[[j]]
        )
      
      result_df <- rbind(result_df, df_new_models)
    }
  }
  
  return(result_df)
}
```

``` r
df_models <-
  all_models_df(
    model_types,
    rank_types,
    df_train,
    df_validate,
    rsquare
  )

df_error <-
  df_models %>%
  select(-model)
```

``` r
df_error %>%
  ggplot(aes(x = n, y = validation)) +
    geom_line() +
    facet_grid(vars(model_name), vars(rank_type))
```

![](c11-psaap-assignment_files/figure-gfm/q4-visualization-1.png)<!-- -->

``` r
fit_q4 <-
  df_models %>%
  arrange(desc(df_models$validation)) %>%
  head(n = 1) %>%
  pull(model) %>%
  `[[`(1)

print(fit_q4$coefficients)
```

    ##   (Intercept)             x             W             L           I_0 
    ## -8.549069e-01  1.018323e+00 -3.204710e+01  2.804722e+00  1.718583e-07 
    ##           U_0           d_p          C_fp 
    ## -2.434876e-01  1.377382e+05 -4.031535e-04

**Observations**:

- Using a random forest approach yielded low success on the validation
  data, `rsquare ~ .4`.
  - This could be over fitting
- The spikiness of `rsquare` makes me suspicious that of whether this
  method is valid or lucky.
  - I will compare the peak `rsquare` to a linear model. If it’s better
    than a linear model, this is worth paying more attention to.
  - I will repeat this method ranking variables by correlation instead
    of partial correlation instead. I thought partial correlation would
    be more appropriate for a non-linear model, but I could be wrong.
  - I also tried brute force but lost patience
  - max is only `.84` which isn’t that good.
- *Note*: You don’t just have to fiddle with `formula`! Remember that
  you have a whole toolkit of *EDA* tools

## Contrasting CI and PI

Let’s revisit the ideas of confidence intervals (CI) and prediction
intervals (PI). Let’s fit a very simple model to these data, one which
only considers the channel location and ignores all other inputs. We’ll
also use the helper function `add_uncertainties()` (defined in the
`setup` chunk above) to add approximate CI and PI to the linear model.

``` r
## NOTE: No need to edit this chunk
fit_simple <-
  df_train %>%
  lm(data = ., formula = T_norm ~ x)

df_intervals <-
  df_train %>%
  add_uncertainties(fit_simple, interval = "confidence", prefix = "ci") %>%
  add_uncertainties(fit_simple, interval = "prediction", prefix = "pi")
```

The following figure visualizes the regression CI and PI against the
objects they are attempting to capture:

``` r
## NOTE: No need to edit this chunk
df_intervals %>%
  select(T_norm, x, matches("ci|pi")) %>%
  pivot_longer(
    names_to = c("method", ".value"),
    names_sep = "_",
    cols = matches("ci|pi")
  ) %>%

  ggplot(aes(x, fit)) +
  geom_errorbar(
    aes(ymin = lwr, ymax = upr, color = method),
    width = 0.05,
    size = 1
  ) +
  geom_smooth(
    data = df_psaap %>% mutate(method = "ci"),
    mapping = aes(x, T_norm),
    se = FALSE,
    linetype = 2,
    color = "black"
   ) +
  geom_point(
    data = df_validate %>% mutate(method = "pi"),
    mapping = aes(x, T_norm),
    size = 0.5
  ) +

  facet_grid(~method) +
  theme_minimal() +
  labs(
    x = "Channel Location (-)",
    y = "Normalized Temperature Rise (-)"
  )
```

    ## `geom_smooth()` using method = 'loess' and formula = 'y ~ x'

    ## Warning in simpleLoess(y, x, w, span, degree = degree, parametric = parametric,
    ## : pseudoinverse used at 0.24625

    ## Warning in simpleLoess(y, x, w, span, degree = degree, parametric = parametric,
    ## : neighborhood radius 0.50375

    ## Warning in simpleLoess(y, x, w, span, degree = degree, parametric = parametric,
    ## : reciprocal condition number 2.0889e-16

    ## Warning in simpleLoess(y, x, w, span, degree = degree, parametric = parametric,
    ## : There are other near singularities as well. 0.25376

![](c11-psaap-assignment_files/figure-gfm/data-simple-model-vis-1.png)<!-- -->

Under the `ci` facet we have the regression confidence intervals and the
mean trend (computed with all the data `df_psaap`). Under the `pi` facet
we have the regression prediction intervals and the `df_validation`
observations.

**Punchline**:

- Confidence intervals are meant to capture the *mean trend*
- Prediction intervals are meant to capture *new observations*

Both CI and PI are a quantification of the uncertainty in our model, but
the two intervals designed to answer different questions.

Since CI and PI are a quantification of uncertainty, they should tend to
*narrow* as our model becomes more confident in its predictions.
Building a more accurate model will often lead to a reduction in
uncertainty. We’ll see this phenomenon in action with the following
task:

### **q5** The following code will construct a predicted-vs-actual plot with your model from *q4* and add prediction intervals. Study the results and answer the questions below under *observations*.

``` r
## TODO: Run this code and interpret the results
## NOTE: No need to edit this chunk
## NOTE: This chunk will use your model from q4; it will predict on the
##       validation data, add prediction intervals for every prediction,
##       and visualize the results on a predicted-vs-actual plot. It will
##       also compare against the simple `fit_simple` defined above.
bind_rows(
  df_validate %>% 
    add_uncertainties(fit_simple, interval = "prediction", prefix = "pi") %>% 
    select(T_norm, pi_lwr, pi_fit, pi_upr) %>% 
    mutate(model = "x only"),
  df_validate %>% 
    add_uncertainties(fit_q4, interval = "prediction", prefix = "pi") %>% 
    select(T_norm, pi_lwr, pi_fit, pi_upr) %>% 
    mutate(model = "q4"),
) %>% 
  
  ggplot(aes(T_norm, pi_fit)) +
  geom_abline(slope = 1, intercept = 0, color = "grey80", size = 2) +
  geom_errorbar(
    aes(ymin = pi_lwr, ymax = pi_upr),
    width = 0
  ) +
  geom_point() +
  
  facet_grid(~ model, labeller = label_both) +
  theme_minimal() +
  labs(
    title = "Predicted vs Actual",
    x = "Actual T_norm",
    y = "Predicted T_norm"
  )
```

![](c11-psaap-assignment_files/figure-gfm/q5-task-1.png)<!-- -->

**Observations**:

- Which model tends to be more accurate? How can you tell from this
  predicted-vs-actual plot?
  - my `q4` model sis more accurate. The distance between predicted and
    actual values is smaller.
- Which model tends to be *more confident* in its predictions? Put
  differently, which model has *narrower prediction intervals*?
  - My model from `q4`.
- How many predictors does the `fit_simple` model need in order to make
  a prediction? What about your model `fit_q4`?
  - fit_simple uses 1 predictor while `fit_q4` uses 7.

Based on these results, you might be tempted to always throw every
reasonable variable into the model. For some cases, that might be the
best choice. However, some variables might be *outside our control*; for
example, variables involving human behavior cannot be fully under our
control. Other variables may be *too difficult to measure*; for example,
it is *in theory* possible to predict the strength of a component by
having detailed knowledge of its microstructure. However, it is
*patently infeasible* to do a detailed study of *every single component*
that gets used in an airplane.

In both cases—human behavior and variable material properties—we would
be better off treating those quantities as random variables. There are
at least two ways we could treat these factors: 1. Explicitly model some
inputs as random variables and construct a model that *propagates* that
uncertainty from inputs to outputs, or 2. Implicitly model the
uncontrolled the uncontrolled variables by not including them as
predictors in the model, and instead relying on the error term
$\epsilon$ to represent these unaccounted factors. You will pursue
strategy 2. in the following Case Study.

# Case Study: Predicting Performance Ranges

### **q6** You are consulting with a team that is designing a prototype heat transfer device. They are asking you to help determine a *dependable range of values* for `T_norm` they can design around for this *single prototype*. The realized value of `T_norm` must not be too high as it may damage the downstream equipment, but it must also be high enough to extract an acceptable amount of heat.

In order to maximize the conditions under which this device can operate
successfully, the design team has chosen to fix the variables listed in
the table below, and consider the other variables to fluctuate according
to the values observed in `df_psaap`.

| Variable | Value    |
|----------|----------|
| `x`      | 1.0      |
| `L`      | 0.2      |
| `W`      | 0.04     |
| `U_0`    | 1.0      |
| (Other)  | (Varies) |

Your task is to use a regression analysis to deliver to the design team
a *dependable range* of values for `T_norm`, given their proposed
design, and at a fairly high level `0.8`. Perform your analysis below
(use the helper function `add_uncertainties()`!), and answer the
questions below.

*Hint*: This problem will require you to *build a model* by choosing the
appropriate variables to include in the analysis. Think about *which
variables the design team can control*, and *which variables they have
chosen to allow to vary*. You will also need to choose between computing
a CI or PI for the design prediction.

``` r
# NOTE: No need to change df_design; this is the target the client
#       is considering
df_design <- tibble(x = 1, L = 0.2, W = 0.04, U_0 = 1.0)
# NOTE: This is the level the "probability" level customer wants
pr_level <- 0.8

## TODO: Fit a model, assess the uncertainty in your prediction, 
#        use the validation data to check your uncertainty estimates, and 
#        make a recommendation on a *dependable range* of values for T_norm
#        at the point `df_design`
fit_q6 <-
  df_train %>%
  lm(formula = T_norm ~ x + L + W + U_0)

df_uncertain <-
  df_design %>%
  add_uncertainties(
    fit_q6,
    interval = "prediction",
    prefix = "pi",
    level = pr_level
  )

df_uncertain %>% 
  select(pi_fit, pi_lwr, pi_upr)
```

    ## # A tibble: 1 × 3
    ##   pi_fit pi_lwr pi_upr
    ##    <dbl>  <dbl>  <dbl>
    ## 1   1.88   1.46   2.30

``` r
df_validate %>%
  filter(T_norm > 1.45685 & T_norm < 2.296426) %>%
  count() / count(df_validate)
```

    ##      n
    ## 1 0.05

**Recommendation**:

- How much do you trust your model? Why?
  - Not very much. Its exceptionally constrained and poorly trained.
- What kind of interval—confidence or prediction—would you use for this
  task, and why?
  - As we are using a model to make predictions we should use a
    prediction interval. We are not sampling, we are modeling future
    observations.
- What fraction of validation cases lie within the interval you predict?
  How does this compare with `pr_level`?
  - 1/20 which is far lower than `pr_level`
- What interval for `T_norm` would you recommend the design team to plan
  around?
  - the calculated interval `1.45685 < T_norm < 2.296426` is the most
    informed recommendation I can make but it appears to be a poor
    interval to use.
- Are there any other recommendations you would provide?
  - Further tweaking is required. This model is not currently usable. I
    recommend a combination of more robust training and experimentation
    with the selected parameters to achieve a more useful result.

*Bonus*: One way you could take this analysis further is to recommend
which other variables the design team should tightly control. You could
do this by fixing values in `df_design` and adding them to the model. An
exercise you could carry out would be to systematically test the
variables to see which ones the design team should more tightly control.

# References

- \[1\] Jofre, del Rosario, and Iaccarino “Data-driven dimensional
  analysis of heat transfer in irradiated particle-laden turbulent
  flow” (2020) *International Journal of Multiphase Flow*,
  <https://doi.org/10.1016/j.ijmultiphaseflow.2019.103198>
