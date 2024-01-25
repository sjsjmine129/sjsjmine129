# [완료-single] s3_image_profileResize (2023.8.24)

기능 : 프로필 버킷에 새 이미지 추가 되면 resize 시킨 이미지들 저장

          각각의 url 데이터베이스 저장

저장된 url정보로 이전의 사진들 삭제

## Input

tikkle-profile-src 에 이미지 업로드됬을때

file이름 {userId}.JPG

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공 | 200 | {"36":"https://tikkle-profile.s3.ap-northeast-2.amazonaws.com/36/tikkle-profile-5.JPG%22,%2248%22:%22https://tikkle-profile.s3.ap-northeast-2.amazonaws.com/48/tikkle-profile-5.JPG%22,%2264%22:%22https://tikkle-profile.s3.ap-northeast-2.amazonaws.com/64/tikkle-profile-5.JPG%22,%22128%22:%22https://tikkle-profile.s3.ap-northeast-2.amazonaws.com/128/tikkle-profile-5.JPG"} |
|  |  | 위 형식으로 users image 에 저장 |
|  |  |  |
|  |  |  |
|  |  |  |