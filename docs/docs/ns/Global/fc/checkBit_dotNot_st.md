# Codesys Code Execution Speed Tests | [MAIN] | [NAMESPACES] | [METRICS] | [BACK]  

## Documentation for Function checkBit_dotNot (BOOL)  

```pascal
//  
INTERFACE
    VAR_INPUT 
        bits : UINT;
        bitToCheck : USINT;
    END_VAR
END_INTERFACE
FUNCTION checkBit_dotNot :
    CASE bitToCheck OF
    	0: checkBit_dotNot := bits.0;
    	1: checkBit_dotNot := bits.1;
    	2: checkBit_dotNot := bits.2;
    	3: checkBit_dotNot := bits.3;
    	4: checkBit_dotNot := bits.4;
    	5: checkBit_dotNot := bits.5;
    	6: checkBit_dotNot := bits.6;
    	7: checkBit_dotNot := bits.7;
    	8: checkBit_dotNot := bits.8;
    	9: checkBit_dotNot := bits.9;
    	10: checkBit_dotNot := bits.10;
    	11: checkBit_dotNot := bits.11;
    	12: checkBit_dotNot := bits.12;
    	13: checkBit_dotNot := bits.13;
    	14: checkBit_dotNot := bits.14;
    	15: checkBit_dotNot := bits.15;
    END_CASE
END_FUNCTION
```

## Metrics  

- VAR_INPUT : 2

| Lines of code | Lines of comments | Lines in total | Maintainable size |
| ------------- | ----------------- | -------------- | ----------------- |
| 18 |0 |18 | 22 |

---
Autogenerated with [ia_tools](https://github.com/tkucic/ia_tools)  

[MAIN]: ../../../../index_st.md
[NAMESPACES]: ../../nsList_st.md
[METRICS]: ../../../metrics_st.md
[BACK]: ../nsMain_st.md