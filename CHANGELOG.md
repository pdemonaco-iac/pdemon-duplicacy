# Changelog

## [1.2.0] - 2026-06-21


### Chore

- *(ci)* Implement lint and release logic

- *(ci)* Update pdk testing

- *(repo)* Updated url & corrected actions

- *(metadata)* Bump dependency version limits


### Other

- *(release)* Publishes to forge

- Consolidated pass test

- Merge pull request #7 from pdemonaco-iac/workflow

chore(ci): implement lint and release logic

- *(release)* Use a github app to bypass rules

- Merge pull request #8 from pdemonaco-iac/workflow2

ci(release): use a github app to bypass rules


## [1.1.0] - 2025-11-16


### Chore

- *(cicd)* REFERENCE.md update at release

- Version bump

- *(cicd)* Fix reference generation


### Feature

- Optional package management

- Sbin in addition to bin


### Other

- Merge pull request #6 from pdemonaco/package_should_be_optional

feat: optional package management


## [1.0.0] - 2025-11-15


### Bugfix

- Specs for existing functionality

- Ruby syntax

- Validation issues & metadata bump


### Chore

- Pdk update

- Update to the current pdk

- Linting & pdk github actions

- Metadata update


### Documentation

- Update documentation & strings

- Update readme & add generation of reference


### Feature

- Ensure the snapshot IDs are valid


### Other

- Merge pull request #1 from pdemonaco/2-fix-ensure-snapshot-ids-are-valid

ensure snapshot ids are valid


### Refactor

- Convert types to structs


## [0.1.0-rc4] - 2019-03-10


### Other

- Log Summary & Tweaks

Added a log summary script which makes the emails sent by the
application a bit cleaner and easier to process. Also, several tiny
tweaks were added to ensure POSIX compliance for the prune and backup
scripts.

- PDK 1.8 Upgrade

Updated to comply with the PDK 1.8 standard.

- Spec Bugfix & Documentation Update

Removed superfluous puppet string type definitions.

- Rework to Types

Switch out all of those crazy in place definitions for actual types.
This vastly simplifies the definitions of data throughout the module and
will allow for easier conversion to Sensitive strings.

- PDK 1.9 and Puppet 6.x

Updating to pdk 1.9 template and ensuring gitlab-ci runs puppet 6.x
tests.

- Type Correction & Minor Tweaks

Missing BackupSchedule entry in the main repository type. Also:
* Used heredoc for long multiline test string
* Added explicit type for b2 url

- Prune Processing Rework

Rewrite of prune functionality as follows:
* a single set of prune parameters can be applied to multiple schedules
in the same repository
* schedules can target other snapshot IDs (repositories) as long as they
  share a storage backend with the master
* bugfixes for the prune emails
* different storage backends can be targeted

Additionally
* rspec-puppet uses the on_supported_os loop as that functionality works
  for Gentoo now

- Merge branch 'alternate-id-snapshots' into 'master'

Prune Processing Rework

See merge request pdemon/pdemon-duplicacy!1


## [0.1.0-rc2] - 2018-10-07


### Other

- Hash Bug

Correcting a bug where the hash parameter for backups can't be passed in
from the wrapper types.

- Cron Entry Arguments

Missing support for arrays as cron-entry arguments. This should fix
that.

- Another Layer for Cron

Missing support for the array arguments at this level too...


## [0.1.0-rc1] - 2018-10-07


### Other

- Initial Commit

Some minor tweaks in the README.md as well as the addition of Gentoo to
the list of supported operating systems.

- Structure for OS Family

Protect against the situation where the os name and os family are the
same. (Future proofing)

- Storage Define Complete

Working up from the bottom apparently.

- Storage & Filters *Done

Mostly complete on these. Maybe need to tweak the way storage is defined
to make it a bit smoother.

- Storage Define

Completed initial work on the storage define. Currently only the b2
backend is supported, however, this should work out the gate as a full
suite of tests have been added to the build infrastructure.

- Filter Testing

Corrected some bugs in filter ensuring that the entries are created in
order.

Additionally, added a series of tests proving this is the case.

- Change in Variable Names

Converted filter_entires to rules improving readability.

- Storage Name Changes

Shorten the variable names for the b2 components to make things easier
to setup

- Storage Update

Added explicit testing of the storage command generation with all
arguments. Additionally, dynamic calculation of the min and max chunk
sizes was explicitly added to the function.

- Remove Puppet 4.x Support

I don't care about testing against older puppet versions.

- Storage Bugfix

Fixed support of unencrypted storage. It wasn't working, but now it is.

- Filter Tests

Added a check to ensure we have the right number of filter rules.

- Environment Script Generation

Reworked the storage define to generate a script which sets the
appropriate parameters for the storage. This script should be sourced by
the backup, prune, and check scripts.

- Rename Env Script

No need to leave a .sh extension on this epp. We're never going to run
it, just sourcing.

- Reworked Script Locations

Repository initialization now creates three subfolders to contain
scripts, logs, and locks for executions. This way we're not messing with
the standard folders.

- Coverage & Tweaks

Changed the tests in the filter spec to align with the repository spec
so coverage is better. Also added coverage to the spec helper.

- Storage Uppercase Keys

Corrected a bug where the environment parameters allowed lowercase
values when inserted into the key names. Also fixed the tests.

- Repository Testing

Cleaned up the naming and parsing for the main repository.

- Backup Job Testing

Created the defined type for scheduling a backup job along with the
supporting script.

Testing still needs to be added to the spec:
* Validate the cron entry
* Check that alternate backup modes build commands appropriately

- Backup Testing

Added more complete testing of the backup script content along with
testing of alternate storage names.

Needs documentation

- Documentation - Filters

Correcting the documentation in the filter defined type manifest so it
is complete and actually useful.

- Filter, Storage, and Repository Documentation

Updated documentation on all three of these pieces to appropriately
generate a REFERENCE.md file. Additionally, "path" parameter was renamed
to "repo_path" so it's nolonger colliding with file/environment path
variables.

- Documentation Rework

Further corrections to the puppet strings in each of the included init
files. Additionally, this includes a rename of the repo_path variable in
the backup defined type to match other instances of that parameter.

- Backup Scheduling

Implemented the calls to actually schedule a backup job from within the
repository definition. This includes testing and some light
documentation of the functionality.

- Add LICENSE

- Duplicacy Class Packages

Now the system ensures both the mail client and the backup application
are installed on the target system. This commit includes tests to verify
this for Gentoo. Other OS's will have to be added in the future.

- Documentation WIP

Adding the current state documentation so I can look at it in rendered
markdown on gitlab.

- Syntax Failure

I forgot to run pdk validate before the last push. :(

- Lookups & Real Deploys

Added the lookup rules for the various datatypes used by this
repository. Additionally, this revision actually creates the target
repos and is hopefully ready for some real-world testing in my
environment.

- Backup Schedule Argument Rework

Updated the schedule argument to use a hash structure at the top level
so it's more intuitive to set within hiera. This also includes some
minor corrections to documentation.

- Backup Script Bugfix

Correction to the path set for the environment variable file. It wasn't
going to work before..

- Quote Environment Variables

This will hopefully resolve a bug during the initialization of a
repository where the password is set to a wrong value possibly due to
variable parsing issues.

- Storage Testing Cleanup

Reduced redundant tests to more complicated single tests on individual
resources.

- Initialization Logging

Record the output of the initialization attempt.

- Documentation & Init Changes

The init command now uses the environment file instead of attempting to
set the environment variables via the exec resource. Additionally, some
changes were made to fix weird rendering problems in the main class
reference documentation.

- Storage - Environment Variables

Returing to using the environment parameter on exec for the storage
commands. We'll used debugging to see what's happening here.

- Password Character Filter

Exclude ' and " as they fuck with shell variable settings and allowing
them would be annoying. Also updated tests to support this filtering.

- Prune Functionality

Initial inclusion of the prune feature. This is nearly identical in
implementation to the backup function.

- Naming of Backups and Logs

Changed the order of name components for both the backup resource and the
log files. Backups nolonger get the word "backup" twice in their name
for no reason.

- Prune Spec Syntax Cleanup

Apparently there was a bit of whitespace leftover as well as a missing
comma on one of the tests. It's fixed now!

- Documentation Update

Cleanup of documentation prior to the beta-release tag.



