---
title: "S3 Server Access Logging"
date: "`r Sys.Date()`"
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

Trong bước này, chúng ta sẽ thực hiện tạo sử dụng tính năng **Server access logging**.

Server access logging cung cấp cho bạn khả năng hiển thị các hoạt động cấp đối tượng chi tiết trên dữ liệu của bạn. Log là tệp văn bản có một dòng cho mỗi bản ghi nhật ký. Mỗi log đại diện cho một yêu cầu và bao gồm các trường được phân cách bằng dấu cách.

Các trường liên quan đến operation, requester, resource và thông tin session. Dưới đây là một ví dụ:

```
79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be awsexamplebucket1 [06/Feb/2019:00:00:38 +0000] 192.0.2.3 79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be 3E57427F3EXAMPLE REST.GET.VERSIONING - "GET /awsexamplebucket1?versioning HTTP/1.1" 200 - 113 - 7 - "-" "S3Console/0.4" - s9lzHYrFp76ZVxRcpX9+5cjAnEH2ROuNkd2BHfIa6UkFVdtjf5mKR3/eTPFvsiP/XV/VLi31234= SigV2 ECDHE-RSA-AES128-GCM-SHA256 AuthHeader awsexamplebucket1.s3.us-west-1.amazonaws.com TLSV1.1
```

### Kích hoạt Server access logging

1. Trong giao diện S3, chọn bucket **logging-workshop**.

![S3console](/images/3.connect/30.png)

2. Trong giao diện bucket, chọn **Properties**.

![CreateBucket](/images/3.connect/31.png)

3. Kéo xuống tại muc **Server access logging**, chọn **Edit**

![CreateBucket](/images/3.connect/32.png)

4. Chọn **Enable**, sau đó chọn **Brow S3** để chọn bucket lưu log.

![CreateBucket](/images/3.connect/33.png)

5. Chọn bucket **logging-workshop-destination**, sau đó nhấn **Choose destination**.

![CreateBucket](/images/3.connect/34.png)

6. Review lại bucket lưu log, sau đó nhấn **Save changes**.

![CreateBucket](/images/3.connect/35.png)

7. Xác nhận **Server access logging** đã được bật.

![CreateBucket](/images/3.connect/36.png)

8. Mở một tab ẩn danh mới và nhập URL truy cập tới file chúng ta đã lưu.

9. Quay về giao diện buckets, chọn bucket **logging-workshop-destination**, chờ khoảng 15 phút, refresh lại bucket.

![CreateBucket](/images/3.connect/37.png)

10. Chúng ta sẽ thấy những file log đã được tạo ra. Chọn vào 1 file log.

![CreateBucket](/images/3.connect/38.png)

11. Chúng ta có thể thấy thông tin file log này. Chọn **Download** và mở file log ra

![CreateBucket](/images/3.connect/39.png)

12. File log sẽ có cấu trúc như sau:

```
b07c1e6c73fc3be646182d0400a50638e0703b6352275b2d165aa35f9791c572 logging-workshop [03/Mar/2024:12:52:26 +0000] 118.69.159.186 arn:aws:iam::928738046450:user/hung 2ET0N53Y32R632Q5 REST.GET.OWNERSHIP_CONTROLS - "GET /logging-workshop?ownershipControls= HTTP/1.1" 200 - 193 - 53 53 "-" "S3Console/0.4, aws-internal/3 aws-sdk-java/1.12.488 Linux/5.10.209-175.858.amzn2int.x86_64 OpenJDK_64-Bit_Server_VM/25.372-b08 java/1.8.0_372 vendor/Oracle_Corporation cfg/retry-mode/standard" - xqa7XzBU4q1xnx4NmkVBFhDsnt0jk07Slo9F3j2kvD0/6zSveFBzQ5t+Zrfs/me6L4epr6/dG3k= SigV4 ECDHE-RSA-AES128-GCM-SHA256 AuthHeader s3.ap-southeast-1.amazonaws.com TLSv1.2 - -
b07c1e6c73fc3be646182d0400a50638e0703b6352275b2d165aa35f9791c572 logging-workshop [03/Mar/2024:12:52:28 +0000] 118.69.159.186 arn:aws:iam::928738046450:user/hung YP9K97RHY7C5JPBC REST.GET.OBJECT_TAGGING S3_logging_workshop.txt "GET /logging-workshop/S3_logging_workshop.txt?tagging= HTTP/1.1" 200 - 115 - 13 10 "-" "S3Console/0.4, aws-internal/3 aws-sdk-java/1.12.488 Linux/5.10.209-175.858.amzn2int.x86_64 OpenJDK_64-Bit_Server_VM/25.372-b08 java/1.8.0_372 vendor/Oracle_Corporation cfg/retry-mode/standard" - nGxxv80fXE5xGWiS6C7OIg7/ncxoVho61Lmw9+qyveqdOBbiqRD4HJZf8qU90j0IeUXNGmwcSwA= SigV4 ECDHE-RSA-AES128-GCM-SHA256 AuthHeader s3.ap-southeast-1.amazonaws.com TLSv1.2 - -
```
