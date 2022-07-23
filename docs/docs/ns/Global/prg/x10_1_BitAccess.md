# Codesys Code Execution Speed Tests | [MAIN] | [NAMESPACES] | [METRICS] | [BACK]  

## Documentation for Program x10_1_BitAccess  

## Interface  

| Direction | Name | Type | Attribute | Initial Value | Documentation |
| --------- | ---- | ---- | --------- | ------------- | ------------- |
| VAR | cNrRuns | subrangeSigned | constant | 5 |  |  
| VAR | cRepeatCalcTimes | UDINT | constant | 1000000 | 1 Million times |  
| VAR | vRunsCompleted | USINT |  | 0 |  |  
| VAR | vStartTime | LTIME |  |  |  |  
| VAR | vTotalTime | LTIME |  |  |  |  
| VAR | vStart | BOOL |  | TRUE |  |  
| VAR | vTest1 | dtSpeedTest |  |  |  |  
| VAR | vTest2 | dtSpeedTest |  |  |  |  
| VAR | vTest3 | dtSpeedTest |  |  |  |  
| VAR | i | UDINT |  |  |  |  
| VAR | vCodesysBits | dtBitStruct |  |  | Test vars |  
| VAR | vNormalInt | UINT |  | 16#5555 |  |  
| VAR | vResult1 | BOOL |  |  |  |  
| VAR | vResult2 | BOOL |  |  |  |  
| VAR | vResult3 | BOOL |  |  |  |  


## Metrics  

- VAR : 2
- VAR : 13

| Actions | Methods | Lines of code | Maintainable size |
| ------- | ------- | ------------- | ----------------- |
| 0 | 0 | 42 | 57 |

---
Autogenerated with [ia_tools](https://github.com/tkucic/ia_tools)  

[MAIN]: ../../../../index.md
[NAMESPACES]: ../../nsList.md
[METRICS]: ../../../metrics.md
[BACK]: ../nsMain.md