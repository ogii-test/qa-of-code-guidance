# Peer review

Peer review of code is a quality assurance activity, where a developer other than the code's author views and tests the usage of a piece of code.

## Motivation

### Why do we need peer review?

Peer review allows a fresh pair of eyes to take a look at your work.
This form of systematic check helps to identify errors in your code and provides feedback on your approach to tackling a problem.
This constructive feedback helps you to improve your code quality and provides confidence in your work.

```{todo}
Must include reference to the AQUA book

Internal and external peer review is required under the AQUA book.

[#24](https://github.com/best-practice-and-impact/qa-of-code-guidance/issues/24)
```

A major benefit of internal review is shared knowledge.
Both the reviewer and reviewee are exposed to new concepts.
It encourages a deeper understanding of what the code is doing.
This can help with future work on the project, as multiple team members have the understanding to maintain the project.

```{todo}
New writing for peer review intro.

Must include more focus on:
- peer review helps reproducibility because peer reviewers have to reproduce the results
- peer review helps quality because it offers constructive challenge
- peer review helps auditability because a transparent review process shines a light on the development process

[#25](https://github.com/best-practice-and-impact/qa-of-code-guidance/issues/25)
```

## What to review

When reviewing code, you should ask yourself the following questions:
* Can I easily understand what the code is doing?
    * Is the code sufficiently documented for me to understand it?
    * Is there duplication in the code that could be simplified by refactoring?
    * Are functions and class methods simple, using few parameters?
* Does the code fulfil its requirements?
* Is the required functionality tested sufficiently?
* How easy will it be to alter this code when requirements change? They always do.
    * Are high level parameters kept in a dedicated configuration file, or Would somebody need to work their way through the code with lots of manual edits to reconfigure for a new run?
* Is the code style consistent?
* Can I generate the same outputs that the analysis claims to produce?
    * Have dependencies been sufficiently documented?
    * Is the code version, data version and configuration recorded?

You might use a review template to formalise review in your development process.
This example is written in Markdown, so that it can be used in Git platform Pull/Merge requests:


```{code-block} md

##  Code review

#### Documentation

Any new code includes all the following forms of documentation:

- [ ] **Function Documentation** as docstrings within the function definition.
- [ ] **Examples** demonstrating major functionality, which runs successfully locally.

#### Functionality

- [ ] **Installation**: Installation or build of the code succeeds.
- [ ] **Functionality**: Any functional claims of new code have been confirmed.
- [ ] **Automated tests**: Unit tests cover essential functions for a reasonable range
  of inputs and conditions. All tests pass on your local machine.
- [ ] **Packaging guidelines**: New code conforms to the project contribution
  guidelines.

#### Final approval (post-review)

The author has responded to my review and made changes to my satisfaction.
- [ ] **I recommend merging this request.**

Estimated time spent reviewing: #

---

### Review comments

*Insert detailed comments here!*

These might include, but not exclusively:

- bugs that need fixing (does it work as expected? and does it work with other code
  that it is likely to interact with?)
- alternative methods (could it be written more efficiently or with more clarity?)
- documentation improvements (does it reflect what the code actually does?)
- additional tests that should be implemented (do the tests effectively assure that it
  works correctly?)
- code style improvements (could the code be written more clearly?)

Your suggestions should be tailored to the code that you are reviewing.
Be critical and clear, but not mean. Ask questions and set actions.

```

Make sure that you share the load on reviewing work within your teams.
Reviewing code from those with more and less experience is beneficial.


## Approaches to code review

### Pair programming

> Two heads are better than one

This practice combines the code writing and review process into one step.
Here, two or three developers work together on a writing a single piece of code.
Each developer takes turns to actively author parts of the code, while others provide real time feedback on the code being written.

This encourages developers to think about and vocalise why they are writing code in a particular way.
It gives reviewers a chance to suggest improvements and question the author's approach as they write code.
The rotational aspect of this practice ensures that all team members gain experience from both the author and review perspective.
From both angles,  you'll learn new techniques and practices.

If used regularly, this approach can help you to get used to receiving constructive feedback and being more open to improve your coding practice.

An alternative is the over-the-shoulder review technique, where one developer authors for the entire session.
This can be useful when working with a mentor, but it is often more useful for a mentor to lead by example.


### Remote review

This approach essentially involves sharing your code with a reviewer, and receiving constructive comments following the review.
This may be an iterative process, until the reviewer is satisfied with the resulting code.

This can work best where changes are small and frequent.
Requesting review of small but regular changes reduces the burden on reviewers, relative to large review of a complete project.
When reviewing larger pieces of work, it may be worth reviewing different aspects of the code is separate passes.
For example, focussing on documentation in one session and then functionality in the next.

The thought of someone else reviewing your code in this way encourages good practices from the outset:
* Clear code and documentation - so that others with no experience can use and test your code
* Usable dependency management - so that others can run your code in their own environment

This form of review is aided by features of most version control platforms, namely the Pull request (or equivalent).
See [](version_control.md) for more information.

```{todo}
There's probably an example from ROpenSci we can point people to for peer review

https://github.com/ropensci/software-review/issues/168

[#26](https://github.com/best-practice-and-impact/qa-of-code-guidance/issues/26)
```