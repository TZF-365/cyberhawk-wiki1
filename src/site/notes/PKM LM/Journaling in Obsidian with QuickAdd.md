---
{"dg-publish":true,"permalink":"/pkm-lm/journaling-in-obsidian-with-quick-add/"}
---


Obsidian is a great place to do your digital journaling, thanks to the daily notes core plugin. But with the addition of the quick add community plugin, you can quickly capture journal entries into specific categories using the command palette. 

*(If you're looking for the Daily Questions part of my journaling workflow, check out [[PKM LM/Daily Questions in Obsidian\|Daily Questions in Obsidian]].)*

## Setting Up the Daily Notes

First, we need to make sure that *Daily Notes* core plugin is in fact toggled on. To access the Settings, click on the gear icon in the lower left.

![](https://thesweetsetup.com/wp-content/uploads/2021/09/quickadd1.jpg)

Next, click on *Core Plugins* and make sure that *Daily Notes* plugin is toggled on. 

![](https://thesweetsetup.com/wp-content/uploads/2021/09/quickadd2.jpg)

Next, go to the sidebar of the settings and scroll down to the *Daily Notes* section. Here you can configure the new file location which tells Obsidian where to store the new Daily Notes files and the location of your template file. 

![](https://thesweetsetup.com/wp-content/uploads/2021/09/quickadd3.jpg)

I have this set to capture new Daily Notes to a *Daily Notes* folder using my *Journaling template* inside of my *Templates* directory. This will take the contents of that file and insert it into the new Daily Note when I create it. So let's close our settings, and take a look at our journaling template. 

![](https://thesweetsetup.com/wp-content/uploads/2021/09/quickadd4.jpg)

I have three different sections here:

- one for learnings, 
- one for journal entries, and 
- one for gratitude.  

So when I click on the new Daily Notes button over here on the left, those three sections will automatically be added to today's Daily Note. 

![](https://thesweetsetup.com/wp-content/uploads/2021/09/quickadd5.jpg)

Once we have our Daily Notes configured, we're ready to set up QuickAdd plugin.

## Setting Up the QuickAdd Plugin

Go back to the Settings, select *Community plugins*, and click Browse. 

![](https://thesweetsetup.com/wp-content/uploads/2021/09/quickadd6.jpg)

Next, search for QuickAdd.

![](https://thesweetsetup.com/wp-content/uploads/2021/09/quickadd7.jpg)

Click *Install*, then click *Enable*.

Once we've installed and enabled the plug in, go over to the left and scroll down to the *QuickAdd* settings. QuickAdd can do a lot of different things, but we're going to be using it to quickly capture text that we want to add to specific sections in our journal. So let's create a section here for *Learnings*. And instead of a template, we're going to select *Capture*, then click *Add choice*. 

![](https://thesweetsetup.com/wp-content/uploads/2021/09/quickadd8.jpg)

Now click on the gear icon for the Learnings action that we just created and configure the settings. 

![](https://thesweetsetup.com/wp-content/uploads/2021/09/quickadd9.jpg)

First we can set what file we want to capture this information to we can choose either the active file or a specific file. Capturing to a specific file allows us to capture to the file from anywhere in Obsidian, so that's what we'll use (`Daily Notes/{{DATE:gggg-MM-DD}}.md`)

This selects the Daily Notes folder, uses a date token to insert today's date, and adds a `.md` for the file extension. 

![](https://thesweetsetup.com/wp-content/uploads/2021/09/quickadd10.jpg)

This will translate to the same date format we use for our Daily Note. 

Next,  scroll down and select *Insert after* and add `## Learnings` to insert our added text after the second level header for *Learnings*. 

![](https://thesweetsetup.com/wp-content/uploads/2021/09/quickadd11.jpg)

Next, we need to put in the value for what we want to capture. So toggle on *Capture format* and then use `- {{VALUE}} #journal/learnings \n`.

![](https://thesweetsetup.com/wp-content/uploads/2021/09/quickadd12.jpg)

This will create a bullet point with the captured text, then automatically add the tag *journal/learnings* and then create a new line. 

We can repeat this process for the other sections, resulting in 3 different QuickAdd entries. And we can enable these directly from the *Command Palette* (without having to launch QuickAdd first) by clicking on the lightning bolt icons. next to the choices we want to enable.

![](https://thesweetsetup.com/wp-content/uploads/2021/09/quickadd13.jpg)

## Using QuickAdd

Now from anywhere in Obsidian, we can hit `Command - P` to invoke the Command Palette, search for *QuickAdd*, and to select the one that we want to use (i.e. *Entry*)

![](https://thesweetsetup.com/wp-content/uploads/2021/09/quickadd14.jpg)

Then we just type out our text, hit *Enter*, and the text that we just typed gets pasted into the appropriate section in our Daily Note. 

![](https://thesweetsetup.com/wp-content/uploads/2021/09/quickadd15.jpg)

QuickAdd also works on the mobile version of Obsidian, which is great way to journal from my iPhone at the end of the day.