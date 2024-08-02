# glibc-all-in-one

This repo helps you to download & debug & compile glibc easily.

## Features

- download glibc binary
- download glibc debug file
- extract custom glibc
- download & compile glibc source code

## Usage

### Download

Check supported packages. Remember to run `update_list` at first.

```sh
➜  glibc-all-in-one ./update_list
[+] Common list has been save to "list"
[+] Old-release list has been save to "old_list"

➜  glibc-all-in-one cat list
2.23-0ubuntu10_amd64
2.23-0ubuntu10_i386
2.23-0ubuntu11_amd64
2.23-0ubuntu11_i386
2.23-0ubuntu3_amd64
2.23-0ubuntu3_i386
2.27-3ubuntu1_amd64
2.27-3ubuntu1_i386
2.28-0ubuntu1_amd64
2.28-0ubuntu1_i386
......

➜  glibc-all-in-one cat old_list
2.21-0ubuntu4.3_amd64
2.21-0ubuntu4.3_amd64
2.21-0ubuntu4_amd64
2.21-0ubuntu4_amd64
2.24-3ubuntu1_amd64
2.24-3ubuntu1_amd64
2.24-3ubuntu2.2_amd64
2.24-3ubuntu2.2_amd64
2.24-9ubuntu2.2_amd64
2.24-9ubuntu2.2_amd64
......
```

Download.

__Note__: use `download` for packages in the `list`; use `download -o` for packages in the `old_list`.

```sh
➜  glibc-all-in-one ./download 2.23-0ubuntu10_i386
Getting 2.23-0ubuntu10_i386
  -> Location: https://mirror.tuna.tsinghua.edu.cn/ubuntu/pool/main/g/glibc/libc6_2.23-0ubuntu10_i386.deb
  -> Downloading libc binary package
  -> Extracting libc binary package
  -> Package saved to libs/2.23-0ubuntu10_i386
  -> Location: https://mirror.tuna.tsinghua.edu.cn/ubuntu/pool/main/g/glibc/libc6-dbg_2.23-0ubuntu10_i386.deb
  -> Downloading libc debug package
  -> Extracting libc debug package
  -> Package saved to libs/2.23-0ubuntu10_i386/dbg
➜  glibc-all-in-one ls libs/2.23-0ubuntu10_i386
. .. .debug  ld-2.23.so  libc-2.23.so  libpthread.so.0   ......
➜  glibc-all-in-one ls libs/2.23-0ubuntu10_i386/.debug
ld-2.23.so  libc-2.23.so   ......
```

```sh
➜  glibc-all-in-one ./download -o 2.24-3ubuntu2.2_amd64
......
```

Needed glibc not in my list?

You can download the debs on your own, then use `extract`.

```sh
./extract ~/libc6_2.26-0ubuntu2_i386.deb /tmp/test
./extract ~/libc6-dbg_2.26-0ubuntu2_i386.deb /tmp/test_dbg
```

### Build

supported version: 2.19, 2.23-2.29

supported arch: i686, amd64

__Note__: you may fail to build older version of glibc. (not my problem). My friend says that Ubuntu 16.04 is perfect to build all of them.

__Note__: change the `GLIBC_DIR` in the `build`, if you don't want to build them on `/glibc`.

```sh
./build 2.29 i686
```
