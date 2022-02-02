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











## Statistics

Start time of this page: January 15, 2022

Completion time of this page: January 16, 2022
