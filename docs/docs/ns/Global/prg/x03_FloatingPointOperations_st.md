# Codesys Code Execution Speed Tests | [MAIN] | [NAMESPACES] | [METRICS] | [BACK]  

## Documentation for Program x03_FloatingPointOperations  

```pascal
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
        vTest5 : dtSpeedTest;
        vTest6 : dtSpeedTest;
        vTest7 : dtSpeedTest;
        vTest8 : dtSpeedTest;
        vTest9 : dtSpeedTest;
        i : UDINT;
        vInteger1 : INT := 1234; (*Test vars*)
        vInteger2 : INT := 4231;
        vReal1 : REAL := 1234.4231;
        vReal2 : REAL := 4231.1234;
        vInteger3 : DINT := 1234;
        vInteger4 : DINT := 4231;
        vResult1 : INT;
        vResult2 : REAL;
        vResult3 : DINT;
        vResult4 : INT;
        vResult5 : REAL;
        vResult6 : DINT;
        vResult7 : INT;
        vResult8 : REAL;
        vResult9 : DINT;
    END_VAR
END_INTERFACE
PROGRAM x03_FloatingPointOperations:
    IF vStart THEN
    	vStartTime := LTIME();
    	vStart := FALSE;
    END_IF
    IF vRunsCompleted > cNrRuns THEN
    	IF vTotalTime = LTIME#0S THEN
    		vTotalTime := LTIME() - vStartTime;
    	END_IF
    	vTest1.AverageExecTime := calcAvg(vTest1.Results); //Time to add two integers 1 milion times
    	vTest2.AverageExecTime := calcAvg(vTest2.Results); //Time to add two reals 1 milion times
    	vTest3.AverageExecTime := calcAvg(vTest3.Results); //Time to add two DINTs (32b INT) 1 milion times
    	vTest4.AverageExecTime := calcAvg(vTest4.Results); //Time to multiply two integers 1 milion times
    	vTest5.AverageExecTime := calcAvg(vTest5.Results); //Time to multiply two reals 1 milion times
    	vTest6.AverageExecTime := calcAvg(vTest6.Results); //Time to multiply two DINTs (32b INT) 1 milion times
    	vTest7.AverageExecTime := calcAvg(vTest7.Results); //Time to divide two integers 1 milion times
    	vTest8.AverageExecTime := calcAvg(vTest8.Results); //Time to divide two reals 1 milion times
    	vTest9.AverageExecTime := calcAvg(vTest9.Results); //Time to divide two DINTs (32b INT) 1 milion times
    		
    	RETURN;
    END_IF

    //------------CALCULATION A -------------------
    vTest1.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResult1 := vInteger1 + vInteger2;
    END_FOR
    vTest1.ExecTime := LTIME() - vTest1.OldTime;

    //------------CALCULATION B -------------------
    vTest2.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResult2 := vReal1 + vReal2;
    END_FOR
    vTest2.ExecTime := LTIME() - vTest2.OldTime;

    //------------CALCULATION C -------------------
    vTest3.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResult3 := vInteger3 + vInteger4;
    END_FOR
    vTest3.ExecTime := LTIME() - vTest3.OldTime;

    //------------CALCULATION D -------------------
    vTest4.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResult4 := vInteger1 * vInteger2;
    END_FOR
    vTest4.ExecTime := LTIME() - vTest4.OldTime;

    //------------CALCULATION E -------------------
    vTest5.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResult5 := vReal1 * vReal2;
    END_FOR
    vTest5.ExecTime := LTIME() - vTest5.OldTime;

    //------------CALCULATION F -------------------
    vTest6.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResult6 := vInteger3 * vInteger4;
    END_FOR
    vTest6.ExecTime := LTIME() - vTest6.OldTime;

    //------------CALCULATION G -------------------
    vTest7.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResult7 := vInteger1 / vInteger2;
    END_FOR
    vTest7.ExecTime := LTIME() - vTest7.OldTime;

    //------------CALCULATION H -------------------
    vTest8.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResult8 := vReal1 / vReal2;
    END_FOR
    vTest8.ExecTime := LTIME() - vTest8.OldTime;

    //------------CALCULATION I -------------------
    vTest9.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResult9 := vInteger3 / vInteger4;
    END_FOR
    vTest9.ExecTime := LTIME() - vTest9.OldTime;


    //------------CATCH RESULTS---------------------
    vTest1.Results[vRunsCompleted] := vTest1.ExecTime;
    vTest2.Results[vRunsCompleted] := vTest2.ExecTime;
    vTest3.Results[vRunsCompleted] := vTest3.ExecTime;
    vTest4.Results[vRunsCompleted] := vTest4.ExecTime;
    vTest5.Results[vRunsCompleted] := vTest5.ExecTime;
    vTest6.Results[vRunsCompleted] := vTest6.ExecTime;
    vTest7.Results[vRunsCompleted] := vTest7.ExecTime;
    vTest8.Results[vRunsCompleted] := vTest8.ExecTime;
    vTest9.Results[vRunsCompleted] := vTest9.ExecTime;
    vRunsCompleted := vRunsCompleted + 1;

END_PROGRAM
```

## Metrics  

- VAR : 2
- VAR : 29

| Actions | Methods | Lines of code | Maintainable size |
| ------- | ------- | ------------- | ----------------- |
| 0 | 0 | 96 | 127 |

---
Autogenerated with [ia_tools](https://github.com/tkucic/ia_tools)  

[MAIN]: ../../../../index_st.md
[NAMESPACES]: ../../nsList_st.md
[METRICS]: ../../../metrics_st.md
[BACK]: ../nsMain_st.md
