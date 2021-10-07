# user_defined_in_basic
An ArchivesSpace plugin that displays selected user defined fields in the basic information section


## How to install it

To install, just activate the plugin in your config/config.rb file by
including an entry such as:

     # If you have other plugins loaded, just add 'user_defined_in_basic' to
     # the list
     AppConfig[:plugins] = ['local', 'other_plugins', 'user_defined_in_basic']

And then clone the `user_defined_in_basic` repository into your
ArchivesSpace plugins directory.  For example:

     cd /path/to/your/archivesspace/plugins
     git clone https://github.com/hudmol/user_defined_in_basic.git

Or if you are after a particular release, download and unzip it from here:

https://github.com/hudmol/user_defined_in_basic/releases


## How to configure it (DUKE-SPECIFIC)

Add an entry to your `config.rb` like this:

      AppConfig[:user_defined_in_basic] = {'accessions' => ['boolean_1','text_1','enum_3','date_1','enum_2','enum_1','integer_1','integer_2','real_1','boolean_2','text_2'],'hide_user_defined_section' => true }


If you don't have a `:user_defined_in_basic` entry the plugin won't do anything.
It will log a warning at startup.

The three keys, `accessions`, `resources`, and `digital_objects`, are the
record types that can have a `user_defined` subrecord. For each key specified
a `user_defined` subrecord will be automatically added when a new record
is created through the staff UI, or will be added to an existing record when
it is edited if it doesn't already have one. Also, the remove button is disabled.

For each record type, specify a list of `user_defined` fields that you would like
to see in the `Basic Information`. The fields specified will be moved to the
`Basic Information` section and will appear in the order specified.

If you specify a field that doesn't exist in the `user_defined` record,
a warning will be logged at startup.

The `hide_user_defined_section` key is optional. If specified with a value of
`true`, then the User Defined section will be hidden in View and Edit modes.
This will give a cleaner display, but it means it will only be possible to
edit the user defined fields that have been moved to the Basic Information
section.
