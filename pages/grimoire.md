### Grimoire

Inspired by the [[grimoire of Fred Bednarski]](https://fdisk.space/grimoire/), this is my place to put assorted snippets of code (which may or may not be cursed, so use at your own risk). Have fun, poke around, but remember that this information may be totally borked.

To change the extensions of audio files in a directory:
> for file in *.opus; do ffmpeg -i ${file%.opus}.opus -c copy ${file%.opus}.ogg && rm ${file%.opus}.opus; done

To download the mp3 audio (or the best audio if that fails) of a youtube video:
> youtube-dl --add-metadata -i -x -f mp3/bestaudio "video_link"

To forward your port 8388 to a server's port 8384 (can be used to get the web interface for syncthing remotely):
> ssh -L 127.0.0.1:8388:127.0.0.1:8384 username@yourserver

To sanitize a file name (the .opus can be any extension):
> mv "$file" "$(echo "${file%.opus}" | iconv -cf UTF-8 -t ASCII//TRANSLIT | tr -d '[:punct:]' | tr '[:upper:]' '[:lower:]' | tr ' ' '-' | sed "s/-\+/-/g;s/\(^-\|-\$\)//g").opus"

*Last updated: {{date}}*