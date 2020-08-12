# About

You want to become an **official maintainer** of a device? Good! Then this guide is for you!

Before starting you should have read the [Build Guide][build] and so having a working port for the device you want to maintain.

Another hard requirement is the use of [Telegram][tg]: it's free, available on all platforms and nice so have that installed before doing anything else.

# Steps

### Join the main SHRP Telegram groups
1. [SHRP community][community]
1. [SHRP releases][releases]

### Build
- Read and *follow* the [Build Guide][build]
- Build locally on your pc and test with at least 1 or 2 other users (the more the better of course). 
- Do not proceed until you have a fully working build - if needed ask for help in [SHRP community][community]

### Formals
Fill out this little [request form][form] to request becoming a maintainer.

### Request access (TG group)
1. In [SHRP community][community] let the [SHRP team][team] know that you filled out the form (use the `@` before the nickname to notify)
1. In [SHRP community][community] request access to become a member of the **maintainers Telegram group** (you will be invited then).

### Request access (github) 
In the **maintainers TG group** request access to the [device-tree repo][dt] if not given already.

### Upload your tree(s)
Import your device tree to the [device-tree repo][dt]

### CI automation scripts
Add a new *CI script* for your device by 
- *forking* this [CI repo][ci-repo]
- adding your *own* script: filename = device *codename*
- and finally create a *pull request* for that change

### Post your build
- In the **maintainers TG group** write `/get post` to get the TG post template.
- Fill out that template and post it back in the TG group



[team]: https://skyhawk-recovery-project.github.io/#/contact?id=team
[dt]: https://github.com/SHRP-Devices
[build]: guide.md
[community]: https://t.me/sky_hawk
[releases]: https://t.me/shrp_official
[form]: https://forms.gle/ifsMN2hCV3Z5wPFDA
[ci-repo]: https://github.com/SHRP-Devices/ci_scripts
[tg]: https://telegram.org/
