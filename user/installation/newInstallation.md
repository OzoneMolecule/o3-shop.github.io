---
title: new installation 
layout: default
parent: Installation instructions
grand_parent: User manuals
nav_order: 10
---

# Installation instructions
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## Command

Install Composer in version 2.2.x ([https://getcomposer.org](https://gecomposer.org)).

Execute the command in the desired installation directory:

```
composer create-project --no-dev o3-shop/o3-shop your_project_name dev-b-1.0-ce
```

The domain for the shop must point to the `source` folder.

Call up your shop via its URL and go through the setup process.

Further contents:

## Permission settings

Read and write access is required for the directories listed below and their subdirectories:

- /source/export
- /source/log/
- /source/out/pictures/
- /source/out/media/
- /source/tmp/
- /var/

also the CLI (Command Line Interface) user needs read and write access to the /var/ directory.

Regarding the browser-based setup, the HTTP server must have write access to the following directory and these files:

- /source/Setup
- /source/config.inc.php
- /source/.htaccess

After completing the installation, remove the write permissions for the file "config.inc.php".

## further steps
