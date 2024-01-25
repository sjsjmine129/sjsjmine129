# [tikkle] get_image_profileSaveUrl (2023.8.1)

기능 : 토큰 확인 아이디 추출

       프로필 사진 업데이트 url id 로 만들어서 리턴

<s3 버킷에 **CORS(Cross-origin 리소스 공유) 편집 필요>**

[
{
"AllowedHeaders": [
"*"
],
"AllowedMethods": [
"PUT"
],
"AllowedOrigins": [
"*"
],
"ExposeHeaders": []
}
]

프론트에서 확인 방식 → url 에 이 람다의 결과 값 지정!

```html
<!DOCTYPE html>
<html>
	<head>
		<title>Image Upload</title>
	</head>
	<body>
		<h1>Image Upload</h1>
		<input type="file" id="imageInput" accept="image/jpeg, image/png" />
		<button id="uploadButton">Upload</button>

		<script>
			document
				.getElementById("uploadButton")
				.addEventListener("click", uploadImage);

			async function uploadImage() {
				const imageInput = document.getElementById("imageInput");
				const file = imageInput.files[0];

				if (!file) {
					alert("Please select an image file.");
					return;
				}

				const url =
					"https://tikkle-profile-src.s3.ap-northeast-2.amazonaws.com/tikkle-profile-src-5.JPG?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAZXNOUYCFT2KMP3OR%2F20230801%2Fap-northeast-2%2Fs3%2Faws4_request&X-Amz-Date=20230801T021331Z&X-Amz-Expires=360&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEDIaDmFwLW5vcnRoZWFzdC0yIkcwRQIhAN59MGtIKYHLWr5jqWjkzkaSmZ3dFrt0DfMcTQzue851AiBFXTH%2FpvktzlQew3Q8sNIFb795MIPtnxQtbriGSxZr9SqTAwjL%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAAaDDY2ODc3MDU0OTg5OSIMu2ykiVMlCDCRiw6KKucCqr1GCEv6fUX4osKyA2ur9WRtM0uxW20kcnNIndyFO9g9k35rKa%2FIMf%2FE7M%2FaoalOPwSuVoQ%2B%2FPNuB1TiQffA0oHk4JPsBy%2Fn98q8IJ4LsWvZsRkIxFr%2Fzuln6Lyc1VMX6zmY7mybcrCVReMs064m4BGqDZo2HlXAV9LzkwJwoPDR0IhwiLORZRYzOm5xEOfZRUke6w8wSJcIn4VL%2Fhs5mGLvosN5ONS6zzXPpFvvnMfF66nz2QhXrAp7DFQyutQ32fOdQatVQYxT2j%2Fg%2BOmvbUBuj4hihhzGh6q7ZEjlS0gYzJmUAcbNymi%2Ftu6Jroacyg0%2FAAx%2FRZYgYuu0TXx5JtlrDBtWLcEtErUVqg5J4wQ7fay4%2B2nxGY0XnKfeyme9T5OG%2Bo7JsZRd7yGFEzsjVSdqfqb4qMb9ylpHesAmCUR5Ufz0H%2BuLLRk8xp59Z80b0vNZMxCisGahVpz%2FIJOA9HtSwXmx1o0wydShpgY6nQHb%2FhV9GHo%2F1fYBNTSL2RcwS1DFK%2F4QdToiD%2FAXY41JAR2CI9CmiuCVitelbv%2BGoGeMNoZdhmBtmkOU4J5MU2ZFjLK4nfPTx0W66nHrc5Za4PFySES0%2BB9LPXnZqpNsLT%2BF0VT8EouTPdm9YrLgXKvXE8I3jPElT%2Bpow5%2BShn8JoTLKGuOXAcCx%2FVks1wh3p77PgwYANTVHm7HAAF%2BQ&X-Amz-Signature=fc4fd4b1437e02373849a04cb805df6ae8905ca99b02eebdae20cb68c81ddbfb&X-Amz-SignedHeaders=host";

				try {
					const response = await fetch(url, {
						method: "PUT",
						body: file,
						headers: {
							"Content-Type": file.type,
						},
					});

					if (response.ok) {
						alert("Image uploaded successfully.");
					} else {
						alert("Failed to upload the image.");
					}
				} catch (error) {
					console.error("Error uploading the image:", error);
					alert("An error occurred while uploading the image.");
				}
			}
		</script>
	</body>
</html>
```

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공 | 200 - 0 | const return_body = {
		success: true,
		data: url,
		detail_code "00",
		message: "success to make url",
		returnToken: returnToken,
	};
	return res.status(200).send(return_body); |
|  |  |  |
|  |  |  |
| 실패
→s3 연결중 오류 | 500 - 00 | console.log("get_image_profileSaveUrl 에서 에러가 발생했습니다.", error);
const return_body = {
success: false,
detail_code: "00",
message: "url making fail",
returnToken: null,
};
return res.status(500).send(return_body);		}; |
|  |  |  |

TEST

성공

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.get(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/get_image_profileSaveUrl",
			{
				headers: {
					authorization:
						"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTA1MjE2NDYsImlzcyI6IkxpRm9saSJ9.w-4NVe-YbhdeXUPKmiZpOZMi8it_FmwNp3jrbIYh4ME,eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTMxMTI3NDYsImlzcyI6IkxpRm9saSJ9.Cl7fT5xT3VxAwpL7QbL8k7z9vaFkaWXr6iDlgReYo0o",
				},
			}
		);

		// Ensure data exists before logging it
		if (response && response.data) {
			console.log(response.data);
		} else {
			console.log("Response or response data is undefined");
		}
	} catch (error) {
    if (error.response && error.response.status) {
      console.error("[status code] ", error.response.status);
    }
    if (error.response && error.response.data) {
      console.error("response data : ", error.response.data);
    }
  }
}

fetchData();
```

NEW!!

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.get(
			"https://d2bk3qgare1vfi.cloudfront.net/dev/get_image_profileSaveUrl",
			{
				headers: {
					authorization:
						"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTA1MjE2NDYsImlzcyI6IkxpRm9saSJ9.w-4NVe-YbhdeXUPKmiZpOZMi8it_FmwNp3jrbIYh4ME,eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTMxMTI3NDYsImlzcyI6IkxpRm9saSJ9.Cl7fT5xT3VxAwpL7QbL8k7z9vaFkaWXr6iDlgReYo0o",
				},
			}
		);

		// Ensure data exists before logging it
		if (response && response.data) {
			console.log(response.data);
		} else {
			console.log("Response or response data is undefined");
		}
	} catch (error) {
		if (error.response && error.response.status) {
			console.error("[status code] ", error.response.status);
		}
		if (error.response && error.response.data) {
			console.error("response data : ", error.response.data);
		}
	}
}

fetchData();
```