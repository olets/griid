# A transformation example: A progressively resposive grid

Here's a simple example of how you might use [griid's `resize` function](https://github.com/olets/griid#3-adjusting-griid-x-cell-grids) to build a progressively responsive grid, targeting just a particular grid. (Note that the calculations aren't *perfect* if @griid--gutter is non-zero, but who's looking that closely?)

	.progressive-grid() {
	    @grid-items--max-width: [your site width];
	    
	    @max5: 5 * @griid--max-width / 6;
	    @max4: 2 * @griid--max-width / 3;
	    @max3: @griid--max-width / 2;
	    @max2: @griid--max-width / 3;
	    @max1: @griid--max-width / 6;
	    
	    @media(max-width: @max5) {
	        .griid--resize(5,5)
	    }
	    @media(max-width: @max4) {
	        .griid--resize(4,4)
	    }
	    @media(max-width: @max3) {
	        .griid--resize(3,3)
	    }
	    @media(max-width: @max2) {
	        .griid--resize(2)
	    }
	    @media(max-width: @max1) {
	        .griid--resize
	    }
	}
	#footer-grid {
		.progressive-grid
	}

