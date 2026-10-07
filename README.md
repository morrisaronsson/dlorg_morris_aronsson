I started with creating the new repo, then cloning it into itself as well. 
Then I made the gitignore and copied the code Kokchun linked us. 
I created the dlorg bash script and used chmod +x to give myself permissions.

For this task I want the script to identify different files and then move them accordingly.

to find the files I used for, like we were taught in lesson 13 loop arrays. But instead of in the file, I set it to the Downloads directory. 
Then for now I just want to know it works so I make it echo that this exists. I didnt set a fail, I just want to know if the script can find it. 
I made one for txt and one for png. 
        
1 #!/usr/bin/env bash
  2
  3 for file in ~/Downloads/*.txt; do
  4     if [[ -f "$file" ]]; then
  5         echo "TXT file found: $(basename "$file")"
  6     fi
  7 done
  8
  9 for file in ~/Downloads/*.png; do
 10     if [[ -f "$file" ]]; then
 11         echo "TXT file found: $(basename "$file")"
 12     fi
 13 done
 14

-

It worked! The script found the files I had created and printed their names.
I used LLM to find the basename function, so that it only showed me the name of the file and not the whole path which was nice, even if it is only for making it easier for me to read. 
Now I need a function where it will move the files into folders depending on their types.

I added the function, writing for files in downloads that have specific suffixes then do move it to the specific folder I designate. Then I created the folders. I repeated this for every type in the lab, I will add more later, and for the others file I just left it empty so that any document without the specific types I´ve specified will be put in that directory. 

next I added the inotifywait function, using -m to monitor, -e to event either files moved to the folder or files created in the folder. Then I formated it to monitor ~/Downloads, using ~ will make it so it works on other users as well, and not only mine. If I had written /linton/Downloads/ that would not help the people hiring me to write this script. Now it will work on any individual users computer. 
Then I piped it | and added while read file do, so that when it reads a file, it does my script, which is to put it into the corresponding folder. I struggled with this for a while, until I asked LLM how my inotifywait line should be structured and it showed me done at the end. So I realized I needed two done at the end. A small mistake but I was staring at it for a while and this helped me get forwards. 
Now this works. I tested it, and anytime a file is created or moved into Downloads it is reshuffled.
Now I want to have the script create each of the directories and use -p so that they are only created if they don´t already exist. This in theory should recreate all the folders incase one of them is deleted by the user.  
This part was easy, I just added the -p then specified where I wanted the folder to be created and what name it should have. I also added two new directories for additional file types, one for zip and one for excel. Other files like mp4 and wav will still go into other. 
With this the base assignment is completed and I feel happy with how I´ve done this. Im sure it could be done much simpler, but this makes sense in my head right now. 
Now I will move on to the bonus tasks. 

2a) Tried this several times, using tmux with three screens, one with the script open in vim as I worked on it, one in my dlorg directory and one in my Downloads directory.
2b) I did this and it worked perfectly. 
2c) Also works perfectly, all the files are moved where they should be. 
2d) BONUS This turned out to be alot simpler than I had feared. I had been thinking on it for a while, wondering if I should use something like if or else to have it create a directory if there is no place for it to go. 
In the end I realized I already have the if built in, I can just add another line, so that every time a file is created of moved into Downloads the script first tries to create the correct directory, and doesnt do that with -p if there already is one. Then it moves the file there. Very simple, but I tried it and it works perfectly. 

2e) BONUS
