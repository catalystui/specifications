<!-- Bản dịch này được tạo bởi ChatGPT và nên được một dịch giả con người xem xét. -->

<!-- Xóa các dòng này trong pull request sau khi bản dịch đã được xác minh. -->

# I18NSPEC

<br/>

> **Đặc tả Quốc tế hóa**<br/>
> Bản sửa đổi 1<br/>
> Ngày 8 tháng 7 năm 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Các định nghĩa, yêu cầu và khái niệm được trình bày trong tài liệu này mô tả hỗ trợ quốc tế hóa thực tế và có thể được diễn đạt lại một cách tự do.

<a id="introduction"></a>
## Giới thiệu

**Đặc tả Quốc tế hóa (I18NSPEC)** thiết lập các khái niệm cốt lõi, thuật ngữ và yêu cầu dùng để đánh giá hỗ trợ đa ngôn ngữ trong hệ sinh thái CatalystUI. Mục đích của đặc tả là cung cấp một tiêu chuẩn rõ ràng để xác định liệu một hệ thống, dịch vụ, framework, ứng dụng hoặc phần triển khai có cung cấp đủ hỗ trợ ngôn ngữ để được xem là nằm trong đặc tả hay không.

Quốc tế hóa quan trọng vì một giao diện người dùng không thể giao tiếp rõ ràng nếu ý nghĩa thiết yếu của nó chỉ có trong một ngôn ngữ. Một hệ thống có thể hoạt động tốt về mặt kỹ thuật, nhưng nếu người dùng không thể hiểu nhãn, hướng dẫn, điều khiển, cài đặt, cảnh báo, lỗi hoặc các luồng công việc cốt lõi, thì hệ thống đó đã không cung cấp một giao diện có ý nghĩa cho những người dùng đó.

Đặc tả này không cố đo chất lượng dịch thuật hoàn hảo, phong cách văn chương, mức độ thích nghi văn hóa, tuân thủ pháp lý hoặc bản địa hóa khu vực đầy đủ. Thay vào đó, đặc tả xác định nền tảng đa ngôn ngữ tối thiểu cần có để người dùng có thể truy cập và vận hành một cách có ý nghĩa các phần thiết yếu của hệ thống trong toàn bộ tập locale bắt buộc của CatalystUI.

Nói đơn giản hơn, I18NSPEC đặt ra ba câu hỏi chính:

1. Người dùng có thể truy cập các phần thiết yếu của hệ thống trong từng ngôn ngữ bắt buộc không?
2. Người dùng có thể chọn một cách hợp lý ngôn ngữ mà họ hiểu không?
3. Hệ thống có giữ được đủ ý nghĩa giữa các ngôn ngữ để vẫn sử dụng được không?

> [!IMPORTANT]
>
> I18NSPEC định nghĩa các yêu cầu quốc tế hóa cho việc xác minh. Đây không phải là một đặc tả riêng cho từng ngôn ngữ. Mỗi locale bắt buộc được kiểm tra theo cùng một đặc tả.

<a id="table-of-contents"></a>
## Mục lục

* [I18NSPEC](#i18nspec)

  * [Giới thiệu](#introduction)
  * [Mục lục](#table-of-contents)
  * [Sự phù hợp](#conformance)
  * [Tập locale bắt buộc](#required-locale-set)
  * [Nội dung hướng tới người dùng](#user-facing-content)

    * [Nội dung hướng tới người dùng](#user-facing-content-1)
    * [Nội dung thiết yếu hướng tới người dùng](#essential-user-facing-content)
    * [Nội dung quan trọng hướng tới người dùng](#critical-user-facing-content)
    * [Nội dung không thiết yếu](#nonessential-content)
  * [Phạm vi bao phủ bản dịch](#translation-coverage)

    * [Phạm vi bao phủ bản dịch thiết yếu](#essential-translation-coverage)
    * [Yêu cầu về phạm vi bao phủ](#coverage-requirement)
    * [Yêu cầu về nội dung quan trọng](#critical-content-requirement)
  * [Chọn ngôn ngữ](#language-selection)

    * [Locale đang hoạt động](#active-locale)
    * [Locale mặc định](#default-locale)
    * [Cơ chế chọn ngôn ngữ](#language-selection-mechanism)
    * [Nhãn tùy chọn ngôn ngữ](#language-option-labels)
  * [Fallback và tương đương locale](#fallbacks-and-locale-equivalence)

    * [Locale fallback](#fallback-locale)
    * [Hành vi fallback](#fallback-behavior)
    * [Tương đương locale](#locale-equivalence)
  * [Yêu cầu triển khai](#implementation-requirements)

    * [Cơ chế dịch ổn định](#stable-translation-mechanism)
    * [Giữ nguyên ý nghĩa](#preservation-of-meaning)
    * [Ngôn ngữ nhạy cảm với hướng chữ](#direction-sensitive-languages)
    * [Giá trị nhạy cảm với locale](#locale-sensitive-values)
  * [Xác minh](#verification)

    * [Nằm trong đặc tả](#within-spec)
    * [Cảnh báo](#warnings)
    * [Lỗi không đạt](#failures)
    * [Hiệu lực xác minh](#verification-validity)

<a id="conformance"></a>
## Sự phù hợp

Một hệ thống được xem là phù hợp với I18NSPEC khi nó đáp ứng các yêu cầu được định nghĩa bởi tài liệu này cho từng locale trong tập locale bắt buộc.

Một hệ thống phù hợp phải:

1. Hỗ trợ từng locale trong tập locale bắt buộc.
2. Cung cấp nội dung đã dịch cho hơn 75% nội dung thiết yếu hướng tới người dùng trong từng locale bắt buộc.
3. Cung cấp nội dung đã dịch cho toàn bộ nội dung quan trọng hướng tới người dùng trong từng locale bắt buộc.
4. Cung cấp một cơ chế hợp lý cho người dùng cuối để chọn locale đang hoạt động.
5. Sử dụng một cơ chế dịch ổn định phù hợp với hệ thống.
6. Giữ nguyên ý nghĩa thiết yếu của nội dung hướng tới người dùng đã được dịch.
7. Tránh dựa vào nội dung fallback để tuyên bố phạm vi bao phủ bản dịch, trừ khi tương đương locale được chấp nhận trong quá trình đánh giá.

Một hệ thống không cần dùng đúng một mẫu triển khai cụ thể để phù hợp với đặc tả này. Nó có thể dùng tệp tài nguyên, bảng dịch, định tuyến theo locale, tài nguyên ngôn ngữ đã biên dịch, trang tĩnh đã bản địa hóa, gói ngôn ngữ khi chạy, bản dịch dựa trên cơ sở dữ liệu hoặc một cơ chế ổn định khác phù hợp với hệ thống.

Việc xác minh tập trung vào khả năng truy cập thực tế của người dùng và ý nghĩa thiết yếu, không phải một kiến trúc kỹ thuật cứng nhắc duy nhất.

<a id="required-locale-set"></a>
## Tập locale bắt buộc

Tập locale bắt buộc định nghĩa các ngôn ngữ và biến thể khu vực phải được đánh giá cho CatalystUI Internationalization Verification.

Tập locale bắt buộc hiện tại bao gồm các locale sau:

| Locale    | Ngôn ngữ                 |
| --------- | ------------------------ |
| `ar-SA`   | Tiếng Ả Rập (Ả Rập Xê Út) |
| `bn-BD`   | Tiếng Bengal (Bangladesh) |
| `de-DE`   | Tiếng Đức (Đức)          |
| `en-GB`   | Tiếng Anh (Vương quốc Anh) |
| `en-IN`   | Tiếng Anh (Ấn Độ)        |
| `en-US`   | Tiếng Anh (Hoa Kỳ)       |
| `es-ES`   | Tiếng Tây Ban Nha (Tây Ban Nha) |
| `es-MX`   | Tiếng Tây Ban Nha (Mexico) |
| `fa-IR`   | Tiếng Ba Tư (Iran)       |
| `fr-FR`   | Tiếng Pháp (Pháp)        |
| `hi-IN`   | Tiếng Hindi (Ấn Độ)      |
| `id-ID`   | Tiếng Indonesia (Indonesia) |
| `it-IT`   | Tiếng Ý (Ý)              |
| `ja-JP`   | Tiếng Nhật (Nhật Bản)    |
| `ko-KR`   | Tiếng Hàn (Hàn Quốc)     |
| `nl-NL`   | Tiếng Hà Lan (Hà Lan)    |
| `pl-PL`   | Tiếng Ba Lan (Ba Lan)    |
| `pt-BR`   | Tiếng Bồ Đào Nha (Brazil) |
| `ru-RU`   | Tiếng Nga (Nga)          |
| `tl-PH`   | Tiếng Tagalog (Philippines) |
| `tr-TR`   | Tiếng Thổ Nhĩ Kỳ (Thổ Nhĩ Kỳ) |
| `uk-UA`   | Tiếng Ukraina (Ukraina)  |
| `ur-PK`   | Tiếng Urdu (Pakistan)    |
| `vi-VN`   | Tiếng Việt (Việt Nam)    |
| `zh-CN`   | Tiếng Trung (Trung Quốc) |
| `zh-Hans` | Tiếng Trung (Giản thể)   |

Một hệ thống phải cung cấp đủ hỗ trợ dịch thuật thiết yếu cho từng locale được liệt kê để được xem là nằm trong đặc tả.

Tập locale bắt buộc không nhằm đại diện cho mọi ngôn ngữ, phương ngữ, khu vực hoặc hệ chữ. Thay vào đó, nó thiết lập một đường cơ sở thực tế cho khả năng sử dụng quốc tế rộng rãi trên nhiều nhóm ngôn ngữ thường gặp trong bối cảnh công nghệ.

<a id="user-facing-content"></a>
## Nội dung hướng tới người dùng

<a id="user-facing-content-1"></a>
### Nội dung hướng tới người dùng

Nội dung hướng tới người dùng là bất kỳ nội dung nào được dự định để người dùng cuối cảm nhận, đọc, nghe, chọn, hiểu hoặc hành động dựa trên đó.

Nội dung hướng tới người dùng có thể bao gồm:

* điều hướng
* nhãn
* nút
* menu
* điều khiển
* tiêu đề
* hộp thoại
* cài đặt
* hướng dẫn
* lời nhắc
* cảnh báo
* lỗi
* xác nhận
* thông báo trạng thái
* văn bản giới thiệu ban đầu
* văn bản trợ giúp bắt buộc
* điều khiển chọn ngôn ngữ
* nội dung luồng công việc cốt lõi

Nội dung hướng tới người dùng không nhất thiết phải là nội dung trực quan. Nó cũng có thể bao gồm nội dung thính giác, xúc giác, ký hiệu hoặc đa giác quan khi nội dung đó truyền đạt ý nghĩa cho người dùng.

<a id="essential-user-facing-content"></a>
### Nội dung thiết yếu hướng tới người dùng

Nội dung thiết yếu hướng tới người dùng là nội dung hướng tới người dùng mà một người dùng cần một cách hợp lý để hiểu, điều hướng, cấu hình hoặc vận hành hành vi thiết yếu của một hệ thống.

Nội dung thiết yếu hướng tới người dùng có thể bao gồm:

* điều hướng chính
* màn hình và chế độ xem cốt lõi
* cài đặt và tùy chọn
* nhãn hướng tới người dùng
* điều khiển hướng tới người dùng
* hướng dẫn bắt buộc
* cảnh báo quan trọng
* lỗi quan trọng
* lời nhắc thiết yếu
* thông báo xác nhận bắt buộc
* điều khiển chọn ngôn ngữ
* luồng công việc cốt lõi cần cho việc sử dụng bình thường

Một hệ thống không cần dịch mọi trang tùy chọn, thông báo ẩn, nhãn nội bộ hoặc văn bản không thiết yếu để đáp ứng I18NSPEC. Tuy nhiên, nội dung cần cho việc sử dụng thiết yếu thông thường phải được dịch theo các yêu cầu của đặc tả này.

<a id="critical-user-facing-content"></a>
### Nội dung quan trọng hướng tới người dùng

Nội dung quan trọng hướng tới người dùng là nội dung thiết yếu hướng tới người dùng mà nếu hiểu sai có thể ngăn việc sử dụng có ý nghĩa, tạo ra lỗi nghiêm trọng hoặc khiến người dùng đưa ra một quyết định quan trọng mà không hiểu hậu quả.

Nội dung quan trọng hướng tới người dùng có thể bao gồm:

* điều khiển chọn ngôn ngữ
* cảnh báo hành động phá hủy
* cảnh báo xóa tài khoản
* xác nhận thanh toán
* xác nhận mua hàng
* lựa chọn quyền riêng tư
* cảnh báo bảo mật
* lời nhắc đồng ý
* hướng dẫn an toàn bắt buộc
* hướng dẫn thiết lập bắt buộc
* thông báo lỗi bắt buộc
* điều hướng cốt lõi cần để đến phần cài đặt ngôn ngữ

Nội dung quan trọng hướng tới người dùng phải được dịch cho từng locale bắt buộc.

Ngưỡng bao phủ bản dịch thiết yếu 75% không được dùng để bỏ lại nội dung quan trọng chưa dịch.

<a id="nonessential-content"></a>
### Nội dung không thiết yếu

Nội dung không thiết yếu là nội dung không được yêu cầu một cách hợp lý để người dùng hiểu, điều hướng, cấu hình hoặc vận hành hành vi thiết yếu của một hệ thống.

Nội dung không thiết yếu có thể bao gồm:

* mã định danh nội bộ
* tên mã nguồn
* chuỗi chỉ dùng để gỡ lỗi
* chi tiết triển khai hướng tới nhà phát triển
* văn bản chẩn đoán ẩn
* trang tiếp thị tùy chọn
* trang hỗ trợ tùy chọn
* văn bản pháp lý hoặc kinh doanh không thiết yếu nằm ngoài phạm vi được đánh giá
* nội dung bên thứ ba không do hệ thống được đánh giá kiểm soát

Nội dung không thiết yếu có thể được dịch, nhưng không bắt buộc cho sự phù hợp với I18NSPEC trừ khi nó trở nên cần thiết để người dùng hiểu hoặc vận hành những phần thiết yếu.

<a id="translation-coverage"></a>
## Phạm vi bao phủ bản dịch

<a id="essential-translation-coverage"></a>
### Phạm vi bao phủ bản dịch thiết yếu

Phạm vi bao phủ bản dịch thiết yếu là lượng nội dung thiết yếu hướng tới người dùng đã được dịch cho một locale cụ thể.

Phạm vi bao phủ nên được đánh giá theo các đơn vị nội dung có ý nghĩa hướng tới người dùng, thay vì theo kích thước tệp, số byte, số dòng, kích thước repository hoặc số trang.

Ví dụ, một nút chưa dịch kiểm soát một hành động thiết yếu có thể quan trọng hơn một đoạn văn tùy chọn lớn chưa dịch nhưng không ảnh hưởng đến việc sử dụng thông thường.

Phạm vi bao phủ bản dịch nên được đánh giá dựa trên việc người dùng có thể hiểu và vận hành hệ thống thiết yếu một cách có ý nghĩa trong locale được đánh giá hay không.

<a id="coverage-requirement"></a>
### Yêu cầu về phạm vi bao phủ

Một hệ thống đáp ứng yêu cầu về phạm vi bao phủ bản dịch cho một locale khi hơn 75% nội dung thiết yếu hướng tới người dùng được dịch cho locale đó.

Một hệ thống đáp ứng yêu cầu bao phủ của I18NSPEC khi đạt ngưỡng này cho mọi locale trong tập locale bắt buộc.

Trong đánh giá thực tế, điều này có thể được biểu diễn như sau:

| Locale  | Phạm vi bao phủ bản dịch thiết yếu | Kết quả |
| ------- | ---------------------------------- | ------- |
| `en-US` | 100%                               | Đạt     |
| `es-ES` | 94%                                | Đạt     |
| `ar-SA` | 78%                                | Đạt     |
| `ja-JP` | 61%                                | Không đạt |

Một locale có mức bao phủ 75% hoặc thấp hơn không đáp ứng yêu cầu về phạm vi bao phủ.

Một locale có hơn 75% mức bao phủ vẫn có thể không đạt nếu nội dung quan trọng hướng tới người dùng chưa được dịch.

<a id="critical-content-requirement"></a>
### Yêu cầu về nội dung quan trọng

Toàn bộ nội dung quan trọng hướng tới người dùng phải được dịch cho từng locale bắt buộc.

Một hệ thống có thể không đạt I18NSPEC ngay cả khi đáp ứng ngưỡng bao phủ chung nếu một hoặc nhiều mục nội dung quan trọng hướng tới người dùng bị thiếu, chưa dịch, gây hiểu lầm hoặc không thể hiểu một cách có ý nghĩa.

Ví dụ, một hệ thống không nên được xem là nằm trong đặc tả nếu giao diện chung đã được dịch nhưng cảnh báo xóa tài khoản, xác nhận mua hàng, cảnh báo bảo mật hoặc bộ chọn ngôn ngữ vẫn chưa được dịch.

<a id="language-selection"></a>
## Chọn ngôn ngữ

<a id="active-locale"></a>
### Locale đang hoạt động

Locale đang hoạt động là locale hiện được chọn cho trải nghiệm của người dùng.

Locale đang hoạt động xác định nội dung đã dịch nào nên được hiển thị, cung cấp hoặc truyền đạt bằng cách khác cho người dùng.

<a id="default-locale"></a>
### Locale mặc định

Locale mặc định là locale được dùng khi người dùng chưa chọn locale đang hoạt động hoặc khi không có tùy chọn người dùng nào khả dụng.

Một hệ thống phải định nghĩa một locale mặc định.

Locale mặc định nên được ghi lại trong tài liệu hoặc có thể được người đánh giá suy luận một cách hợp lý.

<a id="language-selection-mechanism"></a>
### Cơ chế chọn ngôn ngữ

Một hệ thống phù hợp phải cung cấp một cách hợp lý để người dùng cuối thay đổi locale đang hoạt động.

Cơ chế chọn ngôn ngữ phải có sẵn mà không yêu cầu người dùng:

* sửa mã nguồn
* dùng công cụ dành cho nhà phát triển
* chỉnh sửa các tệp cấu hình không được ghi lại trong tài liệu
* cài đặt bản vá không chính thức
* dựa vào hành vi ẩn
* liên hệ bộ phận hỗ trợ cho các thay đổi ngôn ngữ thông thường

Cơ chế chọn ngôn ngữ có thể được cung cấp thông qua:

* cài đặt ứng dụng
* tùy chọn tài khoản
* bộ chọn ngôn ngữ
* lời nhắc khi khởi động
* cài đặt trình duyệt
* cài đặt hệ điều hành
* cài đặt thiết bị
* một cơ chế thích hợp khác mà người dùng cuối có thể truy cập

Cơ chế này không cần tuân theo một mẫu thiết kế cụ thể duy nhất. Nó phải cho phép người dùng chọn một ngôn ngữ được hỗ trợ một cách hợp lý.

<a id="language-option-labels"></a>
### Nhãn tùy chọn ngôn ngữ

Khi hiển thị các tùy chọn ngôn ngữ, hệ thống nên nhận diện từng ngôn ngữ theo cách dễ hiểu đối với người dùng nói ngôn ngữ đó.

Một tùy chọn ngôn ngữ có thể bao gồm:

* tên ngôn ngữ bằng chính ngôn ngữ đó
* tên ngôn ngữ bằng ngôn ngữ hiện đang hoạt động
* mã locale
* nhãn khu vực
* nhãn hệ chữ

Ví dụ:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

Định dạng chính xác có thể khác nhau.

Ý định là người dùng có thể nhận ra ngôn ngữ của mình, hiểu tên ngôn ngữ đang được hiển thị khi có thể, và nhận diện mã locale liên quan.

<a id="fallbacks-and-locale-equivalence"></a>
## Fallback và tương đương locale

<a id="fallback-locale"></a>
### Locale fallback

Locale fallback là locale được dùng khi nội dung đã dịch không khả dụng cho locale đang hoạt động.

Locale fallback có thể giúp duy trì khả năng sử dụng, nhưng nội dung fallback không tự động được xem là nội dung đã dịch cho locale đang hoạt động.

Ví dụ, nếu một hệ thống được đặt thành `es-MX` nhưng hiển thị văn bản `en-US` vì thiếu bản dịch tiếng Tây Ban Nha, văn bản tiếng Anh đó có thể hữu ích như một fallback, nhưng không nên được tính là phạm vi bao phủ bản dịch tiếng Tây Ban Nha.

<a id="fallback-behavior"></a>
### Hành vi fallback

Một hệ thống phù hợp có thể dùng hành vi fallback khi nội dung đã bản địa hóa không khả dụng.

Hành vi fallback nên tránh đầu ra bị hỏng, trống hoặc gây hiểu lầm.

Hành vi fallback không được dùng để tuyên bố sai phạm vi bao phủ bản dịch cho một locale bắt buộc.

Một hệ thống có thể nhận cảnh báo hoặc không đạt nếu hành vi fallback quá nhiều, gây nhầm lẫn, không được ghi lại trong tài liệu hoặc khiến nội dung thiết yếu xuất hiện như chưa được dịch trong một locale bắt buộc.

<a id="locale-equivalence"></a>
### Tương đương locale

Tương đương locale xảy ra khi một bản dịch có thể phục vụ hợp lý cho nhiều hơn một locale mà không ngăn cản việc hiểu hoặc vận hành thiết yếu.

Ví dụ, một hệ thống có thể dùng một bản dịch tiếng Anh cho `en-US`, `en-GB` và `en-IN` nếu ý nghĩa thiết yếu vẫn rõ ràng cho người dùng của từng locale.

Tương đương locale có thể được chấp nhận trong quá trình đánh giá khi khác biệt khu vực là nhỏ và không ảnh hưởng đáng kể đến khả năng sử dụng thiết yếu.

Tương đương locale không được dùng khi một locale bị thiếu sẽ tạo ra sự nhầm lẫn có ý nghĩa, bỏ sót thuật ngữ khu vực quan trọng, phá vỡ hành vi thiết yếu hoặc ngăn người dùng hiểu hệ thống.

Ví dụ, một hệ thống không nên giả định rằng các ngôn ngữ không liên quan là tương đương chỉ vì chúng có cùng hướng viết, khu vực địa lý, họ hệ chữ hoặc nhóm văn hóa rộng.

Tương đương locale là một phán đoán đánh giá, không phải một quy tắc tự động.

<a id="implementation-requirements"></a>
## Yêu cầu triển khai

<a id="stable-translation-mechanism"></a>
### Cơ chế dịch ổn định

Một hệ thống phù hợp phải dùng một cơ chế dịch ổn định phù hợp với hệ thống đang được đánh giá.

Một cơ chế dịch ổn định nên cho phép nội dung đã dịch được bảo trì, cập nhật, đánh giá và mở rộng mà không dựa vào hành vi mong manh hoặc không được ghi lại trong tài liệu.

Một cơ chế dịch ổn định có thể bao gồm:

* tệp tài nguyên
* bảng dịch
* định tuyến theo locale
* tài nguyên ngôn ngữ đã biên dịch
* trang tĩnh đã bản địa hóa
* gói ngôn ngữ khi chạy
* bản dịch dựa trên cơ sở dữ liệu
* một cấu trúc dịch được ghi lại trong tài liệu khác

Một hệ thống nên tránh hardcode nội dung thiết yếu hướng tới người dùng theo cách ngăn cản hỗ trợ dịch thuật bắt buộc.

<a id="preservation-of-meaning"></a>
### Giữ nguyên ý nghĩa

Một bản dịch giữ nguyên ý nghĩa khi người dùng có thể hiểu một cách hợp lý cùng một hướng dẫn, nhãn, cảnh báo, điều khiển, cài đặt hoặc luồng công việc thiết yếu như người dùng của ngôn ngữ nguồn.

Một bản dịch không cần giống từng từ với nội dung nguồn.

Một bản dịch có thể thay đổi trật tự từ, ngữ pháp, cấu trúc câu, thành ngữ, giọng văn hoặc cách diễn đạt khi cần để truyền đạt cùng một ý nghĩa thiết yếu trong ngôn ngữ đích.

Một bản dịch có thể không đạt đánh giá nếu nó gây hiểu lầm, không đầy đủ, vô nghĩa, bị hỏng do máy móc hoặc khác đáng kể với nội dung nguồn theo cách ảnh hưởng đến việc sử dụng thiết yếu.

<a id="direction-sensitive-languages"></a>
### Ngôn ngữ nhạy cảm với hướng chữ

Một số locale bắt buộc thường dùng hướng văn bản từ phải sang trái.

Một hệ thống phù hợp không được ngăn nội dung thiết yếu đã dịch được đọc, hiểu, chọn hoặc hành động dựa trên đó chỉ vì locale đang hoạt động dùng hướng chữ khác.

Hệ thống nên giữ trật tự dễ đọc, hành vi dấu câu và sự liên kết của điều khiển đối với các ngôn ngữ nhạy cảm với hướng chữ.

Mức độ trau chuốt hình ảnh đầy đủ, chất lượng kiểu chữ, hành vi khả năng truy cập và tinh chỉnh bố cục có thể cần đánh giá riêng. Tuy nhiên, nội dung thiết yếu đã dịch phải vẫn có thể sử dụng một cách có ý nghĩa.

<a id="locale-sensitive-values"></a>
### Giá trị nhạy cảm với locale

Giá trị nhạy cảm với locale là các giá trị mà ý nghĩa hoặc khả năng đọc có thể thay đổi theo ngôn ngữ, khu vực, hệ chữ hoặc văn hóa.

Giá trị nhạy cảm với locale có thể bao gồm:

* ngày tháng
* thời gian
* số
* tiền tệ
* đơn vị đo lường
* dạng số nhiều
* giống ngữ pháp
* thứ tự sắp xếp
* định dạng địa chỉ
* định dạng số điện thoại

I18NSPEC không yêu cầu bản địa hóa đầy đủ mọi giá trị nhạy cảm với locale trừ khi giá trị đó là thiết yếu để hiểu hoặc vận hành hệ thống.

Khi các giá trị nhạy cảm với locale là thiết yếu, hệ thống nên biểu diễn chúng theo cách mà người dùng của locale đang hoạt động có thể hiểu một cách hợp lý.

<a id="verification"></a>
## Xác minh

<a id="within-spec"></a>
### Nằm trong đặc tả

Một hệ thống được xem là nằm trong đặc tả khi Nhóm CatalystUI đã đánh giá hệ thống và thấy hợp lý để kết luận rằng nó đáp ứng I18NSPEC.

Một hệ thống có thể nằm trong đặc tả khi:

* mọi locale bắt buộc đều được hỗ trợ
* hơn 75% nội dung thiết yếu hướng tới người dùng được dịch cho từng locale bắt buộc
* toàn bộ nội dung quan trọng hướng tới người dùng được dịch cho từng locale bắt buộc
* người dùng có thể chọn locale đang hoạt động một cách hợp lý
* hành vi fallback không tuyên bố sai phạm vi bao phủ bản dịch
* tương đương locale, nếu được dùng, là hợp lý và được ghi lại trong tài liệu
* nội dung đã dịch giữ nguyên ý nghĩa thiết yếu

Một hệ thống có thể nằm trong đặc tả ngay cả khi một số nội dung không thiết yếu vẫn chưa được dịch.

Một hệ thống có thể nằm trong đặc tả ngay cả khi bản dịch không hoàn hảo, miễn là ý nghĩa thiết yếu được giữ nguyên và các yêu cầu của đặc tả này được đáp ứng.

<a id="warnings"></a>
### Cảnh báo

Một cảnh báo có thể được đưa ra khi hệ thống có vẻ đáp ứng I18NSPEC nhưng chứa các vấn đề cần được ghi lại trong tài liệu.

Cảnh báo có thể bao gồm:

* nội dung không thiết yếu nhỏ chưa được dịch
* thuật ngữ không nhất quán giữa các locale
* bản dịch chưa hoàn hảo nhưng vẫn dễ hiểu
* tương đương locale chấp nhận được nhưng nên được ghi lại trong tài liệu
* hành vi fallback hạn chế
* các trang tùy chọn được dịch một phần
* vấn đề bố cục nhạy cảm với hướng chữ nhưng không ngăn việc sử dụng thiết yếu
* giá trị nhạy cảm với locale có thể hiểu được nhưng chưa lý tưởng

Cảnh báo không nhất thiết ngăn việc xác minh.

<a id="failures"></a>
### Lỗi không đạt

Lỗi không đạt xảy ra khi một hệ thống không đáp ứng một hoặc nhiều điều kiện bắt buộc của I18NSPEC.

Lỗi không đạt có thể bao gồm:

* thiếu hỗ trợ cho một locale bắt buộc
* phạm vi bao phủ bản dịch thiết yếu ở mức 75% hoặc thấp hơn cho một locale bắt buộc
* nội dung quan trọng hướng tới người dùng chưa dịch
* không có cơ chế chọn ngôn ngữ hợp lý
* việc chọn ngôn ngữ yêu cầu sửa đổi mã nguồn
* việc chọn ngôn ngữ yêu cầu công cụ dành cho nhà phát triển
* tải bản dịch bị hỏng
* tuyên bố locale gây hiểu lầm
* hành vi fallback quá mức
* nội dung fallback được tính là nội dung đã dịch mà không có tương đương locale hợp lệ
* nội dung nhạy cảm với hướng chữ không thể đọc hoặc không thể sử dụng
* luồng công việc thiết yếu không khả dụng trong một hoặc nhiều locale bắt buộc

Lỗi không đạt sẽ ngăn việc xác minh cho đến khi được giải quyết.

<a id="verification-validity"></a>
### Hiệu lực xác minh

Xác minh I18NSPEC chỉ áp dụng cho trạng thái đã được đánh giá của hệ thống tại thời điểm xác minh được cấp.

Một hệ thống có thể giữ xác minh qua các bản cập nhật sau này miễn là nó bảo toàn nền tảng quốc tế hóa đã được xác minh.

Những thay đổi nhỏ về cách diễn đạt, bản dịch được thêm vào, bản dịch được cải thiện và cập nhật nội dung thông thường không tự động làm mất hiệu lực xác minh.

Có thể cần một đánh giá mới nếu hệ thống:

* loại bỏ hỗ trợ locale bắt buộc
* làm hỏng việc chọn ngôn ngữ
* giảm đáng kể phạm vi bao phủ bản dịch thiết yếu
* để các luồng công việc thiết yếu mới chưa được dịch
* thay nội dung đã dịch bằng nội dung fallback
* thay đổi kiến trúc dịch theo cách ảnh hưởng đến hành vi đã được xác minh
* giới thiệu các thay đổi lớn hướng tới người dùng làm thay đổi phạm vi đã được đánh giá

Nói cách khác, cải thiện hỗ trợ dịch thuật thường là ổn.

Phá vỡ nền tảng đa ngôn ngữ đã được xác minh có thể cần được đánh giá lại.
