## Bandit Level 0

The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. 


__Result__
```bash
$ ssh   bandit0@bandit.labs.overthewire.org -p 2220                                                                 255 ⨯
The authenticity of host '[bandit.labs.overthewire.org]:2220 ([176.9.9.172]:2220)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[bandit.labs.overthewire.org]:2220,[176.9.9.172]:2220' (ECDSA) to the list of known hosts.
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit0@bandit.labs.overthewire.org's password: 
Linux bandit.otw.local 5.4.8 x86_64 GNU/Linux

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to Steven or morla on
irc.overthewire.org.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ and /proc/ is disabled
  so that users can not snoop on eachother. Files and directories with
  easily guessable or short names will be periodically deleted!

  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few usefull tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /usr/local/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /usr/local/pwndbg/
    * peda (https://github.com/longld/peda.git) in /usr/local/peda/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /usr/local/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)
    * checksec.sh (http://www.trapkit.de/tools/checksec.html) in /usr/local/bin/checksec.sh

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us through IRC on
  irc.overthewire.org #wargames.

  Enjoy your stay!

bandit0@bandit:~$ 
```

## Bandit Level 1

### Level Goal
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

```bash
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme 
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```
- Login
```bash
ssh   bandit1@bandit.labs.overthewire.org -p 2220
```
password:  boJ9jbbUNNfktd78OOpsqOltutMc3MY1


## Bandit Level 1 → Level 2

### Level Goal
The password for the next level is stored in a file called `-` located in the home directory

> Its a dashed filename

```bash
bandit1@bandit:~$ cat < -
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```


## Bandit Level 2 → Level 3
### Level Goal
The password for the next level is stored in a file called spaces in this filename located in the home directory.

```bash
bandit2@bandit:~$ ls
spaces in this filename
bandit2@bandit:~$ cat spaces\ in\ this\ filename 
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```

## Bandit Level 3 → Level 4
### Level Goal
The password for the next level is stored in a hidden file in the inhere directory.

```bash
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ ls -la
total 24
drwxr-xr-x  3 root root 4096 May  7  2020 .
drwxr-xr-x 41 root root 4096 May  7  2020 ..
-rw-r--r--  1 root root  220 May 15  2017 .bash_logout
-rw-r--r--  1 root root 3526 May 15  2017 .bashrc
drwxr-xr-x  2 root root 4096 May  7  2020 inhere
-rw-r--r--  1 root root  675 May 15  2017 .profile
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -la
total 12
drwxr-xr-x 2 root    root    4096 May  7  2020 .
drwxr-xr-x 3 root    root    4096 May  7  2020 ..
-rw-r----- 1 bandit4 bandit3   33 May  7  2020 .hidden
bandit3@bandit:~/inhere$ cat .hidden
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```

## Bandit Level 4 → Level 5
Level Goal
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.
```bash
bandit4@bandit:~/inhere$ for i in {1..9}; do cat <-file0$i; echo "\n";done
��p,k�;��r*��   �.!��C��J       �dx,�\n
e�)�#��5��
          ��p��V�_���ׯ�mm\n
������h!TQO�`�4"aל�߂phT��,�A\n
?�\n�ו$����I&�������c���ގ.�
�r�l$�?h�9('���!y�e�#�x�O��=�\n
ly���~��A�f����-E�{���m�����ܗM\n
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
\n
�T�?�i��j���îP�F�l�n��J����{��@\n
�e�0$�in=��_b�5FA�P7sz��gN\n
```


## Bandit Level 5 → Level 6
Level Goal
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
- human-readable
- 1033 bytes in size
- not executable


| argument  |Description   |
|---|---|
|  .    OR    ./  | Refer to the Current Working Directory   |
|  -type f  |  File is of type : regular file     |
|  -readable |  Matches files which are readable. |
|-executable|Matches  files which are executable   &    directories which are searchable   |
|! -executable|Matches  files that are NOT executable &directories which are NOT searchable |
| -size 1033c| File uses 1033 units of space. `c` refer to bytes.|

```bash
find ./ -type f -readable ! -executable -size 1033c
```

```bash
bandit5@bandit:~/inhere$ find ./ -type f -readable ! -executable -size 1033c
./maybehere07/.file2
```
```bash
bandit5@bandit:~/inhere/maybehere07$ cat < .file2
DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```

## Bandit Level 6 → Level 7
Level Goal
The password for the next level is stored somewhere on the server and has all of the following properties:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

```bash
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2> /dev/null
/var/lib/dpkg/info/bandit7.password
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```

## Bandit Level 7 → Level 8
Level Goal
The password for the next level is stored in the file data.txt next to the word millionth
```bash
bandit7@bandit:~$ cat data.txt | grep "millionth"
millionth       cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```

## Bandit Level 8 → Level 9
Level Goal
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

```bash
bandit8@bandit:~$ sort data.txt | uniq -u
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```


## Bandit Level 9 → Level 10
Level Goal
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

> data.txt is binary not ascii file
```bash
bandit9@bandit:~$ strings data.txt  | grep -E  "=+"
========== the*2i"4
=:G e
========== password
<I=zsGi
Z)========== is
A=|t&E
Zdb=
c^ LAh=3G
*SF=s
&========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
S=A.H&^

```

## Bandit Level 10 → Level 11
Level Goal
The password for the next level is stored in the file data.txt, which contains base64 encoded data

```bash
bandit10@bandit:~$ cat data.txt 
VGhlIHBhc3N3b3JkIGlzIElGdWt3S0dzRlc4TU9xM0lSRnFyeEUxaHhUTkViVVBSCg==
bandit10@bandit:~$ cat data.txt | base64 -d
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```

## Bandit Level 11 → Level 12
Level Goal
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions


```bash
bandit11@bandit:~$ cat data.txt 
Gur cnffjbeq vf 5Gr8L4qetPEsPk8htqjhRK8XSP6x2RHh
bandit11@bandit:~$ cat data.txt | tr "A-Za-z" "N-ZA-Mn-za-m"
The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```
> tr translates
```bash
bandit11@bandit:~$ tr --help
Usage: tr [OPTION]... SET1 [SET2]
Translate, squeeze, and/or delete characters from standard input,
writing to standard output.
```


```bash
bandit12@bandit:~$ ls
data.txt
bandit12@bandit:~$ xxd -r data.txt 
P�^data2.bin=��BZh91AY&SY�O����ڞOv���}?��}��^����������ߣ��;����▒4��▒h�F�F��4▒LM
                                                                               @��z��FM��C�hF�C@�4@f��h
4hh�▒=C%�>X▒,�k���1��GY��                                                                              ��i�hPh�Mh
�J�쌑Oϊ��{RBp�Qix�Y�Z!d��j�(�搿ݳ��/��A�#�A��F��0P��v��`�"3�

                                          ��d�bX?��z��2��<��A �n}
5(3A��
      wO�R����6�XS{�
���9?L�P�yB��=z�m?�L�Nt*�7{qP���%"�w9�qm4�� N3�6���K��H䋑[��}!
                                                              d��3A4$��M~�\ɠJ�C�kUƦ\���\�FSN��&=�[��q   \)�$:��H�t&/�(����]��BB9<s ��h=bandit12@bandit:~$ 
bandit12@bandit:~$ 
bandit12@bandit:~$ xxd -r data.txt > something
-bash: something: Permission denied
bandit12@bandit:~$ xxd -r data.txt > /tmp/something
bandit12@bandit:~$ file /tmp/something
/tmp/something: gzip compressed data, was "data2.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:~$ mv /tmp/something /tmp/something.gz
bandit12@bandit:~$ gunzip /tmp/something.gz
bandit12@bandit:~$ ls -la /tmp/
ls: cannot open directory '/tmp/': Permission denied
bandit12@bandit:~$ file /tmp/something
/tmp/something: bzip2 compressed data, block size = 900k

```

> password: 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL (bandit13)