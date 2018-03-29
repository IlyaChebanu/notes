### Parallelism paradigm shift
Because modern CPUs have multiple cores, and therefore can execute instructions in parallel, nowadays it is more favourable to write code that uses more cycles but has to access memory less because accessing memory is much slower.

Accessing RAM takes thousands of CPU cycles

### Cache optimization
To decrease D-cache misses organise data in contiguous blocks that are as small as possible and access them sequentially (no jumping around within the contiguous memory block).
To decrease I-cache misses keep high performance loops as small as possible and avoid calling functions within innermost loops.

