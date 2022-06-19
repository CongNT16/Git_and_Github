# Git_and_Github

### Mục lục

[I. Mở đầu](#Modau)

[II. Các thao tác với git và github](#cacthaotacvoigitvagithub)
- [0. Repo](#repo)
- [1. Cài đặt](#caidat)

  - [1.1. Linux](#linux)
  - [1.2. Windows](#windows)

- [2. Thao tác với Repo](#thaotacvoirepo)

  - [2.1. Trên Linux](#21trenlinux)
    - [2.1.1. Tạo mới](#211taomoi)
    - [2.1.2. Clone](#212clone)
    - [2.1.3. Add, commit, push](#213addcommitpush)
    - [2.1.4. Pull](#214pull)
  - [2.2. Trên Windows](#22trenwindows)
    - [2.2.1. Tạo một repo mới](#221taomotrepomoi)
    - [2.2.2. Clone](#222clone)
    - [2.2.3. Add, commit, push, pull ](#223)

- [3. Thao tác với tổ chức trong Github](#3)
- [4. Thao tác với nhánh (branch)](#4)
- [5. Issues](#5)
	
[Tổng kết](#Tongket)

===========================

<a name="Modau"></a>
## I. Mở đầu

`Git` là một phần mềm dùng để quản lý phiên bản của mã nguồn tương tự như `SVN` nhưng có nhiều ưu điểm hơn, `Git` đang được sủ dụng rộng rãi hiện nay.

Các dự án thực tế thường có nhiều lập trình viên làm việc song song. Vì vậy, một hệ thống kiểm soát phiên bản như Git là cần thiết để đảm bảo không có xung đột code giữa các lập trình viên.

Ngoài ra, các yêu cầu trong các dự án như vậy thay đổi thường xuyên. Vì vậy, một hệ thống kiểm soát phiên bản cho phép các nhà phát triển revert và quay lại phiên bản cũ hơn của code.

Cuối cùng, đôi khi một số dự án đang được chạy song song liên quan đến cùng một cơ sở code. Trong trường hợp như vậy, khái niệm phân nhánh trong Git là rất quan trọng.

Dễ sử dụng, thao tác nhanh, gọn, lẹ và rất an toàn.
Sễ dàng kết hợp các phân nhánh (branch), có thể giúp quy trình làm việc code theo nhóm đơn giản hơn rất nhiều.
Chỉ cần clone mã nguồn từ kho chứa hoặc clone một phiên bản thay đổi nào đó từ kho chứa, hoặc một nhánh nào đó từ kho chứa là bạn có thể làm việc ở mọi lúc mọi nơi.
Deployment sản phẩm của bạn một cách không thể nào dễ dàng hơn.

#### Một số khái niệm cần làm rõ

**`Git` và `Github` khác nhau như thế nào?**

Lấy ví dụ, bạn có một đoạn script dài 20 dòng, hôm sau bạn tối ưu nó đi, chỉ còn 15 dòng, một ngày khác bạn sửa ở script đó một vài chỗ. Git ghi lại những thời điểm thay đổi đó của bạn và source code của bạn tại thời điểm đó.

Github là một trang web, cho phép bạn lưu source code của mình lên đó. Sự kết hợp hoàn hảo giữa Git và Github mang lại một sự thuận tiện không hề nhỏ cho người dùng. Bạn có thể thay đổi đoạn code của mình mọi lúc mọi nơi mà không sợ bị ghi đè lên hay bị mất dữ liệu do hỏng hóc vì dữ liệu của bạn được lưu cả trên trang web Github và máy cá nhân. Bạn cũng có thể khôi phục được code của mình về một thời điểm bất kỳ nào đó.


**Cần phải làm gì để có thể sử dụng `Github`?**

- B1: Đăng ký một tài khoản tại [github](https://github.com) và đăng nhập
(Nên học cách sử dụng ngôn ngữ `Markdown` để quản lý github được tường minh hơn)

Ngôn ngữ markdown khá đơn giản, bạn có thể đọc tại [đây](https://github.com/Laputa16/Markdown) để biết cách sử dụng.

- B2: Tạo các repo tùy mục đích, clone nó về client và code.

<a name="cacthaotacvoigitvagithub"></a>
## II. Các thao tác với Git và Github

<a name="repo"></a>
### 0. Repo

Git là một công cụ để quản lý mã nguồn. Để làm việc với repo thì bạn phải hiểu về nó. Một số điều bạn cần biết là: 

**Ba trạng thái của một repo:**

<img src=http://i.imgur.com/qkmdJSR.png>

Như hình trên bạn có thể thấy có 3 điểm cần lưu ý:

- Working dir: đây là nơi bạn thực hiện các thao tác chỉnh sửa với file mã nguồn của mình, nó có thể là eclipse, netbean, notepad++,...

- Stagging area: những sự thay đổi của bạn với file mã nguồn được lưu lại, giống như bạn ấn Save trong một file notepad.

- Git directory: nơi lưu trữ mã nguồn của bạn (ở đây là github)

Tương ứng với 3 vị trí này ta có các hành động:

- Add: lưu file thay đổi (mang tính cục bộ) - tương ứng với câu lệnh `git add`

- Commit: Ghi lại trạng thái thay đổi tại máy local (ví dụ như bạn có thể ấn Save nhiều lần với file README.md nhưng chỉ khi commit thì trạng thái của lần ấn Save cuối cùng trước đó mới được lưu lại) - tương ứng với câu lệnh `git commit`

- Push: Đẩy những thay đổi từ máy trạm lên server - tương đương lệnh `git push`

- Pull: đồng bộ trạng thái từ server về máy trạm - tương đương lệnh `git pull`

<a name="caidat"></a>
### 1. Cài đặt

<a name="linux"></a>
#### 1.1. Linux

Với OS là Ubuntu:

> apt-get install git
	
Với OS là Fedora, Centos

> yum instal git

Các thiết lập ban đầu:

- Bạn cần thiết lập tên và email của mình để mỗi khi commit lên server sẽ nhận biết được ai commit lên vì một repo có thể có nhiều người tham gia.
	
> git config --global user.name "Your name"

> git config --global user.email "Your email"

- Lựa chọn trình soạn thảo mặc định, có thể là notepad++, vi, vim, nano,...

> git config --global core.editor vi

- Liệt kê các thiết lập:

> git config --list

**Liên kết với tài khoản github bằng SSH**

> ssh-keygen -t rsa

```sh
Enter file in which to save the key (/root/.ssh/id_rsa): [Press enter]
Enter passphrase (empty for no passphrase): [Press enter]
Enter same passphrase again: [Press enter]
Your identification has been saved in /root/.ssh/id_rsa.
Your public key has been saved in /root/.ssh/id_rsa.pub.
```

Nếu bạn nhập passphrase thì hãy nhớ pass này!

Kết quả:
> ls ~/.ssh/

```sh
id_rsa       id_rsa.pub   known_hosts
```

> ssh-agent -s

> ssh-add ~/.ssh/id_rsa

> cat ~/.ssh/id_rsa.pub

copy đoạn mã này

Truy cập đường dẫn sau https://github.com/settings/ssh (đảm bảo bạn đã đăng nhập vào github), chọn Add SSH key, đặt tên cho key này tại `Title` và paste nội dung vừa copy vào ô `Key`

<img src=http://i.imgur.com/zuxavZ5.png>

Lúc này bạn đã có thể commit lên github tại máy local mà không cần nhập username và password.

<a name="windows"></a>
#### 1.2. Windows	

Download tại địa chỉ: https://windows.github.com/

Cài đặt bình thường, yêu cầu phải có .NET 4.5


Thêm tài khoản Github:

- Click vào tool and options (hình bánh răng cạnh biểu tượng Sync) chọn options, Add account. Khai báo username và password trên github.

- Tại mục Configure git thêm Tên và email của mình


Click Update


<a name="thaotacvoirepo"></a>
### 2. Thao tác với Repo

<a name="21trenlinux"></a>
#### 2.1. Trên Linux

<a name="211taomoi"></a>
##### 2.1.1. Tạo mới

Tạo một repo mới trên trang github.com


<a name="212clone"></a>
##### 2.1.2. Clone

Clone repo đó về bằng một trong các cách sau:

**Linux**

***SSH:***
`git clone "link github"`

hoặc: `git clone "link github" /opt/demo` để clone vào thư mục /opt/demo

đối với phương pháp này các bạn cần nhập passphrase của ~/.ssh/id_rsa (có thể không cần nếu bạn không đặt passphrase)

***HTTPS:***
`git clone "link github"`

hoặc: `git clone "link github" /opt/demo` để clone vào thư mục /opt/demo

Để lấy các link SSH, HTTPS này ta làm như sau: Click vào các hyperlink HTTPS hoặc SSH rồi click Copy to clipboard.

<img src=http://i.imgur.com/1DozAVz.png>

Ở đây tôi sử dụng lệnh `git clone "link github"`

Lúc này trong thư mục hiện tại sẽ có thêm thư mục demo1 chứa các file trong repo trên github.

Chuyển vào thư mục này:

> cd demo1/

> ls

Lúc này sẽ thấy trong thư mục này có file `README.md`. Để sửa file này ta có thể sử dụng bất cứ trình soạn thảo nào, chẳng hạn vi, nano, gedit,...
 
> vi README.md

Thêm vào nội dung như sau:

```
Xin chao!
```

Tạo một thư mục mới, chẳng hạn tên là script để chứa các script của tôi.

> mkdir script

Tạo một script mới trong thư mục đó.

> vi script/script1.sh

```sh
#!/bin/sh
echo "Hello Python Vietnam"
sleep 10
```

bằng cách tương tự các bạn có thể tạo thêm nhiều thư mục, file hướng dẫn, cấu hình, script,... tùy ý

<a name="213addcommitpush"></a>
##### 2.1.3. Add, commit, push

Để thực hiện hành động `add` ta sử dụng lệnh sau

> git add README.md
để `add` file README.md

hoặc `git add *` để add tất cả các file hiện có.
 
Để thự hiện hành động commit file README.md ta thực hiện lệnh
> git commit README.md

hoặc `git commit *` để commit tất cả.

ta nên thêm tham số -m để ghi lại một comment cho hành động đó
 
> git commit README.md -m "ducnc sua doi" 

Lúc này các thay đổi của bạn đã được lưu lại trên máy cục bộ. Để đồng bộ lên server Github ta thực hiện lệnh:

> git push origin master

=> nhập passphrase (nếu bạn đặt passphrase ở mục 1.1.) với phương pháp clone ssh hoặc nhập username, password nếu clone bằng https

<img src=http://i.imgur.com/VOPSzBT.png>

Lúc này trở lại trang github.com và xem `repo script` lúc đầu sẽ thấy các commit của ta đã được đẩy lên.


Một cách khác nếu bạn không muốn thực hiện clone về máy như bước trên thì bạn có thể làm như sau:

- Tạo một repo mới trên github.com mà không tạo file README.md (giả sử ở đây là repo demo2)

- Tại máy local tạo một thư mục để chứa repo mới này. Ví dụ:

> mkdir /opt/demo2

> cd /opt/demo2

- Thực hiện tạo các file, thư mục như ý muốn. Sau đó thực hiện add, commit, push tương tự như trên
Nhưng ở đây cần thêm lệnh `git remote add origin $git-url` trước khi push. Tham khảo ví dụ sau:

> vi README.md

> git add README.md

> git commit README.md

hoặc `git commit README.md -m noi dung`

> git remote add origin "link github"

> git push origin master

Sau đó nhập passphrase(nếu cần) hoặc username + password (nếu sử dụng SSH)

<a name="214pull"></a>
##### 2.1.4. Pull

Giả sử trên server github của bạn có những thay đổi mà máy local chưa cập nhật những thay đổi đó. Bạn thực hiện lệnh sau:

> cd cd /opt/demo1/

> git pull

<a name="22trenwindows"></a>
#### 2.2. Trên Windows

<a name="221taomotrepomoi"></a>
##### 2.2.1. Tạo một repo mới

Tạo repo trên github.com tự như mục 2.1.1.

Tạo repo bằng phần mềm Github

- Click vào dấu cộng, chọn tab Create, đặt tên và chọn đường dẫn cho repo mới

<img src=http://i.imgur.com/MXrpZZu.png>

- Tuy nhiên repo mới sinh ra mới chỉ có ở máy trạm, tại mục `Other`. Chọn chuột phải vào repo đó và chọn `Open in Explorer` để sửa nội dung của repo này.

<img src=http://i.imgur.com/v4Dkdiw.png>

- Sau khi chỉnh sửa xong, để đẩy repo đó lên github.com ta click vào `Publish this repository` và thực hiện như hình sau. Chú ý cần chọn Organization đặt repo này.



<a name="222clone"></a>
##### 2.2.2. Clone

Click vào dấu cộng, chọn tab Clone, lựa chọn tổ chức mong muốn và chọn repo cần clone



Để chỉnh sửa nội dung của repo này ta chọn chuột phải vào nó và chọn `Open in Explorer`



Lúc đó chương trình Windows Explorer sẽ mở ra thư mục chứa repo của github, bạn có thể chỉnh sửa các file trong này, tạo xóa thư mục,... một cách bình thường.

<a name="223"></a>
##### 2.2.3. Add, commit, push, pull 

Trở lại với chương trình Github ta sẽ thấy dòng `uncommited changes` tại repo ta vừa sửa. Bạn hãy điền vào đó comment và ấn `commit to master`



Lúc này sự thay đổi của bạn với mã nguồn đã được ghi lại trên máy local, để đồng bộ nó lên server github bạn hãy ấn vào biểu tượng `Sync` ở góc trên cùng bên phải.

Sau khi đồng bộ xong, quay trở lại repo trên trang github.com.



Để đồng bộ những thay đổi trên github.com về máy local (pull) ta cũng click vào biểu tượng `Sync` như bên trên.


<a name="3"></a>
### 3. Thao tác với tổ chức trong Github

Để tạo một nhóm cho nhiều người cùng làm việc ta làm như sau:

- Truy cập URL: https://github.com/settings/organizations, chọn New Organizations

- Đặt tên và email cho tổ chức



Tại mục `Choose the organization’s plan` chọn Open Source để miễn phí, nhưng lúc này các Repo trong tổ chức sẽ là public.

- Mời các thành viên cho tổ chức



Lúc này vào trang cá nhân của bạn sẽ thấy tại mục Organizations có tổ chức mới vừa tạo. Để cấu hình tổ chức này ta click thẳng vào nó.



Ở đây tôi sẽ tạo một team mới như hình sau:



Các member của team này có quyền write với các repo của team.

Với 3 mức: Read Access, Write Access, Admin Access Github cho phép chúng ta phân quyền tới các thành viên của nhóm.

Để mời một người dùng khác vào team, ta click vào team đó và search tên của người dùng cần tìm



Sau đó hệ thống sẽ yêu cầu bạn nhập password để xác thực, nếu thành công, một email xác nhận sẽ được gửi đến người được mời và người này sẽ xác nhận có tham gia vào tổ chức hay không.

Để tạo một repo cho tổ chức, ta chỉ cần click vào tổ chức đó, sau đó chọn `Create new Repostory`. Các hành động clone, add, commit,... làm như bình thường.

<a name="4"></a>
### 4. Thao tác với nhánh (branch)

```
Sẽ cập nhật và bổ sung sau
```

<a name="5"></a>
### 5. Issues


Giả sử bạn đang theo dõi repo của tôi và thấy có một số chỗ cần sửa đổi, bạn có thể comment ý kiến của mình vào Repo đó. Sau đó người quản trị sẽ xem xét, thay đổi và trả lời bạn.

Để làm việc này bạn cần vào repo đó, click vào `Issue`. 

Sau đó chọn `New issue` (màu xanh) để tạo một issue mới.


Lúc này tại Repo của người quản trị sẽ thấy một Issue mới, người quản trị có thể click vào Issue này để xem, sau đó xem xét sửa đổi, comment lại. Khi sửa đổi hoàn tất thì sẽ đóng issue đó lại.


Bằng cách tạo issue, bạn có thể đăng các câu hỏi, thắc mắc của mình cho chủ của repo đó.

<a name="Tongket"></a>
## Tổng kết 

Bài viết là bài tổng hợp những tao tác với git và github, tham khảo nhiều nguồn.
