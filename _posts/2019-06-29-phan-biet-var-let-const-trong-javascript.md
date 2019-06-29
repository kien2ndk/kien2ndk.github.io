---
title: Phân biệt var, let, const trong Javascript
date: 2019-06-29
categories:
  - javascript
tags:
  - javascript
  - var
  - let
  - const
toc: true
toc_label: Đầu mục bài viết
---

## var
Dùng để khai báo một biến có phạm vi truy cập trong hàm chứa nó
```javascript
function a() {
  var x = 1;

  console.log(x); // 1
}

a();

console.log(x); // Throws a ReferenceError: x is not defined outside a.
```
**Chú ý:** Khi ở global scope (tức là không nằm trong một `function` nào cả), từ khoá `var` tạo ra thuộc tính mới cho global object`(this)` còn `let` thì không.<br>
{: .notice--danger}
```javascript
  var x = 1;
  let y = 2;

  console.log(this.x); // 1
  console.log(this.y); // undefined
```
Dùng `var` khai báo một biến còn có thêm tính chất hoisting<br>
**Hoisting** là khái niệm chỉ việc mọi khai báo biến với từ khoá `var` sẽ được chuyển lên trên cùng của phạm vi hiện tại.
{: .notice--danger}
Ví dụ về hoisting
```javascript
function a() {
  console.log(x); // undefined
  var x = 1;
}

a();
```
Sau khi hoisting đoạn code trên được viết lại như sau
```javascript
function a() {
  var x;
  console.log(x);
  x = 1;
}
```
## const
Dùng để khai báo một hằng số, giá trị của nó không thể thay đổi thông qua việc gán lại và phải gán giá trị lúc khai báo. Như giá trị `pi` trong toán học.
```javascript
// Lưu ý: Các hằng số có thể được khai báo bằng chữ hoa hoặc chữ thường
// nhưng như một quy ước chung là sử dụng các chữ cái viết hoa.
const PI = 3.1415;
```
Khi gán lại giá trị điều này sẽ gây ra lỗi
```javascript
const PI = 3.1415;
PI = 3.14; // Uncaught TypeError: Assignment to constant variable.
```
## let
Dùng để khai báo một biến có phạm vi khối`(block scope)`, một phạm vi khối là khu vực bên trong dấu `{}`
```javascript
let x = 1;

if (true) {
  let x = 2;
  console.log(x); // 2
}

console.log(x); // 1
```
**Chú ý:** Các biến và hằng được khai báo với từ khoá `let` và `const` không được hoisting.
{: .notice--danger}
```javascript
function a () {
  console.log(x); // Uncaught ReferenceError: Cannot access 'x' before initialization
  let x = 1;
}
```
Không thể dùng từ khoá `let` để khai báo lại cùng một biến trong cùng một phạm vi khối.
{: .notice--danger}
```javascript
if (true) {
  let x = 1;
  let x = 2; // Uncaught SyntaxError: Identifier 'x' has already been declared
}
```
## Tổng kết
- Lựa chọn dùng `const` đầu tiên
- Dùng `let` khi biến cần gán lại giá trị
- Hạn chế dùng `var`, trừ khi bạn muốn chia sẻ biến đó thông qua nhiều scope khác nhau