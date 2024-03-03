---
title: "Preparation "
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

To prepare for this workshop, we create a public access bucket to store the files we need to access and a private bucket to store the server access log.

1. Truy cập vào AWS Management Console, tìm S3 và chọn S3.

![S3console](/images/2.prerequisite/20.png)

2. Trong giao diện S3, chọn **Create bucket**.

![CreateBucket](/images/2.prerequisite/21.png)

3. Trong giao diện create bucket

- Mục **AWS Region**, chọn **Asia Pacific (Singapore) ap-southeast-1**.
- Mục **Bucket name**, nhập **`logging-workshop`**.

![CreateBucket](/images/2.prerequisite/22.png)

4. Tiếp tục:

- Mục **Block Public Access settings for this bucket**, bỏ chọn **Block all public access**.
- Mục **Turning off block all public access might result in this bucket and the objects within becoming public**, xác nhận mục này.

![CreateBucket](/images/2.prerequisite/23.png)

5. Kéo xuống dưới cùng, chọn **Create bucket**.

![CreateBucket](/images/2.prerequisite/24.png)

6. Xác nhận bucket đã được tạo thành công và chọn vào bucket.

![CreateBucket](/images/2.prerequisite/25.png)

7. Trong giao diện bucket, chọn **Upload**.

![CreateBucket](/images/2.prerequisite/26.png)

8. Trong giao diện upload, chọn **Add files**.

![CreateBucket](/images/2.prerequisite/27.png)

9.  <!-- !!!!!!! -->

- Tải xuống file **S3_logging_workshop.txt** tại **https://logging-workshop.s3.ap-southeast-1.amazonaws.com/S3_logging_workshop.txt**

{{% notice note %}}
Bạn hãy mở file trong tab mở, nhấn **Ctrl S** để lưu file về máy.
{{% /notice %}}

- Xác nhận file đã chọn thành công.
- Chọn **Upload**.

![CreateBucket](/images/2.prerequisite/28.png)

1.  Xác nhận file đã được tải lên thành công.

![CreateBucket](/images/2.prerequisite/29.png)

11. Trở về giao diện S3, chọn **logging-workshop** bucket.

![CreateBucket](/images/2.prerequisite/30.png)

12. Trong giao diện bucket, chọn mục **Permissions**.

![CreateBucket](/images/2.prerequisite/31.png)

13. Mục **Bucket policy**, chọn **Edit**.

![CreateBucket](/images/2.prerequisite/32.png)

14. Nhập vào mục policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::logging-workshop/*"
    }
  ]
}
```

![CreateBucket](/images/2.prerequisite/33.png)

15. Kéo xuống dưới cùng, chọn **Save changes**

![CreateBucket](/images/2.prerequisite/34.png)

17. Xác nhận update policy thành công.

![CreateBucket](/images/2.prerequisite/35.png)

18. Trở về giao diện bucket, chọn vào file **S3_logging_workshop.txt**.

![CreateBucket](/images/2.prerequisite/36.png)

19. Copy **Object URL**.

![CreateBucket](/images/2.prerequisite/37.png)

20. Paste URL vào trình duyệt vào xác nhận đã truy cập được vào file.

![CreateBucket](/images/2.prerequisite/38.png)
