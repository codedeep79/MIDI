# Musical Instrument Digital Interface in C++
MIDI (Musical Instrument Digital Interface - Giao diện kỹ thuật số dành cho nhạc cụ) là chuẩn công nghiệp về nghi thức giao thông điện tử định rõ các nốt âm nhạc trong nhạc cụ điện tử như là bộ tổng hợp chính xác và ngắn gọn, để nhạc cụ điện tử và máy tính trao đổi dữ liệu, hoặc "nói", với nhau. MIDI không truyền âm thanh – nó chỉ truyền thông tin điện tử về một bản nhạc. MIDI có thế được sử dụng cho các mục đích khác, nhưng mục tiêu ban đầu cho việc phát minh MIDI vẫn là phục vụ cho âm nhạc. Chuẩn MIDI bao gồm 3 thành phần: Giao thức (protocol), Phương tiện kết nối (connector) và Dạng tập tin lưu trữ tiêu chuẩn (standard MIDI file).

Giải thích:

+ Đàn Guitar 6 dây 14 phím lần lượt từ dây to nhất đến dây nhỏ nhất là **Mi La Rê Sol Si Mí** được kí hiệu lần lượt là **E A D G B E**
+ Các nốt nhạc cơ bản trong bản nhạc từ thấp đến cao sẽ là **Đồ - Rê – Mi – Fa – Son – La – Xi**, được ký hiệu **Đô (C), Rê (D), Mi (E), Fa (F), Sol (G), La (A), Si (B)**. Trong đó khoảng cách **Mi - Fa** và **Si - Đô** là nửa cung, còn lại là một cung. 
+ Cầm cây đàn lên, **giả sử** ở **khung (hay còn gọi là phím) thứ 1 của dây Mi (dây số 1 hay số 6 đều được) là nốt Fa**, **ta biết từ Fa lên Sol là một cung, vậy nốt Sol nằm ở phím thứ 3 của dây, tức là một cung trong guitar nghĩa là cách nhau một phím, còn nửa cung là 2 phím sát nhau.** Như ở phím thứ 7 của dây Mi là nốt Si, thì phím thứ 8 là Đô ( do Si-Đô là nửa cung nên nó liền nhau)

![](http://pianominhthanh.com/wp-content/uploads/2017/07/goi-thieu-dan-guitar.jpg)

+ Để biết các nốt nhạc trên cần đàn: **Dựa vào quy tắc một cung nửa cung, ví dụ với dây Si (dây số 2) thì nó là dây Si vì nốt buông của nó là nốt Si (nốt buông là không bấm gì vào dây đó gọi là buông), theo quy tắc thì Si - Đô là nửa cung, vậy nốt Đô nằm ở phím 1 của dây 2 (dây Si), tiếp Đô-Rê là một cung, vậy thì nốt Rê nằm ở phím 3 của dây 2, tương tự như vậy với các dây khác.**
+ Dưới đây mỗi số đại diện cho nửa cung trong quãng tám trong nhạc lý để lập trình hóa ứng dụng

E (Mi) | A (La)| D (Rê)| G (Son)| B (Si)| E (Mí)
-------|-------|-------|--------|-------|------- 
-8     |-3     |2      |**7**   |11     |16
-7     |-2     |3      |8       |**12** |17
-6     |-1     |**4**  |9       |13     |18
-5     |0      |5      |10      |14     |19
-4    |1|6|11|15|20
-3    |2|**7**|**12**|16|21
-2|3|8|13|17|22
-1|**4**|9|14|18|23
0|5|10|15|19|24
1|6|11|16|20|25
2|**7**|**12**|17|21|26
3|8|13|18|22|27
**4**|9|14|19|23|28
5|10|15|20|24|29
14  |6|11|16|21|25|30

```cpp
    static const int chords[][3] =
    {
        { 12,4,7 }, // +C  E  G  = 0
        { 12,9,5 }, // +C  A  F  = 1
        { 12,8,3 }, // +C  G# D# = 2
        { 12,7,3 }, // +C  G  D# = 3
        { 12,5,8 }, // +C  F  G# = 4
        { 12,3,8 }, // +C  D# G# = 5
        { 11,2,7 }, //  B  D  G  = 6
        { 10,2,7 }, // A#  D  G  = 7
        { 14,7,5 }, // +D  G  F  = 8
        { 14,7,11 },// +D  G  B  = 9
        { 14,19,11 }// +D +G  B  = 10
    };
```

