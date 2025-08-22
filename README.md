# uCTF-2025
These are write-ups of the problems I personally solved with help from my team (Bitflip).
Huge thanks and credit to the rest of my team and our very supportive adviser, we may not have gotten top 5 but I'm proud we were able to get max points.
## Software/OS used
- Kali virtualbox VM
- Native windows 11 Ghidra
# Ancient File
We were given file to find a flag in.
Doing the usual steps when given a file, I first cat the file and piped it to head to see any file signatures or artifacts at the front of the file.
``` cat 1cba1c83e54e6c830bf3e5c1853b5dc4 | head ```
There weren't any notable text found aside from a 'word.txt' found at the 2nd line of the output.
## Further investigation
As I'm not familiar with what type of file it is exactly, I decided to run the command file on the file to see what exact filetype it is.
``` file 1cba1c83e54e6c830bf3e5c1853b5dc4 ```
It gave an output of it being an LHa file type. A simple google search as to how to open or extract files from it lead to the command lhasa.
We only need these commands to verify its contents and extract it.
```
lha -l 1cba1c83e54e6c830bf3e5c1853b5dc4
lha -x 1cba1c83e54e6c830bf3e5c1853b5dc4
```
## Extracting the flag
Now that we have words.txt, we just need to cat it and see if it does contain the flag.
It seems to be a list of words (color me surprised), a simple grep command to output to a separate file should allow us to get the flag thanks to us knowing the flag format.
``` cat words.txt | grep uCTF > flag ```
Just cat the flag file and we should have it
``` cat flag```

# In The Property
Another file was given to find a flag.
Like the usual we cat and pipe the file to head for any familiar strings or file signatures.
``` cat bd3688e970d227c7045afde973cbe1e0 | head ```
We can see that there is a PNG signature at the top of the file
## Viewing the png
Clearly the flag wouldn't be as easy as checking the image, but for the sake of being thorough I checked it but it had nothing visually.
Next step when checking image files is using ```zsteg``` or ```exiftool```. Zsteg didn't show any results but exiftool showed us a flag in the metadata of the image.
