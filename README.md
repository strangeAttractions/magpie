# magpie
Currently just a bunch a pseudocode scratchwork that is *not remotely runnable*, but is (intended to) eventually become a dependent-typed Scheme that would serve as a 
metalanguage for implementing dependent-typed languages.
For now, the placeholder name is 'magpie' -- a mischievous bird, in accordance to both its Scheme lineage and dependent-typed aspirations.
To start, the source lang will be Racket, though this will mostly be used as a 'batteries-included' Scheme. If I do not get as much from Racket's (powerful, but rather 
complicated) macro knobs and handles as initially expected (i.e. if only a deep embedding is feasible, rather than shallow or mixed), then this will be rewritten in Chez Scheme. 
Or perhaps even in an ML-family lang, as I become more experienced with SML (or take up Haskell).
The eventual goal is a framework in which to construct type systems, without interleaved escapes to its host lang, and potentially implement macro systems *within* those type 
systems, rather than needing to modify the type systems ad hoc to fit the host lang. 
That is, it should be a dependent-typed lang which is itself extensible and capable of meta-programming, rather than only being a rigid target implemented in Racket (such that 
extensions to the lang must always escape to Racket, or rather than only being an embedded DSL, a la Turnstile).
A bit more on the envisioned characteristics of the lang:
- Provides a framework for implementing typed langs
  - Minimal + readable core; can be reasoned about by inspection (and, to some degree, 'shaped like its semantics')
  - Stdlib(s) contain most of the derivable functions and type system specifications
  - Avoid dependence on nonstandard packages / extensions for standard functionalities
    - i.e. users can build up various type systems from core, but pre-written base systems should be standardized
  - Completely and precisely specified language
    - Could potentially be implemented in other host langs, as long as specs are satisfied
    - Could be formalized (e.g. in Twelf)
    - No larger than Standard ML
- Clarifies the underlying logic of dependent type systems and their semantics through its simplicity
  - i.e. Magpie should be to dependent-typed logic as Scheme is to uni-typed lambda calculus
- Extremely extensible
- Suitable for both programming and proving (should not be too deficient in either)
  - Interactions for incremental development
  - Straightforward system for extending or specializing modules and their signatures
  - Relatively efficient (e.g. implementation ideas from Andras Kovacs' SmallTT)
- Signatures + Modules foremost; the core theory comprises telescopes (of judgements) and equalities -- everything else is derived
