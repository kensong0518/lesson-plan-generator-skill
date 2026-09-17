# 範例輸出：while 迴圈猜數字遊戲（八年級，2 節）

**輸入：** 主題「while 迴圈：猜數字遊戲」，八年級，2 節，Python

**輸出：**

### 學習目標
- 學生能說出 while 迴圈和 for 迴圈的差別（不知道要重複幾次時用 while）
- 學生能用 while 搭配 if / elif / else 寫出會重複詢問的程式
- 學生能用 `random.randint()` 產生隨機數，完成一個可以玩的猜數字遊戲

### 時間表（共 90 分鐘）
| 時段 | 分鐘 | 內容 |
|---|---|---|
| 暖身 | 5 | 老師心裡想一個 1～100 的數字，全班輪流猜，老師只回「太大／太小」 |
| 概念講解 | 10 | while 結構、條件成立就一直做；和 for 的差別；無窮迴圈怎麼停（Ctrl+C） |
| 示範程式 1 | 8 | 倒數計時器：while 基本用法 |
| 學生練習 1 | 12 | 練習題 1（基礎） |
| 概念講解 | 8 | `random.randint()`、`input()` 轉成 `int()`、while 裡面放 if |
| 示範程式 2 | 10 | 猜數字遊戲（固定答案版 → 隨機版） |
| 學生練習 2 | 27 | 練習題 2（進階）＋ 練習題 3（挑戰） |
| 總結回饋 | 10 | 兩組上台玩彼此的遊戲，整理常見錯誤 |

### 示範程式 1：倒數計時器
```python
count = 5
while count > 0:        # 條件成立就繼續
    print(count)
    count = count - 1   # 忘了這行就會變無窮迴圈
print("發射！")
```
預期輸出：
```
5
4
3
2
1
發射！
```

### 示範程式 2：猜數字遊戲
```python
import random

answer = random.randint(1, 100)   # 產生 1～100 的隨機整數
guess = 0
times = 0

while guess != answer:            # 還沒猜中就繼續
    guess = int(input("請猜一個 1～100 的數字："))
    times = times + 1
    if guess > answer:
        print("太大了")
    elif guess < answer:
        print("太小了")
    else:
        print("猜中了！你猜了", times, "次")
```
預期輸出（假設答案是 42，依序輸入 50、25、42）：
```
請猜一個 1～100 的數字：50
太大了
請猜一個 1～100 的數字：25
太小了
請猜一個 1～100 的數字：42
猜中了！你猜了 3 次
```

### 練習題
1. 基礎：用 while 印出 2、4、6、8、10。
   解答：
   ```python
   n = 2
   while n <= 10:
       print(n)
       n = n + 2
   ```
   常見錯誤：`n = n + 2` 沒有縮排，放到迴圈外面，變成無窮迴圈。

2. 進階：讓使用者一直輸入數字，輸入 0 就停止，最後印出總和。
   解答：
   ```python
   total = 0
   num = int(input("輸入數字（0 結束）："))
   while num != 0:
       total = total + num
       num = int(input("輸入數字（0 結束）："))
   print("總和是", total)
   ```
   預期輸出（輸入 3、5、0）：`總和是 8`
   常見錯誤：迴圈裡忘了再 `input()` 一次，程式一直加同一個數字停不下來。

3. 挑戰：把猜數字遊戲改成「最多只能猜 7 次」，超過就公布答案。
   解答：
   ```python
   import random

   answer = random.randint(1, 100)
   times = 0
   win = False

   while times < 7:
       guess = int(input("請猜一個 1～100 的數字："))
       times = times + 1
       if guess > answer:
           print("太大了")
       elif guess < answer:
           print("太小了")
       else:
           print("猜中了！你猜了", times, "次")
           win = True
           break

   if not win:
       print("7 次用完了，答案是", answer)
   ```
   常見錯誤：沒有用 `win` 記錄，猜中之後還是印出「7 次用完了」。

### 課前準備
- 每台電腦先開 IDLE 測試 `import random` 與 `input()` 可正常執行（部分線上編輯器不支援 `input()`）
- 準備兩支範例程式檔，上課前投影測試
- 教學生無窮迴圈的停止方式（IDLE 按 Ctrl+C），先在教師機試一次
- 練習題印成學習單或放在班級雲端
