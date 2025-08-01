Service List
------------

These are the edX services that Devstack can provision, pull, run, attach to, etc.
Each service is accessible at ``localhost`` on a specific port.
The table below provides links to the homepage, API root, or API docs of each service,
as well as links to the repository where each service's code lives.

Most developers will be best served by working with specific combinations of these services, for example ``make dev.pull.cms`` or ``make dev.up.ecommerce``. These will pull in dependencies as needed—starting ecommerce will also start lms, and lms will pull in forums, discovery, and others. If you need multiple, they can be listed like ``make dev.up.cms+ecommerce``. After the service table below there is a list of some common combinations.

Instead of a service name or list, you can also run commands like ``make dev.provision`` / ``make dev.pull.large-and-slow`` / ``make dev.up.large-and-slow``. This is a larger list than most people will need for most of their work, and includes all of the services marked "Default" in the below table. (Some of these targets use ``large-and-slow`` in their name as a warning; others may be changed to use this over time.) However, you can change this list by modifying the ``DEFAULT_SERVICES`` option as described in :doc:`advanced_configuration`.

+-------------------------------------------+-------------------------------------+----------------+--------------+
| Service                                   | URL                                 | Type           | Role         |
+===========================================+=====================================+================+==============+
| `lms`_                                    | http://localhost:18000/             | Python/Django  | Default      |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `cms`_                                    | http://localhost:18010/             | Python/Django  | Default      |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `forum`_                                  | http://localhost:44567/api/v1/      | Ruby/Sinatra   | Default      |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `discovery`_                              | http://localhost:18381/api-docs/    | Python/Django  | Default      |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `ecommerce`_                              | http://localhost:18130/dashboard/   | Python/Django  | Default      |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `credentials`_                            | http://localhost:18150/api/v2/      | Python/Django  | Default      |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `edx_notes_api`_                          | http://localhost:18120/api/v1/      | Python/Django  | Default      |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `frontend-app-learner-dashboard`_         | http://localhost:1996/              | MFE (React.js) | Default      |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `frontend-app-learner-record`_            | http://localhost:1990/              | MFE (React.js) | Default      |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `frontend-app-learning`_                  | http://localhost:2000/              | MFE (React.js) | Default      |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `frontend-app-payment`_                   | http://localhost:1998/              | MFE (React.js) | Default      |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `frontend-app-publisher`_                 | http://localhost:18400/             | MFE (React.js) | Default      |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `frontend-app-gradebook`_                 | http://localhost:1994/              | MFE (React.js) | Default      |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `frontend-app-authn`_                     | http://localhost:1999/              | MFE (React.js) | Default      |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `codejail`_                               | http://localhost:18030/             | Python/Django  | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `registrar`_                              | http://localhost:18734/api-docs/    | Python/Django  | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `frontend-app-program-console`_           | http://localhost:1976/              | MFE (React.js) | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `frontend-app-course-authoring`_          | http://localhost:2001/              | MFE (React.js) | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `frontend-app-account`_                   | http://localhost:1997/              | MFE (React.js) | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `frontend-app-profile`_                   | http://localhost:1995/              | MFE (React.js) | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `xqueue`_                                 | http://localhost:18040/api/v1/      | Python/Django  | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `coursegraph`_                            | http://localhost:7474/browser       | Tooling (Java) | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `insights`_                               | http://localhost:18110              | Python/Django  | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `analyticsapi`_                           | http://localhost:19001              | Python/Django  | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `license-manager`_                        | http://localhost:18171              | Python/Django  | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `frontend-app-ora-grading`_               | http://localhost:1993               | MFE (React.js) | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `designer`_                               | http://localhost:18808              | Python/Django  | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `enterprise-catalog`_                     | http://localhost:18160/             | Python/Django  | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `enterprise-access`_                      | http://localhost:18270              | Python/Django  | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `enterprise-subsidy`_                     | http://localhost:18280              | Python/Django  | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `frontend-app-admin-portal`_              | http://localhost:1991               | MFE (React.js) | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `frontend-app-learner-portal-enterprise`_ | http://localhost:8734               | MFE (React.js) | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `frontend-app-enterprise-checkout`_       | http://localhost:1989               | MFE (React.js) | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+
| `edx-exams`_                              | http://localhost:18740              | Python/Django  | Extra        |
+-------------------------------------------+-------------------------------------+----------------+--------------+

Some common service combinations include:

* ``lms``: LMS, along with dependencies ``forum``, ``discovery``, ``Authn`` and some databases
* ``ecommerce``: Ecommerce, but also LMS as a dependency (for auth)
* ``cms+credentials``: Services can be combined to affect both at once

.. _credentials: https://github.com/openedx/credentials
.. _discovery: https://github.com/openedx/course-discovery
.. _ecommerce: https://github.com/edx/ecommerce
.. _edx_notes_api: https://github.com/openedx/edx-notes-api
.. _forum: https://github.com/openedx/cs_comments_service
.. _frontend-app-payment: https://github.com/edx/frontend-app-payment
.. _frontend-app-publisher: https://github.com/openedx/frontend-app-publisher
.. _frontend-app-gradebook: https://github.com/openedx/frontend-app-gradebook
.. _lms: https://github.com/openedx/edx-platform
.. _frontend-app-program-console: https://github.com/edx/frontend-app-program-console
.. _codejail: https://github.com/openedx/codejail-service
.. _registrar: https://github.com/edx/registrar
.. _cms: https://github.com/openedx/edx-platform
.. _frontend-app-learner-dashboard: https://github.com/openedx/frontend-app-learner-dashboard
.. _frontend-app-learner-record: https://github.com/openedx/frontend-app-learner-record
.. _frontend-app-learning: https://github.com/openedx/frontend-app-learning
.. _frontend-app-course-authoring: https://github.com/openedx/frontend-app-course-authoring
.. _frontend-app-account: https://github.com/openedx/frontend-app-account
.. _frontend-app-profile: https://github.com/openedx/frontend-app-profile
.. _frontend-app-authn: https://github.com/openedx/frontend-app-authn
.. _xqueue: https://github.com/openedx/xqueue
.. _coursegraph: https://github.com/openedx/edx-platform/tree/master/cms/djangoapps/coursegraph#coursegraph-support
.. _frontend-app-ora-grading: https://github.com/edx/frontend-app-ora-grading
.. _insights: https://github.com/edx/edx-analytics-dashboard
.. _analyticsapi: https://github.com/edx/edx-analytics-data-api
.. _designer: https://github.com/edx/portal-designer
.. _enterprise-catalog: https://github.com/openedx/enterprise-catalog
.. _license-manager: https://github.com/openedx/license-manager
.. _enterprise-access: https://github.com/openedx/enterprise-access
.. _enterprise-subsidy: https://github.com/openedx/enterprise-subsidy
.. _frontend-app-admin-portal: https://github.com/openedx/frontend-app-admin-portal
.. _frontend-app-learner-portal-enterprise: https://github.com/openedx/frontend-app-learner-portal-enterprise
.. _frontend-app-enterprise-checkout: https://github.com/edx/frontend-app-enterprise-checkout
.. _edx-exams: https://github.com/edx/edx-exams
