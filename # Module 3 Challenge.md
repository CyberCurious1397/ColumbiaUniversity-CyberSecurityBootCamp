Terminal and Bash

# **A High-Stakes Investigation**

You have just been hired by Lucky Duck Casino as a security analyst.

- Lucky Duck has lost a significant amount of money on the roulette tables over the last month.
- The largest losses occurred on March 10, 12, and 15.
- Your manager believes there is a player working with a Lucky Duck dealer to steal money at the roulette tables.
- The casino has a large database containing data on wins and losses, player analysis, and dealer schedules.
- You are tasked with navigating, modifying, and analyzing these data files to gather evidence on the rogue player and dealer.
- You will prepare several evidence files to assist the prosecution.
- You must work quickly, as Lucky Duck can't afford any more losses.

Lucky Duck Casino has provided you with the following files:

- [Roulette Player Data: Week of March 10Links to an external site.](https://drive.google.com/file/d/1XMPmsNf6Ft80AeaunBJlblF5TWI58jOT/view?usp=sharing)
- [Employee Dealer Schedule: Week of March 10Links to an external site.](https://drive.google.com/file/d/1sjdMeQccirtBNVh1jKS0s7j8ICvEtQEL/view?usp=sharing)

**NOTE**

The instructions ask you to set up the files using a wget command, but the files are also provided in compressed zip format if the command does not work.

# **Lab Environment**

- You will use your local Vagrant virtual machine for today's activities. Use the following credentials to access the machine:
  - Username: sysadmin
  - Password: cybersecurity

# **Instructions**

Use your command-line skills to uncover the identities of the rogue casino player and dealer colluding to scam Lucky Duck out of thousands of dollars.

After your investigation, you will provide a summary of your findings to the casino.

# **Step 1: Investigation Preparation**

Your first task is to set up directories to prepare for your investigation.

1. Begin by making a single directory titled Lucky\_Duck\_Investigations.
2. In this directory, create a directory for this specific investigation titled Roulette\_Loss\_Investigation.
3. In Roulette\_Loss\_Investigation, create the following directories:
  - Player\_Analysis to investigate the casino player.
  - Dealer\_Analysis to investigate the dealers.
  - Player\_Dealer\_Correlation to summarize your findings about the collusion.
4. Create empty files called Notes\_\<Directory Name\>.txt under each subdirectory to store investigation notes.
  - For example: Notes\_Player\_Analysis.txt

# **Step 2: Gathering Evidence**

Your next task is to move evidence from the specific days on which Lucky Duck experienced heavy losses at the roulette tables.

1. Navigate to the directory where you created the Lucky\_Duck\_Investigations directory and run the following command to set up the evidence files:
  - wget "https://drive.google.com/uc?id=1ZLY\_fuFu3wz7tOlxf-GUrnvp3htuGKSa" -O 3-HW-setup-evidence && chmod +x ./3-HW-setup-evidence && ./3-HW-setup-evidence

After running this command, your current directory should have the following subdirectories:

- Dealer\_Schedules\_0310: Contains the dealer schedules.
- Lucky\_Duck\_Investigations: Contains the investigation directories and notes files you created.
- Roulette\_Player\_WinLoss\_0310: Contains the data for player wins and losses.
- The Dealer\_Schedules\_0310 and Roulette\_Player\_WinLoss\_0310 directories contain the dealer schedules and win/loss player data from the roulette tables during the week of March 10.
- Since the losses occurred on March 10, 12, and 15, move the schedules for those days into the directory Dealer\_Analysis.
- Move the files for those days into the directory Player\_Analysis.

# **Step 3: Correlating the Evidence**
Your next task is to correlate the large losses from the roulette tables with the dealer schedule. This will help you determine which dealer and player are colluding to steal money from Lucky Duck. **NOTE** Winnings for Lucky Duck Casino are indicated with a positive number and losses are indicated with a negative number.Complete the player analysis with the following steps:
1. Navigate to the Player\_Analysis directory.
2. Use grep to isolate all of the losses that occurred on March 10, 12, and 15.
3. Place those results in a file called Roulette\_Losses.txt.
4. Preview the file Roulette\_Losses.txt and analyze the data.
  - Record the following in the Notes\_Player\_Analysis.txt file:
    - The times the losses occurred on each day.
    - Whether there is a certain player who was playing during each of those times.
    - The total count of times this player was playing. \>  **Hint:**  Use the wc command to find this value.
Complete the dealer analysis with the following steps:
1. Navigate to the Dealer\_Analysis directory.
2. This file contains the dealer schedules for the various Lucky Duck casino games: Blackjack, Roulette, and Texas Hold 'Em.
  - Preview the schedule to view the format and to understand how the data is separated.
3. Using your findings from the player analysis, create a separate script to look at each day and time that you determined losses occurred. Use awk, pipes, and grep to isolate out the following four fields:
  - Time
  - a.m./p.m.
  - First name of roulette dealer
  - Last name of roulette dealer
For example, if a loss occurred on March 10 at 2 p.m., you would write one script to find the roulette dealer who was working at that specific day and time. **HINT**
1. Run all of the scripts and append those results to a file called Dealers\_working\_during\_losses.txt.
2. Preview your file Dealers\_working\_during\_losses.txt, and analyze the data.
  - Record the following in the Notes\_Dealer\_Analysis.txt file:
    - The primary dealer working at the times where losses occurred.
    - How many times the dealer worked when major losses occurred.

  1. Complete the player/employee correlation.

- In the notes file of the Player\_Dealer\_Correlation directory, add a summary of your findings noting the player and dealer you believe are colluding to scam Lucky Duck.
- Make sure to document your specific reasons for this finding.

# **Step 4: Scripting Your Tasks**
You manager is impressed with the work you have done so far on the investigation.They've now tasked you with building a shell script that can easily analyze future employee schedules. They will use this script to determine which employee was working at a given time in the case of future losses.Complete the following tasks:
1. Remain in the Dealer\_Analysis directory. Develop a shell script called roulette\_dealer\_finder\_by\_time.sh that can analyze the employee schedule to easily find the roulette dealer at a specific time.
**HINT**

- Design the shell script to accept the following two arguments:
  - Date (four digits)
  - Time
**NOTE** The argument should be able to accept a.m. or p.m.
1. Test your script on the schedules to confirm that it outputs the correct dealer at the time specified.

# **Optional Additional Challenge**

- In case there is future fraud on other Lucky Duck games, create a shell script called roulette\_dealer\_finder\_by\_time\_and\_game.sh that has the following three arguments:
  - Specific time
  - Specific date
  - Casino game being played
**HINT**
# **Submission Guidelines**

- Move the following to the Player\_Dealer\_Correlation directory:
  - All note files
  - The following evidence files:
  - Roulette\_Losses
  - Dealers\_working\_during\_losses
  - Your shell script(s)
- Compress the Player\_Dealer\_Correlation folder to a zip file, and submit it through Canvas.
