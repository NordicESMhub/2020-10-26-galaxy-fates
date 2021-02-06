---
permalink: /hackmd-day2/
---

# Online Galaxy Training on Functionally Assembled Terrestrial Ecosystem Simulator (FATES):  Day-2

[HackMD mechanics](https://coderefinery.github.io/manuals/hackmd-mechanics/)

## Note

- Participated in ICOS conference where there was a presentation on online educational tool for ICOS data and ecosystem functioning. 
  Might be interesting to have a look at that for further development. 
- Try out ICOS educational material – online service https://exploredata.icos-cp.eu
- Access to educational material https://github.com/ICOS-Carbon-Portal/jupyter/tree/master/education 
- Access to SSC education project material (Swedish) http://github.com/lunduniversity/schoolprog-satellite
- Yes, using it (with more comprehensive ecological and modelling background notes) in education (HE) would be good. Could be a stand alone workshop, as this is, or a shorter practical exposing early career ecologists (& modellers) to cross disciplinary thinking. Walk-through videos, were also one element discussed.

## Workflow hub

- Info on how to register your workflow to workflowhub: https://about.workflowhub.eu/How-to-register-your-workflow(s)-in-WorkflowHub/ 
(you can login with your github account if you have one; otherwise youwould need to register if you want to upload workflows).

- Workflow from the training is now published on workflow hub: https://workflowhub.eu/workflows/65

![](https://i.imgur.com/rJVG4oo.png)

also available as a shared workflow (shared data --> workflows (then search for fates)).

## Galaxy JupyterLab

https://training.galaxyproject.org/training-material/topics/climate/tutorials/fates-jupyterlab/tutorial.html

- https://vimeo.com/439192348

## Check your run

```
%%bash
cd $HOME/work/fates_alp1
ls -la
```


```
import os
import xarray as xr
xr.set_options(display_style="html")
%matplotlib inline

case = 'fates_alp1'
path = os.path.join(os.getenv('HOME'), 'archive', case, 'lnd', 'hist')
dset = xr.open_dataset(path + '/fates_alp1.clm2.h0.2000-01.nc')
dset
```


```
dset['CANOPY_AREA_BY_AGE'].plot(aspect=3, size=6)  #(aspect=3, size=6, col='fates_levage', col_wrap=1)
```

## Feedback (from today and more generally for future CLM-FATES Galaxy tools & JupyterLab)

- One positive feedback:
  - Very useful to learn how workflow works. 
  - Thats certainly useful to learn Galaxy with CLM FATES simulations. Workflow is already good, but there are rooms to improve. 

- One thing to improve:
    - more explanation for step 6 (smaller steps)
    - more introductions on workflow (creating, sharing, using) and hope to learn more how to develop galaxy tools related to fates. 

- Issues from the feedback: https://github.com/galaxyproject/training-material/issues/2099
      - Feel free to comment, etc.

## Question

- Are there resources for preparing your own CLM-FATES input data?
   - Yes, in various places.
   - CTSM has a tool folder for generating inputdata for any experiments. Look at the readme file there: https://github.com/ESCOMP/CTSM/tree/master/tools
   - EMERALD branch of CTSM also have some tools for creating single site simulations. You can adapt them to your site. 

   - Other places?
   - https://github.com/ESCOMP/CTSM/tree/master/tools/contrib
   

- Are there resources for preparing your own CLM-FATES input data?
    - https://github.com/serbinsh/ctsm_containers/tree/master/tools/create_single_point
    - https://github.com/ESCOMP/CTSM/tree/master/tools
    - https://github.com/ESCOMP/CTSM/wiki/Meeting-Notes-2020-Science

- Do you use extract dataset from list to extract the dataset for step 6?
   - Yes. Edit your workflow and customize it to run your new CO2 experiment. For this you would need to add an extra step to extract the first history file from the history collection and generate the corresponding plot. The final workflow would be similar to the one shown below

- I think that's the one, but then I do not know how to link it in the workflow
    - Just drag the arrow button on the boxes to the arrow of the boxes you want to link the work flow. When you click the starting arrow, some arrow will not linkable (Yellow), just choose the green arrows to link.
    - These need to have more step by step instructions (including how to link tools/outputs etc) if this is to be a stand-alone tutorial.

- Sorry, I did not understand: why can you not drag and connect the added tool directly in the workflow? What do you need to do to fix this? 
     - If you change datatype in the extract tool it can be connected.
          - I tried manually specifying "netcdf" as output, that does not help.
                  - click on the input (red circle) to clean it.
                        - Great: it works.
                        
- its "filled with another connection" issue (same issue as above)
    - Okay, fixed it
    - you need to click on the red "stop sign" thing, then it removes a connection artifact apparently directly on the node 
    - Also remember to refesh your website at some point, if all the solution does not work

- Also, in the workflow, my 'CTSM_FATES-EMERALD_version2.0.0_ALP1_restart_2300-01-01.tar' doesn't connect to the 'CTSM/FATES EMERALD' box.
Specifically, it's not connecting to 'restart for running FATES EMERALD' which doesn't appear as a second point within that box, unlike the example workflow. 
    - Ended up recoding everything, and now it works.
    - Happens when your CLM-FATES turned to 'startup' mode.

- also struggle with this step (#6).... In my workflow there is the "Extract dataset" part missing, and I seem not to be able to navigate to such a tool anywhere... 
     - see above answers. Better use climate.usegalaxy.eu to search the tools and it appears at the bottom.

- Is it possible to run the workflow in another history?
   - Yes. expand the full setup of the workflow. You will find it. 

- I also have problems running the workflow. I created a new history, but it is all red.
  - did you manually specify the correct inputs? 
      - I had to change the automatic selection

- Training material on workflows: https://training.galaxyproject.org/training-material/topics/galaxy-interface/tutorials/history-to-workflow/tutorial.html

- For the workflow, and extract toolbox, make sure you check the type (needs to be netcdf when selecting item in collection)

- All the tools are in https://toolshed.g2.bx.psu.edu/ Galaxy toolshed

- so say I want to rerun the workflow with the same settings but instead of site ALP1 I want to test the site BOR1, how can I make the inputdata available for the workflow?
   - Yes, several things need to be changed. e.g., input date, model resolution.
   - I did not have to change anything so I guess some info is missing in the tutorial.
       - The tutorial does not explain how to run with different input dataset but I agree it can be nice to explain (at least orally) and add a note on this.

- In the new workflow, how do we connect to the correct history data? For me there is no dropdowns for  in the new workflow? Or maybe I've done something wrong earlier.
    - Input datasets need to be available in current history and then choose 'send to new history' 

- Can you go back over how to connect to the correct history data, there is no dropdowns for me in the new workflow? Or maybe I've done something wrong earlier
  - Your inputdata are probably kept in different history. So, you need to switch to the history that have the inputdata, and you will have the options to choose the correct inputdata 

- You might need to re-enter the 'customize model run period' details, this is what I had to do, ie. the hybrid details, run times etc,.

- <span style="color:orange;">When running the workflow: my setup fails to create a plot even though the workflow diagram looks correctly linked, is there a way to display a message what went wrong and why certain steps were not executed?</span>

- Is there a galaxy tool to compare to model output the difference?
    - Example of tools you can use to make the diff: merge the two files (to get c1 c2 for each model) and then Compute an expression on every row (to make a diff). The you can plot the diff.

- "Could not find machine match for 'ac6a55bd313d' or 'ac6a55bd313d' WARNING: No cesm Model version found.
    - This is just a warning, not a problem. 
    
    
