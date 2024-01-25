# [완료-single] sns_rebuildPhoneTable (2023.8.17)

기능 : RDS 켜고 꺼질때 자동으로 작동

phones 테이블 이 삭제되었을 시 재생성

## Output

|  |  | return |
| --- | --- | --- |
| sql에러 |  | console.log("SQL 에서 에러가 발생했습니다.", err);
const return_body = {
success: false,
data: null,
message: "SQL error",
};
return return_body; |
| 데이터 그대로 일때 |  | console.log("data is safe");
const return_body = {
success: true,
data: null,
message: "data is safe",
};
return return_body; |
| 잘 됬을 때 |  | console.log("set all data to phone table"); |
|  |  |  |
|  |  |  |