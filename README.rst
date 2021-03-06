.. You should enable this project on travis-ci.org and coveralls.io to make
   these badges work. The necessary Travis and Coverage config files have been
   generated for you.

.. image:: https://travis-ci.org/smotornyuk/ckanext-workflow.svg?branch=master
    :target: https://travis-ci.org/smotornyuk/ckanext-workflow

.. image:: https://coveralls.io/repos/smotornyuk/ckanext-workflow/badge.svg
  :target: https://coveralls.io/r/smotornyuk/ckanext-workflow

=============
ckanext-workflow
=============

.. Put a description of your extension here:
   What does it do? What features does it have?
   Consider including some screenshots or embedding a video!


------------
Requirements
------------

For example, you might want to mention here which versions of CKAN this
extension works with.


------------
Installation
------------

.. Add any additional install steps to the list below.
   For example installing any non-Python dependencies or adding any required
   config settings.

To install ckanext-workflow:

1. Activate your CKAN virtual environment, for example::

     . /usr/lib/ckan/default/bin/activate

2. Install the ckanext-workflow Python package into your virtual environment::

     pip install ckanext-workflow

3. Add ``workflow`` to the ``ckan.plugins`` setting in your CKAN
   config file (by default the config file is located at
   ``/etc/ckan/default/production.ini``).

4. Add next fields to your dataset schema::

          {
              "field_name": "workflow_type",
              "label": "Workflow type",
              "form_snippet": null,
              "validators": "workflow_type_validator"
          },
          {
              "field_name": "workflow_stage",
              "label": "Workflow state",
              "form_snippet": null,
              "validators": "workflow_stage_validator"
          },
          {
              "field_name": "original_id_of_revision",
              "label": "Original dataset",
              "preset": "revision_field"
          }

5. Add workflow presets to scheming(`ckanext.workflow:presets.json`)::

     scheming.presets = ckanext.scheming:presets.json ckanext.workflow:presets.json


6. Restart CKAN. For example if you've deployed CKAN with Apache on Ubuntu::

     sudo service apache2 reload


---------------
Config Settings
---------------

Document any optional config settings here. For example::

    # The email of SEED admin
    # (optional, default: None).

    workflow.site_admin.email = email@example.com

------------------------
Development Installation
------------------------

To install ckanext-workflow for development, activate your CKAN virtualenv and
do::

    git clone https://github.com/smotornyuk/ckanext-workflow.git
    cd ckanext-workflow
    python setup.py develop
    pip install -r dev-requirements.txt


-----------------
Running the Tests
-----------------

To run the tests, do::

    nosetests --nologcapture --with-pylons=test.ini

To run the tests and produce a coverage report, first make sure you have
coverage installed in your virtualenv (``pip install coverage``) then run::

    nosetests --nologcapture --with-pylons=test.ini --with-coverage --cover-package=ckanext.workflow --cover-inclusive --cover-erase --cover-tests


---------------------------------
Registering ckanext-workflow on PyPI
---------------------------------

ckanext-workflow should be availabe on PyPI as
https://pypi.python.org/pypi/ckanext-workflow. If that link doesn't work, then
you can register the project on PyPI for the first time by following these
steps:

1. Create a source distribution of the project::

     python setup.py sdist

2. Register the project::

     python setup.py register

3. Upload the source distribution to PyPI::

     python setup.py sdist upload

4. Tag the first release of the project on GitHub with the version number from
   the ``setup.py`` file. For example if the version number in ``setup.py`` is
   0.0.1 then do::

       git tag 0.0.1
       git push --tags


----------------------------------------
Releasing a New Version of ckanext-workflow
----------------------------------------

ckanext-workflow is availabe on PyPI as https://pypi.python.org/pypi/ckanext-workflow.
To publish a new version to PyPI follow these steps:

1. Update the version number in the ``setup.py`` file.
   See `PEP 440 <http://legacy.python.org/dev/peps/pep-0440/#public-version-identifiers>`_
   for how to choose version numbers.

2. Create a source distribution of the new version::

     python setup.py sdist

3. Upload the source distribution to PyPI::

     python setup.py sdist upload

4. Tag the new release of the project on GitHub with the version number from
   the ``setup.py`` file. For example if the version number in ``setup.py`` is
   0.0.2 then do::

       git tag 0.0.2
       git push --tags
