# Web
- Challenge Name : Mascot
- Difficulty :  Medium

## Challenge Description
Very gracious host!!


## Methodology
Deploying the challenge instance we are taken to a tic tac toe game website that looks like this

![TicTacToe](https://klsgit-wgcs.github.io/VishwaCTF-2023/writeups/web/assets/tic_tac_toe_ss.PNG)

It's a simple game of tic tac toe. Clicking View Source just revealed javascript that was powering the game. We did not find anything of interest there. For quite some time we could not make much of what to do with it.

So, we went the old school way. The one which every CS student resorts to when they can't find an efficient solution: brute-forcing. In this case [Directory Bruteforcing](https://www.makeuseof.com/what-is-directory-bursting/). Basically we scanned for any hidden folders/directories in the website.

An automated tool like [dirb](https://www.kali.org/tools/dirb/) makes our job easier. We
used a wordlist(available freely, only a google search away).It is basically a file that has a list of directory names.These names will be then checked in the website. We scanned the website and boom we hit a match.
Note the result with 200 status code in the image below:
![DIRB](https://klsgit-wgcs.github.io/VishwaCTF-2023/writeups/web/assets/dirb_ss.PNG)

It was a .git folder, you know the one that is created whenever you create repos with **git init**. It helps git keep track of files:

![Webpage](https://klsgit-wgcs.github.io/VishwaCTF-2023/writeups/web/assets/webpage_ss.PNG)

Now we started navigating the files/folders and on opening the config file, we find a link to a github repository; its the repo containing the code for the website.

![Config](https://klsgit-wgcs.github.io/VishwaCTF-2023/writeups/web/assets/config_ss.PNG)

Navigating to the repo, and opening the FLAGGGGG.md file we get our flag !!

> VishwaCTF{0ctOc@t_Ma5c0t}
