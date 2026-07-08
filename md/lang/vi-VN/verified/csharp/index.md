<!-- Bản dịch này được tạo bởi ChatGPT và nên được một người dịch xem xét lại. -->
<!-- Hãy xóa các dòng này trong pull request sau khi bản dịch đã được xác minh. -->

# Chi tiết xác minh

## C#

### Tổng quan

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Ngôn ngữ lập trình C# đã được verified theo các đặc tả FDEFSPEC (Rev. 1) và FRELSPEC (Rev. 1) tính đến ngày 7 tháng 7 năm 2026.

#### Tuyên bố thiện chí

Chúng tôi tin một cách thiện chí rằng ngôn ngữ lập trình C# có thể biểu diễn hợp lý các khái niệm và điều khoản được định nghĩa trong các đặc tả sau, và có thể được dùng để implement các hệ thống tuân thủ những đặc tả này.

#### Giả định review

This review assumes modern C# and .NET support where version-dependent features are noted.

### Cảnh báo

* CP1252 support is available through the official .NET code pages provider, but may require provider registration or an additional package depending on the target runtime.
* Unsafe pointer behavior may require explicit unsafe authorization.

### Lỗi không đạt

* Không tìm thấy failure FDEFSPEC hoặc FRELSPEC nào đã biết trong quá trình verification này.

### Xác minh FDEFSPEC

#### Số học

| Điều khoản | Đã xác minh | Ghi chú                                   |
| --------- | -------- | --------------------------------------- |
| Bit       | ⚠️       | Không có kiểu số 1 bit; cần mở rộng.                |
| Nibble    | ⚠️       | Không có kiểu số 4 bit; cần mở rộng.                |
| Byte      | ✅        | Được hỗ trợ thông qua `byte` and `sbyte`.   |
| Short     | ✅        | Được hỗ trợ thông qua `short` and `ushort`. |
| Int       | ✅        | Được hỗ trợ thông qua `int` and `uint`.     |
| Long      | ✅        | Được hỗ trợ thông qua `long` and `ulong`.   |
| Float     | ✅        | Được hỗ trợ thông qua `float`.              |
| Double    | ✅        | Được hỗ trợ thông qua `double`.             |
| Boolean   | ✅        | Được hỗ trợ thông qua `bool`.               |

#### Mã hóa văn bản

| Điều khoản | Đã xác minh | Ghi chú                                  |
| --------- | -------- | -------------------------------------- |
| Codepoint | ✅        | Được hỗ trợ thông qua numerics and `Rune`. |
| ASCII     | ✅        | Được hỗ trợ thông qua `Encoding.ASCII`.    |
| CP1252    | ⚠️       | Yêu cầu code pages provider.          |
| UTF-8     | ✅        | Được hỗ trợ thông qua `Encoding.UTF8`.     |
| UTF-16LE  | ✅        | Được hỗ trợ thông qua `Encoding.Unicode`.  |

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

| Điều khoản | Đã xác minh | Ghi chú                                        |
| --------- | -------- | -------------------------------------------- |
| Set       | ✅        | Được hỗ trợ thông qua `HashSet<T>`.              |
| Map       | ✅        | Được hỗ trợ thông qua `Dictionary<TKey,TValue>`. |
| Array     | ✅        | Array native được hỗ trợ.                 |
| File      | ✅        | Được hỗ trợ thông qua file APIs.                 |
| Stream    | ✅        | Được hỗ trợ thông qua `Stream`.                  |

#### Bộ nhớ

| Điều khoản | Đã xác minh | Ghi chú                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Được hỗ trợ thông qua references and pointers. |
| Pointer   | ✅        | Được hỗ trợ thông qua unsafe pointers.         |
| Variable  | ✅        | Variable được hỗ trợ.                   |
| Constant  | ✅        | Được hỗ trợ thông qua `const` and `readonly`.  |

#### Operation

| Provision   | Verified | Notes                                  |
| ----------- | -------- | -------------------------------------- |
| Instruction | ✅        | Represented through IL and operations. |
| Procedure   | ✅        | Được hỗ trợ thông qua `void` methods.      |
| Function    | ✅        | Được hỗ trợ thông qua returning methods.   |

#### Luồng

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Được hỗ trợ thông qua application and `Process` APIs. |
| Thread     | ✅        | Được hỗ trợ thông qua `Thread`.                       |
| Dispatcher | ✅        | Được hỗ trợ thông qua tasks and schedulers.           |

#### Composite

| Điều khoản | Đã xác minh | Ghi chú                              |
| --------- | -------- | ---------------------------------- |
| Member    | ✅        | Type members are supported.        |
| Object    | ✅        | Object được hỗ trợ.             |
| Field     | ✅        | Field được hỗ trợ.              |
| Method    | ✅        | Method được hỗ trợ.             |
| Property  | ✅        | Property được hỗ trợ native. |
| Structure | ✅        | Structure được hỗ trợ native. |
| Class     | ✅        | Class được hỗ trợ.             |
| Interface | ✅        | Interface được hỗ trợ.          |
