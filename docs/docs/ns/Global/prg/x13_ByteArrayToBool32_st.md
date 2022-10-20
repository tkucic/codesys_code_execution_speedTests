# Codesys Code Execution Speed Tests | [MAIN] | [NAMESPACES] | [METRICS] | [BACK]  

## Documentation for Program x13_ByteArrayToBool32  

```pascal
//  
INTERFACE
    VAR CONSTANT
        cNrRuns : subrangeSigned := 5;
        cRepeatCalcTimes : UDINT := 1000000; (*1 Million times*)
    END_VAR
    VAR 
        vRunsCompleted : USINT := 0;
        vStartTime : LTIME;
        vTotalTime : LTIME;
        vStart : BOOL := TRUE;
        vTest1 : dtSpeedTest;
        vTest2 : dtSpeedTest;
        vTest3 : dtSpeedTest;
        vTest4 : dtSpeedTest;
        i : UDINT;
        j : INT;
        vBoolArr1 : ARRAY[1..32] OF BOOL; (*Test vars*)
        vBoolArr2 : ARRAY[1..32] OF BOOL;
        vBoolArr3 : ARRAY[1..32] OF BOOL;
        vBoolArr4 : ARRAY[1..32] OF BOOL;
        vBytes : ARRAY[1..4] OF USINT := ['16#FF', '16#85', '16#0', '16#AB'];
    END_VAR
END_INTERFACE
PROGRAM x13_ByteArrayToBool32:
    IF vStart THEN
    	vStartTime := LTIME();
    	vStart := FALSE;
    END_IF
    IF vRunsCompleted > cNrRuns THEN
    	IF vTotalTime = LTIME#0S THEN
    		vTotalTime := LTIME() - vStartTime;
    	END_IF
    	//Measurement done on 1 milion unpacks
    	//Time to upack 4 bytes to bool array, function
    	vTest1.AverageExecTime := calcAvg(vTest1.Results);
    	//Time to upack 4 bytes to bool array, flat
    	vTest2.AverageExecTime := calcAvg(vTest2.Results);
    	//Time to upack 4 bytes to bool array, bitmask function
    	vTest3.AverageExecTime := calcAvg(vTest3.Results);
    	//Time to upack 4 bytes to bool array, bitmask
    	vTest4.AverageExecTime := calcAvg(vTest4.Results);
    	RETURN;
    END_IF

    //------------CALCULATION A -------------------
    vTest1.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vBoolArr1 := UnpackBytesToBool32(vBytes);
    END_FOR
    vTest1.ExecTime := LTIME() - vTest1.OldTime;

    //------------CALCULATION B -------------------
    vTest2.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vBoolArr2[1] := vBytes[1].0;
    	vBoolArr2[2] := vBytes[1].1;
    	vBoolArr2[3] := vBytes[1].2;
    	vBoolArr2[4] := vBytes[1].3;
    	vBoolArr2[5] := vBytes[1].4;
    	vBoolArr2[6] := vBytes[1].5;
    	vBoolArr2[7] := vBytes[1].6;
    	vBoolArr2[8] := vBytes[1].7;
    	
    	vBoolArr2[9] :=  vBytes[2].0;
    	vBoolArr2[10] := vBytes[2].1;
    	vBoolArr2[11] := vBytes[2].2;
    	vBoolArr2[12] := vBytes[2].3;
    	vBoolArr2[13] := vBytes[2].4;
    	vBoolArr2[14] := vBytes[2].5;
    	vBoolArr2[15] := vBytes[2].6;
    	vBoolArr2[16] := vBytes[2].7;
    	
    	vBoolArr2[17] := vBytes[3].0;
    	vBoolArr2[18] := vBytes[3].1;
    	vBoolArr2[19] := vBytes[3].2;
    	vBoolArr2[20] := vBytes[3].3;
    	vBoolArr2[21] := vBytes[3].4;
    	vBoolArr2[22] := vBytes[3].5;
    	vBoolArr2[23] := vBytes[3].6;
    	vBoolArr2[24] := vBytes[3].7;
    	
    	vBoolArr2[25] := vBytes[4].0;
    	vBoolArr2[26] := vBytes[4].1;
    	vBoolArr2[27] := vBytes[4].2;
    	vBoolArr2[28] := vBytes[4].3;
    	vBoolArr2[29] := vBytes[4].4;
    	vBoolArr2[30] := vBytes[4].5;
    	vBoolArr2[31] := vBytes[4].6;
    	vBoolArr2[32] := vBytes[4].7;

    END_FOR
    vTest2.ExecTime := LTIME() - vTest2.OldTime;

    //------------CALCULATION C -------------------
    vTest3.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vBoolArr3 := UnpackBytesToBool32_2(vBytes);
    END_FOR
    vTest3.ExecTime := LTIME() - vTest3.OldTime;

    vTest4.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vBoolArr4[1] := (vBytes[1] AND 1) <> 0;
    	vBoolArr4[2] := (vBytes[1] AND 2) <> 0;
    	vBoolArr4[3] := (vBytes[1] AND 4) <> 0;
    	vBoolArr4[4] := (vBytes[1] AND 8) <> 0;
    	vBoolArr4[5] := (vBytes[1] AND 16) <> 0;
    	vBoolArr4[6] := (vBytes[1] AND 32) <> 0;
    	vBoolArr4[7] := (vBytes[1] AND 64) <> 0;
    	vBoolArr4[8] := (vBytes[1] AND 128) <> 0;
    	
    	vBoolArr4[9] := (vBytes[2] AND  1) <> 0;
    	vBoolArr4[10] := (vBytes[2] AND 2) <> 0;
    	vBoolArr4[11] := (vBytes[2] AND 4) <> 0;
    	vBoolArr4[12] := (vBytes[2] AND 8) <> 0;
    	vBoolArr4[13] := (vBytes[2] AND 16) <> 0;
    	vBoolArr4[14] := (vBytes[2] AND 32) <> 0;
    	vBoolArr4[15] := (vBytes[2] AND 64) <> 0;
    	vBoolArr4[16] := (vBytes[2] AND 128) <> 0;
    	
    	vBoolArr4[17] := (vBytes[3] AND 1) <> 0;
    	vBoolArr4[18] := (vBytes[3] AND 2) <> 0;
    	vBoolArr4[19] := (vBytes[3] AND 4) <> 0;
    	vBoolArr4[20] := (vBytes[3] AND 8) <> 0;
    	vBoolArr4[21] := (vBytes[3] AND 16) <> 0;
    	vBoolArr4[22] := (vBytes[3] AND 32) <> 0;
    	vBoolArr4[23] := (vBytes[3] AND 64) <> 0;
    	vBoolArr4[24] := (vBytes[3] AND 128) <> 0;
    	
    	vBoolArr4[25] := (vBytes[4] AND 1) <> 0;
    	vBoolArr4[26] := (vBytes[4] AND 2) <> 0;
    	vBoolArr4[27] := (vBytes[4] AND 4) <> 0;
    	vBoolArr4[28] := (vBytes[4] AND 8) <> 0;
    	vBoolArr4[29] := (vBytes[4] AND 16) <> 0;
    	vBoolArr4[30] := (vBytes[4] AND 32) <> 0;
    	vBoolArr4[31] := (vBytes[4] AND 64) <> 0;
    	vBoolArr4[32] := (vBytes[4] AND 128) <> 0;

    END_FOR
    vTest4.ExecTime := LTIME() - vTest4.OldTime;

    //------------CATCH RESULTS---------------------
    vTest1.Results[vRunsCompleted] := vTest1.ExecTime;
    vTest2.Results[vRunsCompleted] := vTest2.ExecTime;
    vTest3.Results[vRunsCompleted] := vTest3.ExecTime;
    vTest4.Results[vRunsCompleted] := vTest4.ExecTime;

    vRunsCompleted := vRunsCompleted + 1;

END_PROGRAM
```

## Metrics  

- VAR : 2
- VAR : 15

| Actions | Methods | Lines of code | Lines of comments | Lines in total | Maintainable size |
| ------- | ------- | ------------- | ----------------- | -------------- | ----------------- |
| 0 | 0 | 101 |9 |124 | 118 |

---
Autogenerated with [ia_tools](https://github.com/tkucic/ia_tools)  

[MAIN]: ../../../../index_st.md
[NAMESPACES]: ../../nsList_st.md
[METRICS]: ../../../metrics_st.md
[BACK]: ../nsMain_st.md
