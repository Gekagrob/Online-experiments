# Online-experiments

This repo contains materials needed for running phonetic adaptation experiments over the internet, in participants' web browsers.

The folder is organized as follows. 

## Root folder

Two experiments are included: one experiment uses a 2 alternative forced choice (2AFC) task and one uses a transcription task. In each experiment, participants are exposed to some audio and/or visual stimuli and make responses by pressing corresonding buttons on the keyboard.

For each experiment, there is a html file and a js file, labeled in the same way.

The html file specifies the corresponding js scripts (including the scripts that implement each experimental module) used to implement the web-based experiment.

The js file specifies the structure of the experiment as well as the parameters one can manipulate to suit different experimental designs (e.g., condition, training list, test list). 

### Structure of the js file
 
The experiment is defined by several blocks (e.g., instructions, training, test). Each block is implemented by a js script in /js-adapt/. 

**Design structure** The general setup of the example experiments is as follows:

  + Experiment Instructions
  + Exposure instructions
  + Practice for exposure
  + Exposure block (training)
  + Test instructions
  + Practice for test
  + Test block (Test1, Test2)
  + Survey on accent perception and language background
  + Demographic survey

#### Parameters

This file also specifies a number of parameters that define the procedure of the experiment. 

+ Experiment setup: `rsrbProtocolNumber`, `consentForm`, `survey` are specified at the top. 
+ URL parameters: these are extracted from the URL (see below)
+ Block parameters
(most parameters are defined in this file and are self-explanatory; below are some typical parameters that can be varied to create variations of a experimental block; see corresponding block js script for detail):
	- showInTest: {'false', 'true'} //when url contains 'mode=test', don't include this block
	- blockRandomizationMethod: {'shuffle', 'dont_randomize'} // whether the order of items within this block are randomized or not
	- mediaType: {'audio', 'visual'} // whether the stimuli is audio or visual
	- feedback: {'false', 'true'} // whether feedback is provided or not 
+ Stimuli paramters
	-  trainingPrefix: directory that contains stimuli for training block
	-  test1Prefix: directory that contains stimuli for test block 1
	-  test2Prefix: directory that contains stimuli for test block 2
	-  trainingList: list of stimuli for training block
	-  test1List:l ist of stimuli for training block for test block 1
	-  test2List: list of stimuli for training block for test block 2
	

## How to create a URL for the experiment

For a test run of the experiment locally, one can run the following: `python -m SimpleHTTPServer`, and use the following URL:

+ For the full experiment: http://0.0.0.0:8000/exp1_2AFC.html?condition=experimental&speaker=M15&order=1&visual=2&block=2
+ For a brief version (limited number of items in each block): http://0.0.0.0:8000/exp1_2AFC.html?condition=testRun&TeL=0
*Test mode*: add `&mode=test` to the end of the URL to skip the initial section (Instructions, Consent form, Headphone adjustment, etc.)

To launch the experiment on the internet, use the following URL (the URL parameters should be specified):
https://www.hlp.rochester.edu/mturk/xxie/io_perception/exp1_2AFC.html?condition={condition}&speaker={speaker}&order={order}&visual={visual}&block={block}

**URL parameters**
The URL takes a few parameters that are defined in the experiment js file. 

+ For the full experiment: 
  +  `condition`:  {'experimental', 'control'} // Which condition is used
  +  `speaker`: {'M4', 'M15'} // Which speaker is used at test phase
For each Condition X Speaker combination, there are 8 lists (2 list item order X 2 test block order X 2 visual orders)
  +  `order` // Which of two reversed orders of items within a list
  +  `visual` //Which of two orders for visual stimuli presentation (whether the target word appears left or right on the screen)
  +  `block`: {'1', '2'} // Which block order is used, whether stimuli set 1 appeared in test block 1 or test block 2
  
+ For a brief version
  +  `condition`:  {'testRun'} // Which condition is used
  +  `TeL`: {'0'} // Which lists are used

## img

This folder contains images presented on the screen during the experiment. 

## js-adapt 

This folder contains various scripts used to create different experimental blocks. For instance, `transcription_fb.js` implements a transcription block with feedback.

## lists

This folder contains the lists of stimuli, organized by experimental blocks. Files ending with "_list0" are the truncated versions of stimuli lists used in test mode (which can be conveniently used to debug the experiment).

## stimuli

This folder contains the audio stimuli used in the main experiment.

## stimuli_soundcheck_

This folder contains the audio stimuli used in the screening phase. 

## surveys

This folder contains the surveys presented at the end of the experiment.

