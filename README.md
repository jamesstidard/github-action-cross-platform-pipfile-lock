# Cross-Platform Pipenv Lock GitHub Workflow
The lock file produced by `pipenv` is specific to the platform
it was created on. This can mean that platform specific dependencies
can be missing after running `pipenv sync` on another platform.

You cannot ask pipenv to produce a cross-platform lock file, instead
you must run `pipenv lock --keep-outdated` on each platform to append
their platform specific dependencies to the lock file without removing
the previous platforms.

This workflow (`.github/workflows/cross-platform-lock.yml`) is a example 
that produces a cross-platform `Pipfile.lock` whenever it detects a change
to the dependencies, and recommits the cross-platform lock file back to
the repository.
