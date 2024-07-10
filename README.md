# Streaming Setup {ffmpeg} Deep stream

This repository provides instructions on how to use the `bluenviron/mediamtx` Docker image to stream media files via RTSP using FFmpeg.

## Prerequisites

- Docker installed on your system
- FFmpeg installed on your system
- Local media files (e.g., `.mp4`, `.mp3`) to stream

## Pull and Run the Docker Image

1. Open a terminal and pull the latest `bluenviron/mediamtx` Docker image and run it:

    ```bash
    docker run --rm -it --network=host bluenviron/mediamtx:latest
    ```

2. The above command will download and launch the MediaMTX server on your local machine.

## Stream Media Files Using FFmpeg

1. Open a second terminal.

2. Use FFmpeg to stream your local media files to the MediaMTX server. Replace `<path_to_media_file>` with the path to your media file:

    ```bash
    ffmpeg -re -stream_loop -1 -i <path_to_media_file> -c copy -f rtsp rtsp://localhost:8554/mystream
    ```

    For example, if you have a video file `video.mp4` located in your home directory, the command would be:

    ```bash
    ffmpeg -re -stream_loop -1 -i ~/video.mp4 -c copy -f rtsp rtsp://localhost:8554/mystream
    ```

    ```bash
    ffmpeg -re -stream_loop -1 -i "/home/vikas/kunal/Shah Rukh Khan & Amir Khan talk about their wonderful interaction with PM Modi.mp4" -f lavfi -i anullsrc=r=44100:cl=stereo -c:v copy -c:a aac -b:a 128k -shortest -rtsp_transport tcp -f rtsp rtsp://mentioned the ip/mystream

    ```

    

## Documentation

For more detailed documentation, please refer to the [MediaMTX GitHub page](https://github.com/bluenviron/mediamtx?tab=readme-ov-file#ffmpeg).

## Troubleshooting

If you encounter issues, please check the following:
- Ensure Docker is running on your system.
- Ensure FFmpeg is installed and accessible from the terminal.
- Verify the path to your media file is correct.
- Check the terminal output for any error messages and refer to the [MediaMTX GitHub issues page](https://github.com/bluenviron/mediamtx/issues) for potential solutions.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
