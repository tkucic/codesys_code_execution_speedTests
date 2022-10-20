# Codesys Code Execution Speed Tests | [MAIN] | [NAMESPACES] | [METRICS] | [BACK]  

## Documentation for Program x09_CaseVsIfElsif  

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
        vTest5 : dtSpeedTest;
        vTest6 : dtSpeedTest;
        i : UDINT;
        vFirstIndex : INT := 15; (*Test vars*)
        vMiddleIndex : INT := 50;
        vLastIndex : INT := 99;
        vResultFirst : INT; (*Should be 0*)
        vResultMiddle : INT; (*Should be 50*)
        vResultLast : INT; (*Should be 99*)
    END_VAR
END_INTERFACE
PROGRAM x09_CaseVsIfElsif:
    IF vStart THEN
    	vStartTime := LTIME();
    	vStart := FALSE;
    END_IF
    IF vRunsCompleted > cNrRuns THEN
    	IF vTotalTime = LTIME#0S THEN
    		vTotalTime := LTIME() - vStartTime;
    	END_IF
    	vTest1.AverageExecTime := calcAvg(vTest1.Results); //Time to run first branch of IF ELSIF 1 Million times
    	vTest2.AverageExecTime := calcAvg(vTest2.Results); //Time to run middle branch of IF ELSIF 1 Million times
    	vTest3.AverageExecTime := calcAvg(vTest3.Results); //Time to run last branch of IF ELSIF 1 Million times
    	vTest4.AverageExecTime := calcAvg(vTest4.Results); //Time to run first branch of CASE 1 Million times
    	vTest5.AverageExecTime := calcAvg(vTest5.Results); //Time to run middle branch of CASE 1 Million times
    	vTest6.AverageExecTime := calcAvg(vTest6.Results); //Time to run last branch of CASE 1 Million times
    	
    	RETURN;
    END_IF

    //------------CALCULATION A -------------------
    vTest1.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResultFirst := returnIndexIfElsif(vFirstIndex);
    END_FOR
    vTest1.ExecTime := LTIME() - vTest1.OldTime;

    //------------CALCULATION B -------------------
    vTest2.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResultMiddle := returnIndexIfElsif(vMiddleIndex);
    END_FOR
    vTest2.ExecTime := LTIME() - vTest2.OldTime;

    //------------CALCULATION C -------------------
    vTest3.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResultLast := returnIndexIfElsif(vLastIndex);
    END_FOR
    vTest3.ExecTime := LTIME() - vTest3.OldTime;

    //------------CALCULATION D -------------------
    vTest4.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResultFirst := returnIndexCase(vFirstIndex);
    END_FOR
    vTest4.ExecTime := LTIME() - vTest4.OldTime;

    //------------CALCULATION E -------------------
    vTest5.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResultMiddle := returnIndexCase(vMiddleIndex);
    END_FOR
    vTest5.ExecTime := LTIME() - vTest5.OldTime;

    //------------CALCULATION F -------------------
    vTest6.OldTime := LTIME();
    FOR i:= 0 TO cRepeatCalcTimes DO
    	vResultLast := returnIndexCase(vLastIndex);
    END_FOR
    vTest6.ExecTime := LTIME() - vTest6.OldTime;

    //------------CATCH RESULTS---------------------
    vTest1.Results[vRunsCompleted] := vTest1.ExecTime;
    vTest2.Results[vRunsCompleted] := vTest2.ExecTime;
    vTest3.Results[vRunsCompleted] := vTest3.ExecTime;
    vTest4.Results[vRunsCompleted] := vTest4.ExecTime;
    vTest5.Results[vRunsCompleted] := vTest5.ExecTime;
    vTest6.Results[vRunsCompleted] := vTest6.ExecTime;

    vRunsCompleted := vRunsCompleted + 1;

END_PROGRAM
METHOD returnIndexIfElsif:
    INTERFACE
        VAR_INPUT 
            searchValue : INT;
        END_VAR
    END_INTERFACE
    IF searchValue = 0 THEN
            returnIndexIfElsif:=0;
            RETURN;

    ELSIF searchValue = 1 THEN
            returnIndexIfElsif:= 1;
            RETURN;

    ELSIF searchValue = 2 THEN
            returnIndexIfElsif:= 2;
            RETURN;

    ELSIF searchValue = 3 THEN
            returnIndexIfElsif:= 3;
            RETURN;

    ELSIF searchValue = 4 THEN
            returnIndexIfElsif:= 4;
            RETURN;

    ELSIF searchValue = 5 THEN
            returnIndexIfElsif:= 5;
            RETURN;

    ELSIF searchValue = 6 THEN
            returnIndexIfElsif:= 6;
            RETURN;

    ELSIF searchValue = 7 THEN
            returnIndexIfElsif:= 7;
            RETURN;

    ELSIF searchValue = 8 THEN
            returnIndexIfElsif:= 8;
            RETURN;

    ELSIF searchValue = 9 THEN
            returnIndexIfElsif:= 9;
            RETURN;

    ELSIF searchValue = 10 THEN
            returnIndexIfElsif:= 10;
            RETURN;

    ELSIF searchValue = 11 THEN
            returnIndexIfElsif:= 11;
            RETURN;

    ELSIF searchValue = 12 THEN
            returnIndexIfElsif:= 12;
            RETURN;

    ELSIF searchValue = 13 THEN
            returnIndexIfElsif:= 13;
            RETURN;

    ELSIF searchValue = 14 THEN
            returnIndexIfElsif:= 14;
            RETURN;

    ELSIF searchValue = 15 THEN
            returnIndexIfElsif:= 15;
            RETURN;

    ELSIF searchValue = 16 THEN
            returnIndexIfElsif:= 16;
            RETURN;

    ELSIF searchValue = 17 THEN
            returnIndexIfElsif:= 17;
            RETURN;

    ELSIF searchValue = 18 THEN
            returnIndexIfElsif:= 18;
            RETURN;

    ELSIF searchValue = 19 THEN
            returnIndexIfElsif:= 19;
            RETURN;

    ELSIF searchValue = 20 THEN
            returnIndexIfElsif:= 20;
            RETURN;

    ELSIF searchValue = 21 THEN
            returnIndexIfElsif:= 21;
            RETURN;

    ELSIF searchValue = 22 THEN
            returnIndexIfElsif:= 22;
            RETURN;

    ELSIF searchValue = 23 THEN
            returnIndexIfElsif:= 23;
            RETURN;

    ELSIF searchValue = 24 THEN
            returnIndexIfElsif:= 24;
            RETURN;

    ELSIF searchValue = 25 THEN
            returnIndexIfElsif:= 25;
            RETURN;

    ELSIF searchValue = 26 THEN
            returnIndexIfElsif:= 26;
            RETURN;

    ELSIF searchValue = 27 THEN
            returnIndexIfElsif:= 27;
            RETURN;

    ELSIF searchValue = 28 THEN
            returnIndexIfElsif:= 28;
            RETURN;

    ELSIF searchValue = 29 THEN
            returnIndexIfElsif:= 29;
            RETURN;

    ELSIF searchValue = 30 THEN
            returnIndexIfElsif:= 30;
            RETURN;

    ELSIF searchValue = 31 THEN
            returnIndexIfElsif:= 31;
            RETURN;

    ELSIF searchValue = 32 THEN
            returnIndexIfElsif:= 32;
            RETURN;

    ELSIF searchValue = 33 THEN
            returnIndexIfElsif:= 33;
            RETURN;

    ELSIF searchValue = 34 THEN
            returnIndexIfElsif:= 34;
            RETURN;

    ELSIF searchValue = 35 THEN
            returnIndexIfElsif:= 35;
            RETURN;

    ELSIF searchValue = 36 THEN
            returnIndexIfElsif:= 36;
            RETURN;

    ELSIF searchValue = 37 THEN
            returnIndexIfElsif:= 37;
            RETURN;

    ELSIF searchValue = 38 THEN
            returnIndexIfElsif:= 38;
            RETURN;

    ELSIF searchValue = 39 THEN
            returnIndexIfElsif:= 39;
            RETURN;

    ELSIF searchValue = 40 THEN
            returnIndexIfElsif:= 40;
            RETURN;

    ELSIF searchValue = 41 THEN
            returnIndexIfElsif:= 41;
            RETURN;

    ELSIF searchValue = 42 THEN
            returnIndexIfElsif:= 42;
            RETURN;

    ELSIF searchValue = 43 THEN
            returnIndexIfElsif:= 43;
            RETURN;

    ELSIF searchValue = 44 THEN
            returnIndexIfElsif:= 44;
            RETURN;

    ELSIF searchValue = 45 THEN
            returnIndexIfElsif:= 45;
            RETURN;

    ELSIF searchValue = 46 THEN
            returnIndexIfElsif:= 46;
            RETURN;

    ELSIF searchValue = 47 THEN
            returnIndexIfElsif:= 47;
            RETURN;

    ELSIF searchValue = 48 THEN
            returnIndexIfElsif:= 48;
            RETURN;

    ELSIF searchValue = 49 THEN
            returnIndexIfElsif:= 49;
            RETURN;

    ELSIF searchValue = 50 THEN
            returnIndexIfElsif:= 50;
            RETURN;

    ELSIF searchValue = 51 THEN
            returnIndexIfElsif:= 51;
            RETURN;

    ELSIF searchValue = 52 THEN
            returnIndexIfElsif:= 52;
            RETURN;

    ELSIF searchValue = 53 THEN
            returnIndexIfElsif:= 53;
            RETURN;

    ELSIF searchValue = 54 THEN
            returnIndexIfElsif:= 54;
            RETURN;

    ELSIF searchValue = 55 THEN
            returnIndexIfElsif:= 55;
            RETURN;

    ELSIF searchValue = 56 THEN
            returnIndexIfElsif:= 56;
            RETURN;

    ELSIF searchValue = 57 THEN
            returnIndexIfElsif:= 57;
            RETURN;

    ELSIF searchValue = 58 THEN
            returnIndexIfElsif:= 58;
            RETURN;

    ELSIF searchValue = 59 THEN
            returnIndexIfElsif:= 59;
            RETURN;

    ELSIF searchValue = 60 THEN
            returnIndexIfElsif:= 60;
            RETURN;

    ELSIF searchValue = 61 THEN
            returnIndexIfElsif:= 61;
            RETURN;

    ELSIF searchValue = 62 THEN
            returnIndexIfElsif:= 62;
            RETURN;

    ELSIF searchValue = 63 THEN
            returnIndexIfElsif:= 63;
            RETURN;

    ELSIF searchValue = 64 THEN
            returnIndexIfElsif:= 64;
            RETURN;

    ELSIF searchValue = 65 THEN
            returnIndexIfElsif:= 65;
            RETURN;

    ELSIF searchValue = 66 THEN
            returnIndexIfElsif:= 66;
            RETURN;

    ELSIF searchValue = 67 THEN
            returnIndexIfElsif:= 67;
            RETURN;

    ELSIF searchValue = 68 THEN
            returnIndexIfElsif:= 68;
            RETURN;

    ELSIF searchValue = 69 THEN
            returnIndexIfElsif:= 69;
            RETURN;

    ELSIF searchValue = 70 THEN
            returnIndexIfElsif:= 70;
            RETURN;

    ELSIF searchValue = 71 THEN
            returnIndexIfElsif:= 71;
            RETURN;

    ELSIF searchValue = 72 THEN
            returnIndexIfElsif:= 72;
            RETURN;

    ELSIF searchValue = 73 THEN
            returnIndexIfElsif:= 73;
            RETURN;

    ELSIF searchValue = 74 THEN
            returnIndexIfElsif:= 74;
            RETURN;

    ELSIF searchValue = 75 THEN
            returnIndexIfElsif:= 75;
            RETURN;

    ELSIF searchValue = 76 THEN
            returnIndexIfElsif:= 76;
            RETURN;

    ELSIF searchValue = 77 THEN
            returnIndexIfElsif:= 77;
            RETURN;

    ELSIF searchValue = 78 THEN
            returnIndexIfElsif:= 78;
            RETURN;

    ELSIF searchValue = 79 THEN
            returnIndexIfElsif:= 79;
            RETURN;

    ELSIF searchValue = 80 THEN
            returnIndexIfElsif:= 80;
            RETURN;

    ELSIF searchValue = 81 THEN
            returnIndexIfElsif:= 81;
            RETURN;

    ELSIF searchValue = 82 THEN
            returnIndexIfElsif:= 82;
            RETURN;

    ELSIF searchValue = 83 THEN
            returnIndexIfElsif:= 83;
            RETURN;

    ELSIF searchValue = 84 THEN
            returnIndexIfElsif:= 84;
            RETURN;

    ELSIF searchValue = 85 THEN
            returnIndexIfElsif:= 85;
            RETURN;

    ELSIF searchValue = 86 THEN
            returnIndexIfElsif:= 86;
            RETURN;

    ELSIF searchValue = 87 THEN
            returnIndexIfElsif:= 87;
            RETURN;

    ELSIF searchValue = 88 THEN
            returnIndexIfElsif:= 88;
            RETURN;

    ELSIF searchValue = 89 THEN
            returnIndexIfElsif:= 89;
            RETURN;

    ELSIF searchValue = 90 THEN
            returnIndexIfElsif:= 90;
            RETURN;

    ELSIF searchValue = 91 THEN
            returnIndexIfElsif:= 91;
            RETURN;

    ELSIF searchValue = 92 THEN
            returnIndexIfElsif:= 92;
            RETURN;

    ELSIF searchValue = 93 THEN
            returnIndexIfElsif:= 93;
            RETURN;

    ELSIF searchValue = 94 THEN
            returnIndexIfElsif:= 94;
            RETURN;

    ELSIF searchValue = 95 THEN
            returnIndexIfElsif:= 95;
            RETURN;

    ELSIF searchValue = 96 THEN
            returnIndexIfElsif:= 96;
            RETURN;

    ELSIF searchValue = 97 THEN
            returnIndexIfElsif:= 97;
            RETURN;

    ELSIF searchValue = 98 THEN
            returnIndexIfElsif:= 98;
            RETURN;

    ELSIF searchValue = 99 THEN
            returnIndexIfElsif:= 99;
            RETURN;

    END_IF
END_METHOD
METHOD returnIndexCase:
    INTERFACE
        VAR_INPUT 
            searchValue : INT;
        END_VAR
    END_INTERFACE
    CASE searchValue OF

            0: returnIndexCase := 0;
            RETURN;

            1: returnIndexCase := 1;
            RETURN;

            2: returnIndexCase := 2;
            RETURN;

            3: returnIndexCase := 3;
            RETURN;

            4: returnIndexCase := 4;
            RETURN;

            5: returnIndexCase := 5;
            RETURN;

            6: returnIndexCase := 6;
            RETURN;

            7: returnIndexCase := 7;
            RETURN;

            8: returnIndexCase := 8;
            RETURN;

            9: returnIndexCase := 9;
            RETURN;

            10: returnIndexCase := 10;
            RETURN;

            11: returnIndexCase := 11;
            RETURN;

            12: returnIndexCase := 12;
            RETURN;

            13: returnIndexCase := 13;
            RETURN;

            14: returnIndexCase := 14;
            RETURN;

            15: returnIndexCase := 15;
            RETURN;

            16: returnIndexCase := 16;
            RETURN;

            17: returnIndexCase := 17;
            RETURN;

            18: returnIndexCase := 18;
            RETURN;

            19: returnIndexCase := 19;
            RETURN;

            20: returnIndexCase := 20;
            RETURN;

            21: returnIndexCase := 21;
            RETURN;

            22: returnIndexCase := 22;
            RETURN;

            23: returnIndexCase := 23;
            RETURN;

            24: returnIndexCase := 24;
            RETURN;

            25: returnIndexCase := 25;
            RETURN;

            26: returnIndexCase := 26;
            RETURN;

            27: returnIndexCase := 27;
            RETURN;

            28: returnIndexCase := 28;
            RETURN;

            29: returnIndexCase := 29;
            RETURN;

            30: returnIndexCase := 30;
            RETURN;

            31: returnIndexCase := 31;
            RETURN;

            32: returnIndexCase := 32;
            RETURN;

            33: returnIndexCase := 33;
            RETURN;

            34: returnIndexCase := 34;
            RETURN;

            35: returnIndexCase := 35;
            RETURN;

            36: returnIndexCase := 36;
            RETURN;

            37: returnIndexCase := 37;
            RETURN;

            38: returnIndexCase := 38;
            RETURN;

            39: returnIndexCase := 39;
            RETURN;

            40: returnIndexCase := 40;
            RETURN;

            41: returnIndexCase := 41;
            RETURN;

            42: returnIndexCase := 42;
            RETURN;

            43: returnIndexCase := 43;
            RETURN;

            44: returnIndexCase := 44;
            RETURN;

            45: returnIndexCase := 45;
            RETURN;

            46: returnIndexCase := 46;
            RETURN;

            47: returnIndexCase := 47;
            RETURN;

            48: returnIndexCase := 48;
            RETURN;

            49: returnIndexCase := 49;
            RETURN;

            50: returnIndexCase := 50;
            RETURN;

            51: returnIndexCase := 51;
            RETURN;

            52: returnIndexCase := 52;
            RETURN;

            53: returnIndexCase := 53;
            RETURN;

            54: returnIndexCase := 54;
            RETURN;

            55: returnIndexCase := 55;
            RETURN;

            56: returnIndexCase := 56;
            RETURN;

            57: returnIndexCase := 57;
            RETURN;

            58: returnIndexCase := 58;
            RETURN;

            59: returnIndexCase := 59;
            RETURN;

            60: returnIndexCase := 60;
            RETURN;

            61: returnIndexCase := 61;
            RETURN;

            62: returnIndexCase := 62;
            RETURN;

            63: returnIndexCase := 63;
            RETURN;

            64: returnIndexCase := 64;
            RETURN;

            65: returnIndexCase := 65;
            RETURN;

            66: returnIndexCase := 66;
            RETURN;

            67: returnIndexCase := 67;
            RETURN;

            68: returnIndexCase := 68;
            RETURN;

            69: returnIndexCase := 69;
            RETURN;

            70: returnIndexCase := 70;
            RETURN;

            71: returnIndexCase := 71;
            RETURN;

            72: returnIndexCase := 72;
            RETURN;

            73: returnIndexCase := 73;
            RETURN;

            74: returnIndexCase := 74;
            RETURN;

            75: returnIndexCase := 75;
            RETURN;

            76: returnIndexCase := 76;
            RETURN;

            77: returnIndexCase := 77;
            RETURN;

            78: returnIndexCase := 78;
            RETURN;

            79: returnIndexCase := 79;
            RETURN;

            80: returnIndexCase := 80;
            RETURN;

            81: returnIndexCase := 81;
            RETURN;

            82: returnIndexCase := 82;
            RETURN;

            83: returnIndexCase := 83;
            RETURN;

            84: returnIndexCase := 84;
            RETURN;

            85: returnIndexCase := 85;
            RETURN;

            86: returnIndexCase := 86;
            RETURN;

            87: returnIndexCase := 87;
            RETURN;

            88: returnIndexCase := 88;
            RETURN;

            89: returnIndexCase := 89;
            RETURN;

            90: returnIndexCase := 90;
            RETURN;

            91: returnIndexCase := 91;
            RETURN;

            92: returnIndexCase := 92;
            RETURN;

            93: returnIndexCase := 93;
            RETURN;

            94: returnIndexCase := 94;
            RETURN;

            95: returnIndexCase := 95;
            RETURN;

            96: returnIndexCase := 96;
            RETURN;

            97: returnIndexCase := 97;
            RETURN;

            98: returnIndexCase := 98;
            RETURN;

            99: returnIndexCase := 99;
            RETURN;

    END_CASE
END_METHOD
```

## Metrics  

- VAR : 2
- VAR : 17

| Actions | Methods | Lines of code | Lines of comments | Lines in total | Maintainable size |
| ------- | ------- | ------------- | ----------------- | -------------- | ----------------- |
| 0 | 2 | 556 |7 |773 | 575 |

---
Autogenerated with [ia_tools](https://github.com/tkucic/ia_tools)  

[MAIN]: ../../../../index_st.md
[NAMESPACES]: ../../nsList_st.md
[METRICS]: ../../../metrics_st.md
[BACK]: ../nsMain_st.md
