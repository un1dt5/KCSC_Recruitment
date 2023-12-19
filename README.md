# __**KCSC_Recruitment**__ 
## _Real Warmup (Reverse)_

**Description:** 

![Warmup1](Warmup1.png)

### Solution
Đề bài cho 1 file .exe, tải về rồi ném nó vào DetectItEasy ta thấy compiler MinGW (có thể được viết bằng C)

![Warmup2](Warmup2.png)

Load IDA lên xem thử nào

![Warmup3](Warmup3.png)

Ngay function Main có 1 string trong khá là sú
> S0NTQ3tDaDQwYF9NfF98bjlgX0QzTidfVjAxJ183N1wvX0tDU0N9

Dùng Base64 Decode và...
Done!

Flag:
 >KCSC{Ch40`_M|_|n9`_D3N'_V01'_77\/_KCSC}

~~bruh why is it formatted like that~~

## _VBS (Forensic)_

![vbs1](vbs1.png)

### Solution
Đề bài cho 1 file zip, nén 1 file .vbs, giải nén nó ra và... file có đặt password
Tưởng đọc sót đề, check lại không thấy có password

Hmm, thử crack xem sao

![vbs2](vbs2.png)

Done, password là:
> kma9239

Giải nén ra và đọc file, tìm được 1 link pastebin

![vbs3](vbs3.png)

Có 1 string encode dạng base64, decode ta được flag

![vbs4](vbs4.png)

Flag:
> KCSC{Vb4_h01_lor""_ae_th0ng_c4m_=(((}

## _an-tơ-nây-típ (Forensic)_

![ads0](ads0.png)

### Solution
Đề bài là Alternative, hint1 là ADvertiSement (ADS in hoa)
=> Alternate Data Stream

Tải file về giải nén có 2 folder, tập trung vào folder Download tại nó nhiều file trông sú

![ads1](ads1.png)

Mở PowerShell trong folder và chạy lệnh để tìm ADS (lọc bớt file thì có file test8.txt dính payload)

![ads2](ads2.png)
 
Ta chạy tiếp lệnh để đọc nội dung file payload.ps1

![ads3](ads3.png)
Now what is going on here

Chia các câu lệnh ra cho dễ đọc

![ads4](ads4.png)

Và cho chạy thử trên PowerShell:

![ads5](ads5.png)

Và chúng ta có flag:
> KCSC{B1_@u4n_m4n_1s_7h3_b3st}

~~*Làm xong 2 bài rồi mới đọc Note có thể có malware 💀*~~

## _Pokemon Hof Panel Level 1 (Web)_

![hof0](hof0.png)

### Solution
Đề bài cho 1 web ~~cute~~ nhập tên và chọn pokemon
![hof1](hof1.png)

Ô

![hof2](hof2.png)

Thử đọc Cookie

![hof3](hof3.png)

Value của trainer_data giống dạng base64
> Tzo3OiJUcmFpbmVyIjozOntzOjQ6Im5hbWUiO3M6NjoidW4xZHQ1IjtzOjc6InN0YXJ0ZXIiO3M6OToiQnVsYmFzYXVyIjtzOjEwOiJpc0NoYW1waW9uIjtiOjA7fQ%3D%3D

Đem decode ta được
> O:7:"Trainer":3 {s:4:"name";s:6:"un1dt5";s:7:"starter";s:9:"Bulbasaur";s:10:"isChampion";b:0;}

Đổi thử "isChampion";b:1;, encode lại rồi ném vào Cookie, refresh trang và

![hof4](hof4.png)

Flag:
> KCSC{n0w_y0u_kn0w_s3r1al1z3_f0m4rt}

## _Ez_Ceasar (Crypto)_

![ez0](ez0.png)

### Solution
Đề bài cho file nén chứa 1 script Python, tải về giải nén rồi đọc code

![ez1](ez1.png)

Cuối script có cho sẵn `ct='ldtdMdEQ8F7NC8Nd1F88CSF1NF3TNdBB1O'`
Giờ thì viết code để giải mã flag

![ez2](ez2.png)

Found it!

![ez3](ez3.png)

Flag
> KCSC{C3as4r_1s_Cl4ss1c4l_4nd_C00l}

## _A gift for pwners (Pwn)_

![gift0](gift0.png)

### Solution
Đề bài cho 1 file không có extension tên `gift`

Mở bằng Notepad đọc thử và banh mắt ra tìm flag thôi

![gift1](gift1.png)

Flag
> KCSC{A_gift_for_the_pwners_0xdeadbeef}

(Post Ending)
## _ログ分析 (Forensic)_

**Description:** 

![log0](log0.png)

### Solution
Đề bài cho file zip chứa Windows Event Logs, nc vào server đã cho là form các câu hỏi về phân tích log

Question 1: What is the computer name of Franky machine? (for example: BenjaminHungTran)
Đọc trong tất cả file log đều thấy tên máy là FanAnhB => Answer

![log1](log1.png)
> Answer: FanAnhB

Question 2: Which user accidentally activated the malware? (for example: adam)
Nhận thấy trong hầu hết các log đều có user "ethan", bên cạnh đó file "sadboy.bat" ~~trông rất sú~~ được kích hoạt tải về khi mở file "kcsclogo.xlsm" ~~rầu quá azai~~

![log2](log2.png)
> Answer: ethan

Question 3: What is the ip address of C2 server? (for example: 6.9.69.96)
Ngay log bên trên cũng chứa thông tin ip server của attacker

> Answer: 192.168.11.129

Question 4: Which is the malicious file automatically run when machine start? (for example: bundau.dll)
Lần theo dấu vết của azai buồn ta tìm thấy file được copy vào folder Startup của Windows, sau đó đã đổi tên thành "YW5obGFuZ2NvYw.bat"

![log3](log3.png)
> Answer: YW5obGFuZ2NvYw.bat

Question 5: What is the MD5 hash of a connect-back shell file? (for example: d41d8cd98f00b204e9800998ecf8427e)
~~Tới câu này em thành sadboy luôn~~
Trong câu hỏi nói tới connect-back shell file là file shell để gửi remote command, tìm trong PowerShell Operational log đã thấy file rshell.ps1 (rất sure là nó rồi), giờ phải build lại file tương tự để check md5

![log4](log4.png)

Lần đầu copy y chang trong log (obfuscated) vào file txt rồi đổi extension, ném vào linux để chạy md5sum nhưng ra sai mã (có lẽ em bị lỗi trong lúc copy)
Lại nghĩ phải deobfuscate file mới đúng, đi tìm payload rồi build lại, vẫn sai (cái này sai nặng)
Tới lúc đã kết thúc, sau khi được các anh thông não thì copy lại mất vài lần mới ra được file chuẩn
update: thiếu cái xuống dòng nên sai ~~chôn quá azai buồn~~

![log5](log5.png)
> Answer: cb43c6882e42767610cb09f3012805e6

Question 6: Which file did the attacker exfiltrate? (for example: hinhlolicucnet.jpg)
Sort log theo thời gian đọc thấy attacker dump file lsass.dmp rồi lấy trộm về server

![log6](log6.png)
![log7](log7.png)
> Answer: lsass.dmp

Question 7: Which user credentials could be leaked? (for example: Yuzu)
File lsass.dmp chứa credential của các user
Tiếp tục sort log tìm lệnh attacker đã dùng, tìm thấy "net user /domain"

![log8](log8.png)
> Answer: administrator

![log9](log9.png)
Flag
> KCSC{521f1068aee21539b0cb5ea74883018b}
