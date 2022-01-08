# video_processing


broken mp4:
 - Repair missing keyframes
 - lost key frame 

#editing via shotcut for example

ffmpeg -i "input_file.mp4" -force_key_frames "expr:gte(t,n_forced*3)" -strict -2 output_file.mp4


#processing all videos to the same MP4 baseline, to avoid distorsions , sync issues audio + video  
ffmpeg -i titlefile.mp4 -vf setdar=16/9 -video_track_timescale 29971 -ac 1 newtitle.mp4

#each of the newtitle.mp4  files go into mylist.txt
#content is:
    file './newtitle.mp4'
    ...

#then joining those baseline MP4s:
ffmpeg -f concat -safe 0 -i mylist.txt -c copy output


Broken mkv or unknown codec try:  
ffmpeg -i "example input video.mov" -vcodec h264 -b:v 10485760 -acodec aac -b:a 327680 "transcoded video.mp4"


Changing the bitrate:

discover what it is today with b/r or bitrate or b, usually 10,000kb/s with:  ffmpeg -i  file

and set what it should be around with    -b 1000k

=>   ffmpeg -i input.mp4 -b:v 1000k -vcodec h264 -acodec ac3 output.mp4


reduce frame rate:
 To change the output frame rate to 30 fps, use the following command:

ffmpeg -i <input> -filter:v fps=fps=30 <output>

 
 
 
 
 
ffmpeg -i input.mp4 -vcodec libx264 -profile:v main -level 3.1 -preset medium -crf 23 -x264-params ref=4 -acodec libmp3lame -movflags +faststart output.mp4
## converting Videos to iPad format for an old iPad2 on res. of 1024x720/landscape
ffmpeg -i How_Home_Plumbing_works.mkv -vf scale=-1:720 -c:v libx264 -crf 18 -preset medium -c:a copy How_Home_Plumbing_works3.mp4
