# Codesys Code Execution Speed Tests | [MAIN] | [NAMESPACES] | [METRICS] | [BACK]  

## Documentation for Program x00_CalcMIPS_FLOPS  

```pascal
//  
INTERFACE
    VAR 
        vStart : BOOL;
        vDone : BOOL;
        vMIPS : REAL;
        vFLOPS : REAL;
        vkFLOPS : REAL;
        vMFLOPS : REAL;
        vGFLOPS : REAL;
    END_VAR
END_INTERFACE
PROGRAM x00_CalcMIPS_FLOPS:
    vDone := FALSE;
    (*Calculate MIPS and FLOPS of this machine
    	PS: These calcs are not 100% accurate but more to compare machine to machine*)
    (*
    	System spec:
    	- OS Name	Microsoft Windows 10 Home	
    	- Version	10.0.19044 Build 19044	
    	- OS Manufacturer	Microsoft Corporation	
    	- System Manufacturer	SAMSUNG ELECTRONICS CO., LTD.	
    	- System Model	3570R/370R/470R/450R/510R/4450RV	
    	- System Type	x64-based PC	
    	- Processor	Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz, 2501 Mhz, 2 Core(s), 4 Logical Processor(s)	
    	- Installed Physical Memory (RAM)	8,00 GB	
    	- Total Physical Memory	7,89 GB	
    	- Available Physical Memory	3,80 GB	
    	- Total Virtual Memory	9,75 GB	
    	- Available Virtual Memory	5,66 GB	
    	
    	MIPS 	-> 407
    	FLOPS 	-> 3.32e+08
    	kFLOPS 	-> 3.32e+05
    	MFLOPS 	-> 332
    	GFLOPS 	-> 0.332
    *)
    vMIPS 	:= calcMIPS();
    vFLOPS	:= calcFLOPS();
    vkFLOPS := vFLOPS / 1000.0;
    vMFLOPS := vFLOPS / 1000000.0;
    vGFLOPS := vFLOPS / (1000.0 * 1000000.0);

    vDone := TRUE;
END_PROGRAM
```

## Metrics  

- VAR : 7

| Actions | Methods | Lines of code | Lines of comments | Lines in total | Maintainable size |
| ------- | ------- | ------------- | ----------------- | -------------- | ----------------- |
| 0 | 0 | 7 |23 |31 | 14 |

---
Autogenerated with [ia_tools](https://github.com/tkucic/ia_tools)  

[MAIN]: ../../../../index_st.md
[NAMESPACES]: ../../nsList_st.md
[METRICS]: ../../../metrics_st.md
[BACK]: ../nsMain_st.md