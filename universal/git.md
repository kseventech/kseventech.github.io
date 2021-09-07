# Git

## Current git workflow

At the moment, the git workflow is not standardized within organization. It is set by the main project developer or by the developers own style.  
Sometimes it is based on the already existing project for which we are outsourcing a developer.  

#### Upcoming improvements

With introduction of CI/CD, there is a definitive need for standardization of some kind.  
Developers need to adapt and update according to this flow, so that new automation improvements deliver updates smoothly.

#### Options

When looking at the options for this standard, I've come across two styles coming from two biggest version control companies:
[ Github Flow ]( https://guides.github.com/introduction/flow/ )
and
[ Gitlab Flow ]( https://docs.gitlab.com/ee/topics/gitlab_flow.html ).  
Both strategies are very similar and there are no real drawbacks between chosing one or the other.  
I am going with Gitlab just because it is compatible with Gitlab CI/CD out of the box.

## Gitlab Flow

[ Gitlab Flow ](https://docs.gitlab.com/ee/topics/gitlab_flow.html) is a simpler alternative to Git flow.  
it is compatible and recommended for use in modern CI/CD systems and workflows.

#### Main branch

Branching in Gitlab flow is simple. It only calls for one primary branch: **main**.  
Feature branches are created from main and merged back when done.  

#### Production branch

When deployment to production needs to happen, a merge request is submitted from main into the production branch.

#### Environment branches

If there are additional environments such as pre-production, Gitlab advocates for a downstream flow where the merge happens first from main to pre-production, and then from pre-production to production. This ensures that everything is tested in all environments.
