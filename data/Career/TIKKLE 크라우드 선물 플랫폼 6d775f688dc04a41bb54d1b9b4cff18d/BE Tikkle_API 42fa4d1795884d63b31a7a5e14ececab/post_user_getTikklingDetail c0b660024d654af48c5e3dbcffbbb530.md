# post_user_getTikklingDetail

기능: 티클상세보기 페이지를 위한 데이터 불러오기

"body": {
    "tikkling_id": 5,
    "tikkle_quantity": 30,
    "message": "선물이지롱"
  }

## Output

|  | statusCode | body |
| --- | --- | --- |
| 성공
→자신에게 보낸경우 티켓을 지급받지 못함 | 200-01 | {
const return_body = {
success: true,
detail_code: “01”,
message: 티클을 성공적으로 보냈습니다. 자신의 티클 보내기에서는 티켓을 받을 수 없습니다.
returnToken,
}
 |
|  |  |  |
|  |  |  |
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