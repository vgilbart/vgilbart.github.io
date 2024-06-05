---
layout: post
title: Retrieving untracked RStudio files... or saving one day of scripts
tags: [Rstudio]

---

## One day of script slipping through the fingertips

It’s 4:45 pm and I’m wrapping up my analysis for the day, when a dear biologist colleague comes to my desk and tells me “Valentine, something went wrong with RStudio”. Her RStudio window froze, and all she can do is force its closing. She can open a new second RStudio window that will work, but the first that opens up is always the same frozen one. 

She continues, “and inside the frozen window, there is this untracked file that I really want to retrieve, it has all the analysis that I did for the day, but I did not save it once”… AH

## Hide-and-seek with untracked RStudio files

Ok, as always, we will pray for stack overflow to give us an answer. So let’s search "rstudio unsaved files”. Our prayers have been answered quickly, as we easily found [another soul that was as lost as us 8 years ago](https://stackoverflow.com/questions/35223435/how-to-get-unsaved-script-tabs).

So here are some solutions if you are looking to retrieve untracked RStudio files under Mac.

- If you are not working within R projects ([although you are advised to](https://support.posit.co/hc/en-us/articles/200526207-Using-RStudio-Projects)), you should go under: 
```{bash}
/Users/${USERNAME}/.local/share/rstudio/sources/
```

- If you use R projects, go to the directory of your projects, and look for:
```{bash}
.Rproj.user/${SOMEALPHANUM}/sources/
```

If you have several folder with ${SOMEALPHANUM}, you can of course use `ls -l` in order to find the one with an adequate timestamp.

Then look for: 
```{bash}
session-${SOMENUMBERS}/${SOMEALPHANUM}-contents
``` 

If you have several sessions and/or contents, you can once again run `ls -l` in order to find the one with an adequate timestamp. To get the content of the file, just run:
```{bash}
cat ${SOMEALPHANUM}-contents
```

You can save in a more practical folder by running:
```{bash}
cat ${SOMEALPHANUM}-contents > ${SOMEBETTERPATH}
```

## RStudio always remembers

You can also get access to the latest R history under the following (no matter if you use R projects or not):
```{bash}
/Users/${USERNAME}/.local/share/rstudio/history_database
``` 

If you want to remove the prefix before every R command, run:
```{bash}
cat history_database | cut -d ':' -f2-
```

This last command will cut the content of the file in fields separated by the delimiter `:`, and ask for the 2nd field and more.

## Moral of the story

Saving scripts is just like drinking water, you should do it regularly throughout the day. 

For some reason, taking a peak at the session’s content under the Terminal unfroze her RStudio window. So in the end, all is well, she has her untracked file and her RStudio back!





