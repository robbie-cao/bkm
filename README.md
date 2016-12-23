# Best Known Method

## Markdown

### Online Editor

- [StackEdit](https://stackedit.io) - Extended markdown support on LaTeX mathematical expressions and UML diagrams
- [Math Online Editor](https://upmath.me) - Writing math texts for the web with LaTeX equations support

### Table of Content

```
<link rel="stylesheet" href="http://yandex.st/highlightjs/6.2/styles/googlecode.min.css">
  
<script src="http://code.jquery.com/jquery-1.7.2.min.js"></script>
<script src="http://yandex.st/highlightjs/6.2/highlight.min.js"></script>
  
<script>hljs.initHighlightingOnLoad();</script>
<script type="text/javascript">
 $(document).ready(function(){
      $("h2,h3,h4,h5,h6").each(function(i,item){
        var tag = $(item).get(0).localName;
        $(item).attr("id","wow"+i);
        $("#category").append('<a class="new'+tag+'" href="#wow'+i+'">'+$(this).text()+'</a></br>');
        $(".newh2").css("margin-left",0);
        $(".newh3").css("margin-left",20);
        $(".newh4").css("margin-left",40);
        $(".newh5").css("margin-left",60);
        $(".newh6").css("margin-left",80);
      });
 });
</script>
<div id="category"></div>
```

### Page Break

```
<div style="page-break-after: always;"></div>
```

### Image in Width/Height

```
<center>
<img src="images/drawing.png" alt="Drawing" style="width: 600px;"/>
</center>
```

### Centering an Image

```
<p align="center">
  <img src="https://assets-cdn.github.com/images/modules/logos_page/GitHub-Mark.png" width="256" title="Github Logo">
</p>

-or-

<center>![](image.png)
```

### Text in Color

```
<span style="color:red">Text in red color</span>
```

## TeX / LaTeX

```
# compile
latex foo.tex
# display on screen with X11
xdvi foo.dvi
# convert dvi to postscript
dvips -Pcmz foo.dvi foo.ps
# convert dvi to pdf
dvipdf foo.dvi
```

## GitHub

### Gravizo - Graphviz, UMLGraph or PlantUML for README

A simple way of describing graphs and include it easily in your web for free, blog, markdown page, github, and any location where remote images can be showed.

Gravizo uses Graphviz to render graphs. It supports DOT, PlantUML, UMLGraph syntax and SVG in JSON format. It will include other formats in the future. No javascript, no plugins needed so you can include in any document.

Example:

![Alt text](http://g.gravizo.com/g?
  digraph G {
    aize ="4,4";
    main [shape=box];
    main -> parse [weight=8];
    parse -> execute;
    main -> init [style=dotted];
    main -> cleanup;
    execute -> { make_string; printf};
    init -> make_string;
    edge [color=red];
    main -> printf [style=bold,label="100 times"];
    make_string [label="make a string"];
    node [shape=box,style=filled,color=".7 .3 1.0"];
    execute -> compare;
  }
)

```
![Alt text](http://g.gravizo.com/g?
  digraph G {
    aize ="4,4";
    main [shape=box];
    main -> parse [weight=8];
    parse -> execute;
    main -> init [style=dotted];
    main -> cleanup;
    execute -> { make_string; printf};
    init -> make_string;
    edge [color=red];
    main -> printf [style=bold,label="100 times"];
    make_string [label="make a string"];
    node [shape=box,style=filled,color=".7 .3 1.0"];
    execute -> compare;
  }
)
```

![Alt text](http://g.gravizo.com/g?
@startuml;
actor User;
participant "First Class" as A;
participant "Second Class" as B;
participant "Last Class" as C;
User -> A: DoWork;
activate A;
A -> B: Create Request;
activate B;
B -> C: DoWork;
activate C;
C --> B: WorkDone;
destroy C;
B --> A: Request Created;
deactivate B;
A --> User: Done;
deactivate A;
@enduml
)

```
![Alt text](http://g.gravizo.com/g?
@startuml;
actor User;
participant "First Class" as A;
participant "Second Class" as B;
participant "Last Class" as C;
User -> A: DoWork;
activate A;
A -> B: Create Request;
activate B;
B -> C: DoWork;
activate C;
C --> B: WorkDone;
destroy C;
B --> A: Request Created;
deactivate B;
A --> User: Done;
deactivate A;
@enduml
)
```

> http://www.gravizo.com

> https://github.com/TLmaK0/gravizo

### Starts

To get a list of users that have stared a repository you can append /stargazers to the url of the repository:

```
https://github.com/[user]/[repo]/stargazers
```

### Watchers

You can also see who the watchers:

```
https://github.com/[user]/[repo]/watchers
```

> http://webapps.stackexchange.com/questions/41799/how-can-i-list-people-who-have-starred-my-github-repository

### Trending

Trending in open source: https://github.com/trending

### Hot Projects

Most forks: https://github.com/search?o=desc&q=stars:%3E1&s=forks&type=Repositories

Most stars: https://github.com/search?q=stars:%3E1&s=stars&type=Repositories

> http://stackoverflow.com/questions/19855552/how-to-find-out-the-most-popular-repositories-on-github

## Shell

### Batch Renaming

Rename '.png.jpg' to '.jpg':

```
rename '.png.jpg' '.jpg' ./*

-or-

cd dir/with/messedup/files

for file in *.png.jpg; do
	mv "$file" "${file%.png.jpg}.jpg"
done

-or-

for fn in *.jpg; do convert "$fn" `echo $fn | sed 's/jpg$/png/'`; done

-or-

ls *.jpg | xargs -I{} convert "{}" `echo {} | sed 's/jpg$/png/'`
```

This can be also be done with `xargs` and `sed` to change the file extension:

```
ls | grep \.png$ | sed 'p;s/\.png/\.jpg/' | xargs -n2 mv

-or-

find . -name "*.png" -print0 | sed 'p;s/\.png/\.jpg/' | xargs -0 -n2 mv

-or-

ls *.svg.png | xargs basename -s .svg.png | xargs -I {} mv {}.svg.png {}.png
```

If you have files in subdirectories that you want converted, then you can pipe find to a while read loop:

```
find . -type f -name '*.png' |
while read file; do
	convert "$file" -resize "${file%.png}.jpg"
done
```

> http://stackoverflow.com/questions/10972002/batch-renaming-files-in-command-line-and-xargs

### Random File

Choose a random file from a directory in a shell script:

```
ls path/to/*.mp3 | awk 'BEGIN{ srand(); } { line[NR]=$0 } END{ print line[(int(rand()*NR+1))] }'

echo `find . -maxdepth 1 -mindepth 1 -type f -print0 | sort --zero-terminated --random-sort |  sed 's/\d000.*//g'`

find . -type f | shuf -n1

for f in `ls /usr/bin`; do  echo "$RANDOM $f" ; done | sort -R | head -n1 | cut -d' ' -f2-
```

> http://stackoverflow.com/questions/701505/best-way-to-choose-a-random-file-from-a-directory-in-a-shell-script

### `pv`

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

Copy a file using `pv` and watch its progress:

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

### SSH

Piping the microphone from one machine to the speakers of another:

```
dd if=/dev/dsp | ssh -C user@host dd of=/dev/dsp

-or-

dd if=/dev/dsp | ssh -c arcfour -C user@host dd of=/dev/dsp
```

Tunnel audio chat over ssh:

```
arecord -f cd -t raw | oggenc - -r | ssh user@host mplayer -
```

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

## Imaging

Image conversion:

```
convert icon.svg -scale 32 tmp/32.png
convert tmp/16.png tmp/32.png tmp/48.png tmp/128.png tmp/256.png  icon.ico

/usr/bin/convert -resize x16 -gravity center -crop 16x16+0+0 input.jpg \
-transparent white -colors 256 output/favicon.ico

/usr/bin/convert -resize x16 -gravity center -crop 16x16+0+0 input.png \
-flatten -colors 256 output/favicon.ico

ffmpeg -i img.png img.ico
ffmpeg -i input.jpg -vf scale=320:240 output_320x240.png
ffmpeg -i input.jpg -vf scale=320:-1 output_320.png
```

> https://trac.ffmpeg.org/wiki/Scaling%20(resizing)%20with%20ffmpeg

## Web Development

### JavaScript Compressor

<li><a href="http://developer.yahoo.com/yui/compressor/">YUI Compressor</a></li>
<li><a href="http://code.google.com/closure/compiler/">Google Closure Compiler</a></li>
<li><a href="http://www.dojotoolkit.org/">Dojo ToolKit</a>'s ShrinkSafe compiler</li>
<li><a href="http://www.crockford.com/javascript/jsmin.html">JSMin</a></li>
<li><a href="http://github.com/mishoo/UglifyJS">UglifyJS</a></li>

> http://stackoverflow.com/questions/599911/what-do-you-use-to-minimize-and-compress-javascript-libraries

> http://stackoverflow.com/questions/28932/best-javascript-compressor

### Tool to Unminify / Decompress JavaScript

- [JSBeautifier](http://jsbeautifier.org/)
- [Javascript Formatter](http://www.blackbeltcoder.com/Resources/JSFormatter.aspx)
- [UNMINIFY](http://unminify.com) - Unminify JS, CSS and HTML Code

> http://stackoverflow.com/questions/822119/tool-to-unminify-decompress-javascript

### Start a Web Server in Any Folder

#### Python

```shell
$ python -m SimpleHTTPServer 8080
```

Replace `8080` with another number if you want it to listen on a different port.

For ports < 1024 it needs to run with root privileges.

The python 3.x equivalent of this is:

```shell
$ python3 -m http.server
```


#### PHP

```shell
$ php -S 0.0.0.0:8080
```

#### Ruby

Without `gem`

```shell
$ ruby -run -e httpd . -p8080
```

With `serve`

```shell
$ gem install serve
$ serve 8080
```

#### Node.js

Use `Connect` and `ServeStatic` with `Node.js`:

1. Install connect and serve-static with NPM

   ```shell
   $ npm install connect serve-static
   ```

2. Create server.js file with this content:

   ```shell
   var connect = require('connect');
   var serveStatic = require('serve-static');
   connect().use(serveStatic(__dirname)).listen(8080, function(){
       console.log('Server running on 8080...');
   });
   ```

3. Run with Node.js

   ```shell
   $ node server.js
   ```

Simplest Node.js server:

```shell
$ npm install http-server -g
$ http-server
```


## Reference

