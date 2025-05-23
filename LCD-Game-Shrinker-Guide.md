## LCD-Game-Shrinker

LCD-Game-Shrinker is a program that shrinks MAME high-resolution artwork and graphics for portable devices running LCD-Game-Emulator. You can read more on the projects GitHub page: https://github.com/bzhxx/LCD-Game-Shrinker

When creating this guide I used the **FREE** [Oracle VM VirtualBox](https://www.virtualbox.org/) with [Ubuntu 20.0.4.2 LTS](https://ubuntu.com/#download) running under Windows 10. This is a great way to get a build environment set up quickly. 

Speaking of which, I've made a script called `lcdsetup.sh` that automates upto and including **Step 6** if you prefer which you can [download here](https://github.com/DNA64/game-and-watch-noob-installer#lcdsetupsh)

Before we continue it's important that you make sure Ubuntu is updated or you'll be installing old outdated packages and get errors.

Open a Terminal window and type, or copy and paste the following line, then press Enter.

    sudo apt-get update

Do the same for the following line as well.

    sudo apt-get upgrade

Now you should be up to date and can proceed with the following guide.

**STEP 1**

Before you can set up the build environment, you'll need to install `git` in order to clone the required repositories. If you're not sure whether you have git installed you can check by typing `git --version` in a Terminal window (It does not come pre-installed with Ubuntu 20.04.2 LTS). If it shows something like `git version 2.25.1` you can skip ahead to step 2 as it's already installed. If not, continue on with step 1...

Open a Terminal window and type, or copy and paste the following line, then press Enter.

    sudo apt install git

Enter your password when asked and press "Y" when prompted and move onto step 2.

    
**STEP 2**

For this example, I've created a folder on my desktop and named it `lcd-games`,  this is where all of our related files and folders are going to be placed. You can name yours whatever you like.
Open a Terminal window and navigate to the directory you just created.

**STEP 3**

*Now let's clone in the LCD-Game-Shrinker GitHub repo..*

In the Terminal window type or copy and paste the following line and press enter.

    git clone https://github.com/bzhxx/LCD-Game-Shrinker

**STEP 4**

Ubuntu comes with the required [lz4](https://github.com/lz4) and [Python3](https://www.python.org/downloads/) installed which means less work for you, at least Ubuntu 20.0.4.2 LTS does. That said, you'll still need to install **pip** in Ubuntu. So, once again open a Terminal window and type or copy and paste the following line, and press enter.

    sudo apt install python3-pip
    
Enter your password when asked and press "Y" when prompted. This will install pip and any required dependencies. 

**STEP 5**

Change into the LCD-Game-Shrinker directory by typing or copying and paste the following line into the Terminal window and press enter.

    cd LCD-Game-Shrinker
    
Once inside the LCD-Game-Shrinker directory copy and paste the following line into the Terminal window and press enter to install the required files to run the python scripts.

    python3 -m pip install -r requirements.txt
    

**STEP 6**

Finally, before we can use LCD-Game-Shrinker we need to install a free Vector Graphics Editor called **Inkscape**. You can download this via the Ubuntu Software app. It will likely be in the Editor's picks right at the top of the page when you launch the app. Just click on the Inkscape logo, then the Install button, and provide your password when prompted to install it. If you have issues later and get the error `returned non-zero exit status 1.` try re-installing Inkscape to solve the issue, this worked for someone who got this error. Inkscape should be the latest/stable build and at least version 1.1. If it's anything less your system isn't updated and you need to do that or install Inkscape manually.

    sudo add-apt-repository ppa:inkscape.dev/stable-1.1
    sudo apt-get update
    sudo apt install inkscape

**STEP 7**

Now we'll need a **ROM** and its **Artwork** to see if we have everything set up right. You'll have to source these MAME ROM files yourself by searching Google, as well as the separate art packs created by Hydef &/or DarthMarino. For best results use the MAME 0.229 romset. **Please do not ask others for them!**

Both the **zipped** ROM and the zipped Artwork must be placed into their respective folders. .mgw files will NOT work with LCD-Game-Shrinker! You MUST find the correct MAME 0.229 ROM set in .zip format! (Do not unpack!)

    lcd-games/LCD-Game-Shrinker/input/artwork/
    lcd-games/LCD-Game-Shrinker/input/rom/
    
**STEP 8**
Now that you have the ROM and the artwork in the correct folders, let's see if all that work paid off!

 From the Terminal window and within the `LCD-Game-Shrinker` directory run `python3 shrink_it.py` to process all files or `python3 shrink_it.py input/rom/gnw_mygame_zip` to process a single file. Make sure to change the roms filename ;P
 
If all went well you should see the word **COMPLETE** next to each games progress bar. Every game must have its properly named artwork or you'll get errors. The most common errors you'll encounter are due to missing artwork or wrong filenames. You can either rename the artwork as needed or edit the games `.py` script in `LCD-Game-Shrinker/custom/` should you encounter any of these errors. 

Finally copy all of the outputed `.gw` files (These are your Game & Watch ROM files) located in `LCD-Game-Shrinker/output/` to `game-and-watch-retro-go/roms/gw`. That's it! You're now ready to follow the [game-and-watch-retro-go readme](https://github.com/kbeckmann/game-and-watch-retro-go#readme) and flash the games to your G&W.

For any and all issues, feel free to join us on [Discord](https://discord.gg/rE2nHVAKvn) or on [r/GameAndWatchMods](https://www.reddit.com/r/GameAndWatchMods/)

Thanks to @Fuzion9#6018 from the Discord who followed this portion of the guide and confirmed it works with the same setup. A complete guide is in the works and will be made available soon.