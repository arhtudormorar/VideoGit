# VideoGit
## Converts git commit history, to a beautiful animated coding video.
## Installation
1. [Install Silicon with `brew install silicon` or `cargo install silicon`)](https://github.com/Aloxaf/silicon)
2. [Install FFmpeg](https://ffmpeg.org/)
3. Run `pip install videogit`
## Usage
- Make sure you cd to the root directory containing your git repo. ( You should be able to run git commands like `git status` )
- run `videogit -l` to view a list of your commits
- pick and copy the hash of your starting commit, if you do not specify final commit hash, videogit will just make the video from your starting hash to the latest commit
- run `videogit <starting_commmit_hash_here>` or `videogit <starting_commmit_hash_here> <final_commit_hash_here>` filling in the starting and ending hashes
- run `videogit -h` for a full list of options

## Example Usage
- `videogit ba12dc8 -wpm 60 -r 24 -f main.py test.cpp include/test.h`
  
  Creates a 24 fps video from the commit ba12dc8 to the HEAD, at a typing speed of 60 wpm, for files `main.y`, `test.cpp`, and `include/test.h`
 
- `videogit 5f7198d a06dcff -o output-dir` 

- `videogit 5baaac53561796cd69b0ac71112f1105f4005375 -w 60 -r 24 -f tests/video01.spec.ts --show-line-numbers --title "tests > video01.ts"`

  Creates a video from commit 5f7198d to commit a06dcff, for all files changed over that period, and outputs the videos to `output-dir`

- `videogit $(git log --grep="^01" --pretty=format:"%h" -n 1) $(git log --grep="^02" --pretty=format:"%h" -n 1) -w 180 -r 24 -f tailwind.config.js --show-line-numbers --title "tailwind.config.js" --output-filename 01_video`

  Creates a video from the first commit with message starting "01" to the first commit with message starting "02", with custom output filename `01_video--tailwind.config.js.mp4`
## Example Videos
[![Video Git Demo](https://img.youtube.com/vi/872y0LlQmGg/0.jpg)](https://www.youtube.com/watch?v=872y0LlQmGg)

## All Options
```
                            -------- VideoGit --------                          

usage: videogit [-h] [-l] [-f FILES [FILES ...]] [-d GIT_REPO_DIRECTORY] [-w WPM] [-r FRAME_RATE] [-o OUTPUT_DIR]
                [-u UP_DOWN_SPACE] [-m MAX_LINE_LENGTH] [-v] [--show-line-numbers] [--title TITLE]
                [--output-filename OUTPUT_FILENAME]
                inital_commit [final_commit]

VideoGit by shahanneda (shahan.ca): Converts git commits, to a beautiful animated video. To get started
type videogit -l,

positional arguments:
  inital_commit         the hash of the commit to start the video at
  final_commit          the hash of the commit to end the video at, if not specified will use the HEAD (default:
                        the most recent commit)

options:
  -h, --help            show this help message and exit
  -l, --list-git-commits
                        list your recent commits and hashes (default: None)
  -f, --files FILES [FILES ...]
                        a list of specific files to make the video, if not set will try to to make the video for
                        all changed files, example: videogit <hash> -f file1.cpp file2.cpp) (default: None)
  -d, --git-repo-directory GIT_REPO_DIRECTORY
                        the repo of your project, only needs to be set if it is diffrent than the current working
                        directory (default: current directory)
  -w, --wpm WPM         the speed of the video in words per minute (default: 480)
  -r, --frame-rate FRAME_RATE
                        the framerate of the output video (default: 30)
  -o, --output-dir OUTPUT_DIR
                        the directory of the output videos (default: current directory)
  -u, --up-down-space UP_DOWN_SPACE
                        how many lines above and below the current editing line to include in the video (default: 20)
  -m, --max_line_length MAX_LINE_LENGTH
                        the maximum line length in chars before wrapping the text (default: 200)
  -v, --verbose         print any errors or logging information (default: False)
  --show-line-numbers   show line numbers in the output video (default: False)
  --title TITLE         custom title to display in the window (default: file path) (default: None)
  --output-filename OUTPUT_FILENAME
                        custom prefix for the output video filename (replaces the commit hash part, default:
                        {commit1}--{commit2}--) (default: None)
```

## Local installation
1. `pipx uninstall videogit`
2. `pipx install -e .`

## Contributing
Feel free to make any pull requests with new features or fixes.
