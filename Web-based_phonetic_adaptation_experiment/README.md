# read-me

This folder contains materials needed for running phonetic adaptation experiments over the internet, in subjects' web browsers.

Two examples are included: one experiment uses a 2 alternative forced choice (2AFC) task and one uses a transcription task. In each experiment, participants are exposed to some audio and/or visual stimuli and make responses by pressing corresonding buttons on the keyboard.

The folder is organized as follows. 

# Root folder

For each experiment, there is a html file and a js file, labeled in the same way.

The html file specifies the corresponding js scripts (including the scripts that implement each experimental module) used to implement the web-based experiment.

The js file specifies the structure of the experiment as well as the parameters one can manipulate to suit different experimental designs (e.g., condition, training list, test list). 

## Structure of the js file
 
The experiment is defined by several blocks (e.g., instructions, training, test). Each block is implemented by a js script in /js-adapt/. 

**Design** The general setup of the example experiments is as follows:

   Experiment Instructions
   Exposure instructions
   Practice for exposure
   Exposure block
   Test instructions
   Practice for test
   Test block
   Survey on accent perception and language background
   Demographic survey

This file also specifies the stimuli and lists to be used in the experiment. 

## How to create a URL for the experiment

For local test one can run the following:
python -m SimpleHTTPServer

Then in the browser, use the following URL:
For test mode: http://0.0.0.0:8000/exp1_2AFC.html?condition=testRun&TrL=A&TeL=0&mode=test (mode=test skips the initial section)
For full experiment: http://0.0.0.0:8000/exp1_2AFC.html?condition=experimental&speaker=M15&order=1&visual=2&block=2

The URL takes a few parameters that are specified in the experiment js file: which experiment to run (the html file), experimental condition (condition), stimuli list, etc. 


# img

This folder contains images presented on the screen during the experiment. 

# js-adapt 

This folder contains various scripts used to create different experimental blocks. For instance, `transcription_fb.js` implements a transcription block with feedback.

# lists

This folder contains the lists of stimuli, organized by experimental blocks. Files ending with "_list0" are the truncated versions of stimuli lists used in test mode (which can be conveniently used to debug the experiment).

# stimuli

This folder contains the audio stimuli used in the main experiment.

# stimuli_soundcheck_

This folder contains the audio stimuli used in the screening phase. 

# Surveys

This folder contains the surveys presented at the end of the experiment.

