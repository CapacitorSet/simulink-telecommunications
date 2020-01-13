To import parameters from Matlab, simply assign the variable from the Matlab prompt (eg. `mySNR = 2`), then use that in Simulink instead of a numeric value (eg. insert `mySNR` rather than `2` in the parameters for the AWGN block).

Use a "To Workspace" block to export signals to the workspace, where it will be available under `out.<name>`.

In this case we wanted to plot the BER against the SNR. The code is quite simple:

```matlab
x = -5:0.2:15 % The SNR range to be plotted
clear y
i = 0
for mySNR = x
  i = i + 1
  tmp = sim('exercise','ReturnWorkspaceOutputs', 'on')
  y(i) = tmp.BER(501)
end
```
