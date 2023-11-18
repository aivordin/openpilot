# Hardcoded Fingerprint comma.ai openpilot Continuous Micro-Fork Generator

![label_of_a_large_fingerprint_logo_on_a_single_prescription_pill_bottle_that_is_transparent_orange__product_image_](https://github.com/hardcoded-fp/openpilot/assets/5363/e209996e-d1dc-45ff-8745-c5fbeea4573c)

*PRESCRIPTION ONLY: Consult your vehicle brand's [Discord channel](https://discord.comma.ai) for guidance first.*

## How and Why to Use

Open comma.ai openpilot fingerprinting issues: https://github.com/commaai/openpilot/issues?q=is%3Aissue+is%3Aopen+fingerprint

openpilot queries the firmware of your vehicle upon start and configures itself to your vehicle accordingly with a list of pre-existing firmwares in the codebase. This process is called [Fingerprinting](https://github.com/commaai/openpilot/wiki/Fingerprinting). If you currently see an error of `Car Unrecognized: Dashcam Mode`, you should try to go through the [fingerprinting guide](https://github.com/commaai/openpilot/wiki/Fingerprinting). *Please make sure to follow the suggestion in the guide to try the `master-ci` branch first and reaching out to the vehicle brand's Discord channel if you have issues.*

If you are having trouble going through the fingerprinting guide and after consulting the vehicle brand's Discord channel, you may agree to use this repository to install a version of openpilot on your vehicle with a hardcoded fingerprint so you can get things working ASAP. This method does not require knowledge of SSH, editing code, or modifying system files.

_Be aware that choosing and setting an erronous fingerprint can and usually will cause your vehicle and openpilot to behave unexpectedly_. **To repeat, consult your vehicle brand's Discord channel for guidance first.**

This repository is not to be considered a replacement for proper fingerprinting and should be used as an emergency, last, and temporary resort. As such, it does not apply cosmetic changes to the UI to disable warning messages such as "untested branch" as that is a genuine warning. Users and resident vehicle brand experts prescribing this should campaign and create a [pull request for the proper upstreaming of their fingerprints to the official openpilot repository](https://github.com/commaai/openpilot/pulls). The commits of this repository are direct child commits of the official commits.

This GitHub repository periodically continuously generates openpilot branches off of openpilot's "deployment"-style and "unstable" `master-ci` branches with a hardcoded fingerprint identification of the vehicle for the purpose of installing the "unstable" `master-ci` flavor of openpilot on un-fingerprinted vehicles where there is currently fingerprinting trouble.

The branches here should be considered a temporary solution until the official openpilot repository is updated with the necessary fingerprints in the "unstable" `master-ci` branch. At which point, users should switch back to the official openpilot branches of "unstable" `master-ci` once their desired fingerprints are added to that branch.

A common feature suggestion for comma.ai's openpilot is to have a selectable vehicle selector in the settings if a vehicle is unrecognized. This is a temporary out-of-openpilot-codebase solution until such functionality is implemented and present. This repository may still be useful in the case of [false positives](https://github.com/commaai/openpilot/issues/28483) if such a selector is implemented and if access to it is unavailable due to the false positive.

The generator only hardcodes fingerprints for vehicle identification. It will not override "Dashcam Only" in the code such as in this file for Ford: https://github.com/commaai/openpilot/blob/fa353401f44751d88ffdc583449177451d726d63/selfdrive/car/ford/interface.py#L17.

You can see a list of fingerprint models, their corresponding installer URLs for the [URL installer](https://github.com/commaai/openpilot/wiki/Forks#url-installers-at-installation-screen), and a link to a GitHub view of the branches here:

https://hardcoded-fp.github.io/openpilot/

## "Stable" `release3` Option

This GitHub repository also periodically continuously generates openpilot branches off of openpilot's "deployment"-style "stable" `release3` branches with a hardcoded fingerprint identification of the vehicle for the purpose of installing the respective "stable" `release3` flavors of openpilot on un-fingerprinted vehicles where there is currently a massive lag in the freshness of fingerprints in the "stable" `release3` compared to the "unstable" `master-ci` that has more current fingerprints but they want the possible increased "stable" `release3`'s stability.

Users who are forcing a fingerprint on "stable" `release3` to take advantage of the stability not present in `master-ci` should note that forced fingerprinting identities of vehicles into "stable" `release3` may turn it "unstable" and may cause unexpected behavior. Specific fingerprint data has historically been used to work around bugs in interactions with the vehicle of certain firmwares and such workarounds may not be present in the base "stable" `release3` codebase. If "stable" `release3` turns out to be "unstable", users should switch to the "unstable" `master-ci` branch and work with the community and developers to make it "stable" again in time for the next release of the "stable" `release3`.

## Design Questions

### How often are the branches generated?

Every day. If the base commits haven't changed, the generated commits have a stable hash and will not change.

### Custom Forks?

This is generally not necessary for other forks as many of them have vehicle selectors. This is only useful for openpilot codebases without selectors such as comma.ai's official openpilot.

### Why not dynamically generate the installer and inject the fingerprint?

Injecting the fingerprint with the installer may produce non-pushed commits and/or non-commited code that can only be found on the device itself. By producing these branches periodically with GitHub, the commit on the device will have a commit in GitHub that can be referenced if help is sought.
