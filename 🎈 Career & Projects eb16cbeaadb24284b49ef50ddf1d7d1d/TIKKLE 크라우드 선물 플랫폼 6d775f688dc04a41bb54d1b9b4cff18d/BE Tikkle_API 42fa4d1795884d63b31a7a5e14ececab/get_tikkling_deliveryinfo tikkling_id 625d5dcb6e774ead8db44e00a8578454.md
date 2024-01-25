# get_tikkling_deliveryinfo/:tikkling_id

기능: 

tikkling_id =0  → 자신의 가장 최근 배송내역을 불러옴

tikkling_id >= 1 → 해당 티클링에 대한 배송내역을 불러옴

"body": {
    "tikkling_id": 5,
    "tikkle_quantity": 30,
    "message": "선물이지롱"
  }

## Output

|  | statusCode | body |
| --- | --- | --- |
| 성공
→자신에게 보낸경우 티켓을 지급받지 못함 | 200-00 | {
const return_body = {
success: true,
detail_code: “01”,
message: 티클을 성공적으로 보냈습니다. 자신의 티클 보내기에서는 티켓을 받을 수 없습니다.
returnToken,
data: 
{
"delivery_info"
:{"id":4,"invoice_number":null,"courier_company_code":null,"tikkling_id":124,"state_id":1,"zonecode":"12417","address":"Ddd","detail_address":"Ddd","created_at":"2023-11-16T16:16:20.000Z","start_delivery_date":null,"expected_delivery_date":null,"actual_delivery_date":null},

"delivery_check_link"
:"http://info.sweettracker.co.kr/tracking/5?t_key=hCTgxKBi91rgVLAG4SYqkw&t_code=null&t_invoice=null"}}

}
 |
| 실패
→ 해당 유저에 대한 배송기록이 존재하지 않음 | 400-01 | {"message": "해당 티클링의 배송 기록이 없습니다.number ", "success": false}, "status": 404} |
| 실패
→ 해당 티클링에 대한 배송기록이 존재하지 않음 | 400-02 | {"message": "해당 티클링의 배송 기록이 없습니다.number ", "success": false}, "status": 404} |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
| 실패
→서버 에러 | 500-00 | console.log("post_user_getTikklingDetail 에서 에러가 발생했습니다.", err);
    const return_body = {
      success: false,
      detail_code: "00",
      message: "SQL error",
      returnToken: null,
    };
    return res.status(500).send(return_body); |

DS