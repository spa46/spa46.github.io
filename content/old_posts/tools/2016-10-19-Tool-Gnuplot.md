+++
title = "Gnuplot"
date = 2016-10-19
weight = 100
tags = ["gnuplot"]
+++

{% include toc %}

# Introduction

Gnuplot(freeware) is a command-driven, interactive, function, and data plotting program for producing a 2D and 3D graph. Although, This does not have many features compared to commercial plotting software, it isn’t complex to use. Therefore, it is ideal for users for those who do not want to learn tools that are difficult to learn and use.
<br>
<br>
<br>
<br>


# Structure (Abstract)

      __________________________________________________________
      Function            Returns
      -----------      ------------------------------------------
      abs(x)            absolute value of x, |x|
      acos(x)           arc-cosine  of x
      asin(x)           arc-sine    of x  
      atan(x)           arc-tangent of x
      cos(x)            cosine      of x,  x is in radians.
      cosh(x)           hyperbolic cosine of x, x is in radians
      erf(x)            error function of x
      exp(x)            exponential function of x, base e
      inverf(x)         inverse error function of x
      invnorm(x)        inverse normal distribution of x
      log(x)            log of x, base e
      log10(x)          log of x, base 10
      norm(x)           normal Gaussian distribution function
      rand(x)           pseudo-random number generator      
      sgn(x)            1 if x > 0, -1 if x < 0, 0 if x=0
      sin(x)            sine      of x, x is in radians
      sinh(x)           hyperbolic sine of x, x is in radians
      sqrt(x)           the square root of x
      tan(x)            tangent of x, x is in radians
      tanh(x)           hyperbolic tangent of x, x is in radians
      ___________________________________________________________
      Bessel, gamma, ibeta, igamma, and lgamma functions are also
      supported.  Many functions can take complex arguments.
      Binary and unary operators are also supported.  


# Syntax

       plot {[ranges]}
            {[function] | {"[datafile]" {datafile-modifiers}}}
            {axes [axes] } { [title-spec] } {with [style] }
            {, {definitions,} [function] ...}


# Plotting Data

      gnuplot>  plot  "test.dat" using 1:2 title 'Column', \
                      "test.dat" using 1:3 title 'Beam'

*No blank space after the line continuation character, "\" .

### Example of test.dat format

	# X     Y
	1.0   1.2
	2.0   1.8
	3.0   1.6

# command

### set command

      Create a title:                  > set title "TITLE NAME"
      Put a label on the x-axis:       > set xlabel "X-AXIS NAME"
      Put a label on the y-axis:       > set ylabel "Y-AXIS NAME"
      Change the x-axis range:         > set xrange [LOWEST_X:HIGHEST_X]
      Change the y-axis range:         > set yrange [LOWEST_Y:HIGHEST_Y]
      Have Gnuplot determine ranges:   > set autoscale
      Move the key:                    > set key X,Y
      Delete the key:                  > unset key
      Put a label on the plot:         > set label "NAME" at X, Y
      Remove all labels:               > unset label
      Plot using log-axes:             > set logscale
      Plot using log-axes on y-axis:   > unset logscale; set logscale y
      Change the tic-marks:            > set xtics 10
      Return to the default tics:      > unset xtics; set xtics auto

# C++ library

There is a C++ library for easy use: gnuplot-iostream interface. This pushes data arrays and mouse clicks using the iostream pipe to plot the data with extra functions. This low level interface simply use std::vector<std::vector<std::pair<double, double>>> to push data.

### Documentation
For a documentation, click [here](https://github.com/dstahlke/gnuplot-iostream/wiki)

### Download
To Clone the source code from git:

	git clone https://github.com/dstahlke/gnuplot-iostream.git

For a high lavel interface, refer to [gnuplot-cpp library](http://code.google.com/p/gnuplot-cpp)

### Compile

locate "gnuplot-iostream.h" and include the file, and
link *boost_iostreams, boost_system, boost_filesystem* when you compile.

For example,

	 g++ -o test test.cc -lboost_iostreams -lboost_system -lboost_filesystem

<br>

# Samples

![sample1](/images/gnuplot_bg.png)

![sample2](/images/gnuplot_bg1.png)

# References
1. [gnuplot official website](http://gnuplot.sourceforge.net/)
2. [gnuplot manual](http://www.fnal.gov/docs/products/gnuplot/manual/)   
2. T.kawano, (2005). gnuplot tips. [http://lowrank.net/gnuplot/index-e.html](http://lowrank.net/gnuplot/index-e.html)
3. Dan Stahlke. Gnuplot-iostream interface. [http://www.stahlke.org/dan/gnuplot-iostream/](http://www.stahlke.org/dan/gnuplot-iostream/)
