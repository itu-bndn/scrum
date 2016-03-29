# Scrum

> Our guidelines for how we do Scrum

## Increments

Once a potentially shippable increment is ready as the result of a finished sprint, the associated product should have its version incremented according to [Semantic Versioning](http://semver.org/).

A [GitHub release](https://help.github.com/articles/creating-releases/) is then to be created with a high-level description of the changes made during the sprint and a [changelog](http://keepachangelog.com/) reflecting the exact items finished. Both the tag version and release title must be the product version prefixed by a single _v_ (eg. `v1.0.0`). The following template is to be used for the release description:

```md
This release implements some new feature and fixes various bugs.

### Changes

- #1 Implemented feature xyz
- #2 Fixed bug caused by xyz

[`v1.0.0...v1.1.0`](https://github.com/org/repo/compare/v1.0.0...v1.1.0)
```

## Task board

The task board encompasses all the ongoing projects of the team and is managed using [Waffle.io](https://waffle.io/). The board is divided into the following stages:

-   __Backlog__  
    This is where items of the product backlog are kept and is odered by the product owner. All new [GitHub issues](https://help.github.com/articles/creating-an-issue/) opened in repositories of the team will show up here.

-   __Ready__  
    When an item is ready for a sprint and a [developer has signed up](https://help.github.com/articles/assigning-issues-and-pull-requests-to-other-github-users/) for it, it will be moved to the "Ready" stage and [assigned to the GitHub milestone](https://help.github.com/articles/associating-milestones-with-issues-and-pull-requests/) associated with the sprint. [GitHub pull requests](https://help.github.com/articles/using-pull-requests/) will start out in this stage. The item is then to be given an estimate after which the developer can proceed to work on the item.

-   __In Progress__  
    Once a developer starts working on an item it will be moved to the "In Progress" stage. It is the responsibility of the developer to update the estimate of the item as they progress their work.

-   __Review__  
    Once the developer considers an item done it will be moved to the "Review" stage and [assigned a GitHub label](https://help.github.com/articles/applying-labels-to-issues-and-pull-requests/) of either `major`, `minor`, or `patch` according to [Semantic Versioning](http://semver.org/). Another developer will then be chosen and assigned to perform a code review.

-   __Accept__  
    Once an item has been approved in the "Review" stage, it will be moved to the "Accept" stage for final approval from the product owner.

-   __Done__  
    Once an item is considered done according to the Definition of Done it will be moved to the "Done" stage either by closing or merging the item or manually moving it on the board.

## Estimation

The following Fibonacci point scale is used for estimating the work required for completing a backlog item:

Points  | Meaning
---:    | :---
__1__   | Can solve the issue quickly without needing to research
__2__   | Can solve the issue by researching a little
__3__   | Can solve the issue by researching a medium amount
__5__   | Can solve the issue with a little bit of pair programming or a lot of researching
__8__   | Can solve the issue with a lot of pair programming
__13__  | Issue is not divisible, but is very hard, i.e. requires group work
__21__  | Issue can most likely be subdivided
__34__  | Issue must be subdivided into at least two issues
__55__  | Large issue, must be subdivided into several issues
__89__  | User story should most likely be revised as it encompasses a lot of issues)
__144__ | Ambiguous user story that must be revised as it encompasses too many issues to be divided as-is

## Development

Development of an implementation of a backlog item is carried out in accordance to [GitHub Flow](https://guides.github.com/introduction/flow/) with some additional requirements and tooling support. One of the primary requirements of the development workflow is the use of [protected branches](https://help.github.com/articles/configuring-protected-branches/) in order to enforce the workflow and ensure the integrity of the main product branches.

### Workflow

1.  __Create a topic branch__  
    All work is to be carried out on topic branches to ensure isolation. Make sure that the name of your branch describes the work you'll be doing and that it's written in kebab-case (eg. `my-topic-branch`).

2.  __Add commits__  
    Once your topic branch has been created you can start making the desired changes. Make sure to keep each commit small in order to allow for easy reverts which _can_ and _will_ happen. It's a good idea to use a [GUI client](https://git-scm.com/download/gui/linux) when committing to ease [staging patches](https://git-scm.com/book/en/v2/Git-Tools-Interactive-Staging#Staging-Patches). Also make sure to familiarize yourself with [the seven rules of a great git commit message](http://chris.beams.io/posts/git-commit/).

3.  __Create a pull request__  
    When you've committed and pushed some work it's time to create a pull request against the main product branch. Follow the same guidelines for writing pull request titles and descriptions as you would for commit messages and [assign yourself to the issue](https://help.github.com/articles/assigning-issues-and-pull-requests-to-other-github-users/). If your pull request resolves an existing issue then make sure to state this in either the title or description of the pull request using the [corresponding keywords](https://help.github.com/articles/closing-issues-via-commit-messages/) to associate the pull request with the issue. Once created, your pull request will show up in "In Progress" stage on the task board. Keep in mind that you can continue committing to your branch after the pull request has been created.

4.  __Assign a developer for a code review__  
    Once satisfied with your work it will need a code review from another developer. Move the pull request (or its associated issue) to the "Review" stage on the task board and [assign to the pull request](https://help.github.com/articles/assigning-issues-and-pull-requests-to-other-github-users/) the developer who will review it.

5.  __Implement feedback from the review__  
    If the code review finds anything that needs to be changed then implement and commit the changes to your topic branch. This prompts another review so repeat step 4. If nothing is found and the work is approved then proceed to the next step.

6.  __Squash commits__  
    Now that the code has been finalized it's time to [rebase and squash all the commits](https://robots.thoughtbot.com/git-interactive-rebase-squash-amend-rewriting-history) of your topic branch into a single unit of work on top of the main product branch. If you're not entirely comfortable with rebases it's a good idea to get another developer to help you out.

7.  __Assign the product owner for final approval__

8.  __Merge the pull request__  
    Your pull request is now ready to be merged into the main product branch; well done! :tada:

## Reviewing

After finishing an implementation of a backlog item it must go through a [lightweight code review](https://en.wikipedia.org/wiki/Code_review#Types) performed by a developer different from the one who implemented the code. The review process is managed by [PullApprove](https://pullapprove.com/) and its purpose is to improve the quality and correctness of the code. In addition to checking that all automated checks pass, the developer performing the review should ensure that:

-   __The code is tested__  
    Check that the code is sufficiently tested and that the implemented tests adhere to the specification of the item being implemented.

-   __The code is performant__  
    Within reason, check that the code doesn't contain any known performance pitfalls. If you know of a better way of doing something then suggest it and ideally back it up with a benchmark.

-   __The code is understandable__  
    Check that the code uses sufficiently descriptive function and variable names and is commented appropriately. Other developers will need to read the code down the line as well and must be able to understand it.

-   __The code is well-documented__  
    Check that publically exposed APIs are fully documented as these will be used by other developers who are likely unfamiliar with them. Internal APIs should be sufficiently documented as well.

-   __The code is consistent__  
    Check that the code fits in with the rest of the codebase and follows the code style conventions laid out by the team. Just like in collaborative writing it shouldn't be possible to tell which developer implemented which code by simply looking at it.

-   __The code minimises duplication__  
    Check that the code doesn't add unnecessary duplication and instead reuses code where possible and appropriate.

## License

[![](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/by-sa.svg)](http://creativecommons.org/licenses/by-sa/4.0/)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/)
