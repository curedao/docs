---
description: >-
  We use Democratic Pull Requests to enable DAO members to vote on changes to
  the DAO constitution.
---

# 👍 Vote on Amendments to the Constitution

When a Pull Request is made to the main branch, a new comment is posted on the PR where you can click 👍 or 👎. When a Pull Request is updated, it will clear the voting and restart the vote.

## Rules of Voting

[.voting.yml](../.voting.yml) contains the rules of voting:

* `percentageToApprove` is the percentage of up-votes needed to approve a merge.
* `minVotersRequired` is the minimum number of unique voters needed to merge.
* `minVotingWindowMinutes` is the minimum amount of time that must pass after the voting comment is created before any vote can pass. 12 hours was selected because it allows at least 4 hours of review time after subtracting 8 hours for sleep.

## Voters

[.voters.yml](../.voters.yml) defines the allowed voters and their vote weights. Each entry has the format of 
`<github-user>:<voting-weight>`. Each voter will be assigned a vote weight of 1 until and unless a weighting system is democratically approved.

To be added to the voter list, please introduce yourself in the Introductions channel on the Discussions page.
