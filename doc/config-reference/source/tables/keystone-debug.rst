..
    Warning: Do not edit this file. It is automatically generated from the
    software project's code and your changes will be overwritten.

    The tool to generate this file lives in openstack-doc-tools repository.

    Please make any changes needed in the code, then run the
    autogenerate-config-doc tool from the openstack-doc-tools repository, or
    ask for help on the documentation mailing list, IRC channel or meeting.

.. _keystone-debug:

.. list-table:: Description of logging configuration options
   :header-rows: 1
   :class: config-ref-table

   * - Configuration option = Default value
     - Description
   * - **[DEFAULT]**
     -
   * - ``pydev_debug_host`` = ``None``
     - (String) Host to connect to for remote debugger.
   * - ``pydev_debug_port`` = ``None``
     - (Port number) Port to connect to for remote debugger.
   * - ``standard_threads`` = ``False``
     - (Boolean) Do not monkey-patch threading system modules.
   * - **[audit]**
     -
   * - ``namespace`` = ``openstack``
     - (String) namespace prefix for generated id
