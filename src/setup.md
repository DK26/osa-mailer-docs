# Setup

## Preface

Currently, OSA-Mailer simply checks its `outbox` directory each time it is executed. As the development is proceedings towards a stable, complete version, OSA-Mailer is currently built only for Windows (i686 to support both 32bit and 64bit architectures) but of course the source code could be built into any architecture that is supported by LLVM & Rust.

If you wish for an early build for Linux, or any other architectural build, feel free to open a [discussion](https://github.com/DK26/osa-mailer/discussions/new/choose) about it.

Since at this stage there is no point to invest in an installer, nothing special is required but to extract OSA-Mailer from its 7zip archive and to execute the binary on regular cycles (1 minute, 10 minutes, etc.).

The following chapters will provide step-by-step instructions on how to configure and deploy OSA-Mailer.

Download the most current 7zip archive (.7z) asset of OSA-Mailer from the [releases](https://github.com/DK26/osa-mailer/releases) page (e.g. `osamailer-alpha-2.7z`) and follow the instructions in the following chapters.

## Roadmap

- Windows Service (Installer)
- *nix Service (Package)