## Show details about the OS and the machine

Prerequisites: `inxi` is installed on the target machine.

This is analogous to `msinfo32`, `dxdiag`, or pressing `Ctrl+PauseBreak` in Windows.


### Display all system information (including hardware IDs)
(Requires elevation to read certain hardware serial numbers)

```shell
sudo inxi -Fx
```

### Display system information, with hardware IDs redacted  
```shell
inxi -Fxz
```
