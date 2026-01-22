# Contributing

## Preparing the work

If you're planning to work on a large feature, please come discuss in
[#emersion on Libera Chat] before starting the implementation. This will ensure
everybody is on the same page. For very large features, writing a design
document can be very helpful for maintainers.

## Commit log

A [linear, "recipe" style][linear-log] history is used. This means that every
commit should be small, digestible, stand-alone, and functional. Rather than a
purely chronological commit history like this:

    doc: final docs for view transforms
    fix tests when disabled, redo broken doc formatting
    better transformed-view iteration (thanks Hannah!)
    try to catch more cases in tests
    tests: add new spline test
    fix compilation on splines
    doc: notes on reticulating splines
    compositor: add spline reticulation for view transforms

We aim to have a clean history which only reflects the final state, broken up
into functional groupings:

    compositor: add spline reticulation for view transforms
    compositor: new iterator for view transforms
    tests: add view-transform correctness tests
    doc: fix formatting for view transforms

This ensures that the final patch series only contains the final state, without
the changes and missteps taken along the development process. A linear history
eases reviewing, cherry-picking and reverting changes. If you aren't
comfortable with manipulating the Git history, have a look at [git-rebase.io].

## Commit message

The first line of a commit message should contain a prefix indicating what part
is affected by the patch followed by one sentence that describes the change.
For examples:

    database: simplify nested queries
    cmd/dkim-keygen: add option to read private key
    backend/drm: add support for color transforms

If in doubt what prefix to use, look at other commits that change the same
file(s) as the patch being sent.

The body of the commit message should describe what the patch changes and why,
and also note any particular side effects. This shouldn't be empty on most of
the cases. It shouldn't take a lot of effort to write a commit message for an
obvious change, so an empty commit message body is only acceptable if the
questions "What?" and "Why?" are already answered on the one-line summary.

If a commit should close an issue, add a `Closes: <link>` line at the end of
the commit description.

See [notes on commit messages] for a recommended reading on writing commit
messages.

## Review

Smaller changes might be merged with little fanfare, but larger changes will
require more time and effort to review. Some patches might be rejected, for
instance because a new feature is deemed undesirable.

Splitting patches properly into commits (see above) can help a lot reduce
review time. Please feel free to bump your patch by pinging me every two weeks
or so without activity.

If you do get asked to revise the patches, please bear in mind the notes above.
You should use `git rebase -i` to make revisions, so that your patches follow
the clear linear split documented above. Following that split makes it easier
for reviewers to understand your work, and to verify that the code you're
submitting is correct.

## Use of LLMs

Vegetarians don't force their eating habits onto everybody else. In the same
spirit, regardless of the reviewer's opinion about large language models
(LLMs), patches written with the help of LLMs aren't outright rejected as long
as:

- The patch author has a full understanding of the submitted code. The author
  has carefully reviewed the output of the tool used to generate the patch.
- The patch (and assorted description) is indistinguishable from one fully
  written by a human. In particular, the submission doesn't contain huge walls
  of unnecessary text or code.
- The patch author agrees to the [Developer Certificate of Origin]. In
  particular, the author certifies that they have the right to submit the patch
  under the project's open-source license. This can be achieved by adding a
  `Signed-off-by` trailer to the commit description.
- The patch author discloses their use of LLMs in the description. This can be
  achieved by adding an `Assisted-by` trailer to the commit description.

The reviewer may still decide to reject the patch without further
justification.

[#emersion on Libera Chat]: https://web.libera.chat/gamja/#emersion
[linear-log]: https://www.bitsnbites.eu/git-history-work-log-vs-recipe/
[git-rebase.io]: https://git-rebase.io
[notes on commit messages]: http://who-t.blogspot.de/2009/12/on-commit-messages.html
[Developer Certificate of Origin]: https://developercertificate.org/
