# Red_Team_PIF_Distraction_Tool
Cyber Defense Techniques Red Team Distraction Tool 
Written by Oscar Dorantes

# Contains:
- playinface.yml
- playinfaces.yml
- spam_inventory.ini
- Spaminations Folder

# Questions:
- What is the goal of this tool? What purpose does it bring to the competitions?

The goal of this tool is to temporarily stop Blue Team from accessing Linux terminal lines. The ansipble scripts, playinface.yml and playinfaces.yml, will flood Blue’s terminal lines with ASCII art of Spongebob episodes. This is achieved by the following command that prints a long text file directly on the terminal line of a specified blue user:

“/usr/bin/cat {file path of spam text file}| tee /dev/{SSH terminal line of Blue User} > /dev/null”

The Tool will find the terminal lines of blue users by searching ip addresses. This aids Red Team as they will still have access to the Linux machines while the Blue users are distracted. 

- Did other tools influence your tool? If so, what are they? If not, what was your inspiration for the tool?

The inspiration for the tool was the command “cat /var/log/mail.log”. During the first competition, as Blue Team I had used this command instead of “tail /var/log/mail.log” which caused a loss of terminal access as the entire file of mail logs had to load. This gave me the idea to restrict terminal access of the Blue Team now that I am on the Red Team. Now not only would it be long files, I wanted it to be Spongebob themed, so making an animation was an obvious thought. The name for the tool derives from a meme tweet referencing the Spongebob episode, “Opposite Day”.

- What is the feasibility of another team member quickly learning to use or contribute to your tool? What makes it easy or difficult to learn?

All this tool needs is for an SSH key of the Red Control Box to be placed in the Linux Scored Virtual Machine’s authorized keys file. As soon as I or another member places this key, I can run the ansible script, playinface.yml, from the Red Control Box. This copies all the spam animation files into the target box, plays the initial animation on Blue terminal lines, and initiates a cron job that consistently keeps the SSH key within authorized keys. Whenever I choose, the playinfaces.yml will be used to play a specific animation to all machines I have available and Blue terminal lines. The only difficulties that can arrive is if the cronjob is disabled or if the IP addresses of Blue Team machines change.
