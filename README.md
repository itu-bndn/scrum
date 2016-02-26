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

## License

[![](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/by-sa.svg)](http://creativecommons.org/licenses/by-sa/4.0/)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/)
