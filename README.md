# CysTerra Official Extension Repository
![Packages Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/cryville/CysTerra.ExtensionRepo/publish_packages.yml?label=Packages)
![GitHub License](https://img.shields.io/github/license/cryville/CysTerra.ExtensionRepo)

CysTerra is a universal geohazard information platform that fetches information related to earthquakes, tsunamis, volcanoes, etc. from various event sources, and combines them into a unified interface with text description, map representation, and text-to-speech output.

This is the official extension repository of CysTerra, containing the extension packages for download in the CysTerra apps.

If you simply want to use the app, please visit the [project page](https://www.cryville.world/Projects/A017) instead.

If you want to learn about extension development, please refer to the [CysTerra extension development documentation](https://docs.eew.cryville.world/).

## Repository Structure
- [`Cryville.EEW.ExtensionRepo`](Cryville.EEW.ExtensionRepo) contains the source of the program that builds the extension repository.
- [`CysTerra.Interfaces`](CysTerra.Interfaces) points to a submodule which contains the libraries required for extension development.
- [`extensions`](extensions) contains the published extension packages.

## Submitting your Extension Packages
You can submit your extension packages to this repository by creating pull requests. Before submission, your extensions must meet the following requirements:

- Your extension MUST be open-sourced with the LGPL license, or the GPL/AGPL license with an exception in the license giving permission to link it with the nonfree applications.
- The name of your extension MUST NOT start with `Cryville` to distinguish it from our first-party components. Consider following the naming pattern described in the [extension development documentation](https://docs.eew.cryville.world/docs/getting-started.html) (the naming pattern is not enforced).

You will want to upload your extensions without downloading existing extensions in the repository. First, fork the repository and clone it sparsely and partially:

```sh
git clone --filter=blob:none --no-checkout https://github.com/<your_account_name>/CysTerra.ExtensionRepo.git
git sparse-checkout init --cone
```

As an additional step, for each initial submission of an extension, add it to the sparse-checkout path:

```sh
git sparse-checkout add extensions/<extension-name>
git checkout master
mkdir extensions/<extension-name>
```

Next, build your extension with the Release configuration and copy the build output to the path `extensions/<extension-name>/universal/<version>/` in the repository (check existing extensions in the repository for examples). Make a commit with the message `bump(<extension-name>): <version>`, push it, and finally open a pull request.
