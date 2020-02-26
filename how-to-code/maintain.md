# Hướng dẫn bảo trì react-native repo

## Giới thiệu

Sau khi đã xây dựng xong 1 app và up lên app store các thứ, thì giai đoạn gian nan tiếp theo là bảo trì.

## Điều kiện tiên quyết

1. Thành thạo JS, có tư duy lập trình, biết dùng máy vi tính
2. Có hiểu biết về react-native
3. Phải có repo react-native chạy được

## Phương thức bảo trì

Bảo trì có thể bao gồm refactor (thu gọn, làm mịn) hoặc tái sử dụng lại repo.

### Làm mịn

Trước hết, hãy tạo ra một nhánh trên bộ kiểm soát phiên bản mà bạn đang dùng. Sau đó làm mịn trên nhánh đó, chỉ gộp lại vào nhánh chính sau khi đã căn chỉnh xong xuôi, tránh động vào các thư viện vì có thể gây xung đột với nhánh chính.

### Tái sử dụng repo (Fork)

Xuất phát từ nhu cầu tái sử dụng lại các đoạn code, các đoạn chỉnh sửa thư viện để giảm bớt thời gian đau đầu căn chỉnh, dò lỗi trên Google, Fork đã ra đời.

Fork có thể hiểu đơn giản là bạn duplicate lại repo (folder chứa code) hiện tại và làm việc với nó cho một dự án mới.

Để đảm bảo bản duplicate là một cái app hoàn toàn mới, bạn cần phải tinh chỉnh một số thứ như bên dưới.

Việc tạo ra logo nên sử dụng XD.

#### Với iOS

Đổi `Bundle Name` trong XCode. Để quá trình đẩy lên store được mượt mà, bạn còn phải đổi cả `Bundle Indentifier` nữa.

Vào thư mục `Images.casset`, đổi lại logo. Kích thước của logo đều được định sẵn trong file.

#### Với Android

Đổi `applicationId` trong `build.gradle`.

**Lưu ý**: Chỉ thay đổi `applicationId`, giữ nguyên `packageName` (chẳng hạn `com.companyName.oldRepoName`)

Đổi lại hình logo trong thư mục `/android/app/src/main/res`, kích thước được định nghĩa theo bảng sau.

Tên | Kích thước (đơn vị Pixel)
--- | ---
LDPI | 36 x 36
MDPI | 48 x 48
TVDPI | 64 x 64
HDPI | 72 x 72
XHDPI | 96 x 96
XXHDPI | 144 x 144
XXXHDPI | 192 x 192

Gen lại file để ký số, cách làm [như sau](https://reactnative.dev/docs/0.59/running-on-device)

#### Firebase Messaging

Nếu bạn sử dụng Google Firebase để làm thông báo đẩy (Push Notification), bạn phải thực hiện các bước sau:

- Đăng nhập vào Google Console, cài đặt Firebase mới hoặc lấy luôn ứng dụng đang chạy.
- Chọn Add App (thêm ứng dụng), chọn iOS hoặc/ và Android
- Thiết lập BundleId/ ApplicationId và điền form theo yêu cầu
- Tải lại `googleInfoService` và thay thế cái tương tự trong thư mục android/ ios trong repo

## Tham khảo

* [Kích thước ảnh cho Android](https://stackoverflow.com/questions/12768128/android-launcher-icon-size)