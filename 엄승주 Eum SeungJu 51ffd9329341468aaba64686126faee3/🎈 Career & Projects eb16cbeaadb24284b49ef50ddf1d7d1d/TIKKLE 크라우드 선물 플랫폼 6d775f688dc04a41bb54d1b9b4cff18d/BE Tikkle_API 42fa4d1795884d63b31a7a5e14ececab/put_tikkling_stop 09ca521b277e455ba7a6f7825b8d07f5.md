# put_tikkling_stop

기능: 티클링을 중단

## Input

tikkling_id: 3

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공
 | 200-00 | {
 success: true,
 detail_code: "00",
  message: `티클링을 성공적으로 중단하였습니다.`,
  returnToken,
} |
| 실패
→존재하지 않는 티클링에 대한 요청 | 404-00 | success: false,
 detail_code: "00",
message: "비정상적 요청, 티클링을 찾을 수 없습니다.",
returnToken: null,

 |
| 실패
→이미 종료된 티클에 의해 종료 요청 | 400-00 | {
success: false,
detail_code: "00",
message: "이미 종료된 티클링입니다.",
returnToken,
} |
| 실패
→서버 에러 | 500-00 | {
success: false,
detail_code: "00",
message: "서버 에러",
} |