`pytest` is a popular testing framework in Python that is widely used for writing simple and scalable test cases. Here’s an overview of how `pytest` is commonly used, including its features, setup, and examples:

### Key Features of `pytest`

1. **Simple Syntax**: `pytest` allows you to write tests using standard Python assertions, making it easy to learn and use.
    
2. **Fixtures**: It provides a powerful fixture system for setup code that can be reused across multiple tests.
    
3. **Parameterization**: You can run a single test function with different parameters, making it easier to test various scenarios.
    
4. **Plugins**: `pytest` has a rich ecosystem of plugins to extend its capabilities (e.g., for coverage, mocking, and parallel test execution).
    
5. **Support for Multiple Testing Styles**: It supports unittest-style tests as well as its own style, allowing flexibility in how tests are written.
    

### Getting Started with `pytest`

1. **Installation**: To install `pytest`, you can use pip:
    
    `pip install pytest`
    
2. **Basic Test Structure**: Create a Python file (e.g., `test_sample.py`) and define your test functions. Test functions should start with `test_` to be automatically recognized by `pytest`.
    
    ``` Python
def test_addition():   
  assert 1 + 1 == 2  
def test_subtraction():     
  assert 3 - 1 == 2
```
    
3. **Running Tests**: Run the tests from the command line by executing:
    
    `pytest`
    
    This will discover and run all tests in files matching the pattern `test_*.py` or `*_test.py`.
    
4. **Viewing Results**: After running, `pytest` will provide a summary of the test results, showing which tests passed and which failed.
    

### Using Fixtures

Fixtures allow you to set up necessary conditions for your tests. Here’s an example of how to use them:

``` Python
import pytest  
@pytest.fixture 
def sample_data():     
    return [1, 2, 3]  
def test_sum(sample_data):     
    assert sum(sample_data) == 6
```

In this example, the `sample_data` fixture provides a list to the test function `test_sum`, ensuring that any setup needed is handled in one place.

### Parameterization

You can run the same test with different inputs using the `@pytest.mark.parametrize` decorator:

``` Python
import pytest  

@pytest.mark.parametrize("a, b, expected", [     
		(1, 2, 3),     
		(2, 3, 5),     
		(3, 5, 8) 
]) 
def test_add(a, b, expected):     
     assert a + b == expected
```

### Running Specific Tests

You can run specific tests by passing the filename or the test function name to the `pytest` command:

``` bash
pytest test_sample.py 
pytest test_sample.py::test_addition
```

### Generating Reports

You can generate more detailed reports with additional options:

- To generate a report in a specific format, such as HTML:
  
    `pytest --html=report.html`


### Conclusion

`pytest` is a versatile and powerful testing framework that simplifies the process of writing and managing tests in Python. Its flexibility, extensive features, and active community make it a preferred choice for many developers when ensuring the quality and reliability of their code.