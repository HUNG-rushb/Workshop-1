---
title: "Các bước chuẩn bị"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

Để chuẩn bị cho workshop này, chúng ta tạo 1 bucket với public access để chứa file cần truy cập và 1 private bucket để chứa server access log.

### Tạo 2 bucket

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

6. Xác nhận bucket đã được tạo thành công.

![CreateBucket](/images/2.prerequisite/25.png)

7. Tiếp tục tạo bucket **logging-workshop-destination**

- Mục **AWS Region**, chọn **Asia Pacific (Singapore) ap-southeast-1**.
- Mục **Bucket name**, nhập **`logging-workshop-destination`**.
- Không cần bỏ chọn mục **Block Public Access settings for this bucket**.
- Kéo xuống dưới cùng, chọn **Create bucket**.
- Xác nhận bucket đã được tạo thành công.

![CreateBucket](/images/2.prerequisite/39.png)
![CreateBucket](/images/2.prerequisite/40.png)
![CreateBucket](/images/2.prerequisite/41.png)

### Cập nhật quyền tạo log cho S3 log delivery group

8. Quay về giao diện các bucket, chon bucket **logging-workshop-destination**. Kéo xuống mục **Object Ownership**, chọn **Edit**

![CreateBucket](/images/2.prerequisite/41-5.png)
![CreateBucket](/images/2.prerequisite/42.png)

9.  Chọn **ACLs enabled**, xác nhận **I acknowledge that ACLS will be restored.**, nhấn **Save changes**. Bước này sẽ giúp những đối tượng trong **Access control list (ACL)** ngoài bucket owner có quyền tạo object.

![CreateBucket](/images/2.prerequisite/43.png)

10. Sau đó kéo xuống mục **Access control list (ACL)**, chọn **Edit**.

![CreateBucket](/images/2.prerequisite/44.png)

11. Tại mục **S3 log delivery group**, chọn quyền **Write**, sau đó **Save changes**.

![CreateBucket](/images/2.prerequisite/45.png)

12. Xác nhận quyền **Write** cho **S3 log delivery group**.

![CreateBucket](/images/2.prerequisite/46.png)

### Upload file vào bucket

8. Chọn bucket **logging-workshop**. Trong giao diện bucket, chọn **Upload**.

![CreateBucket](/images/2.prerequisite/26.png)

9. Trong giao diện upload, chọn **Add files**.

![CreateBucket](/images/2.prerequisite/27.png)

10. Tiếp tục:

- Tải xuống file **S3_logging_workshop.txt** tại {{%attachments  pattern=".txt"/%}}

{{% notice note %}}
Bạn hãy mở file trong tab mới, nhấn **Ctrl + S** để lưu file về máy.
{{% /notice %}}

- Xác nhận file đã chọn thành công.
- Chọn **Upload**.

![CreateBucket](/images/2.prerequisite/28.png)

11. Xác nhận file đã được tải lên thành công.

![CreateBucket](/images/2.prerequisite/29.png)

### Thêm policy cho bucket

12. Trở về giao diện S3, chọn **logging-workshop** bucket.

![CreateBucket](/images/2.prerequisite/30.png)

13. Trong giao diện bucket, chọn mục **Permissions**.

![CreateBucket](/images/2.prerequisite/31.png)

14. Mục **Bucket policy**, chọn **Edit**.

![CreateBucket](/images/2.prerequisite/32.png)

15. Nhập vào mục policy:

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

16. Kéo xuống dưới cùng, chọn **Save changes**

![CreateBucket](/images/2.prerequisite/34.png)

17. Xác nhận update policy thành công.

![CreateBucket](/images/2.prerequisite/35.png)

### Truy cập file

18. Trở về giao diện bucket, chọn vào file **S3_logging_workshop.txt**.

![CreateBucket](/images/2.prerequisite/36.png)

19. Copy **Object URL**.

![CreateBucket](/images/2.prerequisite/37.png)

20. Paste URL vào trình duyệt vào xác nhận đã truy cập được vào file. Hãy giữ lại URL này cho phần tiếp theo.

![CreateBucket](/images/2.prerequisite/38.png)
