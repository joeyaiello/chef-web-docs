=====================================================
Install |chef compliance| Server
=====================================================

To install the |chef compliance| server in a standalone configuration, first review the prerequisites and then follow the steps below.

Prerequisites
=====================================================
The |chef compliance| server has the following prerequisites:

* An x86_64 compatible system architecture; |redhat enterprise linux| and |centos| may require updates prior to installation
* A resolvable hostname that is specified using a |fqdn| or an IP address
* A connection to |ntp| to prevent clock drift
* Optional. A local user account under which services will run, a local user account for |postgresql|, and a group account under which services will run. See http://docs.chef.io/install_server_pre.html#uids-and-gids for more information

The following prerequisites apply to every installation of the |chef compliance| server.

Supported Platforms
-----------------------------------------------------
The following table lists the supported platforms for the |chef compliance| server:

.. list-table::
   :widths: 280 100 120
   :header-rows: 1

   * - Platform
     - Architecture
     - Version
   * - |centos|
     -
     - ``6.x``, ``7.x``
   * - |redhat enterprise linux|
     -
     - ``6.x``, ``7.x``
   * - |ubuntu|
     -
     - ``12.04 LTS``, ``14.04 LTS``

Unsupported
+++++++++++++++++++++++++++++++++++++++++++++++++++++
Although you can audit many kinds of servers, the |chef compliance| server itself is not supported on the following platforms:

* Any |linux| or |unix| distribution that is not listed as a supported platform
* |windows|
* 32-bit architectures


Standalone
=====================================================
The standalone installation of |chef compliance| server creates a working installation on a single server. This installation is also useful when you are installing |chef compliance| in a virtual machine, for proof-of-concept deployments, or as a part of a development or testing loop.

To install the |chef compliance| server:

#. Download the package from http://downloads.chef.io/compliance/.
#. Upload the package to the machine that will run the |chef compliance| server, and then record its location on the file system. The rest of these steps assume this location is in the ``/tmp`` directory
#. Install the |chef compliance| package on the server, using the name of the package provided by |company_name|. For |redhat| and |centos| 6:

   .. code-block:: bash

      $ rpm -Uvh /tmp/chef-compliance-<version>.rpm

   For |ubuntu|:

   .. code-block:: bash

      $ dpkg -i /tmp/chef-compliance-<version>.deb

   After a few minutes, the |chef compliance| will be installed.

#. Run the following to start all of the services:

   .. code-block:: bash

      $ chef-compliance-ctl reconfigure

#. Run the following command to create an administrator:

   .. code-block:: bash

      $ chef-compliance-ctl user-create username password

   For example:

   .. code-block:: bash

      $ chef-compliance-ctl user-create admin pA$$word


|amazon aws marketplace|
=====================================================
You can install the |chef compliance| server as an |amazon ami| instance.

Launch the AMI
-----------------------------------------------------
.. include:: ../../includes_cloud/includes_cloud_aws_compliance_launch_ami.rst

Configure the Server
-----------------------------------------------------
.. include:: ../../includes_cloud/includes_cloud_aws_compliance_configure.rst

Ports
+++++++++++++++++++++++++++++++++++++++++++++++++++++
For a |chef compliance| instance that is launched from the |amazon aws marketplace|, the following ports are configured automatically using the one-click installation:

.. list-table::
   :widths: 60 420
   :header-rows: 1

   * - Port
     - Description
   * - 443
     - HTTPS
   * - 22
     - SSH

If the |chef compliance| instance is launched in a way that does not use the one-click installation, these ports may need to be configured manually.

Hostname
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. include:: ../../includes_cloud/includes_cloud_aws_compliance_update_hostname.rst

Edit AMI Instance Size
-----------------------------------------------------
.. include:: ../../includes_cloud/includes_cloud_aws_compliance_change_instance.rst
