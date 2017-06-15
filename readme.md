Expect for Windows Command Prompt Powered by GopherLua
=======================================================

- A tool like `expect` on Linux.
- Scripts are to be written with Lua (GopherLua)
- Some built-in functions exists:
    - `expect()` accesses CONOUT$ directly and watches the cursor-line (0.1 seconds interval)
    - `send()` occurs keyboard events against CONIN$.
    - `spawn()` starts applications and returns true on success or false on failure.

Sample
------

sample.lua:

```sample.lua
if spawn([[c:\Program Files\Git\usr\bin\ssh.exe]],"foo@example.com") then
    expect("password:")
    send("PASSWORD\r")
    expect("~]$")
    send("exit\r")
end
```

On the command prompt:

```console
$ expect.exe sample.lua
foo@example.com's password:
Last login: Thu Jun 15 13:21:57 2017 from XXXXXXXXXXXX.XXXX.XX.XXX.XXX.XXXXXXX.XX.XX
FreeBSD 9.1-RELEASE-p24 (XXXXXXXX) #0: Thu Feb  5 10:03:29 JST 2015

Welcome to FreeBSD!

[foo@XXXXXXX ~]$ exit
logout
Connection to example.com closed.
```