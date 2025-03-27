# Installing git pre-commit hook for juptyer notebooks

**Source** :  [*medium.com : version-control-on-jupyter-notebooks*](https://medium.com/somosfit/version-control-on-jupyter-notebooks-6b67a0cf12a3)


## Why should I configure that ?

Jupyter notebooks are very useful when it comes to Data Science. Unfortunatly these amazing tools come with a small weakness, when you're daring to commit and push one of these on a Git repository, it will make unnecessary long commits that unable you to see clearly the real changes that were made.

## How to configure the pre-commit hook ?
### Step-by-step guide

- Inside the .git/hooks hidden folder located in the Git local repository [[1]](#footnotes)

- Remove pre-commit.sample extension : 
    - ```mv pre-commit.sample pre-commit```
    - ```move pre-commit.sample pre-commit```<img src="https://static.vecteezy.com/system/resources/thumbnails/020/975/574/small/window-10-logo-window-10-icon-transparent-free-png.png" width="24" height="24"> 

- Then copy paste this script Inside pre-commit file :
    - 
    LINUX[[2]](#footnotes) :

        #!/bin/sh

        git diff --name-only -- '*.ipynb' > /tmp/changed_notebooks.txt
        git diff --cached --name-only -- '*.ipynb' >> /tmp/changed_notebooks.txt

        sort -u /tmp/changed_notebooks.txt > /tmp/unique_notebooks.txt

        while IFS= read -r notebook; do
            jupyter nbconvert --ClearOutputPreprocessor.enabled=True --inplace "$notebook"
        done < /tmp/unique_notebooks.txt

        rm -f /tmp/changed_notebooks.txt /tmp/unique_notebooks.txt

        git add .


    WINDOWS :
        
        #!/bin/bash
        git diff --name-only -- '.ipynb'
        git diff --cached --name-only -- '.ipynb' | sort -u | while read notebook; do
            jupyter nbconvert --ClearOutputPreprocessor.enabled=True --inplace "$notebook"
        done
        git add .


<br>
<br>

> **<span style="color:yellow">⚠ WARNING :</span>** \
> In order to preperly run jupyter nbconvert tool :
> Install : jupyter_contrib_nbextensions
>
> CONDA : \
> ```conda install -c conda-forge jupyter_contrib_nbextensions```
>
> PIP : \
> ```pip install jupyter_contrib_nbextensions```

<br>

## Footnotes 
    
[1]: Hidden folders are visible by typing the command \
```ls -la``` or ```dir /a```
<img src="https://static.vecteezy.com/system/resources/thumbnails/020/975/574/small/window-10-logo-window-10-icon-transparent-free-png.png" width="24" height="24">

[2]: Linux script hasn't been tested, let me know if it needs to be fixed.

<br>

> **Note :**
> This document hasn't been done with the help AI \
> Written by Quentin Barthélemy (BlueHowl)