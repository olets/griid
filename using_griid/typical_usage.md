# Typical usage

-    1. Likely: run adjustment functions in media queries to treat one grid as another in certain contexts ([see below](https://github.com/olets/griid#b-grid-transformations))
-    2. Possibly:
	- run `.griid--initialize` to revert any changes made by adjustment functions,
	- or if you only need to reset a particular type of grid, you can save a little weight by running `.griid--initialize-equal-cells`, `.griid--initialize-unequal-cells`, or `.griid--initialize-row`
	- to have specific grids use a different baseline font size, you don't need to do a full new initialization. Just run `.griid--fz(@fontSize)`##griid LESS functions and mixins

griid has support for all sorts of adjustments. These are especially useful for media queries - turn your 1/3 - 2/3 layout into 1/2 - 1/2 [quickly and cleanly](https://github.com/olets/griid#2-adjusting-griid-cell-n-d-grids). [Progressively resize a grid](https://github.com/olets/griid#a-transformation-example-a-progressively-resposive-grid) first from 6 columns (the factory default max columns for griid) [to 5](https://github.com/olets/griid#3-adjusting-griid-x-cell-grids), then 4, 3, 2, 1. Turn a [single-row grid into](https://github.com/olets/griid#1-adjusting-griid-cell-grids) a three-column grid. Pretty much anything you could want to do, you can.

&nbsp;

Explanations of all the adjustments are here. You might also **[check out the test suite](https://cdn.rawgit.com/olets/griid/bcb6ef678f7501d5d4304aee04e2493effc8aeca/tests/griid-tests.html) for an example of each available adjustment**.

