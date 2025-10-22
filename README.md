# EDK2 Build and Release Workflow

This repository contains a GitHub Actions workflow designed to automate the process of building and releasing the [tianocore/edk2](https://github.com/tianocore/edk2) UEFI firmware from specific tags.

## How It Works

The workflow performs the following steps:

1.  **Parses Tags**: Takes a comma-separated list of EDK2 tags as input.
2.  **Builds from Source**: For each tag, it checks out the corresponding source code from the `tianocore/edk2` repository.
3.  **Handles Submodules**: Fixes known submodule URL issues and updates all submodules.
4.  **Archives Source**: Creates a `.7z` archive of the complete source code for each tag.
5.  **Builds EFI Shells**: Compiles two versions of the EFI Shell:
    *   A minimal version (`Shell_*.efi`).
    *   A full-featured version (`Shell_2nd_*.efi`).
6.  **Creates GitHub Releases**: For each tag, it creates a new GitHub Release, deleting any existing one for the same tag. The release includes the source code archive and the two EFI shell binaries as assets.

## How to Use

1.  Navigate to the **Actions** tab of this repository.
2.  Select the **EDK2: Build and Release from Tags** workflow from the list on the left.
3.  Click the **Run workflow** dropdown button.
4.  In the **Comma-separated EDK2 tags** input field, enter the tags you want to build (e.g., `edk2-stable202502,edk2-stable202505`).
5.  Click the **Run workflow** button to start the process.

Upon completion, you will find a new GitHub Release for each tag you specified.
