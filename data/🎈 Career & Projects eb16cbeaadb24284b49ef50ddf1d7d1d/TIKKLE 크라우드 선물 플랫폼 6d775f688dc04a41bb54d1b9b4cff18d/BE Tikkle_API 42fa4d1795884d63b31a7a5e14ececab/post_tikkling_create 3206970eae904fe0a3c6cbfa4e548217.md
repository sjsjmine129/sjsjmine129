# post_tikkling_create

기능 : 티클링 생성하기

## Input

{ "headers": { 

"Authorization": { 

"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTA1MjE2NDYsImlzcyI6IkxpRm9saSJ9.w-4NVe-YbhdeXUPKmiZpOZMi8it_FmwNp3jrbIYh4ME", "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTMxMTI3NDYsImlzcyI6IkxpRm9saSJ9.Cl7fT5xT3VxAwpL7QbL8k7z9vaFkaWXr6iDlgReYo0o" } }, "body": { 

"funding_limit": "2023-08-30", 

"tikkle_quantity": 100, 

"product_id": 5 }, 

"queryStrignParameters": {} 

}

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공
 | 200-00 | {
success: true,
detail_code: “00”,
message: "티클링 생성을 성공하였습니다.",
returnToken,
}
 |
| 실패
→ 이미 티클링중인 유저 | 403-01 | {
detail_code: “01”
success: false,
message: "잘못된 요청, 이미 티클링중인 유저입니다.",
returnToken,
}
 |
| 실패
→해당 상품의 재고가 남아있지 않음 | 403-02 | {
detail_code: “02”
success: false,
message: "잘못된 요청, 해당 상품의 재고가 남아있지 않습니다.",
returnToken,
}
 |
| 실패
→ 유저의 티켓이 부족 | 403-03 | {
detail_code: “03”
success: false,
message: "잘못된 요청, 해당 상품의 재고가 남아있지 않습니다.",
returnToken,
}
 |
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