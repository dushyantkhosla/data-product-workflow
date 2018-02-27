# Motivation

> “Why do most developers fear to make continuous changes to their code? They are afraid they’ll break it! Why are they afraid they’ll break it? Because they don’t have tests.”

There are a lot of types of software testing, from Unit Testing (checking to make sure individual code works), Branch Testing (making sure the code works with all the other software you've changed in your area) to integration testing (making sure your code works with everyone else's) and Security Testing (making sure your code doesn't allow bad security things to happen).

For most software, this is something that is easy to think about (but not necessarily to implement). If a certain function in the code takes in two numbers and averages them, that can be Unit tested with a function that ensures the result is accurate. You can then check your changes in, and Integration tests can run against the new complete software build with a fabricated set of results to ensure that everything works as expected.

But not so with Data Science work - or at least not all the time. There are a lot of situations where the answer is highly dependent on minute changes in the data, parameters, or other transitory conditions, and since many of these results fall within ranges (even between runs) you can't always put in a 10 and expect a 42 to come out.

First, make sure you know how to code with error-checking and handling routines in your chosen language.
Next, implement a Unit Test framework within your code - use `pytest` or `nose`

After you've done the basics above, it's time to start thinking about the larger testing framework. It's not just that the code runs and integrates correctly, it's that it returns an expected result. In some cases, you can set a deterministic value to test with, like number of rows in a dataset or the expected data type from a function, and check that value against the run.

But if you can't - the values can't always be deterministic due to the nature of the algorithm. In that case, pick the metric you use for the algorithm (p-value, F1-score, or AUC, or whatever is appropriate) and check if it lies within an acceptable range.

# Example

https://pandas.pydata.org/pandas-docs/stable/contributing.html#test-driven-development-code-writing

> pandas is serious about testing and strongly encourages contributors to embrace test-driven development (TDD). This development process “relies on the repetition of a very short development cycle: first the developer writes an (initially failing) automated test case that defines a desired improvement or new function, then produces the minimum amount of code to pass that test.” So, before actually writing any code, you should write your tests.

- All tests should go into the `tests/` subdirectory of the specific package.
- Writing tests in three steps;
  - Get/make the input data
  - Manually construct the result you expect
  - Compare the actual result to the expected correct result

```python
def test_pivot(self):
    data = {
        'index' : ['A', 'B', 'C', 'C', 'B', 'A'],
        'columns' : ['One', 'One', 'One', 'Two', 'Two', 'Two'],
        'values' : [1., 2., 3., 3., 2., 1.]
    }

    frame = DataFrame(data)
    pivoted = frame.pivot(index='index', columns='columns', values='values')

    expected = DataFrame({
        'One' : {'A' : 1., 'B' : 2., 'C' : 3.},
        'Two' : {'A' : 1., 'B' : 2., 'C' : 3.}
    })

    assert_frame_equal(pivoted, expected)
  ```
# Tests for Data Science

> The nature of data-science work is Exploratory and expected to improve/change over time. As such, instead of testing the exact output of scripts, we test the _properties_ of the output.

For a classification task, we might want to test if

- The classifier performs better than random chance
- The output object has a `coef_` attribute, which contains a non-empty NumPy array

# Practical Advice

- Keep samples of data (perhaps under `tests/data/`) for running tests.
- The Prodution Phase of the process will benefit most from this.
