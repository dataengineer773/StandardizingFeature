I want to transform a feature to have a mean of 0 and a standard deviation of 1, scikit-learn’s StandardScaler performs both transformations A common alternative to min-max scaling discussed in Recipe 4.1 is rescaling of features to be
approximately standard normally distributed. To achieve this, we use standardization to transform the
data such that it has a mean, x̄, of 0 and a standard deviation, σ, of 1. Specifically, each element in the
feature is transformed so that:
where x’
i
is our standardized form of xi
. The transformed feature represents the number of standard
deviations the original value is away from the feature’s mean value (also called a z-score in statistics).
Standardization is a common go-to scaling method for machine learning preprocessing and in my
experience is used more than min-max scaling. However, it depends on the learning algorithm. For
example, principal component analysis often works better using standardization, while min-max scaling
is often recommended for neural networks (both algorithms are discussed later in this book). As a
general rule, I’d recommend defaulting to standardization unless you have a specific reason to use an
alternative.
We can see the effect of standardization by looking at the mean and standard deviation of our solution’s
output, If our data has significant outliers, it can negatively impact our standardization by affecting the feature’s
mean and variance. In this scenario, it is often helpful to instead rescale the feature using the median
and quartile range. In scikit-learn, we do this using the RobustScaler method
