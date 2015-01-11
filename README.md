openexr.js
==========

**WIP** - A complete port of OpenEXR 2.2 to Javascript for a new generation of high-dynamic-range browser-based approval workflows.

- [Open an issue](https://github.com/vfx-engineering/openexr.js/issues/new) on GitHub if you have any questions concerning the project.


## Project updates

### 2015/01/11

**I have made fire** - The holidays have been intense. I was able to port OpenEXRs underlying library **ilmbase** almost entirely to Javascript. Go check out the working test files, which are the ported C tests **HalfTest**, **IexTest** and **ImathTest** from ilmbase.
You should see the console outputs, which are similar to the code running natively on your CPU - but this time the tests are running inside the Javascript Engine of your browser.

Before your click on the links keep in mind this is not optimized code. The js files are quite large and the execution could take a few seconds to complete. Please be patient. If your browser should complain that the javascript is taking to long to execute - just click on "Wait" or "Continue execution". This should only happen on **ImathTest** which executes quite a lot of tests.

* [HalfTest](http://vfx.engineering/projects/openexr-js/20150111/halftest/) - Some tests on the Half class, which encapsulates the exr 16-bit floating-point format.

* [IexTest](http://vfx.engineering/projects/openexr-js/20150111/iextest/) - A few tests on the exception-handling library Iex.

* [ImathTest](http://vfx.engineering/projects/openexr-js/20150111/imathtest/) - Many tests on the powerful math library, which implements 2D and 3D vectors, 3x3 and 4x4 matrices, quaternions and other useful 2D and 3D math functions.


**Currently I am working on the port of the IlmThread part of ilmbase. Javascript does not support Multi-threading. Probably the concept of web workers is the only way to do this. We will see ...**

The output of the executed tests in your browser should look something like this:

#### HalfTest

```

------ testing type half------ 

size and alignment
sizeof  (half) = 2
alignof (half) = 2
ok


------ Testing Size done------ 

basic arithmetic operations:
f1 = 1, f2 = 2, h1 = 3, h2 = 4
h1 = f1 + f2: 3
h2 += f1: 5
h2 = h1 + h2: 8
h2 += h1: 11
h1 = h2: 11
h2 = -h1: -11
ok


------ Testing Arithmetic done------ 

float-to-half conversion error for normalized half numbers
max error          = 0.000488101
max expected error = 0.00048828
ok


------ Testing Normalized Conversions done------ 

rounding normalized numbers to 10-bit precision
max error          = 0
max expected error = 0
ok

rounding denormalized numbers to 10-bit precision
max error          = 0
max expected error = 0
ok

rounding normalized numbers to 9-bit precision
max error          = 0.00097561
max expected error = 0.00097656
ok

rounding denormalized numbers to 9-bit precision
max error          = 5.96046e-08
max expected error = 5.96046e-08
ok

rounding normalized numbers to 1-bit precision
max error          = 0.249634
max expected error = 0.249999
ok

rounding denormalized numbers to 1-bit precision
max error          = 1.52588e-05
max expected error = 1.52588e-05
ok

rounding normalized numbers to 0-bit precision
max error          = 0.499756
max expected error = 0.499999
ok

rounding denormalized numbers to 0-bit precision
max error          = 3.05176e-05
max expected error = 3.05176e-05
ok


------ Testing Rounding Errors done!------

specific bit patterns

              1    0 01111111 00000000000000000000000    0 01111 0000000000
              1    0 01111111 00000000000000000000000

      1.0009766    0 01111111 00000000010000000000000    0 01111 0000000001
      1.0009766    0 01111111 00000000010000000000000

      1.0004883    0 01111111 00000000001000000000000    0 01111 0000000000
              1    0 01111111 00000000000000000000000

      1.0004882    0 01111111 00000000000111111111111    0 01111 0000000000
              1    0 01111111 00000000000000000000000

      1.0004884    0 01111111 00000000001000000000001    0 01111 0000000001
      1.0009766    0 01111111 00000000010000000000000

      1.0019531    0 01111111 00000000100000000000000    0 01111 0000000010
      1.0019531    0 01111111 00000000100000000000000

      1.0014648    0 01111111 00000000011000000000000    0 01111 0000000010
      1.0019531    0 01111111 00000000100000000000000

      1.0014647    0 01111111 00000000010111111111111    0 01111 0000000001
      1.0009766    0 01111111 00000000010000000000000

       1.001465    0 01111111 00000000011000000000001    0 01111 0000000010
      1.0019531    0 01111111 00000000100000000000000

     0.99951172    0 01111110 11111111110000000000000    0 01110 1111111111
     0.99951172    0 01111110 11111111110000000000000

     0.99975586    0 01111110 11111111111000000000000    0 01111 0000000000
              1    0 01111111 00000000000000000000000

     0.99975592    0 01111110 11111111111000000000001    0 01111 0000000000
              1    0 01111111 00000000000000000000000

      0.9997558    0 01111110 11111111110111111111111    0 01110 1111111111
     0.99951172    0 01111110 11111111110000000000000

  5.9604645e-08    0 01100111 00000000000000000000000    0 00000 0000000001
  5.9604645e-08    0 01100111 00000000000000000000000

  1.1920929e-07    0 01101000 00000000000000000000000    0 00000 0000000010
  1.1920929e-07    0 01101000 00000000000000000000000

  8.9406967e-08    0 01100111 10000000000000000000000    0 00000 0000000010
  1.1920929e-07    0 01101000 00000000000000000000000

  8.9401006e-08    0 01100111 01111111111110010111001    0 00000 0000000001
  5.9604645e-08    0 01100111 00000000000000000000000

  8.9412929e-08    0 01100111 10000000000001101000111    0 00000 0000000010
  1.1920929e-07    0 01101000 00000000000000000000000

              0    0 00000000 00000000000000000000000    0 00000 0000000000
              0    0 00000000 00000000000000000000000

  2.9802322e-08    0 01100110 00000000000000000000000    0 00000 0000000000
              0    0 00000000 00000000000000000000000

  2.9808284e-08    0 01100110 00000000000011010001110    0 00000 0000000001
  5.9604645e-08    0 01100111 00000000000000000000000

  2.9796361e-08    0 01100101 11111111111001011100100    0 00000 0000000000
              0    0 00000000 00000000000000000000000

  6.1035156e-05    0 01110001 00000000000000000000000    0 00001 0000000000
  6.1035156e-05    0 01110001 00000000000000000000000

  6.1094761e-05    0 01110001 00000000010000000000000    0 00001 0000000001
  6.1094761e-05    0 01110001 00000000010000000000000

  6.1064959e-05    0 01110001 00000000001000000000000    0 00001 0000000000
  6.1035156e-05    0 01110001 00000000000000000000000

  6.1064951e-05    0 01110001 00000000000111111111111    0 00001 0000000000
  6.1035156e-05    0 01110001 00000000000000000000000

  6.1064966e-05    0 01110001 00000000001000000000001    0 00001 0000000001
  6.1094761e-05    0 01110001 00000000010000000000000

  6.0975552e-05    0 01110000 11111111100000000000000    0 00000 1111111111
  6.0975552e-05    0 01110000 11111111100000000000000

  6.1005354e-05    0 01110000 11111111110000000000000    0 00001 0000000000
  6.1035156e-05    0 01110001 00000000000000000000000

  6.1005358e-05    0 01110000 11111111110000000000001    0 00001 0000000000
  6.1035156e-05    0 01110001 00000000000000000000000

   6.100535e-05    0 01110000 11111111101111111111111    0 00000 1111111111
  6.0975552e-05    0 01110000 11111111100000000000000

              2    0 10000000 00000000000000000000000    0 10000 0000000000
              2    0 10000000 00000000000000000000000

              3    0 10000000 10000000000000000000000    0 10000 1000000000
              3    0 10000000 10000000000000000000000

             10    0 10000010 01000000000000000000000    0 10010 0100000000
             10    0 10000010 01000000000000000000000

            0.1    0 01111011 10011001100110011001101    0 01011 1001100110
    0.099975586    0 01111011 10011001100000000000000

            0.2    0 01111100 10011001100110011001101    0 01100 1001100110
     0.19995117    0 01111100 10011001100000000000000

     0.30000001    0 01111101 00110011001100110011010    0 01101 0011001101
     0.30004883    0 01111101 00110011010000000000000

          65504    0 10001110 11111111110000000000000    0 11110 1111111111
          65504    0 10001110 11111111110000000000000

          65536    0 10001111 00000000000000000000000    0 11111 0000000000
            inf    0 11111111 00000000000000000000000

          65520    0 10001110 11111111111000000000000    0 11111 0000000000
            inf    0 11111111 00000000000000000000000

      65519.996    0 10001110 11111111110111111111111    0 11110 1111111111
          65504    0 10001110 11111111110000000000000

      65520.004    0 10001110 11111111111000000000001    0 11111 0000000000
            inf    0 11111111 00000000000000000000000

   4.290774e+09    0 10011110 11111111100000000000100    0 11111 0000000000
            inf    0 11111111 00000000000000000000000

  3.4028235e+38    0 11111110 11111111111111111111111    0 11111 0000000000
            inf    0 11111111 00000000000000000000000

            inf    0 11111111 00000000000000000000000    0 11111 0000000000
            inf    0 11111111 00000000000000000000000

            nan    0 11111111 11111111111111111111111    0 11111 1111111111
            nan    0 11111111 11111111110000000000000

            nan    0 11111111 10101010101010101010101    0 11111 1010101010
            nan    0 11111111 10101010100000000000000

             -1    1 01111111 00000000000000000000000    1 01111 0000000000
             -1    1 01111111 00000000000000000000000

     -1.0009766    1 01111111 00000000010000000000000    1 01111 0000000001
     -1.0009766    1 01111111 00000000010000000000000

     -1.0004883    1 01111111 00000000001000000000000    1 01111 0000000000
             -1    1 01111111 00000000000000000000000

     -1.0004882    1 01111111 00000000000111111111111    1 01111 0000000000
             -1    1 01111111 00000000000000000000000

     -1.0004884    1 01111111 00000000001000000000001    1 01111 0000000001
     -1.0009766    1 01111111 00000000010000000000000

     -1.0019531    1 01111111 00000000100000000000000    1 01111 0000000010
     -1.0019531    1 01111111 00000000100000000000000

     -1.0014648    1 01111111 00000000011000000000000    1 01111 0000000010
     -1.0019531    1 01111111 00000000100000000000000

     -1.0014647    1 01111111 00000000010111111111111    1 01111 0000000001
     -1.0009766    1 01111111 00000000010000000000000

      -1.001465    1 01111111 00000000011000000000001    1 01111 0000000010
     -1.0019531    1 01111111 00000000100000000000000

    -0.99951172    1 01111110 11111111110000000000000    1 01110 1111111111
    -0.99951172    1 01111110 11111111110000000000000

    -0.99975586    1 01111110 11111111111000000000000    1 01111 0000000000
             -1    1 01111111 00000000000000000000000

    -0.99975592    1 01111110 11111111111000000000001    1 01111 0000000000
             -1    1 01111111 00000000000000000000000

     -0.9997558    1 01111110 11111111110111111111111    1 01110 1111111111
    -0.99951172    1 01111110 11111111110000000000000

 -5.9604645e-08    1 01100111 00000000000000000000000    1 00000 0000000001
 -5.9604645e-08    1 01100111 00000000000000000000000

 -1.1920929e-07    1 01101000 00000000000000000000000    1 00000 0000000010
 -1.1920929e-07    1 01101000 00000000000000000000000

 -8.9406967e-08    1 01100111 10000000000000000000000    1 00000 0000000010
 -1.1920929e-07    1 01101000 00000000000000000000000

 -8.9401006e-08    1 01100111 01111111111110010111001    1 00000 0000000001
 -5.9604645e-08    1 01100111 00000000000000000000000

 -8.9412929e-08    1 01100111 10000000000001101000111    1 00000 0000000010
 -1.1920929e-07    1 01101000 00000000000000000000000

             -0    1 00000000 00000000000000000000000    1 00000 0000000000
             -0    1 00000000 00000000000000000000000

 -2.9802322e-08    1 01100110 00000000000000000000000    1 00000 0000000000
             -0    1 00000000 00000000000000000000000

 -2.9808284e-08    1 01100110 00000000000011010001110    1 00000 0000000001
 -5.9604645e-08    1 01100111 00000000000000000000000

 -2.9796361e-08    1 01100101 11111111111001011100100    1 00000 0000000000
             -0    1 00000000 00000000000000000000000

 -6.1035156e-05    1 01110001 00000000000000000000000    1 00001 0000000000
 -6.1035156e-05    1 01110001 00000000000000000000000

 -6.1094761e-05    1 01110001 00000000010000000000000    1 00001 0000000001
 -6.1094761e-05    1 01110001 00000000010000000000000

 -6.1064959e-05    1 01110001 00000000001000000000000    1 00001 0000000000
 -6.1035156e-05    1 01110001 00000000000000000000000

 -6.1064951e-05    1 01110001 00000000000111111111111    1 00001 0000000000
 -6.1035156e-05    1 01110001 00000000000000000000000

 -6.1064966e-05    1 01110001 00000000001000000000001    1 00001 0000000001
 -6.1094761e-05    1 01110001 00000000010000000000000

 -6.0975552e-05    1 01110000 11111111100000000000000    1 00000 1111111111
 -6.0975552e-05    1 01110000 11111111100000000000000

 -6.1005354e-05    1 01110000 11111111110000000000000    1 00001 0000000000
 -6.1035156e-05    1 01110001 00000000000000000000000

 -6.1005358e-05    1 01110000 11111111110000000000001    1 00001 0000000000
 -6.1035156e-05    1 01110001 00000000000000000000000

  -6.100535e-05    1 01110000 11111111101111111111111    1 00000 1111111111
 -6.0975552e-05    1 01110000 11111111100000000000000

             -2    1 10000000 00000000000000000000000    1 10000 0000000000
             -2    1 10000000 00000000000000000000000

             -3    1 10000000 10000000000000000000000    1 10000 1000000000
             -3    1 10000000 10000000000000000000000

            -10    1 10000010 01000000000000000000000    1 10010 0100000000
            -10    1 10000010 01000000000000000000000

           -0.1    1 01111011 10011001100110011001101    1 01011 1001100110
   -0.099975586    1 01111011 10011001100000000000000

           -0.2    1 01111100 10011001100110011001101    1 01100 1001100110
    -0.19995117    1 01111100 10011001100000000000000

    -0.30000001    1 01111101 00110011001100110011010    1 01101 0011001101
    -0.30004883    1 01111101 00110011010000000000000

         -65504    1 10001110 11111111110000000000000    1 11110 1111111111
         -65504    1 10001110 11111111110000000000000

         -65536    1 10001111 00000000000000000000000    1 11111 0000000000
           -inf    1 11111111 00000000000000000000000

         -65520    1 10001110 11111111111000000000000    1 11111 0000000000
           -inf    1 11111111 00000000000000000000000

     -65519.996    1 10001110 11111111110111111111111    1 11110 1111111111
         -65504    1 10001110 11111111110000000000000

     -65520.004    1 10001110 11111111111000000000001    1 11111 0000000000
           -inf    1 11111111 00000000000000000000000

  -4.290774e+09    1 10011110 11111111100000000000100    1 11111 0000000000
           -inf    1 11111111 00000000000000000000000

 -3.4028235e+38    1 11111110 11111111111111111111111    1 11111 0000000000
           -inf    1 11111111 00000000000000000000000

           -inf    1 11111111 00000000000000000000000    1 11111 0000000000
           -inf    1 11111111 00000000000000000000000

            nan    1 11111111 11111111111111111111111    1 11111 1111111111
            nan    1 11111111 11111111110000000000000

            nan    1 11111111 10101010101010101010101    1 11111 1010101010
            nan    1 11111111 10101010100000000000000

ok


------ Testing Bit testBitPatterns done!------

classification of bit patterns

              0    0 00000 0000000000    finite zero 
              1    0 01111 0000000000    finite normalized 
      1.0009766    0 01111 0000000001    finite normalized 
  5.9604645e-08    0 00000 0000000001    finite denormalized 
  1.1920929e-07    0 00000 0000000010    finite denormalized 
  6.1035156e-05    0 00001 0000000000    finite normalized 
  6.1094761e-05    0 00001 0000000001    finite normalized 
  6.0975552e-05    0 00000 1111111111    finite denormalized 
              2    0 10000 0000000000    finite normalized 
              3    0 10000 1000000000    finite normalized 
    0.099975586    0 01011 1001100110    finite normalized 
     0.19995117    0 01100 1001100110    finite normalized 
     0.30004883    0 01101 0011001101    finite normalized 
          65504    0 11110 1111111111    finite normalized 
            inf    0 11111 0000000000    infinity 
            nan    0 11111 1111111111    nan 
            nan    0 11111 1010101010    nan 
             -1    1 01111 0000000000    finite normalized negative 
     -1.0009766    1 01111 0000000001    finite normalized negative 
 -5.9604645e-08    1 00000 0000000001    finite denormalized negative 
 -1.1920929e-07    1 00000 0000000010    finite denormalized negative 
 -6.1035156e-05    1 00001 0000000000    finite normalized negative 
 -6.1094761e-05    1 00001 0000000001    finite normalized negative 
 -6.0975552e-05    1 00000 1111111111    finite denormalized negative 
             -2    1 10000 0000000000    finite normalized negative 
             -3    1 10000 1000000000    finite normalized negative 
   -0.099975586    1 01011 1001100110    finite normalized negative 
    -0.19995117    1 01100 1001100110    finite normalized negative 
    -0.30004883    1 01101 0011001101    finite normalized negative 
         -65504    1 11110 1111111111    finite normalized negative 
           -inf    1 11111 0000000000    infinity negative 
            nan    1 11111 1111111111    nan negative 
            nan    1 11111 1010101010    nan negative 

            inf    0 11111 0000000000    infinity 
           -inf    1 11111 0000000000    infinity negative 
            nan    0 11111 1111111111    nan 
            nan    0 11111 0111111111    nan 
ok


------ Testing Classification done!------

values in std::numeric_limits<half>
min_exponent
max_exponent
min_exponent10
max_exponent10
ok


------ Testing Limits done!------

halfFunction<T>
ok


------ Testing Function done!------


------ Testing finshed!------



```

#### IexTest

```

See if throw and catch work:
1
2
3
4
5
ok

```

#### ImathTest

```
Testing some basic vector operations
ok

Testing functions in ImathColor.h & ImathColorAlgo.h
rgb2packed -> packed2rgb
Imath::Color4 * f
Imath::Color4 / f
Assignment and comparison
ok

Testing functions in ImathShear.h
Imath::Shear6 constructors
Imath::Shear6 * f
Imath::Shear6 / f
Assignment and comparison
ok

Testing functions in ImathMatrix.h
Imath::M33f shear functions
M33f constructors and equality operators
M33d constructors and equality operators
M44f constructors and equality operators
M44d constructors and equality operators
Converting between M33 and M44
3x3 Matrix minors
3x3 determinant
Outer product of two 3D vectors
4x4 determinants
4x4 matrix minors
M44 multiplicaftion test
ok

Testing misc functions in ImathMatrixAlgo.h
Testing the building of an orthonormal direct frame from : a position, an x axis direction and a normal to the y axis
IMATH_INTERNAL_NAMESPACE::computeLocalFrame()
ok

Add a translate/rotate/scale offset to an input frame and put it in another frame of reference
IMATH_INTERNAL_NAMESPACE::addOffset()
ok

Compute Translate/Rotate/Scale matrix from matrix A 
with the Rotate/Scale of Matrix B
IMATH_INTERNAL_NAMESPACE::computeRSMatrix()
ok

Testing functions in ImathRoots.h

solveCubic
coefficients:   1   6  11   6  solutions: -3 -2 -1
coefficients:   2   2 -20  16  solutions: -4 1 2
coefficients:   3  -3   1  -1  solutions: 1
coefficients:   2   0 -24 -32  solutions: -2 4
coefficients:   1   0   0   0  solutions: -0
coefficients:   8 -24  24  -8  solutions: 1
coefficients:   0   2 -10  12  solutions: 2 3
coefficients:   0   1  -1 -20  solutions: -4 5
coefficients:   0   3 -12  12  solutions: 2
coefficients:   0   1   0   0  solutions: -0
coefficients:   0   1   0   1  solutions: none
coefficients:   0   0   3  -6  solutions: 2
coefficients:   0   0   5  15  solutions: -3
coefficients:   0   0   1   0  solutions: -0
coefficients:   0   0   0   1  solutions: none
coefficients:   0   0   0   0  solutions: [-inf, inf]

solveQuadratic
coefficients:   1   3   2  solutions: -2 -1
coefficients:   1   0  -9  solutions: -3 3
coefficients:   1  -4   0  solutions: 0 4
coefficients:   2  -4   2  solutions: 1
coefficients:   0  -4   8  solutions: 2
coefficients:   0   7   0  solutions: -0
coefficients:  10   0   0  solutions: -0
coefficients:   0   0   0  solutions: [-inf, inf]
coefficients:   0   0   1  solutions: none
coefficients:   3  -6  30  solutions: none
ok

Testing functions in ImathFun.h
floor
ceil
trunc
divs / mods
divp / modp
successor, predecessor

f 0
sf 1.40129846e-45
pf -1.40129846e-45
spf -0
psf 0

f -0
sf 1.40129846e-45
pf -1.40129846e-45
spf -0
psf 0

f 1
sf 1.00000012
pf 0.99999994
spf 1
psf 1

f -1
sf -0.99999994
pf -1.00000012
spf -1
psf -1

f 16
sf 16.0000019
pf 15.999999
spf 16
psf 16

f 7
sf 7.00000048
pf 6.99999952
spf 7
psf 7

f 0.699999988
sf 0.700000048
pf 0.699999928
spf 0.699999988
psf 0.699999988

f inf
sf inf
pf inf
spf inf
psf inf

f nan
sf nan
pf nan
spf nan
psf nan

f 3.40282347e+38
sf inf
pf 3.40282326e+38
spf 3.40282347e+38
psf inf

f -3.40282347e+38
sf -3.40282326e+38
pf -inf
spf -inf
psf -3.40282347e+38

d 0
sd 4.94065645841246544e-324
pd -4.94065645841246544e-324
spd -0
psd 0

d -0
sd 4.94065645841246544e-324
pd -4.94065645841246544e-324
spd -0
psd 0

d 1
sd 1.00000000000000022
pd 0.999999999999999889
spd 1
psd 1

d -1
sd -0.999999999999999889
pd -1.00000000000000022
spd -1
psd -1

d 16
sd 16.0000000000000036
pd 15.9999999999999982
spd 16
psd 16

d 7
sd 7.00000000000000089
pd 6.99999999999999911
spd 7
psd 7

d 0.699999999999999956
sd 0.700000000000000067
pd 0.699999999999999845
spd 0.699999999999999956
psd 0.699999999999999956

d inf
sd inf
pd inf
spd inf
psd inf

d nan
sd nan
pd nan
spd nan
psd nan

d 1.79769313486231571e+308
sd inf
pd 1.79769313486231551e+308
spd 1.79769313486231571e+308
psd inf

d -1.79769313486231571e+308
sd -1.79769313486231551e+308
pd -inf
spd -inf
psd -1.79769313486231571e+308
ok

Testing 4x4 and 3x3 matrix inversion:
M44f
M33f
ok

Testing functions in ImathFrustum.h
perspective 123
planes 
exceptions 123
orthographic 1
planes 
passed inequality test
passed equality test
ok

Testing random number generators
erand48(), nrand48()
Rand32
  values
  differences between successive values
  range
Rand48
  values
  differences between successive values
  range
solidSphereRand()
hollowSphereRand()
ok

Testing extraction of rotation angle from 3x3 matrices
Testing extraction of Euler angles from matrices
extractEulerXYZ()
order = 101
extractEulerZYX()
order = 2001
Eulerf::extract()
order = 101
order = 1
order = 1101
order = 1001
order = 2101
order = 2001
order = 11
order = 111
order = 1011
order = 1111
order = 2011
order = 2111
order = 2000
order = 2100
order = 1000
order = 1100
order = 0
order = 100
order = 2110
order = 2010
order = 1110
order = 1010
order = 110
order = 10
ok

Testing extraction of scale, shear, rotation, translation from matrices
Imath::extractSHRT()
  random angles
    3x3
    4x4
  special angles
    3x3
    4x4
ok

Testing basic quaternion operations
ok

Testing quaternion rotations
  exact 90-degree rotations
  exact zero-degree rotations
  exact 180-degree rotations
  other angles
  random from and to vectors
  nearly equal from and to vectors
  nearly opposite from and to vectors
ok

Testing quaternion spherical linear interpolation
  combinations of 90-degree rotations around x, y and z
  random rotations
ok

Testing line algorithms
closest points on two lines
  non-intersecting, non-parallel lines
  intersecting, non-parallel lines
  parallel lines
  coincident lines
  random lines
line-triangle intersection
  line-plane intersection inside triangle
  line-plane intersection outside triangle
  line parallel to triangle
  zero-area triangle
  random lines and triangles
ok

Testing box algorithms
  ray-box entry and exit, random rays
    box = ((-1 -1 -1) (1 1 1))
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((10 20 30) (1010 21 31))
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((10 20 30) (11 1020 31))
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((10 20 30) (11 21 1030))
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((-1e+10 -2e+10 -3e+10) (5e+15 6e+15 7e+15))
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((1 1 1) (2 1 1))
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((1 1 1) (1 2 1))
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((1 1 1) (1 1 2))
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((1 1 1) (1 2 3))
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((1 1 1) (2 3 1))
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((1 1 1) (2 1 3))
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((-1 -2 1) (-1 -2 1))
    single-point box, ray intersects
    single-point box, ray does not intersect
    box = ((1 1 1) (1 1 1))
    single-point box, ray intersects
    single-point box, ray does not intersect
    box = ((0 0 0) (0 0 0))
    single-point box, ray intersects
    single-point box, ray does not intersect
    empty box, no rays intersect
  ray-box entry and exit, nearly axis-parallel rays
    dir ~ (1 0 0), result = 1
    dir ~ (-1 0 0), result = 1
    dir ~ (1 0 0), result = 0
    dir ~ (-1 0 0), result = 0
    dir ~ (0 1 0), result = 1
    dir ~ (0 -1 0), result = 1
    dir ~ (0 1 0), result = 0
    dir ~ (0 -1 0), result = 0
    dir ~ (0 0 1), result = 1
    dir ~ (0 0 -1), result = 1
    dir ~ (0 0 1), result = 0
    dir ~ (0 0 -1), result = 0
  ray-box intersection, random rays
    box = ((-1 -1 -1) (1 1 1))
    ray starts inside box
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((10 20 30) (1010 21 31))
    ray starts inside box
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((10 20 30) (11 1020 31))
    ray starts inside box
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((10 20 30) (11 21 1030))
    ray starts inside box
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((-1e+10 -2e+10 -3e+10) (5e+15 6e+15 7e+15))
    ray starts inside box
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((1 1 1) (2 1 1))
    ray starts inside box
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((1 1 1) (1 2 1))
    ray starts inside box
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((1 1 1) (1 1 2))
    ray starts inside box
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((1 1 1) (1 2 3))
    ray starts inside box
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((1 1 1) (2 3 1))
    ray starts inside box
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((1 1 1) (2 1 3))
    ray starts inside box
    ray starts outside box, intersects
    ray starts outside box, does not intersect
    box = ((-1 -2 1) (-1 -2 1))
    single-point box, ray intersects
    single-point box, ray does not intersect
    box = ((1 1 1) (1 1 1))
    single-point box, ray intersects
    single-point box, ray does not intersect
    box = ((0 0 0) (0 0 0))
    single-point box, ray intersects
    single-point box, ray does not intersect
    empty box, no rays intersect
  ray-box intersection, nearly axis-parallel rays
    dir ~ (1 0 0), result = 1
    dir ~ (-1 0 0), result = 1
    dir ~ (1 0 0), result = 0
    dir ~ (-1 0 0), result = 0
    dir ~ (0 1 0), result = 1
    dir ~ (0 -1 0), result = 1
    dir ~ (0 1 0), result = 0
    dir ~ (0 -1 0), result = 0
    dir ~ (0 0 1), result = 1
    dir ~ (0 0 -1), result = 1
    dir ~ (0 0 1), result = 0
    dir ~ (0 0 -1), result = 0
  transform box by matrix
  closest points in and on box
ok

Testing box methods
    constructors for type V2s
    constructors for type V2i
    constructors for type V2f
    constructors for type V2d
    constructors for type V3s
    constructors for type V3i
    constructors for type V3f
    constructors for type V3d
    constructors for type V4s
    constructors for type V4i
    constructors for type V4f
    constructors for type V4d
    makeEmpty() for type V2s
    makeEmpty() for type V2i
    makeEmpty() for type V2f
    makeEmpty() for type V2d
    makeEmpty() for type V3s
    makeEmpty() for type V3i
    makeEmpty() for type V3f
    makeEmpty() for type V3d
    makeEmpty() for type V4s
    makeEmpty() for type V4i
    makeEmpty() for type V4f
    makeEmpty() for type V4d
    makeInfinite() for type V2s
    makeInfinite() for type V2i
    makeInfinite() for type V2f
    makeInfinite() for type V2d
    makeInfinite() for type V3s
    makeInfinite() for type V3i
    makeInfinite() for type V3f
    makeInfinite() for type V3d
    makeInfinite() for type V4s
    makeInfinite() for type V4i
    makeInfinite() for type V4f
    makeInfinite() for type V4d
    extendBy() point for type V2s
    extendBy() point for type V2i
    extendBy() point for type V2f
    extendBy() point for type V2d
    extendBy() point for type V3s
    extendBy() point for type V3i
    extendBy() point for type V3f
    extendBy() point for type V3d
    extendBy() point for type V4s
    extendBy() point for type V4i
    extendBy() point for type V4f
    extendBy() point for type V4d
    extendBy() box for type V2s
    extendBy() box for type V2i
    extendBy() box for type V2f
    extendBy() box for type V2d
    extendBy() box for type V3s
    extendBy() box for type V3i
    extendBy() box for type V3f
    extendBy() box for type V3d
    extendBy() box for type V4s
    extendBy() box for type V4i
    extendBy() box for type V4f
    extendBy() box for type V4d
    comparators for type V2s
    comparators for type V2i
    comparators for type V2f
    comparators for type V2d
    comparators for type V3s
    comparators for type V3i
    comparators for type V3f
    comparators for type V3d
    comparators for type V4s
    comparators for type V4i
    comparators for type V4f
    comparators for type V4d
    size() for type V2s
    size() for type V2i
    size() for type V2f
    size() for type V2d
    size() for type V3s
    size() for type V3i
    size() for type V3f
    size() for type V3d
    size() for type V4s
    size() for type V4i
    size() for type V4f
    size() for type V4d
    center() for type V2s
    center() for type V2i
    center() for type V2f
    center() for type V2d
    center() for type V3s
    center() for type V3i
    center() for type V3f
    center() for type V3d
    center() for type V4s
    center() for type V4i
    center() for type V4f
    center() for type V4d
    isEmpty() for type V2s
    isEmpty() for type V2i
    isEmpty() for type V2f
    isEmpty() for type V2d
    isEmpty() for type V3s
    isEmpty() for type V3i
    isEmpty() for type V3f
    isEmpty() for type V3d
    isEmpty() for type V4s
    isEmpty() for type V4i
    isEmpty() for type V4f
    isEmpty() for type V4d
    isInfinite() for type V2s
    isInfinite() for type V2i
    isInfinite() for type V2f
    isInfinite() for type V2d
    isInfinite() for type V3s
    isInfinite() for type V3i
    isInfinite() for type V3f
    isInfinite() for type V3d
    isInfinite() for type V4s
    isInfinite() for type V4i
    isInfinite() for type V4f
    isInfinite() for type V4d
    hasVolume() for type V2s
    hasVolume() for type V2i
    hasVolume() for type V2f
    hasVolume() for type V2d
    hasVolume() for type V3s
    hasVolume() for type V3i
    hasVolume() for type V3f
    hasVolume() for type V3d
    hasVolume() for type V4s
    hasVolume() for type V4i
    hasVolume() for type V4f
    hasVolume() for type V4d
    majorAxis() for type V2s
    majorAxis() for type V2i
    majorAxis() for type V2f
    majorAxis() for type V2d
    majorAxis() for type V3s
    majorAxis() for type V3i
    majorAxis() for type V3f
    majorAxis() for type V3d
    majorAxis() for type V4s
    majorAxis() for type V4i
    majorAxis() for type V4f
    majorAxis() for type V4d
ok

Testing Procrustes algorithms in single precision...
Testing known translate/rotate matrix:
 (  1.000000e+00   0.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00   1.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00   0.000000e+00   1.000000e+00   0.000000e+00
   0.000000e+00   0.000000e+00   0.000000e+00   1.000000e+00)
  OK
Testing known translate/rotate matrix:
 (  1.000000e+00   0.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00   1.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00   0.000000e+00   1.000000e+00   0.000000e+00
   3.000000e+00   5.000000e+00  -2.000000e-01   1.000000e+00)
  OK
Testing known translate/rotate matrix:
 (  1.000000e+00   0.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00  -1.000000e+00   1.224647e-16   0.000000e+00
   0.000000e+00  -1.224647e-16  -1.000000e+00   0.000000e+00
   3.000000e+00   5.000000e+00  -2.000000e-01   1.000000e+00)
  OK
Testing known translate/rotate matrix:
 (  7.071068e-01   8.659561e-17   7.071068e-01   0.000000e+00
   0.000000e+00  -1.000000e+00   1.224647e-16   0.000000e+00
   7.071068e-01  -8.659561e-17  -7.071068e-01   0.000000e+00
   3.000000e+00   5.000000e+00  -2.000000e-01   1.000000e+00)
  OK
Testing known translate/rotate matrix:
 ( -5.000000e-01   7.071068e-01  -5.000000e-01  -0.000000e+00
   5.000000e-01   7.071068e-01   5.000000e-01   0.000000e+00
   7.071068e-01  -8.659561e-17  -7.071068e-01   0.000000e+00
   3.000000e+00   5.000000e+00  -2.000000e-01   1.000000e+00)
  OK
Testing with known translate/rotate/scale matrix
(  1.000000e+00   0.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00   1.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00   0.000000e+00   1.000000e+00   0.000000e+00
   0.000000e+00   0.000000e+00   0.000000e+00   1.000000e+00)
numPoints: 1 2 3 4 5 6 7 8 9   OK
Testing with known translate/rotate/scale matrix
(  1.000000e+00   0.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00   1.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00   0.000000e+00   1.000000e+00   0.000000e+00
   4.000000e-01   6.000000e+00   1.000000e+01   1.000000e+00)
numPoints: 1 2 3 4 5 6 7 8 9   OK
Testing with known translate/rotate/scale matrix
(  1.000000e+00   0.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00  -1.000000e+00   1.224647e-16   0.000000e+00
   0.000000e+00  -1.224647e-16  -1.000000e+00   0.000000e+00
   4.000000e-01   6.000000e+00   1.000000e+01   1.000000e+00)
numPoints: 1 2 3 4 5 6 7 8 9   OK
Testing with known translate/rotate/scale matrix
(  7.071068e-01   8.659561e-17   7.071068e-01   0.000000e+00
   0.000000e+00  -1.000000e+00   1.224647e-16   0.000000e+00
   7.071068e-01  -8.659561e-17  -7.071068e-01   0.000000e+00
   4.000000e-01   6.000000e+00   1.000000e+01   1.000000e+00)
numPoints: 1 2 3 4 5 6 7 8 9   OK
Testing with known translate/rotate/scale matrix
( -5.000000e-01   7.071068e-01  -5.000000e-01  -0.000000e+00
   5.000000e-01   7.071068e-01   5.000000e-01   0.000000e+00
   7.071068e-01  -8.659561e-17  -7.071068e-01   0.000000e+00
   4.000000e-01   6.000000e+00   1.000000e+01   1.000000e+00)
numPoints: 1 2 3 4 5 6 7 8 9   OK
Testing with known translate/rotate/scale matrix
( -1.000000e+00   1.414214e+00  -1.000000e+00  -0.000000e+00
   1.000000e+00   1.414214e+00   1.000000e+00   0.000000e+00
   1.414214e+00  -1.731912e-16  -1.414214e+00   0.000000e+00
   4.000000e-01   6.000000e+00   1.000000e+01   1.000000e+00)
numPoints: 1 2 3 4 5 6 7 8 9   OK
Testing with known translate/rotate/scale matrix
( -1.000000e-02   1.414214e-02  -1.000000e-02  -0.000000e+00
   1.000000e-02   1.414214e-02   1.000000e-02   0.000000e+00
   1.414214e-02  -1.731912e-18  -1.414214e-02   0.000000e+00
   4.000000e-01   6.000000e+00   1.000000e+01   1.000000e+00)
numPoints: 1 2 3 4 5 6 7 8 9   OK
Testing Procrustes algorithm with arbitrary matrix: 
( -1.000000e-02   1.414214e-02  -1.000000e-02  -0.000000e+00
   1.000000e-02   1.414214e-02   1.000000e-02   0.000000e+00
   1.414214e-02  -1.731912e-18  -1.414214e-02   0.000000e+00
   4.000000e-01   6.000000e+00   1.000000e+01   1.000000e+00)
   numPoints: 1 2 3 4 5 6 7 8 9 OK
Testing Procrustes algorithm with arbitrary matrix: 
( -1.000000e-02   1.414214e-02  -1.000000e-02  -0.000000e+00
   1.000000e-02   1.414214e-02   1.000000e-02   0.000000e+00
   1.414214e-02  -1.731912e-18  -1.414214e-02   0.000000e+00
   4.241421e-01   6.098995e+00   9.995858e+00   1.000000e+00)
   numPoints: 1 2 3 4 5 6 7 8 9 OK
Testing Procrustes algorithm with arbitrary matrix: 
( -1.000000e-02   1.414214e-02  -1.000000e-02  -0.000000e+00
   1.000000e-02   1.414214e-02   1.000000e-02   0.000000e+00
   1.414214e-02  -1.731912e-18  -1.414214e-02   0.000000e+00
   5.582843e-01   5.985858e+00   1.010172e+01   1.000000e+00)
   numPoints: 1 2 3 4 5 6 7 8 9 OK
Testing Procrustes algorithm with arbitrary matrix: 
(  1.219579e-02   1.573132e-02   1.946348e-03   0.000000e+00
   5.124720e-03  -1.589186e-03  -1.926686e-02   0.000000e+00
  -1.500000e-02   1.224745e-02  -5.000000e-03   0.000000e+00
   6.842304e+00  -5.755414e+00  -7.631837e+00   1.000000e+00)
   numPoints: 1 2 3 4 5 6 7 8 9 OK
Testing Procrustes algorithm with arbitrary matrix: 
(  1.829368e-02   2.359698e-02   2.919522e-03   0.000000e+00
   3.279821e-02  -1.017079e-02  -1.233079e-01   0.000000e+00
  -3.000000e-02   2.449490e-02  -1.000000e-02   0.000000e+00
   6.842304e+00  -5.755414e+00  -7.631837e+00   1.000000e+00)
   numPoints: 1 2 3 4 5 6 7 8 9 OK
Testing Procrustes algorithm with arbitrary matrix: 
( -2.546762e-03  -9.270112e-03   2.841794e-02  -0.000000e+00
  -7.301607e-02   1.017024e-01   2.663240e-02   0.000000e+00
   3.267767e-02   2.090770e-02   9.748737e-03   0.000000e+00
  -1.106096e+01   3.731658e+00   1.384479e+00   1.000000e+00)
   numPoints: 1 2 3 4 5 6 7 8 9 OK
Testing Procrustes algorithm with arbitrary matrix: 
( -2.546762e-03  -9.270112e-03   2.841794e-02  -0.000000e+00
  -7.301607e-05   1.017024e-04   2.663240e-05   0.000000e+00
   3.267767e-02   2.090770e-02   9.748737e-03   0.000000e+00
  -1.106096e+01   3.731658e+00   1.384479e+00   1.000000e+00)
   numPoints: 1 2 3 4 5 6 7 8 9 OK
Testing Procrustes algorithm with arbitrary matrix: 
( -2.546762e-03  -9.270112e-03   2.841794e-02  -0.000000e+00
  -7.301607e-05   1.017024e-04   2.663240e-05   0.000000e+00
   0.000000e+00   0.000000e+00   0.000000e+00   0.000000e+00
  -1.106096e+01   3.731658e+00   1.384479e+00   1.000000e+00)
   numPoints: 1 2 3 4 5 6 7 8 9 OK
Testing Procrustes algorithms in double precision...
Testing known translate/rotate matrix:
 (  1.000000e+00   0.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00   1.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00   0.000000e+00   1.000000e+00   0.000000e+00
   0.000000e+00   0.000000e+00   0.000000e+00   1.000000e+00)
  OK
Testing known translate/rotate matrix:
 (  1.000000e+00   0.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00   1.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00   0.000000e+00   1.000000e+00   0.000000e+00
   3.000000e+00   5.000000e+00  -2.000000e-01   1.000000e+00)
  OK
Testing known translate/rotate matrix:
 (  1.000000e+00   0.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00  -1.000000e+00   1.224647e-16   0.000000e+00
   0.000000e+00  -1.224647e-16  -1.000000e+00   0.000000e+00
   3.000000e+00   5.000000e+00  -2.000000e-01   1.000000e+00)
  OK
Testing known translate/rotate matrix:
 (  7.071068e-01   8.659561e-17   7.071068e-01   0.000000e+00
   0.000000e+00  -1.000000e+00   1.224647e-16   0.000000e+00
   7.071068e-01  -8.659561e-17  -7.071068e-01   0.000000e+00
   3.000000e+00   5.000000e+00  -2.000000e-01   1.000000e+00)
  OK
Testing known translate/rotate matrix:
 ( -5.000000e-01   7.071068e-01  -5.000000e-01  -0.000000e+00
   5.000000e-01   7.071068e-01   5.000000e-01   0.000000e+00
   7.071068e-01  -8.659561e-17  -7.071068e-01   0.000000e+00
   3.000000e+00   5.000000e+00  -2.000000e-01   1.000000e+00)
  OK
Testing with known translate/rotate/scale matrix
(  1.000000e+00   0.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00   1.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00   0.000000e+00   1.000000e+00   0.000000e+00
   0.000000e+00   0.000000e+00   0.000000e+00   1.000000e+00)
numPoints: 1 2 3 4 5 6 7 8 9   OK
Testing with known translate/rotate/scale matrix
(  1.000000e+00   0.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00   1.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00   0.000000e+00   1.000000e+00   0.000000e+00
   4.000000e-01   6.000000e+00   1.000000e+01   1.000000e+00)
numPoints: 1 2 3 4 5 6 7 8 9   OK
Testing with known translate/rotate/scale matrix
(  1.000000e+00   0.000000e+00   0.000000e+00   0.000000e+00
   0.000000e+00  -1.000000e+00   1.224647e-16   0.000000e+00
   0.000000e+00  -1.224647e-16  -1.000000e+00   0.000000e+00
   4.000000e-01   6.000000e+00   1.000000e+01   1.000000e+00)
numPoints: 1 2 3 4 5 6 7 8 9   OK
Testing with known translate/rotate/scale matrix
(  7.071068e-01   8.659561e-17   7.071068e-01   0.000000e+00
   0.000000e+00  -1.000000e+00   1.224647e-16   0.000000e+00
   7.071068e-01  -8.659561e-17  -7.071068e-01   0.000000e+00
   4.000000e-01   6.000000e+00   1.000000e+01   1.000000e+00)
numPoints: 1 2 3 4 5 6 7 8 9   OK
Testing with known translate/rotate/scale matrix
( -5.000000e-01   7.071068e-01  -5.000000e-01  -0.000000e+00
   5.000000e-01   7.071068e-01   5.000000e-01   0.000000e+00
   7.071068e-01  -8.659561e-17  -7.071068e-01   0.000000e+00
   4.000000e-01   6.000000e+00   1.000000e+01   1.000000e+00)
numPoints: 1 2 3 4 5 6 7 8 9   OK
Testing with known translate/rotate/scale matrix
( -1.000000e+00   1.414214e+00  -1.000000e+00  -0.000000e+00
   1.000000e+00   1.414214e+00   1.000000e+00   0.000000e+00
   1.414214e+00  -1.731912e-16  -1.414214e+00   0.000000e+00
   4.000000e-01   6.000000e+00   1.000000e+01   1.000000e+00)
numPoints: 1 2 3 4 5 6 7 8 9   OK
Testing with known translate/rotate/scale matrix
( -1.000000e-02   1.414214e-02  -1.000000e-02  -0.000000e+00
   1.000000e-02   1.414214e-02   1.000000e-02   0.000000e+00
   1.414214e-02  -1.731912e-18  -1.414214e-02   0.000000e+00
   4.000000e-01   6.000000e+00   1.000000e+01   1.000000e+00)
numPoints: 1 2 3 4 5 6 7 8 9   OK
Testing Procrustes algorithm with arbitrary matrix: 
( -1.000000e-02   1.414214e-02  -1.000000e-02  -0.000000e+00
   1.000000e-02   1.414214e-02   1.000000e-02   0.000000e+00
   1.414214e-02  -1.731912e-18  -1.414214e-02   0.000000e+00
   4.000000e-01   6.000000e+00   1.000000e+01   1.000000e+00)
   numPoints: 1 2 3 4 5 6 7 8 9 OK
Testing Procrustes algorithm with arbitrary matrix: 
( -1.000000e-02   1.414214e-02  -1.000000e-02  -0.000000e+00
   1.000000e-02   1.414214e-02   1.000000e-02   0.000000e+00
   1.414214e-02  -1.731912e-18  -1.414214e-02   0.000000e+00
   4.241421e-01   6.098995e+00   9.995858e+00   1.000000e+00)
   numPoints: 1 2 3 4 5 6 7 8 9 OK
Testing Procrustes algorithm with arbitrary matrix: 
( -1.000000e-02   1.414214e-02  -1.000000e-02  -0.000000e+00
   1.000000e-02   1.414214e-02   1.000000e-02   0.000000e+00
   1.414214e-02  -1.731912e-18  -1.414214e-02   0.000000e+00
   5.582843e-01   5.985858e+00   1.010172e+01   1.000000e+00)
   numPoints: 1 2 3 4 5 6 7 8 9 OK
Testing Procrustes algorithm with arbitrary matrix: 
(  1.219579e-02   1.573132e-02   1.946348e-03   0.000000e+00
   5.124720e-03  -1.589186e-03  -1.926686e-02   0.000000e+00
  -1.500000e-02   1.224745e-02  -5.000000e-03   0.000000e+00
   6.842304e+00  -5.755414e+00  -7.631837e+00   1.000000e+00)
   numPoints: 1 2 3 4 5 6 7 8 9 OK
Testing Procrustes algorithm with arbitrary matrix: 
(  1.829368e-02   2.359698e-02   2.919522e-03   0.000000e+00
   3.279821e-02  -1.017079e-02  -1.233079e-01   0.000000e+00
  -3.000000e-02   2.449490e-02  -1.000000e-02   0.000000e+00
   6.842304e+00  -5.755414e+00  -7.631837e+00   1.000000e+00)
   numPoints: 1 2 3 4 5 6 7 8 9 OK
Testing Procrustes algorithm with arbitrary matrix: 
( -2.546762e-03  -9.270112e-03   2.841794e-02  -0.000000e+00
  -7.301607e-02   1.017024e-01   2.663239e-02   0.000000e+00
   3.267767e-02   2.090770e-02   9.748737e-03   0.000000e+00
  -1.106096e+01   3.731658e+00   1.384479e+00   1.000000e+00)
   numPoints: 1 2 3 4 5 6 7 8 9 OK
Testing Procrustes algorithm with arbitrary matrix: 
( -2.546762e-03  -9.270112e-03   2.841794e-02  -0.000000e+00
  -7.301607e-05   1.017024e-04   2.663239e-05   0.000000e+00
   3.267767e-02   2.090770e-02   9.748737e-03   0.000000e+00
  -1.106096e+01   3.731658e+00   1.384479e+00   1.000000e+00)
   numPoints: 1 2 3 4 5 6 7 8 9 OK
Testing Procrustes algorithm with arbitrary matrix: 
( -2.546762e-03  -9.270112e-03   2.841794e-02  -0.000000e+00
  -7.301607e-05   1.017024e-04   2.663239e-05   0.000000e+00
   0.000000e+00   0.000000e+00   0.000000e+00   0.000000e+00
  -1.106096e+01   3.731658e+00   1.384479e+00   1.000000e+00)
   numPoints: 1 2 3 4 5 6 7 8 9 OK
Testing TinySVD algorithms in single precision...
Verifying SVD for [[1, 0, 0], [0, 1, 0], [0, 0, 1]]
Verifying SVD for [[1, 0, 0], [0, -1, 0], [0, 0, 1]]
Verifying SVD for [[0, 0, 0], [0, 0, 0], [0, 0, 0]]
Verifying SVD for [[0, 0, 0], [0, 0, 0], [0, 0, 1]]
Verifying SVD for [[1, 0, 0], [0, 1, 0], [0, 0, 0]]
Verifying SVD for [[1, 0, 0], [0, 0, 0], [0, 0, 0]]
Verifying SVD for [[1, 0, 0], [1e-10, 0, 0], [0, 0, 0]]
Verifying SVD for [[1, 0, 0], [1e-10, 0, 0], [0, 0, 100000]]
Verifying SVD for [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
Verifying SVD for [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
Verifying SVD for [[10000, 0.001, 0], [0.001, 1e-10, 0], [0, 0, 0]]
Verifying SVD for [[62720, 73500, 4900], [5120, 6000, 400], [256, 300, 20]]
Verifying SVD for [[60026, 4902, 248], [4902, 404, 26], [248, 26, 10]]
Verifying SVD for [[0.00235883, -0.00965581, 0.00109599], [0.00886718, 0.00167718, -0.00430815], [0.00397605, 0.00198805, 0.0089576]]
Verifying SVD for [[2.35883e-09, -9.65581e-09, 1.09599e-09], [8.86718e-09, 1.67718e-09, -4.30815e-09], [3.97605e-09, 1.98805e-09, 8.9576e-09]]
Verifying SVD for [[-0.466739, 0.674663, 0.97647], [-0.0324608, 0.0465845, 0.0674312], [-0.0888851, 0.128039, 0.185326]]
Verifying SVD for [[1e-08, 0, 0], [0, 1e-08, 0], [0, 0, 1e-08]]
Verifying SVD for [[1, 0, 0], [0, 0.00036, 0], [1e-18, 0, 0.00018]]
Verifying SVD for [[1.3, 0, 0], [0, 0.0003, 0], [1e-17, 0, 0]]
Verifying SVD for [[1, 0, 0], [0, 0.01, 0], [0, 0, 0.01]]
Verifying SVD for [[1, 0, 0], [0, 1, 0], [0, 0, 0]]
Verifying SVD for [[1, 0, 0], [0, 0.001, 0], [0, 0, 1e-06]]
Verifying SVD for [[0.595886, -0.797612, -1], [0.391945, 0.917631, -0.341818], [-0.450561, -0.712591, 0.47125]]
Verifying SVD for [[4.38805e-09, -2.5319e-09, -4.65679e-09], [-3.23e-10, 1.8637e-10, 3.42781e-10], [-4.61573e-09, 2.66326e-09, 4.8984e-09]]
Verifying SVD for [[0, -1e-22, 0], [1e-07, 0, 0], [0, 0, 0]]
Verifying SVD for [[0, -1e-22, 0], [1e-07, 0, 0], [0, 0, 1]]
Verifying SVD for [[1, 0, 0, 0], [0, 1, 0, 0], [0, 0, 1, 0], [0, 0, 0, 1]]
Verifying SVD for [[1, 0, 0, 0], [0, -1, 0, 0], [0, 0, 1, 0], [0, 0, 0, 1]]
Verifying SVD for [[1, 0, 0, 0], [0, 1, 0, 0], [0, 0, 1, 0], [0, 0, 0, 0]]
Verifying SVD for [[1, 0, 0, 0], [0, 1, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0]]
Verifying SVD for [[0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0]]
Verifying SVD for [[1, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0]]
Verifying SVD for [[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12], [13, 14, 15, 16]]
Verifying SVD for [[0, -1e-22, 0, 0], [1e-07, 0, 0, 0], [0, 0, 1, 0], [0, 0, 0, 1]]
Verifying SVD for [[10000, 0.001, 0, 0], [0.001, 1e-10, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0]]
Verifying SVD for [[62720, 73500, 4900, 2450], [5120, 6000, 400, 2450], [256, 300, 20, 2450], [128, 150, 10, 5]]
Verifying SVD for [[62750, 73560, 4990, 2540], [5130, 6020, 430, 2540], [266, 320, 50, 2540], [138, 170, 40, 35]]
Testing TinySVD algorithms in double precision...
Verifying SVD for [[1, 0, 0], [0, 1, 0], [0, 0, 1]]
Verifying SVD for [[1, 0, 0], [0, -1, 0], [0, 0, 1]]
Verifying SVD for [[0, 0, 0], [0, 0, 0], [0, 0, 0]]
Verifying SVD for [[0, 0, 0], [0, 0, 0], [0, 0, 1]]
Verifying SVD for [[1, 0, 0], [0, 1, 0], [0, 0, 0]]
Verifying SVD for [[1, 0, 0], [0, 0, 0], [0, 0, 0]]
Verifying SVD for [[1, 0, 0], [1e-10, 0, 0], [0, 0, 0]]
Verifying SVD for [[1, 0, 0], [1e-10, 0, 0], [0, 0, 100000]]
Verifying SVD for [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
Verifying SVD for [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
Verifying SVD for [[10000, 0.001, 0], [0.001, 1e-10, 0], [0, 0, 0]]
Verifying SVD for [[62720, 73500, 4900], [5120, 6000, 400], [256, 300, 20]]
Verifying SVD for [[60026, 4902, 248], [4902, 404, 26], [248, 26, 10]]
Verifying SVD for [[0.00235883, -0.00965581, 0.00109599], [0.00886718, 0.00167718, -0.00430815], [0.00397605, 0.00198805, 0.0089576]]
Verifying SVD for [[2.35883e-09, -9.65581e-09, 1.09599e-09], [8.86718e-09, 1.67718e-09, -4.30815e-09], [3.97605e-09, 1.98805e-09, 8.9576e-09]]
Verifying SVD for [[-0.466739, 0.674663, 0.97647], [-0.0324608, 0.0465845, 0.0674312], [-0.0888851, 0.128039, 0.185326]]
Verifying SVD for [[1e-08, 0, 0], [0, 1e-08, 0], [0, 0, 1e-08]]
Verifying SVD for [[1, 0, 0], [0, 0.00036, 0], [1e-18, 0, 0.00018]]
Verifying SVD for [[1.3, 0, 0], [0, 0.0003, 0], [1e-17, 0, 0]]
Verifying SVD for [[1, 0, 0], [0, 0.01, 0], [0, 0, 0.01]]
Verifying SVD for [[1, 0, 0], [0, 1, 0], [0, 0, 0]]
Verifying SVD for [[1, 0, 0], [0, 0.001, 0], [0, 0, 1e-06]]
Verifying SVD for [[0.595886, -0.797612, -1], [0.391945, 0.917631, -0.341818], [-0.450561, -0.712591, 0.47125]]
Verifying SVD for [[4.38805e-09, -2.5319e-09, -4.65679e-09], [-3.23e-10, 1.8637e-10, 3.42781e-10], [-4.61573e-09, 2.66326e-09, 4.8984e-09]]
Verifying SVD for [[0, -1e-22, 0], [1e-07, 0, 0], [0, 0, 0]]
Verifying SVD for [[0, -1e-22, 0], [1e-07, 0, 0], [0, 0, 1]]
Verifying SVD for [[1, 0, 0, 0], [0, 1, 0, 0], [0, 0, 1, 0], [0, 0, 0, 1]]
Verifying SVD for [[1, 0, 0, 0], [0, -1, 0, 0], [0, 0, 1, 0], [0, 0, 0, 1]]
Verifying SVD for [[1, 0, 0, 0], [0, 1, 0, 0], [0, 0, 1, 0], [0, 0, 0, 0]]
Verifying SVD for [[1, 0, 0, 0], [0, 1, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0]]
Verifying SVD for [[0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0]]
Verifying SVD for [[1, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0]]
Verifying SVD for [[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12], [13, 14, 15, 16]]
Verifying SVD for [[0, -1e-22, 0, 0], [1e-07, 0, 0, 0], [0, 0, 1, 0], [0, 0, 0, 1]]
Verifying SVD for [[10000, 0.001, 0, 0], [0.001, 1e-10, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0]]
Verifying SVD for [[62720, 73500, 4900, 2450], [5120, 6000, 400, 2450], [256, 300, 20, 2450], [128, 150, 10, 5]]
Verifying SVD for [[62750, 73560, 4990, 2540], [5130, 6020, 430, 2540], [266, 320, 50, 2540], [138, 170, 40, 35]]

************ Testing IMATH_INTERNAL_NAMESPACE::ImathJacobiEigenSolver ************
Jacobi EigenSolver in single precision...PASS
Jacobi EigenSolver in double precision...PASS
Min/Max EigenValue in single precision...PASS
Min/Max EigenValue in double precision...PASS
Timing Jacobi EigenSolver in single precision...
Jacobi EigenSolver of 3x3 matrices took 510000 clocks.
TinySVD            of 3x3 matrices took 507000 clocks.
-0.591716% speed up.
Jacobi EigenSolver of 4x4 matrices took 781000 clocks
TinySVD            of 4x4 matrices took 1527000 clocks
48.854% speed up.
Timing Jacobi EigenSolver in double precision...
Jacobi EigenSolver of 3x3 matrices took 344000 clocks.
TinySVD            of 3x3 matrices took 539000 clocks.
36.1781% speed up.
Jacobi EigenSolver of 4x4 matrices took 901000 clocks
TinySVD            of 4x4 matrices took 2256000 clocks
60.0621% speed up.
************      ALL PASS          ************
Testing functions in ImathFrustumTest.h
isVisible(Vec3) passed Vec3
passed Box
passed Sphere

ok





```




### 2014/12/26

Holidays are the best time to work on new projects. I carried around this idea for very long and started working on it today.


