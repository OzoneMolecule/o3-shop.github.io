---
title: Migration from OXID 
layout: default
parent: Installation instructions
grand_parent: User manuals
nav_order: 15
permalink: /usermanuals/installation/oxidmigration
---

## Migration from OXID eShop to O3 Shop
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

In principle, a migration between the OXID eShop and O3-Shop is possible, but we recommend a new installation to get a clean installation.

### Requirements for a migration

Please ensure that *all* requirements are met beforehand:

- an error-free Composer installation of the OXID eShop
- OXID eShop in version 6.4.3
For older shop versions, please carry out the update offered by OXID eSales to the named shop version beforehand. Newer OXID shops (> 6.4.3) cannot be migrated.
- OXID eShop Community Edition
The migration only supports Community Editions. The migration of Professional or Enterprise Editions is not supported.
- The OXID eShop was installed via the package "oxid-esales/oxideshop-project".
Check if "oxid-esales/oxideshop-project" is mentioned as "name" in the file "composer.json" in the main directory of your shop. If you use a different package composition, please check its components manually to see if they can be repla>

### Perform migration
#### Create backup

Before migrating, create a backup of the shop. This includes the database and the files on the server.

#### Replace packages

Execute the following Composer commands individually on the console in the main directory of your shop.
```
composer require -W o3-shop/shop-metapackage-ce:^1.0 --no-scripts --no-plugins
composer require -W o3-shop/testing-library:^1.0 o3-shop/shop-ide-helper:^1.0 --dev --no-plugins --no-scripts
composer config extra.incenteev-parameters.dist-file 'vendor/o3-shop/testing-library/test_config.yml.dist'
composer remove oxid-esales/oxideshop-metapackage-ce --no-scripts --no-plugins
composer remove oxid-esales/testing-library:^1.0 oxid-esales/oxideshop-ide-helper:^1.0 --dev --no-scripts --no-plugins
composer require o3-shop/shop-metapackage-ce:^1.0
```

Confirm all overwrite requests with "y".

If the Azure theme is explicitly installed in your shop
```
composer remove oxid-esales/azure-theme --dev
```

#### Data migration

With the current status, no migration of data is necessary.

#### Finishing work

In the case of additional packages installed by OXID or individual compositions of the shop project, please check which packages need to be replaced from "oxid-esales" to "o3-shop".

### Overview of the packages replaced by O3-Shop and their versions

| OXID package                         | OXID version  | O3-Shop package             | O3-Shop version |
|:-------------------------------------|--------------:|:----------------------------|----------------:|
| oxid-esales/oxideshop-project        | dev-b-6.0-ce  | o3-shop/o3-shop             | dev-b-1.0-ce    |
| oxid-esales/oxideshop-metapackage-ce | 6.4.3         | o3-shop/shop-metapackage-ce | 1.0.0           |

```
oxid-esales/oxideshop-ce: 6.10.3                         -> o3-shop/shop_ce: 1.0.0
oxid-esales/oxideshop-composer-plugin: 5.2.2             -> o3-shop/shop-composer-plugin: 1.0.0
oxid-esales/oxideshop-facts: 2.4.0                       -> o3-shop/shop-facts: 1.0.0
oxid-esales/oxideshop-unified-namespace-generator: 2.2.0 -> o3-shop/shop-unified-namespace-generator: 1.0.0
oxid-esales/oxideshop-doctrine-migration-wrapper: 3.3.0  -> o3-shop/shop-doctrine-migration-wrapper: 1.0.0
oxid-esales/oxideshop-db-views-generator: 1.3.0          -> o3-shop/shop-db-views-generator: 1.0.0
oxid-esales/codeception-page-objects: 2.3.0              -> o3-shop/codeception-page-objects: 1.0.0
oxid-esales/codeception-modules: 1.4.2                   -> o3-shop/codeception-modules: 1.0.0

oxid-esales/flow-theme: 3.8.1                            -> o3-shop/flow-theme: 1.0.0
oxid-esales/wave-theme: 1.6.2                            -> o3-shop/wave-theme: 1.0.0
oxid-esales/azure-theme: *                               -> currently discontinued

oxid-esales/oxideshop-demodata-installer: 1.3.0          -> o3-shop/shop-demodata-installer: 1.0.0
oxid-esales/oxideshop-demodata-ce: 6.0.4                 -> o3-shop/shop-demodata-ce: 1.0.0

oxid-esales/paypal-module: 6.4.1                         -> o3-shop/paypal-module: 1.0.0
oxid-esales/gdpr-optin-module: 2.3.3                     -> o3-shop/gdpr-optin-module: 1.0.0
oxid-professional-services/usercentrics: 1.2.1           -> o3-shop/usercentrics: 1.0.0

oxid-esales/testing-library: 8.1.0                       -> o3-shop/testing-library: 1.0.0
oxid-esales/oxideshop-ide-helper: 4.1.0                  -> o3-shop/shop-ide-helper: 1.0.0
oxid-esales/developer-tools: 1.1.0                       -> o3-shop/developer-tools: 1.0.0
oxid-esales/php-selenium: 1.0.5                          -> o3-shop/php-selenium: 1.0.0
oxid-esales/mink-selenium-driver: 1.1.2                  -> o3-shop/mink-selenium-driver: 1.0.0
```
