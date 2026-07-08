<!-- Bản dịch này được tạo bởi ChatGPT và nên được một người dịch xem xét lại. -->
<!-- Hãy xóa các dòng này trong pull request sau khi bản dịch đã được xác minh. -->

# Chi tiết review

## Python

### Tổng quan

Ngôn ngữ lập trình Python đã được review theo các đặc tả FDEFSPEC (Rev. 1) và FRELSPEC (Rev. 1) tính đến ngày 7 tháng 7 năm 2026.

#### Tuyên bố review

Mặc dù Python có thể biểu diễn nhiều khái niệm bắt buộc thông qua type tích hợp, object, function, class, module thư viện chuẩn và custom validation, các cơ chế này không đủ để đáp ứng các đặc tả CatalystUI áp dụng ở cấp ngôn ngữ.

Python provides strong support for text encoding, files, streams, objects, functions, classes, properties, processes, threads, and dispatched execution through its built-in behavior and standard library. However, Python does not provide the required fixed-width scalar numeric types, does not define true constants, and relies on dynamic runtime behavior for several constructs that other verified languages can express more directly.

Vì vậy, chúng tôi không tin Python cung cấp nền tảng đủ ổn định cho implementation tuân thủ CatalystUI nếu không có hạ tầng bổ sung đáng kể.

Do đó, Python chưa được cấp trạng thái CatalystUI Verified cho ngôn ngữ lập trình.

#### Giả định review

This review evaluates Python itself and its bundled standard library.

Third-party packages, implementation-specific extensions, optional native modules, external type checkers, transpilers, and custom runtime frameworks are not treated as language-level support.

### Cảnh báo

* Python provides unlimited-precision integers, not fixed-width integer primitives.
* Python `float` is usually double precision, but not a distinct fixed-width family.
* Some low-level memory behavior may require `ctypes` or implementation-specific behavior.
* Python type hints are not enforced at runtime.
* Python supports properties, but setter behavior may be omitted.
* Python can model several structures through standard-library features, but not as a native structure type.

### Lỗi không đạt

* Python does not provide most required fixed-width scalar numeric types.
* Python does not provide a dedicated scalar 32-bit floating point type.
* Python does not provide true language-level constants.
* Python does not define procedures separately from functions.
* Python does not provide native pointer support.
* Python does not provide native interface support.

### Xác minh FDEFSPEC

#### Số học

| Điều khoản | Đã xác minh | Ghi chú                                |
| --------- | -------- | ------------------------------------ |
| Bit       | ❌        | Không có kiểu số 1 bit.               |
| Nibble    | ❌        | Không có kiểu số 4 bit.               |
| Byte      | ❌        | Không có kiểu số nguyên scalar 8 bit.        |
| Short     | ❌        | Không có kiểu số nguyên scalar 16 bit.       |
| Int       | ❌        | Không có kiểu số nguyên scalar 32 bit.       |
| Long      | ❌        | Không có kiểu số nguyên scalar 64 bit.       |
| Float     | ❌        | Không có kiểu float scalar 32 bit.         |
| Double    | ⚠️       | `float` is usually double precision. |
| Boolean   | ✅        | Được hỗ trợ thông qua `bool`.            |

#### Mã hóa văn bản

| Điều khoản | Đã xác minh | Ghi chú                            |
| --------- | -------- | -------------------------------- |
| Codepoint | ✅        | Strings use Unicode code points. |
| ASCII     | ✅        | Codec được hỗ trợ.                 |
| CP1252    | ✅        | Codec được hỗ trợ.                 |
| UTF-8     | ✅        | Codec được hỗ trợ.                 |
| UTF-16LE  | ✅        | Codec được hỗ trợ.                 |

#### Trạng thái thao tác

| Điều khoản | Đã xác minh | Ghi chú                       |
| --------- | -------- | --------------------------- |
| Status    | ⚠️       | Yêu cầu custom validation. |
| Context   | ⚠️       | Yêu cầu custom validation. |
| Operation | ⚠️       | Yêu cầu custom validation. |
| Detail    | ⚠️       | Yêu cầu custom validation. |
| Result    | ⚠️       | Yêu cầu custom validation. |

### Xác minh FRELSPEC

#### Collection

| Điều khoản | Đã xác minh | Ghi chú                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Được hỗ trợ thông qua `set`.       |
| Map       | ✅        | Được hỗ trợ thông qua `dict`.      |
| Array     | ✅        | Được hỗ trợ thông qua sequences.   |
| File      | ✅        | Được hỗ trợ thông qua file APIs.   |
| Stream    | ✅        | Được hỗ trợ thông qua stream APIs. |

#### Bộ nhớ

| Điều khoản | Đã xác minh | Ghi chú                        |
| --------- | -------- | ---------------------------- |
| Address   | ⚠️       | Object identity only.        |
| Pointer   | ❌        | No native pointer support.   |
| Variable  | ✅        | Name bindings are supported. |
| Constant  | ❌        | No true constants.           |

#### Operation

| Provision   | Verified | Notes                             |
| ----------- | -------- | --------------------------------- |
| Instruction | ⚠️       | Bytecode is implementation-level. |
| Procedure   | ❌        | Functions return `None`.          |
| Function    | ✅        | Function được hỗ trợ.          |

#### Luồng

| Provision  | Verified | Notes                            |
| ---------- | -------- | -------------------------------- |
| Process    | ✅        | Được hỗ trợ thông qua process APIs.  |
| Thread     | ✅        | Được hỗ trợ thông qua `threading`.   |
| Dispatcher | ✅        | Được hỗ trợ thông qua executor APIs. |

#### Composite

| Điều khoản | Đã xác minh | Ghi chú                            |
| --------- | -------- | -------------------------------- |
| Member    | ✅        | Object members are supported.    |
| Object    | ✅        | Object được hỗ trợ.           |
| Field     | ✅        | Attributes can represent fields. |
| Method    | ✅        | Method được hỗ trợ.           |
| Property  | ⚠️       | Getter/setter support exists.    |
| Structure | ⚠️       | Standard-library models only.    |
| Class     | ✅        | Class được hỗ trợ.           |
| Interface | ❌        | No native interface support.     |
