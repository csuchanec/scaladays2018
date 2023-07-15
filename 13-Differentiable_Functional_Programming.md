# Differentiable Functional Programming

@noelwelsh

* deep learning isn't deep & functional

* what is deep learning
  * supervised learning by paramertized function by gradient descent

* paramatrized function - functions returning functions - parameter gives us a family of functions
* supervised learning - choose parameters to fit data
* gradient decent - how to choose the parameters
    * calculate the derivative of the loss function with respect to the parameters - trying to decrease the error
    * this tells the direction of the gradient
    * then take small step in downhill direction

* choice of functions that is expressive
  * want to be reasonable amount to 
  * choice of functions is suited ot gpu exceleration
  * tesors - multidimensional arrays
  * generalize to matrix math
  * matrix "weights" are parameters

* non-linearity - basically any non-linear function
  * ReLU(x) = max(0, x)
  * f(x) = ReLU(x * Weights)  <- Layer
* deep compose many (compose functions)

* look at Tensor flow

* Differentiable Programming
  * software that automatically calculates derivatives and compiles to GPU code
  * become more complex with flows in them


* Automatic Differentiation
  * derivatives are compisitional
    * functions compose --> g . f = g(f(x))
    * the derivative can be calculated independently
  * calculate gradient
    * Mathamatical approach - gets exact answer (just take derivative) but size of derivative grows exposntional
    * programmers approach - use epsilon and just and run function twice then divide by epsilon
    * automatic diferentiation approach
      * Forward Mode AD - calculate with dual numbers
        a + bE,  E^2=0
        * manipulation of chain rule
          f(a + bE) = f(a) + f'(a)bE
          * there is a monad for dual numbers -- flatmap
          * forward mode scalse in the size of the input dimension
      * Reverse Mode 
        * chain rule doesn't care about the order so we can flip it around and calculate it backwards
        * you need a representation of control flow because you have to go back over it
        * Use monad or continuations
        * scalse on the size of the output dimension and usually the output is much smaller than the input

* for deep learning, generalize to tensors

https://github.com/noelwelsh/fdl







