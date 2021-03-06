#############
Using Astropy
#############

.. _cpp_using_astropy:

Integration of Astropy core into the LSST software stack is an ongoing process that will evolve over time as we work on enhancing interoperability of the current codebase with Astropy.
This document is not discussing Astropy affiliated packages, use of which must go through the standard :ref:`RFC <decision-making-rfc>` process.
Not all Astropy core packages can be used by default.

The following packages should be used from Astropy in preference to other Python packages:

* :mod:`astropy.io.fits` instead of ``pyfits`` (use of ``pyfits`` is now deprecated).

The following packages can be used internally in packages if they do not leak into public APIs:

* :mod:`astropy.coordinates`
* :mod:`astropy.time`
* :mod:`astropy.table`
* :mod:`astropy.units`
* :mod:`astropy.units.quantity`
* :mod:`astropy.constants`
* :mod:`astropy.cosmology`
* :mod:`astropy.visualization`
* :mod:`astropy.vo`

The interaction of Astropy with LSST C++ classes providing related functionality should be carefully monitored.
If the code is already using ``afw`` it is strongly preferred that ``afw`` equivalents be used until such time as specific ``afw`` interfaces are deprecated.
:mod:`astropy.table` views into ``afw.table`` tables can be used if required.

Changing public APIs to use the above Astropy packages requires prior permission and possibly an :ref:`RFC <decision-making-rfc>`.

These items have functionality that is similar to that provided in LSST packages:

* :mod:`astropy.modeling`
* :mod:`astropy.convolution`
* :mod:`astropy.wcs`
* :mod:`astropy.stats`
* :mod:`astropy.nddata`

They are not allowed to be used in LSST code without special permission, such as submitting an :ref:`RFC <decision-making-rfc>`.

This advice will evolve as interoperability with Astropy develops.
