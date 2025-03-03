# Crestron-Stewart-CVM
Crestron SIMPLE+ Module for controlling a Stewart CVM controller via IP or RS232

### Installation

 Copy the two files `Stewart CVM.usp` and `Stewart CVM.ush` to your configured `SIMPL User Modules folder` (see: Options -> Preferences -> Directories ). The default location is `C:\Users\Public\Documents\Crestron\SIMPL\Usrsplus`. 
 
 Alternativly you can run the `deploy.bat` script included in this repo.

### Give us some love
If you use this module in a Crestron project please give it a Star. :star:

## Usage


| Parameter | Description                                      |
| :---      | :--- |
| `user` | User name for CVM Login |
| `password` | Password for CVM Login |
| `memory[1..24]` |  Optionaly give each memory location a name for the `RecallByName` feature (See below) |

1. Configure the `user` and `password` parameters to match those configured in the CVM Web User interface.
2. Connect `RX$`, `TX$`, and `CVM_CONNECT_FB` to either a TCP/IP Client or a RS232 Client connected to the CVM control box. (In the case of RS232 set Connected=1)
3. Use the `Motor_1_xxx` and `Motor_2_xxx` digital joins to manualy control the left and right masking for fine adjustment and/or to set for the memory recall.
4. Use `RECALL_1` thru `RECALL_24` to recall the the corresponding memory locations directly. The associated `RECALL_X_FB` joins give feedback.
5. Optionaly set the `TargetName$` to the value of one of the `memory[x]` values and pulse the `RecallByName` join. If a direct match to `TargetName$` exists that memory slot will be recalled. If no dirrect match is found the memory slot with the special name of `SAFETY` will be used. If no slot is named `SAFETY` and no direct match is found then no memory slot will be recalled.
6. Use the `Store[1..24]` joins the store the current masking positions to the coresponding memory slot.
7. `ActiveName$` will have the name of the selected memory slot regardless if it is selected via `RECALL_x` or via `RecallByName`.

![SIMPL+ Layout][simplModule]

[simplModule]: images/simpl+layout.png