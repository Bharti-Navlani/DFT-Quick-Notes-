
## Area 

-> PD complainted about DFT logic increase was more ( we consider mostly ~3%)<br>
-> so after analysis noticed thats due to more memories in the design<br>
-> more memory so more number of interface logic inteserted by tessent ( memory interface = no of memories)<br>
-> & the logic inside that has pipeline logic inserted to & from memory<br>
-> Now since the memories were not at very high freq functionally so we removed the pipeline for those memories to reduce -> overall area overhead<br> 

## Wrapper 

### Shared wrapper 
-> no additional area for PD<br>
-> DFT can also use for TD test<br>
-> SI-> Q path will also be tested as functional freq as we don't constraint SE so both D-> Q & SI -> Q will be seen in STA<br>
-> DFT can't estimate coverage just by intest , they have to run Extest also at block level to get overrall coverage<br>

-> sometime the combo cone is very long until PI hits register so tool many not consider shared wrapper at that point 
(we define depth of combo logic during scan insertion based on that it adds shared wrapper )<br>

### Dedicated wrapper 
-> area overhead<br>
-> additional delay to mux inside dedicate wrapper<br>
-> High speed path cannot be tested<br>
-> D is looped back to Q for decidated wrapper so easy for HOLD timing closer<br>

