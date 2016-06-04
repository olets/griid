# Typical usage

-    1. Likely: run adjustment functions in media queries to treat one grid as another in certain contexts ([see below](https://github.com/olets/griid#b-grid-transformations))
-    2. Possibly:
	- run `.griid--initialize` to revert any changes made by adjustment functions,
	- or if you only need to reset a particular type of grid, you can save a little weight by running `.griid--initialize-equal-cells`, `.griid--initialize-unequal-cells`, or `.griid--initialize-row`
	- to have specific grids use a different baseline font size, you don't need to do a full new initialization. Just run `.griid--fz(@fontSize)`##griid LESS functions and mixins
