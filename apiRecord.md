# API 호출 이력 녹화
---
- selenium 을 활용하여 화면에서 발생한 API 호출 이력을 녹화하여 test case로 등록하는 방법을 제공합니다. 
- IE 계열의 microsoft에서 제공하는 브라우져에서는 사용할 수 없습니다. (권한문제)
- 별도의 window/mac client 프로그램 설치 필요



![image](https://user-images.githubusercontent.com/85854794/221328322-0cb3571e-57c9-4a40-9da1-a4d909f8b34c.png)


### 테스트 화면 S생명 
> 인터넷 급여실손의료비보장보험 다이렉트 보험료 계산  
> 생년월일과 성별입력으로 보험료가 구해지는 간단한 화면  
> [바로가기](https://direct.samsunglife.com/medical.eds#uiTabProduct2)

![image](https://user-images.githubusercontent.com/52950400/230808453-39d8ea33-9cd7-4e4d-8bb0-51456fcbbc46.png)


> Request
```
{
    "proType": "9",
    "prcdId": 1119,
    "prcd": "Y064501ANNNAE02",
    "prdtVcd": "002",
    "insCd": "LY0645004",
    "repCd": "LQ_NX75GL5L0000_G03",
    "prdtnm": "인터넷 급여 실손의료비보장보험(2301)(갱신형,무배당)",
    "contName": "고객님",
    * "contBirth": "19850312", // 생년월일
    * "contGender": "1",  // 성별
    ....   
}
```
> Response
```
{
    "contAmt": "0",
    "contAmtSp": "0",
    * "premium": "7270", // 월 보험료
    "success": true,
    ...
}
```
