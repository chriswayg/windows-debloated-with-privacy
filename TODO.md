# TODO

## Automate App Installation

- Install all Apps, Tools, Utilities and Software using [Chocolatey Software | Chocolatey - The package manager for Windows](https://chocolatey.org/) (if available there)
  - replaces the Install section of Chris Titus Windows Tool
  - replaces individual installs
  - Use [GitHub - computercam/_windowsconf: a simple script to install apps and debloat windows](https://github.com/computercam/_windowsconf) as a starting point

## Automate Configuration   

- Automate configuration using Boxstarter
  - [Automate Windows configurations with Boxstarter and Chocolatey](https://www.techtarget.com/searchitoperations/tutorial/Automate-Windows-configurations-with-Boxstarter-and-Chocolatey)
  - Boxstarter Commands: [Boxstarter | Using Boxstarter Commands](https://boxstarter.org/usingboxstarter)
  - Windows Configuration Commands: [Boxstarter | Boxstarter WinConfig Features](https://boxstarter.org/winconfig)
    - Code: https://github.com/chocolatey/boxstarter/tree/00520040f51007b43c2622dc9cf6005a30098fe8/Boxstarter.WinConfig
  - Run the configuration from a Gist: https://boxstarter.org/learn/weblauncher
  - Probably useful for integrating various debloat scripts
  - Individual account pre-configuration?

## Check other debloat scripts
- [Search · debloat windows · GitHub](https://github.com/search?q=debloat+windows)
  - [Search (sorted by Stars) · debloat windows · GitHub](https://github.com/search?o=desc&q=debloat+windows&s=stars&type=Repositories)
- [GitHub - W4RH4WK/Debloat-Windows-10: A Collection of Scripts Which Disable / Remove Windows 10 Features and Apps](https://github.com/W4RH4WK/Debloat-Windows-10)
- This looks good: [GitHub - LeDragoX/Win-Debloat-Tools: These scripts will Customize, Debloat and Improve Privacy/Performance and System Responsiveness on Windows 10+.](https://github.com/LeDragoX/Win-Debloat-Tools)
- Very interesting Security focused script: [GitHub - simeononsecurity/Windows-Optimize-Harden-Debloat: Fully Optimize, Harden, and Debloat Windows 10 and Windows 11 Deployments to Windows Best Practices and DoD STIG/SRG Requirements. The ultimate Windows 10 & 11 security and privacy script!](https://github.com/simeononsecurity/Windows-Optimize-Harden-Debloat)
- Very Comprehensive Project: [GitHub - farag2/Sophia-Script-for-Windows: The most powerful PowerShell module on GitHub for Windows 10 & Windows 11 fine-tuning and tweaking](https://github.com/farag2/Sophia-Script-for-Windows)
  - [GitHub - Sophia-Community/SophiApp: The most powerful open source tweaker for fine-tuning Windows 10 & Windows 11. The next chapter of the Sophia Script project.](https://github.com/Sophia-Community/SophiApp)
- Combines various scripts and does an Analysis (see also Packages.zip): [GitHub - builtbybel/privatezilla: 👀👮🐢🔥Performs a privacy & security check of Windows 10](https://github.com/builtbybel/privatezilla)


## Modularize

- separate out the hardware specific sections for a more generalized outline and script

## Test in a VM
- using various debloater scripts

## How to validate?
- privacy
- security
- functionality
- is there a test script?
