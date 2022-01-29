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

You can get the exact same file.











## Statistics

Start time of this page: January 15, 2022

Completion time of this page: January 16, 2022
