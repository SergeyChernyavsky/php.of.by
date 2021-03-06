Dev server usage
================
SSH
---
Connect using following credentials:

- Hostname: ``your_host``
- Username: ``<username>``

Samba
-----
Connect using following credentials:

- Folder name: ``\\your_host\<username>``
- Username: ``your_host\<username>``

Creating environment
--------------------

#. It is recommended to use git on your workstation instead of using it on dev server
#. Add SSH key to ``https://github.com/settings/keys``
#. Set domain ``user.name``, ``user.email`` and ``core.autocrlf`` for repo:
   ::

    git config --local user.name "Your Name"
    git config --local user.email "your@email"
    git config --local core.autocrlf input

#. Clone project from ``git@github.com:PHP-Belarus/php.of.by.git`` to ``~/www/phpofby``
#. Copy apache config from ``~/www/phpofby/app/Resources/configs/apache/phpofby_dev.apache`` to ``~/www/phpofby/phpofby.apache``
#. Replace ``<username>`` with your username in ``~/www/phpofby/phpofby.apache``
#. Execute ``sudo a2ensite phpofby_<username>``
#. Check if apache configuration is correct by executing ``/usr/sbin/apache2ctl configtest``
#. Execute ``sudo service apache2 restart`` if apache config is correct
#. Execute ``php phing.phar dependencies-install``
#. Use all values from ``app/config/parameters.yml.dist`` for ``app/config/parameters.yml`` generation.
#. Check application with ``php phing.phar``
#. Add your workstation IP to ``web/config.php`` and ``web/app_dev.php``
#. Check application with ``./bin/symfony_requirements``, ``http://your_host/config.php`` and ``http://your_host/app_dev.php``

Privileges
----------

#. Developers have sudo privilege for executing ``service`` application without password

