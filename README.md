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

## Audio

Wav -> MP3

```
ffmpeg -i input.wav -vn -ar 44100 -ac 2 -ab 192k -f mp3 output.mp3
```

> http://stackoverflow.com/questions/3255674/convert-audio-files-to-mp3-using-ffmpeg

> http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs
