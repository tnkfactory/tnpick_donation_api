# 아이돌 리스트 조회 API

## Request  

Method : GET/POST

        https://www.tnpick.com/sho/api/v1/donation/rank/{PRD_ID}/?check_cd={CHECK_CD}


| 매크로명  | 설명   |
|--|--|
| {PRD_ID} | 상품 ID : 0 을 입력하면 전체 횟차(누적) 순위가 표시된다.  |
| {CHECK_CD}  | md5hex( PRD_ID + API_KEY), api_key는 별도 전달 |



## Response
type : JSON

    { res_cd : 1 (succes) or -1 (fail)
    res_msg : ""  or "에러메시지",
    prd_name : 상품명(기부상품명),
    prd_id : 상품ID,
    rank_list : [
                   { idol_name : text, rank : int, donation_count : int}, { ... }, ...
                ]
    }
  

| 컬럼명| 설명   | 설명 |
|--|--|--|
| res_cd | 응답코드  | 0 (성공),  아래 표 참조 |
| res_msg | 응답 메시지  | 성공이면 "", 실패이면 메시지 출력
| prd_name | 상품명  | 기부상품명 
| prd_id | 상품ID  | 기부상품 ID
| rank_list | 순위 LIST  | 순위 List (Array). JSONArray



## rank_list

| 컬럼명| 설명   |
|--|--|
| idol_name | 아이돌 이름  |
| rank | 순위  |
| donation_count | 기부건수  |

## res_cd (응답코드)
|Result Code|	Description|
|--|--|
|0	|Success|
|2	|No Campaigns|
|4	|Wrong API KEY|
|9	|System Error|

