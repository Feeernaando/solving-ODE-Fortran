# General info
In this repo you can find 3 programmes that solve ordinary differential equations (O.D.E) using different methods. 

# What each programme solves

## [Title](Solving_Dif_Eq_1.f90)

* Solves a damped harmonic oscillator type equation of the parameters

    X''(t) - (0.05)X'(t) + (0.15)X(t) = 0

    using the Euler method with four different h values (relative to the precision of the method )


# Libraries used
The programme mostly uses built-in FORTRAN 90 functions. 

* IEEE_ARITHMETIC - This library is used in order to detect NaN and Infty values that may cause the programme to crash.

# Setup
To compile and execute the code the compiler gfortran is necessary. 

* In Linux (Ubunut) the code is compiled by typing in terminal

gfortran FastHistograms_6.f90 -o FastHistograms_6

* To execute it type in terminal

./FastHistograms_6

* To use the code create and specific folder. In such folder compile the code and save the files to be used to create the histogram.

# How to use it
In order to use the code the following variables need to be manually set by the user before compiling and executing the programme


!Name of the file with the data that is to be sorted in a histogram.
CHARACTER(LEN=120) :: DATAFILE_OF_INTEREST = 'Ex_Data_2.dat'

!Name of the file where the bins and height are stores, i.e. the histogram
CHARACTER(LEN=120) :: HISTOGRAM_FILE = 'HISTOGRAM_Ex_Data_2.dat'

!Number of datapoints known in the file.
INTEGER(KIND = IDP), PARAMETER :: N = 10000

!Parameters to set the histograms characteristics
 
REAL(KIND = DP), PARAMETER :: BIN_SIZE = 0.5
!With this variable you can set the size of the bins. !To be printed fully is necessary to configure the amount of characters to be printed at lines 113 and 120

REAL(KIND = DP), PARAMETER :: CENTRAL_VALUE = 0.0
!With this variable you set the central value of the histogram, by default it can be left set at 0.0.

REAL(KIND = DP), PARAMETER :: RIGHT_BOUND = 10
!With this variable you set the maximum value of the data to be considered while creating the histogram.

REAL(KIND = DP), PARAMETER :: LEFT_BOUND = -10
!With this variable you set the minimum value of the data to be considered while creating the histogram, if negative the minus has to be included in the stated value.

# Test datafile
In order for the user to give it a try along side this programme you can find two datasets named Ex_Data.dat and Ex_Data_2.dat each of those files contains 10,000 lines each containing a value. You can determine the statistics of such datasets by using the code. 

I also provide a short script for gnuplot in order to visualize the created histogram. The file is plot_histogram.plt

# Usage
I want to retain all the rights for the following code as my intention is for it to be used by anyone who needs a fast and reliable way to create histograms. If you want to contribute in a certain way I am open to discuss the terms of such contribution. Basically I just want this code to always be available to any student in need of creating an histogram
If you need to create histograms in a fast way, go on, this is intended for you ;)

If you have any doubt regarding how to use this code please email me at
fernando.lr@ciencias.unam.mx
fernaaando@proton.me

# About
This piece of code was born during my thesis to obtain my degree as a physicist at the Faculty of Sciences at UNAM (in Mexico City). During my investigation I needed to analyze the statistics of Montecarlo simulations of 10^10 iterations with a resolution of 10 digits after the decimal point. Such conditions generate files of 60plus Gb. That no python library could handle, so… I went back to my computational physics course In which my professor taught us that FORTRAN was the tool when high volumes of data are to be processed in a fast way. In the end FORTRAN was the answer. Indeed all the simulations of my thesis work were performed using FORTRAN and in the end I was able to develop all my investigation using only a pair of personal desktops around my house (Yep, COVID pandemic was in the way when I was developing my thesis)