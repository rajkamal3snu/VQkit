# Public release safety checklist

This repository is **public**. Never push, copy, fork, or merge the history of the private VQkit source repository into it.

Before attaching a release artifact:

1. Build platform- and Python-version-specific binary wheels from a controlled build environment.
2. Inspect the wheel contents. Confirm private implementation modules are not shipped as readable Python files, and exclude source archives, debugging symbols, private data, keys, credentials and internal paths.
3. Test installation in a fresh isolated environment on each supported platform.
4. Test the command-line entry point and representative VASP/QE workflows.
5. Verify the binary distribution's license and any third-party notices.
6. Attach **reviewed** artifacts to a GitHub Release with checksums and platform requirements.
7. Keep the original development repository private.

**Caution:** `.gitignore` is only an accident-prevention aid. It does not protect files already committed, and compiled extensions can still be reverse engineered.

No binary release should be announced until this checklist has been completed.
