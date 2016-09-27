# Best Known Method

## GitHub

To get a list of users that have stared a repository you can append /stargazers to the url of the repository:

```
https://github.com/[user]/[repo]/stargazers
```

You can also see who the watchers:

```
https://github.com/[user]/[repo]/watchers
```

> http://webapps.stackexchange.com/questions/41799/how-can-i-list-people-who-have-starred-my-github-repository

Trending in open source: https://github.com/trending

Most forks: https://github.com/search?o=desc&q=stars:%3E1&s=forks&type=Repositories

Most stars: https://github.com/search?q=stars:%3E1&s=stars&type=Repositories

> http://stackoverflow.com/questions/19855552/how-to-find-out-the-most-popular-repositories-on-github

## Shell

Choose a random file from a directory in a shell script:

```
ls path/to/*.mp3 | awk 'BEGIN{ srand(); } { line[NR]=$0 } END{ print line[(int(rand()*NR+1))] }'

echo `find . -maxdepth 1 -mindepth 1 -type f -print0 | sort --zero-terminated --random-sort |  sed 's/\d000.*//g'`

find . -type f | shuf -n1

for f in `ls /usr/bin`; do  echo "$RANDOM $f" ; done | sort -R | head -n1 | cut -d' ' -f2-
```

> http://stackoverflow.com/questions/701505/best-way-to-choose-a-random-file-from-a-directory-in-a-shell-script

Simulate typing:

```
echo "You can simulate on-screen typing just like in the movies" | pv -qL 10
```

Monitor progress of a command:

```
pv access.log | gzip > access.log.gz
```

Live ssh network throughput test:

```
yes | pv | ssh $host "cat > /dev/null"

pv /dev/zero|ssh $host 'cat > /dev/null'
```

Time how fast the computer reads from `/dev/zero`:

```
pv /dev/zero > /dev/null
```

Copy a file using pv and watch its progress:

```
pv sourcefile > destfile
```

> https://blog.urfix.com/9-tricks-pv-pipe-viewer/

Transfer a directory from A to B and monitor progress:

```
# on computer A, with IP address 192.168.1.100
$ tar -cf - /path/to/dir | pv | nc -l -p 6666 -q 5
# on computer B
$ nc 192.168.1.100 6666 | pv | tar -xf -
```

> http://www.catonmat.net/blog/unix-utilities-pipe-viewer/

Using `pv` and `dialog` together to create a dialog progress:

```
tar -czf - ./Documents/ | (pv -n > backup.tgz) 2>&1 | dialog --gauge "Progress" 10 70
```

> http://www.tecmint.com/monitor-copy-backup-tar-progress-in-linux-using-pv-command/

Extract tar ball and show progress using the dialog command:

```
(pv -n backup.tar.gz | tar xzf - -C path/to/data ) 2>&1 | dialog --gauge "Running tar, please wait..." 10 70 0
```

> http://www.cyberciti.biz/open-source/command-line-hacks/pv-command-examples/

## Audio

Wav -> MP3

```
ffmpeg -i input.wav -vn -ar 44100 -ac 2 -ab 192k -f mp3 output.mp3

ffmpeg -i audio.wav -acodec libmp3lame audio.mp3
```

> http://stackoverflow.com/questions/3255674/convert-audio-files-to-mp3-using-ffmpeg

> http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs

Convert a video into animated GIF

```
ffmpeg -i video.mp4 -vf scale=500:-1 -t 10 -r 10 image.gif
```

> http://www.labnol.org/internet/useful-ffmpeg-commands/28490/

> http://www.tecmint.com/ffmpeg-commands-for-video-audio-and-image-conversion-in-linux/
