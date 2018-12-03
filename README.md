# video_processing


broken mp4:
 - Repair missing keyframes
 - lost key frame 

editing via shotcut for example

ffmpeg -i "input_file.mp4" -force_key_frames "expr:gte(t,n_forced*3)" -strict -2 output_file.mp4
