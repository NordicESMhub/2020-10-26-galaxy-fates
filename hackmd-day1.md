---
permalink: /hackmd-day1/
---


# Online Galaxy Training on Functionally Assembled Terrestrial Ecosystem Simulator (FATES), day 1

Your host for this online meeting will be: Anne Fouilloux

[HackMD mechanics](https://coderefinery.github.io/manuals/hackmd-mechanics/)


# 🗣 Welcome & practical information for workshops (30 mins)

•	Hi! 🙋 Today we learn about CLM-FATES and how to run it in the Galaxy portal.


### Where to find the training material

- The training material is available on the [Galaxy Training Network](https://training.galaxyproject.org/)

    - [Introduction to FATES](https://training.galaxyproject.org/training-material/topics/climate/tutorials/fates/slides.html)
    - [CLM-FATES Galaxy tool Hands-on](https://training.galaxyproject.org/training-material/topics/climate/tutorials/fates/tutorial.html)
    - [CLM-FATES in Galaxy Climate JupyterLab](https://training.galaxyproject.org/training-material/topics/climate/tutorials/fates-jupyterlab/tutorial.html)


- All material is online and CC-BY.

## How to ask questions and follow along: HackMD

* **HackMD is our base communication system**:
    * You can **ask questions** at the bottom
    * You can check towards the bottom for a link to our current section
* [HackMD mechanics](https://coderefinery.github.io/manuals/hackmd-mechanics/)
* Anytime, create a new bullet point **at the bottom** to ask a question.  Someone will be watching and respond, and ask the instructor by voice if you want.
* HackMD should contain detailed information on hands-on and breaks (always at bottom).
* You can also ask questions by voice anytime

## How to watch and listen: Zoom

- [Zoom mechanics](https://coderefinery.github.io/manuals/zoom-mechanics/) - you probably know this by now
- Rename yourself to  **Firstname Lastname**.  You can rename yourself from the participant list.
- **You can indicate status from participant list**: Yes="going well", No="have a problem".  We watch other signals, too.
    - Everyone please indicate "Yes" if you find the "yes" sign.
- We understand that screen space is limited. If you have an external screen, we recommend to use it but we cannot require it. Although all the material is online, we will try to not require you to have all the windows open at once.

## Code of Conduct

- We follow [The Carpentries Code of Conduct](https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html).
- This is a hands-on, interactive workshop.
    - Be kind to each other and help each other as best you can.
    - If you can't help someone or there is some problem, let someone know.
    - If you notice something that prevents you from learning as well as you can, let us know and don't suffer silently.
- It's also about the little things:
    - volume
    - font size
    - generally confusing instructor
    - **not enough breaks**

## Additional Material
- [Longer 2019 FATES tutorial slides](https://docs.google.com/presentation/d/1kztSENcOOw54XpjDCebcOLWciC8kqJegkMJGnuQKisI/edit?usp=sharing)
- [Perspetives paper](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1029/2018MS001453)
- [Koven et al FATES paper](https://bg.copernicus.org/articles/17/3017/2020/bg-17-3017-2020-discussion.html)
- [Needham et al. 'prescribed phyisology' paper](https://escholarship.org/content/qt2qx8z1xx/qt2qx8z1xx.pdf)

There are Biweekly FATES meeting. Contact FATES developers if you are interested (for instance Rosie).

## Github of FATES:

- https://github.com/NGEET/fates
- https://github.com/NGEET/fates/issues


## 💻 Hands-on preparation
 
 - Login to https://climate.usegalaxy.eu/ and login to https://usegalaxy.eu/

## Questions on FATES introduction

- Where can I find obervations to compare with FATES simulations? 
    - Observations available at https://ns2806k.webs.sigma2.no/EMERALD/EMERALD_platform/observation/

- Tools and Examples (for now to be used from Galaxy JupyterLab):
    - “Here's the link to the library (only the first two functions are really fates-specific, and can hopefully be a template for how to unroll the other 
       multiplexed dimensions via xarray): https://github.com/ckoven/ctsm_py/blob/master/ctsm_py/fates_xarray_funcs.py”

    - https://github.com/ckoven/ctsm_py/blob/master/notebooks/fates_notebook.ipynb

- FATES Intro (slides:
    - At some point, the understorey disappear, why?
          - The video is available at: https://doi.org/10.5446/43627 (Koven et al., 2020 https://doi.org/10.5194/bg-17-3017-202)
    - How many PFTs are there in FATES? 
          - Currently 12 in default
          - However many PFTs as you want but there are 12-16 clearly defined ones right now (12 in default parameter file (easy to turn off) + some people are making new ones).
    - How do bushes, grass, mosses and such fit into the picture? 
          - https://github.com/NGEET/fates/issues/707 
          - There's a discussion group trying to define plant functional traits for mosses (from a non-LSM perspective) which may inform the moss development, if we want it to be consistent with the broader research field. 
    - Has FATES been compared to individual based models? Do you think that will be the future of Vegetation models when computational power allows at some point? 
          - Yes there were a few studies available.
  
    - Does FATES represent permafrost processes?
          - No. (The Host Land Model (HLM) handles the non-biotic soil.)
          - FATES only simulates the living vegetation, so the PF processes is handled by the host model (e.g. CLM). 
     - Does FATES replaces CLM or will be part of CLM? 
          - FATES runs in a "host" LSM. So, it is not going to replace CLM 
          - It replaces the "natural vegetation" in CLM 5.0+.
      - Do I assume correctly, to implement O3 damage (from single leave impact to ecosystem impact) in a meaningfull way, one would need to implement it into FATES in the long run?
      - CLM has ozone damage to plants, don’t know if that carries over to FATES or not. 
      - Reduced complexity modes are super cool! Is there any documentation available on these modes so far, so people could follow what will be developed in the near future.
           - See links above on extended documentation

## Questions on Intro to Galaxy:

- Current PPT is available here: https://training.galaxyproject.org/training-material/topics/introduction/slides/introduction.html#1
- I saw the Cyverse logo on a slide, how does Galaxy compare to a service like Cyverse?
    - CyVerse has enabled Galaxy to serve thousands of researchers worldwide.
- So Galaxy 'Tools' abstract an application, script, or workflow?
    - A galaxy tool wraps an existing application (for us FATES) so that we can run these tools within complex workflows.
- Since Galaxy is open source are different servers running differnt versions, do you have to be careful with that?
    - Yes there are several instances worldwide: some are public and others are private. 
    - Workflows created on one instance can run on another according the tools were installed by the Galaxy admins.
    - Yes in our case, we have to use the European Galaxy instance because FATES has not been deployed on any other instances (such as the main Galaxy instance in US or Galaxy instance in Australia). 
    - when using a Galaxy instance and willing to run climate tools, first checks that the tools are available; if not contact the corresponding Galaxy administrators and ask if the tools can be installed. 
    - Anyone can use Galaxy Europe; even if you live/work outside Europe.
- How do you find a tool from the toolbox if you know what you want to do but don't know how it is called?
  - use toolshed to browser more info link:
  - https://toolshed.g2.bx.psu.edu/
  - https://galaxyproject.org/toolshed/
  - The gitter link for asking questions about tools (who can fill the link?): 
     - https://climate.usegalaxy.eu/ bottom right "startchat" button
     - For Galaxy Europe: https://gitter.im/usegalaxy-eu/Lobby 

- How can the model be developed without version control? 
  - If using GALAXY tools, version control is fixed and done automatically
  - For model development, we will use interactive tools (jupyter notebook). Git will be available for version control.

- which galaxy should we use? climate, the general one or live? 
  - Use: https://climate.usegalaxy.eu/, and login
  - https://climate.usegalaxy.eu/ is the same Galaxy instance than https://usegalaxy.eu; the only different is the front page and visibility of tools: we try to highlight climate tools in the climate Galaxy instance.
  

- How to look at the info of each processing dataset in history?
  - Left click the dataset, there is an info (i) button appear, just click the info button. You will see the info. 

- How to keep the GALAXY history running safely without unexpected interruption? 
    - Tasks are running on remote machines "independently" of the Galaxy server itself. You can safely close your web browser and the tasks will continue to run.

- How to move the output files of the model from GALAXY to other places?  
    - You can download them directly (save icon).
    - When writing a paper, we recommend you archive the results from your history for instance in Zenodo, pangea or any other national archive (for instance NIRD archive in Norway).

- PROBLEMS?! An error occurred. An error occurred while updating information with the server. Please contact a Galaxy administrator if the problem persists.
     - Problems on the Galaxy server may occur and if the task is not rerun automatically, you can re-run the task. 
     - In workflow, we can set re-submit automatically. I think there are some problems on the server (due to the last upgrade on Friday). You can also notify the Galaxy team on gitter (https://gitter.im/usegalaxy-eu/Lobby)

- If your CLM-FATES task turned red: it failed. No panic. 
     - Galaxy server may have problems (see above). Anyway, before re-running your task, double check your CLM-FATES parameters (in particular inputs and restart files).
     - How do you check that and which job needs to be resubmited?
    ![](https://i.imgur.com/m4Ul51u.png)

- It takes for ever. Is it still running?
      - Remember to refresh the website if your dataset in GALAXY history remain yellow (in processing) for a long while.

- Panoply cannot see my history file?
      - To use panoply, make sure to add ".nc" in the file name, or else, panoply will not be able to recognize

- From where should I start panoply?
      - Remember to login on live.usegalaxy.eu, your GALAXY history will appear automatically.

- How can I change history?
      - If you have several history ongoing, you may have to navigate the history (right upper corner, window symbol) to switch the working history to the right one that you want. 

- I did not manage to run CLM-FATES: how can I catch up?
      - If your CLM-FATES failed but you still want to play with Panoply, etc. Here is a shared history with 5 years simulation: https://climate.usegalaxy.eu/u/annefou/h/fates 
        you can them import it in your history.


## feedback

one positive feedback:
- I guess this has taken some time - thank you!
- Good pace, nice tutorial layout :)
- Agreed, was nice to work through things step by step
- great to work with GUI

one thing to improve:

-	Some sort of progress bar to keep track of the model run would be nice!
-	Check validity of input before model compilation (avoid crashes after long time)
-	GALAXY page Not adaptive to smaller screens, makes it difficult to navigate when using split screen
-	still not entierly clear what I should do in which "page" (live / climate etc)
-	One might need to refresh Galaxy to see if the run is over
-	Could we separate compiling and running as seperate tools for the model, because many of the modelling work will just use the same compiled executables. Then, people just need to replicate the running workflow rather than compiling workflow. 












