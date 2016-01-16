# GenericLAMP Virtual box setup
This repository contains YAML files that define single LAMP box. 

Note: Contents of this repository are intended to be used with 
[multi box vagrant with puppet setup we provide](https://github.com/the-shop/STARCommerce) only.

## Setup
  - Put the code of projects you want to execute through this box in `BoxData/GenericLAMP` directory of main project
  - Hosts setup: 
    - Box IP is `192.168.56.200`
    - There's no limit on projects you can host on this box
    - Apache on this box is set for 
    [mass virtual hosting based of domain](https://httpd.apache.org/docs/2.2/vhosts/mass.html)
    - If project you want to run contains `index.php` in root of the project directory, for example Magento 1, and given
    that project folder is called `magento1`, then the naming convention is to set the URL to be 'magento1.local'. 
    `.local` TLD means that in this particular case Apache will expect index.php to live at 
    `BoxData/GenericLAMP/magento1/index.php` location
    - If your project `index.php` is in subdirectory of your project, for example for Magento 2 where main site 
    index.php lives in `<PROJECT_ROOT_DIR>/pub` directory, Apache will read every other TLD that is not ".local" and 
    assume that provided TLD is name of the subdirectory. In this particular case, given your Magento 2 root directory 
    is named "magento2", URL that will map to `BoxData/GenericLAMP/magento2/pub/index.php` is `magento2.pub`
    - All other subdirectory names will work using explained `TLD <=> directory` schema, i.e. `test.public_html` will 
    map to `BoxData/GenericLAMP/test/public_html/index.php` file 
    - If you'd use all of the examples provided above, you could update your 
    [hosts file](https://en.wikipedia.org/wiki/Hosts_(file)#Location_in_the_file_system). Database can be accessed at 
    with following lines:
      - `192.168.56.200 magento1.local`
      - `192.168.56.200 magento2.pub`
      - `192.168.56.200 test.public_html`
    - This setup behaves as standard WAMP, MAMP,... with the exception of mapping `index.php` location based of TLD 

## Tweaking resources
This pre-defined setup is intended for development machines with quad core CPUs and at least 8 GB of RAM. If you have 
more than that, feel free to bump up numbers defined in `puphpet/boxes/*.yaml` files (`memory` and `cpus` fields)

## IMPORTANT
**For now, this is intended for local setup only, there might be security implications if used on production 
so please DO NOT USE THIS ON PRODUCTION.**