# Problem

Setuptools contains a bug preventing packages with dependency_links from including in their setup_requires
packages which themselves contain dependency_links.

Here is an example stack trace:

```
Traceback (most recent call last):
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/sandbox.py", line 154, in save_modules
    yield saved
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/sandbox.py", line 195, in setup_context
    yield
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/sandbox.py", line 250, in run_setup
    _execfile(setup_script, ns)
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/sandbox.py", line 45, in _execfile
    exec(code, globals, locals)
  File "/tmp/easy_install-q3o63zpj/tag_versioning-0.0.16/setup.py", line 40, in <module>
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
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/dist.py", line 643, in fetch_build_egg
    links = opts['find_links'][1] + links
TypeError: can only concatenate str (not "list") to str

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "setup.py", line 20, in <module>
    f"https://pypi.fury.io/{_GEMFURY_DEPLOY_TOKEN}/snagajob/tag_versioning/"
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
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/command/easy_install.py", line 679, in easy_install
    return self.install_item(spec, dist.location, tmpdir, deps)
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/command/easy_install.py", line 705, in install_item
    dists = self.install_eggs(spec, download, tmpdir)
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/command/easy_install.py", line 890, in install_eggs
    return self.build_and_install(setup_script, setup_base)
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/command/easy_install.py", line 1158, in build_and_install
    self.run_setup(setup_script, setup_base, args)
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/command/easy_install.py", line 1144, in run_setup
    run_setup(setup_script, args)
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/sandbox.py", line 253, in run_setup
    raise
  File "/usr/local/lib/python3.7/contextlib.py", line 130, in __exit__
    self.gen.throw(type, value, traceback)
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/sandbox.py", line 195, in setup_context
    yield
  File "/usr/local/lib/python3.7/contextlib.py", line 130, in __exit__
    self.gen.throw(type, value, traceback)
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/sandbox.py", line 166, in save_modules
    saved_exc.resume()
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/sandbox.py", line 141, in resume
    six.reraise(type, exc, self._tb)
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/_vendor/six.py", line 685, in reraise
    raise value.with_traceback(tb)
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/sandbox.py", line 154, in save_modules
    yield saved
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/sandbox.py", line 195, in setup_context
    yield
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/sandbox.py", line 250, in run_setup
    _execfile(setup_script, ns)
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/sandbox.py", line 45, in _execfile
    exec(code, globals, locals)
  File "/tmp/easy_install-q3o63zpj/tag_versioning-0.0.16/setup.py", line 40, in <module>
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
  File "/home/circleci/project/.venv/lib/python3.7/site-packages/setuptools/dist.py", line 643, in fetch_build_egg
    links = opts['find_links'][1] + links
TypeError: can only concatenate str (not "list") to str
```

# Description

setuptool's `setup` [calls]([_install_setup_requires]) `_install_setup_requires`:

```
def setup(**attrs):
    # Make sure we have any requirements needed to interpret 'attrs'.
    _install_setup_requires(attrs)
return distutils.core.setup(**attrs)
```

`_install_setup_requires` [calls]([parse_config_files]) `distutils.core.Distribution`'s `parse_config_files`:

```
def _install_setup_requires(attrs):
    # Note: do not use `setuptools.Distribution` directly, as
    # our PEP 517 backend patch `distutils.core.Distribution`.
    dist = distutils.core.Distribution(dict(
        (k, v) for k, v in attrs.items()
        if k in ('dependency_links', 'setup_requires')
    ))
    # Honor setup.cfg's options.
    dist.parse_config_files(ignore_option_errors=True)
    if dist.setup_requires:
dist.fetch_build_eggs(dist.setup_requires)
```

`distutils.core.Distribution.parse_config_files` [calls]([ConfigParser_get]) `ConfigParser`'s `get`.

```
    def parse_config_files(self, filenames=None):
        ...
                for opt in options:
                    if opt != '__name__' and opt not in ignore_options:
                        val = parser.get(section,opt)
                        opt = opt.replace('-', '_')
                        opt_dict[opt] = (filename, val)
        ...
```

The first thing that `get` does is to [call]([_unify_values]) `_unify_values`:

```
d = self._unify_values(section, vars)
```

`_unify_values` stringifies all values, preventing us from combining arrays and strings! (`value = str(value)` below.)

```
    def _unify_values(self, section, vars):
        """Create a sequence of lookups with 'vars' taking priority over
        the 'section' which takes priority over the DEFAULTSECT.

        """
        sectiondict = {}
        try:
            sectiondict = self._sections[section]
        except KeyError:
            if section != self.default_section:
                raise NoSectionError(section) from None
        # Update with the entry specific variables
        vardict = {}
        if vars:
            for key, value in vars.items():
                if value is not None:
                    value = str(value)
                vardict[self.optionxform(key)] = value
        return _ChainMap(vardict, sectiondict, self._defaults)
```

[_install_setup_requires]: https://github.com/pypa/setuptools/blob/v41.0.1/setuptools/__init__.py#L144
[parse_config_files]: https://github.com/pypa/setuptools/blob/v41.0.1/setuptools/__init__.py#L137
[ConfigParser_get]: https://github.com/python/cpython/blob/v3.7.3/Lib/distutils/dist.py#L413
[_unify_values]: https://github.com/python/cpython/blob/v3.7.3/Lib/configparser.py#L780
