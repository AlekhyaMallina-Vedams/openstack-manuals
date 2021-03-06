..
    Warning: Do not edit this file. It is automatically generated from the
    software project's code and your changes will be overwritten.

    The tool to generate this file lives in openstack-doc-tools repository.

    Please make any changes needed in the code, then run the
    autogenerate-config-doc tool from the openstack-doc-tools repository, or
    ask for help on the documentation mailing list, IRC channel or meeting.

.. _manila-api:

.. list-table:: Description of API configuration options
   :header-rows: 1
   :class: config-ref-table

   * - Configuration option = Default value
     - Description
   * - **[DEFAULT]**
     -
   * - ``admin_network_config_group`` = ``None``
     - (String) If share driver requires to setup admin network for share, then define network plugin config options in some separate config group and set its name here. Used only with another option 'driver_handles_share_servers' set to 'True'.
   * - ``admin_network_id`` = ``None``
     - (String) ID of neutron network used to communicate with admin network, to create additional admin export locations on.
   * - ``admin_subnet_id`` = ``None``
     - (String) ID of neutron subnet used to communicate with admin network, to create additional admin export locations on. Related to 'admin_network_id'.
   * - ``api_paste_config`` = ``api-paste.ini``
     - (String) File name for the paste.deploy config for manila-api.
   * - ``api_rate_limit`` = ``True``
     - (Boolean) Whether to rate limit the API.
   * - ``db_backend`` = ``sqlalchemy``
     - (String) The backend to use for database.
   * - ``enable_v1_api`` = ``False``
     - (Boolean) Deploy v1 of the Manila API. This option is deprecated, is not used, and will be removed in a future release.
   * - ``enable_v2_api`` = ``False``
     - (Boolean) Deploy v2 of the Manila API. This option is deprecated, is not used, and will be removed in a future release.
   * - ``max_header_line`` = ``16384``
     - (Integer) Maximum line size of message headers to be accepted. Option max_header_line may need to be increased when using large tokens (typically those generated by the Keystone v3 API with big service catalogs).
   * - ``osapi_max_limit`` = ``1000``
     - (Integer) The maximum number of items returned in a single response from a collection resource.
   * - ``osapi_share_base_URL`` = ``None``
     - (String) Base URL to be presented to users in links to the Share API
   * - ``osapi_share_ext_list`` =
     - (List) Specify list of extensions to load when using osapi_share_extension option with manila.api.contrib.select_extensions.
   * - ``osapi_share_extension`` = ``manila.api.contrib.standard_extensions``
     - (List) The osapi share extensions to load.
   * - ``osapi_share_listen`` = ``::``
     - (String) IP address for OpenStack Share API to listen on.
   * - ``osapi_share_listen_port`` = ``8786``
     - (Port number) Port for OpenStack Share API to listen on.
   * - ``osapi_share_workers`` = ``1``
     - (Integer) Number of workers for OpenStack Share API service.
   * - ``share_api_class`` = ``manila.share.api.API``
     - (String) The full class name of the share API class to use.
   * - ``volume_api_class`` = ``manila.volume.cinder.API``
     - (String) The full class name of the Volume API class to use.
   * - ``volume_name_template`` = ``manila-share-%s``
     - (String) Volume name template.
   * - ``volume_snapshot_name_template`` = ``manila-snapshot-%s``
     - (String) Volume snapshot name template.
   * - **[oslo_middleware]**
     -
   * - ``max_request_body_size`` = ``114688``
     - (Integer) The maximum body size for each request, in bytes.
   * - ``secure_proxy_ssl_header`` = ``X-Forwarded-Proto``
     - (String) DEPRECATED: The HTTP Header that will be used to determine what the original request protocol scheme was, even if it was hidden by an SSL termination proxy.
