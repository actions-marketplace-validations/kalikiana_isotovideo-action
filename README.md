# Isotovideo test runner

Execute standalone [openQA](https://open.qa) tests within containers. If your repository contains a test distribution or an openQA wheel this action can be used to execute it.

Under the hood the action is analoguous to something like this:

    SCHEDULE=tests/foo/bar CASEDIR=. QEMU_NO_KVM=1 isotovideo

## Inputs

## schedule

Analoguous to the `SCHEDULE` environment variable you can specify a list of test modules to be executed instead of using a main.pm in the same repository.

## Example usage

```yaml
on: [push, pull_request]
jobs:
  isotovideo:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: kalikiana/isotovideo-action@main
        with:
          schedule: tests/foo/bar
      - uses: actions/upload-artifact@v2
        with:
          name: Test results
          path: .
        if: always()
```
