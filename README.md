# Autoscreencast

This utility is meant to enable easier recording of screencasts. It interprets a
markdown file to send commands to a window that is being recorded.

## Requirements
* ffmpeg
* asciinema
* screenkey
* xdotool

## Usage

1. Open two terminal windows, one is the target and the other is the script
2. Run `record_screencast` in the script terminal in a directory with
    a properly formatted markdown script. Default name is `<dirname>.md`
3. Wait for recording to finish

### Examples

#### README.md
This README is properly formatted to run this example directly.
1. Open two terminals, the script window should be in this repo
2. Run `record_screencast -y -s README.md`
3. Select the record terminal when prompted

You should see the following commands entered in the terminal
```
command echo "Hello"
```

We can also send individual keypresses
```
key e c h b space quotedbl H e l l o quotedbl
```

Whoops, we misspelled `echo` as `echb`. Let's go back
and fix it
```
key Left Left Left Left Left Left Left Left
key BackSpace o Return
```

We may also be in a position where we need to sleep
so a command can complete.
```
command echo -n "Hello " && sleep 1 && echo "World"
sleep 1.5
command echo "Finished"
```

We can also send control key sequences
```
command echo -n "Hello " && sleep 100 && echo "World"
sleep 1.5
key ctrl+c
```
