# Uncommon VHDL Process Sensitivity List Bug

This repository demonstrates a subtle yet crucial error that can occur in VHDL code related to process sensitivity lists.  Improperly specifying the sensitivity list in a VHDL process can lead to unpredictable behavior and difficult-to-debug issues.  In this example, we'll explore a scenario where a process doesn't react to changes in signals as expected, causing the output to not reflect the actual input values.

## Bug Description:

The bug lies in the sensitivity list of the process in the `error_example` entity.  The sensitivity list only includes the clock (`clk`) and reset (`rst`) signals. However, the process also uses the `data_in` signal. Because `data_in` is not in the sensitivity list, the process doesn't update the `internal_data` signal when `data_in` changes asynchronously.  This can lead to stale data being assigned to `data_out`, and the output not reflecting the correct input values.

## Solution:

The solution involves correctly specifying the sensitivity list of the process.  The `data_in` signal must be explicitly included in the sensitivity list to ensure the process updates whenever `data_in` changes.  This will resolve the issue where the output does not reflect the most recent input values. 