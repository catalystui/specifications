<!-- Bản dịch này được ChatGPT tạo ra và cần được người dịch xem xét. -->
<!-- Xóa các dòng này trong một pull request sau khi bản dịch được xác minh. -->

# FRELSPEC

<br/>

> **Đặc tả quan hệ nền tảng**<br/>
> Bản sửa đổi 2.1<br/>
> Ngày 24 tháng 11 năm 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Bảo lưu mọi quyền.<br/>
> <br/>
> Các định nghĩa và khái niệm được trình bày ở đây mô tả các cấu trúc toán học nền tảng và có thể được diễn đạt lại tự do.

## Giới thiệu

**Đặc tả quan hệ nền tảng (FRELSPEC)** thiết lập các cấu trúc quan hệ cốt lõi làm nền tảng cho hệ sinh thái CatalystUI. Mục đích là cung cấp cách hiểu thống nhất về quan hệ giữa bộ nhớ, các tập hợp dữ liệu, thao tác và cấu trúc hợp thành trong tài liệu, đặc tả, triển khai và đánh giá xác minh, bảo đảm tính nhất quán, rõ ràng và đồng bộ.

Bằng cách định nghĩa chính xác và ổn định các quan hệ giữa những khái niệm nền tảng, FRELSPEC cung cấp điểm tham chiếu chung cho các đặc tả cấp cao hơn, đồng thời cho phép từng triển khai thiết lập quy tắc và hành vi riêng. Nhờ đó, nhà phát triển, người đánh giá và người triển khai có thể suy luận trên cùng một cơ sở khi xác định liệu ngôn ngữ, dịch vụ, framework hay hệ thống có biểu diễn được các cấu trúc quan hệ cần thiết để phù hợp với đặc tả hay không.

> [!IMPORTANT]
>
> Chúng tôi biểu đạt các định nghĩa bằng một dạng ký pháp dẫn xuất từ [lý thuyết tập hợp](https://en.wikipedia.org/wiki/Set_theory). Cách tiếp cận này cung cấp định nghĩa chính xác, không mơ hồ, đồng thời duy trì tính rõ ràng và súc tích. Các định nghĩa được tổ chức để dễ tham chiếu, diễn giải rõ ràng và có hệ thống phân cấp khái niệm nhất quán.

## Mục lục

- [FRELSPEC](#frelspec)
  - [Giới thiệu](#giới-thiệu)
  - [Mục lục](#mục-lục)
  - [Các bản sửa đổi](#các-bản-sửa-đổi)
    - [Bản sửa đổi 2.1](#bản-sửa-đổi-21)
    - [Bản sửa đổi 2](#bản-sửa-đổi-2)
  - [Bộ nhớ](#bộ-nhớ)
    - [Word](#word)
    - [Address](#address)
      - [Address()](#address-1)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [Tập hợp dữ liệu](#tập-hợp-dữ-liệu)
    - [Set](#set)
      - [Set()](#set-1)
    - [Map](#map)
      - [Map(k)](#mapk)
    - [Array](#array)
      - [Array(i)](#arrayi)
    - [File](#file)
      - [File(i)](#filei)
    - [Stream](#stream)
      - [Stream()](#stream-1)
  - [Thao tác](#thao-tác)
    - [Instruction](#instruction)
    - [Procedure](#procedure)
      - [Procedure(k)](#procedurek)
    - [Function](#function)
      - [Function(k)](#functionk)
  - [Luồng thực thi](#luồng-thực-thi)
    - [Process](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [Cấu trúc hợp thành](#cấu-trúc-hợp-thành)
    - [Member](#member)
    - [Object](#object)
      - [Object(k)](#objectk)
    - [Field](#field)
      - [Field(o,k)](#fieldok)
    - [Method](#method)
      - [Method(o,k)](#methodok)
    - [Property](#property)
      - [Property(o,k)](#propertyok)
      - [Get(o,k)](#getok)
      - [Set(o,k)](#setok)
    - [Structure](#structure)
      - [Structure(s,k)](#structuresk)
    - [Class](#class)
      - [Class(c,a)](#classca)
    - [Interface](#interface)
      - [Interface(r,o)](#interfacero)

## Các bản sửa đổi

### Bản sửa đổi 2.1

**Ngày 24 tháng 11 năm 2026**

Chúng tôi tinh chỉnh định nghĩa File để thiết lập cơ chế phân giải dữ liệu do siêu dữ liệu chi phối và định nghĩa lại Stream như một cơ chế độc lập để tạo hoặc truy xuất dữ liệu tuần tự. Những thay đổi này cho phép luồng biểu diễn dãy hữu hạn hoặc vô hạn mà không áp đặt thêm ràng buộc lên các tập hợp dữ liệu khác.

### Bản sửa đổi 2

**Ngày 21 tháng 11 năm 2026**

Chúng tôi phát hiện sự thiếu nhất quán trong cách biểu diễn bộ nhớ và giá trị lưu trữ bằng byte và mảng byte. Chúng tôi thiết lập Word làm biểu diễn bộ nhớ nền tảng, thống nhất quan hệ giữa Bộ nhớ, Thao tác và Cấu trúc hợp thành.

Chúng tôi phát hiện sự thiếu nhất quán trong việc đánh chỉ số mảng và quan hệ giữa các tập hợp dữ liệu. Chúng tôi chuẩn hóa các chỉ số hữu hạn, liên tiếp và làm rõ quan hệ giữa Array, File và Stream.

Chúng tôi phát hiện sự dư thừa và mơ hồ trong quan hệ thực thi và hợp thành. Chúng tôi tinh chỉnh thủ tục, hàm, bộ điều phối và quan hệ đối tượng để giải quyết các vấn đề này, đồng thời duy trì tính độc lập với triển khai.

## Bộ nhớ

### Word

Một từ là bất kỳ dãy bit $w \in \mathrm{Bit}^n$ nào được lưu trong bộ nhớ, sao cho $n \in \mathbb{N}^+$.

### Address

Một địa chỉ là bất kỳ từ $a \in A$ nào, trong đó $A$ là tập hợp các từ, sao cho $a$ xác định duy nhất một vị trí trong cấu trúc bộ nhớ được chỉ định.

#### Address()

> $\mathrm{Address}(b_0,\dots,b_{n-1}) = \sum_{i=0}^{n-1} b_i \cdot 2^{n-1-i} \in \{m \in \mathbb{Z} \mid 0 \leq m \leq 2^n-1\}$

### Pointer

Một con trỏ là bất kỳ hàm $f_p : \{a\} \to B$ nào sao cho $a \in A$ là địa chỉ và $B$ là tập hợp các từ, trong đó mỗi lần áp dụng $f_p$ sẽ tính giá trị từ được lưu tại vị trí bộ nhớ do $a$ xác định.

#### Pointer()

> Giả sử $f_m : A \to B$ là ánh xạ bộ nhớ.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

Một biến là bất kỳ hàm $f_v : \{k\} \to B$ nào sao cho $k$ là khóa và $B$ là tập hợp các từ, trong đó biến mở rộng con trỏ bằng cách liên kết khóa với địa chỉ và tính giá trị từ được lưu tại địa chỉ đó.

#### Variable(k)

> Giả sử $f_b : \{k\} \to \{a\}$ là hàm liên kết của biến.
>
> Giả sử $f_p : \{a\} \to B$ là con trỏ.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

Một hằng là bất kỳ biến $f_c : \{k\} \to B$ nào sao cho $k$ là khóa và $B$ là tập hợp các từ, trong đó từ liên kết với $k$ không thể thay đổi sau khi được gán.

#### Constant(k)

> Giả sử $b_0 \in B$ là từ được gán cho $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ sau khi $b_0$ được gán.

## Tập hợp dữ liệu

### Set

Một tập hợp là bất kỳ bộ sưu tập hữu hạn, không có thứ tự gồm các từ phân biệt.

#### Set()

> Giả sử $B$ là tập hợp các từ.
>
> $S \subseteq B, |S| \in \mathbb{N}_0$

### Map

Một ánh xạ là bất kỳ hàm $f_m : K \to V$ nào sao cho $K$ là tập hợp khóa và $V$ là tập hợp giá trị, trong đó mỗi khóa liên kết với đúng một giá trị.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Một mảng là bất kỳ hàm $f_a : I \to V$ nào sao cho $I \subseteq \mathbb{N}$ là tập hợp hữu hạn, liên tiếp các chỉ số nguyên và $V$ là tập hợp các từ, trong đó mỗi chỉ số xác định đúng một giá trị.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

Một tệp là bất kỳ bộ $(f_m,d)$ nào sao cho $d$ là mảng các từ và $f_m : I \times \{d\} \to \mathrm{Array}$ là hàm siêu dữ liệu được biểu diễn bằng mảng các từ, trong đó $I$ là tập hợp hữu hạn, liên tiếp các chỉ số nguyên và $f_m$ xác định cách phân giải dữ liệu từ $d$.

#### File(i)

> Giả sử $(f_m,d)$ là tệp.
>
> $\mathrm{File}(i) = f_m(i,d),\quad i \in I$

### Stream

Một luồng là bất kỳ hàm $f_s$ nào sao cho mỗi lần áp dụng $f_s$ sinh ra đoạn tiếp theo $c$ trong dãy hữu hạn hoặc vô hạn, trong đó $f_s$ thiết lập cơ chế tạo hoặc truy xuất dữ liệu tuần tự.

#### Stream()

> Giả sử $f_c : K \to C$ là hàm phân giải đoạn, trong đó $K \subseteq \mathbb{N}$ là tập hợp liên tiếp các chỉ số nguyên và $C$ là tập hợp các đoạn.
>
> Giả sử $k \in K$ là chỉ số của đoạn tiếp theo.
>
> $\mathrm{Stream}() = f_s() = f_c(k)$, tiến $k$ sau mỗi lần áp dụng.

## Thao tác

### Instruction

Một lệnh là bất kỳ từ hoặc bộ hữu hạn các từ $i \in B$ nào sao cho $B$ là tập hợp các từ hoặc bộ hữu hạn các từ, trong đó mỗi lệnh biểu diễn một thao tác tính toán duy nhất cần thực hiện.

### Procedure

Một thủ tục là bất kỳ biến $f_{proc} : \{k\} \to B$ nào sao cho $f_{proc}(k)$ biểu diễn mảng lệnh $f_a : I \to V$, trong đó việc thực thi thủ tục thực hiện từng lệnh theo thứ tự chỉ số.

#### Procedure(k)

> $\mathrm{Procedure}(k)$ là việc thực thi mỗi $f_a(i)$ theo thứ tự tăng dần của $i \in I$.

### Function

Một hàm là bất kỳ thủ tục $f_{func} : \{k\} \to B$ nào mà khi thực thi trả về địa chỉ $a_r \in A$ xác định từ kết quả hoặc từ đầu tiên của mảng từ biểu diễn kết quả.

#### Function(k)

> Giả sử $f_m : A \to B$ là ánh xạ bộ nhớ, trong đó $a_r \in A$ xác định từ kết quả $r \in B$.
>
> $\mathrm{Function}(k) = a_r, f_m(a_r) = r$

## Luồng thực thi

### Process

Một tiến trình là bất kỳ luồng thực thi có giới hạn nào nhận đầu vào, thực thi một hay nhiều thủ tục hoặc hàm và tạo đầu ra, trong đó tiến trình biểu diễn một đơn vị biến đổi riêng biệt trong hệ thống.

### Thread

Một luồng thực thi (thread) là bất kỳ dòng thực thi nào nằm trong tiến trình, cung cấp một đường thực thi các thủ tục hoặc hàm thuộc tiến trình đó.

#### Thread(p)

> Giả sử $p$ là tiến trình.
>
> Giả sử $(w_0, \dots, w_n)$ là bộ hữu hạn các thủ tục hoặc hàm thuộc $p$.
>
> $\mathrm{Thread}(p)$ là việc thực thi mỗi $w_j$ theo thứ tự tăng dần của $j$ trong $p$.

### Dispatcher

Một bộ điều phối là bất kỳ bộ $(t,W,f_d)$ nào sao cho $t$ là luồng thực thi, $W$ là tập hợp thủ tục hoặc hàm được chấp nhận làm công việc, và $f_d$ là quy tắc điều phối chọn công việc từ $W$, trong đó bộ điều phối làm cho công việc đã chọn được thực thi trên $t$ theo quy tắc đó.

#### Dispatcher(t)

> Giả sử $t$ là luồng thực thi.
>
> Giả sử $W$ là tập hợp thủ tục hoặc hàm được bộ điều phối chấp nhận, trong đó $\forall w \in W$, $w$ là thủ tục hoặc hàm.
>
> Giả sử $f_d : \mathcal{P}^+(W) \to W$ là quy tắc điều phối chọn công việc từ tập con khác rỗng của công việc đã chấp nhận.
>
> $\mathrm{Dispatcher}(t)$ là việc thực thi mỗi $f_d(W')$ được chọn trên $t$, trong đó $W' \subseteq W$, $W' \neq \varnothing$ và $f_d(W') \in W'$.

## Cấu trúc hợp thành

### Member

Một thành viên là bất kỳ phần tử $m \in M$ nào sao cho $M$ là tập hợp phần tử và $f_o : K \to M$ là ánh xạ thành viên của đối tượng, trong đó $m = f_o(k)$ với một khóa $k \in K$ nào đó.

### Object

Một đối tượng là bất kỳ bộ $(a,K,f_o)$ nào sao cho $a \in A$ là địa chỉ, $K$ là tập hợp khóa và $f_o : K \to M$ là ánh xạ thành viên, trong đó $M$ là tập hợp phần tử, cho phép đối tượng biểu diễn cấu trúc hợp thành có thể định địa chỉ mà các thành viên được gán cho khóa thông qua $f_o$.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

Một trường là bất kỳ bộ $(o,k,m)$ nào sao cho $o = (a,K,f_o)$ là đối tượng, $k \in K$ là khóa và $m = f_o(k)$ là thành viên, trong đó trường biểu diễn một thành viên có khóa được phân giải từ ánh xạ thành viên của đối tượng.

#### Field(o,k)

> Giả sử $o = (a,K,f_o)$ là đối tượng.
>
> $\mathrm{Field}(o,k) = (o,k,f_o(k)), k \in K$

### Method

Một phương thức là bất kỳ trường $(o,k,m)$ nào sao cho $m$ là thủ tục hoặc hàm, trong đó phương thức biểu diễn thành viên có khóa và có thể thực thi của đối tượng.

#### Method(o,k)

> Giả sử $(o,k,m)$ là trường.
>
> $\mathrm{Method}(o,k) = (o,k,m)$, trong đó $m$ là thủ tục hoặc hàm.

### Property

Một thuộc tính là bất kỳ trường $(o,k,m)$ nào sao cho $m = (X,f_a)$ là ánh xạ bộ truy cập, $X = \{\mathrm{Get}, \mathrm{Set}\}$, và $f_a : X \to M$ ánh xạ mỗi bộ truy cập tới thành viên, trong đó $f_a(\mathrm{Get})$ là hàm và $f_a(\mathrm{Set})$ là thủ tục, cho phép thuộc tính định nghĩa cả hành vi truy xuất và gán của thành viên có khóa.

#### Property(o,k)

> Giả sử $(o,k,m)$ là trường, trong đó $m = (X,f_a)$ là ánh xạ bộ truy cập.
>
> $\mathrm{Property}(o,k) = (o,k,m)$

#### Get(o,k)

> Giả sử $(o,k,(X,f_a))$ là thuộc tính.
>
> $\mathrm{Get}(o,k)$ là việc áp dụng $f_a(\mathrm{Get})$.

#### Set(o,k)

> Giả sử $(o,k,(X,f_a))$ là thuộc tính.
>
> $\mathrm{Set}(o,k)$ là việc áp dụng $f_a(\mathrm{Set})$.

### Structure

Một cấu trúc (thường viết tắt là `struct`) là bất kỳ đối tượng $s = (a,K,f_s)$ nào sao cho $K$ là tập hợp khóa hữu hạn và $f_s : K \to M$ là ánh xạ thành viên có các khóa không thể thay đổi sau khi cấu trúc được gán, trong đó cấu trúc là đối tượng chuyên biệt có bố cục thành viên theo khóa cố định.

#### Structure(s,k)

> Giả sử $s = (a,K,f_s)$ là cấu trúc.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

Một lớp là bất kỳ đối tượng $c = (a_c,K_c,f_c)$ nào sao cho $K_c$ là tập hợp khóa hữu hạn và $f_c : K_c \to M$ là ánh xạ định nghĩa thành viên, trong đó lớp là đối tượng chuyên biệt có các thành viên theo khóa định nghĩa bố cục thành viên dùng để tạo các đối tượng khác.

#### Class(c,a)

> Giả sử $c = (a_c,K_c,f_c)$ là lớp.
>
> Giả sử $a \in A$ là địa chỉ được gán cho đối tượng tạo từ $c$.
>
> Giả sử $f_o : K_c \to M$ là ánh xạ thành viên tuân theo các định nghĩa của $f_c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_o)$

### Interface

Một giao diện là bất kỳ đối tượng $r = (a_r,K_r,f_r)$ nào sao cho $K_r$ là tập hợp khóa hữu hạn và $f_r : K_r \to M$ là ánh xạ yêu cầu thành viên, trong đó giao diện là đối tượng chuyên biệt có các thành viên theo khóa định nghĩa những thành viên mà đối tượng khác phải cung cấp.

#### Interface(r,o)

> Giả sử $r = (a_r,K_r,f_r)$ là giao diện.
>
> Giả sử $o = (a,K,f_o)$ là đối tượng.
>
> Giả sử $f_v : M \times M \to \{0,1\}$ là quy tắc xác thực xác định liệu một thành viên có đáp ứng yêu cầu của thành viên khác hay không.
>
> $\mathrm{Interface}(r,o)$ đúng khi $K_r \subseteq K$ và $\forall k \in K_r,\ f_v(f_o(k),f_r(k)) = 1$.
