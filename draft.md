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

The following three examples demonstrate how to call NAG Library for Python routines using kdb+ and PyQ.  These examples were carefully selected, as they will mirror the majority of usage cases a customer will encounter across all 1,700+ routines within the library.  If your usage case falls outside of these three examples, please contact NAG support for assistance.

### 3.1 Example One: BLAS Routine DAXPY

Our first example demonstrates how to perform the linear algebra operation<br>

LATEX: $y:= \alpha x + y.$

Below is the NAG Library for Python signature for this routine.

```
   naginterfaces.library.blas.daxpy(alpha,x,y)
   
   Parameters: alpha: float
               x: float, array-like, shape(n)
               y: float, array-like, shape(n)
               
   Returns:    y: float, ndarray, shape(n)
```

Within our terminal, we begin by starting a PyQ interaction session.

```
$ pyq
```

Next, we import PyQ and the NAG Library for Python

```
>>> from pyq import q
>>> from naginterfaces.library import blas
```

We then enter a q environment and define our parameers as q objects.

```
>>> q()
q) alpha:0.5f
q) x:(2.0, 2.0, 2.0, 2.0f)
q) y:(4.0, 4.0, 4.0, 4.0f)
```

Finally, we exit the q environment and invoke the NAG routine.

```
q) \
>>> z = blas.daxpy(float(q.alpha), q.x, q.y)
>>> z  # display solution: array([4., 4., 4., 4.])
```

### 3.2 Example Two: Nearest Correlation Matrix

Our second example employs a nearest correlation matrix routine which, for a given approximate correlation matrix $G$, computes the nearest correlation matrix $X$ by minimizing the weighted Frobenius norm<br>

LATEX: 

where $W$ is a diagonal matrix of weights.

The NAG Library for Python signature for this routine is below.

```
naginterfaces.library.correg.bounded(g,opt,alpha=None,w=None,errtol=0.0,maxits=0,maxit=200)

Parameters: g: float, array-like, shape(n,n)
            opt:str, length 1
            alpha: None or float, optional
            w: None or float, array-like, shape(n), optional
            errtol: float, optional
            maxits: int, optional
            maxit: int, optional

Returns:    x: float, ndarray, shape(n,n)
            itera: int
            feval: int
            nrmgrd: float
```

### 3.3 Example Three: Numerical Integration

With our final example, we demonstrate how to incorporate a user-defined callback function with a NAG Library for Python routine.  This example approximates the definite integal<br>

LATEX:

The NAG Library for Python signature for this routine is below.

```
naginterfaces.library.quad.dim1_fin_smooth(f,a,b,epsabs,epsrel,data=None)

Parameters: f: callable, result = f(x,data=None)
               Parameters:
                   x: float
                   data: arbitrary, optional, modifiable in place
            a: float
            b: float
            epsabs: float
            epsrel: float
            data: arbitrary, optional

Returns:    result: float
            abserr: float
```

## 4 Links


