# Hướng dẫn code react-native đại cương

## Mục lục

1. [Giới thiệu](#Giới-thiệu)
2. [Điều kiện tiên quyết](#Điều-kiện-tiên-quyết)
3. [Cài đặt](#Cài-đặt)
4. [Cách thức code](#Cách-thức-code)
5. [Tham khảo](#Tham-khảo)

## Giới thiệu

Bài viết này tổng hợp tài liệu và cách thức để xây dựng ứng dụng cho thiết bị di động, dựa trên React-native. Bài viết này chủ yếu tổng hợp dựa trên [Tài liệu của React-Native](https://reactnative.dev/docs/0.59/getting-started).

## Điều kiện tiên quyết

1. Biết sử dụng máy tính, có tư duy lập trình.
2. Nếu phát triển ứng dụng chạy trên thiết bị của Apple thì **nên** có máy Mac (có thể xem xét sử dụng máy ảo trên Windows hoặc Linux để chạy)
3. Máy tính đang dùng có ít nhất 8GB RAM trở lên vì phải chạy máy ảo
4. Thành thạo ngôn ngữ JavaScript
5. Kiên nhẫn

**Lời khuyên**: Nên cài đặt một công cụ Editor như VS Code, Atom... thay vì sử dụng IDE.

## Cài đặt và khởi chạy

Mình khuyên dùng `react-native-cli` thay cho `expo-cli`, vì ít lỗi linh tinh và đã được battle-test từ cộng đồng rất nhiều. Sau đây là hướng dẫn cho từng hệ điều hành (chưa test trên Linux nên chưa viết).

### Windows

Với Windows thì chỉ có thể chạy được Android.
#### 1. Cài đặt các thành phần

Đầu tiên, ta phải cài đặt [`chocolatey`](https://chocolatey.org/install). Các bước cài đặt như sau:

1. Mở Window PowerShell (Administrator) bằng cách nhấn tổ hợp phím Window + X
2. Copy `Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))` vào PowerShell và nhấn Enter
3. Đợi cho tiến trình cài đặt xong
4. Kiểm tra cài đặt, bằng cách gõ lệnh `choco` vào PowerShell

Sau khi cài đặt xong `chocolatey`, ta phải cài tiếp node, python2 và Java SE Development Kit (JDK). Vẫn trên PowerShell đó, copy lệnh `choco install -y nodejs.install python2 jdk8` vào và nhấn Enter.

#### 2. Cài đặt Android Studio

Trong lúc chờ cài đặt 3 thằng trên, hãy cài đặt [Android Studio](https://developer.android.com/studio/index.html). Lúc này một hộp thoại sẽ mở lên để bạn chọn những thứ muốn cài cũng như đường dẫn cài đặt, cứ bấm next và finish thôi.

Sau khi Android Studio kia chạy xong thì nó sẽ mở bảng thiết lập, chọn Custom, đảm bảo tích hết 4 thằng sau:

- `Android SDK`
- `Android SDK Platform`
- `Performance (Intel ® HAXM)`
- `Android Virtual Device`

Rồi bấm next và đợi cài dặt.

#### 3. Cài đặt Android SDK

Sau khi cài đặt xong xuôi Android Studio, sẽ có một hộp thoại "Welcome to Android Studio", nhấn vào "Configure" và chọn "SDK Manager".

Chọn tab "SDK Platforms", nhớ nhấn vào "Show Package Details". Tìm đến `Android 9 (Pie)` và đảm bảo tích chọn 2 thằng sau:

- `Android SDK Platform 28`
- `Intel x86 Atom_64 System Image` hoặc `Google APIs Intel x86 Atom System Image`

Tiếp đến, chọn tab "SDK Tools", nhớ nhấn vào "Show Package Details". Tìm đến `Android SDK Build-Tools` và chọn phiên bản `28.0.3`.

Cuối cùng, nhấn nút "Apply" và chọn tải toàn bộ những phần đã chọn. Nếu có hộp thoại nào hỏi quyền thì cứ accept hết.

#### 4. Chỉnh path

Chuột phải vào `This PC` chọn Properties. Chọn nút "Advanced system settings".

Chọn tab "Advanced" và chọn nút "Environment Variables..."

Ở bảng "User variables...", chọn nút "New". Nhập `ANDROID_HOME` vào "Variable name" và đường dẫn vào Android SDK (thường có dạng `c:\Users\tên_người_dùng\AppData\Local\Android\Sdk`) vào "Variable Value". Sau đó nhấn OK.

Ở bảng "System variables", chọn thuộc tính "Path" và nhấn nút "Edit". Sau đó chọn nút "New" và dán đường dẫn vào platform-tools (thường có dạng `c:\Users\YOUR_USERNAME\AppData\Local\Android\Sdk\platform-tools`). Sau đó nhấn OK. Và làm tương tự với thuộc tính "Path" ở "User variables".

#### 5. Cài đặt react-native-cli

Mở PowerShell hoặc Command Prompt bằng quyền Administrator. Gõ lệnh `npm i react-native-cli -g`.

Sau đó mở "Visual Studio Code" bằng quyền Administrator. Kéo folder mà bạn mong muốn chứa code vào và mở terminal trên Visual Studio Code lên.

Gõ lệnh `react-native init AwesomeProject` (bạn có thể thay "AwesomeProject" bằng bất cứ tên nào bạn muốn đặt). Chờ tiến trình chạy xong là bạn có repo mới chạy react-native rồi.

#### 6. Chạy thử

Bạn có thể chạy thử trên thiết bị ảo hoặc thiết bị thật.

**Lời khuyên**: nên chạy trên thiết bị thật để test được nhiều thứ và để giảm bớt gánh nặng cho máy tính.

Nếu muốn chạy trên thiết bị thật:

1. Bật chế độ "Developer" (nhà phát triển) trên điện thoại của bạn - bằng cách nhấn liên tục vào thông số bản Build trong phần Setting/About
2. Kết nối thiết bị với máy tính qua cổng USB
3. Vào project vừa tạo bằng Visual Studio Code (nhớ mở bằng Administrator) và viết lệnh sau vào terminal `react-native run-android`
4. Nếu thiết bị báo lỗi không kết nối được với developvement server thì mở PowerShell bằng quyền Administrator. Sau đó gõ lệnh `adb reverse tcp:8081 tcp:8081`. Rồi tắt hết server node đang chạy và làm lại bước 3.

Nếu muốn chạy trên thiết bị ảo:

1. Khởi động Android Studio, chọn "Open Existing Project..."
2. Trỏ vào thư mục android trong project bạn vừa tạo
3. Nhấn vào nút "AVD Manager" và chọn "Create Virtual Device...", chọn một điện thoại bất kỳ và bấm "Next", rồi chọn "Pie API Level 28"

Nếu không "Create Virtual Device..." được do thiếu "HAXM". Vào [trang này](https://github.com/intel/haxm/releases) và tải bản zip cho windows về và tự cài. Sau đó mở lại "AVD Manager" là được.

4. Sau khi thiết lập xong thiết bị, bấm nút tam giác màu xanh để khởi chạy
5. Vào project vừa tạo bằng Visual Studio Code (nhớ mở bằng Administrator) và viết lệnh sau vào terminal `react-native run-android`
6. Nếu vẫn gặp sự cố thì xem lại cách thiết lập như phần trên

### macOS

Với macOS thì chạy được cả Android lẫn iOS.

## Cách thức code

Các bạn nên tham khảo theo hướng dẫn trong mục tham khảo. Tuy nhiên có vài thứ mình cần phải viết nhanh để bạn hiểu trước về react-native (gần như không khác gì reactJS).

Đầu tiên, React-native không phải là bộ sinh code, nó được phát triển trên nền của các code native (C-Objective, Java...), nên sẽ rất khó trả lời câu hỏi về hiệu năng (tót nhất là đừng làm gì sáng tạo hơn những luật mà react-native đã đề ra và khuyên dùng)

Tiếp đến, react-native (hoặc reactJS) tổ chức các thành phần tạo nên app là `component` (View, Text... đều là component, và kể cả các class mà người dùng tự định nghĩa - nếu chọn `extends React.Component` thì cũng tính là component).

Trong component thì thường có hai thằng, `props` và `state`.

- `props` là dữ liệu được truyền từ ngoài vào, không thay đổi
- `state` là dữ liệu thay đổi

Tuỳ theo mục đích sử dụng mà dùng props hay state. Chẳng hạn, muốn tính xem người dùng bấm một nút bao nhiêu lần và biểu thị lên màn hình thì dùng `state`.

**Lưu ý**: Dữ liệu ở đây bao hàm rất rộng, từ những dữ liệu nguyên thuỷ như String, Number, đến các Component hoặc Function.

Sau đấy là `style`. Khác với ứng dụng nền web, style trong react-native buộc phải dùng theo kiểu JSX thay cho CSS. Chả hạn:

```
// với CSS
body {
  padding-left: 40px;
}

// với JSX
const styles = StyleSheet.create({
  body: {
    paddingLeft: 40,
  },
});
```

Làm như này thì có thể gây ra khó khăn khi muốn tái sử dụng. Bởi vậy mình lại khuyên bạn chỉ style cho component, và tái sử dụng component thay vì tái sử dụng style (nếu chỉnh sửa style này ở chỗ nọ sẽ gây ra những thay đổi không đáng có ở chỗ khác).

Sau cùng là cách viết các hàm bên trong một class. Mỗi tài liệu học lại có một cách viết hàm riêng, có thằng viết là `increaseCount = () => {}` theo kiểu Arrow Function, có thằng lại viết `function increaseCount(){}` rồi bind this các thứ. 

Vậy đâu là chuẩn? Câu trả lời là cách nào cũng đúng, bạn muốn viết theo quy chuẩn nào thì viết, nhưng mình thích kiểu hàm mũi tên (Arrow Function) hơn vì bạn sẽ đỡ tay bind các thứ. Lý giải ngắn gọn là `this` trong JS (khác với Java hay C#), sẽ trỏ về thằng gọi hàm; bởi vậy khi viết theo kiểu function truyền thống, bạn phải bind để this trỏ đúng, còn Arrow Function thì nó đã bind ngay từ lúc khởi chạy rồi.

**Lời khuyên**: Nên bắt đầu bằng cách cài đặt như tài liệu, và làm theo tutorial thay vì đọc tài liệu. Hãy coi tài liệu mà react-native viết ra là một cái từ điển, khi nào cần gì thì lên đấy tra (hoặc vào thẳng trong react-native trên code để đọc hiểu nếu não đủ to).

## Tham khảo

### Tài liệu chuẩn (Documentation)

* [Tài liệu chuẩn của React-Native](https://reactnative.dev/docs/0.59/getting-started)
* [Tài liệu chuẩn của Redux](https://redux.js.org/introduction/getting-started)

### Tài liệu học (Tutorial)

* [Hướng dẫn dựng một ứng dụng (tiếng Anh)](https://www.raywenderlich.com/485-react-native-tutorial-building-ios-apps-with-javascript)
* [Hướng dẫn áp dụng Redux trong React-native (tiếng Việt)](https://youtu.be/16ACnNoxCNM)
