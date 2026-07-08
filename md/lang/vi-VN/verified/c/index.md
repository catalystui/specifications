<!-- Bản dịch này được tạo bởi ChatGPT và nên được một người dịch xem xét lại. -->
<!-- Hãy xóa các dòng này trong pull request sau khi bản dịch đã được xác minh. -->

# Chi tiết xác minh

## C

### Tổng quan

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Ngôn ngữ lập trình C đã được verified theo các đặc tả FDEFSPEC (Rev. 1) và FRELSPEC (Rev. 1) tính đến ngày 7 tháng 7 năm 2026.

#### Tuyên bố thiện chí

Chúng tôi tin một cách thiện chí rằng ngôn ngữ lập trình C có thể biểu diễn hợp lý các khái niệm và điều khoản được định nghĩa trong các đặc tả sau, và có thể được dùng để implement các hệ thống tuân thủ những đặc tả này.

#### Tuyên bố review

C provides strong low-level support for foundational data representation, memory access, files, streams, procedures, functions, structures, and direct system-oriented implementation.

While C does not natively provide several object-oriented composite constructs, these limitations are isolated to specific FRELSPEC composite provisions and are documented below. These failures do not prevent C from being considered within spec overall, but they should be understood when using C for CatalystUI-compatible implementations.

#### Giả định review

This review assumes modern standard C support where version-dependent features are noted. Exact-width integer support assumes the corresponding `<stdint.h>` types are provided by the implementation.

This review treats C as a low-level representation language. Byte-exact encodings may be represented directly through byte arrays, lookup tables, and explicit parsing logic when no named standard codec is provided.

### Cảnh báo

* Exact-width integer types depend on implementation support.
* CP1252 can be represented byte-for-byte, but no named standard codec is provided.
* UTF-16LE serialization requires explicit byte-order handling.
* Standard threads may be omitted by some C implementations.
* Object-oriented patterns may be manually emulated, but are not native language constructs.

### Lỗi không đạt

* C does not provide native method members.
* C does not provide native properties.
* C does not provide native classes.
* C does not provide native interfaces.

### Xác minh FDEFSPEC

#### Số học

| Điều khoản | Đã xác minh | Ghi chú                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Use bit-fields or masks.                    |
| Nibble    | ⚠️       | Use bit-fields or masks.                    |
| Byte      | ✅        | Được hỗ trợ thông qua `unsigned char`.          |
| Short     | ✅        | Được hỗ trợ thông qua `int16_t` and `uint16_t`. |
| Int       | ✅        | Được hỗ trợ thông qua `int32_t` and `uint32_t`. |
| Long      | ✅        | Được hỗ trợ thông qua `int64_t` and `uint64_t`. |
| Float     | ✅        | Được hỗ trợ thông qua `float`.                  |
| Double    | ✅        | Được hỗ trợ thông qua `double`.                 |
| Boolean   | ✅        | Được hỗ trợ thông qua `bool`; C99+.             |

#### Mã hóa văn bản

| Điều khoản | Đã xác minh | Ghi chú                                   |
| --------- | -------- | --------------------------------------- |
| Codepoint | ✅        | Được hỗ trợ thông qua `char32_t`; C11+.     |
| ASCII     | ✅        | Có thể biểu diễn dưới dạng byte values.           |
| CP1252    | ⚠️        | Yêu cầu explicit byte mapping.         |
| UTF-8     | ✅        | Được hỗ trợ thông qua UTF-8 literals; C11+. |
| UTF-16LE  | ⚠️        | Yêu cầu byte-order handling.           |

#### Trạng thái thao tác

| Điều khoản | Đã xác minh | Ghi chú                           |
| --------- | -------- | ------------------------------- |
| Status    | ✅        | Có thể được biểu diễn bằng an enum.  |
| Context   | ✅        | Có thể được biểu diễn bằng a value.  |
| Operation | ✅        | Có thể được biểu diễn bằng a value.  |
| Detail    | ✅        | Có thể được biểu diễn bằng a value.  |
| Result    | ✅        | Có thể được biểu diễn bằng a struct. |

### Xác minh FRELSPEC

#### Collection

| Điều khoản | Đã xác minh | Ghi chú                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Có thể được biểu diễn bằng structs. |
| Map       | ✅        | Có thể được biểu diễn bằng structs. |
| Array     | ✅        | Array native được hỗ trợ.   |
| File      | ✅        | Được hỗ trợ thông qua file APIs.   |
| Stream    | ✅        | Được hỗ trợ thông qua stream APIs. |

#### Bộ nhớ

| Điều khoản | Đã xác minh | Ghi chú                      |
| --------- | -------- | -------------------------- |
| Address   | ✅        | Addresses are supported.   |
| Pointer   | ✅        | Pointers are supported.    |
| Variable  | ✅        | Variable được hỗ trợ.   |
| Constant  | ✅        | Được hỗ trợ thông qua `const`. |

#### Operation

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Represented through machine operations. |
| Procedure   | ✅        | Được hỗ trợ thông qua `void` functions.     |
| Function    | ✅        | Được hỗ trợ thông qua returning functions.  |

#### Luồng

| Provision  | Verified | Notes                                  |
| ---------- | -------- | -------------------------------------- |
| Process    | ✅        | Được hỗ trợ thông qua hosted environments. |
| Thread     | ⚠️        | Được hỗ trợ thông qua `<threads.h>`; C11+. |
| Dispatcher | ✅        | Can be represented directly.           |

#### Composite

| Điều khoản | Đã xác minh | Ghi chú                                    |
| --------- | -------- | ---------------------------------------- |
| Member    | ✅        | Struct members are supported.            |
| Object    | ✅        | Structs can form addressable composites. |
| Field     | ✅        | Struct fields are supported.             |
| Method    | ❌        | No native method members.                |
| Property  | ❌        | No explicit Get/Set accessor map.        |
| Structure | ✅        | Structure được hỗ trợ native.       |
| Class     | ❌        | No native class construct.               |
| Interface | ❌        | No native interface construct.           |
