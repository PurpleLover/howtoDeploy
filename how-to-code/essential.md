# Tổng hợp ghi chú

## Lời nói đầu

Đây là ghi chép tổng hợp lại về react, có thể xem thêm tài liệu chính thức để biết thêm.

## Component

Hệ thống trong React cấu thành từ nhiều `component`.

Các component trong React có thể viết theo dạng `class` hoặc `hooks` (dạng arrow function).

Chẳng hạn với kiểu `class`,

```
class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      //define your state here
    }
  }

  innerFunction = () => {
    //write function you wanna run in this component
  }

  render() {
    return (
      //write components you wanna render here
    );
  }
}
```

Với kiểu `hooks`, vào thời điểm viết bài này, mình không có kinh nghiệm làm việc với kiểu này. Nếu cần thì viết theo `class` vẫn có hệ thống và quản lý tiện hơn.

Ngoài ra, `React.Component` cung cấp một số function có sẵn cho component, có thể xem thêm [tại đây](https://reactjs.org/docs/react-component.html). Các function này sẽ giúp bạn chạy các lệnh vào các thời điểm khác nhau trong vòng đời của component.

## state và props

props là giá trị bất kỳ (abitrary) mà component nhận vào, thường được truyền từ ngoài vào.

state là cũng tương tự như props, nhưng do component quản lý. 

Trong hầu hết các trường hợp, nếu state thay đổi thì component sẽ render lại.

Chẳng hạn, bạn có một class như sau:

```
class LoadingComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      isVisible: true,
      title: props.title,
    };
  }

  componentDidMount() {
    setTimeout(this.turnLoadingOff, 3000);
  }

  turnLoadingOff = () => {
    this.setState({
      isVisible: false,
    });
  }

  render() {
    return (
      <View>
        <Modal
          animationType="slide"
          transparent={false}
          visible={this.state.isVisible}
        >
          <ActivityIndicator size="large" />
          <View>
            <Text>{this.state.title}</Text>
          </View>
        </Modal>
      </View>
    );
  }
}
```

Như trong ví dụ, class trên có state là `isVisible`, state này sẽ thay bị thay đổi thành false 3 giây sau khi component render xong.

Trong khi đó, `title` được truyền từ ngoài vào, tức là ta sẽ không thay đổi được giá trị này, mà chỉ có thể thay đổi sau khi gán lại cho một biến khác - như trong ví dụ, tôi gán cho biến `state.title`.

Nói một cách dễ hiểu, component này tạo ra một cái hình ảnh xoay xoay để tạo cảm giác cho người dùng là mọi thứ đang chạy. Nó nhận vào một tiêu đề để render ra màn hình. Và sau 3 giây thì hình ảnh xoay xoay sẽ biến mất.

Chẳng hạn, tái sử dụng lại component trên ở một chỗ khác.

```
import LoadingComponent from './components/LoadingComponent';

class LoginScreen extends React.Component {
  render() {
    return(
      <View>
        <LoadingComponent title="What is love?" />
      </View>
    );
  }
}
```

## conditional rendering

Đôi khi bạn muốn render theo điều kiện mình đặt ra. Chẳng hạn với _LoadingComponent_ phía trên, nếu maintainer của bạn trong một phút bất cẩn không truyền vào giá trị nào hoặc là truyền vào cái bạn không muốn thì sao?

Lúc này chắc hẳn bạn sẽ muốn kiểm tra giá trị đầu vào, bằng không màn hình sẽ render ra một cục null to đùng hoặc một giá trị nào đấy không đúng như bạn tưởng.

```
render() {
  return (
    {
      this.state.title && <Text>{this.state.title}</Text>
    }
  )
}
```

Đó là cách bạn thực hiện render theo điều kiện. Câu lệnh trên sẽ thực hiện như sau, nó sẽ kiểm tra xem `this.state.title` có giá trị hay là null hay không. Nếu điều kiện trả về true, nó sẽ thực hiện lệnh tiếp sau. Nếu điều kiện trả về false, nó sẽ bị bỏ qua.

**Lưu ý 1**: Conditional Rendering chỉ hỗ trợ các toán tử, không hỗ trợ lệnh như `if else`. Các toán tử hay dùng có thể là toán tử 3 ngôi (?:), toán tử logic (&& hoặc ||). Xem thêm về các toán tử [tại đây](https://developer.mozilla.org/vi/docs/Web/JavaScript/Guide/Expressions_and_Operators).

**Lưu ý 2**: không phải lúc nào cũng nên viết như trên. Đặc biệt đối với hệ điều hành Android, viết như trên thì sẽ gây ra lỗi _không bọc văn bản trong component Text_ vì component sẽ thực hiện render `this.state.title` ngay thay vì thực hiện điều kiện (với trường hợp là có giá trị). Bởi vậy để giải quyết vấn đề này, hãy thêm hai dấu `!!` trước `this.state.title` để ép cho thành kiểu Boolean nhằm thực hiện thay đổi.

## Styling

Để có một phần mềm đẹp đẽ và sắc màu thì không thể không style cho nó. Đối với phần mềm nền Web, ta có thể dùng CSS để style cho chúng.

ReactJS có hỗ trợ css style, thông qua thuộc tính `className` khi đặt vào các thẻ. Còn React-native thì chỉ hỗ trợ JSX-style.

Cụ thể, thay vì gõ luật CSS như sau:

```
.header {
  background-color: white;
  font-size: 16px;
}
```

thì viết lại thành thế này:

```
const styles = StyleSheet.create({
  header: {
    backgroundColor: 'white',
    fontSize: 16,
  },
});
```

Ngoài ra, thay vì dùng `float` các kiểu thì React chuộng dùng `flex` và `grid` hơn.

**Ghi chú**: react có thể không hỗ trợ less, sass. Nhưng vẫn có nhiều library giúp ta làm được việc này, bạn chỉ cần google và cài đặt. Việc cài đặt có thành công hay có lỗi gì thì tôi không chịu trách nhiệm.

## API invoker

React vốn là framework frontend, vì vậy trong nhiều trường hợp, ta sẽ phải gọi lên API (thường dùng REST hoặc Graph) để lấy dữ liệu.

Việc gọi API trong React cũng tương tự dùng Ajax trong Jquery. Ta dùng lệnh:

```
fetch("your-endpoint-url", options)
```

options ở đây có thể bao gồm phương thức (get, post, put...), header (nếu server yêu cầu phải có header gửi kèm).

Dữ liệu trả về của fetch giống như ajax, đều là Promise. Hiểu nôm na thì cả hai đều chạy bất đồng bộ, và bạn phải đợi nó chạy xong thì mới trả về kết quả cho bạn.

Để hứng được kết quả, bạn có thể sử dụng `then catch` hoặc `async await`. Chẳng hạn:

```
//dùng then catch
const getSalaryInfo = () => {
  const result = fetch('/api/salary/info')
    .then(rs => rs)
    .then(rs => rs.json())
    .catch(error => console.log(error));
  console.log(result);
}

//dùng async await
const getSalaryInfo = async () => {
  const result = await fetch('/api/salary/info');
  console.log(result);
}

```

## Tham khảo

* [Tài liệu của ReactJs](https://reactjs.org/docs)
* [Tài liệu JavaScript trên MDN](https://developer.mozilla.org/vi/docs/Web/JavaScript/Guide/Using_promises)
