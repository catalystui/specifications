<!-- Bản dịch này được tạo bởi ChatGPT và nên được một người dịch xem xét lại. -->
<!-- Hãy xóa các dòng này trong pull request sau khi bản dịch đã được xác minh. -->

# Chi tiết xác minh

## Java

### Tổng quan

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Ngôn ngữ lập trình Java đã được verified theo các đặc tả FDEFSPEC (Rev. 1) và FRELSPEC (Rev. 1) tính đến ngày 7 tháng 7 năm 2026.

#### Tuyên bố thiện chí

Chúng tôi tin một cách thiện chí rằng ngôn ngữ lập trình Java có thể biểu diễn hợp lý một phần lớn các khái niệm và điều khoản được định nghĩa trong các đặc tả sau, và có thể được dùng để implement các hệ thống tuân thủ những đặc tả này.

#### Giả định review

This review assumes modern Java language support where version-dependent features are noted. Features such as local variable inference, records, and foreign memory access may require later Java versions.

### Cảnh báo

* Java does not have native support for unsigned numeric types, which may require widening or alternative representations for certain provisions.
* Direct memory address and pointer-style behavior may require Java 22+ Foreign Function and Memory API support.
* Java does not have native property syntax, requiring getter and setter methods instead.

### Lỗi không đạt

* Java does not provide CP1252 as a guaranteed standard charset, requiring implementation-specific support, additional libraries, or custom handling for full compliance.
* Java properties do not provide an explicit keyed member backed by a required Get/Set accessor map.

### Xác minh FDEFSPEC

#### Số học

| Điều khoản | Đã xác minh | Ghi chú                                            |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | Không có kiểu số 1 bit; cần mở rộng.                         |
| Nibble    | ⚠️       | Không có kiểu số 4 bit; cần mở rộng.                         |
| Byte      | ⚠️       | Signed 8-bit only; widen for unsigned.           |
| Short     | ⚠️       | Signed 16-bit only; widen for unsigned.          |
| Int       | ⚠️       | Signed 32-bit; unsigned helpers require Java 8+. |
| Long      | ⚠️       | Signed 64-bit; unsigned helpers require Java 8+. |
| Float     | ✅        | 32-bit floating point is supported.              |
| Double    | ✅        | 64-bit floating point is supported.              |
| Boolean   | ✅        | Boolean type is supported.                       |

#### Mã hóa văn bản

| Điều khoản | Đã xác minh | Ghi chú                                    |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | Được hỗ trợ thông qua `int` and `Character`. |
| ASCII     | ✅        | Charset chuẩn được bảo đảm.             |
| CP1252    | ❌        | Không được bảo đảm bởi `StandardCharsets`.    |
| UTF-8     | ✅        | Charset chuẩn được bảo đảm.             |
| UTF-16LE  | ✅        | Charset chuẩn được bảo đảm.             |

#### Trạng thái thao tác

| Điều khoản | Đã xác minh | Ghi chú                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | Có thể được biểu diễn bằng a custom type.        |
| Context   | ✅        | Có thể được biểu diễn bằng a custom value.       |
| Operation | ✅        | Có thể được biểu diễn bằng a custom value.       |
| Detail    | ✅        | Có thể được biểu diễn bằng a custom value.       |
| Result    | ✅        | Có thể được biểu diễn bằng a custom return type. |

### Xác minh FRELSPEC

#### Collection

| Điều khoản | Đã xác minh | Ghi chú                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Được hỗ trợ thông qua `Set`.       |
| Map       | ✅        | Được hỗ trợ thông qua `Map`.       |
| Array     | ✅        | Array native được hỗ trợ.   |
| File      | ✅        | Được hỗ trợ thông qua file APIs.   |
| Stream    | ✅        | Được hỗ trợ thông qua stream APIs. |

#### Bộ nhớ

| Điều khoản | Đã xác minh | Ghi chú                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | Direct addresses require Java 22+ FFM.                         |
| Pointer   | ⚠️       | Pointer-like access requires Java 22+ FFM.                     |
| Variable  | ✅        | Declarations and `var` are supported; `var` requires Java 10+. |
| Constant  | ✅        | Được hỗ trợ thông qua `final`.                                     |

#### Operation

| Provision   | Verified | Notes                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | Represented through bytecode and operations. |
| Procedure   | ✅        | Được hỗ trợ thông qua `void` methods.            |
| Function    | ✅        | Được hỗ trợ thông qua returning methods.         |

#### Luồng

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Được hỗ trợ thông qua application and `Process` APIs. |
| Thread     | ✅        | Được hỗ trợ thông qua `Thread`.                       |
| Dispatcher | ✅        | Được hỗ trợ thông qua `Executor` APIs.                |

#### Composite

| Điều khoản | Đã xác minh | Ghi chú                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | Class members are supported.           |
| Object    | ✅        | Object được hỗ trợ.                 |
| Field     | ✅        | Field được hỗ trợ.                  |
| Method    | ✅        | Method được hỗ trợ.                 |
| Property  | ❌        | Không có accessor map tường minh.              |
| Structure | ✅        | Được hỗ trợ thông qua records; Java 16+.   |
| Class     | ✅        | Class được hỗ trợ.                 |
| Interface | ✅        | Interface được hỗ trợ.              |
