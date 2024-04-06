# Renton Technical College CSI-248

<br />

![Alt text](Images/logo.jpg)

This repository is a part of CSI-248 at Renton Technical College.

## Guided Activity 3 - Project Creation

We will complete this assignment together in class. If you are having problems with this assignment please refer to the lecture recording.

1. Clone the repository to your local machine. (Do not use OneDrive for assignments in this course!)
2. Make note of the folder where you cloned the repository.
3. After you have cloned this repository navigate to your local repository using the cd command.
4. Open the repository in Visual Studio Code by typing `code .`
5. Open the terminal in Visual Studio Code by hitting ctrl + \` or cmd + \` on mac.
6. Create a directory for your screenshots with `mkdir Screenshots`
   
   ![Alt text](<Images/GA3 - Project Creation - Step 6.png>)

8. Create a new React Project called timer using Vite `npm create vite timer`
   
   ![Alt text](<Images/GA3 - Project Creation - Step 7.png>)

9. Type `cd timer` to navigate into the timer folder and run `npm install`
10. This will install all of the dependencies for the project.
11. We are also going to add bootstrap to this project. Run `npm install bootstrap`
    
    ![Alt text](<Images/GA3 - Project Creation - Step 10.png>)

12. type `npm run dev`to launch the react app and take a screenshot. Save in the screenshots dir.
    
    ![Alt text](<Images/GA3 - Project Creation - Step 11.png>)

13. Once the development server is running in your terminal you will need another terminal to create commits.
14. Click the + icon in the corner of your terminal to launch another instance of the terminal.
    
    ![Alt text](<Images/GA3 - Project Creation - Step 13.png>)

15. You will now have two terminals running, one with the Node development server and another where you can run git commands.
16. Click the new terminal and run the following:

    ![Alt text](<Images/GA3 - Project Creation - Step 15.png>)

17. Type `git add .` to stage all updated files.
    
    ![Alt text](<Images/GA3 - Project Creation - Step 16.png>)

18. Type `git status` to see all files ready for commit.
    
    ![Alt text](<Images/GA3 - Project Creation - Step 17.png>)

19. Type `git commit -m "project created"`
20. Type `git push`

## Guided Activity 3 - Creating the Timer App

1. First let's delete the unnecessary template files that Vite provides.
2. Vite includes a lot of built-in css styling for the template page that we are not going to use.
3. In the src folder open App.css and delete everything inside of it.
   
   ![Alt text](<Images/GA3 - Creating the Timer App - Step 3.png>)

5. Do the same for index.css
   
   ![Alt text](<Images/GA3 - Creating the Timer App - Step 4.png>)

6. If you would like to do styling at a later time you can add to these files.

7. Inside of App.jsx delete all of the code and replace it with the following:
   
   ![Alt text](<Images/GA3 - Creating the Timer App - Step 6.png>)

8. Take a screenshot of the output and save in the screenshots directory. Your app should now look like this:
   
   ![Alt text](<Images/GA3 - Creating the Timer App - Step 7 cropped.png>)

9. First lets add a component with a couple of buttons. These will be used to set the duration of the timer.
10. Open Terminal and cd into the the src folder. Type `mkdir Components` to create a folder named Components.
    
   ![Alt text](<Images/GA3 - Creating the Timer App - Step 9.png>)

11. In the Components folder, make a file called TimerInput.jsx. This is the component where the user will set the duration of the timer in minutes.

    ![Alt text](<Images/GA3 - Creating the Timer App - Step 10.png>)

12. Type the following code into TimerInput.jsx:

    ![Alt text](<Images/GA3 - Creating the Timer App - Step 11.png>)

13. In the Components folder, create another file called Timer.jsx. This is the component where the actual countdown will occur.

   ![Alt text](<Images/GA3 - Creating the timer - dylan.png>)

14. Modify App.jsx to import the TimerInput and the Timer Component:

    ![Alt text](<Images/GA3 - Creating the Timer App - Step 12 (Josh).png>)

15. We now have a very interesting scenario. The Child components (TimerInput and Timer) both need access to the minutes variable.
16. When you have a variable that needs to be accessed by multiple children, you should store that variable in a common parent (App.jsx)
17. App.jsx will track the number of minutes.
18. A callback function will need to be sent to the TimerInput via props so that it can modify the minutes tracked in App.jsx
19. The number of minutes will need to be send to the timer via props so it know how long to run for.
20. Props can only pass information from parent to child, so how can we pass information from child (TimerInput) to parent (App.jsx)?
21. We will have to use a callback functions.
22. First lets create a minutes variable inn App.jsx that is tracked by state.
    
    ![Alt text](<Images/GA3 - Creating the Timer App - Step 20 (Josh).png>)

24. Import the useState.
    
    ![Alt text](<Images/GA3 - Creating the Timer App - Step 21 (Josh).png>)

25. Now we need to pass the minutes variable and the setMinutes function down to the TimerInput component.
    
    ![Alt text](<Images/GA3 - Creating the Timer App - Step 22.png>)

26. Inside of TimerInput.jsx lets take in minutes and setMinutes as props and use them in the component.
    
    ![Alt text](<Images/GA3 - Creating the Timer App - Step 23.png>)

27. Next, lets create 2 clickHandler functions: handleAddMinute and handleSubtractMinute. They will fire when the buttons are clicked and call the the provided setMinutes function.
    
    ![Alt text](<Images/GA3 - Creating the Timer App - Step 24.png>)

28. Notice that these functions do not directly change the minutes variable, instead they provide a function to be called that will change them.

29. Now lets add the functions to the buttons.
    
    ![Alt text](<Images/GA3 - Creating the Timer App - Step 27 (Josh).png>)

30. At this point your buttons should be functioning and updating the number of minutes. Take a screenshot and add to the screenshots folder.

    ![Alt text](<Images/GA3 - Creating the Timer App - Step 27.gif>)

31. Our TimerInput Component is complete. Let's create a commit and push to git
32. `git add .`
33. `git commit -m "TimerInput Component Working"`
34. `git push`

## Guided Activity 3 - Creating the Countdown Effect

1. Let's work on the Timer Component.
2. This component is going to take in a number of minutes from App.jsx and start a countdown based on those minutes.
3. Inside of the Timer Component we are interested in the number of seconds, so we will track those with state.
4. Additionally we will need to set a timer that will reduce the number of seconds every 1000ms.
5. Add the following code at the top of Timer.jsx
   
   ![Alt text](<Images/GA3 - Creating the Countdown Effect - Step 5.png>)

7. We also need to calculate the minutes and seconds remaning to display them to the user.
8. These variables will automatically recalculate each time the seconds changes.
9. This is because the seconds variable is tracked by state. When it changes, a re-render of the component is triggered.
   
   ![Alt text](<Images/GA3 - Creating the Countdown Effect - Step 8.png>)

10. Now lets modify App.jsx to pass the minutes to Timer.jsx
    
   ![Alt text](<Images/GA3 - Creating the Countdown Effect - Step 9.png>)

12. Your app should now look like this.

    ![Alt text](<Images/GA3 - Creating the Countdown Effect - Step 10.png>)

13. Take a screenshot of the output and add it to ScreenShots
14. Our Timer Component is now complete
15. `git add .`
16. git Commit -m "Timer Component Complete"
17. git push

## Guided Activity 3 - Finishing up App.jsx

1. Now we simply need to add functionality to start and reset the timer.
2. We need to track whether the timer is currently running or not. If it is running we will render the Timer component.
3. We will also need functions to start and reset the timer.
4. Modify App.jsx with the following:
   
   ![Alt text](<Images/GA3 - Finishing Up App jsx - Step 4.png>)

6. Now we only want to render the timer when isRunning is true.
7. We also need to set the buttons to start and stop the timer.
   
   ![Alt text](<Images/GA3 - Finishing Up App jsx - Step 6.png>)

9. The basic functionality of our Timer App should now be working.
    
   ![Alt text](<Images/GA3 - Finishing Up App jsx - Step 7.png>)

11. Select a time and start the timer. Take a screenshot and add to the screenshots folder.

12. When done create a new commit with Guided Activity 3 Timer Complete.
13. `git add .`
14. `git commit -m "Guided Activity 3 Timer App Complete"`
15. `git push`

## Guided Activity 3 - Bootstrap & Custom Styles

1. Our application is not very exciting looking.
2. Let's use some built-in bootstrap classes to change the appearance. Modify App.jsx to appear as follows:

   ![Alt text](<Images/GA3 - BootstrapAndCustomStyles-pt1.png>)

3. Modify Timer.jsx to appear as follows:

   ![Alt text](<Images/GA3-BootstrapAndCustomStyles-pt2.png>)


4. Modify TimerInput.jsx to appear as follows:

   ![Alt text](<Images/GA3-BootstrapAndCustomStyles-pt3.png>)

5. Your application should now appear as follows: 

   ![Alt text](<Images/GA3-BootstrapAndCustomStyles-pt4.gif>)

6. Let’s take it just a step further and add some pop to our cards. In Main.jsx, switch the import for "./index.css" to "./app.css"

   ![Alt text](<Images/GA3-BootstrapAndCustomStyles-pt5.png>)     

7. Now add the following code inside of App.css

   ![Alt text](<Images/GA3-BootstrapAndCustomStyles-pt6.png>)

8. Your application should now appear as follows: 

   ![Alt text](<Images/GA3-BootstrapAndCustomStyles-pt7.gif>)
   
9. When done create a new commit with Guided Activity 3 Complete.
10. `git add .`
11. `git commit -m "Guided Activity 3 Complete"`
12. `git push`

Feel free to message your instructor or the TA on Canvas if you have any questions.
