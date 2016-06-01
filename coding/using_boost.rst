###########
Using Boost
###########

.. _cpp_using_boost:

A Boost library shall be used in in preference to any other method of accomplishing the same effect only if:

1. the effect cannot be accomplished with a C++11 standard language feature, and
2. a C++ standard library equivalent is not available, or
3. the C++ standard library equivalent is not usable with our minimum supported compiler version (i.e. ``gcc`` version 4.8).

In particular the following libraries were accepted before we adopted ``gcc`` 4.8 as our minimum compiler version, but have been or are being replaced by ``std::`` equivalents,
and are thus no longer accepted, include:

* ``array``: use ``std::array`` from ``<array>``
* ``bind``: use ``std::bind``
* ``cstdint``: use ``<cstdint>``
* ``filesystem``: use ``<filesystem>``
* ``lambda``: use C++11 lambda functions
* ``lexical_cast``: use ``std::to_string``, ``std::sto``, ``std::stod`` etc.
* ``math``: use ``<cmath>`` wherever possible
* ``noncopyable``: use ``= delete`` on the copy constructor and assignment operator
* ``random``: use ``<random>``
* ``ref``: use ``std::forward`` and universal / forwarding references
* ``smart_ptr``: use ``std::shared_ptr`` and ``std::unique_ptr`` from ``<memory>`` instead of ``boost::shared_ptr`` and ``boost::scoped_ptr``
* ``static_assert``: use C++11 ``static_assert``
* ``tuple``: use ``<tuple>``
* ``type_traits``: use ``<type_traits>``
* ``unordered_map``: use ``<unordered_map>``

Certain Boost libraries are recommended; they should be used whenever applicable in preference to any other method of accomplishing the same effect. In general, any library that is tagged with *"Standard .... {something}"* in the `Boost library listing <http://www.boost.org/doc/libs>`_ falls into this category (unless its use conflicts with the above rules on the availability of standard library / language equivalents).
Among others, this category includes:

* ``current_function``
* ``format``
* ``regex`` (until we adopt ``gcc`` 4.9 as our minimum compiler version, at which point use ``std::regex``)
* ``test``

Additional Boost libraries are considered safe; they may be used freely where applicable.

* ``any``
* ``GIL``
* ``iterator``
* ``MPI``
* ``multi_index``
* ``numeric``
* ``tokenizer``
* ``variant``

Most other Boost libraries may be used after appropriate design review.
Particular caution should be used when the library involves substantial template metaprogramming or requires linking (is not listed on the above page as *"Build & Link .... Header-only"*).
Among others, the following libraries fall into the extra-caution category:

* ``Fusion``
* ``MPL``
* ``serialization``

Certain Boost libraries conflict with LSST-standard ways of doing things, are inappropriate for LSST code, are insufficiently developed or well-maintained, or have been found to be excessively complicated.
These are not allowed without special permission.

* ``config``
* ``preprocessor``
* ``python``
* ``throw_exception``
