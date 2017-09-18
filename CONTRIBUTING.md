# Contributing to *PROJECT NAME*

**Instructions**: This template provides the documentation boilerplate needed
to guide your users through the contribution process.

- Include your communication channels in the **General questions** section
- Add or remove requirements to the bug reports as needed in the
  **Bug and issues** section
- Adjust the times and labels to match your rules in the **Triaging issues**
  section
- The instructions in the **Submitting contributions** section are considered
  best practices but may not be suited to your workflow.
  Details you should pay attention:
    - Change `<upstream-owner>` and `<repo-name>` with your data
    - Change `<dev-branch>` to your actual development branch (master,
      development, etc)
    - If you use a particular git or branching workflow, describe it
    - Add your coding conventions
    - This template suppose your change log follows the  *Keep a Changelog*
      format
    - Specify how to run your project's tests
- Specify your approval process
- Finally, be nice with your users and let them know you care about their
  contributions

Feel free to edit the text below and remove these instructions.

---

This document contains a set of guidelines to help you during the contribution
process.
Please review it in order to ensure a fast and effective response from the
maintainers and volunteers.

We are happy to welcome all contributions from anyone willing to improve this
project.
We expect you to follow the [Code of Conduct](CODE_OF_CONDUCT.md).
Thank you for helping out and remember, no contribution is too small.

## Table Of Contents

- [General questions](#general-questions)
- [Issues and bugs](#issues-and-bugs)
- [Feature requests](#feature-requests)
- [Issue triaging](#issue-triaging)
- [Submitting contributions](#submitting-contributions)
    - [Sign your work](#sign-your-work)
- [Additional notes](#additional-notes)
- [References](#references)

## General questions

The main function of the issue tracker is to record bug reports and feature
requests.
For general questions you can look the [documentation] to learn more about
the project and find some examples.
If you still have questions please consider using [Stack Overflow].
You can get in touch directly with us or helpful people using the following
media:

- Slack Channel
- IRC channel
- Mailing list
- Other resources

## Issues and bugs

Before creating a new issue please search for similar issues, open or closed,
to see if someone else has already noticed the same problem and possible
solutions.
Do not comment on open issues unless you can provide more information to
resolve it.
Use the subscribe function to keep up-to-date with the report or the voting
system to support it.
When you can't find a previous report open an issue keeping in mind the
following considerations:

- Try to reproduce the bug using the code found on the master branch to ensure
  it hasn't been fixed
- Fill the bug report template with all the information requested
- Provide a failing test case or an example with step by step instructions to
  reproduce the bug
- Copy and paste the full error message, including the backtrace
- Be as detailed as possible and include any additional information relevant to
  the report

## Feature requests

If you want to request or implement a new feature please submit an issue
describing the details and possible use cases.
When the feature can be implemented as a plugin/extension/external package
please do so to maintain the code base as small and simple as possible.
Features that break backwards compatibility must provide good reasons to do it
and a deprecation note when applicable.

## Issue triaging

Another great way to contribute is helping to triage issues.
Label any new report as *bug* to allow for easy search and classification.
Once the issue has been reviewed it should be tested to confirm it is an actual
bug.
When the problem cannot be reproduced ask the OP for more information and label
as *need-info*.
Wait for a reply at least one week before pinging the OP as an attention call
and label the issues as *waiting-response*.
If there is no response after one month the issue can be closed due the lack of
information and reproducibility.
If the bug can be reproduced label it as *confirmed* and use all the relevant
labels to make management easier.

In any case, please search for related issues and add references to them.
Label duplicated bugs when there are previous reports and redirect users to the
current comments thread to keep discussions focused and concentrated in one
place.

Label feature request issues as *new-feature*.
Depending on the request add the labels *need-opinions*, *breaking-change*,
*help-wanted*, *up-for-grabs*, *easy-pick*, etc.

## Submitting contributions

We are glad to receive code contributions in the form of patches, improvements
and new features.
Below you will find the process and workflow used to review and merge your
changes.

### Step 0: Find or create an issue

Every change in this project should/must have an associated issue.
If you want to contribute a patch, comment on the bug report to let the
maintainers, volunteers and interested people know you are working on it.
If you want to contribute a new feature or code improvement open a new issue
first to discuss it and be sure the maintainers will want to merge it before
working.

### Step 1: Fork the project

Fork the project and work on your own copy.
Keep a reference to the original project in `upstream` remote.

```sh
git clone https://github.com/<your-username>/<repo-name>
cd <repo-name>
git remote add upstream https://github.com/<upstream-owner>/<repo-name>
```

If you have already forked the project, update your copy before working.

```
git remote update
git checkout <dev-branch>
git rebase upstream/<dev-brach>
```

### Step 2: Branch

Create a new branch. Use its name to identify the issue your addressing.

```sh
git checkout -b ###-issue-name
```

### Step 3: Code

- **Follow the code conventions**: Through this project we use the following
  conventions:
    - Use [semantic linewrapping] with a hard limit at 80 columns when editing
      markdown files
    - Linting rules
    - Additional rules

- **Document your changes**: Add or update the relevant entries for your change
  in the documentation to reflect your work and inform the users about it.
  If you don't write documentation, we have to, and this can hold up acceptance
  of your changes

- **Add unit tests**: If you add or modify functionality, it must include unit
  tests.
  If you don't write tests, we have to, and this can hold up acceptance of
  your changes

- **Update the CHANGELOG**: Once you meet all previous requirements, add an
  entry to the *Unreleased* section of the change log.
  Again, if you don't update the CHANGELOG, we have to, and this holds up
  acceptance.

### Step 4: Commit

Try to commit as often as you can, keeping your changes logically grouped
within individual commits.
Generally it's easier to review changes that are split across multiple commits.

```sh
git add changed-file-1 changed-file-2
git commit
```

A good commit message should describe what changed and why.
Follow these guidelines when writing one:

1. Use the imperative, present tense: "change" not "changed" nor "changes"
1. The first line should contain a short description of the change in 50
   characters or less.
1. Do not end the description with a dot
1. The description must be in lowercase
1. Use the format `<type>(<scope>): <subject>`, where scope refers to the
   subsystem changed and type could be:
    - **chore**: Changes to the build process or auxiliary tools and libraries
      such as documentation generation
    - **docs**: Documentation only changes
    - **feat**: A new feature
    - **fix**: A bug fix
    - **refactor**: A code change that neither fixes a bug nor adds a feature
    - **style**: Changes that do not affect the meaning of the code
      (white-space, formatting, missing semi-colons, etc)
    - **test**: Adding missing or correcting existing tests
1. Keep the second line blank
1. Use the rest of the message to explain the patch in detail
1. Wrap the message's body at 72 columns
1. Add a reference to the related issue at the end.
   Use the `Fix:` prefix and the full issue URL
1. For other references use `Ref:`

Use git interactive rebase if you need to tidy up your commits.

### Step 5: Rebase

Rebase your branch to include the latest work on your branch and resolve
possible merge conflicts.

```sh
git fetch upstream
git rebase upstream/<dev-branch>
```

### Step 6: Test

Bug fixes and features should have tests and avoid breaking tested code.
Run the test suite and make sure all tests pass.
Run the linter to verify your code follows the coding style and conventions.
Please do not submit patches that fail either check.

```sh
test command
```

### Step 7: Push

When your work is ready and complies with the project conventions,
upload your changes to your fork:

```sh
git push origin <branch-name>
```

### Step 8: Pull request

Open a new Pull Request from your working branch to `<dev-branch>`.
Write about the changes and add any relevant information to the reviewer.
Add a reference to the related issue with `Fix: ###` or `Close: ###`,
depending if the pull request fixes a bug or adds a new feature,
at the end of the PR message, where ### is the number of the issue.

### Step 9: Review and approval

**Note**: Add here your approval process.

### Sign your work

Please sign your work using your real name because your signature certifies
that you wrote it or otherwise have the right to contribute it according to
the DCO below.
To do it just add a line to every git commit message:
`Signed-off-by: Joe Smith <joe.smith@email.com>`.
You can sign your commit automatically with git commit -s. 

```
Developer Certificate of Origin
Version 1.1

Copyright (C) 2004, 2006 The Linux Foundation and its contributors.
1 Letterman Drive
Suite D4700
San Francisco, CA, 94129

Everyone is permitted to copy and distribute verbatim copies of this
license document, but changing it is not allowed.


Developer's Certificate of Origin 1.1

By making a contribution to this project, I certify that:

(a) The contribution was created in whole or in part by me and I
    have the right to submit it under the open source license
    indicated in the file; or

(b) The contribution is based upon previous work that, to the best
    of my knowledge, is covered under an appropriate open source
    license and I have the right under that license to submit that
    work with modifications, whether created in whole or in part
    by me, under the same open source license (unless I am
    permitted to submit under a different license), as indicated
    in the file; or

(c) The contribution was provided directly to me by some other
    person who certified (a), (b) or (c) and I have not modified
    it.

(d) I understand and agree that this project and the contribution
    are public and that a record of the contribution (including all
    personal information I submit with it, including my sign-off) is
    maintained indefinitely and may be redistributed consistent with
    this project or the open source license(s) involved.
```

## Additional notes

Any note and indication not covered above will be here.

## References

Add here references. Include all kind of references from git tutorials to
project-specific topics.


[documentation]: #
[Stack Overflow]: http://stackoverflow.com/
[semantic linewrapping]: https://scott.mn/2014/02/21/semantic_linewrapping/
