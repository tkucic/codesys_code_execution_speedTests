# Codesys Code Execution Speed Tests | [MAIN] | [NAMESPACES] | [METRICS] | [BACK]  

## Documentation for Function BOOLARR_TO_BYTES2 (ARRAY[1..4] OF USINT)  

```pascal
//  
INTERFACE
    VAR_IN_OUT 
        Data : ARRAY[1..32] OF BOOL;
    END_VAR
END_INTERFACE
FUNCTION BOOLARR_TO_BYTES2 :
    BOOLARR_TO_BYTES2[1] := BOOLARR_TO_BYTES2[1] OR SHL(BOOL_TO_USINT(Data[1]),0);
    BOOLARR_TO_BYTES2[1] := BOOLARR_TO_BYTES2[1] OR SHL(BOOL_TO_USINT(Data[2]),1);
    BOOLARR_TO_BYTES2[1] := BOOLARR_TO_BYTES2[1] OR SHL(BOOL_TO_USINT(Data[3]),2);
    BOOLARR_TO_BYTES2[1] := BOOLARR_TO_BYTES2[1] OR SHL(BOOL_TO_USINT(Data[4]),3);
    BOOLARR_TO_BYTES2[1] := BOOLARR_TO_BYTES2[1] OR SHL(BOOL_TO_USINT(Data[5]),4);
    BOOLARR_TO_BYTES2[1] := BOOLARR_TO_BYTES2[1] OR SHL(BOOL_TO_USINT(Data[6]),5);
    BOOLARR_TO_BYTES2[1] := BOOLARR_TO_BYTES2[1] OR SHL(BOOL_TO_USINT(Data[7]),6);
    BOOLARR_TO_BYTES2[1] := BOOLARR_TO_BYTES2[1] OR SHL(BOOL_TO_USINT(Data[8]),7);
    	
    BOOLARR_TO_BYTES2[2] := BOOLARR_TO_BYTES2[2] OR SHL(BOOL_TO_USINT(Data[9]) ,0);
    BOOLARR_TO_BYTES2[2] := BOOLARR_TO_BYTES2[2] OR SHL(BOOL_TO_USINT(Data[10]),1);
    BOOLARR_TO_BYTES2[2] := BOOLARR_TO_BYTES2[2] OR SHL(BOOL_TO_USINT(Data[11]),2);
    BOOLARR_TO_BYTES2[2] := BOOLARR_TO_BYTES2[2] OR SHL(BOOL_TO_USINT(Data[12]),3);
    BOOLARR_TO_BYTES2[2] := BOOLARR_TO_BYTES2[2] OR SHL(BOOL_TO_USINT(Data[13]),4);
    BOOLARR_TO_BYTES2[2] := BOOLARR_TO_BYTES2[2] OR SHL(BOOL_TO_USINT(Data[14]),5);
    BOOLARR_TO_BYTES2[2] := BOOLARR_TO_BYTES2[2] OR SHL(BOOL_TO_USINT(Data[15]),6);
    BOOLARR_TO_BYTES2[2] := BOOLARR_TO_BYTES2[2] OR SHL(BOOL_TO_USINT(Data[16]),7);
    	
    BOOLARR_TO_BYTES2[3] := BOOLARR_TO_BYTES2[3] OR SHL(BOOL_TO_USINT(Data[17]),0);
    BOOLARR_TO_BYTES2[3] := BOOLARR_TO_BYTES2[3] OR SHL(BOOL_TO_USINT(Data[18]),1);
    BOOLARR_TO_BYTES2[3] := BOOLARR_TO_BYTES2[3] OR SHL(BOOL_TO_USINT(Data[19]),2);
    BOOLARR_TO_BYTES2[3] := BOOLARR_TO_BYTES2[3] OR SHL(BOOL_TO_USINT(Data[20]),3);
    BOOLARR_TO_BYTES2[3] := BOOLARR_TO_BYTES2[3] OR SHL(BOOL_TO_USINT(Data[21]),4);
    BOOLARR_TO_BYTES2[3] := BOOLARR_TO_BYTES2[3] OR SHL(BOOL_TO_USINT(Data[22]),5);
    BOOLARR_TO_BYTES2[3] := BOOLARR_TO_BYTES2[3] OR SHL(BOOL_TO_USINT(Data[23]),6);
    BOOLARR_TO_BYTES2[3] := BOOLARR_TO_BYTES2[3] OR SHL(BOOL_TO_USINT(Data[24]),7);
    	
    BOOLARR_TO_BYTES2[4] := BOOLARR_TO_BYTES2[4] OR SHL(BOOL_TO_USINT(Data[25]),0);
    BOOLARR_TO_BYTES2[4] := BOOLARR_TO_BYTES2[4] OR SHL(BOOL_TO_USINT(Data[26]),1);
    BOOLARR_TO_BYTES2[4] := BOOLARR_TO_BYTES2[4] OR SHL(BOOL_TO_USINT(Data[27]),2);
    BOOLARR_TO_BYTES2[4] := BOOLARR_TO_BYTES2[4] OR SHL(BOOL_TO_USINT(Data[28]),3);
    BOOLARR_TO_BYTES2[4] := BOOLARR_TO_BYTES2[4] OR SHL(BOOL_TO_USINT(Data[29]),4);
    BOOLARR_TO_BYTES2[4] := BOOLARR_TO_BYTES2[4] OR SHL(BOOL_TO_USINT(Data[30]),5);
    BOOLARR_TO_BYTES2[4] := BOOLARR_TO_BYTES2[4] OR SHL(BOOL_TO_USINT(Data[31]),6);
    BOOLARR_TO_BYTES2[4] := BOOLARR_TO_BYTES2[4] OR SHL(BOOL_TO_USINT(Data[32]),7);
END_FUNCTION
```

## Metrics  

- VAR_IN_OUT : 1

| Lines of code | Lines of comments | Lines in total | Maintainable size |
| ------------- | ----------------- | -------------- | ----------------- |
| 32 |0 |35 | 34 |

---
Autogenerated with [ia_tools](https://github.com/tkucic/ia_tools)  

[MAIN]: ../../../../index_st.md
[NAMESPACES]: ../../nsList_st.md
[METRICS]: ../../../metrics_st.md
[BACK]: ../nsMain_st.md