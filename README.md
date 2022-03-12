# unraid-new-files
Lists media added to Plex Server Nightly

##LIST OF ORIGINAL COMMANDS TRIED

tree /mnt/user/data/media > /mnt/remotes/FRACTAL_Plex/DATA LIST TREE/list.txt

tree /mnt/disk1 > "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/disk1.txt" && tree /mnt/disk2 > "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/disk2.txt" && tree /mnt/disk3 > "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/disk3.txt" && tree /mnt/disk4 > "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/disk4.txt" && tree /mnt/disk5 > "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/disk5.txt" && tree /mnt/disk6 > "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/disk6.txt" && tree /mnt/disk7 > "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/disk7.txt"

sort "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/disk1.txt" "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/disk2.txt" | uniq -u > "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/difference.txt"

##creates folder with todays date and outputs disk directories
cd "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE" && mkdir "$(date '+%Y-%m-%d')" && cd "$(date '+%Y-%m-%d')" && tree /mnt/disk1 > "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/disk1.txt" && tree /mnt/disk2 > "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/disk2.txt" && tree /mnt/disk3 > "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/disk3.txt" && tree /mnt/disk4 > "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/disk4.txt" && tree /mnt/disk5 > "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/disk5.txt" && tree /mnt/disk6 > "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/disk6.txt" && tree /mnt/disk7 > "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/disk7.txt"

##find diff between files yesterday and today
yest=$( date -d "yesterday 13:00 " '+%Y-%m-%d' )
sort "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/"$(date '+%Y-%m-%d')"/disk6.txt" "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/"$yest"/disk6.txt" | uniq -u > "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/difference.txt"

tree /mnt/disk1 > "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/"$(date '+%Y-%m-%d')"/disk1.txt"



______FINAL______________________

Make Date Folder and add disk files
mkdir "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/$(date '+%Y-%m-%d')" && cd "$_" && tree /mnt/disk1 > disk1.txt && tree /mnt/disk2 > disk2.txt && tree /mnt/disk3 > disk3.txt && tree /mnt/disk4 > disk4.txt && tree /mnt/disk5 > disk5.txt && tree /mnt/disk6 > disk6.txt && tree /mnt/disk7 > disk7.txt

----SHELL SCRIPTS----


##dailytreeoutput

mkdir "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/$(date '+%Y-%m-%d')" && cd "$_"

i=1

for i in {1..7}
do
   tree /mnt/disk$i > disk$i.txt
done


##compareoutput

mkdir "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/$(date '+%Y-%m-%d')/New Files" && cd "$_"

yest=$( date -d "yesterday 13:00 " '+%Y-%m-%d' )

i=1

for i in {1..7}
do
   sort "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/"$(date '+%Y-%m-%d')"/disk$i.txt" "/mnt/remotes/FRACTAL_Plex/DATA LIST TREE/"$yest"/disk$i.txt" | uniq -u > "disk$i.txt"
done

find . -type f -empty -print -delete
