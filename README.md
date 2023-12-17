# __**KCSC_Recruitment**__ 
## _Real Warmup (Reverse)_

**Description:** 

[https://raw.githubusercontent.com/un1dt5/KCSC_Recruitment/f5af0df4865faf5eaee6eb310d5730544ce07bda/Warmup1.png](https://github.com/un1dt5/KCSC_Recruitment/blob/f5af0df4865faf5eaee6eb310d5730544ce07bda/Warmup1.png)

### Solution
Đề bài cho 1 file .exe, tải về rồi ném nó vào DetectItEasy ta thấy compiler MinGW (có thể được viết bằng C)
(img2)

Load IDA lên xem thử nào
(img3)

Ngay function Main có 1 string trong khá là sú
> S0NTQ3tDaDQwYF9NfF98bjlgX0QzTidfVjAxJ183N1wvX0tDU0N9

Dùng Base64 Decode thử và...
Done!
(img4)

Flag:
 >KCSC{Ch40`_M|_|n9`_D3N'_V01'_77\/_KCSC}

~~bruh why did it format like this...~~

## _VBS (Forensic)_

**Description:** 
 (img0)

### Solution
Đề bài cho 1 file zip, nén 1 file .vbs, giải nén nó ra và... ồ
(img1)
Tưởng đọc sót đề, check lại không thấy có password
Hmm, thử crack xem sao
(img2)
Done, password là:
> kma9239

Giải nén ra và đọc file, tìm được 1 link pastebin
(img3)
Có 1 string encode dạng base64, decode ta được flag
(img4)

Flag:
> KCSC{Vb4_h01_lor""_ae_th0ng_c4m_=(((}

## _an-tơ-nây-típ (Forensic)_

**Description:** 
 (img0)
> task's description

### Solution
Đề bài là Alternative, hint1 là ADvertiSement (ADS in hoa)
=> Alternate Data Stream

Tải file về giải nén có 2 folder, tập trung vào folder Download tại nó nhiều file trông sú
(img1)

Mở PowerShell trong folder và chạy lệnh để tìm ADS (lọc bớt file thì có file test8.txt dính payload)
(img2)
 
 Ta chạy tiếp lệnh để đọc nội dung file payload.ps1
 (img3)
Now what is going on here

Chia các câu lệnh ra cho dễ đọc
(img4)

Và cho chạy thử trên PowerShell:
(img5)

Và chúng ta có flag:
> KCSC{B1_@u4n_m4n_1s_7h3_b3st}

~~*Làm xong 2 bài rồi mới đọc Note có thể có malware 💀*~~

## _Pokemon Hof Panel Level 1 (Web)_

**Description:** 
 (img0)

### Solution
Đề bài cho 1 web ~~cute~~ nhập tên và chọn pokemon
(img1)

Ô
(img2)

Thử đọc Cookie
(img3)

Value của trainer_data giống dạng base64
> Tzo3OiJUcmFpbmVyIjozOntzOjQ6Im5hbWUiO3M6NjoidW4xZHQ1IjtzOjc6InN0YXJ0ZXIiO3M6OToiQnVsYmFzYXVyIjtzOjEwOiJpc0NoYW1waW9uIjtiOjA7fQ%3D%3D

Đem decode ta được
> O:7:"Trainer":3 {s:4:"name";s:6:"un1dt5";s:7:"starter";s:9:"Bulbasaur";s:10:"isChampion";b:0;}

Đổi thử "isChampion";b:1;, encode lại rồi ném vào Cookie, refresh trang và
(img4)

Flag:
> KCSC{n0w_y0u_kn0w_s3r1al1z3_f0m4rt}

## _Ez_Ceasar (Crypto)_

**Description:** 
 (img0)

### Solution
Đề bài cho file nén chứa 1 script Python, tải về giải nén rồi đọc code
(img1)

Cuối script có cho sẵn `ct='ldtdMdEQ8F7NC8Nd1F88CSF1NF3TNdBB1O'`
Giờ thì viết code để giải mã flag
(img2)

Found it!
(img3)

Flag
> KCSC{C3as4r_1s_Cl4ss1c4l_4nd_C00l}

## _A gift for pwners (Pwn)_

**Description:** 
 (img0)

### Solution
Đề bài cho 1 file không có extension tên `gift`

Mở bằng Notepad đọc thử
OK banh mắt ra tìm flag thôi
(img2)

Flag
> KCSC{A_gift_for_the_pwners_0xdeadbeef}
