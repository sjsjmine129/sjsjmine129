# get_friend_event

기능 : 현재 block되지 않은 친구중 다가오는 7일 이내의 친구 생일데이터 가져오기

## Input

{
"requestContext": {
"connectionId": "ConnectionID_TEST2"
},
"headers": {
"Authorization": {
"accessToken": "eyJDsw",
"refreshToken": "eyJho8NI"
}
}
}

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공
→생일인 친구 존재하지 않음 | 200-01 | {
success: true,
detail_code: “01”,
data: [],
message: "생일인 친구가 없습니다.”,
accessToken,
} |
| 성공
→ 생일인 친구 존재 | 200-02 | {
success: true,
data: [{
name: “gkdl”,
birthday: “2023-12-12”,
image: “fhaiojfe”,
is_tikkling: 1
}],
detail_code: "02",
message: "성공적으로 생일인 친구를 불러왔습니다.",
returnToken,
} |
| 실패 
→ 토큰 없음
    토큰 오류
    리프레시 토큰 오류 | 401-99 | console.log("authtoken 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "99",
message: "login again",
};
return res.status(401).send(return_body); |
| 실패
→서버 에러 | 500-00 | {
success: false,
detail_code: "00",
message: "서버 에러",
} |