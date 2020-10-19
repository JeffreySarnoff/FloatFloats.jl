# PairArithmetic.jl

### Copyright ©2020 by Jeffrey Sarnoff. This material is made available under the MIT License.

----

## The Concept

### create a more performant, less demanding analog of `Double64s`
   - introduce hardwon improvements in error-free transformations
   - allow faithful rounding within the least significant octet

## The Extended Precision Arithmetic

#### when working with unexceptional values
   - processing advantages  
        - improves speed for primitives
        - improves operational throughput
   - expected accuracy   
        - primitives are accurate to 104 significant bits  
        - simple operations are accurate to 100 bits
        - common computations should keep 85 good bits

#### when using exceptional values
   - with _NaNs_
       - special case logic requires branching
   - with _subnormals_    
       - subnormals are inherently slow on most processors
   - with tiny or huge values ∉ [floatmin(T)^(3/4), floatmax(T)^(3/4)]
       - indivdual operations are computed without accuracy guards
   
### design for interoperable advantage   
   - make ready the use of `StructArrays.jl` with Vectors and Matricies of `Pairs`
       - this is a requirement for best success in applying LoopVectorization.jl
 
----

## References

- for the _Pair Arithmetic_ defintions
```
Faithfully Rounded Floating-point Computations
by Marko Lange and Siegfried M. Rump
ACM Transactions on Mathematical Software, July 2020, Article No.: 21
https://doi.org/10.1145/3290955
```
