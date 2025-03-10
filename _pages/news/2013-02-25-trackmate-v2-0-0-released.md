---
title: 2013-02-25 - TrackMate v2.0.0 released
---

We just released a new major version of [TrackMate\_](/plugins/trackmate), our framework to perform automated and manual tracking of blob-like structures.

Most visible changes involve data export and basic analysis, user interface, performance improvement ... There is no new tracking and detection algorithm in this release. We hope nevertheless that you will enjoy this brand new version.

We would like to thank the users we contacted for the release-candidates testing, and who greatly facilitated this release.

Since June 2012:

### Changelog since v1.2

Most changes in this version are for developers and are not displayed in the text below, which lists only changes visible to users.

#### Highlights

-   TrackMate now uses [ImgLib2](/libs/imglib2) internally, and is therefore ready to be moved to [ImageJ2](/software/imagej2).
-   TrackMate now computes edge features (on top of spot and track features). These features enable the immediate measure of velocity, displacement, etc...
-   Tracks can be colored in the Hyperstack displayer, in the 3D viewer and in TrackScheme using indifferently track or edge features.

{% include img src="/media/news/trackmate-edgecoloring.png" align="center" %}

-   All spot, edge and track features are computed automatically and kept in sync even versus manual modifications.
-   All spot, edge and track features are saved in the XML file.
-   All spot, edge and track features can be exported as ImageJ results tables. Then they can be exported to text files, readable by let's say Excel. (Please note that the authors of the plugin do not deem Excel as a proper solution for scientific analysis and recommend more professional solutions.)

{% include img src="/media/news/trackmate-analysisbutton.png" width="400px" alt="TrackMate Analysis Button" align="center" %}

-   All spot, edge and track features can be plotted as specialized graphs, thanks to a dedicated GUI panel.

{% include img src="/media/news/trackmate-grapherpanel.png" align="center" %}

-   Tracks can be named in TrackScheme. These names are used to sort alphanumerically the tracks as they are laid out. To change the name of a track, just double-click its current name in the TrackScheme view.
-   We use [semantic versioning](http://semver.org/) for release numbers from now on. The rules about backward incompatible changes - described below - required a major version change. However, we reserve the right to make a major number change only when there is backward incompatible changes to the user only. API changes might not trigger a major version change.

#### Backward incompatible changes

Even if the detectors and trackers are still the same that of versions 1.x, there are some incompatible changes that required a major version change.

-   The XML file format changed and is therefore not compatible anymore between major versions. However, XML files generated with the previous version (v1.2) can be imported in v2.0.0. and are converted on the fly.
-   In linear-assignment-problem trackers (LAP tracker and simple LAP tracker), the time interval to bridge gaps is specified in frame interval instead of time interval.
-   In LAP trackers, detection of split and merge events are constrained to two consecutive frames.
-   The spot morphology analyzer is disabled.
-   Removed the spot intensity kurtosis, skewness and variance features.

#### Improvements

-   Much better memory management in LAP tracker: Tracking on large number of spots will consume much less memory if tracks are not branching.
-   Speed up considerably the loading of large xml files.
-   Better GUI refreshing when performing heavy calculations.
-   All major operations are now multi-threaded, notably computing spot, edge and track features.
-   Track layout in TrackScheme is now deterministic: when branching, branches are sorted left to right using the name of the first spot in the branches.
-   Spots added manually are added in TrackScheme live in a dedicated column, to facilitate manual tracking.
-   In TrackScheme, added menu items to select tracks downward or upward in time from current selection.
-   In TrackScheme, the selection table can be exported as an ImageJ results table.
-   Better track layout in TrackScheme for tree-like structures.
-   Improved the performance of several track analyzers.
-   Full keyboard navigation.
-   The filter panels that appear in the GUI can have their threshold entered by keyboard: Set the focus to the histogram panel (press tab until the threshold value is displayed in dark red instead of orange, or click the panel), and type a number - possibly decimal, wait 1 s. You can also use the arrow keys to change it by 10% (left/right) or set it to a max or min value (up/down).

#### Bug fixes

-   Fix a nasty and dangerous bug in LoG detector: We were not converting the filter sigma to pixel coordinates, yielding different filter strengths depending on the spatial calibration entered, even if the user-specified radius was the same. This generated a weirdness in spot coordinates that Alison Twelvetrees noted.
-   Fix the bug that caused the GUI to often hang after the initial filtering step.
-   Fix a bug when rendering tracks in the 3D viewer: the filtered-out tracks were displayed anyway. Noticed by David Mason.
-   Fix a bug causing TrackScheme and XML files to sometimes receive empty tracks.
-   Numerous minor bugfixes.


