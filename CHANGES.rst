Changelog
=========

UNRELEASED
----------

- The project has moved to `Jazzband <https://jazzband.co/>`_. This is the
  first release under the new organization. The new repository URL is
  `<https://github.com/jazzband/django-redis>`_.
- Removed support for end-of-life Django < 2.2.
- Removed support for unmaintained redis-py 2.X.

Version 4.11.0
--------------

Date: 2019-12-13

- Removed support for Python 2.7 and 3.4.
- Removed support for Django 2.0 and 2.1.
- Added support for Python 3.8.
- Added support for Django 2.2 and 3.0.
- Changed msgpack-python soft dependency to msgpack.
- Fixed ``.touch()`` method for sharded client.
- Fixed prefix escaping for the sharded client.
- Fixed ``.add()`` method to return a bool.

Version 4.10.0
--------------

Date: 2018-10-19

- Add support and testing for Django 2.1 and Python 3.7. No actual code changes
  were required.
- Add support for redis-py 3.0.
- Add touch command.


Version 4.9.1
-------------

Date: 2018-10-19

- Pin redis version to 2.10.6


Version 4.9.0
-------------

Date: 2018-03-01

- Add testing and support for Django 2.0. No actual code changes were required.
- Escape ``KEY_PREFIX`` and ``VERSION`` when used in glob expressions.
- Improve handling timeouts less than 1ms.
- Remove fakeredis support.
- Add datetime, date, time, and timedelta serialization support to the JSON
  serializer.
- The deprecated feature of passing ``True`` as a timeout value is no longer
  supported.
- Fix ``add()`` with a negative timeout to not store key (it is immediately
  invalid).
- Remove support for Django < 1.11.
- Add support for atomic incr if key is not set.


Version 4.8.0
-------------

Date: 2017-04-25

- Drop deprecated exception with typo ConnectionInterrumped. Use
  ConnectionInterrupted instead.
- Remove many workarounds related to old and not supported versions
  of django and redis-py.
- Code cleaning and flake8 compliance fixes.
- Add better impl for ``close`` method.
- Fix compatibility warnings with python 3.6


Version 4.7.0
-------------

Date: 2017-01-02

- Add the ability to enable write to slave when master is not available.
- Add ``itersize`` parameter to ``delete_pattern``.


Version 4.6.0
-------------

Date: 2016-11-02

- Fix incorrect behavior of ``clear()`` method.


Version 4.5.0
-------------

Date: 2016-09-21

- Now only support Django 1.8 and above. Support for older versions has been dropped.
- Remove undocumented and deprecated support for old connection string format.
- Add support for ``PASSWORD`` option (useful when the password contains url unsafe
  characters).
- Make the package compatible with fake redis.
- Fix compatibility issues with latest django version (1.10).


Version 4.4.4
-------------

Date: 2016-07-25

- Fix possible race condition on incr implementation using
  lua script (thanks to @prokaktus).


Version 4.4.3
-------------

Date: 2016-05-17

- Fix minor ttl inconsistencies.


Version 4.4.2
-------------

Date: 2016-04-21

- Fix timeout bug (thanks to @skorokithakis)


Version 4.4.1
-------------

Date: 2016-04-13

- Add additional check for avoid wrong exception on ``get_redis_connection``.


Version 4.4.0
-------------

Date: 2016-04-12

- Make redis client pluggable (thanks to @arnuschky)
- Add version number inside python module (thanks to @BertrandBordage)
- Fix clear method (thanks to @ostcar)
- Add the ability to specify key prefix on delete and delete_pattern.
- BREAKING CHANGE: improved compression support (make it more plugable).


Version 4.3.0
-------------

Date: 2015-10-31

- Improved exception handling in herd client (thanks to @brandoshmando)
- Fix bug that not allows use generators on delete_many (thanks to @ostcar).
- Remove obsolete code that makes hard dependency to mspack.


Version 4.2.0
-------------

Date: 2015-07-03

- Add ``persist`` and ``expire`` methods.
- Remove old and broken dummy client.
- Expose a redis lock method.


Version 4.1.0
-------------

Date: 2015-06-15

- Add plugable serializers architecture (thanks to @jdufresne)
- Add json serializer (thanks to @jdufresne)
- Add msgpack serializer (thanks to @uditagarwal)
- Implement delete_pattern using iter_scan for better performance (thanks to @lenzenmi)


Version 4.0.0
-------------

- Remove usage of deprecated ``get_cache`` method.
- Added connection option SOCKET_CONNECT_TIMEOUT. [Jorge C. Leitão].
- Replace setex and friends with set, because it now supports all need for atomic.
  updates (thanks to @23doors) (re revert changes from 3.8.x branch).
- Fix django 1.8 compatibilities.
- Fix django 1.9 compatibilities.
- BREAKING CHANGE: Now timeout=0 works as django specified (expires immediately)
- Now requires redis server >= 2.8
- BREAKING CHANGE: ``redis_cache`` is no longer a valid package name


Version 3.8.4
-------------

- Backport django 1.8 fixes from master.


Version 3.8.3
-------------

- Minor fix on regular expression for old url notation.


Version 3.8.2
-------------

- Revert some changes from 3.8.1 that are incompatible with redis server < 2.6.12


Version 3.8.1
-------------

- Fix documentation related to new url format.
- Fix documentation parts that uses now removed functions.
- Fix invalid url transformation from old format (password was not set properly)
- Replace setex and friends with set, because it now supports all need for atomic
  updates (thanks to @23doors).


Version 3.8.0
-------------

- Add compression support. (Thanks to @alanjds)
- Change package name from redis_cache to django_redis.
- Add backward compatibility layer for redis_cache package name.
- BACKWARD INCOMPATIBLE CHANGE: use StrictRedis instead of Redis class of redis-py
- Add redis dummy backend for development purposes. (Thanks to @papaloizouc)
- Now use redis native url notation for connection string (the own connection string
  notation is also supported but is marked as deprecated).
- Now requires redis-py >= 2.10.0
- Remove deprecated ``raw_cache`` property from backend.


Version 3.7.2
-------------

- Add missing forward of version parameter from ``add()`` to ``set()`` function. (by @fellowshipofone)

Version 3.7.1
-------------

- Improve docs (by @dkingman).
- Fix missing imports on sentinel client (by @opapy).
- Connection closing improvements on sentinel client (by @opapy).

Version 3.7.0
-------------

- Add support for django's ``KEY_FUNCTION`` and ``REVERSE_KEY_FUNCTION`` (by @teferi)
- Accept float value for socket timeout.
- Fix wrong behavior of ``DJANGO_REDIS_IGNORE_EXCEPTIONS`` with socket timeouts.
- Backward incompatible change: now raises original exceptions instead of self defined.

Version 3.6.2
-------------

- Add ttl method purposed to be included in django core.
- Add iter_keys method that uses redis scan methods for memory efficient keys retrieval.
- Add version keyword parameter to keys.
- Deprecate django 1.3.x support.

Version 3.6.1
-------------

- Fix wrong import on sentinel client.


Version 3.6.0
-------------

- Add pluggable connection factory.
- Negative timeouts now works as expected.
- Delete operation now returns a number of deleted items instead of None.


Version 3.5.1
-------------

- Fixed redis-py < 2.9.0 incompatibilities
- Fixed runtests error with django 1.7


Version 3.5.0
-------------

- Removed: stats module (should be replaced with an other in future)
- New: experimental client for add support to redis-sentinel.
- Now uses a django ``DEFAULT_TIMEOUT`` constant instead of ``True``.
  Deprecation warning added for code that now uses ``True`` (unlikely).
- Fix wrong forward of timeout on shard client.
- Fix incr_version wrong behavior when using shard client (wrong client used for set new key).


Version 3.4.0
-------------

- Fix exception name from ConnectionInterrumped to
  ConnectionInterrupted maintaining an old exception class
  for backward compatibility (thanks Łukasz Langa (@ambv))

- Fix wrong behavior for "default" parameter on get method
  when DJANGO_REDIS_IGNORE_EXCEPTIONS is True
  (also thanks to Łukasz Langa (@ambv)).

- Now added support for master-slave connection to default
  client (it still experimental because is not tested in
  production environments).

- Merged SimpleFailoverClient experimental client (only for
  experiment with it, not ready for use in production)

- Django 1.6 cache changes compatibility. Explicitly passing in
  timeout=None no longer results in using the default timeout.

- Major code cleaning. (Thanks to Bertrand Bordage @BertrandBordage)

- Bugfixes related to some index error on hashring module.


Version 3.3.0
-------------

- Add SOCKET_TIMEOUT attribute to OPTIONS (thanks to @eclipticplane)

Version 3.2.0
-------------

- Changed default behavior of connection error exceptions: now by default
    raises exception on connection error is occurred.

Thanks to Mümin Öztürk:

- cache.add now uses setnx redis command (atomic operation)
- cache.incr and cache.decr now uses redis incrby command (atomic operation)


Version 3.1.7
-------------

- Fix python3 compatibility on utils module.

Version 3.1.6
-------------

- Add nx argument on set method for both clients (thanks to Kirill Zaitsev)

Version 3.1.5
-------------

- Bug fixes on sharded client.

Version 3.1.4
-------------

- Now reuse connection pool on massive use of ``get_cache`` method.

Version 3.1.3
-------------

- Fixed python 2.6 compatibility.

Version 3.1.2
-------------

- Now on call close() not disconnect all connection pool.

Version 3.1.1
-------------

- Fixed incorrect exception message on LOCATION has wrong format.
    (Thanks to Yoav Weiss)

Version 3.1
-----------

- Helpers for access to raw redis connection.

Version 3.0
-----------

- Python 3.2+ support.
- Code cleaning and refactor.
- Ignore exceptions (same behavior as memcached backend)
- Pluggable clients.
- Unified connection string.


Version 2.2.2
-------------

- Bug fixes on ``keys`` and ``delete_pattern`` methods.


Version 2.2.1
-------------

- Remove duplicate check if key exists on ``incr`` method.
- Fix incorrect behavior of ``delete_pattern`` with sharded client.


Version 2.2
-----------

- New ``delete_pattern`` method. Useful for delete keys using wildcard syntax.


Version 2.1
-----------

- Many bug fixes.
- Client side sharding.
