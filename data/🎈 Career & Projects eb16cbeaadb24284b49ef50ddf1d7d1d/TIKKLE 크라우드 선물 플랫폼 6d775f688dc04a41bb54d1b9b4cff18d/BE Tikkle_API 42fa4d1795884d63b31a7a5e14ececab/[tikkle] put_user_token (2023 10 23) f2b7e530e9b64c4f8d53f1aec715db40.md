# [tikkle] put_user_token (2023.10.23)

기능 : 디바이스 토큰 저장

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공 | 200 - 00 | const return_body = {
    success: true,
    detail_code: "00",
    message: "success to update token info",
    returnToken: returnToken,
  };
  return res.status(200).send(return_body); |
| 실패 
→ 인풋 데이터 오류 | 400 - 00 | console.log("put_user_token의 입력 데이터에서 에러가 발생했습니다.");
    const return_body = {
      success: false,
      detail_code: "00",
      message: "input value is null or invalid",
      returnToken: null,
    };
    return res.status(400).send(return_body); |
|  |  |  |
| 실패
→쿼리  오류 | 500 - 00 | console.log("put_user_token의 query에서 에러가 발생했습니다.", err);
    const return_body = {
      success: false,
      detail_code: "00",
      message: "SQL error",
      returnToken: null,
    };
    return res.status(500).send(return_body); |
|  |  |  |