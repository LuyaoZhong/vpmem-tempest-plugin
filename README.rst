=================================================
How to Install VPMEM Tempest Plugin and Run tests
=================================================

#. You first need to install Tempest.

#. Prepare a custom image file on host, and configure the tempest.conf::

    [scenario]
    img_file = cirros-0.4.0-x86_64-disk.img (-> your custom image file)
    img_dir = /home/stack/devstack/files (-> your custom image dir)

#. Install the package from the plugin root directory::

    $ sudo pip install -e .

#. List installed plugin by tempest unity::

    $ tempest list-plugins
    +----------------------+------------------------------------------------+
    |         Name         |                   EntryPoint                   |
    +----------------------+------------------------------------------------+
    | vpmem-tempest-plugin | vpmem_tempest_plugin.plugin:VPMEMTempestPlugin |
    +----------------------+------------------------------------------------+

#. List tempest tests in this plugin::

    $ tempest run --list-tests |grep vpmem_tempest_plugin
    vpmem_tempest_plugin.tests.scenario.test_server_basic_ops.TestServerBasicOps.test_server_basic_ops...
    ...

#. Run tempest tests of this plugin::

    $ tempest run --regex vpmem_tempest_plugin*
