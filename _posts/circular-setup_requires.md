```
Looking in indexes: https://7gHQv-KP9A659oOaUYzBU8YwFZlkwpc@pypi.fury.io/snagajob/, https://pypi.python.org/simple
Collecting snag_setup_helpers
  Downloading https://pypi.fury.io/snagajob/-/ver_1T6EiG/snag_setup_helpers-0.0.2.tar.gz
    ERROR: Complete output from command python setup.py egg_info:
    ERROR: Looking in indexes: https://7gHQv-KP9A659oOaUYzBU8YwFZlkwpc@pypi.fury.io/snagajob/, https://pypi.python.org/simple
    Collecting tag_versioning
      Downloading https://pypi.fury.io/snagajob/-/ver_240Ulr/tag_versioning-0.0.17.tar.gz
        ERROR: Complete output from command python setup.py egg_info:
        ERROR: Looking in indexes: https://7gHQv-KP9A659oOaUYzBU8YwFZlkwpc@pypi.fury.io/snagajob/, https://pypi.python.org/simple
        Collecting snag_setup_helpers
          Downloading https://pypi.fury.io/snagajob/-/ver_1T6EiG/snag_setup_helpers-0.0.2.tar.gz
        ERROR: Exception:
        Traceback (most recent call last):
          File "/home/circleci/project/.venv/lib/python3.7/site-packages/pip/_internal/cli/base_command.py", line 178, in main
            status = self.run(options, args)
          File "/home/circleci/project/.venv/lib/python3.7/site-packages/pip/_internal/commands/install.py", line 352, in run
            resolver.resolve(requirement_set)
          File "/home/circleci/project/.venv/lib/python3.7/site-packages/pip/_internal/resolve.py", line 131, in resolve
            self._resolve_one(requirement_set, req)
          File "/home/circleci/project/.venv/lib/python3.7/site-packages/pip/_internal/resolve.py", line 294, in _resolve_one
            abstract_dist = self._get_abstract_dist_for(req_to_install)
          File "/home/circleci/project/.venv/lib/python3.7/site-packages/pip/_internal/resolve.py", line 242, in _get_abstract_dist_for
            self.require_hashes
          File "/home/circleci/project/.venv/lib/python3.7/site-packages/pip/_internal/operations/prepare.py", line 361, in prepare_linked_requirement
            with self.req_tracker.track(req):
          File "/usr/local/lib/python3.7/contextlib.py", line 112, in __enter__
            return next(self.gen)
          File "/home/circleci/project/.venv/lib/python3.7/site-packages/pip/_internal/req/req_tracker.py", line 94, in track
            self.add(req)
          File "/home/circleci/project/.venv/lib/python3.7/site-packages/pip/_internal/req/req_tracker.py", line 63, in add
            % (link, fp.read()))
        LookupError: https://pypi.fury.io/snagajob/-/ver_1T6EiG/snag_setup_helpers-0.0.2.tar.gz#md5=abb69c3efd1c3879c7035140f3be20d5 (from https://pypi.fury.io/snagajob/snag-setup-helpers/) is already being built: snag_setup_helpers from https://pypi.fury.io/snagajob/-/ver_1T6EiG/snag_setup_helpers-0.0.2.tar.gz#md5=abb69c3efd1c3879c7035140f3be20d5
        Traceback (most recent call last):
          File "<string>", line 1, in <module>
          File "/tmp/pip-install-9073zwqm/tag-versioning/setup.py", line 22, in <module>
            from snag_setup_helpers import load_requirements
        ModuleNotFoundError: No module named 'snag_setup_helpers'
        ----------------------------------------
    ERROR: Command "python setup.py egg_info" failed with error code 1 in /tmp/pip-install-9073zwqm/tag-versioning/
    Couldn't find index page for 'tag_versioning' (maybe misspelled?)
    No local packages or working download links found for tag_versioning
    Traceback (most recent call last):
      File "<string>", line 1, in <module>
      File "/tmp/pip-install-_943dstd/snag-setup-helpers/setup.py", line 33, in <module>
        long_description=open(os.path.join(_HERE, "README.md")).read(),
      File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/__init__.py", line 142, in setup
        _install_setup_requires(attrs)
      File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/__init__.py", line 137, in _install_setup_requires
        dist.fetch_build_eggs(dist.setup_requires)
      File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/dist.py", line 586, in fetch_build_eggs
        replace_conflicting=True,
      File "/home/circleci/project/.venv/lib/python3.7/site-packages/pkg_resources/__init__.py", line 780, in resolve
        replace_conflicting=replace_conflicting
      File "/home/circleci/project/.venv/lib/python3.7/site-packages/pkg_resources/__init__.py", line 1063, in best_match
        return self.obtain(req, installer)
      File "/home/circleci/project/.venv/lib/python3.7/site-packages/pkg_resources/__init__.py", line 1075, in obtain
        return installer(requirement)
      File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/dist.py", line 653, in fetch_build_egg
        return cmd.easy_install(req)
      File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/command/easy_install.py", line 673, in easy_install
        raise DistutilsError(msg)
    distutils.errors.DistutilsError: Could not find suitable distribution for Requirement.parse('tag_versioning')
    ----------------------------------------
ERROR: Command "python setup.py egg_info" failed with error code 1 in /tmp/pip-install-_943dstd/snag-setup-helpers/
Traceback (most recent call last):
  File "setup.py", line 22, in <module>
    from snag_setup_helpers import load_requirements
ModuleNotFoundError: No module named 'snag_setup_helpers'
Exited with code 1
```
