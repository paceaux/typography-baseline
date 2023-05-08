# Contributing to typography-baseline.css

This is adapted from the contribution guidelines for normalize.css. But please still take a moment to review this document because there are some differences. The goal of this is still fundamentally the same: make the contribution process easy and effective for everyone involved.

Following these guidelines helps to communicate that you respect the time of the developer(s) managing and developing this open source project. In return, they should reciprocate that respect in addressing your issue or assessing patches and features.

## Using the issue tracker

The issue tracker is the preferred channel for bug reports, features requests and submitting pull requests, but please respect the following restrictions:

    Please do not use the issue tracker for personal support requests.

    Please do not derail or troll issues. Keep the discussion on topic and respect the opinions of others.

## Bug reports

A bug is a demonstrable problem that is caused by the code in the repository. Good bug reports are extremely helpful and detailed. 

Guidelines for bug reports:

1. Use the GitHub issue search – check if the issue has already been reported.

2. Check if the issue has been fixed – try to reproduce it using the latest master branch in the repository.

3. Isolate the problem – create a live example (e.g., on Codepen or JSFiddle). 

A good bug report shouldn't leave others needing to chase you up for more information. Please try to be as detailed as possible in your report. 

* What steps will reproduce the issue? (i.e. The minimum amount of code that shows the problem)
* What browser(s) and OS experience the problem? (i.e. Browsers and operating systems with exact version numbers )
* What would you expect to be the outcome and what _is_ the outcome? (i.e. "was expecting `font-size` to be `17px`, it is `21px` )

All these details will help people to fix any potential bugs.

Example:

    Short and descriptive example bug report title

    A summary of the issue and the browser/OS environment in which it occurs. If suitable, include the steps required to reproduce the bug.

        This is the first step
        This is the second step
        Further steps, etc.

    <url> - a link to the reduced test case

    Any other information you want to share that is relevant to the issue being reported. This might include the lines of code that you have identified as causing the bug, and potential solutions (and your opinions on their merits).

## Feature requests

Feature requests are welcome. But take a moment to find out whether your idea fits with the scope and aims of the project. It's up to you to make a strong case to convince the project's developer(s) of the merits of this feature. Please provide as much detail and context as possible.

This is all about typography; it's not a Table Baseline, or a Form Baseline. We just want to make sure that all things relating to text have a good starting point. 

## Pull requests

Good pull requests - patches, improvements, new features - are a fantastic help. They should remain focused in scope and avoid containing unrelated commits.

Ask first before embarking on any significant work, otherwise you risk spending a lot of time working on something that the project's developer(s) might not want to merge into the project.

Please adhere to the coding conventions used throughout a project (whitespace, accurate comments, etc.) and any other requirements (such as test coverage).

Follow this process if you'd like your work considered for inclusion in the project:

1. Fork the project, clone your fork, and configure the remotes:

    ```
    # Clone your fork of the repo into the current directory
    git clone https://github.com/<your-username>/typography-baseline.css
    # Navigate to the newly cloned directory
    cd typography-baseline.css
    # Assign the original repo to a remote called "upstream"
    git remote add upstream https://github.com/paceaux/typography-baseline.css
    ```

2. If you cloned a while ago, get the latest changes from upstream:

    ```
    git checkout develop
    git pull upstream develop
    ```

3. Never work directly on master (Master is a 1:1 match for NPM). Instead work off of Develop as it contains active work.   Create a new topic branch (off the latest version of develop) to contain your feature, change, or fix. 

    ```
    git checkout -b feature/<topic-branch-name>
    ```


4. Commit your changes in logical chunks. Please adhere to these git commit message conventions or your code is unlikely be merged into the main project. Use Git's interactive rebase feature to tidy up your commits before making them public.

    Be sure that the file is updated if appropriate. 

    Open a Pull Request with a clear title and description to merge your feature into develop

**IMPORTANT**: By submitting a patch, you agree to allow the project owner to license your work under the same license as that used by the project.

## CSS Conventions

Keep the CSS file as readable as possible by following these guidelines:

* Sections are identified in comment blocks
* * Comment sections start with `*=====`
* * Comment sections end with `=====*/`
* * Comment sections "tag" the things the section addresses with a `#` following the subject. This is for searching in the codebase
* * Comment sections within the `:root` have one blank line above and no blank lines below
* * Comment sections for rulesets have two blank lines above, and one blank line below

* Comments are short and to the point.
* comments above a block reference the entire ruleset
* Rules are sorted "inside-out" by how they affect sizing of a box
* Selectors are grouped together in order of likelihood of being used. 


## Maintainers

If you have commit access, please follow this process for merging patches, minor releases, and cutting new releases.

### Accepting patches and minor releases

* Check that a patch is within the scope and philosophy of the project.
* Check that a patch has any necessary tests and a proper, descriptive commit message.
* Test the patch locally.
* Do not use GitHub's merge button. Apply the patch to master locally (either via git am or by checking the whole branch out). Amend minor problems with the author's original commit if necessary. Then push to GitHub.

### Releasing a new version

* Include all new functional changes in the CHANGELOG.
* Use a dedicated commit to increment the version. The version needs to be added to the CHANGELOG (inc. date), the package.json, and normalize.css files.
* The commit message must be of v0.0.0 format.
* Create an annotated tag for the version: git tag -m "v0.0.0" 0.0.0.
* Push the changes and tags to GitHub: git push --tags origin master

### Semver strategy

Semver is a widely accepted method for deciding how version numbers are incremented in a project. Versions are written as MAJOR.MINOR.PATCH.

Almost any change to CSS rules is considered backwards-breaking and will result in a new major release. No changes to CSS _rules_ can add functionality in a backwards-compatible manner, therefore almost no changes are considered minor.

The only exceptions are:

- _Adding_ CSS Variables (without applying them to any rules). This considered a minor release.
- Changes to documentation or the test.html file. This qualifies as a minor release.
- Changes to the linter or tester. This qualifies as a minor release.
- _Corrections_ to documentation count as a patch.
