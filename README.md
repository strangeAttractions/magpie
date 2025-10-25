# magpie
Expect no more than a bunch a pseudocode scratchwork -- *not remotely runnable* -- but intended to eventually become a dependent-typed Scheme that would serve as a metalanguage
for implementing dependent-typed languages.
For now, the placeholder name is 'Magpie' -- a mischievous bird, in accordance to both its Scheme lineage and dependent-typed aspirations.
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
- Signatures and Modules foremost; the core theory comprises telescopes (of judgements) and equalities -- everything else is derived

While each of the above points has been achieved in multiple existing langs, I do not think any of them *quite* meet these aspirations. Or maybe I just like Scheme syntax
better than Agda's or Lean's.  
Disclaimer: I am not a professional type theorist or computer scientist. I began in molecular biology; only a few years ago did I realize how much I enjoyed, and want to learn
more of, math and programming. So I will need all the help I can get (easier said than done, when I am not personally acquainted with any computer scientists!)
This is likely to be a many years long project, even with the minimalism of the lang even if I do find help. In fact, I am still trying to figure out *what the underlying
semantics should be*, and *what the best design for the implementation should be*. So this is only a dream, for now (hopefully not A Dream of Spring...).

Main inspirations:
- Scheme: balance of minimalism & expressivity for (uni-typed) lambda calc; 'shaped like its semantics'
  - Magpie's surface syntax will closely resemble that of Scheme
- Standard ML: balance of minimalism & expressivity for restriction of System F & parameterized modules
  - Note: said 'minimalism' is the small set of built-ins; SML's surface syntax is (for my taste) somewhat verbose
- SmallTT (Kovacs): techniques for *efficient NbE* in dependent-typed system (by controlled unfolding in particular)
- Andromeda 2 (Bauer et al): generic framework for implementing type systems as algebraic theories
- BiTTs (Felicissimo): generic bidirectional typing (to make the convenience of partial annotation compatible with an algebraic representation)
- Pterodactyl (Sterling's WIP): telescopes as fundamental, module operations as extending & quotienting telescopes
- ModTT+ParamTT (Sterling & Harper 2021) / MTT (Gratzer et al 2019-23): modal type system for phased compilation/evaluation
  - this may or may not be possible to implement in sufficiently generic way

