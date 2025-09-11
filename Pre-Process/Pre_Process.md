# Pre_Processing And Optical Visualization 

This comprises of two main parts, one is pre-processing and the other one is optical flow visualization

- `Pre_Processing`: The pipeline begins by initializing paths, defining optical_flow_data as the output directory and dataset videos as the input. It ensures the output directory exists or creates it if missing. All video files with extensions .mp4, .avi, or .mov are automatically discovered. Each video is opened using `cv2.VideoCapture`, and its FPS and resolution are read for monitoring. Frames are resized to 640×480 and converted to grayscale using `cv2.cvtColor`. Dense optical flow is computed between consecutive frames using `cv2.calcOpticalFlowFarneback`. The resulting motion vectors are saved as compressed .npz files, enabling efficient storage and later analysis of temporal motion patterns.

- `Optical_Visualization`: The visualization pipeline begins by initializing paths to load .npz optical flow files and their corresponding original videos, while creating the `visualized_optical_flow` output directory. It lists all flow files and matches them with the correct video sources. Each video is opened using `cv2.VideoCapture`, and motion vectors are loaded via np.load. Video properties like FPS and resolution are read for setup. An output writer is initialized to save the final .mp4. For each frame, flow vectors are converted to HSV (Hue = direction, Value = magnitude), then to BGR using `cv2.cvtColor`. The flow is blended onto the original frame using `cv2.addWeighted`, displayed live, and saved. Finally, all resources are released.


To sum it up the .npz files we obtain by running the pre-processing.py file, the obtained vectors(.npz) files are overlayed over the videos that we have got from UCF Crime data set in 7:3 ratio producing an optically visualized video where the motion is represented using HSV


