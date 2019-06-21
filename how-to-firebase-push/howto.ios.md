# Hướng dẫn kết nối với Firebase trên iOS

Vào thời điểm viết bài này, người viết bài đang chuyển từ thư viện `FCM` sang `react-native-firebase` để áp dụng được tính năng thông báo đẩy (Push Notification). Tuy nhiên, cách setup Firebase trên code không khác gì so với hướng dẫn chính thức từ chính Google Firebase cả. Bài viết này để ghi chú lại từng bước thực hiện, nhằm tránh gây sốc phản vệ. Thôi lảm nhảm thế đủ rồi, bắt đầu nào.

## Chuẩn bị

Để deploy một app iOS trên App Store, bạn sẽ cần có tài khoàn Developer (cá nhân mất tầm $100/năm, còn doanh nghiệp là $300/năm - hút máu thì vãi cứt). Tôi sẽ không hướng dẫn bạn tạo và sử dụng tiền của mình bởi tôi đã ghi chú lại nó trong một bài viết khác, bạn có thể tìm thấy trong repo này.

Để bắt đầu, bạn cần phải cấu hình một số thứ sau trên trang [Apple Dev](https://developer.apple.com)

* Identifier của ứng dụng, chứa Bundle ID, ví dụ `com.Ant.PokemonGO`
* APN Key, sau khi Gen xong thì tải về, đặt vào một chỗ để chuẩn bị tải lên cho bước sau. Cái này chỉ Gen **Một lần duy nhất**.

Sau khi cấu hình xong, hãy vào Xcode của mình, mục `Capacities`, bật 2 thằng sau

* Push Notification
* Background -> Remote Notification

Một thằng sẽ phụ trách việc đẩy thông báo khi bạn online (bật app) và một cái khi bạn méo bật app (như Doulingo chửi chết con mẹ đứa nào không chịu học tiếng Nhật chả hạn).

Bạn sẽ cần có một tài khoản Google Dev, chỉ cần Free thôi, chủ yếu có thể kích hoạt Firebase. Sau đó Add thêm app mới,

- đảm bảo `Bundle ID` trùng khớp với Bundle ID mà bạn đã đăng ký trên trang Apple Dev.
- nhớ nhập thêm `Team ID` của ứng dụng

Sau đó cứ làm theo hướng dẫn của nó thôi, nhớ tải file và gắn vào đúng chỗ nhé. Tiếp đến vào `Cloud Messaging`, chọn app đã tạo và Upload cục kia lên.

## Gắn Firebase lên Project

### Bước 1

Đặt `GoogleInfo.plist` vào cạnh `Info.plist` trong Xcode. Chỉ cần kéo thả và chọn Okay khi cần thôi.

### Bước 2

Thêm dòng sau vào Podfile

`pod 'Firebase/Messaging', '~> 5.3.0'`

### Bước 3

...


## Tham khảo

Hướng dẫn cài đặt từng bước của React-native-firebase

* [Bắt đầu](https://rnfirebase.io/docs/v4.3.x/installation/ios)
* [Gửi thông điệp](https://rnfirebase.io/docs/v4.3.x/messaging/ios)
* [Thông báo](https://rnfirebase.io/docs/v4.3.x/notifications/ios)

Hướng dẫn cấu hình trên Firebase

* [Chi tiết](https://firebase.google.com/docs/cloud-messaging/ios/client)