<!-- Bản dịch này được tạo bởi ChatGPT và nên được một người dịch xem xét lại. -->
<!-- Hãy xóa các dòng này trong pull request sau khi bản dịch đã được xác minh. -->

# Chi tiết xác minh

## C++

### Tổng quan

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Ngôn ngữ lập trình C++ đã được verified theo các đặc tả FDEFSPEC (Rev. 1) và FRELSPEC (Rev. 1) tính đến ngày 7 tháng 7 năm 2026.

#### Tuyên bố thiện chí

Chúng tôi tin một cách thiện chí rằng ngôn ngữ lập trình C++ có thể biểu diễn hợp lý các khái niệm và điều khoản được định nghĩa trong các đặc tả sau, và có thể được dùng để implement các hệ thống tuân thủ những đặc tả này.

#### Giả định review

This review assumes modern standard C++ support where version-dependent features are noted. Exact-width integer support assumes the corresponding `<cstdint>` types are provided by the implementation.

This review treats C++ as a systems programming language with direct support for low-level representation, object modeling, memory control, generic programming, and concurrent execution.

### Cảnh báo

* Exact-width integer types depend on implementation support.
* CP1252 can be represented byte-for-byte, but no named standard codec is provided.
* UTF-16LE serialization requires explicit byte-order handling.
* Some concurrency and character features require modern C++ revisions.

### Lỗi không đạt

* Không tìm thấy failure FDEFSPEC hoặc FRELSPEC nào đã biết trong quá trình verification này.

### Xác minh FDEFSPEC

#### Số học

| Điều khoản | Đã xác minh | Ghi chú                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Use bit-fields or masks.                    |
| Nibble    | ⚠️       | Use bit-fields or masks.                    |
| Byte      | ✅        | Được hỗ trợ thông qua `std::byte`.              |
| Short     | ✅        | Được hỗ trợ thông qua `int16_t` and `uint16_t`. |
| Int       | ✅        | Được hỗ trợ thông qua `int32_t` and `uint32_t`. |
| Long      | ✅        | Được hỗ trợ thông qua `int64_t` and `uint64_t`. |
| Float     | ✅        | Được hỗ trợ thông qua `float`.                  |
| Double    | ✅        | Được hỗ trợ thông qua `double`.                 |
| Boolean   | ✅        | Được hỗ trợ thông qua `bool`.                   |

#### Mã hóa văn bản

| Điều khoản | Đã xác minh | Ghi chú                                |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | Được hỗ trợ thông qua `char32_t`.        |
| ASCII     | ✅        | Có thể biểu diễn dưới dạng byte values.        |
| CP1252    | ⚠️        | Yêu cầu explicit byte mapping.      |
| UTF-8     | ✅        | Được hỗ trợ thông qua `char8_t`; C++20+. |
| UTF-16LE  | ⚠️        | Yêu cầu byte-order handling.        |

#### Trạng thái thao tác

| Điều khoản | Đã xác minh | Ghi chú                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | Có thể được biểu diễn bằng an enum.           |
| Context   | ✅        | Có thể được biểu diễn bằng a value.           |
| Operation | ✅        | Có thể được biểu diễn bằng a value.           |
| Detail    | ✅        | Có thể được biểu diễn bằng a value.           |
| Result    | ✅        | Có thể được biểu diễn bằng a struct or class. |

### Xác minh FRELSPEC

#### Collection

| Điều khoản | Đã xác minh | Ghi chú                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | Được hỗ trợ thông qua `std::set`.              |
| Map       | ✅        | Được hỗ trợ thông qua `std::map`.              |
| Array     | ✅        | Được hỗ trợ thông qua arrays and `std::array`. |
| File      | ✅        | Được hỗ trợ thông qua file streams.            |
| Stream    | ✅        | Được hỗ trợ thông qua iostreams.               |

#### Bộ nhớ

| Điều khoản | Đã xác minh | Ghi chú                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Addresses are supported.                   |
| Pointer   | ✅        | Pointers are supported.                    |
| Variable  | ✅        | Variable được hỗ trợ.                   |
| Constant  | ✅        | Được hỗ trợ thông qua `const` and `constexpr`. |

#### Operation

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Represented through machine operations. |
| Procedure   | ✅        | Được hỗ trợ thông qua `void` functions.     |
| Function    | ✅        | Được hỗ trợ thông qua returning functions.  |

#### Luồng

| Provision  | Verified | Notes                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | Được hỗ trợ thông qua hosted execution.      |
| Thread     | ✅        | Được hỗ trợ thông qua `std::thread`; C++11+. |
| Dispatcher | ✅        | Được hỗ trợ thông qua async and schedulers.  |

#### Composite

| Điều khoản | Đã xác minh | Ghi chú                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | Class members are supported.            |
| Object    | ✅        | Object được hỗ trợ.                  |
| Field     | ✅        | Field được hỗ trợ.                   |
| Method    | ✅        | Method được hỗ trợ.                  |
| Property  | ✅        | Get/Set maps can be represented.        |
| Structure | ✅        | Structure được hỗ trợ native.      |
| Class     | ✅        | Classes are natively supported.         |
| Interface | ✅        | Có thể được biểu diễn bằng abstract classes. |
