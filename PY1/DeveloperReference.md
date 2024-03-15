# Pin1Yin1 complier

## Status

in working...

there are still no useable compiler now

## Frontend

Frontend should parse the source code and output a `ast` in json format.

the ast standard follow the rust code [there](https://github.com/pin1yin1yu3yan2/Pin1Yin1-rustc) (this means that there are still no standard now...)

for example, this code

``` pin1yin1
zheng3 zhu3 can1 zheng3 argc fen1 zhi3 zhi3 zi4 argv jie2 
han2
    ruo4 can1 can1 1 da4 0 jie2 huo4 can1 2 xiao3 3 jie2 yu3 fei1 fo3 jie2
    han2 
        shi4 if ((1>0)||(2<3)&&!false){} else{} jie2
    jie2 ze2 han2 

    jie2
jie2
```

**may** be parsed to a ast follow

``` json
[
    {
        "FuncionDefinition": {
            "type": {
                "type": "zheng3"
            },
            "name": "zhu3",
            "args": [
                {
                    "type": {
                        "type": "zheng3"
                    },
                    "name": "argc"
                },
                {
                    "type": {
                        "decorators": [
                            "Pointer",
                            "Pointer"
                        ],
                        "type": "zi4"
                    },
                    "name": "argv"
                }
            ],
            "body": [
                {
                    "If": {
                        "branches": [
                            {
                                "conds": [
                                    {
                                        "Binary": [
                                            "Or",
                                            {
                                                "Binary": [
                                                    "Gt",
                                                    {
                                                        "Digit": 1
                                                    },
                                                    {
                                                        "Digit": 0
                                                    }
                                                ]
                                            },
                                            {
                                                "Binary": [
                                                    "And",
                                                    {
                                                        "Binary": [
                                                            "Lt",
                                                            {
                                                                "Digit": 2
                                                            },
                                                            {
                                                                "Digit": 3
                                                            }
                                                        ]
                                                    },
                                                    {
                                                        "Unary": [
                                                            "Not",
                                                            {
                                                                "Variable": "fo3"
                                                            }
                                                        ]
                                                    }
                                                ]
                                            }
                                        ]
                                    }
                                ],
                                "body": []
                            }
                        ],
                        "else": []
                    }
                }
            ]
        }
    }
]
```

the code

```pin1yin1
zheng3 zhu3 can1 zheng3 argc fen1 zhi3 zhi3 zi4 argv jie2 
han2
jie2
```

**may** be parsed to a ast follow

```json
[
    {
        "FuncionDefinition": {
            "type": {
                "type": "zheng3"
            },
            "name": "zhu3",
            "args": [
                {
                    "type": {
                        "type": "zheng3"
                    },
                    "name": "argc"
                },
                {
                    "type": {
                        "decorators": [
                            "Pointer",
                            "Pointer"
                        ],
                        "type": "zi4"
                    },
                    "name": "argv"
                }
            ],
            "body": []
        }
    }
]
```

the code

```pin1yin1
zheng3 zhu3 can1 zheng3 argc fen1 zhi3 zhi3 zi4 argv jie2
han2

    zheng3 a deng3 114 fen1
    shi4 int a = 114; jie2
    
    fu2 b deng3 114 fen1
    shi4 float b = 114.0; jie2
    
    xu1 c deng3 114 fen1
    shi4 This is not going to implement in py1. This word is know only a keeping keyword. jie2
    
    zi4 d deng3 wen2 _s fen1
    shi4 char d = ' '; jie2
    
    bu4 e deng3 fo3 yu3 zhen1 fen1
    shi4 bool e = false && true; jie2
    
    zu3 6 zheng3 aa deng3 han2 1 1 4 5 1 4 jie2 fen1
    shi4 int aa[6] = {1,1,4,5,14}; jie2
    
    zu3 zi4 dd deng3 chuan4 tiansuohaoer fen1
    shi4 char dd[] = "tiansuohaoer"; jie2
    
    a deng3 a jia1 a jian3 a cheng2 a chu2 a fen1
    shi4 a = a + a - a * a / a; jie2
    
    ruo4 can1 can1 1 da4 0 jie2 huo4 can1 2 xiao3 3 jie2 yu3 fei1 fo3 jie2
    han2 jie2
    ze2 han2 jie2
    shi4 if ((1>0)||(2<3)&&!false){} else{} jie2
    
    zheng3 i deng3 0 fen1
    chong2 can1 i xiao3 5 jie2
    han2 i deng3 i jia1 1 fen1 jie2
    shi4 int i = 0; while(i < 5){ i = i + 1;} jie2
    
    yin3 bian4 aaa deng3 a fen1
    shi4 auto& aaa = a; jie2
    
    fan3 0 fen1
    shi4 return 0; jie2
    
jie2
```
**may** be parsed to a ast follow

```json
[{"FuncionDefinition":{"type":{"type":"zheng3"},"name":"zhu3","args":[{"type":{"type":"zheng3"},"name":"argc"},{"type":{"decorators":["Pointer","Pointer"],"type":"zi4"},"name":"argv"}],"body":[{"VariableDefinition":{"type":{"type":"zheng3"},"name":"a","init":{"Digit":114}}},{"VariableDefinition":{"type":{"type":"fu2"},"name":"b","init":{"Digit":114}}},{"VariableDefinition":{"type":{"type":"xu1"},"name":"c","init":{"Digit":114}}},{"VariableDefinition":{"type":{"type":"zi4"},"name":"d","init":{"Char":" "}}},{"VariableDefinition":{"type":{"type":"bu4"},"name":"e","init":{"Binary":["And",{"Variable":"fo3"},{"Variable":"zhen1"}]}}},{"VariableDefinition":{"type":{"decorators":["6"],"type":"zheng3"},"name":"aa","init":{"Initialization":[{"Digit":1},{"Digit":1},{"Digit":4},{"Digit":5},{"Digit":1},{"Digit":4}]}}},{"VariableDefinition":{"type":{"decorators":["Array"],"type":"zi4"},"name":"dd","init":{"String":"tiansuohaoer"}}},{"VariableAssign":{"name":"a","assign":{"Binary":["Sub",{"Binary":["Add",{"Variable":"a"},{"Variable":"a"}]},{"Binary":["Div",{"Binary":["Mul",{"Variable":"a"},{"Variable":"a"}]},{"Variable":"a"}]}]}}},{"If":{"branches":[{"conds":[{"Binary":["Or",{"Binary":["Gt",{"Digit":1},{"Digit":0}]},{"Binary":["And",{"Binary":["Lt",{"Digit":2},{"Digit":3}]},{"Unary":["Not",{"Variable":"fo3"}]}]}]}],"body":[]}],"else":[]}},{"VariableDefinition":{"type":{"type":"zheng3"},"name":"i","init":{"Digit":0}}},{"While":{"conds":[{"Binary":["Lt",{"Variable":"i"},{"Digit":5}]}],"body":[{"VariableAssign":{"name":"i","assign":{"Binary":["Add",{"Variable":"i"},{"Digit":1}]}}}]}},{"VariableDefinition":{"type":{"decorators":["Reference"],"type":"bian4"},"name":"aaa","init":{"Variable":"a"}}},{"Return":{"val":{"Digit":0}}}]}}]
```

## Backend

there are still no backend now,too
