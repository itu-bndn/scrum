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

## License

[![](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/by-sa.svg)](http://creativecommons.org/licenses/by-sa/4.0/)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/)
