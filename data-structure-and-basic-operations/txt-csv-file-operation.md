---
coverY: 0
---

# txt/csv file operation

Manipulating txt documents is a very important lesson. Writing, appending, and reading txt documents is very common in python programming.

## write to txt

```python
fw = open('test.txt', 'w')

for i in range(20):
    print(i, file=fw)

fw.close()
```

Writing txt is very simple, you can use the print function to write txt.

After running the above program, you will get a file called test.txt in the folder where the python program is located. The following is the content of the file.

```python
0
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
```

You can also write to a file using the file's own features:

```python
fw = open('test.txt', 'w')

for i in range(20):
    fw.write(str(i)+'\n')

fw.close()
```

You can get the exact same file. **(The write method can only write the content of the string type, so you need to convert the result to the string type to write it with write.)**

The print function comes with a line break (you can use end='' to cancel the automatic line break), but the write function does not have a line break.

{% hint style="danger" %}
<mark style="color:red;">**There are few things to note:**</mark>

Using the print function can print any format, but using write can only write data of type string, so you need to convert the data to a string, so it seems easier to use the print function.

**But the print function also has a disadvantage, that is, the efficiency is relatively low. If you need to write a large amount of content, it is best to use the write method.**

When we use 'w' to open a file, all the content in the file will be deleted, so we need to pay special attention. If there is important content in your file, this operation will destroy the original content, and the lost content cannot be recovered.

After we write to a file, the computer uses a caching mechanism to first write a portion of the content to a memory or disk buffer instead of writing it directly to disk. So if you don't close a file, part of the content will be lost. So make sure to close the file after we write to it.
{% endhint %}

```python
fw = open('test.txt', 'w')

for i in range(20):
    print(i, file=fw, flush=True)

fw.close()
```

```python
fw = open('test.txt', 'w')

for i in range(20):
    fw.write(str(i)+'\n')
    fw.flush()

fw.close()
```

If your program may crash, but you don't want to lose data, using flush can make the cache write to disk immediately. The above are two different ways of writing to the cache immediately.

## append to txt

```python
fw = open('test.txt', 'a')

for i in range(20):
    fw.write(str(i)+'\n')
    fw.flush()

fw.close()
```

The above code is to append to txt file.&#x20;

Use 'a' to append the file, the original file content will not be deleted, the newly written file content will be appended at the end of the file.

Both print and write can be used for file appending.

The file after appending looks like this, if you run the code once, then the result is 0-19 repeated twice, and if you run the code twice, it is 0-19 repeated three times.

If test.txt does not exist, then using append will create a new file called test.txt, and then append whatever you want to the empty file.

```python
0
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
0
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19

```

## read txt

```python
f = open('test.txt', 'r')
lines = f.readlines()
f.close()

for line in lines:
    print(line, end='')
```

The 'r' mode is used to read txt. When reading txt, the content in txt will not be deleted, but read-only mode is used.

The above program can print each line in txt.

Reading a txt file does not require closing the txt text, since you are not writing to the file and the file will not be locked by the OS, but it is still recommended to close the file after reading the entire contents of the text to avoid problems.

```python
0
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
0
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
>>> 
```

## csv file

Comma-Separated Values are simply referred to as csv files.

For example, the following file contains the iris dataset. If you save it as iris.csv, you can open it with excel.

```python
sepal_length,sepal_width,petal_length,petal_width,species
5.1,3.5,1.4,0.2,setosa
4.9,3.0,1.4,0.2,setosa
4.7,3.2,1.3,0.2,setosa
4.6,3.1,1.5,0.2,setosa
5.0,3.6,1.4,0.2,setosa
5.4,3.9,1.7,0.4,setosa
4.6,3.4,1.4,0.3,setosa
5.0,3.4,1.5,0.2,setosa
4.4,2.9,1.4,0.2,setosa
4.9,3.1,1.5,0.1,setosa
5.4,3.7,1.5,0.2,setosa
4.8,3.4,1.6,0.2,setosa
4.8,3.0,1.4,0.1,setosa
4.3,3.0,1.1,0.1,setosa
5.8,4.0,1.2,0.2,setosa
5.7,4.4,1.5,0.4,setosa
5.4,3.9,1.3,0.4,setosa
5.1,3.5,1.4,0.3,setosa
5.7,3.8,1.7,0.3,setosa
5.1,3.8,1.5,0.3,setosa
5.4,3.4,1.7,0.2,setosa
5.1,3.7,1.5,0.4,setosa
4.6,3.6,1.0,0.2,setosa
5.1,3.3,1.7,0.5,setosa
4.8,3.4,1.9,0.2,setosa
5.0,3.0,1.6,0.2,setosa
5.0,3.4,1.6,0.4,setosa
5.2,3.5,1.5,0.2,setosa
5.2,3.4,1.4,0.2,setosa
4.7,3.2,1.6,0.2,setosa
4.8,3.1,1.6,0.2,setosa
5.4,3.4,1.5,0.4,setosa
5.2,4.1,1.5,0.1,setosa
5.5,4.2,1.4,0.2,setosa
4.9,3.1,1.5,0.1,setosa
5.0,3.2,1.2,0.2,setosa
5.5,3.5,1.3,0.2,setosa
4.9,3.1,1.5,0.1,setosa
4.4,3.0,1.3,0.2,setosa
5.1,3.4,1.5,0.2,setosa
5.0,3.5,1.3,0.3,setosa
4.5,2.3,1.3,0.3,setosa
4.4,3.2,1.3,0.2,setosa
5.0,3.5,1.6,0.6,setosa
5.1,3.8,1.9,0.4,setosa
4.8,3.0,1.4,0.3,setosa
5.1,3.8,1.6,0.2,setosa
4.6,3.2,1.4,0.2,setosa
5.3,3.7,1.5,0.2,setosa
5.0,3.3,1.4,0.2,setosa
7.0,3.2,4.7,1.4,versicolor
6.4,3.2,4.5,1.5,versicolor
6.9,3.1,4.9,1.5,versicolor
5.5,2.3,4.0,1.3,versicolor
6.5,2.8,4.6,1.5,versicolor
5.7,2.8,4.5,1.3,versicolor
6.3,3.3,4.7,1.6,versicolor
4.9,2.4,3.3,1.0,versicolor
6.6,2.9,4.6,1.3,versicolor
5.2,2.7,3.9,1.4,versicolor
5.0,2.0,3.5,1.0,versicolor
5.9,3.0,4.2,1.5,versicolor
6.0,2.2,4.0,1.0,versicolor
6.1,2.9,4.7,1.4,versicolor
5.6,2.9,3.6,1.3,versicolor
6.7,3.1,4.4,1.4,versicolor
5.6,3.0,4.5,1.5,versicolor
5.8,2.7,4.1,1.0,versicolor
6.2,2.2,4.5,1.5,versicolor
5.6,2.5,3.9,1.1,versicolor
5.9,3.2,4.8,1.8,versicolor
6.1,2.8,4.0,1.3,versicolor
6.3,2.5,4.9,1.5,versicolor
6.1,2.8,4.7,1.2,versicolor
6.4,2.9,4.3,1.3,versicolor
6.6,3.0,4.4,1.4,versicolor
6.8,2.8,4.8,1.4,versicolor
6.7,3.0,5.0,1.7,versicolor
6.0,2.9,4.5,1.5,versicolor
5.7,2.6,3.5,1.0,versicolor
5.5,2.4,3.8,1.1,versicolor
5.5,2.4,3.7,1.0,versicolor
5.8,2.7,3.9,1.2,versicolor
6.0,2.7,5.1,1.6,versicolor
5.4,3.0,4.5,1.5,versicolor
6.0,3.4,4.5,1.6,versicolor
6.7,3.1,4.7,1.5,versicolor
6.3,2.3,4.4,1.3,versicolor
5.6,3.0,4.1,1.3,versicolor
5.5,2.5,4.0,1.3,versicolor
5.5,2.6,4.4,1.2,versicolor
6.1,3.0,4.6,1.4,versicolor
5.8,2.6,4.0,1.2,versicolor
5.0,2.3,3.3,1.0,versicolor
5.6,2.7,4.2,1.3,versicolor
5.7,3.0,4.2,1.2,versicolor
5.7,2.9,4.2,1.3,versicolor
6.2,2.9,4.3,1.3,versicolor
5.1,2.5,3.0,1.1,versicolor
5.7,2.8,4.1,1.3,versicolor
6.3,3.3,6.0,2.5,virginica
5.8,2.7,5.1,1.9,virginica
7.1,3.0,5.9,2.1,virginica
6.3,2.9,5.6,1.8,virginica
6.5,3.0,5.8,2.2,virginica
7.6,3.0,6.6,2.1,virginica
4.9,2.5,4.5,1.7,virginica
7.3,2.9,6.3,1.8,virginica
6.7,2.5,5.8,1.8,virginica
7.2,3.6,6.1,2.5,virginica
6.5,3.2,5.1,2.0,virginica
6.4,2.7,5.3,1.9,virginica
6.8,3.0,5.5,2.1,virginica
5.7,2.5,5.0,2.0,virginica
5.8,2.8,5.1,2.4,virginica
6.4,3.2,5.3,2.3,virginica
6.5,3.0,5.5,1.8,virginica
7.7,3.8,6.7,2.2,virginica
7.7,2.6,6.9,2.3,virginica
6.0,2.2,5.0,1.5,virginica
6.9,3.2,5.7,2.3,virginica
5.6,2.8,4.9,2.0,virginica
7.7,2.8,6.7,2.0,virginica
6.3,2.7,4.9,1.8,virginica
6.7,3.3,5.7,2.1,virginica
7.2,3.2,6.0,1.8,virginica
6.2,2.8,4.8,1.8,virginica
6.1,3.0,4.9,1.8,virginica
6.4,2.8,5.6,2.1,virginica
7.2,3.0,5.8,1.6,virginica
7.4,2.8,6.1,1.9,virginica
7.9,3.8,6.4,2.0,virginica
6.4,2.8,5.6,2.2,virginica
6.3,2.8,5.1,1.5,virginica
6.1,2.6,5.6,1.4,virginica
7.7,3.0,6.1,2.3,virginica
6.3,3.4,5.6,2.4,virginica
6.4,3.1,5.5,1.8,virginica
6.0,3.0,4.8,1.8,virginica
6.9,3.1,5.4,2.1,virginica
6.7,3.1,5.6,2.4,virginica
6.9,3.1,5.1,2.3,virginica
5.8,2.7,5.1,1.9,virginica
6.8,3.2,5.9,2.3,virginica
6.7,3.3,5.7,2.5,virginica
6.7,3.0,5.2,2.3,virginica
6.3,2.5,5.0,1.9,virginica
6.5,3.0,5.2,2.0,virginica
6.2,3.4,5.4,2.3,virginica
5.9,3.0,5.1,1.8,virginica

```

In the following chapters, it is detailed how to read the iris dataset and how to batch the strings into float format data. See the following chapters:

{% content-ref url="../data-mining-and-machine-learning/iris-data-set.md" %}
[iris-data-set.md](../data-mining-and-machine-learning/iris-data-set.md)
{% endcontent-ref %}

Writing to csv files is also very simple: for example, the following code can write some random numbers in csv:

```python
fw = open('test_csv.csv', 'w')

import random

print('title,random1,random2,random3,random4,random5', file=fw)

for i in range(20):
    print(i, end=',', file=fw)

    for j in range(5):
        print(random.random(), end=',', file=fw)

    print(file=fw)

fw.close()
```

The above code will generate a csv file with headers:

```python
title,random1,random2,random3,random4,random5
0,0.13920821221869129,0.9522697952396495,0.34893933506932984,0.44287699353372123,0.9740162167112401,
1,0.33167053647408684,0.6706277608298793,0.9679670228363058,0.520982841192996,0.9713818471524674,
2,0.3324510990064081,0.32287387846269566,0.1058155893216689,0.9742846724607953,0.21252692346921043,
3,0.31602358524658003,0.4005417313075852,0.4068362055128625,0.1724509426874148,0.10622359642506785,
4,0.35526542984026865,0.312907111754292,0.7916674109709352,0.12272010493579044,0.9415022347136395,
5,0.8977171525124167,0.26007550478011465,0.426182826413232,0.9797812186860544,0.3869263934916106,
6,0.9673035021211389,0.6281127352904776,0.7097705120084107,0.3850032164915692,0.8422969072174212,
7,0.7549533245386693,0.9228969689103006,0.21558259105299327,0.7119374084709735,0.1402498564352258,
8,0.2964269356156751,0.11744252935429211,0.2828689159198011,0.5172936786778944,0.34723078182030365,
9,0.824526410847394,0.16072589666398285,0.9514658616584855,0.8054027733119995,0.5858403521453424,
10,0.19491688083089664,0.2673292503044872,0.37736469105294856,0.03618232318847403,0.03784298738562997,
11,0.032322107628285024,0.31244424236446233,0.27905142440915454,0.30839710150523425,0.3482383064391852,
12,0.05380326711217709,0.17466073990466724,0.057656916954841986,0.7553245862727377,0.31201296840916426,
13,0.5175540508757746,0.8923683192529758,0.06488475523934722,0.4153216944797755,0.8569633610047449,
14,0.5279849545013076,0.7704328716144113,0.8816172548810176,0.6735017034714119,0.32340740106831267,
15,0.018449284744372685,0.11417768109396476,0.9813110943814584,0.5147346200884056,0.5035131444800754,
16,0.9159087461634295,0.714381521030152,0.5935606255314029,0.810339370316849,0.6884831335467722,
17,0.37404760187674135,0.2943069545617619,0.3485670600049414,0.4126138494587901,0.6143583103915412,
18,0.7102954649859569,0.624748312531278,0.694722612218366,0.05100870633477783,0.0721580907338999,
19,0.2779818882828635,0.3376512799571485,0.7877080243826541,0.4263405199542226,0.14899008366395672,

```

Use notepad to open the csv file.&#x20;

At this time, the file is not in the form of cells, but in plain text. This format is not easy to observe the data. You can use excel to open the csv file:

![excel with csv](<../.gitbook/assets/image (9).png>)

{% hint style="danger" %}
<mark style="color:red;">**It should be noted that csv needs to have the same number of commas in each line (the last comma is not counted), if the number of commas is different, the format may be messed up. If a cell is empty, it should be indicated by two consecutive commas: , ,**</mark>

**In addition, there is no space after the comma in csv, which is different from the English grammar.**
{% endhint %}

{% hint style="success" %}
csv can not only be separated by commas, but also tab (\t) or spaces or special symbols such as # or $, but excel cannot open these files correctly.

If the data you need to save already has commas in it, then you should **not** use commas as csv delimiters, because then commas in your data will also be treated as csv delimiters. At this point you should use the tab key.
{% endhint %}

## Statistics

Start time of this page: January 15, 2022

Completion time of this page: January 16, 2022
