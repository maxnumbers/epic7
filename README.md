## Directions for Windows

###### Screenshots

* Start by taking all your screenshots. You will only be able to use this OCR file in conjunction with screenshots of each piece of gear you want in the optimizer. The screenshots are must be taken in an emulator and you must set the emulator resolution to **2200x1080** in order for the script to work. **Nox** and **LDPlayer** support this resolution and take compatible screenshots. We recently discovered that **MuMu** does not take screenshots compatible with this script. Sorry for the inconvenience.

* When taking the screenshots be sure to **tap** on each piece of gear before screenshotting. Do not hover/hold down your finger on each one, as the placement of the item box is different between tapping and holding. Once you've screenshotted all your gear, move on to the next step.

###### Python Setup

1. Download and install the 64 bit Anaconda python 3.7 distribution for windows - https://www.anaconda.com/products/individual

2. Download and Install the latest 64 bit version of Tesseract-OCR - https://github.com/UB-Mannheim/tesseract/wiki

    You should install it to the default directory unless you have a good reason not to.

3. Run Anaconda Navigator, which was installed as a part of the Anaconda distribution. Launch "Powershell Prompt". Copy and paste the two lines below, in order, hitting enter after each.

    ``pip install pytesseract``

    ``pip install opencv-python``

    You should see "Successfully installed [package name]" after each. Close the prompt when done.

###### Download and Edit the Script

4. Download the files in this repository. Scroll up to the top of this webpage and click the green "Code" button, then click "Download ZIP". Extract the files somewhere (I just extracted the folder within the ZIP file to the downloads folder)

5. Return to Anaconda Navigator. Launch JupyterLab. This will open a browser window. On the lefthand side, navigate to where you extracted the folder (in my case: ``Downloads/epic7-master``). Double click on "E7 Gear OCR.ipynb". This will open the code for the OCR script.

6. Uncomment (delete the # in front of) these lines since we're doing this in windows:

    ``pytesseract.pytesseract.tesseract_cmd = "C:/Program Files/Tesseract-OCR/tesseract"``

    ``TESSDATA_PREFIX = r"C:\Program Files\Tesseract-OCR"``

    Note: If you changed the install directory for tesseract, make sure the path to tesseract listed in these two lines is the same as the one you installed tesseract to!

7. Let's do a test run! Go to **Run > Run All Cells**. If you scroll down to the bottom of the window, you'll see a text progress indicator. When you see "JSON file finished!" you should see a new file on the lefthand side: "exported_gear.json". Double click that. If next to "items: []" it says "1 item" then the test run worked correctly. You can click the arrow to expand "items: []" if you want to see what the data looks like.

###### Copy Screenshots & Run

8. Delete the sample image in the screenshots folder (``epic7-master/screenshots``) that we just tested the script on.

9. Copy your 2200x1080 gear screenshots to ``epic7-master/screenshots`` from whereever you have them stored.

10. Go back to JupyterLab and do **Run > Run All Cells** again. This will overwrite the "exported_gear.json" file from earlier with one that has all your gear in it. Congratulations! You're done with this script.

###### Optimizer

* Make sure you have the latest version of the optimizer here: https://github.com/Zarroc2762/E7-Gear-Optimizer/releases. After running the optimizer, select "Import JSON from web optimizer (/u/HyrTheWinter)". Then click the "Import" button and browse to the folder that exported_gear.json is in and load it. You should see green text at the bottom saying "Succesfully imported 0 heroes and X items..." where x is the number of screenshots you took. Congratulations! You've imported your gear.

###### Sanity Checks

* I highly recommend doing some quick sanity checks of the imported gear to ensure the script didnt make any mistakes. The most common error with this OCR library is adding a '7' to the end of the recognized number. So a spd sub of 10 could be recorded as 107. Go to the inventory tab in the optimizer and click each stat column heading to sort the values. Just make sure that none of the highest values are crazy. Congratulations! You're ready to start optimizing your gear.

###### Using in the Future

* In the future when you want to do this all over again, all you need to do is to copy your new screenshots into the screenshots folder, open "E7 Gear OCR.ipynb" in JupyterLab, do Run > Run All Cells. This will give you your new json file.

* If you **don't** want to keep the heroes you previously added to the optimizer, then just import the json as above. If you **do** want to keep your heroes, I suggest that you first delete all the items in the optimizer (go to the Inventory tab, highlight all the items, click the "-" button). Then on the General tab click the "Append" button (instead of "Import") and load your new json. This will add your up to date gear into the optimizer while keeping your heroes.
