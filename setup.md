## Setup

1. Working with virtual environments in Python is important for isolating dependencies. It can be tricky to set them up. Create a new virtual environment - use conda or venv. See [these instructions](https://gist.github.com/discdiver/0bb3bf96f02c182f96d45278f9564551), if needed.
1. Install the latest, unreleased, version of ControlFlow from the `main` branch into your virtual environment:
   `pip install git+https://github.com/PrefectHQ/ControlFlow`
   or with uv installed:
   `uv pip install git+https://github.com/PrefectHQ/ControlFlow`
1. Upgrade Prefect to the latest Prefect 3.0rc version:
    `pip install prefect --pre`
    or with uv installed:
    `uv pip install prefect --pre`
1. Connect to Prefect Cloud (this assumes you already have a Prefect Cloud account), if you aren't already authenticated from the CLI:
    `prefect cloud login`

### Run a test Prefect flow

Run a Prefect flow to test your Prefect setup.

1. In a text editor (VS Code is great if you are choosing one) copy the following:

```python
import httpx
from prefect import flow

@flow(log_prints=True)
def test_flow():
    res = httpx.get("https://example.com")
    print(res)

if __name__ == "__main__":
    test_flow()
```

Talk through what the code is doing, if you aren't 100% sure.

1. Run the script from the terminal with `python my_flow.py`

1. Check out the **Runs** tab in the Prefect Cloud UI.

That's good for now. Let's move on to ControlFlow!

### Configure OpenAI for ControlFlow

1. Log in or sign up for an [OpenAI account](https://platform.openai.com/signup).
1. Create and copy an [API key](https://platform.openai.com/api-keys) from your account.
1. Save your OpenAI API key locally:
    Set the API key as an environment variable: `export OPENAI_API_KEY='paste-your-api-key-here'`
    This is a temporary way to set the key - it only lives in your current terminal session.
    If you want to set the key permanently, you can add it as a line to the hidden `.zshrc` file in your home directory:
    `export OPENAI_API_KEY='paste-key-here'`
    This will set the environment variable every time you open a new terminal session.
1. Save the following ControlFlow Python code in a file named `my_number_picker.py`:

    ```python
    from controlflow import Agent, Task, flow

    a1 = Agent(name="A1", instructions="You struggle to make decisions.")
    a2 = Agent(
        name="A2",
        instructions="You like to make decisions.",
    )


    @flow
    def demo():
        task = Task("choose a number between 1 and 100", agents=[a1, a2], result_type=int)
        return task.run()


    if __name__ == "__main__":
        demo()
    ```

1. Run the script from the terminal with `python my_number_picker.py`
1. Check out the results in the terminal.
1. Check out the results in the **Runs** tab in the Prefect Cloud UI. What do you notice?
