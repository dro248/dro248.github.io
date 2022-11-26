# FFMPEG & Bash Incatations

Convert ts file (MPEG-2 stream) to mp4 (with PV progress bar):
```bash
# w/ progress bar
pv sample_input_video.ts | ffmpeg -i pipe:0 -c:v h264_videotoolbox -c:a aac sample_output_video.mp4 -hide_banner

# w/o progressbar
ffmpeg -i sample_input_video.ts -c:v h264_videotoolbox -c:a aac sample_output_video.mp4 -hide_banner
```

Convert ts file (MPEG-2 stream) to mp3 (with PV progress bar):
```bash
# w/ progress bar
pv sample_input_video.ts | ffmpeg -i pipe:0 -q:a 0 -map a sample_output_video.mp3

# w/o progress bar
ffmpeg -i sample_input_video.ts -q:a 0 -map a sample_output_video.mp3
```

Batch rename ts files to mp3:
```bash
# use the -n flag for dry-run testing
rename  's/\.ts$/.mp3/' *.ts
```

Batch remove the substring '.ts' from all files ending in .mp3:
```bash
rename rename 's/.ts//' *.mp3
``` 