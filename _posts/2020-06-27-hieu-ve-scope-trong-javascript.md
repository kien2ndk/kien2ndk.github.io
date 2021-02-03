---
title: Hiểu về Scope trong Javascript
date: 2019-06-27
excerpt: Hiểu về Scope(Phạm vi) trong Javascript
categories:
  - javascript
tags:
  - javascript
  - scope
toc: true
toc_label: Đầu mục bài viết
---

## Định nghĩa
Scope đề cập tới thời gian tồn tại và quyền truy cập của một biến. Các biến không thể truy cập được từ bên ngoài scope mà chúng được khai báo.

Các loại 5 Scope trong Javascript
- Global Scope
- Module Scope
- Function Scope
- Block Scope
- Lexical Scope

## Global Scope
Các biến được định nghĩa bên ngoài tất cả các hàm hoặc dấu ngoặc nhọn`(block scope)` or `module scope` có scope là global scope.<br>
Các biến trong global scope có thể được sử dụng ở bấy kỳ đâu trong ứng dụng.

Khi khai báo một biến trong HTML bên ngoài tất cả các hàm, bạn đã tạo ra một biến toàn cục `(global variable)`.
```html
<script>
  let x = 1; // global variable
  console.log(x); // 1
</script>
```
Một biến được khai báo bên ngoài tất cả các hàm, trong bất kì tập tin nào là một biến toàn cục
Khi ứng dụng chạy, bạn có thể sử dụng tất cả các biến toàn cục, và các biến toàn cục bị huỷ khi ứng dụng ngừng chạy.

Ngoài ra bạn có thể tạo ra biến toàn cục bằng các sử dụng `window` ở bất kỳ đâu trong ứng dụng.
```javascript
window.y = 2; // global variable
```
Bạn có thể truy xuất biến `y` ở bất kỳ đâu.
```javascript
console.log(y); // 2
```
## Module scope

## Định nghĩab
Scope trong Javascript xác định những biến bạn có quyền truy cập, có 2 loại scope trong Javascript
- Global scope (Phạm vi toàn cầu)
- Local scope (Phạm vi địa phương)

## Global scope
Nếu một biến được khai báo bên ngoài tất cả các hàm hoặc dấu ngoặc nhọn `{}`, thì nó được xác định là được định nghĩa trong `global scope`. Khi bạn đã khai báo một biến toàn cầu bạn có thể sử dụng biến đó ở bất kỳ đâu trong ứng dụng.
```javascript
var x = 1;

function a() {
  console.log(x); // 1
}

a();
```

## Local scope
Trong Javascript có 2 loại `Local scope` là `Function scope` và `Block scope`
### Function scope`(Phạm vi hàm)`
Các biến khai báo bên trong hàm, chúng chỉ được truy cập từ bên trong hàm đó. Bạn không thể truy cập các biến này từ bên ngoài hàm.
```javascript
function a() {
  var x = 1;
}

a();

console.log(x); // Uncaught ReferenceError: x is not defined
```

### Blocl scope`(Phạm vi khối)`
Phạm vi khối được xác định với dấu ngoặc nhọn `{}`, các biến được khai báo với từ khoá `let` và `const` có phạm vi khối và chúng chỉ được truy cập trong khối mà chúng được xác định.
```javascript

```


## Tổng kết
- Lựa chọn dùng `const` đầu tiên
- Dùng `let` khi biến cần gán lại giá trị
- Hạn chế dùng `var`, trừ khi bạn muốn chia sẻ biến đó thông qua nhiều scope khác nhau