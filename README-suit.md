## About `suit-help`

This is a fork of [firefly-help](https://github.com/Caltech-IPAC/firefly-help/).  
This architecture allows the maintenance of a help repository for the Portal
Aspect of the Rubin Observatory/LSST project Science Platform that is customized
to the application of Firefly in that project but that facilitates updating that
documentation with refinements from the upstream Firefly core help repository.

The `suit-help` repository will contain both unique content and content modified
over time to use more Rubin/LSST-flavored examples and references.

The intent is that the fork be updated from the upstream along with each major
Firefly release.

The Firefly team also welcomes pull requests to firefly-help itself that improve
the core documentation.

## Quick Start

#### `git clone https://github.com/lsst/suit-help`

Clone this repository into `suit-help` directory.
`cd suit-help` to perform the other commands.


#### `gradle projects`

List the projects in this repository.  Ignore `root`.

#### `gradle build`

Builds all of the projects.  To build only one project, prefix `build` with the project name, i.e.  `gradle atlas:build`

#### `gradle ${project}:run`

Builds and launches the project's Help applications to your default browser.  
Replace `${project}` with the name of the project you wish to run.


## HOWTOs

### Make update to `suit-help`

All updates should be done in a `feature branch`.  Assuming you are working on Atlas fall of 2020 release.  
To create a branch from the latest changes in `master`:

    git checkout master
    git pull
    git checkout -b atlas_2020_fall
    
Then, make any necessary updates. This will most likely involve changes to the files in `html/atlas` or `atlas_toc.js`.    
Once you are done, commit your changes:

    git commit -am 'a message about your changes'
    
Push your changes to GitHub:

    git push origin head    


(Optional) Squashing Commits

If you created a lot of commits, and wish to squash some or all of them to tidy up the logs:

    git log --oneline master..
    
To print a one-line log of all your commits, not yet in `master`.  
To squash the commits:

    git rebase -i master
    
Replace `pick` with `s` to squash the commit(s), then update the commit message appropriately.
If you have not pushed your changes to GitHub, then a simple `git push origin head` will do.
If you have previously pushed your changes to GitHub, it will produce errors.
In this case, you need to force the push, i.e., `git push -f origin head`.

If you are new to this concept and wish to read more about it, try this: https://blog.carbonfive.com/always-squash-and-rebase-your-git-commits/ -- or do your own research on the web.


Create a Pull Request:

- Goto https://github.com/lsst/suit-help/pulls
- Click on 'New pull request'
- Make sure on the left-hand side say `master`, select your branch from the right-hand side `compare` dropdown.
- Click 'Create pull request'
- Assign someone as a reviewer
- Once reviewed, click 'Merge pull request' to merge your changes to `master`


(Optional) Deploy to IRSA Kubernetes to testing.

- Goto http://irsawebdev5.ipac.caltech.edu:8100/view/IRSA%20k8s/job/ikc_onlinehelp/
- Click 'Build with Parameters' on left toolbar
- Under `BRANCH`, enter your `feature branch` name, i.e `atlas_2020_fall`
- Leave `SUB_DOMAIN` blank to have it deploy to  `atlas-2020-fall.irsakudev.ipac.caltech.edu/onlinehelp/atlas/`




### Make update to `firefly-help`

Updates to `firefly-help` should be done in `firefly-help` repository: https://github.com/Caltech-IPAC/firefly-help

First, clone the repository:

    git clone https://github.com/Caltech-IPAC/firefly-help
    
Then, follow the steps outlined above, but replacing `suit-help` with `firefly-help`.


### To pull `firefly-help` changes to `suit-help`    

Because `suit-help` is a fork of `firefly-help`, you may need to pick up changes that were made to `firefly-help` from time to time.
This process should be done by an admin.    

To sync `suit-help` on github:
- Goto https://github.com/lsst/suit-help/pulls
- Click 'New pull request'
- Select `lsst/suit-help` from the `base repository` dropdown 
- Click on `compare across forks`
- Select `Caltech-IPAC/firefly-help` from the `head repository` dropdown
- Click 'Create pull request'
- Then, click 'Merge pull request' to merge the changes to `master`
- This may require resolving merge conflicts
