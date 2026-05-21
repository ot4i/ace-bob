# ace-bob
This repo provides step-by-step instructions for how to get up and running with IBM Bob within the ACE Toolkit: 
* Installing IBM Bob Shell
* Running IBM Bob Shell in ACE Toolkit (by creating a Terminal window shortcut and preferences)
* Configuring the ace-bob IBM Bob skill (This teaches IBM Bob the art of creating message flows and ESQL that follow best practices)

## Installing IBM Bob Shell
1. The ACE Toolkit runs on Windows, xLinux or MacOS. You can find detailed instructions for installing IBM Bob shell on each of these platforms [here](https://bob.ibm.com/docs/shell/getting-started/install-and-setup). Focussing on Windows, you can open Powershell and install IBM Bob Shell using this command:

   ```irm -Uri "https://bob.ibm.com/download/bobshell.ps1" | iex```

   ![image](https://github.ibm.com/user-attachments/assets/7ed76dd5-0000-48c2-bfe6-1a0b8a40ce5d)

## Running IBM Bob Shell in ACE Toolkit

1. Start the ACE Toolkit and from the Toolkit's Window menu choose Preferences. When the Preferences pop-up opens navigate to the section **Terminal > Local Terminal**

   ![image](https://github.ibm.com/user-attachments/assets/d5760607-5f6e-4571-b925-e3ce4d86dcf8)

2. Click the **Add** button and in the resulting dialog provide the following details:

   * Name = **IBM Bob Shell**
   * Path = **C:\Users\BenThompson\AppData\Roaming\npm\Bob.cmd**
   <br />
   <img src="https://github.ibm.com/user-attachments/assets/ac6839e1-0694-4e87-8be6-00c7ae7fd470" width="500"/>

   Click **Add**. Control will return back to the prior window showing preferences for Local Terminal. From the drop-down menu change the Initial Working Directory to be **Eclipse workspace**.

   ![image](https://github.ibm.com/user-attachments/assets/fd587be4-fce7-48ff-8687-81ce82e78eeb)

   Click **Apply and Close**.

3. Return to the Toolkit's Window menu and choose Preferences again. When the Preferences pop-up opens, use the filter to navigate to the section **Terminal**. From the Presets drop-down, select Eclipse Dark and click **Apply and Close**:
   
   ![image](https://github.ibm.com/user-attachments/assets/2b6a7aaf-fbd5-45a5-b270-afecb1821e0b)


4. Staying in the ACE Toolkit, from the top Toolbar click the **Terminal** shortcut (shown in the red box below):

   ![image](https://github.ibm.com/user-attachments/assets/a3653554-a19b-46b5-9f4d-5712a11aa1dc)

5. From the Launch Terminal pop-up, select IBM Bob Shell from the **Choose terminal** dropdown and click OK:

   <img src="https://github.ibm.com/user-attachments/assets/41743abe-7b28-49ca-920f-ea86513a2623" width="500"/>

6. An IBM Bob Shell Terminal will open. By default it will be located at the bottom of the screen:

   ![image](https://github.ibm.com/user-attachments/assets/cb2d514a-297c-4838-b07f-c3677ff2c376)

   Scroll down and on first use you will be presented with a dialog to accept the IBM Bob License:

   ![image](https://github.ibm.com/user-attachments/assets/73aec59c-0aac-4c77-9966-88299314bf47)

   Next you will be asked to trust the folder. Due to our earlier set-up we have chosen to launch IBM Bob's workspace to match the ACE Toolkit's Eclipse workspace directory. This makes it easier to use IBM Bob to interact with ACE Toolkit files in the local workspace.

   ![image](https://github.ibm.com/user-attachments/assets/ca2d404c-1181-4b20-959b-b7cada03f34a)

   If you've already been using IBM Bob then he may ask you to trust other directories as well. Once you have made these decisions IBM Bob Shell will be ready to respond to queries as shown below:

   ![image](https://github.ibm.com/user-attachments/assets/e5234b16-059f-436c-8ef9-65e9dddb8d00)

## Configuring the ace-bob IBM Bob skill

Skills are reusable instruction sets that teach IBM Bob about new workflows and specialized tasks. You can consider them as recipes that IBM Bob follows to complete specific types of work in a consistent, repeatable manner. When you activate a skill, IBM Bob receives the skill's instructions and gains access to any supporting files in the skill directory. Bob then follows these instructions to complete your task according to the defined workflow. Skills load once per conversation to avoid duplicate prompts. Bob automatically determines when to activate a skill based on your request and the skill's description.

1. When operating IBM Bob Shell in the ACE Toolkit, the prior configuration steps documented above have targetted your ACE Toolkit Eclipse workspace to be the IBM Bob project root directory. To make skills available for IBM Bob Shell in this context, navigate to this ACE Toolkit Eclipse workspace and if it does not already exist, create a folder called /.bob  Alternatively if you want to use IBM Bob across multiple ACE Toolkit workspaces, you may prefer to define ACE skills globally in your user's home directory (look for a directory called **~/.bob** - for example on Windows this will be at the disk location **C:\\Users\\YourUserName\\.bob**)

2. This Git repository contains the IBM Bob Skill definition for a skill called ace-bob that teaches IBM Bob the art of creating message flows and ESQL that follow best practices. You can git clone this skill to your global skills location as shown below:

![image](https://github.ibm.com/user-attachments/assets/06db7e47-3e90-4bac-a599-dc04c72afda7)


Bens To Do List for further future improvements in refining the skill:
* DONE: Tell the Skill where to locate the MessageFlow.xsd to avoid Bob guessing at the class names for nodes (often Bob will incorrectly guess at ComIbmHTTPInput for example)
* DONE: Teach Bob about the structure of Eclipse projects including the .project file and Application descriptor
* Tell Bob what to do about subflow division and the use of dependent libraries.
* Add more examples of flow development best practice ...
* Avoid multiple consecutive Compute nodes where possible (tree copying expensive)
* Do not use CARDINALITY statement inside loops
* Minimize the use of String manipulation functions
* Make ESQL code as efficient as possible by minimizing the number of statements
* Use the LASTMOVE or CARDINALITY statement when wanting to check for the existence of a field
* Declare REFERENCEs in order to minimize CPU spend on navigation of the logical tree (especially when dealing with heavily nested structures)
* Use the CREATE with PARSE statement in preference to serialising a copy of the logical tree
* Encourage the use of the Catch terminal at the start of the message flow in preference to the messy flow design of wiring every Failure terminal of individual nodes
* Add something about Compute mode and when to make the Compute node responsible for tree copying versus just editting isolated areas of the tree such as LocalEnvironment
* Give a list of ESQL functions that do NOT exist to avoid Bob making silly mistakes (eg CHECKSUM)
