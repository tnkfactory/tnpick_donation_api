# 1. 기부 캠페인 조회
## Request

```
https://www.tnpick.com/sho/api/v1/donation/campaign/{campaign_id}/?check_cd={check_cd}
```

| 매크로명  | 설명   |
|--|--|
| {campaign_id} | 캠페인 ID : 0 을 입력하면 전체 기부 캠페인이 표시된다.  |
| {check_cd}  |  md5(연동을 위한 api_key +  campaign_id)  , api_key 는 별도 전달 |

## Response
Type : JSON
```
     { res_cd : 0 (succes) or ...
       campaign_list : [
                   { campaign_name : text, campaign_id : number }, { ... }, ...
                ]
    }
```

| 컬럼명| 설명   | 
|--|--|
| res_cd | 응답코드 (number)  0 :성공,  그 외 아래 표 참조 |
| campaign_list | 기부 캠페인 LIST (JSONArray)  |

## campaign_list

| 컬럼명| 설명   |
|--|--|
| campaign_id |  기부 캠페인 ID (number) |
| campaign_name | 기부 캠페인 명  |

## Example

```
https://www.tnpick.com/sho/api/v1/donation/campaigns/0/?check_cd=7f28000ff8d19a569e72323feecsd7sda9408ca
```

```
{   
   "res_cd":0,
   "campaign_list":[
      {
         "campaign_name":"[기부하기-23차] 라포레 오가닉 생리대 4종 SET",
         "campaign_id":103466
      },
      {
         "campaign_name":"[기부하기-22차] 라포레 오가닉 생리대 4종 SET",
         "campaign_id":103361
      },
      {
         "campaign_name":"[기부하기-21차] 라포레 오가닉 생리대 4종 SET",
         "campaign_id":103226
      }
   ]
  
}

```

# 2. 기부 순위 조회

## Request  

```
https://www.tnpick.com/sho/api/v1/donation/rank/{campaign_id}/?check_cd={check_cd}

```

| 매크로명  | 설명   |
|--|--|
| {campaign_id} | 캠페인 ID : 0 을 입력하면 전체 횟차(누적) 순위가 표시된다.  |
| {check_cd}  | md5(연동을 위한 api key +  campaign_id)  |



## Response
type : JSON
```
    { res_cd : 0 (succes) or ...
    res_msg : ""  or "에러메시지",
    campaign_name : 기부캠페인 명,
    campaign_id : 캠페인 ID,
    rank_list : [
                   { idol_name : text, rank : number, donation_count : number}, { ... }, ...
                ]
    }
    
```  

| 컬럼명| 설명   |
|--|--|
| res_cd | 응답코드 (number)   0  : 성공,  그 외 아래 표 참조 |
| res_msg | 응답 메시지  성공이면 "", 실패이면 메시지 출력 |
| campaign_name | 기부 캠페인 이름  |
| campaign_id | 기부 캠페인 ID (number) |
| rank_list | 순위 LIST (JSONArray) |



## rank_list

| 컬럼명 | 설명  |
|--|--|
| idol_name | 아이돌 이름  |
| rank | 순위  (number) |
| donation_count | 기부건수 (number)  |

## Example

```
https://www.tnpick.com/sho/api/v1/donation/rank/0/?check_cd=23sd7f28000ff8d19a569e7feecd7a9323408ca

```

```
{
   "res_msg":"",
   "campaign_name":"전체누적순위",
   "campaign_id":0,
   "res_cd":0,
   "rank_list":[
      {
         "idol_name":"박창근",
         "donation_count":857,
         "rank":1
      },
      {
         "idol_name":"이솔로몬",
         "donation_count":638,
         "rank":2
      },
      {
         "idol_name":"제이호",
         "donation_count":214,
         "rank":3
      },
      {
         "idol_name":"박장현",
         "donation_count":206,
         "rank":4
      },
      {
         "idol_name":"이승윤",
         "donation_count":150,
         "rank":5
      }
   ]
}

```


# 3. 응답코드 (res_cd)

| res_cd (number) | 설명 |
|--|--|
| 0	| 성공 |
| 2	| 캠페인이 없습니다. |
| 3	| 파라미터 오류 입니다. |
| 4	| 체크코드가 잘못입력되었습니다. |
| 9	| 시스템 에러 입니다.(관리자에 문의) |




