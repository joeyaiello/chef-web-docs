.. The contents of this file are included in multiple topics.
.. This file should not be changed in a way that hinders its ability to appear in multiple documentation sets.
.. This file is hooked into a slide deck
.. If changes are made to this file, also update includes_custom_resources_website_final_resource


.. code-block:: ruby

   # continued from previous slide
   
     template "/etc/httpd/conf/httpd-#{instance_name}.conf" do
       source 'httpd.conf.erb'
       variables(
         :instance_name => instance_name,
         :port => port
       )
       owner 'root'
       group 'root'
       mode '0644'
       action :create
     end
   
   ... # continued on next slide
