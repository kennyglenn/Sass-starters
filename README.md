Sass-starters
=============
A basic set of SCSS globals and a typography file, a starting point. 



Font size
---------
When using this a base font size needs to be set. This is usually done on the html element. [More info](http://css-tricks.com/snippets/css/less-mixin-for-rem-font-sizing/)

	html {
	  font-size: 62.5%;
	}

	@mixin font-size($sizeValue: 1.6, $line: $sizeValue * 1.5) {
	  font-size: ($sizeValue * 1) + px;
	  line-height: ($line * 1) + px;
	  font-size: ($sizeValue / 10) + rem;
	  line-height: ($line / 10) + rem;
	}

#### Usage
	@include font-size(18);
 
 

Mediaqueries
------------
These mediaqueries are written mobile first. If you dont want to do mobile first change the min to max. [More info](https://coderwall.com/p/brz5-g)

	@mixin respond-to($media) {
	  @if $media == x-small {
	    @media only screen and (max-width: 27.5em) { @content; }
	  }
	  @if $media == small {
	    @media only screen and (min-width: 43.75em) { @content; }
	  }
	  @else if $media == medium {
	    @media only screen and (min-width: 53.125em) { @content; }
	  }
	  @else if $media == large {
	    @media only screen and (min-width: 64.375em) { @content; }
	  }
	}
 
#### Usage 
	section {
	  width: 100%;
	  @include repond-to(small){ 
	    width: 75%;
	  } 
	}
 
 

Retina/high pixel ratio images
------------------------------
Mediaqueries for high pixel ratios. Create a double resolution background image, scale with background size. [More info](http://37signals.com/svn/posts/3271-easy-retina-ready-images-using-scss)

	@mixin image-2x($image, $width, $height) {
	  @media (min--moz-device-pixel-ratio: 1.3),
	         (-o-min-device-pixel-ratio: 2.6/2),
	         (-webkit-min-device-pixel-ratio: 1.3),
	         (min-device-pixel-ratio: 1.3),
	         (min-resolution: 1.3dppx) {
	 
	    background-image: url($image);
	    background-size: $width $height;
	  }
	}

#### Usage
	@include image-2x('image@2x.png', 25px, 25px);
 


Clear floats
------------
Adds psudeo elements around the element to clear the float. [More info](http://blog.teamtreehouse.com/a-better-clearfix-with-sass)

	@mixin clearfloat {
	    &:before, &:after {
          content: "\0020";
          display: block;
          height: 0;
          overflow: hidden;
	    }
	    &:after {
          clear: both;
	    }
	}
 
#### Usage
	@include clearfloat;
 
 

Image replacement
-----------------
There are many ways to do image replacement, this works for me. This can be used as an placeholder since it is static. [More info](http://nicolasgallagher.com/another-css-image-replacement-technique/)

	%hide-text {
	  color: transparent;
	  font: 0/0 a; 
	  text-shadow: none;
	}
 
 #### Usage

	@extend %hide-text;




