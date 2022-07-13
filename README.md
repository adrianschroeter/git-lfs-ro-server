OBS Git LFS provider

This service answers git LFS requests and let OBS deliver the files
based on a static database.

This is only supposed to be used for converted sources from classic
OBS source repositories. This is not supposed to be used for sources
which are supposed to be actively maintained in git directly.


### obs_git_lfs

is the server component. It requires the database to be available in

  /etc/obs-git-lfs.db

It runs by default on port 9999 with plain http (no ssl as security is
provided via sha256 checksums).


### obs_git_lfs_admin

is the admin tool to build up the database. There are two ways to call
it, either by specifing all data manualy:

 obs_git_lfs_admin project package source-revision-of-expanded-package filename file-sha256 file-size-in-byte
 
or let the tool building the sha256 sum and checking the file size:

 obs_git_lfs_admin project package source-revision-of-expanded-package local_file_with_correct_filename

You may use an absolute path for the file here, but the filename must be the same 
as in OBS

It creates or extendes an sqlite database in the local working directory:

  obs-git-lfs.db

