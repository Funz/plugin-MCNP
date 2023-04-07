[![.github/workflows/ant.yml](https://github.com/Funz/plugin-MCNP/actions/workflows/ant.yml/badge.svg)](https://github.com/Funz/plugin-MCNP/actions/workflows/ant.yml)

# Funz plugin: MCNP

This plugin is dedicated to launch MCNP calculations from Funz.
It supports the following syntax and features:

  * Input
    * file type supported: any MCNP standard input file
    * parameter syntax: 
      * variable syntax: `%(...)`
      * formula syntax: `@{...}`
      * comment char: `C ` (note that it holds two chars)
    * example input file:
        ```
        Godiva-type critical reactor and kcode example
        c skip 10 and run a total of 110 keff cycles with 1000 neutrons per cycle
         1    1  -18.74  -1  imp:n=1   $ enriched uranium sphere (godiva)
         2    0           1  imp:n=0   $ all space outside the sphere
        
         1    so %(r~8.741)                 $ radius of the godiva sphere
        
         kcode 1000 1.0 10 1010         $ kcode defines a criticality calculation
         ksrc  0 0 0                   $ initial keff spatial dist is point at origin
         m1    92235 -93.71  92238 -5.27  92234 -1.02  $ define u with weight fractions
        ```
      * will identify input:
        * r, expected to be around 8.71

  * Output
    * file type supported: '*o'
    * read criticality values printed
    * example output file:
        ```
        ...
        
         -----------------------------------------------------------------------------------------------------------------------------------
         |                                                                                                                                 |
         | the final estimated combined collision/absorption/track-length keff = 0.99946 with an estimated standard deviation of 0.00063   |
         |                                                                                                                                 |
        ...
        ```
        * will return output:
          * mean_keff=0.99946
          * sigma_keff=0.00063


![Analytics](https://ga-beacon.appspot.com/UA-109580-20/plugin-MCNP)
