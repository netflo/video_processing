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
