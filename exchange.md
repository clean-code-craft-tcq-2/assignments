# Exchange and develop

It's time to take-over code and experience the benefits of clear coding (or the drawbacks of low-clarity)

You are going to take-over and develop the Receiver in phases

## Phase-1: Grant access

1. [Click here](exchange-tcq2.pdf) to see the details of the exchange. Notice the three columns.
1. Look for your GitHub username in the 'sender developer' column
1. In that row, look for the GitHub username in the 'transfer to' column. Grant this user write-access to your repo.

## Phase-2: Peer review

This can go in parallel with Phase-1.

Look for your GitHub username in the 'transfer to' column. The url to the left of it would be the repo you will take-over. Click on that link to access the pull request.

Check if you can understand the sender's interface. Check if it can run and generate output on the console. Enter your comments / questions / compliments. Focus on the code, not the person.

Caution: These are public repos. Do not communicate personal information such as phone numbers, etc. in the comments.

Do not wait for a response to your comments. The Sender's output-format is sufficient to develop the Receiver - you don't need to run the Sender till you reach the integration-phase.

## Phase-3: Check access

Check if you have access to the new repo, which you take-over.

In your old repo, respond to the person who has reviewed your Sender.

## Phase-4: Develop the Receiver

In the repo you have taken-over, write tests for the Receiver: Send data in the format given by the Sender and assert the expected statistics.

Establish a workflow in GitHub Actions to build and test your Receiver.

Code the Receiver in that repo. Let it be testable without having to run the Sender.

## Phase-5: Integrate (optional)

Build both the Sender and your Receiver in a workflow. Pipe the output of the Sender to the Receiver.
