# Marketing Team Hackathon

## Setup

Follow the instructions in the [Setup](setup.md) document to get your environment set up and test out Prefect and ControlFlow.

## Build with ControlFlow

Now that we've got things set up and we're starting to see the power of Prefect and ControlFlow, let's tackle a marketing business problem and build a proof of concept to solve it with our tools.

### Problem

Your sales team wants to reach out to existing customers when the customer's company is in the news. Create a flow that will check the news for a customer's company once a day, summarize the news article, and send an email to the sales team with the summary.

Note, this project will require us to use a built-in LangChain tool to give your agent more capabilities.

You will want to use several ControlFlow tasks to fetch the news, extract the news, and summarize it.

For this example, let's assume that the list of Prefect companies is Google, Apple, and Microsoft.

## Create a deployment

Let's turn our flow into a deployment so that we can run the flow on a schedule.

1: Use `.serve` to create a deployment that can run the flow on a schedule.

1. Someone else in the group, trigger a run of the flow from the UI.
1. Create a schedule to run the flow once per day.

### Move your project off your machine

1. Shut down your local server with `control + c`.
1. Use a Prefect Managed work pool to run the flow in Prefect's infrastructure - no worker required.
1. Create a Prefect Managed work pool in the UI.
1. Store your flow code on GitHub.
1. Update your Python code to create a deployment that uses your code on GitHub and your Prefect Managed work pool.

### Create an automation to email

### Additional stretch goals

#### Eexplore deployments

1. Use a Prefect push work pool to run the flow on GCP or AWS.
1. Use a hybrid-type work pool to run the flow with a work pool and a worker.

#### Explore Human-in-the-Loop interactive workflows

1. Pause a workflow and wait for a person to copy in text for summarization.
1. Pause the workflow again for the user to approve or ask for a new summary.

#### Change the Email automation to a Slack message

1. This requires a Slack API key and a Slack channel to send messages to.

#### Choose your own adventure

This has been a pretty structured start, but there are lots of directions you can take it to make it more useful and learn more.
