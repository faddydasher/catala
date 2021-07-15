# OCaml French Law Library

This folder contains a ready-to-use OCaml library featuring French public
algorithms coded up in Catala.

## Organization

### Law source

The `law_source` folder contains the files generated by the Catala compiler.
These files are generated using the following rule from the top-level `Makefile`
of this repository:

```
make generate_french_law_library_ocaml
```

They can be compiled using

```
make build_french_law_library_ocaml
```

In particular, `law_source/unit_tests/run_tests.ml` provides an executable
that runs the unit tests coming from the source Catala examples, and that can
be launched with

```
make run_french_law_library_ocaml_tests
```

The `law_source` files rely on the Catala OCaml runtime, located in
`compiler/runtime.{ml, mli}`. This runtime defines the types of the values
manipulated by the Catala programs in OCaml and the operations available for them.

### Wrappers

Then, the `api.{ml, mli}` module provides a wrapper around the functions
exported in `law_source`. These wrappers mostly convert back and forth between
idiomatic OCaml types and the types expected by the Catala programs in OCaml.

`api.web.ml` is used for the JS library (see the [dedicated README](../js/README.md)).

Finally, `bench.ml` provides a simple benchmarking executable that runs the
computations of each algorithm a bunch of times with random inputs. You can run it
from the root of this repository with

```
make run_french_law_library_benchmark_ocaml
```