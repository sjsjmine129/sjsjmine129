# [완료-single] mysql_notification_myBirthday

기능 : 이 함수는 사용자의 생일이 5일 남았을 때 사용자에게 알림을 보내는 역할을 합니다. 이 함수는 특정 사용자의 생일이 5일 남은지를 확인하고, 만약 그렇다면 사용자에게 "5일 후에 생일이니, 이번 선물은 티클에서 받아보는 건 어떨까요?"라는 메시지를 알림으로 보냅니다.

## Input

매일 오후 4시

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공 | 200 | {"success": true, "message": "생일인 유저 ${birthday_users.length}명에게 생일 알림을 완료했습니다."} |
| 실패 | 500 | "내부 서버 오류" |