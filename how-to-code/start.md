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
2. Nếu phát triển ứng dụng chạy trên thiết bị của Apple thì bắt buộc phải có Mac (có thể là Macbook, iMac, Mac desktop tuỳ theo điều kiện tài chính của bản thân).
3. Máy tính không quá yếu
4. Thành thạo ngôn ngữ JavaScript
5. Kiên nhẫn

**Lời khuyên**: Nên cài đặt một công cụ Editor như VS Code, Atom... thay vì sử dụng IDE.

## Cài đặt

Người viết bài khuyên dùng `react-native-cli` thay cho `expo-cli`, vì kinh nghiệm làm việc của người viết bài chỉ gắn tới thằng đầu tiên.

React-native là framework chạy trên Node vì thế bạn cần cài đặt được Node, đi kèm với Node là trình quản lý NPM.

Với các bạn dùng macOS thì khuyên dùng sử dụng [homebrew](https://brew.sh/), với Windows thì dùng [choco](https://chocolatey.org/) để cài đặt node. Và tiếp đó dùng npm để cài đặt react-native-cli.

Chi tiết các bước thực hiện xem [tại đây](https://reactnative.dev/docs/0.59/getting-started).

**Lưu ý**: Với các bạn nào dùng macOS thì nên cài thêm XCode phiên bản mới nhất để hỗ trợ được hệ máy mới cũng như build và đẩy lên App Store. Nếu chỉ muốn chạy thử trên máy ảo thì có thể tham khảo [GenyMotion](https://www.genymotion.com/) thay vì cài đặt Android Studio (vì thằng này vừa nặng vừa chiếm dụng nhiều tài nguyên).

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