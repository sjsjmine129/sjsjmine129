# [tikkle] get_bank_data (2023.9.25)

기능 : 은행 리스트 데이터 가져옴

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공
→ 데이터 가져오기 성공 | 200 - 00 | const return_body = {
		success: true,
		data: sqlResult,
		detail_code: "00",
		message: "success get bank info",
		returnToken: returnToken,
	};
	return res.status(200).send(return_body); |
|  |  |  |
|  |  |  |
|  |  |  |
| 실패
→DB  오류 | 500 - 01 | const return_body = {
			success: false,
			detail_code: "01",
			message: "SQL error",
			returnToken: null,
		};
		return res.status(500).send(return_body); |