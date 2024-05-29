# CoqIEEE754Validation
This is the code developed during my bachelor's thesis on validating floating-point operations in Coq. 

## Usage

To generate test vectors using Berekley TestFloat, edit the variable `testfloat_gen` in the Makefile. It needs to contain the path to the `testfloat_gen` executable. Test vectors are generated by running `make testfloat format="f32" level="1"`. This will generate test vectors for operations add, sub, mult, div and sqrt. Change the makefile to include fma. Change the format and level accordingly. To generate a specific amount of test vectors, eg. 1 000 000 test vectors, add `n="-n 1000000"`:

```
make testfloat format="f32" level="1" n="-n 1000000"
```

These test vectors can be run with `make run_testfloat format="f32" level="1"`. Change level and format accordingly. The result of the test runs can be found in the folder `testfloat_results`. 

Any folder of containing TestFloat test vectors (that follow the same naming scheme as the ones generated with the makefile) can be run with the script `RunTestFloatTests.sh`. It takes the path to the folder and the rounding mode as argument. A text file containing test vectors can be run separately with `runner_test_float.py` as well, which requires the format, file path, operation and rounding mode as arguments.

Fused multiply-add can be generated separately with `make testfloat_fma format="f32"`. These are ran with `make run_fma format="f32"`.

