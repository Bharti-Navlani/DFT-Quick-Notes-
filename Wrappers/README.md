# DFT-Quick-Notes-


## About Wrapper 

🗒️Wrapper Requirement in SoC Testing (Hierarchy Based Approach)

- In SoC , the design is divided into multiple cores or blocks 
- For testing purpose , the SoC is usually verified using a hierarchical test approach 
- In this approach , each block is tested independently before full chip testing 
- To test the block independently , the primary inputs and primary output of block must be fully controllable and observable
  This means : test patterns must be applied to the block input & output response must be captured and observed
- From a DFT perspective all PI and PO of the block should ideally be registered
  This means : input and output should directly connected to flip flop (functioanally already there then we are GOOD!! , but this not always !! )

🗒️Decidated Wrapper 
- When ports are not registered (input port when traced fwd hits to ff/register , same for o/p when traced backwards)
- In such cases , additional wrapper cells are inserted at block level
- When wrapper cells are explicitly added because no funtional register exists , they are called - "DEDICATED WRAPPER"
- Flops are added dedicated for DFT purpose , dedicated for DFT use 

🗒️Shared Wrapper 
- When ports are registered (input port when traced fwd doest not hit directly to ff/register , same for o/p when traced backwards)
- These functional flops can be coverted into scan flip flop
- Using SCAN IN (SI) , SCAN ENABLE (SE) , SCAN OUT (SO) signals we can control and observe these signals during test
- When ports are not registered, Instead it may first pass through combination logic 
- In this case DFT tool traces the signal forward from the port 
- The trace continues until it  reached the first sequential element/ ff/ register 
- This flop is functionally present this can be used as wrapper cell
- Since flop is functionally present in the design , no new wrapper is added 
- The same flop servers both functionally logic and wrapper 
- so this is "SHARED WRAPPER"

📌In Summary<br>
  if DFT adds wrapper then "DEDICATE WRAPPER" if DFT used flops functionally present in the design as wrapper cell then "SHARED"<br>
  Ports registered - then flop is already present then "SHARED"<br>
  Ports not registered - then either add "DEDICATE WRAPPER" or after some combo logic use the flop functional present as wrapper then it is "SHARED"<br>


<img width="377" height="236" alt="Screenshot 2026-03-15 101246" src="https://github.com/user-attachments/assets/b003f9de-5bf3-4c14-9459-8bbc8c146489" />


<img width="1619" height="589" alt="wrapper" src="https://github.com/user-attachments/assets/6a27d02f-4502-42ed-8457-32124a9d2f0c" />

Intest Mode :
Input wrappers are in shift mode only 
Core flops will toggle in shift and capture
Output wrapper also will also be in shift and capture 

In case of tessent edt
wrp edt -> wrapper flops are targetted 
int edt -> wrapper flops + internal flops are targeted 
same edt clk is used for both intest & extest 

How DOES IT TAKES CARE OF POWER OF CORE LOGIC WHILE TARGET OF EXTEST ?

clock will still toggle to internal core but internal logic be just shifting Zeros 
so toggling power is reduced 

Wrapper Chain Length can be mode in case of SHARED WRAPPER 

<img width="328" height="196" alt="wrapper_2" src="https://github.com/user-attachments/assets/d05b0e8c-e514-4d9f-a3c3-7b71b1cfe2db" />

