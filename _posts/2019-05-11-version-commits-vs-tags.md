---
layout: post
title:  "Software versioning: commits vs. tags"
date:   2019-05-11 13:57:19 -0400
categories: version git tag commit
---
Some notes to myself about why I prefer to version source-controlled software
using Git tags instead of commits:

* Version commits pollute the commit history with messages irrelevant to changes
  in functionality
* Version commits can create merge conflicts if a PR is based on an incremented
  version and another version goes to the integration branch while the PR is out
* CI commits can fail the build if two PRs are merged close together: when the
  first build tries to push the commit with the updated version, it will fail
  because it does not have the second commit.
* CI commits require developers to pull commits every time they push to CI,
  even if they are the only ones who have committed.
* Version commits can makes it difficult to match up other tags that were added
  to the commit on which the version commit is .

Problems with Git commits:
* Github doesn't (yet) provide protection of tags, so someone might delete them
  from the remote repository.  There are some community calls for the feature
  in the [Github Community Forum][forum] and [the unofficial Github issues repo][isaacs].
  * A workaround is being notified when a tag changes, at least, so that
    you can audit and restore.
* For Python, there is better tooling around version commits ([bumpversion]) than
  around managing versions in tags.

[forum]: https://github.community/t5/How-to-use-Git-and-GitHub/Feature-Request-Protected-Tags/td-p/19028
[isaacs]: https://github.com/isaacs/github/issues/1091
[bumpversion]: https://github.com/peritus/bumpversion
