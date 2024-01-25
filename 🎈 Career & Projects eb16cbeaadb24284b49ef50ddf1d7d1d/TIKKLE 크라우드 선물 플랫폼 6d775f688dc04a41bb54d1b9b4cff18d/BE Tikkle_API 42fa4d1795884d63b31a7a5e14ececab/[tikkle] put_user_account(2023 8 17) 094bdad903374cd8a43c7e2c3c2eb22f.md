# [tikkle] put_user_account(2023.8.17)

기능 : 

유저 테이블에 암호화해서 주소 저장

input{

account : “123412”,

bank_code:  2

}

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공 | 200 - 00 | const return_body = {
success: true,
detail_code: "00",
message: "success to update account info",
returnToken: returnToken,
};
return res.status(200).send(return_body); |
| 실패 
→ 인풋 데이터 오류 | 400 - 00 | console.log("put_user_account의 입력 데이터에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "00",
message: "input value is null or invalid",
returnToken: null,
};
return res.status(400).send(return_body); |
|  |  |  |
| 실패
→쿼리  오류 | 500 - 00 | console.log("put_user_account의 query에서 에러가 발생했습니다.", err);
const return_body = {
success: false,
detail_code: "00",
message: "SQL error",
returnToken: null,
};
return res.status(500).send(return_body); |
|  |  |  |

해석하기

```jsx
const crypto = require("crypto");

async function fetchData() {
	const algorithm = "aes-256-cbc"; // Use the same algorithm that was used for encryption
	const ivHex = ;//파라미터 스토어에 저장되어 있음
	const iv = Buffer.from(ivHex, "hex");

	const keyHex =;//파라미터 스토어에 저장되어 있음
	const key = Buffer.from(keyHex, "hex");

	const encryptedData = "a8af9dd94c9ae2acf14aab9674bf0041";

	// Decryption
	const decipher = crypto.createDecipheriv(algorithm, key, iv);

	let decryptedData = decipher.update(encryptedData, "hex", "utf-8");
	decryptedData += decipher.final("utf-8");

	console.log("Decrypted Data:", decryptedData);
}

fetchData();
```