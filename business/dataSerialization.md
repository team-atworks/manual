# 데이터 직렬화
- C공제의 경우 데이터 구조가 XML->Json으로 변경되는 전환 프로젝트였습니다. 
- 프로젝트에서 표준을 정하지 못해 개발자 임의로 root node, parent node 이름을 변경하는 경우가 많았습니다. 그런 경우에도 결과를 비교하기 위해 데이터 직렬화 프로세스를 도입

### 데이터 직렬화 규칙
- Object 형태의 데이터 parent node의 이름은 비교대상에서 제외하고 string, number, boolean 원시 타입의 데이터만 key, value 기준으로 비교합니다. 
- key가 중복나는 경우 value를 리스트 형태로 저장하고 비교시에 내림차순으로 정렬하여 비교
- list의 경우 list_{index}_{key} 형태로 저장하여 비교

직렬화 전 데이터 
```
{
  "key1":"value1-1",
  "object":{
    "key1":"value1-2",
    "key2":"value2",
  },
  "list":[
    {
      "innerKey1":"innerValue1",
      "innerKey2":"innerValue2",
    },
    {
      "innerKey1":"innerValue3",
      "innerKey2":"innerValue4",
    },
  ]
}
```

직렬화 후 데이터
```
{
  "key1":["value1-1", "value1-2"],
  "key2":"value2",
  "list_0_innerKey1":"innerValue1",
  "list_0_innerKey2":"innerValue2",
  "list_1_innerKey1":"innerValue3",
  "list_1_innerKey2":"innerValue4",
}
```
