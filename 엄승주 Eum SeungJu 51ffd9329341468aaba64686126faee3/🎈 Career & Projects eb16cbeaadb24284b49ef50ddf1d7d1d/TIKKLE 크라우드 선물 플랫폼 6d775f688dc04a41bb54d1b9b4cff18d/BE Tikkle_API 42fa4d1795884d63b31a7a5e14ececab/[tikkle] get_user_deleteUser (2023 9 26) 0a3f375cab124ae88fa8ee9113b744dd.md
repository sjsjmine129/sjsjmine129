# [tikkle] get_user_deleteUser (2023.9.26)

기능 : 토큰으로 아이디 확인

           유저 데이터에 삭제 속성 1로 바꿈

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공 | 200 - 00 | const return_body = {
		success: true,
		data: null,
		detail_code: "00",
		message: "success to delete user",
		returnToken: returnToken,
	};
	return res.status(200).send(return_body); |
|  |  |  |
|  |  |  |
| 실패
→DB  쿼리 오류 | 500 - 00 | console.log("get_user_deleteUser의 query에서 에러가 발생했습니다.", err);
		const return_body = {
			success: false,
			detail_code: "00",
			message: "SQL error",
			returnToken: null,
		};
		return res.status(500).send(return_body); |
|  |  |  |