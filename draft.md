# Using the NAG Library for Python witk Kdb+ and PyQ

<p align="center">
  Christopher Brandt<br>
  Numerical Algorithms Group (NAG) Inc.<br>
  Lisle, IL, USA<br>
  christopher.brandt@nag.com<br>
  April 3, 2019
</p>

## 1 Background

This paper provides detailed instructions on how to use the NAG Library for Python with kdb+ and PyQ.  The NAG Library contains more than 1,700 mathematical and statistical routines,  and is accessible by numerous programming languages (including Python, C++, Java, Fortran, etc.).  PyQ is an extension to kdb+ featuring zero-copy sharing of data between Python and the q programming language.  The enclosed examples will illustrate how to access routines within the NAG Library for Python using data stored in kdb+.

## 2 Setting Up the Workspace

Installation for both the NAG Library for Python and the PyQ extension to kdb+ may be performed using pip.<br>

To install the NAG Library for Python:

    $ python -m pip install --extra-index-url https:nag/com/downloads/py/naginterfaces_nag naginterfaces

To install PyQ from Kx:

    $ python -m pip install pyq

Both the NAG Library for Python and kdb+ are commercial software packages that require active licenses for their respective usage.  To obtain a temporary license for the NAG Library for Python, please contact NAG support at support@nag.com.

## 3 Examples


### 3.1 Example 1: BLAS Routine DAXPY

### 3.2 Example Two: Nearest Correlation Matrix

### 3.1 Example Three: Numerical Integration


## 4 Links


