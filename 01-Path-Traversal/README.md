# Path Traversal (Directory Traversal) - Simple Case

## What is Path Traversal? 
Imagine you work in a massive office building. Your desk is in Room 101. Your boss tells you, "You can only look at the files inside Room 101."

But there is a hallway. If you walk out of Room 101, go back one door (`../`), go back another door (`../`), and go back one more door (`../`), you suddenly find yourself in the CEO's office! You are now reading files you were never supposed to see.

**Path Traversal** is exactly that. It is tricking the web server into walking backward out of its designated folder to read secret files on the computer.

---

## Breaking Down the Attack

**1. The Normal Situation:**
The website has an image: `<img src="/loadImage?filename=218.png">`. 
The server takes the filename `218.png`, and adds it to the folder where images are kept: `/var/www/images/`. So it reads `/var/www/images/218.png`. Normal.

**2. The Attack:**
The hacker changes `218.png` to `../../../etc/passwd`. 
So the server reads: `/var/www/images/../../../etc/passwd`

**3. The Magic Trick (`../`)**
In Linux (and Windows), the symbols `../` mean **"go up one folder."**
*   Start at `/var/www/images/`
*   `../` takes you to `/var/www/`
*   `../` takes you to `/var/`
*   `../` takes you to `/` (the very top of the computer, the root).
*   Then it reads `etc/passwd`.

**4. What is `/etc/passwd`?**
On Linux, `/etc/passwd` is a file that lists every user on the computer. Hackers love to steal this file because it tells them the usernames (like `root`, `admin`, `peter`, `carlos`).

**5. Windows Version**
Windows doesn't use `/etc/passwd`. Instead, hackers use the same `../` trick to read `C:\Windows\win.ini` (a sensitive Windows configuration file). On Windows, you can use `../` or `..\`.

---

## Why is it a vulnerability?
The web application thought it was safe because it put all images in the `/var/www/images/` folder. But it trusted the user's input. It didn't check if the user typed `../../`. So the hacker used the `../` to break out of the image folder and read the entire server.

**The One Thing to Remember:**
Path Traversal = Tricking the server into walking backward (`../`) to read hidden files.
