# 1. Planning & Design (Map the Maze Part 1)

**Purpose of CLI Work:** 
The Command Line Interface (CLI) allows users to navigate, create, organize, and share files without relying on interfaces. 

**File System Tree:**  
/  
└── Daniel  
    ├── Documents  
    │   └── dannyshoeshopping.jpg
    ├── Music  
    │   └── song01.mp3 
    └── Photos

**Pseudocode for CLI Navigation & File Manipulation:**  
1. Start at home directory (cd ~).
2. Create new folder "Practice" (mkdir Practice).
3. Inside "Practice", create subfolders: Docs, Photos, Music.
4. Create a text file "notes.txt" inside Docs (touch notes.txt).
5. Move "notes.txt" into Music folder (mv notes.txt Music/).
6. Verify structure with ls and tree.
7. Record the full path of Music folder (pwd).

**Objectives for Activities:**  
- Map the Maze (Part 1): Learn file system structures and how to represent them as diagrams.
- Map the Maze (Part 2): Practice core commands for navigating and creating files in Ubuntu.
- House Sitting Adventure: Test CLI knowledge in a simulated scenario with challenges, hidden files, and troubleshooting.

**Reflection on Planning:**  
Creating both a diagram and pseudocode provided a clear roadmap before using actual commands. Planning ensured that I understood the logic of how folders and files connect, making later execution more accurate and efficient

---

# 2. Technical Development (Map the Maze Part 2)

**Tools Used:** 
- Ubuntu VM (guest OS)
- Terminal (CLI environment)
- Hostshare (for file transfer between Mac and VM)

**Commands & Outputs:**  
pwd
<br> /home/ubuntu

cd Documents
pwd
<br> /home/ubuntu/Documents

mkdir MazeGame
cd MazeGame
ls
<br> (empty)

touch clue1.txt clue2.txt clue3.txt
ls
<br> clue1.txt clue2.txt clue3.txt

nano clue1.txt
<br> Edited text: "Hello my name is Daniel!"

cp clue1.txt ~/hostshare/
ls ~/hostshare
<br> clue1.txt now visible in Mac host


**Result:**  
All required commands were executed correctly, with organized documentation of outputs and reasoning

---

# 3. Testing & Evaluation (House Sitting Adventure)

**Example Test Cases:** 
### Test 1 – Verify Created Files
cd kitchen
ls
<br> apple banana cereal crackers donut milk orange


✅ Confirmed all files appeared as expected.

### Test 2 – Remove Files and Confirm Deletion
rm orange milk
ls
<br> apple banana cereal crackers donut


✅ Files successfully removed.

### Test 3 – Reveal Hidden Items
ls -a
<br> . .. .rotten_bananas apple banana cereal crackers donut
rm .rotten_bananas
ls -a
<br> . ..


✅ Hidden file detected and deleted.

### Test 4 – Copying and Editing Files
cd main_entrance
touch note.txt
nano note.txt
<br> "Thanks for trusting me to watch your house!"
ls
<br> instructions.txt note.txt


✅ Verified file creation and editing.

## Bug / Correction Example

At one point, I tried rm orange, milk (with a comma), which failed. Corrected to rm orange milk (space-separated arguments).

Result:
Multiple tests confirmed the accuracy of commands. Before-and-after outputs proved changes, and errors were acknowledged and fixed

---

# 4. Reflection & Professionalism
The portfolio demonstrates how file systems function as hierarchical structures and how the CLI can be used to manage them effectively. Unlike a graphical interface, the CLI uses commands but is more efficient. The activities provided hands-on practice with creating, moving, deleting, and revealing files, helping establish key concepts of file system navigation.

Common challenges included syntax errors and remembering operations such as rm -r. However, correcting these mistakes contributed to a deeper understanding of the commands. Overall, the experience strengthened technical accuracy, problem-solving skills, and professional documentation practices.

---
