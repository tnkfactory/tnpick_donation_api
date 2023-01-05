# 기부 캠페인 조회
## Request
Method : GET/POST

```
https://www.tnpick.com/sho/api/v1/donation/campaign/{campaign_id}/?check_cd={CHECK_CD}
```

| 매크로명  | 설명   |
|--|--|
| {campaign_id} | 캠페인 ID : 0 을 입력하면 전체 기부 캠페인이 표시된다.  |
| {CHECK_CD}  |  md5(연동을 위한 api key +  campaign_id)  |

## Response
Type : JSON
```
     { res_cd : 0 (succes) or ...
       campaign_list : [
                   { campaign_name : text, campaign_id : int }, { ... }, ...
                ]
    }
```

| 컬럼명| 설명   | 
|--|--|
| res_cd | 응답코드  0 (성공),  아래 표 참조 |
| campaign_list | 기부 캠페인 LIST (JSONArray)  |


# 기부 순위 조회

## Request  

Method : GET/POST
```
https://www.tnpick.com/sho/api/v1/donation/rank/{campaign_id}/?check_cd={CHECK_CD}
```

| 매크로명  | 설명   |
|--|--|
| {campaign_id} | 캠페인 ID : 0 을 입력하면 전체 횟차(누적) 순위가 표시된다.  |
| {CHECK_CD}  | md5(연동을 위한 api key +  campaign_id)  |



## Response
type : JSON
```
    { res_cd : 0 (succes) or ...
    res_msg : ""  or "에러메시지",
    prd_name : 상품명(기부상품명),
    prd_id : 상품ID,
    rank_list : [
                   { idol_name : text, rank : int, donation_count : int}, { ... }, ...
                ]
    }
```  

| 컬럼명| 설명   |
|--|--|
| res_cd | 응답코드   0 (성공),  아래 표 참조 |
| res_msg | 응답 메시지  성공이면 "", 실패이면 메시지 출력 |
| campaign_name | 기부 캠페인  |
| campaign_id | 기부 캠페인 ID |
| rank_list | 순위 LIST (JSONArray) |



## rank_list

| 컬럼명| 설명   |
|--|--|
| idol_name | 아이돌 이름  |
| rank | 순위  |
| donation_count | 기부건수  |


# res_cd (응답코드)
| res_cd |	|
|--|--|
|0	|성공|
|2	|캠페인이 없습니다.|
|3	|파라미터 오류 입니다.|
|4	|체크코드가 잘못입력되었습니다.|
|9	|시스템 에러 입니다.(관리자에 문의)|

