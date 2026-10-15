# Cloud build: KernelSU LKM for r9q QGKI 5.4.289

This repository contains Samsung's `r9q_eur_openx` Linux 5.4.289 source.
The workflow at `.github/workflows/build-kernelsu-lkm-r9q.yml` builds a
`kernelsu.ko` module using that exact defconfig.

## Why it uses KernelSU v0.9.5

Upstream KernelSU no longer supports Android kernels older than 5.10. The
final upstream release supporting the 5.4 family is `v0.9.5`; using a newer
release for this source tree is not supported. The workflow intentionally
uses `v0.9.5` and configures `CONFIG_KSU=m`.

## Run it on GitHub

1. Create a **private** repository on GitHub. Do not initialise it with a
   README, licence, or `.gitignore`.
2. Upload the contents of this `Kernel` folder to that repository. The
   `.github` directory must be included.
3. Open **Actions** in GitHub, select **Build KernelSU LKM for Samsung r9q
   QGKI 5.4**, then choose **Run workflow**.
4. Leave the tag as `v0.9.5` and run it. When it completes, download the
   `kernelsu-lkm-r9q-qgki-5.4.289` artifact.

The artifact contains the module, its SHA-256, `modinfo` output, the final
kernel configuration, `Module.symvers`, and the build log.

## Important compatibility boundary

The produced file is for `5.4.289-qgki` and the `r9q_eur_openx` source
configuration only. It must be validated against the running phone before
installation. Building the module does not patch or flash a boot image.
