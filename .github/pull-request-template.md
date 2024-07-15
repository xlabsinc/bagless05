# xlabsinc pull request
```
NOTE: pull request should be from a branch in the format <your-login>/github-issue-number 
e.g: xb01/<issue-number>, otherwise pr-lint will not allow you to submit a pull request
```

## Title
Include a title for this pull request which must describe in one line the 
purpose of this change, the title must be prefixed with one of the keywords: 
build, ci, docs, feat, fix, perf, refactor, style, test, add, delete like,
fix: incorrect parameter store value being accessed

## Description
Include a summary of the change and which issue is fixed, user story is 
associated with this change is mandatory.  Please also include relevant 
motivation and context. List if any dependencies that are required for 
this change.
Your pull request body must have the associated user story, cloudcoe-####

## Type of change

Please delete options that are not relevant.
- [ ] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [ ] This change requires a documentation update

## How Has This Been Tested?

Please describe the tests that you ran to verify your changes. Provide instructions so we can reproduce. Please also list any relevant details for your test configuration

- [ ] cfn-lint run, include options that were used to suppress any warnings
- [ ] pylint for any python code, score out of 10
- [ ] Any other tests and validation


## Checklist:

- [ ] My code follows the style guidelines of this project
- [ ] I have performed a self-review of my own code
- [ ] I have commented my code, particularly in hard-to-understand areas
- [ ] I have made corresponding changes to the documentation
- [ ] My changes generate no new warnings
- [ ] I have added tests that prove my fix is effective or that my feature works
- [ ] New and existing unit tests pass locally with my changes
- [ ] Any dependent changes have been merged and published in downstream modules


