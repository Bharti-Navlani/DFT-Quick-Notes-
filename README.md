## DFT-Quick-Notes-


# About Wrapper 

>> Wrapper Requirement in SoC Testing (Hierarchy Based Approach)

- In SoC , the design is divided into multiple cores or blocks 
- For testing purpose , the SoC is usually verified using a hierarchical test approach 
- In this approach , each block is tested independently before full chip testing 

- To test the block independently , the primary inputs and primary output of block must be fully controllable and observable
  This means : test patterns must be applied to the block input & output response must be captured and observed

- From a DFT perspective all PI and PO of the block should ideally be registered
  This means : input and output should directly connected to flip flop (functioanally already there then we are GOOD!! , but this not always !! )

Case 1
- When ports are registered :
  These functional flops can be coverted into scan flip flop
  Using SCAN IN (SI) , SCAN ENABLE (SE) , SCAN OUT (SO) signals we can control and observe these signals during test

- When functinals flops are already present
  These flops are simply converted into scan flops

Case 2 
- When ports are not registered
  In such cases , additional wrapper cells are inserted at block level
  



