<!-- Bản dịch này được tạo bởi ChatGPT và nên được một dịch giả con người xem xét. -->

<!-- Xóa các dòng này trong pull request sau khi bản dịch đã được xác minh. -->

![CatalystUI Verified for Internationalization](/images/verification/verified-logo-internationalization.png)

# CatalystUI Verified cho Quốc tế hóa

Chào mừng bạn đến với tài liệu CatalystUI Verification dành cho quốc tế hóa.

**CatalystUI Verified cho Quốc tế hóa** cho biết rằng một hệ thống, dịch vụ, framework, ứng dụng hoặc phần triển khai đã được Nhóm CatalystUI đánh giá và được nhận thấy là cung cấp đủ hỗ trợ đa ngôn ngữ cho tập ngôn ngữ quốc tế hóa bắt buộc của CatalystUI.

Việc xác minh này không phải là bảng xếp hạng chung về chất lượng dịch thuật, phong cách viết, độ sâu bản địa hóa hoặc mức độ thích nghi văn hóa. Thay vào đó, nó xác định liệu hệ thống được đánh giá có cung cấp một nền tảng ổn định và thực tế để người dùng truy cập chức năng thiết yếu của nó trong các ngôn ngữ được hỗ trợ bắt buộc hay không.

Nói đơn giản hơn, việc xác minh này hỏi liệu người dùng có thể sử dụng một cách có ý nghĩa các phần thiết yếu của một hệ thống trong những ngôn ngữ bắt buộc hay không, và liệu họ có được cung cấp một cách hợp lý để chọn ngôn ngữ mà họ hiểu hay không.

<a id="purpose"></a>
## Mục đích

Quốc tế hóa quan trọng vì một hệ thống không thể được xem là có khả năng truy cập rộng rãi nếu ý nghĩa thiết yếu của nó bị khóa sau một ngôn ngữ.

CatalystUI được thiết kế xoay quanh sự rõ ràng, nhất quán và việc biểu diễn trung thực tương tác giữa con người và máy tính. Ngôn ngữ là một phần của tương tác đó. Nếu người dùng không thể hiểu nhãn, hướng dẫn, cảnh báo, điều khiển, cài đặt hoặc nội dung thiết yếu của một hệ thống, thì hệ thống đó đã không giao tiếp rõ ràng, ngay cả khi chức năng bên dưới về mặt kỹ thuật vẫn hoạt động.

Internationalization Verification tồn tại để nhận diện các hệ thống cung cấp đủ hỗ trợ dịch thuật cho người dùng trên toàn bộ tập ngôn ngữ bắt buộc của CatalystUI. Mục tiêu không phải là đòi hỏi bản dịch hoàn hảo của mọi từ tùy chọn, thông báo ẩn dành cho nhà phát triển hoặc trang không thiết yếu. Mục tiêu là xác định liệu các phần thiết yếu của hệ thống có thể được hiểu và sử dụng bởi mọi người trong từng ngôn ngữ bắt buộc hay không.

<a id="what-verification-means"></a>
## Ý nghĩa của việc xác minh

Một hệ thống trở thành **CatalystUI Verified cho Quốc tế hóa** khi nó được đánh giá theo các yêu cầu được liệt kê trong phần này và được nhận thấy là nằm trong đặc tả.

Để được xác minh, một hệ thống phải cung cấp bản dịch cho hơn 75% các phần thiết yếu hướng tới người dùng của hệ thống trong từng ngôn ngữ bắt buộc. Nó cũng phải cung cấp một cơ chế hợp lý cho người dùng cuối để thay đổi ngôn ngữ đang hoạt động.

Một hệ thống không cần dịch mọi mã định danh nội bộ, chi tiết triển khai hướng tới nhà phát triển, chuỗi gỡ lỗi, trang tiếp thị tùy chọn hoặc văn bản hỗ trợ không thiết yếu. Tuy nhiên, các phần hướng tới người dùng cần để hiểu và vận hành hệ thống thiết yếu phải có sẵn trong từng ngôn ngữ bắt buộc.

<a id="required-languages"></a>
## Ngôn ngữ bắt buộc

Tập ngôn ngữ quốc tế hóa hiện tại của CatalystUI được chọn từ một đánh giá thực tế về các ngôn ngữ thường cần trong bối cảnh công nghệ, bao gồm phạm vi người nói toàn cầu, mức sử dụng trực tuyến phổ biến, kỳ vọng đối với phần mềm đa ngôn ngữ và nhu cầu khả năng truy cập khu vực rộng rãi.

Tập ngôn ngữ này không nhằm đại diện cho mọi ngôn ngữ, mọi phương ngữ hoặc mọi biến thể khu vực. Thay vào đó, nó thiết lập một đường cơ sở thực tế cho các hệ thống tìm kiếm khả năng sử dụng quốc tế rộng rãi trên nhiều nhóm ngôn ngữ thường gặp nhất thế giới trong bối cảnh công nghệ.

Tập ngôn ngữ quốc tế hóa hiện tại của CatalystUI bao gồm các locale sau:

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

Một hệ thống phải cung cấp đủ phạm vi bao phủ bản dịch thiết yếu cho từng nhóm ngôn ngữ được liệt kê để được xem là nằm trong đặc tả.

Tuy nhiên, các biến thể khu vực có thể được đánh giá với sự linh hoạt hợp lý khi khác biệt giữa các biến thể là nhỏ và không ảnh hưởng đáng kể đến khả năng hiểu hoặc vận hành hệ thống của người dùng. Ví dụ, một hệ thống vẫn có thể đủ điều kiện xác minh nếu nó cung cấp một bản dịch tiếng Anh mạnh nhưng không dịch riêng từng biến thể tiếng Anh theo khu vực, miễn là ý nghĩa thiết yếu, điều hướng, hướng dẫn, cảnh báo và điều khiển vẫn rõ ràng đối với người dùng của các biến thể còn thiếu.

Sự linh hoạt này không áp dụng khi một biến thể bị thiếu sẽ tạo ra sự nhầm lẫn có ý nghĩa, bỏ sót thuật ngữ khu vực quan trọng, phá vỡ hành vi nhạy cảm với locale hoặc ngăn người dùng hiểu các phần thiết yếu của hệ thống.

<a id="essential-translation-coverage"></a>
## Phạm vi bao phủ bản dịch thiết yếu

Đối với Internationalization Verification, **phạm vi bao phủ bản dịch thiết yếu** chỉ các phần của hệ thống mà người dùng cần một cách hợp lý để hiểu, điều hướng, cấu hình và vận hành hệ thống.

Các phần thiết yếu có thể bao gồm:

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

Một hệ thống được xem là đáp ứng yêu cầu về phạm vi bao phủ bản dịch khi hơn 75% nội dung thiết yếu hướng tới người dùng của nó có sẵn trong từng ngôn ngữ bắt buộc.

Ngưỡng này tồn tại vì công việc quốc tế hóa có thể lớn, liên tục và phụ thuộc vào ngữ cảnh. Một hệ thống vẫn có thể nằm trong đặc tả ngay cả khi một số nội dung không thiết yếu hoặc ưu tiên thấp hơn vẫn chưa được dịch. Tuy nhiên, trải nghiệm thiết yếu phải có sẵn một cách có ý nghĩa trong mọi ngôn ngữ bắt buộc.

<a id="language-selection"></a>
## Chọn ngôn ngữ

Một hệ thống đã được xác minh phải cung cấp một cách hợp lý để người dùng cuối thay đổi ngôn ngữ đang hoạt động.

Cơ chế chọn ngôn ngữ nên dễ tìm, dễ hiểu và có sẵn mà không yêu cầu kiến thức kỹ thuật. Người dùng không nên cần chỉnh sửa tệp cấu hình, sửa mã nguồn, cài đặt công cụ dành cho nhà phát triển hoặc dựa vào hành vi không được ghi lại trong tài liệu chỉ để thay đổi ngôn ngữ.

Khi hiển thị các tùy chọn ngôn ngữ, hệ thống nên nhận diện từng ngôn ngữ theo cách dễ hiểu cả với người dùng nói ngôn ngữ đó lẫn người dùng hiện đang sử dụng một ngôn ngữ đã chọn khác.

Ví dụ, một tùy chọn ngôn ngữ có thể được hiển thị bằng:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

Định dạng chính xác có thể khác nhau, nhưng ý định nên giữ nguyên: người dùng có thể nhận ra ngôn ngữ của mình, hiểu tên ngôn ngữ hiện đang hiển thị khi có thể, và nhận diện mã locale liên quan.

<a id="what-within-spec-means"></a>
## “Nằm trong đặc tả” nghĩa là gì

Khi một hệ thống được xem là **nằm trong đặc tả**, điều đó có nghĩa là Nhóm CatalystUI đã đánh giá thủ công hệ thống và thấy hợp lý để kết luận rằng nó đáp ứng các yêu cầu quốc tế hóa được mô tả bởi hạng mục xác minh này.

Điều này không yêu cầu một mẫu triển khai cứng nhắc duy nhất. Một hệ thống có thể đáp ứng yêu cầu thông qua tệp tài nguyên, bảng dịch, định tuyến theo locale, tài nguyên ngôn ngữ đã biên dịch, bản dịch dựa trên cơ sở dữ liệu, gói ngôn ngữ khi chạy hoặc một cơ chế ổn định khác phù hợp với hệ thống.

Việc xác minh quan tâm đến khả năng thực tế để người dùng truy cập hệ thống thiết yếu trong các ngôn ngữ bắt buộc, chứ không phải hệ thống có sử dụng một kiến trúc dịch cụ thể nào hay không.

<a id="what-verification-does-not-mean"></a>
## Việc xác minh không có nghĩa là gì

CatalystUI Verified cho Quốc tế hóa không bảo đảm rằng mọi bản dịch đều hoàn hảo, văn chương, tự nhiên, đầy đủ về văn hóa hoặc đủ pháp lý cho mọi khu vực.

Nó cũng không tự động xác minh khả năng truy cập, kiểu chữ, bố cục từ phải sang trái, định dạng theo locale, định dạng tiền tệ, định dạng ngày tháng, tuân thủ pháp lý hoặc yêu cầu kinh doanh khu vực trừ khi các mối quan tâm đó được bao gồm trong phạm vi quốc tế hóa được đánh giá.

Một hệ thống có thể cung cấp phạm vi bao phủ bản dịch mạnh nhưng vẫn cần đánh giá riêng về khả năng truy cập, chất lượng bản địa hóa, tuân thủ khu vực hoặc các mối quan tâm chuyên biệt khác.

<a id="why-this-verification-exists"></a>
## Vì sao việc xác minh này tồn tại

Một giao diện người dùng chỉ hữu ích khi người dùng có thể hiểu điều nó đang truyền đạt.

Nhiều hệ thống tuyên bố hỗ trợ ngôn ngữ trong khi chỉ dịch một phần nhỏ của trải nghiệm, giấu việc chọn ngôn ngữ, bỏ qua các thông báo quan trọng hoặc để các luồng công việc thiết yếu bị dịch một phần. Điều này tạo ra nhầm lẫn và ngăn người dùng tin tưởng hệ thống.

Internationalization Verification tồn tại để đặt ra một tiêu chuẩn rõ ràng hơn. Nó nhận diện các hệ thống nỗ lực nghiêm túc và thực tế để hỗ trợ người dùng trên toàn bộ tập ngôn ngữ bắt buộc của CatalystUI và cung cấp một cách hợp lý để người dùng chọn ngôn ngữ họ cần.

<a id="verification-scope"></a>
## Phạm vi xác minh

CatalystUI Verification cho Quốc tế hóa áp dụng cho hệ thống, dịch vụ, framework, ứng dụng hoặc phần triển khai được đánh giá như nó tồn tại tại thời điểm xác minh được cấp.

Một hệ thống đã được xác minh cung cấp đủ phạm vi bao phủ bản dịch thiết yếu cho các ngôn ngữ bắt buộc. Điều đó không bảo đảm rằng mọi trang, tính năng, bản phát hành, plugin, tiện ích mở rộng hoặc tích hợp bên thứ ba trong tương lai đều tự động nằm trong đặc tả.

Các sản phẩm, module, dịch vụ, gói ngôn ngữ hoặc bản sửa đổi lớn riêng biệt có thể cần đánh giá riêng tùy theo hạng mục xác minh được yêu cầu.

<a id="verification-validity"></a>
## Hiệu lực xác minh

CatalystUI Verification chỉ áp dụng cho trạng thái đã được đánh giá của hệ thống tại thời điểm xác minh được cấp.

Một hệ thống có thể giữ xác minh qua các bản cập nhật sau này miễn là nó bảo toàn nền tảng quốc tế hóa đã được xác minh. Những thay đổi nhỏ về cách diễn đạt, bản dịch được thêm vào và cập nhật nội dung thông thường không tự động làm mất hiệu lực xác minh.

Có thể cần một đánh giá mới nếu hệ thống loại bỏ hỗ trợ ngôn ngữ bắt buộc, làm hỏng việc chọn ngôn ngữ, giảm đáng kể phạm vi bao phủ bản dịch thiết yếu hoặc thay đổi kiến trúc quốc tế hóa theo cách ảnh hưởng đến hành vi đã được xác minh.

Nói cách khác, cải thiện hỗ trợ dịch thuật thường là ổn. Phá vỡ nền tảng đa ngôn ngữ đã được xác minh có thể cần được đánh giá lại.

<a id="verified-systems"></a>
## Hệ thống đã xác minh

Các hệ thống đã biết được xác minh về quốc tế hóa được liệt kê riêng trên trang CatalystUI Verified thích hợp.
