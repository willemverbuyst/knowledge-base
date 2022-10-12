## os

Creating new file

```go
var newFile *os.File
var err Error

newFile, err = os.Create("test.txt")
...
newFile.Close()
```

Check if file exists

```go
var fileInfo os.FileInfo
var err Error

fileInfo, err = os.Stat("noneexistingfile.txt")
if err != nil {
	if os.IsNotExist(err) {
		log.Fatal("file does not exist")
	}
	...
}
```

Remove file

```go
err := os.Remove("test.txt")
```


Write to file

```go
file, err := os.OpenFile(
	"test.txt",
	os.O_WRONLY|os.O_TRUNC|os.O_CREATE,
	0644,	
	)
if err != nil {
	log.Fatal(err)
}
defer file.Close()

byteSlice := []byte("hello world")
bytesWritten, err := file.Write(byteSlice)
```


| method | example | what does it do? |
|--------|---------|------------------|
| Open | os.Open() | open file in read only mode |
| Truncate | os.Truncate("test.txt", 0) | truncate file, 0 means everything will be removed |
| OpenFile | os.OpenFile("test.txt", O_CREATE\|os.O_APPEND, 0644) |  open file with name of file, opening mode, permissions |
| Rename | os.Rename("old", "new") | update the path/name |
| Remove | os.Remove("test.txt") | remove file |


## ioutil

Write to file

```go
t := []byte("some text")
err := ioutil.WriteFile("test.txt", t, 0644)
```

Read all as string

```go
file, err = os.Open("test.txt")
if err != nil {
	log.Fatal(err)
}
defer file.Close()

data, err := ioutil.ReadAll(file)
```

Read all as byte slice

```go
file, err = os.Open("test.txt")
if err != nil {
	log.Fatal(err)
}
defer file.Close()

data, err := ioutil.ReadFile(file)
```


## bufio
Write to file

```go
file, err := os.OpenFile(
	"test.txt",
	os.O_WRONLY|os.O_CREATE,
	0644,	
	)
if err != nil {
	log.Fatal(err)
}
defer file.Close()

bufferedWriter := bufio.NewWriter(file)
bs := []byte{97, 98, 99}

bytesWritten, err := bufferedWriter.Write(bs)

// bytesWritten, err := bufferedWriter.WriteString("some string")

bufferedWriter.Flush()
```

Reading file with delimiters

```go
file, err = os.Open("test.txt")
if err != nil {
	log.Fatal(err)
}
defer file.Close()

scanner := bufio.NewScanner(file)
scanner.Split(bufio.ScanWords)

success := scanner.Scan()

if success == false {
	err == scanner.Err()
	if err == nil {
		log.Println("scan completed")
	} else {
		log.Fatal(err)
	}
}

fmt.Println("First line:", scanner.Text())

for scanner.Scan() {
	fmt.Println(scanner.Text())
}
if err := scanner.Err(), err != nil {
	log.Fatal(err)
}
```


Get Stdin

```go
scanner := bufio.NewScanner(os.Stdin)
scanner.Scan()

text := scanner.Text()
```


## io
Read file

```go
file, err = os.Open("test.txt")
if err != nil {
	log.Fatal(err)
}
defer file.Close()

byteSlice := make([]byte, 2)

numberBytesRead, err := io.Readfull(file, byteSlice)
```

