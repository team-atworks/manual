# 시스템 분석
### 1. Source 분석
- 시스템의 Source를 분석하여 (Controller, Dto) API 구조를 정리합니다. 
- 타사의 경우 적용하려는 시스템 담당자에게 API 구조에 대한 정보를 받아서 등록하는 방식으로 수행되는데, 일반적인 프로젝트에서 API 구조 문서에 대한 존재여부와 정확성을 검증할 수 없습니다. 가장 정확한 것은 Source이기 때문에 분석을 통해 API 구조를 정리합니다. 
- [Path variable](https://github.com/kimtaehan11/atworks-hello/blob/main/business/pathVariable.md), Fixed length 방식의 경우 Log 분석만으로 API 를 호출할 수 없습니다. 
- 형상관리 시스템인 git, svn 등과 연계하여 특정일마다 변경된 API에 대한 업데이트를 자동으로 수행합니다. (시스템과 협의 필요)


변경전 Source code
```
// Contoller
@PostMapping("")
public ResponseEntity<Long> saveServer(@Valid @RequestBody ServerSaveRequest requestDto){
    Long serverId = serverService.save(requestDto);
    serverMapper.reload();
    ...
}

// Dto
public class ServerSaveRequest {

    @NotNull
    private String serverName;

    @NotNull
    private ServerType serverType;

    // HTTP
    private String url;
    private DataFormat dataFormat;
    private LoginProcess loginProcess;

    // TCP
    private IpPort ipPort;
    
    // DATABASE
    private DBMS dbms;
    private ConnectionInfo connectionInfo;
}
```

변경후 API 구조 

![image](https://user-images.githubusercontent.com/85854794/221094702-653555e1-0d2a-45b2-92ba-b0ea2930707a.png)



### 2. Log 수집
- 실제 시스템 Log 데이터를 수집하여 test case 를 생성
- request (필수), response (옵션) 의 정보가 있는 Log 데이터를 시스템 담당자가 제공해야 합니다. 


실제 전환된 Log 데이터
```
20210901115932.205<!--CS--><!--CS-->{serviceId}<!--CS-->zizin80<!--CS-->210.60.13.105<!--CS-->
.....
    pageNm="{pageName}" serviceID="{serviceId}" w2xPath="{pageId}">
    <CommCode>
        <vector result="2">
            <data vectorkey="0">
                <comm>
                    <code value="{code1}"/>
                </comm>
            </data>
            <data vectorkey="1">
                <comm>
                    <code value="{code2}"/>
                </comm>
            </data>
        </vector>
    </CommCode>
    <RuleList>
        <vector result="0"/>
    </RuleList>
</MDATA>
```

server 데이터 구조에 따른 테스트 수행 화면
![image](https://user-images.githubusercontent.com/85854794/221109998-574fb450-dcf2-4f4f-a0f8-50ea4baeccdb.png)













