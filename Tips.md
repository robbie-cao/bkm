# Tips

## `tty`

**Send message in terminal to another**

```
$ tty                                   # Get the file name of the terminal connected to standard input
                                        # Result could be sth like '/dev/ttys009' or '/dev/pts/9'
$ echo "hello world" > /dev/ttys009     # /dev/ttys009 is the target terminal message will be sent to
$ hexdump > /dev/urandom > /dev/pts/9   # Print randow hex to /dev/pts/9
```


## Reference

