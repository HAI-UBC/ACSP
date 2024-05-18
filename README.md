# ACSP Software Development Manual 

## Meta 
Document Version: 0.2

Last updated: Spring 2024 by Vedant Bahel and Max G


Objective: This document presents:
1. List of different versions of the ACSP applets (located in the CS server)
2. How to edit the code of this applet and compile it?
3. How to run the applet?

## Tutorial video 

Watch a tutorial on the ACSP software manual and editing ACSP [here](https://youtu.be/AcGemFRnlwI)


## Different versions of the ACSP applet:

| Version | Name              | Features                          | Developer          | Year | Codebase (In CS server) | Materials|
| ------- | ----------------- | --------------------------------- | ------------------ | ---- | -------- | -------- |
| v0      | CSP               | Non-adaptive base CSP applet      | Team CISpace       | 1999-2010   | NA | [AISpace Website](http://www.aispace.org/index.shtml)     |
| v1      | ACSP              | Adaptive CSP applet (with hints)  | Samada K           | 2016-17     | /ubc/cs/research/conati/CIspaceCSP/XAI(Lea&Vanessa)/StudySoftware acsp-control.jar | [Thesis](https://open.library.ubc.ca/soa/cIRcle/collections/ubctheses/24/items/1.0348694)         |
| v2      | ACSP_Exp          | ACSP with explanations of hints   | Lea R and Vanessa P| Summer 2019 | /ubc/cs/research/conati/CIspaceCSP/XAI(Lea&Vanessa)/StudySoftware acsp-expl.jar | [Thesis](https://open.library.ubc.ca/soa/cIRcle/collections/ubctheses/24/items/1.0389817?o=0)|
| v3      | ACSP_Confusion    | Confusion self-reporting for hints| Vedant B           | Summer 2023 | /ubc/cs/research/conati/CIspaceCSP/ACSP_Bahel_Sriram/Confusion Study/Constraint |  [Thesis]()       |
| v4      | ACSP_PXAI_Upfront | Explanations delivered upfront    | Vedant B           | Winter 2023 | /ubc/cs/research/conati/CIspaceCSP/ACSP_Bahel_Sriram/PXAI Study/Software |  [Thesis]()        |
| v5      | ACSP_PXAI_Singular| Hint close button disabled        | Vedant B           | Winter 2023 | /ubc/cs/research/conati/CIspaceCSP/ACSP_Bahel_Sriram/PXAI Study/Software |    [Thesis]()      |
| v6      | ACSP_RP           | Explanation text reduced          | Max                | Spring 2024 | /ubc/cs/research/conati/CIspaceCSP/Max_RP |   [Report](./Max_Gilmour___COGS_402_Written_Report.pdf) |


## Code retrieval story 
When I (Vedant B) started working on the project, it wasn't easy to retrieve the code (as this GitHub repo did not exist). How did I get the code for v2 (a version before mine)? 

The code v2 codebase was stored in the CS server and was packed by a version control system called CVS. 
The folders are placed scattered at: /ubc/cs/research/conati/CIspaceCSP/CVS 

I unpacked the code by using the command:
cvs -d /ubc/cs/research/conati/CIspaceCSP/CVS checkout Constraint 

This method will still work (in case required). Sometimes if the "cvs" command doesn't work, contact help@cs. They will install the command for you to use it. 


## Current code retrieval protocols 

We do not use CVS anymore. For accessing the codebase of the above-listed version, follow their location in the CS server. Find the appropriate folder and edit/run the code as per the directions in the following sections. 

The code cannot be uploaded to GitHub because they are too large files to be pushed to GitHub. That is why they are stored in the CS server. 

## Accessing the CS servers 

To access the CS servers and retrieve the code, follow the guidelines:
- https://my.cs.ubc.ca/docs/connecting-department-unix-servers
- Using Xmanager makes it easy: https://my.cs.ubc.ca/docs/free-terminal-emulation-software-xmanager

## Project folder structure:

For each version, the following is how the codebase looks like: 

```
1. Constraint

    a. AIspace

        i. Adaptation 

            - (v1 updates were added here)

            - (v3,v4,v5 updates were added here)

                1. explanation 

                    - (v2 updates were added here)

                    - (v6 updates were added here)

        ii. Constraint 

            - (v0 was added here)

        iii. cspTools 
        
        iv. graphToolKit 

        v. XMLReader 

    b. lib
```


## Editing the code:

Following the above-described folder structure, based on your goal, you can make changes to the relevant files:
1. Changes to the hint box/explanation delivery method are done in files in the Adaptation folder. (e.g. v1,v3,v4,v5)
2. Changes to explanations are done in the explanation sub-folder in the Adaptation folder. (e.g. v6)


## Log-ing function
As you might have noted, when someone runs ACSP and closes it, ACSP creates a log file in the parent folder which includes all the steps they used to solve the problems, the functions they used from the applet, hints received, etc.  

If you add a new function to the applet, make sure you add a feature to log the usage of that function:
```AIspace.Constraint.Log.writeStamped("Sample Log");```

## How to compile the code:
Set Constraint main folder as CWD and run: 
javac -classpath ";./lib/batik/lib/*" AIspace/<Subfolder_name_goes_here>/*.java

Where the subfolder name will be all sub-folders containing java files. You have to run it one by one for all folders. In some cases, there are sub-sub folders. Make sure you include that path. Example: AIspace/Adaptation/explanation/*.java


## How to run the code: 
java -classpath ";./lib/batik/lib/*" AIspace/Adaptation/AdaptiveCSP_main_LocationBasedHide_M2_NoOLM_Explain2

## Which CSP problems did Samad, LV and Vedant use for their user study?
All of them used a set of 3 CSP problems: Sample 1, Sample 2 and Sample 3. These CSP problems are not built-in in the ACSP menu, they need to be opened from File>Open with. The problem files are located in the server at CIspaceCSP/XAI(Lea&Vanessa)/StudySoftware/Applet Problems.

