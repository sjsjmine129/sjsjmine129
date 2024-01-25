# [완료-single] mysql_notification_friendBirthday

기능 : 친구의 생일이 되면, 해당 친구에게 알림을 보내는 함수입니다. 이 함수는 특정 사용자의 친구 목록을 데이터베이스에서 찾아내고, 그 중 오늘 생일인 사람이 있는지 확인합니다. 만약 있으면 해당 친구에게 "오늘은 친구의 생일입니다" 라는 알림 메시지를 전송합니다.

## Input

매일 오전 10시

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공 | 200 | {"success": true, "message": "생일인 유저 ${birthday_users_friends.name}님의 친구 ${birthday_users_friends.length}명에게 생일 알림을 완료했습니다."} |
| 실패 | 500 | "내부 서버 오류" |