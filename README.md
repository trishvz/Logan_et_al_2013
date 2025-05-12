# Logan_et_al_2013
R code and data published in Logan et al. 2013

LICENSING INFORMATION

R Code to fit the models reported in Logan, Van Zandt, Verbruggen, and
Wagenmakers (in press).  On the ability to inhibit thought and action:
General and special theories of an act of control.  Psychological Review.

Copyright (C) 2013  Trisha Van Zandt

This program is free software: you can redistribute it and/or modify it
under the terms of the GNU General Public License as published by the Free
Software Foundation, either version 3 of the License, or (at your option)
any later version.

This program is distributed in the hope that it will be useful, but WITHOUT
ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for
more details.

To read the GNU General Public License,
see <http://www.gnu.org/licenses/>.

ARE YOU USING THIS CODE?

If you use or modify this code for your own purposes, please cite our paper.


SUMMARY

In this directory tree you will find the data for three experiments:
Verbruggen and Logan (2009; in VerLog09), Bisset and Logan (2011; in
BisLog11), and Logan et al. (in press; in Loganetal13).  The data files are
named all.dat, and are found in the top of the directory for each
experiment.

The directory structure is such that the files generating and describing
the fits to individual subjects are located at the lowest level of the
tree, in a directory called "Subject."  Within this Subject directory are
two files, fit.r and fit_loop.r.  The file fit.r contains the code to
generate a good set of starting values for the minimization.  The file
fit_loop.r takes the resulting starting values and performs the
minimization 25 times.  

HOW TO USE THIS DIRECTORY

To fit a particular model to a particular subject's data, descend the
relevant directory tree until you reach the Subject directory.  Note
carefully: Subject must be the working directory.  Open fit.r and specify
the subject of interest by setting the value of the subject variable.  Then
execute the file fit.r (as a batch job in R or execute the entire buffer
within R).  The result should be a file titled subj.Rdata.  Then execute the
file fit_loop.r, which will load "subj.Rdata.".  The best-fitting parameters
and the details of the minimization will be stored in the file subj.Rdata,
overwriting the preliminary fits computed by fit.r.  If you want to save
the preliminary fits, rename the file saved in fit_loop.r something else.

DETAILS

The different models are defined by the parameters that were held constant
and permitted to vary in the fits, and these constraints are given in the
file constraint.r, which is located in the same directory that contains
Subject.

The different models are roughly clustered in groups (e.g., One, Two, Three
for Logan et al.) within which restricted sets of parameters (e.g., the go
process parameters) are constrained.  The likelihood.r files within each
group directory differ only in terms of how the parameters are transformed.
All parameter searches took place over the entire real line, from -Inf to
Inf, and these parameters were then transformed appropriately (e.g., to the
range 0 to minimum.RT for the nondecision times) within the routines that
compute the likelihood.  Most of the likelihood.r files are identical,
except for the models in which accumulation rates were constrained to sum
to a constant.

All routines that do not depend on the particular model being fit are found
in the main Diffusion Race Model directory in the file functions.r.

THE IMPORTANCE OF STARTING VALUES

A suggested set of starting values are given in fit.r.  The user must be
aware that the process by which these starting values were selected
depended in large part on a complex process of guessing, fitting of
preliminary, restricted models, and luck.  The fits that will result on
other computers with other processors, random number generators, versions
of R and so forth will differ somewhat from the fits we obtained and
reported in Logan et al. (in press).  

Note also that some tweaking of these starting values may be required for
individual subjects.

FIND A MISTAKE? CAN'T GET IT TO WORK?

Please contact Trisha Van Zandt at van-zandt.2@osu.edu.
