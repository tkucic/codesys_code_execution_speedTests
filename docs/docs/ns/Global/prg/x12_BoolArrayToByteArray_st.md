# Codesys Code Execution Speed Tests | [MAIN] | [NAMESPACES] | [METRICS] | [BACK]  

## Documentation for Program x12_BoolArrayToByteArray  

```pascal
//  
INTERFACE
    VAR CONSTANT
        cNrRuns : subrangeSigned := 5;
        cRepeatCalcTimes : UDINT := 1000000; (*1 Million times*)
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
        vTest7 : dtSpeedTest;
        i : UDINT;
        j : INT;
        vBoolArr : ARRAY[1..32] OF BOOL; (*Test vars*)
        vBytes1 : ARRAY[1..4] OF USINT;
        vBytes2 : ARRAY[1..4] OF USINT;
        vBytes3 : ARRAY[1..4] OF USINT;
        vBytes4 : ARRAY[1..4] OF UINT;
        vBytes5 : ARRAY[1..4] OF UINT;
        vBytes6 : ARRAY[1..4] OF USINT;
        vBytes7 : ARRAY[1..4] OF USINT;
    END_VAR
END_INTERFACE
PROGRAM x12_BoolArrayToByteArray:
    (*Runs once on event's rising edge*)
    vDone 		:= FALSE;
    vStartTime 	:= LTIME();

    FOR vRunsCompleted:=0 TO cNrRuns DO
    	Measure();
    END_FOR

    vTotalTime := LTIME() - vStartTime;

    vTest1.Desc 			:= 'Time to pack bool array to 4 bytes, function, milion times';
    vTest1.AverageExecTime 	:= calcAvg(vTest1.Results);
    vTest2.Desc 			:= 'Time to pack bool array to 4 bytes, flat, milion times';
    vTest2.AverageExecTime 	:= calcAvg(vTest2.Results);
    vTest3.Desc 			:= 'Time TO pack bool array to 4 bytes, bitmask, milion times';
    vTest3.AverageExecTime 	:= calcAvg(vTest3.Results);
    vTest4.Desc 			:= 'Time to pack bool array to 4 bytes, bitmask function, milion times';
    vTest4.AverageExecTime 	:= calcAvg(vTest4.Results);
    vTest5.Desc 			:= 'Time TO pack bool array to 4 bytes, bitmask function in a loop, milion times';
    vTest5.AverageExecTime 	:= calcAvg(vTest5.Results);
    vTest6.Desc 			:= 'Time to pack bool array to 4 bytes, clear + bitmask, milion times';
    vTest6.AverageExecTime 	:= calcAvg(vTest6.Results);
    vTest7.Desc 			:= 'Time TO pack bool array to 4 bytes, clear + bitmask, function, milion times';
    vTest7.AverageExecTime 	:= calcAvg(vTest7.Results);
    	
    vDone := TRUE;
    vStart:= FALSE;

END_PROGRAM
ACTION Measure:
    //------------CALCULATION A -------------------
    vTest1.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vBytes1 := BOOLARR_TO_BYTES(vBoolArr);
    END_FOR
    vTest1.ExecTime := LTIME() - vTest1.OldTime;

    //------------CALCULATION B -------------------
    vTest2.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vBytes2[1].0 := vBoolArr[1];
    	vBytes2[1].1 := vBoolArr[2];
    	vBytes2[1].2 := vBoolArr[3];
    	vBytes2[1].3 := vBoolArr[4];
    	vBytes2[1].4 := vBoolArr[5];
    	vBytes2[1].5 := vBoolArr[6];
    	vBytes2[1].6 := vBoolArr[7];
    	vBytes2[1].7 := vBoolArr[8];
    	
    	vBytes2[2].0 := vBoolArr[9];
    	vBytes2[2].1 := vBoolArr[10];
    	vBytes2[2].2 := vBoolArr[11];
    	vBytes2[2].3 := vBoolArr[12];
    	vBytes2[2].4 := vBoolArr[13];
    	vBytes2[2].5 := vBoolArr[14];
    	vBytes2[2].6 := vBoolArr[15];
    	vBytes2[2].7 := vBoolArr[16];
    	
    	vBytes2[3].0 := vBoolArr[17];
    	vBytes2[3].1 := vBoolArr[18];
    	vBytes2[3].2 := vBoolArr[19];
    	vBytes2[3].3 := vBoolArr[20];
    	vBytes2[3].4 := vBoolArr[21];
    	vBytes2[3].5 := vBoolArr[22];
    	vBytes2[3].6 := vBoolArr[23];
    	vBytes2[3].7 := vBoolArr[24];
    	
    	vBytes2[4].0 := vBoolArr[25];
    	vBytes2[4].1 := vBoolArr[26];
    	vBytes2[4].2 := vBoolArr[27];
    	vBytes2[4].3 := vBoolArr[28];
    	vBytes2[4].4 := vBoolArr[29];
    	vBytes2[4].5 := vBoolArr[30];
    	vBytes2[4].6 := vBoolArr[31];
    	vBytes2[4].7 := vBoolArr[32];
    END_FOR
    vTest2.ExecTime := LTIME() - vTest2.OldTime;

    //------------CALCULATION C -------------------
    vTest3.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	FOR j:=1 TO 4 DO
    		vBytes3[j].0 := vBoolArr[1 + ((j-1) * 8)]; //1,9, 17, 25
    		vBytes3[j].1 := vBoolArr[2 + ((j-1) * 8)];
    		vBytes3[j].2 := vBoolArr[3 + ((j-1) * 8)];
    		vBytes3[j].3 := vBoolArr[4 + ((j-1) * 8)];
    		vBytes3[j].4 := vBoolArr[5 + ((j-1) * 8)];
    		vBytes3[j].5 := vBoolArr[6 + ((j-1) * 8)]; //6, 14, 22, 30
    		vBytes3[j].6 := vBoolArr[7 + ((j-1) * 8)]; //7, 15, 23, 31
    		vBytes3[j].7 := vBoolArr[8 + ((j-1) * 8)]; //8, 16, 24, 32
    	END_FOR
    END_FOR
    vTest3.ExecTime := LTIME() - vTest3.OldTime;

    vTest4.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	setBitToValue_bitmask(vBytes4[1], 1, vBoolArr[1]);
    	setBitToValue_bitmask(vBytes4[1], 2 ,vBoolArr[2]);
    	setBitToValue_bitmask(vBytes4[1], 3,vBoolArr[3]);
    	setBitToValue_bitmask(vBytes4[1], 4,vBoolArr[4]);
    	setBitToValue_bitmask(vBytes4[1], 5,vBoolArr[5]);
    	setBitToValue_bitmask(vBytes4[1], 6,vBoolArr[6]);
    	setBitToValue_bitmask(vBytes4[1], 7,vBoolArr[7]);
    	setBitToValue_bitmask(vBytes4[1], 8,vBoolArr[8]);
    	
    	setBitToValue_bitmask(vBytes4[2], 1,vBoolArr[9]);
    	setBitToValue_bitmask(vBytes4[2], 2,vBoolArr[10]);
    	setBitToValue_bitmask(vBytes4[2], 3,vBoolArr[11]);
    	setBitToValue_bitmask(vBytes4[2], 4,vBoolArr[12]);
    	setBitToValue_bitmask(vBytes4[2], 5,vBoolArr[13]);
    	setBitToValue_bitmask(vBytes4[2], 6,vBoolArr[14]);
    	setBitToValue_bitmask(vBytes4[2], 7,vBoolArr[15]);
    	setBitToValue_bitmask(vBytes4[2], 8,vBoolArr[16]);
    	
    	setBitToValue_bitmask(vBytes4[3], 1,vBoolArr[17]);
    	setBitToValue_bitmask(vBytes4[3], 2,vBoolArr[18]);
    	setBitToValue_bitmask(vBytes4[3], 3,vBoolArr[19]);
    	setBitToValue_bitmask(vBytes4[3], 4,vBoolArr[20]);
    	setBitToValue_bitmask(vBytes4[3], 5,vBoolArr[21]);
    	setBitToValue_bitmask(vBytes4[3], 6,vBoolArr[22]);
    	setBitToValue_bitmask(vBytes4[3], 7,vBoolArr[23]);
    	setBitToValue_bitmask(vBytes4[3], 8,vBoolArr[24]);
    	
    	setBitToValue_bitmask(vBytes4[4], 1,vBoolArr[25]);
    	setBitToValue_bitmask(vBytes4[4], 2,vBoolArr[26]);
    	setBitToValue_bitmask(vBytes4[4], 3,vBoolArr[27]);
    	setBitToValue_bitmask(vBytes4[4], 4,vBoolArr[28]);
    	setBitToValue_bitmask(vBytes4[4], 5,vBoolArr[29]);
    	setBitToValue_bitmask(vBytes4[4], 6,vBoolArr[30]);
    	setBitToValue_bitmask(vBytes4[4], 7,vBoolArr[31]);
    	setBitToValue_bitmask(vBytes4[4], 8,vBoolArr[32]);
    END_FOR
    vTest4.ExecTime := LTIME() - vTest4.OldTime;

    vTest5.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
        FOR j:=1 TO 4 DO
            setBitToValue_bitmask(vBytes5[j], 1, vBoolArr[1 + ((j-1) * 8)]);
            setBitToValue_bitmask(vBytes5[j], 2, vBoolArr[2 + ((j-1) * 8)]);
            setBitToValue_bitmask(vBytes5[j], 3, vBoolArr[3 + ((j-1) * 8)]);
            setBitToValue_bitmask(vBytes5[j], 4, vBoolArr[4 + ((j-1) * 8)]);
            setBitToValue_bitmask(vBytes5[j], 5, vBoolArr[5 + ((j-1) * 8)]);
            setBitToValue_bitmask(vBytes5[j], 6, vBoolArr[6 + ((j-1) * 8)]);
            setBitToValue_bitmask(vBytes5[j], 7, vBoolArr[7 + ((j-1) * 8)]);
            setBitToValue_bitmask(vBytes5[j], 8, vBoolArr[8 + ((j-1) * 8)]);
        END_FOR
    END_FOR
    vTest5.ExecTime := LTIME() - vTest5.OldTime;


    vTest6.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
        vBytes6[1] := 0;
        vBytes6[2] := 0;
        vBytes6[3] := 0;
        vBytes6[4] := 0;

    	vBytes6[1] := vBytes6[1] OR SHL(BOOL_TO_USINT(vBoolArr[1]),0);
    	vBytes6[1] := vBytes6[1] OR SHL(BOOL_TO_USINT(vBoolArr[2]),1);
    	vBytes6[1] := vBytes6[1] OR SHL(BOOL_TO_USINT(vBoolArr[3]),2);
    	vBytes6[1] := vBytes6[1] OR SHL(BOOL_TO_USINT(vBoolArr[4]),3);
    	vBytes6[1] := vBytes6[1] OR SHL(BOOL_TO_USINT(vBoolArr[5]),4);
    	vBytes6[1] := vBytes6[1] OR SHL(BOOL_TO_USINT(vBoolArr[6]),5);
    	vBytes6[1] := vBytes6[1] OR SHL(BOOL_TO_USINT(vBoolArr[7]),6);
    	vBytes6[1] := vBytes6[1] OR SHL(BOOL_TO_USINT(vBoolArr[8]),7);
    	
    	vBytes6[2] := vBytes6[2] OR SHL(BOOL_TO_USINT(vBoolArr[9]) ,0);
    	vBytes6[2] := vBytes6[2] OR SHL(BOOL_TO_USINT(vBoolArr[10]),1);
    	vBytes6[2] := vBytes6[2] OR SHL(BOOL_TO_USINT(vBoolArr[11]),2);
    	vBytes6[2] := vBytes6[2] OR SHL(BOOL_TO_USINT(vBoolArr[12]),3);
    	vBytes6[2] := vBytes6[2] OR SHL(BOOL_TO_USINT(vBoolArr[13]),4);
    	vBytes6[2] := vBytes6[2] OR SHL(BOOL_TO_USINT(vBoolArr[14]),5);
    	vBytes6[2] := vBytes6[2] OR SHL(BOOL_TO_USINT(vBoolArr[15]),6);
    	vBytes6[2] := vBytes6[2] OR SHL(BOOL_TO_USINT(vBoolArr[16]),7);
    	
    	vBytes6[3] := vBytes6[3] OR SHL(BOOL_TO_USINT(vBoolArr[17]),0);
    	vBytes6[3] := vBytes6[3] OR SHL(BOOL_TO_USINT(vBoolArr[18]),1);
    	vBytes6[3] := vBytes6[3] OR SHL(BOOL_TO_USINT(vBoolArr[19]),2);
    	vBytes6[3] := vBytes6[3] OR SHL(BOOL_TO_USINT(vBoolArr[20]),3);
    	vBytes6[3] := vBytes6[3] OR SHL(BOOL_TO_USINT(vBoolArr[21]),4);
    	vBytes6[3] := vBytes6[3] OR SHL(BOOL_TO_USINT(vBoolArr[22]),5);
    	vBytes6[3] := vBytes6[3] OR SHL(BOOL_TO_USINT(vBoolArr[23]),6);
    	vBytes6[3] := vBytes6[3] OR SHL(BOOL_TO_USINT(vBoolArr[24]),7);
    	
    	vBytes6[4] := vBytes6[4] OR SHL(BOOL_TO_USINT(vBoolArr[25]),0);
    	vBytes6[4] := vBytes6[4] OR SHL(BOOL_TO_USINT(vBoolArr[26]),1);
    	vBytes6[4] := vBytes6[4] OR SHL(BOOL_TO_USINT(vBoolArr[27]),2);
    	vBytes6[4] := vBytes6[4] OR SHL(BOOL_TO_USINT(vBoolArr[28]),3);
    	vBytes6[4] := vBytes6[4] OR SHL(BOOL_TO_USINT(vBoolArr[29]),4);
    	vBytes6[4] := vBytes6[4] OR SHL(BOOL_TO_USINT(vBoolArr[30]),5);
    	vBytes6[4] := vBytes6[4] OR SHL(BOOL_TO_USINT(vBoolArr[31]),6);
    	vBytes6[4] := vBytes6[4] OR SHL(BOOL_TO_USINT(vBoolArr[32]),7);
    END_FOR
    vTest6.ExecTime := LTIME() - vTest6.OldTime;

    vTest7.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vBytes7 := BOOLARR_TO_BYTES2(vBoolArr);
    END_FOR
    vTest7.ExecTime := LTIME() - vTest7.OldTime;

    //------------CATCH RESULTS---------------------
    vTest1.Results[vRunsCompleted] := vTest1.ExecTime;
    vTest2.Results[vRunsCompleted] := vTest2.ExecTime;
    vTest3.Results[vRunsCompleted] := vTest3.ExecTime;
    vTest4.Results[vRunsCompleted] := vTest4.ExecTime;
    vTest5.Results[vRunsCompleted] := vTest5.ExecTime;
    vTest6.Results[vRunsCompleted] := vTest6.ExecTime;
    vTest7.Results[vRunsCompleted] := vTest7.ExecTime;
END_ACTION
```

## Metrics  

- VAR : 2
- VAR_INPUT : 1
- VAR : 21

| Actions | Methods | Lines of code | Lines of comments | Lines in total | Maintainable size |
| ------- | ------- | ------------- | ----------------- | -------------- | ----------------- |
| 1 | 0 | 179 |5 |206 | 204 |

---
Autogenerated with [ia_tools](https://github.com/tkucic/ia_tools)  

[MAIN]: ../../../../index_st.md
[NAMESPACES]: ../../nsList_st.md
[METRICS]: ../../../metrics_st.md
[BACK]: ../nsMain_st.md
