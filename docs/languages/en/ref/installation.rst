.. _introduction.installation:

************
Installation
************

Installing Zend Framework 2 is extremely simple. You can download and install the framework in 4 different ways:

- `Download the latest stable release`_ as  ``.zip`` and ``.tar.gz`` file formats;

- Use `Pyrus`_ to install specific components or the entire framework;

- Use `Composer`_ to install specific components or the entire framework.

- Using a `Git`_ client. Zend Framework is open source software, and the Git repository used
  for its development is publicly available on GitHub. Consider using Git to get Zend Framework if you already
  use Git for your application development, want to contribute back to the framework, or need to upgrade your
  framework version more often than releases occur.

  The *URL* for Zend Framework's *Git* repository is:
  `https://github.com/zendframework/zf2`_

Once you have a copy of Zend Framework available, your application needs to be able to access the framework
classes. Though there are several ways to achieve this, for instance we provided a *PSR-0-compliant* autoloading
system using the :doc:`Zend\\Loader\\StandardAutoloader </modules/zend.loader.standard-autoloader>` components
or you can use *Composer* as suggested in the
`ZendSkeletonApplication <https://github.com/zendframework/ZendSkeletonApplication>`_.

Zend provides a :doc:`Getting Started with Zend Framework 2 </user-guide/overview>` to get you up and running as quickly as possible.
This is an excellent way to begin learning about the framework with an emphasis on real world examples
that you can build upon.

Since Zend Framework components are loosely coupled, you may use a somewhat unique combination of them in your own
applications. The following chapters provide a comprehensive reference to Zend Framework on a
component-by-component basis.


.. _`Download the latest stable release`: http://packages.zendframework.com/
.. _`Pyrus`: http://packages.zendframework.com/
.. _`Composer`: http://packages.zendframework.com/
.. _`Git`: http://git-scm.com/
.. _`https://github.com/zendframework/zf2`: https://github.com/zendframework/zf2
.. _`several ways to achieve this`: http://www.php.net/manual/en/configuration.changes.php
.. _`include_path`: http://www.php.net/manual/en/ini.core.php#ini.include-path
.. _`QuickStart`: http://framework.zend.com/docs/quickstart