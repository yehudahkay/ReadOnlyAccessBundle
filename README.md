# ReadOnlyAccessBundle

A Kimai 2 plugin, which allows to give users a readonly access to limited Companies defined in Kimai.

The Developer of this plugin whishes to thank the creator of the CustomCSS Plugin because it was very helpfull. - https://github.com/Keleo/CustomCSSBundle

## Installation

First clone it to your Kimai installation `plugins` directory:
```
cd /kimai/var/plugins/
git clone https://github.com/fungus75/ReadOnlyAccessBundle.git
```

Create (or add if still exist) the file config/packages/local.yml
with this content:
```
kimai:
    permissions:
        sets:
            READONLYACCESSPLUGIN: ['edit_readonly_user', 'view_readonly_customer']
            READONLYACCESSPLUGINADMIN: ['@READONLYACCESSPLUGIN']
            READONLYACCESSPLUGINUSER:  ['@READONLYACCESSPLUGIN','!edit_readonly_user']
        maps:
            ROLE_READONLYACCESS_ADMIN: ['READONLYACCESSPLUGINADMIN']
            ROLE_READONLYACCESS_USER:  ['READONLYACCESSPLUGINUSER']
```
Make sure that you just use spaces and no tabs!


And then rebuild the cache: 
```
cd /kimai/
bin/console cache:clear
bin/console cache:warmup
```

## Permissions

This bundle ships a new administration screen, which will be available for the following users:

- `ROLE_SUPER_ADMIN` - every super administrator
- `edit_custom_css` - every use that owns this permission 
 
## Storage

This bundle stores the custom CSS rules in the file `var/data/custom-css-bundle.css`. 
Make sure its writable by your webserver!

## Screenshot

![Screenshot](https://raw.githubusercontent.com/Keleo/CustomCSSBundle/master/screenshot.jpg)
