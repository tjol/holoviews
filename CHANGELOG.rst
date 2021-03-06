Version 1.4.3
-------------

A minor bugfix release to patch a number of small but important issues.

Fixes and improvements:


* Added a `DynamicMap Tutorial
  <http://holoviews.org/Tutorials/Dynamic_Map.html>`_ to explain how to
  explore very large or continuous parameter spaces in HoloViews (`PR
  #470 <https://github.com/ioam/holoviews/issues/470>`_).
* Various fixes and improvements for DynamicMaps including slicing (`PR
  #488 <https://github.com/ioam/holoviews/issues/488>`_) and validation
  (`PR #483 <https://github.com/ioam/holoviews/issues/478>`_) and
  serialization (`PR #483
  <https://github.com/ioam/holoviews/issues/478>`_)
* Widgets containing matplotlib plots now display the first frame from
  cache providing at least the initial frame when exporting DynamicMaps
  (`PR #486 <https://github.com/ioam/holoviews/issues/483>`_)
* Fixed plotting bokeh plots using widgets in live mode, after changes
  introduced in latest bokeh version (commit `1b87c91e9
  <https://github.com/ioam/holoviews/commit/1b87c91e9e7cf35b267344ccd4a2fa91dd052890>`_).
* Fixed issue in coloring Point/Scatter objects by values (`Issue #467
  <https://github.com/ioam/holoviews/issues/467>`_).


Backwards compatibility:

* The behavior of the ``scaling_factor`` on Point and Scatter plots has
  changed now simply multiplying ``area`` or ``width`` (as defined by
  the ``scaling_method``). To disable scaling points by a dimension
  set ``size_index=None``.
* Removed hooks to display 3D Elements using the ``BokehMPLRawWrapper``
  in bokeh (`PR #477 <https://github.com/ioam/holoviews/pull/477>`_)
* Renamed the DynamicMap mode ``closed`` to ``bounded`` (`PR #477 <https://github.com/ioam/holoviews/pull/485>`_)


Version 1.4.2
-------------

Over the past month since the 1.4.1 release, we have improved our
infrastructure for building documentation, updated the main website and
made several additional usability improvements.

Documentation changes:

* Major overhaul of website and notebook building making it much easier
  to test user contributions (`Issue #180
  <https://github.com/ioam/holoviews/issues/180>`_, `PR #429
  <https://github.com/ioam/holoviews/pull/429>`_)

* Major rewrite of the documentation (`PR #401
  <https://github.com/ioam/holoviews/pull/401>`_, `PR #411
  <https://github.com/ioam/holoviews/pull/411>`_)

* Added Columnar Data Tutorial and removed most of Pandas
  Conversions as it is now supported by the core.

Fixes and improvements:

* Major improvement for grid based layouts with varying aspects (`PR
  #457 <https://github.com/ioam/holoviews/pull/457>`_)

* Fix for interleaving %matplotline inline and holoviews
  plots (`Issue #179 <https://github.com/ioam/holoviews/issues/179>`_)

* Matplotlib legend z-orders and updating fixed (`Issue #304
  <https://github.com/ioam/holoviews/issues/304>`_, `Issue #305
  <https://github.com/ioam/holoviews/issues/305>`_)

* ``color_index`` and ``size_index`` plot options support specifying
  dimension by name (`Issue #391
  <https://github.com/ioam/holoviews/issues/391>`_)

* Added ``Area`` Element type for drawing area under or between
  Curves. (`PR #427 <https://github.com/ioam/holoviews/pull/427>`_)

* Fixed issues where slicing would remove styles applied to an
  Element. (`Issue #423
  <https://github.com/ioam/holoviews/issues/423>`_, `PR #439
  <https://github.com/ioam/holoviews/pull/439>`_)

* Updated the ``title_format`` plot option to support a ``{dimensions}``
  formatter (`PR #436 <https://github.com/ioam/holoviews/pull/436>`_)

* Improvements to Renderer API to allow JS and CSS requirements for
  exporting standalone widgets (`PR #426
  <https://github.com/ioam/holoviews/pull/426>`_)

* Compatibility with the latest Bokeh 0.11 release (`PR #393
  <https://github.com/ioam/holoviews/pull/393>`_)


Version 1.4.1
-------------

Over the past two weeks since the 1.4 release, we have implemented
several important bug fixes and have made several usability
improvements.

New features:

* Improved help system. It is now possible to recursively list all the
  applicable documentation for a composite object. In addition, the
  documentation may now be filtered using a regular expression pattern.
  (`PR #370 <https://github.com/ioam/holoviews/pull/370>`_)

* HoloViews now supports multiple active display hooks making it easier
  to use nbconvert. For instance, PNG data will be embedded in the
  notebook if the argument display_formats=['html','png'] is supplied to
  the notebook_extension. (`PR #355 <https://github.com/ioam/holoviews/pull/355>`_)

* Improvements to the display of DynamicMaps as well as many new
  improvements to the Bokeh backend including better VLines/HLines and
  support for the Bars element.
  (`PR #367 <https://github.com/ioam/holoviews/pull/367>`_ ,
  `PR #362 <https://github.com/ioam/holoviews/pull/362>`_,
  `PR #339 <https://github.com/ioam/holoviews/pull/339>`_).

* New Spikes and BoxWhisker elements suitable for representing
  distributions as a sequence of lines or as a box-and-whisker plot.
  (`PR #346 <https://github.com/ioam/holoviews/pull/346>`_,
  `PR #339 <https://github.com/ioam/holoviews/pull/339>`_) 

* Improvements to the notebook_extension. For instance, executing
  hv.notebook_extension('bokeh') will now load BokehJS and automatically
  activate the Bokeh backend (if available).

* Significant performance improvements when using the groupby operation
  on HoloMaps and when working with highly nested datastructures.
  (`PR #349 <https://github.com/ioam/holoviews/pull/349>`_,
  `PR #359 <https://github.com/ioam/holoviews/pull/359>`_)

Notable bug fixes:

* DynamicMaps are now properly integrated into the style system and can
  be customized in the same way as HoloMaps.
  (`PR #368 <https://github.com/ioam/holoviews/pull/368>`_)

* Widgets now work correctly when unicode is used in the dimension
  labels and values (`PR #376 <https://github.com/ioam/holoviews/pull/376>`_).
  
  
Version 1.4.0
-------------

Over the past few months we have added several major new features and
with the help of our users have been able to address a number of bugs
and inconsistencies. We have closed 57 issues and added over 1100 new
commits.

Major new features:

* Data API: The new data API brings an extensible system of to add new
  data interfaces to column based Element types. These interfaces
  allow applying powerful operations on the data independently of the
  data format. The currently supported datatypes include NumPy, pandas
  dataframes and a simple dictionary format. (`PR #284 <https://github.com/ioam/holoviews/pull/284>`_)

* Backend API: In this release we completely refactored the rendering,
  plotting and IPython display system to make it easy to add new plotting
  backends. Data may be styled and pickled for each backend independently and
  renderers now support exporting all plotting data including widgets
  as standalone HTML files or with separate JSON data. 

* Bokeh backend: The first new plotting backend added via the new backend
  API. Bokeh plots allow for much faster plotting and greater interactivity.
  Supports most Element types and layouts and provides facilities for sharing
  axes across plots and linked brushing across plots. (`PR #250 <https://github.com/ioam/holoviews/pull/250>`_)

* DynamicMap: The new DynamicMap class allows HoloMap data to be generated
  on-the-fly while running a Jupyter IPython notebook kernel. Allows
  visualization of unbounded data streams and smooth exploration of large
  continuous parameter spaces. (`PR #278 <https://github.com/ioam/holoviews/pull/278>`_)

Other features:

* Easy definition of custom aliases for group, label and Dimension
  names, allowing easier use of LaTeX.
* New Trisurface and QuadMesh elements.
* Widgets now allow expressing hierarchical relationships between
  dimensions.
* Added GridMatrix container for heterogeneous Elements and gridmatrix
  operation to generate scatter matrix showing relationship between
  dimensions.
* Filled contour regions can now be generated using the contours operation.
* Consistent indexing semantics for all Elements and support for
  boolean indexing for Columns and NdMapping types.
* New hv.notebook_extension function offers a more flexible alternative
  to %load_ext, e.g. for loading other extensions
  hv.notebook_extension(bokeh=True).

Experimental features:

* Bokeh callbacks allow adding interactivity by communicating between
  bokehJS tools and the IPython kernel, e.g. allowing downsampling
  based on the zoom level.

Notable bug fixes:

* Major speedup rendering large HoloMaps (~ 2-3 times faster).
* Colorbars now consistent for all plot configurations.
* Style pickling now works correctly.

API Changes:

* Dimension formatter parameter now deprecated in favor of value_format.
* Types of Chart and Table Element data now dependent on selected interface.
* DFrame conversion interface deprecated in favor of Columns pandas interface.


Version 1.3.2
-------------

Minor bugfix release to address a small number of issues:

Features:

* Added support for colorbars on Surface Element (1cd5281).
* Added linewidth style option to SurfacePlot (9b6ccc5).

Bug fixes:

* Fixed inversion inversion of y-range during sampling (6ff81bb).
* Fixed overlaying of 3D elements (787d511).
* Ensuring that underscore.js is loaded in widgets (f2f6378).
* Fixed Python3 issue in Overlay.get (8ceabe3).


Version 1.3.1
-------------

Minor bugfix release to address a number of issues that weren't caught
in time for the 1.3.0 release with the addition of a small number of
features:

Features:

* Introduced new ``Spread`` element to plot errors and confidence
  intervals (30d3184).
* ``ErrorBars`` and ``Spread`` elements now allow most Chart
  constructor types (f013deb).

Bug fixes:

* Fixed unicode handling for dimension labels (061e9af).
* Handling of invalid dimension label characters in widgets (a101b9e).
* Fixed setting of fps option for MPLRenderer video output (c61b9df).
* Fix for multiple and animated colorbars (5e1e4b5).
* Fix to Chart slices starting or ending at zero (edd0039).


Version 1.3.0
-------------

Since the last release we closed over 34 issues and have made 380
commits mostly focused on fixing bugs, cleaning up the API and
working extensively on the plotting and rendering system to
ensure HoloViews is fully backend independent.

We'd again like to thank our growing user base for all their input,
which has helped us in making the API more understandable and
fixing a number of important bugs.

Highlights/Features:

* Allowed display of data structures which do not match the
  recommended nesting hierarchy (67b28f3, fbd89c3).
* Dimensions now sanitized for ``.select``, ``.sample`` and
  ``.reduce`` calls (6685633, 00b5a66).
* Added ``holoviews.ipython.display`` function to render (and display)
  any HoloViews object, useful for IPython interact widgets (0fa49cd).
* Table column widths now adapt to cell contents (be90a54).
* Defaulting to matplotlib ticking behavior (62e1e58).
* Allowed specifying fixed figure sizes to matplotlib via
  ``fig_inches`` tuples using (width, None) and (None, height) formats
  (632facd).
* Constructors of ``Chart``, ``Path`` and ``Histogram`` classes now support
  additional data formats (2297375).
* ``ScrubberWidget`` now supports all figure formats (c317db4).
* Allowed customizing legend positions on ``Bars`` Elements (5a12882).
* Support for multiple colorbars on one axis (aac7b92).
* ``.reindex`` on ``NdElement`` types now support converting between
  key and value dimensions allowing more powerful conversions. (03ac3ce)
* Improved support for casting between ``Element`` types (cdaab4e, b2ad91b,
  ce7fe2d, 865b4d5).
* The ``%%opts`` cell magic may now be used multiple times in the same
  cell (2a77fd0)
* Matplotlib rcParams can now be set correctly per figure (751210f).
* Improved ``OptionTree`` repr which now works with eval (2f824c1).
* Refactor of rendering system and IPython extension to allow easy
  swapping of plotting backend (#141)
* Large plotting optimization by computing tight ``bbox_inches`` once
  (e34e339).
* Widgets now cache frames in the DOM, avoiding flickering in some
  browsers and make use of jinja2 template inheritance. (fc7dd2b)
* Calling a HoloViews object without arguments now clears any
  associated custom styles. (9e8c343)
  

API Changes

* Renamed key_dimensions and value_dimensions to kdims and vdims
  respectively, while providing backward compatibility for passing
  and accessing the long names (8feb7d2).
* Combined x/y/zticker plot options into x/y/zticks parameters which
  now accept an explicit number of ticks, an explicit list of tick
  positions (and labels), and a matplotlib tick locator.
* Changed backend options in %output magic, ``nbagg`` and ``d3`` are
  now modes of the matplotlib backend and can be selected with
  ``backend='matplotlib:nbagg'`` and ``backend='matplotlib:mpld3'``
  respectively. The 'd3' and 'nbagg' options remain supported but will
  be deprecated in future.
* Customizations should no longer be applied directly to ``Store.options``;  
  the ``Store.options(backend='matplotlib')`` object should be
  customized instead.  There is no longer a need to call the
  deprecated ``Store.register_plots`` method.
  
  
Version 1.2.0
-------------

Since the last release we closed over 20 issues and have made 334
commits, adding a ton of functionality and fixing a large range of
bugs in the process.

In this release we received some excellent feedback from our users,
which has been greatly appreciated and has helped us address a wide
range of problems.

Highlights/Features:

* Added new ``ErrorBars`` Element (f2b276b)
* Added ``Empty`` pseudo-Element to define empty placeholders in
  Layouts (35bac9f1d)
* Added support for changing font sizes easily (0f54bea)
* Support for holoviews.rc file (79076c8)
* Many major speed optimizations for working with and plotting
  HoloViews data structures (fe87b4c, 7578c51, 5876fe6, 8863333)
* Support for ``GridSpace`` with inner axes (93295c8)
* New ``aspect_weight`` and ``tight`` Layout plot options for more
  customizability of Layout arrangements (4b1f03d, e6a76b7)
* Added ``bgcolor`` plot option to easily set axis background color
  (92eb95c)
* Improved widget layout (f51af02)
* New ``OutputMagic`` css option to style html output (9d42dc2)
* Experimental support for PDF output (1e8a59b)
* Added support for 3D interactivity with nbagg (781bc25)
* Added ability to support deprecated plot options in %%opts magic.
* Added ``DrawPlot`` simplifying the implementation of custom plots
  (38e9d44)

API changes:

* ``Path`` and ``Histogram`` support new constructors (7138ef4, 03b5d38)
* New depth argument on the relabel method (f89b89f)
* Interface to Pandas improved (1a7cd3d)
* Removed ``xlim``, ``ylim`` and ``zlim`` to eliminate redundancy.
* Renaming of various plot and style options including:

  * ``figure_*`` to ``fig_*``
  * ``vertical_spacing`` and ``horizontal_spacing`` to ``vspace`` and ``hspace`` respectively
  * Deprecation of confusing ``origin`` style option on RasterPlot
* ``Overlay.__getitem__`` no longer supports integer indexing (use ``get`` method instead)

Important bug fixes:

* Important fixes to inheritance in the options system (d34a931, 71c1f3a7)
* Fixes to the select method (df839bea5)
* Fixes to normalization system (c3ef40b)
* Fixes to ``Raster`` and ``Image`` extents, ``__getitem__`` and sampling.
* Fixed bug with disappearing adjoined plots (2360972)
* Fixed plot ordering of overlaid elements across a ``HoloMap`` (c4f1685)


Version 1.1.0
-------------

Highlights:

* Support for nbagg as a backend (09eab4f1)
* New .hvz file format for saving HoloViews objects (bfd5f7af)
* New ``Polygon`` element type (d1ec8ec8)
* Greatly improved Unicode support throughout, including support for
  unicode characters in Python 3 attribute names (609a8454)
* Regular SelectionWidget now supports live rendering (eb5bf8b6)
* Supports a list of objects in Layout and Overlay constructors (5ba1866e)
* Polar projections now supported (3801b76e)

API changes (not backward compatible):

* ``xlim``, ``ylim``, ``zlim``, ``xlabel``, ``ylabel`` and ``zlabel``
  have been deprecated (081d4123)
* Plotting options ``show_xaxis`` and ``show_yaxis`` renamed to
  ``xaxis`` and ``yaxis``, respectively (13393f2a).
* Deprecated IPySelectionWidget (f59c34c0)

In addition to the above improvements, many miscellaneous bug fixes
were made.


Version 1.0.1
-------------

Minor release addressing bugs and issues with 1.0.0.

Highlights:

* New separate Pandas Tutorial (8455abc3)
* Silenced warnings when loading the IPython extension in IPython 3 (aaa6861b)
* Added more useful installation options via ``setup.py`` (72ece4db)
* Improvements and bug-fixes for the ``%%opts`` magic tab-completion (e0ad7108)
* ``DFrame`` now supports standard constructor for pandas dataframes (983825c5)
* ``Tables`` are now correctly formatted using the appropriate ``Dimension`` formatter (588bc2a3)
* Support for unlimited alphabetical subfigure labelling (e039d00b)
* Miscellaneous bug fixes, including Python 3 compatibility improvements.


Version 1.0.0
-------------

First public release available on GitHub and PyPI.
