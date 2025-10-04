# Codesys Code Execution Speed Tests | [MAIN] | [NAMESPACES] | [METRICS] | [BACK]  

## Documentation for Program x05_SysMemLib  

```pascal
//  
INTERFACE
    VAR CONSTANT
        cNrRuns : subrangeSigned := 5;
        cRepeatCalcTimes : UDINT := 1000000; (*1 Million times*)
        cEmptyStruct : dtTestStruct;
    END_VAR
    VAR_INPUT 
        vStart : BOOL := FALSE;
    END_VAR
    VAR 
        vDone : BOOL := FALSE;
        vRunsCompleted : USINT := 0;
        vStartTime : LTIME;
        vTotalTime : LTIME;
        vTest1 : dtSpeedTest;
        vTest2 : dtSpeedTest;
        vTest3 : dtSpeedTest;
        vTest4 : dtSpeedTest;
        vTest5 : dtSpeedTest;
        vTest6 : dtSpeedTest;
        i : UDINT;
        vResultStruct1 : dtTestStruct; (*Test variables*)
        vResultStruct2 : dtTestStruct;
        vResultStruct3 : dtTestStruct;
        vResultStruct4 : dtTestStruct;
        vResult5 : BOOL;
        vResult6 : BOOL;
    END_VAR
END_INTERFACE
PROGRAM x05_SysMemLib:
    (*Runs once on event's rising edge*)
    vDone 		:= FALSE;
    vStartTime 	:= LTIME();

    FOR vRunsCompleted:=0 TO cNrRuns DO
    	Measure();
    END_FOR

    vTotalTime := LTIME() - vStartTime;

    vTest1.Desc				:= 'Setting a struct with an empty struct, 1 milion times';
    vTest1.AverageExecTime 	:= calcAvg(vTest1.Results);
    vTest2.Desc				:= 'Setting a struct with SysMemSet, 1 milion times';
    vTest2.AverageExecTime 	:= calcAvg(vTest2.Results);
    vTest3.Desc				:= 'Copy a struct to another struct, 1 milion times';
    vTest3.AverageExecTime 	:= calcAvg(vTest3.Results);
    vTest4.Desc				:= 'Copy a struct to another struct with memset, 1 milion times';
    vTest4.AverageExecTime 	:= calcAvg(vTest4.Results);
    vTest5.Desc				:= 'Compare a struct to another struct, 1 milion times';
    vTest5.AverageExecTime 	:= calcAvg(vTest5.Results);
    vTest6.Desc				:= 'Compare a struct to another struct with memcmp, 1 milion times';
    vTest6.AverageExecTime 	:= calcAvg(vTest6.Results);
    vDone := TRUE;
    vStart:= FALSE;

END_PROGRAM
ACTION Measure:
    //------------RESET STRUCT WITH A EMPTY STRUCT -------------------
    vTest1.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResultStruct1 := cEmptyStruct;
    END_FOR
    vTest1.ExecTime := LTIME() - vTest1.OldTime;

    //------------RESET STRUCT WITH MEM SET -------------------
    vTest2.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	SysMemSet(ADR(vResultStruct2), 16#0 , SIZEOF(vResultStruct2));
    END_FOR
    vTest2.ExecTime := LTIME() - vTest2.OldTime;

    //------------COPY STRUCT TO ANOTHER STRUCT -------------------
    vTest3.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResultStruct3 := cEmptyStruct;
    END_FOR
    vTest3.ExecTime := LTIME() - vTest3.OldTime;

    //------------COPY STRUCT TO ANOTHER STRUCT MEMCPY -------------------
    vTest4.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	SysMemCpy(ADR(vResultStruct4), ADR(cEmptyStruct) , SIZEOF(cEmptyStruct));
    END_FOR
    vTest4.ExecTime := LTIME() - vTest4.OldTime;

    //------------COMPARE STRUCT TO ANOTHER STRUCT -------------------
    //NOTE: Codesys doesn't support complex struct comparing with = <>
    vTest5.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResult5 := vResultStruct3.dummy1 = cEmptyStruct.dummy1
    			AND vResultStruct3.dummy2[0] = cEmptyStruct.dummy2[0]
    			AND vResultStruct3.dummy2[1] = cEmptyStruct.dummy2[1]
    			AND vResultStruct3.dummy2[2] = cEmptyStruct.dummy2[2]
    			AND vResultStruct3.dummy2[3] = cEmptyStruct.dummy2[3]
    			AND vResultStruct3.dummy2[4] = cEmptyStruct.dummy2[4]
    			AND vResultStruct3.dummy2[5] = cEmptyStruct.dummy2[5]
    			AND vResultStruct3.dummy2[6] = cEmptyStruct.dummy2[6]
    			AND vResultStruct3.dummy2[7] = cEmptyStruct.dummy2[7]
    			AND vResultStruct3.dummy2[8] = cEmptyStruct.dummy2[8]
    			AND vResultStruct3.dummy2[9] = cEmptyStruct.dummy2[9]
    			AND vResultStruct3.dummy2[10] = cEmptyStruct.dummy2[10]
    			AND vResultStruct3.dummy2[11] = cEmptyStruct.dummy2[11]
    			AND vResultStruct3.dummy4 = cEmptyStruct.dummy4
    			AND vResultStruct3.dummy5 = cEmptyStruct.dummy5
    			AND vResultStruct3.dummy6 = cEmptyStruct.dummy6
    			AND vResultStruct3.Elem1 = cEmptyStruct.Elem1
    			AND vResultStruct3.Id = cEmptyStruct.Id
    			AND vResultStruct3.IdText = cEmptyStruct.IdText;
    END_FOR
    vTest5.ExecTime := LTIME() - vTest5.OldTime;

    //------------COMPARE STRUCT TO ANOTHER STRUCT MEMCMP -------------------
    vTest6.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResult6 := SysMemCmp(ADR(vResultStruct4), ADR(cEmptyStruct),SIZEOF(cEmptyStruct)) = 0;
    END_FOR
    vTest6.ExecTime := LTIME() - vTest6.OldTime;

    //------------CATCH RESULTS---------------------
    vTest1.Results[vRunsCompleted] := vTest1.ExecTime;
    vTest2.Results[vRunsCompleted] := vTest2.ExecTime;
    vTest3.Results[vRunsCompleted] := vTest3.ExecTime;
    vTest4.Results[vRunsCompleted] := vTest4.ExecTime;
    vTest5.Results[vRunsCompleted] := vTest5.ExecTime;
    vTest6.Results[vRunsCompleted] := vTest6.ExecTime;
END_ACTION
```

## Metrics  

- VAR : 3
- VAR_INPUT : 1
- VAR : 17

| Actions | Methods | Lines of code | Lines of comments | Lines in total | Maintainable size |
| ------- | ------- | ------------- | ----------------- | -------------- | ----------------- |
| 1 | 0 | 74 |9 |92 | 96 |

---
Autogenerated with [ia_tools](https://github.com/tkucic/ia_tools)  

[MAIN]: ../../../../index_st.md
[NAMESPACES]: ../../nsList_st.md
[METRICS]: ../../../metrics_st.md
[BACK]: ../nsMain_st.md
