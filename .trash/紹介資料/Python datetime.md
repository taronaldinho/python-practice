---
tags:
  - Python
  - Reference
aliases: 
cssclasses: 
publish: false
---
# Python datetime

Python datetimeとは、＜以降書きかけ＞

---

## この資料の目的
# datetime

## 時刻を表すクラス datetime.datetime

```python
from datetime import datetime
```

```python
# 現在時刻の取得
d_now = datetime.now()

print(d_now)        # 2022-02-11 18:50:34.860366
print(type(d_now))  # <class 'datetime.datetime'>
```

```python
# 年
d_now.year  # 2022

# 月
d_now.month # 2

# 日
d_now.day   # 11

# 時
d_now.hour  # 18

# 分
d_now.minute  # 50

# 秒
d_now.second  # 34

# マイクロ秒
d_now.microsecond  # 860366
```

```python
# 日時を指定してdatetimeを生成
# 下の行の右辺はdatetime(1983, 11, 19)でもOK
d_19831119 = datetime(
                 year=1983, 
                 month=11, 
                 day=19, 
                 hour=0, 
                 minute=0, 
                 second=0, 
                 microsecond=0
              )
```

## 日時の差 datetime.timedelta

```python
from datetime import timedelta
```

```python
# datetime同士の差はtimedeltaとなる
delta_1 = d_now - d_20190203

print(delta_1)        # 13964 days, 18:50:34.860366
print(type(delta_1))  # <class 'datetime.timedelta'>
```

```python
# timedeltaを生成
delta_2 = timedelta(days=7)

print(delta_2)        # 7 days, 0:00:00
print(type(delta_2))  # <class 'datetime.timedelta'>
```

引数で `days, seconds, microseconds, milliseconds, minutes, hours, weeks` が指定できる。

```python
# 現在時刻の7日前
seven_days_before = d_now - delta_2
```

datetime.timedelta は年月の差を直接扱えない。そのような場合は dateutil.relativedelta を使う。（前月末日の計算も簡単）

[dateutil - powerful extensions to datetime](https://dateutil.readthedocs.io/en/stable/)

## 日付と文字列の変換

フォーマット文字列の考え方は以下を参照ください。

|ディレクティブ|意味|使用例|
|---|---|---|
|%w|曜日を10進表記した文字列を表示します。0 が日曜日で、6 が土曜日を表します。|0, 1, ..., 6|
|%d|0埋めした10進数で表記した月中の日にち。|01, 02, ..., 31|
|%m|0埋めした10進数で表記した月。|01, 02, ..., 12|
|%y|0埋めした10進数で表記した世紀無しの年。|00, 01, ..., 99|
|%Y|西暦 ( 4桁) の 10 進表記を表します。|0001, 0002, ..., 2013, 2014, ..., 9998, 9999|
|%H|0埋めした10進数で表記した時 (24時間表記)。|00, 01, ..., 23|
|%I|0埋めした10進数で表記した時 (12時間表記)。|01, 02, ..., 12|
|%M|0埋めした10進数で表記した分。|00, 01, ..., 59|
|%S|0埋めした10進数で表記した秒。|00, 01, ..., 59|
|%f|Microsecond as a decimal number, zero-padded to 6 digits.|000000, 000001, ..., 999999|
|%z|UTCオフセットを ±HHMM[SS[.ffffff]] の形式で表示します (オブジェクトがnaiveであれば空文字列)。|(空文字列), +0000, -0400, +1030, +063415, -030712.345216|
|%Z|タイムゾーンの名前を表示します (オブジェクトがnaiveであれば空文字列)。|(空文字列), UTC, GMT|

[https://docs.python.org/ja/3/library/datetime.html#strftime-and-strptime-behavior](https://docs.python.org/ja/3/library/datetime.html#strftime-and-strptime-behavior)

```python
# datetimeからフォーマットを指定してstr(文字列)に変換
datetime_format = "%Y/%m/%d"
str_now = d_now.strftime(datetime_format)

print(str_now)        # 2022/02/11
print(type(str_now))  # <class 'str'>
```

```python
# 漢字を含むフォーマット
kanji_format = "%Y年%m月%d日"
str_now = d_now.strftime(kanji_format)

print(str_now)  # 2022年02月11日
```

```python
# このようにformat()関数と併用することも可能
f_format = "%Y{}%m{}%d{}"
str_now = d_now.strftime(f_format).format("年", "月", "日")

print(str_now)  # 2022年02月11日
```

```python
# 月日などをゼロ埋めしたくない場合は
# %#m や %#d などに置き換える(Windowsの場合有効な手段)
tmp_format_without_zerofilling = "%Y年%#m月%#d日"
str_now = d_now.strftime(tmp_format_without_zerofilling)

print(str_now)  # 2022年2月11日
```

```python
# strからdatetimeに変換
string = "2020年2月29日"
strp_format = "%Y年%m月%d日"

print(datetime.strptime(string, strp_format))  # 2020-02-29 00:00:00
```

## タイムゾーン datetime.timezone

```python
from datetime import timezone
```

```python
# utc → coordinated universal time: 協定世界時
tz_utc = timezone.utc

print(tz_utc)        # UTC
print(type(tz_utc))  # <class 'datetime.timezone'>
```

```python
d_now_with_utc = datetime.now(tz=tz_utc)

print(d_now_with_utc)  # 2022-02-11 09:50:35.681202+00:00
```

```python
# UTCからの時差はtimedeltaで与える
# jst → Japan Standard Time: 日本標準時
tz_jst = timezone(timedelta(hours=9))

print(tz_jst)        # UTC+09:00
print(type(tz_jst))  # <class 'datetime.timezone'>
```

```python
d_now_with_jst = datetime.now(tz=tz_jst)

print(d_now_with_jst)  # 2022-02-11 18:50:35.935045+09:00
```