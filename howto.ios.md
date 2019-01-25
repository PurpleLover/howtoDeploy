# Hướng dẫn triển khai ứng dụng trên nền tảng iOS (Apple)

## Mục lục
1. [Giới thiệu](#Giới-thiệu)
2. [Điều kiện tiên quyết](#Điều-kiện-tiên-quyết)
3. [Các lỗi thường gặp](#Các-lỗi-thường-gặp)
4. [Cách đăng ký tài khoản nhà phát triển](#Cách-đăng-ký-tài-khoản-nhà-phát-triển)
    * [Đối với chương trình bình thường](#Đối-với-chương-trình-bình-thường)
    * [Đối với chương trình Enterprise](#Đối-với-chương-trình-Enterprise)
5. [Cách đăng tải ứng dụng lên AppStore](#Cách-đăng-tải-ứng-dụng-lên-AppStore)
6. [Nguồn tham khảo](#Nguồn-tham-khảo)

## Giới thiệu
Hiện giờ Apple đưa ra hai chương trình phát triển ứng dụng như sau:
### Chương trình bình thường (Apple Developer Program)
* Chi phí: $99/năm
* Có đầy đủ lựa chọn từ cá nhân đến tổ chức hay doanh nghiệp
* Ứng dụng phát triển ra sẽ phục vụ cho tất cả mọi người

### Chương trình Enterprise (Apple Developer Enterprise Program)
* Chi phí: $299/năm
* Chỉ dành cho doanh nghiệp
* Ứng dụng phát triển ra sẽ chỉ phục vụ nhân công trong doanh nghiệp đó

Nếu bạn đăng ký tài khoản cho doanh nghiệp thì cần phải có:
* Thông tin giấy phép đăng ký kinh doanh (bản tiếng Việt/ bản dịch tiếng Anh)
* Số D-U-N-S (_nếu là doanh nghiệp nhà nước thì không bắt buộc_)
* Trang Web của doanh nghiệp

### Đối với số D-U-N-S
[Kiểm tra xem doanh nghiệp mình đã có hay chưa](https://developer.apple.com/enroll/duns-lookup/#!/search)

Nếu chưa có thì thực hiện theo các bước sau đây,
* Truy cập vào [trang web này](https://fedgov.dnb.com/webform/pages/CCRSearch.jsp)

![duns-01](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/duns_register/duns_01.png)
* Bấm vào `Select a country or terriority` và chọn `VIETNAM`
* Hoàn tất form theo và chọn `Submit`

![duns-02](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/duns_register/duns_02.png)

Sau đó đợi đại diện DNB tại Việt Nam gọi, hãy trả lời là để tạo Apple Account, không tốn phí đăng ký.

## Điều kiện tiên quyết
1. Có AppleID, nếu chưa có thì đăng ký [tại đây](https://appleid.apple.com/account#!&page=create). Điền đầy đủ thông tin chính xác, và bật _xác thực hai yếu tố_.
2. Có thẻ tín dụng thừa hơn $300

## Các lỗi thường gặp
Người đứng tên đăng ký AppleID, thẻ VISA và tài khoản nhà phát triển của Apple nên là cùng một người, với đầy đủ họ tên (cả đệm nếu có). Vì khi tên người thay đổi sẽ tốn rất nhiều thời gian để gửi xác thực cho Apple.

Nếu có vấn đề gì liên quan thì gửi trực tiếp email hoặc gọi cho Apple để được giải đáp. Thông tin liên hệ với Apple, xem [tại đây](https://developer.apple.com/contact/#!/topic/select).

Ngoài ra, Apple chỉ chấp nhận 26 kí tự trong bảng Alphabet tiếng Anh, và các kí tự số từ 0 đến 9. Tuyệt đối không sử dụng kí tự Unicode (ê, â, ă...).

## Cách đăng ký tài khoản nhà phát triển
### Đối với chương trình bình thường
#### Bước 1
Truy cập vào [địa chỉ này](https://developer.apple.com/programs/enroll/) để tới trang đăng ký chương trình bình thường.

#### Bước 2
Kéo xuống dưới và nhấn vào nút `Start Your Enrollment`.

![02](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_normal/02.png)
#### Bước 3
Nhập AppleID và mật khẩu vào form.

![03](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_normal/03.png)

Đảm bảo mọi thông tin AppleID của mình là đúng. Rồi chọn thực thể của mình và chọn `Continue`.

![05](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_normal/05.png)

##### Nếu chọn cá nhân (Invidual)
![06](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_normal/06.png)

Điền đầy đủ thông tin yêu cầu và nhấn `Continue`. (Nhớ tích vào ô đồng ý với các điều khoản và dịch vụ trước khi bấm tiếp tục)

![07](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_normal/07.png)

Đảm bảo mọi thông tin là chính xác và nhấn `Continue`.

![08](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_normal/08.png)

Nếu bạn muốn Apple tự trừ phí hàng năm thì tích vào ô chọn `Automatic Renewal` để tự động gia hạn, điều này không bắt buộc. Rồi nhấn `Purchase`.

![09](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_normal/09.png)

##### Nếu chọn doanh nghiệp (Organization)
![_06a](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_normal/_06a.png)

Kéo xuống dưới chọn `Continue`.

![_06b](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_normal/_06b.png)

Nếu là chủ doanh nghiệp hoặc nhà sáng lập, thì chọn phương án thứ nhất, và điền `Email` làm việc của mình vào.

![_07a](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_normal/_07a.png)

Nếu là đại diện uỷ quyền của doanh nghiệp, thì chọn phương án thứ hai, rồi điền `Email` làm việc của mình và đầy đủ thông tin cá nhân của mình vào.

![_07b](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_normal/_07b.png)

Rồi điền thông tin doanh nghiệp vào mẫu, xong xuôi nhấn `Continue`

![_07c](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_normal/_07c.png)

#### Bước 4
Sau khi hoàn thiện xong các bước trên, trang web sẽ tự động chuyển hướng sang một trang mới, hãy điền AppleID và mật khẩu của mình vào đó, và nhấn `Sign In`.

![10](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_normal/10.png)

#### Bước 5
Điền đầy đủ thông tin cần thiết và chọn phương thức thanh toán, rồi nhấn `Continue`.

![11](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_normal/11.png)

**Lưu ý**: Sau khi hoàn thành mọi thủ tục, sẽ mất trong khoảng từ 24 đến 48 giờ để Apple gửi thông báo xác nhận vào hòm thư điện tử của bạn hoặc gọi đến điện thoại của bạn.

#### Bước 6
Sau khi nhận được mã kích hoạt, nhấn vào đường link và hoàn tất việc kích hoạt trong trang web mở ra (copy code kích hoạt vào chỗ đòi nhập).

![12](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_normal/12.png)

### Đối với chương trình Enterprise
#### Bước 1
Truy cập vào [địa chỉ này](https://developer.apple.com/programs/enterprise/enroll/) để tới trang đăng ký chương trình Enterprise.

#### Bước 2
Kéo xuống dưới và nhấn vào nút `Start Your Enrollment`.

![01](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_enterprise/01.png)

#### Bước 3
Đảm bảo mọi thông tin AppleID của mình là đúng. Rồi chọn thực thể của mình (doanh nghiệp hay doanh nghiệp nhà nước) và chọn `Continue`.

![02](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_enterprise/02.png)

#### Bước 4
Chọn `Authority` cho mình
* Nếu là nhà sáng lập: chọn phương án thứ nhất
* Nếu là đại diện uỷ quyền: chọn phương án thứ hai

![03](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_enterprise/03.png)

Cách điền thông tin tương tự với lựa chọn doanh nghiệp của chương trình bình thường.

#### Bước 5
Điền thông tin của doanh nghiệp vào mẫu.

![04](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_enterprise/04.png)

#### Bước 6
Nhập CAPTCHA và chọn `Continue`.

![05](https://github.com/PurpleLover/howtoDeploy/blob/master/images/images-ios/_enterprise/05.png)

**Lưu ý**: Sau khi nhập xong thông tin, Apple sẽ liên hệ với mình để kiểm tra thông tin và gửi đường dẫn để hoàn tất thanh toán. Thường mất từ 2 tới 4 tuần để đợi hoàn tất thủ tục.

## Cách đăng tải ứng dụng lên AppStore
(Sẽ bổ sung sau)

## Nguồn tham khảo
* [Đăng ký tài khoản bình thường](https://www.easyeasyapps.net/en/how-to-publish-app-tutorials/apple-developer)
* [Đăng ký tài khoản Enterprise](http://learn.buildfire.com/publishing/apple-specific-articles/how-to-create-an-apple-enterprise-developer-account)
* [Cách đăng ký mã D-U-N-S](http://gamestudio.vn/tin-tuc/22-goc-lap-trinh/huong-dan-chi-tiet-cach-dang-ky-tai-khoan-apple-developer-de-submit-ung-dung-len-appstore-714.html)