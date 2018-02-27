# How is TDD relevant for data science?

Our core contribution as Data Scientists in building intelligent applications is in shaping the _brain_ (or the ML Engine) of the application which will drive actions. We have to ensure that this core driving component of the app is _always behaving as expected_, and this is where TDD comes to our rescue.

# Motivation

## Example 1

Imagine that you work for DHL and your new smart app with an improved Routing Engine is going live tomorrow. The model performed admirably in Training, but you shudder at the thought of an unexpected input value or some unforeseen system spike causing your engine to produce False Positives that lead to chaos and monetary loss. You remember that you've wrapped up the predictions in test-cases that will trust model predictions only when they lie within a pre-defined confidence interval and demand human-approval for edge cases.

## Example 2

If you introduce a bug today that slows your job down, with A good CI pipeline that automatically runs nightly tests on the master, you will at the very least find out tomorrow about it. This would also help find out-of-memory errors or disk-space errors.

TDD can not only help us ensure that nothing went wrong while developing our model but also prompts us to think what we want to achieve and forces us to think about edge cases where things can potentially go wrong. TDD allow us to be more confident.

# Challenge

TDD for Data Science is certainly trickier than TDD for software engineering because of the exploratory nature of our approach. We know during our search for influential features that most of them would not end up on the final model. How do we decide which ones to test?

# Best Practices

- Testing all features and algorithms stringently during the Exploratory phase is an overkill, and will slow you down.
- Once you have figured out which model and features to use, you can start writing tests for feature engineering, model development, performance, persistence and integration.
- Your use case will help establish an appropriate performance metric and a minimum level of acceptable performance.
  - Example, RMSE < x for regression tasks; Recall > r, for a classification task
  - Allows you to automatically test your model, helps focus efforts on optimizing against relevant and meaningful performance measures, and defines a clear line when you can stop tuning.
- Pair program! You come up with a test case, your colleague makes it pass and then the role reverses.
- Automate your testing with a CI tool like Jenkins
- Tests should not take more than a few minutes to run.

# The Agile Mindset

With your Sprint Goals and your DoDs in hand, it should be fairly simple to write high-level tests, and then work your way down.
