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
Now I need a function where it will move the files into folders depending on their types.

