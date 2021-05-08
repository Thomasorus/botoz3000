# 🤖 BOTOZ 🤖

> A bunch of command line scripts to automate repetitive tasks podcasters have to do.

## The tasks

Botoz can execute 3 tasks:

- Turn a youtube video to an mp3 file, create an xml file with the `<item>` part pre-filled, then update the main xml file.
- Create an xml file with the `<item>` part prefilled with the metadata found inside an existing mp3 file, then update the main xml file.
- Create an xml file with the `<channel>` part automatically written from the config file.


## How to use

Botoz3000 needs some configuration steps before being used. Once they are done, those configurations steps can be reused indefinitely.

### The `config.py` file

This file contains the configuration for all your podcasts. You can have just one or 100. Inside of it, you will see this:

```python
podcasts = {
    "default": {
```
Followed by a lot of text. This is the sample/example of a podcast. Copy paste everything starting from line 4 and paste it at the end before the final bracket. Rename the `default` you just pasted to the podcast you want to manage.

Then fill in everything:

- `general` contains general informations and configurations you will need to do certain tasks.
- `mp3` contains configuration for the quality of encoding of your mp3 files
- `channel` contains the podcast `<channel>` informations required to build an XML podcast file.
- `item` contains the podcast `<item>` informations required to generate an entry.

Each line has an explanation about what it's used for. **If a line does not have an explanation, it means you don't have to touch it and it will be filled by Botoz**.

### The command line

Once the podcast configuration is done, use the command line this way:

- `./botoz3000.sh your_command your_podcast file_or_url`

For example, to download a youtube video and turn it into a podcast:

Download the files, go to the folder, open a terminal and type:

- `./botoz3000.sh yt-mp3 default https://www.youtube.com/watch?v=yBLdQ1a4-JI`

Let the script work, it will return to you a mp3 and an xml file in a folder.

## Requirements

You need to install:

- youtube-dl
- ffmpeg
- requests

On MacOS you can use Brew to install youtube-dl and ffmpeg:

- `brew install youtube-dl`
- `brew install ffmpeg`

But you'll also need to use the Python package manager:

- `pip3 install requests`

On Ubuntu:

- `pip3 install youtube-dl`
- `pip3 install ffmpeg`
- `pip3 install requests`

On windows:

- **Not tested for now**
- Download Python 3 [here](https://www.python.org/downloads/)
- `pip3 install youtube-dl`
- `pip3 install ffmpeg`
- `pip3 install requests`


## About MP3 quality

### VBR table

Use this table to choose the quality of your mp3 files.

[More info](https://trac.ffmpeg.org/wiki/Encode/MP3)

<table class="wiki">
<tbody><tr><th colspan="4"> <strong>LAME Bitrate Overview</strong> 
</th></tr><tr><td> <tt>lame</tt> option </td><td> Average kbit/s </td><td> Bitrate range kbit/s </td><td> <tt>ffmpeg</tt> option
</td></tr><tr><td> <tt>-b 320</tt> </td><td> 320 </td><td> 320 CBR (non VBR) example </td><td> <tt>-b:a 320k</tt> (NB this is 32KB/s, or its max)
</td></tr><tr><td> <tt>-V 0</tt> </td><td> 245 </td><td> 220-260 </td><td> <tt>-q:a 0</tt> (NB this is VBR from 22 to 26 KB/s)
</td></tr><tr><td> <tt>-V 1</tt> </td><td> 225 </td><td> 190-250 </td><td> <tt>-q:a 1</tt>
</td></tr><tr><td> <tt>-V 2</tt> </td><td> 190 </td><td> 170-210 </td><td> <tt>-q:a 2</tt>
</td></tr><tr><td> <tt>-V 3</tt> </td><td> 175 </td><td> 150-195 </td><td> <tt>-q:a 3</tt>
</td></tr><tr><td> <tt>-V 4</tt> </td><td> 165 </td><td> 140-185 </td><td> <tt>-q:a 4</tt>
</td></tr><tr><td> <tt>-V 5</tt> </td><td> 130 </td><td> 120-150 </td><td> <tt>-q:a 5</tt>
</td></tr><tr><td> <tt>-V 6</tt> </td><td> 115 </td><td> 100-130 </td><td> <tt>-q:a 6</tt>
</td></tr><tr><td> <tt>-V 7</tt> </td><td> 100 </td><td> 80-120  </td><td> <tt>-q:a 7</tt>
</td></tr><tr><td> <tt>-V 8</tt> </td><td> 85  </td><td> 70-105  </td><td> <tt>-q:a 8</tt>
</td></tr><tr><td> <tt>-V 9</tt> </td><td> 65  </td><td> 45-85   </td><td> <tt>-q:a 9</tt>
</td></tr></tbody></table>

## License

Botoz is a free to use by individuals and organizations that do not operate by capitalist principles. For more information see the license file.