#  Using pytest to improve testing

Watching mcoding and he showed a really good setup for automated
testing using pytest, tox and github
actions.[Automated testing](https://www.youtube.com/watch?v=DhUpxWjOhME)

One of the focuses was really on how to use pytest efficiently. The
issue with standard testing is that if one test fails none of the others
run.

Using the parameterize decorator we can run the multiple tests with a
single function

```
@pytest.mark.parameterize("test_input,expected", [(.., ..), (.., ..)])

def test_multi(test_input, expected):
    assert function('test_expected, input) is expected

```

We can also skip functionality testing with `@pytest.mark.skip` if we
haven't implemented functions yet

We can create what are known as fixtures which are boiler plate code for
setup and teardown of functionality before testing. The method is set in
a conftest.py file and use the `@pytest.fixture(scope="session")` and
wrap the function. This setup is then able to be used across all tests.

Another thing to look into for testing is the inbuilt function called
`monkeytest`

We can add test coverage with pytest as well.

