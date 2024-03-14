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
{
    "function": {
        "type": {
            "const": null,
            "decorators": [],
            "width": null,
            "sign": null,
            "real_type": "zheng3"
        },
        "name": "zhu3"
    },
    "params": [
        {
            "type": {
                "const": null,
                "decorators": [],
                "width": null,
                "sign": null,
                "real_type": "zheng3"
            },
            "name": "argc"
        },
        {
            "type": {
                "const": null,
                "decorators": [
                    "Reference",
                    "Reference"
                ],
                "width": null,
                "sign": null,
                "real_type": "zi4"
            },
            "name": "argv"
        }
    ],
    "codes": [
        {
            "If": {
                "ruo4": {
                    "conds": [
                        {
                            "BracketExpr": {
                                "lhs": {
                                    "BracketExpr": {
                                        "lhs": {
                                            "NumberLiteral": {
                                                "Digit": {
                                                    "number": 1
                                                }
                                            }
                                        },
                                        "op": "Gt",
                                        "rhs": {
                                            "NumberLiteral": {
                                                "Digit": {
                                                    "number": 0
                                                }
                                            }
                                        }
                                    }
                                },
                                "op": "Or",
                                "rhs": {
                                    "lhs": {
                                        "BracketExpr": {
                                            "lhs": {
                                                "NumberLiteral": {
                                                    "Digit": {
                                                        "number": 2
                                                    }
                                                }
                                            },
                                            "op": "Lt",
                                            "rhs": {
                                                "NumberLiteral": {
                                                    "Digit": {
                                                        "number": 3
                                                    }
                                                }
                                            }
                                        }
                                    },
                                    "op": "And",
                                    "rhs": {
                                        "UnaryExpr": {
                                            "operator": "Not",
                                            "expr": {
                                                "Variable": "fo3"
                                            }
                                        }
                                    }
                                }
                            }
                        }
                    ],
                    "block": [
                        {
                            "Comment": {}
                        }
                    ]
                },
                "chains": [
                    {
                        "block": []
                    }
                ]
            }
        }
    ]
}
```

the code

```pin1yin1
zheng3 zhu3 can1 zheng3 argc fen1 zhi3 zhi3 zi4 argv jie2 
han2
jie2
```

**may** be parsed to a ast follow

```json
{
    "function": {
        "type": {
            "const": null,
            "decorators": [],
            "width": null,
            "sign": null,
            "real_type": "zheng3"
        },
        "name": "zhu3"
    },
    "params": [
        {
            "type": {
                "const": null,
                "decorators": [],
                "width": null,
                "sign": null,
                "real_type": "zheng3"
            },
            "name": "argc"
        },
        {
            "type": {
                "const": null,
                "decorators": [
                    "Reference",
                    "Reference"
                ],
                "width": null,
                "sign": null,
                "real_type": "zi4"
            },
            "name": "argv"
        }
    ],
    "codes": []
}
```

## Backend

there are still no backend now,too
