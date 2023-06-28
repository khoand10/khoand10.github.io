+++
author = "khoand"
title = "How to work with multiple Git accounts"
date = "2023-06-15"
description = "How to work with multiple Git accounts"
tags = [
    "git",
]
summary ="git setup"
+++

Việc sử dụng 2 tài khoảng github trên cùng một máy rất phổ biến nhưng việc cùng một thời điểm làm việc với 2 repository github đôi khi gây khó khăn và nhầm lẫn giữa tài khoản.
Bài hướng dẫn này mình sẽ sử dụng github.com nhưng cũng sẽ tương tự với các công cụ git khác(gitlab, bitbucket,...). Giả sử một tài khoản của công ty và một tài khoản cá nhân.

_Trước khi bắt đầu hãy chắc chắn rằng bạn biết cách setup 1 tài khoản git trước đã :D_

**1. Generating ssh-key**
```sh
$ ssh-keygen -t ed25519 -C "office_email" -f "git-office"
$ ssh-keygen -t ed25519 -C "personal_email" -f "git-personal"
...
$ ssh-keygen -t ed25519 -C "your-email-n" -f "user-n"
```
_Lưu ý: đừng quên add public key lên Github_

**2. Declare user to config file**

Thêm thông tin 2 user vừa tạo vào ~/.ssh/config.

_Lưu ý: nếu file config không tồn tại, hãy tạo ra một file mới_
```sh
Host git_office
    HostName github.com
    User git
    IdentityFile ~/.ssh/git-office
Host git_personal
    HostName github.com
    User git
    IdentityFile ~/.ssh/git-personal
```
Giải thích: 
- `git_office, git_personal`: Tên để phân biệt các tài khoản với nhau. Hãy đặt "git_office, git_personal" thành những tên có ý nghĩa đối với bạn.
- `github.com`: địa chỉ của git(có thể thay bằng gitlab.com, your-company-git.com,...)
- `~/.ssh/git-office`: link đến ssh-key chúng ta đã gen ở bước 1. Thông tin này là quan trọng nhất hãy chắc chắn link đến đúng ssh-key
  
**3. Clone with different accounts**

```bash
$ git clone git@{host name}:{repository}
```
Ví dụ link repository của trang blogs này trên github là: `git@github.com:khoand10/khoand10.github.io.git` và sử dụng tài khoản `git_personal` đã tạo ở bước một thì khi clone về  sẽ như sau.

```bash
$ git clone git@git_personal:khoand10/khoand10.github.io.git
```
Nếu đã setup project từ trước thì phải thay đổi remote url
```bash
$  git remote set-url git@git_personal:khoand10/khoand10.github.io.git
```

**4. Configure user and email**

```bash
$ cd {office project path}
$ git config user.email "office_email@gmail.com"
$ git config user.name "company username"

$ cd {personal project path}
$ git config user.email "personal-email@gmail.com"
$ git config user.name "khoand10"
```

**5. Kiểm tra kết quả**

Cuối cùng là cách kiểm tra xem mình đã config đúng hay chưa
```bash
$ ssh -T git@{host name}
```

![Image alt](../images/result.png)

Tham khảo [rahularity](https://gist.github.com/rahularity/86da20fe3858e6b311de068201d279e3)
 

<!-- ### Đầu tiên là phải biết cách setup một tài khoản git :D
google/chat-gpt

### Setup ssh-key
1. Generating ssh-key
```bash
$ ssh-keygen -t rsa -C "your-email-1" -f "user-1"
```
Giải thích: lệnh trên sẽ tạo ra cặp public key và private key cho tài khoản github có email là `your-email-1`. Output sẽ có tên là `user-1`

2. Add to config file
Open ~/.ssh/config và thêm những thông tin sau
```
Host user1
	HostName github.com
	User git
	IdentityFile ~/.ssh/user-1
```

3. Add publib key to Github



### Clone/add repository
...
### Config username and email
...
### Verify
... -->


