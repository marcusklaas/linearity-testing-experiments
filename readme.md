linearity testing experiments
-----------------------------

This repository contains experiments to test superlinear parsing behavior. The goal is to find
a method that is fast, resistant to noise and data efficient.

## approach one: linear fit

We sample a number of points and then fit a linear model. The idea is that
when the growth is superlinear, the best linear fit will likely intercept the y-axis at some negative y.
When it is (sub)linear, the probability of that happening should be no larger than 0.5. So we can
do a one-sided hypothesis test of the intercept variable. If it is significantly smaller than zero, we
can conclude that the behavior is superlinear. We may want to start with a few samples and keep resampling
until we get the required significance (p < 10E-6?). To maintain the speed we want, we'll probably want to
abort as soon as the significance drops below some predefined threshold (p > 0.25?).
