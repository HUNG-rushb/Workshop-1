---
title: "Giới thiệu"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

Khi sử dụng tính năng logging trên Amazon S3, bạn có thể ghi lại các hành động do người dùng và dịch vụ thực hiện trên tài nguyên Amazon S3 của mình. Sau đó, bạn có thể sử dụng bản ghi logging cho mục đích kiểm tra, kiểm soát.

![S3log](/images/1.introduce/10.png)

Bạn có thể ghi lại logging của Amazon S3 bằng **Server access logging** hoặc **AWS CloudTrail logs**.

**Server access logging** là một chức năng nằm trong dịch vụ S3 của AWS, cung cấp log chi tiết cho các yêu cầu được gửi tới S3 bucket.

**Server access logging** bị disabled theo mặc định. Log thường được gửi trong vòng vài giờ và rất hiếm khi mất log. Tính năng này không bị tính phí logging cũng như các thao tác PUT lưu log vào bucket. Bạn chỉ bị tính phí cho việc lưu trữ log và các thao tác GET trên file log. Bạn có thể sử dụng **object lifecycle management** để xóa bớt log cũ, giảm thiểu chi phí lưu trữ.

![S3sal](/images/1.introduce/11.png)

**AWS CloudTrail** là dịch vụ cung cấp bản ghi các hành động được thực hiện bởi người dùng, vai trò hoặc dịch vụ trong Tài khoản AWS của bạn. Bạn có thể sử dụng **CloudTrail** để kiểm tra tài khoản của mình bằng cách logging và monitor mọi hoạt động, phát hiện nếu như có hoạt động bất thường trong tài khoản của mình.

Log các hành động của **Amazon S3** bằng **AWS CloudTrail** giúp bảo mật tài khoản của bạn bằng cách cung cấp khả năng kiểm tra và phân tích quyền truy cập.

![S3ct](/images/1.introduce/12.png)

<!-- ![S3ct](/images/1.introduce/12.png) -->

**So sánh giữa hai cách**

| Log properties                                                                                       | AWS CloudTrail | Amazon S3 server logs |
| ---------------------------------------------------------------------------------------------------- | :------------: | :-------------------: |
| Can be forwarded to other systems (Amazon CloudWatch Logs, Amazon CloudWatch Events)                 |      Yes       |          No           |
| Deliver logs to more than one destination (for example, send the same logs to two different buckets) |      Yes       |          No           |
| Turn on logs for a subset of objects (prefix)                                                        |      Yes       |          No           |
| Cross-account log delivery (target and source bucket owned by different accounts)                    |      Yes       |          No           |
| Integrity validation of log file by using digital signature or hashing                               |      Yes       |          No           |
| Default or choice of encryption for log files                                                        |      Yes       |          No           |
| Object operations (by using Amazon S3 APIs)                                                          |      Yes       |          Yes          |
| Bucket operations (by using Amazon S3 APIs)                                                          |      Yes       |          Yes          |
| Searchable UI for logs                                                                               |      Yes       |          No           |
| Fields for Object Lock parameters, Amazon S3 Select properties for log records                       |      Yes       |          No           |

Bên cạnh đó, **Amazon Athena** là dịch vụ query tương tác giúp bạn dễ dàng phân tích dữ liệu trong **Amazon S3** bằng SQL tiêu chuẩn. Bạn không cần quản lý bất kỳ cơ sở hạ tầng nào với Athena và bạn chỉ trả tiền cho các truy vấn bạn chạy.

Sau khi bật **server access logs** hoặc **AWS CloudTrail** và lưu trữ trong S3 bucket mục tiêu, bạn có thể muốn phân tích hoặc tìm kiếm thông tin từ log. Logs không được **Amazon S3** tự động phân tích và bạn có thể có rất nhiều dữ liệu. Để phân tích tất cả dữ liệu **Amazon S3**, bạn có thể sử dụng **Amazon Athena**.

![S3athena](/images/1.introduce/13.png)
