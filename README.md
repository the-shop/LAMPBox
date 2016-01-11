# LAMP box setup
This repository contains YAML files that define minimal VM setup for dynamic LAMP installation.
 
It includes:
  - Apache2
  - PHP 5.6
  - MySQL 5.6

Note: Contents of this repository are intended to be used with 
[multi box vagrant with puppet setup we provide](https://github.com/the-shop/STARCommerce) only.

## Tweaking resources
This pre-defined setup is intended for development machines with quad core CPUs and at least 8 GB of RAM. If you have 
more than that, feel free to bump up numbers defined in `*.yaml` files (`memory` and `cpus` fields)

## IMPORTANT
**STLL AN EARLY WIP**

**For now, this is intended for local setup only, there might be security implications if used on production 
so please DO NOT USE THIS ON PRODUCTION.**