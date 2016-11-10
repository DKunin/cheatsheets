# Make video smaller

    ffmpeg -i vid.mp4 -vf scale=640:480 vid-small.mp4

# Rotate video

    ffmpeg -i in.mov -vf "transpose=1" out.mov

For the transpose parameter you can pass:

0 = 90CounterCLockwise and Vertical Flip (default)
1 = 90Clockwise
2 = 90CounterClockwise
3 = 90Clockwise and Vertical Flip

Use -vf "transpose=2,transpose=2" for 180 degrees.

# Trim from 2″ for 3 seconds, and encode into a "Twitter friendly" format.

    ffmpeg -i source.mp4 -pix_fmt yuv420p -an -ss 2 -t 3 temp.mp4

# Make a palette for GIF.

    ffmpeg -i temp.mp4 -vf palettegen=max_colors=24 palette.png

# Make a GIF with the palette.

    ffmpeg -i temp.mp4 -i palette.png -filter_complex "scale=400:-1:flags=lanczos[x];[x][1:v]paletteuse" -r 30 out.gif

# Get info from video info

    ffmpeg -i video.avi

# Turn video into images

    ffmpeg -i video.mpg image%d.jpg

# Extract sound and save as mp3

    ffmpeg -i source_video.avi -vn -ar 44100 -ac 2 -ab 192k -f mp3 sound.mp3

# Convert wav to mp3 

    ffmpeg -i son_origine.avi -vn -ar 44100 -ac 2 -ab 192k -f mp3 son_final.mp3

[CheatSheet](http://rodrigopolo.com/ffmpeg/cheats.php)