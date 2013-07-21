# Resume Generator (Work in progress)

[forked](https://github.com/smt/resume)
## Intro
Markdown is a simple way to write and update documents with presentational formatting like resumes.  To be able to control these documents, you need to learn how to write markdown, and you need a way to convert it into useful formats like pdf, docx, and html.

Writing your resume in markdown and using the process described below lets you write it once, and output .docx, .pdf, HTML, and other formats.  So you can update your resume and send a docx to your recruiters, post an HTML version to your website, and put markdown version on your GitHub.

## Learn markdown (It's not that hard)

[Read a little about it](http://en.wikipedia.org/wiki/Markdown)

[Play around with how the formatting works.](http://dillinger.io/)

[Use a cheat sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

Great! Now you can write markdown.

## Setup your computer to output useful formats

The following steps will get your Mac setup so you can convert a markdown document into a variety of formats like pdf, docx, and html.  

At the end of this setup, generating your output files will be as easy as typeing "rake all" . 

Many of the instructions are elementary because it should be as easy as possible for developers of all levels to be able utilize this process.

This setup is for Mac.  PC will require a variation of this setup.

- Install [Xcode](https://developer.apple.com/xcode/).  You may be required to register a free developer account with Apple.  Also when you open Xcode for the first time, you need to install sytem components.  *This is required for installing Command Line Tools*.

- In Xcode, go to preferences > Downloads: Install Command Line Tools.  *This is required for installing Haskell*.

- Go to [github.com](http://www.github.com) and register if you don't have a login yet.

- Install [GitHub](http://mac.github.com/).  *This is advised for downloading necessary files.*

- In the GitHub application, got to Preferences > Advanced > Install Command Line Tools *This is advised for uploading your files to the GitHub servers.*

- Install [MacTex](http://mirror.ctan.org/systems/mac/mactex/mactex-basic.pkg). *This is required for generating PDFs.*

- Install [Pandoc](https://code.google.com/p/pandoc/downloads/detail?name=pandoc-1.11.1.dmg&can=2&q=) *This is the engine for generating various files.*

- In your Mac, in Application > Utilities, find the "Terminal" application.  Drag it to your dock. *This is advised for ease of workflow.*

- Open the Terminal application
- 
- Enter the following commands and hit return for each of the following in Terminal.  Some of these may take a while to finish.  Wait for each to finish before typing the next.  Enter your password when prompted.  *This is necessary for installing things to generate PDFS.*

 - ````sudo chown -R `whoami` /usr/local/texlive````
 - ````tlmgr update --self````
 - ````tlmgr install ucs````
 - ````tlmgr install etoolbox````
 - *if you don't already have Ruby installed enter (this takes a while) (It will ask for password some point in install process):*   
 ````\curl -L https://get.rvm.io | bash -s stable --ruby````
 - *if you don't already have Homebrew installed enter:*  
````ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"```` ... when that's done run: ````brew doctor````
 - *if you don't already have Haskell installed enter:*  (this takes a while) (really really long time)
````brew install haskell-platform```` ... then run ````cabal update````
 - ````cabal install pandoc````

- ~~Now we need to edit your Path file.  Enter this Terminal command, and it should open a document in text edit called ".bash_profile".~~

 - ~~Add a line to the end of this file of ````export PATH="$HOME/.cabal/bin:$PATH"````.~~

 - ~~The ".bash_profile" file should look like this (The first few lines may be different, and leave them how you found them.  The last line is what you added.)~~

   ~~[[ -s "$whatever/.whatever/whatever/whatever" ]] && whatever "$whatever/.whatever/whatever/whatever" # whatever RVM whatever whatever whatever whatever *whatever whatever whatever* ~~
  ~~export PATH="$HOME/.cabal/bin:$PATH"~~

 - ~~Save this file and close it.~~

- ~~Restart the computer. *This is possibly necessary to make this change take full effect on your computer.*~~
- Your computer should now be prepared to process a markdown file into various formats like pdf,docx, and HTML.

## Download the project files from GitHub

- Go to [https://github.com/defualt/resume](github.com/defualt/resume).  Log in to GitHub if you are not already.
- On that link's page, click "Fork"
- Refresh the page until it no longer says its processing.
- When the forking process is done, click the "Clone in Desktop" button.  This should open your GitHub desktop application and ask you to choose a location on your harddrive.  Choose where you want to place folder containing the files you will be using.  It should begin downloading.
- When the GitHub download is done, look in your Resume project folder.  It should be full of files.

## Test the process of outputting various file formats
- Find the "resume.markdown" file in the Resume project folder.  This is where you will write your resume in the markdown language you learned at the beginning of this process.
- For now, replace the text in here with something simple like this:

````
 # Here's a big header
 ## Smaller
 ###Even smaller
````

- Now we're going to process this into docx, pdf, HTML and more.
- Drag the Resume folder (the one containing all the files for the project) into the Terminal application.
- In the terminal window that opens, type  
````rake all````
- You should see it processing.
- When it completes, look in your Resume project folder, in the "output" subfolder, you will find the files you just generated.
- Now make any change you want to the resume.markdown file again.
- In the terminal, type, ````rake all```` again.
- In the output folder, find that the old files were replaced with new files that show the changes.

## Put the pieces together

- Now fill out the resume.markdown file with your real resume.  
- Output your various files like HTML, docx, and PDF by typing ````rake all````

## Update your resume in the future
- Whenever you return to work on your resume file in the future, just drag the Resume project folder to the terminal, and each time you want to output the files after you make changes, enter ````rake all```` 

##Coming sooner or later
- How to format templates for PDF, DOCX, HTML.
- How to upload and sync with Github.
