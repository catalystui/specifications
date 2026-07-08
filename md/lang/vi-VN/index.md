<!-- Bản dịch này được tạo bởi ChatGPT và nên được một người dịch xem xét lại. -->
<!-- Hãy xóa các dòng này trong pull request sau khi bản dịch đã được xác minh. -->

![CatalystUI Verified for Programming Languages](/images/verification/verified-logo-languages.png)

# CatalystUI Verified cho ngôn ngữ lập trình

Chào mừng bạn đến với tài liệu CatalystUI Verification dành cho ngôn ngữ lập trình.

**CatalystUI Verified cho ngôn ngữ lập trình** cho biết một ngôn ngữ lập trình đã được Nhóm CatalystUI xem xét và được xác định là cung cấp các biểu diễn dữ liệu nền tảng và cấu trúc quan hệ cần thiết để diễn đạt các hệ thống tương thích với CatalystUI.

Việc xác minh này không phải là bảng xếp hạng chung các ngôn ngữ lập trình. Nó không quyết định một ngôn ngữ có tốt hơn, nhanh hơn, dễ hơn, mới hơn, phổ biến hơn hay thú vị hơn ngôn ngữ khác hay không. Thay vào đó, nó xác định liệu ngôn ngữ có cung cấp một nền tảng ổn định và thực tế cho các đặc tả mà CatalystUI Verification yêu cầu hay không.

Nói đơn giản hơn, việc xác minh này hỏi liệu một ngôn ngữ lập trình có thể biểu diễn trung thực dữ liệu và các mối quan hệ cơ bản mà CatalystUI phụ thuộc vào hay không.

## Mục đích

Ngôn ngữ lập trình tạo nên nền tảng biểu diễn bên dưới mọi implementation của CatalystUI. Trước khi một framework, thư viện, runtime, ứng dụng hoặc dịch vụ có thể tuân theo CatalystUI Stack, ngôn ngữ dùng để xây dựng nó phải có khả năng diễn đạt các khái niệm nền tảng mà mô hình phụ thuộc vào.

Đối với ngôn ngữ lập trình, điều này chủ yếu có nghĩa là hai việc:

1. Ngôn ngữ phải có khả năng biểu diễn dữ liệu nền tảng.
2. Ngôn ngữ phải có khả năng biểu diễn các mối quan hệ nền tảng giữa dữ liệu.

Những vấn đề này được định nghĩa thông qua các đặc tả nền tảng của CatalystUI. FDEFSPEC định nghĩa các biểu diễn dữ liệu nền tảng được mong đợi. FRELSPEC định nghĩa các quan hệ nền tảng được mong đợi giữa các biểu diễn đó, bao gồm collection, quan hệ bộ nhớ, operation, quan hệ threading và composite.

Một ngôn ngữ lập trình đã được xác minh cung cấp cho developer đủ sự rõ ràng và quyền kiểm soát để xây dựng các hệ thống tương thích với CatalystUI mà không phải dựa vào những workaround mong manh, không rõ ràng hoặc không ổn định cho các khái niệm cơ bản mà CatalystUI yêu cầu.

## Xác minh nghĩa là gì

Một ngôn ngữ lập trình trở thành **CatalystUI Verified** khi nó được xem xét theo các đặc tả được liệt kê trong phần này và được xác định là within spec.

Đối với Programming Language Verification, việc xem xét tập trung vào việc ngôn ngữ có thể diễn đạt các yêu cầu nền tảng được định nghĩa bởi các đặc tả áp dụng hay không. Điều này không có nghĩa bản thân ngôn ngữ là một implementation của CatalystUI. Nó có nghĩa là ngôn ngữ cung cấp một nền tảng phù hợp để xây dựng các implementation tương thích với CatalystUI.

Một ngôn ngữ không cần đáp ứng các yêu cầu này theo cùng cách với ngôn ngữ khác. Các ngôn ngữ khác nhau dùng cú pháp, hệ thống kiểu, thư viện chuẩn, compiler, runtime và design pattern khác nhau. CatalystUI Verification cho phép những khác biệt đó miễn là các khái niệm cần thiết có thể được diễn đạt rõ ràng, đáng tin cậy và nhất quán.

## “Within Spec” nghĩa là gì

Khi một ngôn ngữ lập trình được xem là **within spec**, điều đó có nghĩa Nhóm CatalystUI đã xem xét thủ công ngôn ngữ đó và thấy hợp lý khi kết luận rằng hành vi bắt buộc được mô tả bởi các đặc tả áp dụng có thể được diễn đạt trong ngôn ngữ đó.

Điều này không yêu cầu một mẫu implementation cứng nhắc duy nhất. Một ngôn ngữ có thể đáp ứng yêu cầu thông qua primitive tích hợp, tính năng thư viện chuẩn, hành vi compiler, hành vi runtime, bảo đảm được tài liệu hóa hoặc một cơ chế ổn định khác phù hợp với ngôn ngữ đó.

Xác minh quan tâm đến khả năng thực tế để biểu diễn và bảo toàn ý nghĩa của đặc tả, chứ không phải việc ngôn ngữ có dùng đúng cùng tên, cấu trúc, cú pháp hoặc thiết kế nội bộ như văn bản đặc tả hay không.

## Vì sao việc xác minh này tồn tại

CatalystUI được thiết kế xoay quanh sự rõ ràng, nhất quán và biểu diễn trung thực cách con người và máy tính tương tác. Ngôn ngữ lập trình quan trọng vì chúng quyết định developer có thể thực tế diễn đạt điều gì, các hệ thống đó có thể được mô hình hóa an toàn đến đâu và các implementation cấp cao hơn có thể được xây dựng rõ ràng đến mức nào.

Nếu một ngôn ngữ không thể cung cấp các khái niệm nền tảng bắt buộc một cách ổn định, thì các implementation CatalystUI cấp cao hơn sẽ khó được tin cậy hơn. Developer có thể bị đẩy về phía abstraction không rõ ràng, hành vi khó dự đoán, dependency mong manh hoặc việc viết lại không cần thiết chỉ để diễn đạt những ý tưởng đáng lẽ phải đáng tin cậy ngay từ đầu.

Programming Language Verification tồn tại để xác định những ngôn ngữ nào cung cấp nền tảng đủ mạnh cho công việc CatalystUI. Nó giúp developer, nhà thiết kế ngôn ngữ và tổ chức hiểu rõ hơn liệu một ngôn ngữ có phù hợp để xây dựng hệ thống tương thích với CatalystUI hay không.

## Một ngôn ngữ trở thành verified như thế nào

Để trở thành **CatalystUI Verified cho ngôn ngữ lập trình**, một ngôn ngữ phải được xem xét theo các đặc tả được liệt kê trong phần này.

Quy trình chung là:

1. Các đặc tả CatalystUI áp dụng được xác định.
2. Ngôn ngữ được xem xét theo từng đặc tả bắt buộc.
3. Nhóm CatalystUI xác định liệu ngôn ngữ có đáp ứng mục đích và yêu cầu của các đặc tả hay không.
4. Nếu ngôn ngữ được xác định là within spec, nó có thể được cấp CatalystUI Verification.
5. Khi đã được xác minh, ngôn ngữ có thể được liệt kê trên trang [Verified Languages](/verified/).

Việc xem xét có thể cân nhắc tài liệu chính thức của ngôn ngữ, hành vi thư viện chuẩn, hành vi compiler, hành vi runtime, ví dụ implementation, test case và bằng chứng khác cần thiết để xác định liệu ngôn ngữ có đáp ứng yêu cầu hay không.

Hành vi compiler và runtime có thể được cân nhắc trong review khi hành vi đó là một phần của cách ngôn ngữ thường được dùng và được dùng chính thức. Tuy nhiên, việc xác minh một ngôn ngữ lập trình không tự động xác minh mọi compiler, runtime, package, framework, library, application hoặc tool trong hệ sinh thái của ngôn ngữ đó.

## Đặc tả áp dụng

Các đặc tả được liệt kê trong phần này định nghĩa những yêu cầu dùng cho Programming Language Verification.

Đối với ngôn ngữ lập trình, nền tảng đang hoạt động hiện tập trung vào các nhóm đặc tả sau:

* **FDEFSPEC**, định nghĩa các biểu diễn dữ liệu nền tảng.
* **FRELSPEC**, định nghĩa các quan hệ nền tảng giữa các biểu diễn dữ liệu.

Cùng nhau, các đặc tả này thiết lập nền tảng tối thiểu cần thiết để một ngôn ngữ lập trình biểu diễn các hệ thống tương thích với CatalystUI.

Các đặc tả bổ sung có thể được giới thiệu sau cho những nhóm xác minh chuyên biệt hơn. Các đặc tả đó có thể định nghĩa yêu cầu implementation cấp cao hơn, platform, accessibility, internationalization, framework, service hoặc runtime. Tuy nhiên, các đặc tả sau này xây dựng trên nền tảng thay vì thay thế nó.

Một ngôn ngữ lập trình trở thành verified bằng cách đáp ứng các đặc tả bắt buộc cho nhóm này. Ngôn ngữ đó không được kỳ vọng đáp ứng những yêu cầu implementation-specific không liên quan trừ khi các yêu cầu đó được thêm vào Programming Language Verification.

## Phạm vi xác minh

CatalystUI Verification cho ngôn ngữ lập trình áp dụng cho ngôn ngữ lập trình ở trạng thái đã được review.

Một ngôn ngữ verified cung cấp nền tảng phù hợp cho phát triển tương thích với CatalystUI. Nó không bảo đảm rằng mọi project viết bằng ngôn ngữ đó đều tuân theo CatalystUI đúng cách, và cũng không tự động xác minh hệ sinh thái xung quanh.

Các tool, library, framework, runtime, application, service hoặc implementation riêng biệt có thể cần review riêng tùy theo nhóm xác minh đang được yêu cầu.

Vì vậy, Programming Language Verification nên được hiểu là một kiểm tra nền tảng. Nó xác nhận rằng ngôn ngữ có thể biểu diễn các khái niệm bắt buộc. Nó không xác nhận rằng mọi cách dùng ngôn ngữ đều áp dụng các khái niệm đó đúng cách.

## Hiệu lực xác minh

CatalystUI Verification chỉ áp dụng cho trạng thái đã được review của một ngôn ngữ lập trình tại thời điểm việc xác minh được phát hành.

Ngôn ngữ lập trình được xem là trường hợp đặc biệt vì nhiều ngôn ngữ duy trì compatibility qua nhiều phiên bản. Một ngôn ngữ có thể giữ verification qua các phiên bản sau miễn là nó duy trì backward compatibility với những feature, primitive, representation và behavior mà review ban đầu dựa vào.

Chỉ riêng feature mới của ngôn ngữ không làm mất hiệu lực verification. Một phiên bản tương lai có thể cần review mới chỉ khi nó loại bỏ, phá vỡ hoặc thay đổi đáng kể nền tảng đã được verified.

Nói cách khác, mở rộng một ngôn ngữ thường là ổn. Phá vỡ phần nền tảng đã verified có thể cần review.

## Ngôn ngữ đã verified

Các ngôn ngữ lập trình đã known verified được liệt kê riêng trên trang [Verified Languages](/verified/).
