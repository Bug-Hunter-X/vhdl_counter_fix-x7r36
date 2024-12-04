# VHDL Counter Off-by-One Error
This repository demonstrates a subtle off-by-one error in a simple VHDL counter.  The error is in the handling of the counter's maximum value.  The provided solution corrects the issue and explains the problem in detail.

## Bug Description
The `buggy_counter` entity uses a simple process to increment a counter on each rising clock edge. However, when the counter reaches its maximum value (15), the reset condition `internal_count <= 0;` might cause a one-cycle delay before the actual reset occurs, potentially leading to incorrect behavior in a larger system. This is because the value of `internal_count` is not updated until the end of the process in this version. 

## Solution
The `bugSolution.vhdl` file provides a corrected version of the counter that immediately resets to 0 using `internal_count <= 0;` in the `elsif` condition.