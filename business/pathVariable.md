# Path variable
- Path Variable이란 Query String과 같이 데이터를 넘기는 방법 중의 하나로 경로를 변수처럼 사용하는 것을 의미합니다. 
- 예시 : (GET) /api/v1/servers/{serverId} 

### aTworks Log 수집시 문제 
- /api/v1/servers/{serverId} 의 경우 실제 url 호출시에는 /api/v1/servers/11 URL에 reqeust data가 입력되서 구분을 할 수 없었습니다.
- path variable 때문에 /api/v1/servers/1, /api/v1/servers/2, /api/v1/servers/3 각각 신규 API로 인지되서 추가로 등록되는 문제 발생

### 해결방안 
- source 분석단계에서 urlPath와 urlPathPattern으로 구분하여 table에 저장 
- urlPath : /api/v1/servers/{serverId}
- urlPathPattern : /api/v1/servers/%
- log에서 path variable이 들어오는 경우 log에서 들어온 urlPath (/api/v1/servers/3)과 urlPathPattern과 역 like 검색을 통해 대상 API 구조를 추출함 

```
// query dsl 조건식 
Expressions.asString(urlPath).like(layout.urlInfo.urlPathPattern)

// 중복 URL 발생시 % 가 적은 수로 우선순위 정리함
layouts.stream()
.sorted(Comparator.comparing(s-> (int) s.getUrlInfo().getUrlPathPattern().chars()
        .filter(c->c=='%')
        .count()))
.findFirst();
```

- 이 방법도 완벽하지 않다고 생각해서 더 좋은 방법이 있을까 해서 테스트 케이스를 작성중에 Spring에서도 정상적으로 호출하지 않은 현상 발생 
- 아래의 경우 1번쨰 PatchMapping만 호출됨 
- 
```
@PatchMapping("{serverId}/{sample}")
...

@PatchMapping("{serverId}/sample")
... 
``` 
