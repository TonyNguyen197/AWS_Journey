## Giới thiệu
Chúng ta sẽ triển khai Unishop trong một AWS Region và sau đó sử dụng AWS Backup và EC2 AMIs để tạo một bản backup của cửa hàng chúng ta ở một Region khác. Chúng ta sẽ khám phá DR bằng việc mô phỏng một thảm họa trong Region chính và phục hồi cửa hàng trong Region backup. Module này sẽ mất khoảng 90 phút để hoàn thành


Ứng dụng mẫu là Unishop. Nó là một ứng dụng Spring Boot Java kết nối tới một CSDL MySQL với một frontend được viết bằng Bootstrap.
Ứng dụng này được triển khai trên một EC2 Instance (t3.small) với một VPC chuyên dụng sử dụng một Public Subnet. Lưu ý rằng đây không phải là một kiến trúc cơ sở hạ tầng lý tưởng để chạy sản phẩm ứng dụng sẵn sàng cao nhưng đủ đáp ứng cho bài thực hành này.

Để cấu hình một hạ tầng và triển khai một ứng dụng, chúng ta sẽ sử dụng Cloudformation. Cloudformation là một cách thức dễ dàng để tăng tốc việc cung cấp cloud với hạ tầng là mã code (Infrastructure as Code - IaC).

Chúng ta sẽ bắt đầu triển khai Unishop đến us-east-1 AWS Region và xác định chức năng. Sau đó sử dụng một EC2 AMI và AWS Backup để tạo và kiển tra một ứng dụng đầy đủ chức năng trong  us-west-1 Region

- [**Chuẩn bị**](#a1)
Đằng nhập vào AWS Management Console bằng một IAM User có quyền  PowerUserAccess hoặc AdministratorAccess để đảm bảo thực hiện bài lab này thành công

Lưu ý rằng bạn sẽ phải chi trả một khoảng phí cho việc triển khai tài nguyên trong bài lab này. Sau khi hoàn thành, nhớ hoàn thành phần [Dọn dẹp tài nguyên](#a2) để xóa những tài nguyên AWS không cần thiết
Bài lab này sẽ mất khoảng 90 phút để hoàn thành

-[**Truy cập S3**](#b1)

## Cho phép Amazon S23 truy cập công khai

1.1 Click [S3](https://console.aws.amazon.com/s3/home?region=us-east-1#/){:target="\_blank"} để chuyển hướng đến trang chủ S3
1.2 Click vào mục **Block Public Access settings for this account**

![Đây là ảnh](AWS_Journey/doc1/pictures/pic1_2.png)
