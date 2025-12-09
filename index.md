<link rel="stylesheet" href="/assets/custom.css">

[![Artifact GitHub Repository](https://img.shields.io/badge/eportfolio-github-233E56?style=for-the-badge&logo=github)](https://github.com/michaelTurco/michaelturco.github.io)&nbsp;[![Merit Pages - Michael Turco](https://img.shields.io/badge/merit_pages-michael_turco-0A6EB4?style=for-the-badge&logo=merit)](https://meritpages.com/Michael-Turco/8191998)

## Introduction

My name is **Michael Turco**, and this ePortfolio is my capstone project for CS-499 at SNHU. I'll be creating a professional and polished artifact through three different categories of enhancements, and showcasing the skills I've learned while attending SNHU. I plan to graduate with a Bachelor's degree in Computer Science / Software Engineering in December 2025!

## Table of Contents

- [Overview of my Artifact](#overview-of-my-artifact)
- [Informal Code Review Video](#informal-code-review-video)
- [Enhancement 1 - Software Engineering and Design](#enhancement-1---software-engineering-and-design)
- [Enhancement 2 - Algorithms and Data-Structures](#enhancement-2---algorithms-and-data-structures)
- [Enhancement 3 - Databases](#enhancement-3---databases)
- [Course Outcomes](#course-outcomes)

## Overview of my Artifact

The artifact I selected for all three enhancements is my full-stack mobile application called **Track My Weight** from CS-360 Mobile Architecture and Programming. The original app lets the user create an account and log in to a local MySQL database, record new weight entries, and view their weight history in a scrollable list.

**Original Artifact:** [(Entire Project)](https://github.com/michaelTurco/CS-360-Mobile-Architecture-And-Programming/tree/10afc06251f83af4ad8769564a242649a72e942c)&nbsp;&nbsp;[(Java Files)](https://github.com/michaelTurco/CS-360-Mobile-Architecture-And-Programming/tree/10afc06251f83af4ad8769564a242649a72e942c/app/src/main/java/com/turco_michael_weight_tracking)  
**Updated Artifact:** [(Entire Project)](https://github.com/michaelTurco/CS-360-Mobile-Architecture-And-Programming)&nbsp;&nbsp;[(Java Files)](https://github.com/michaelTurco/CS-360-Mobile-Architecture-And-Programming/tree/main/app/src/main/java/com/turco_michael_weight_tracking)

I originally completed the first version of the app in February 2025, and chose it for this portfolio because it provided a strong foundation and plenty of opportunities for meaningful improvement. Through the **three enhancements described below**, I turned this project into a much more polished, professional, and user-ready application that I intend to publish on the app store.

---
## Informal Code Review Video

In this video, I walk through the original version of my artifact in Android Studio. This covers the **Track My Weight** app, and I evaluate the current state of the code, such as coding style and errors, and I also outline the changes I plan to implement across all three enhancement categories.

<iframe width="640" height="360" src="https://www.youtube.com/embed/5ZZaW-F6zio" frameborder="0" allowfullscreen></iframe>

---
## Enhancement 1 - Software Engineering and Design
**Original narrative PDF:** [(View Narrative)](https://github.com/michaelTurco/michaelturco.github.io/blob/main/narratives/CS-499%20Milestone%20Two%20Narrative.pdf)

For the first enhancement to my full-stack application, I've updated the UI and added some new features to improve the user experience while using the app.

In the login screen, I added a custom title and icon, some description text, and a 'Remember Me' button. Users can now automatically be logged in when opening the app, saving them time when quickly trying to access the app. When the 'Remember Me' flag is set, it saves their credentials to the app's storage, and whenever the app opens, it auto populates the username & password and attempts to sign in. These fairly simple changes completely change the feel of this login menu, and makes the app significantly more user friendly and convenient to use.

<img src="/assets/images/login_page.png" width="400">

I applied the custom logo I made to the app's icon, and replaced the name so it displays properly in the user's app list. I created an adaptive android icon, with a background and foreground component. Fortunately, I thought ahead when creating this logo back in CS-360, and saved the original image file with two distinct layers so I didn't have to remake the gradient!

<img src="/assets/images/app_icon.png" width="300">

Lastly, I updated the settings page by adding a custom 'Measurement Unit' feature, which allows the user to switch between pounds and kilograms. This part was a little bit harder than it may seem at first, I had to update every single UI element that was hard-coded to originally work with pounds. I also had to change how the user input was handled when adding a new weight or setting a goal weight, since a value of '50' could either mean 50 pounds or 50 kilograms depending on what setting they had activated.

To help me out with this, I made a helper class called 'UnitConverter', as well as a 'MeasurementUnit' enum, in case I ever wanted to add more measurement units in the future. I made functions to convert from any measurement unit to any other measurement unit, which came in very handy. I figured out that storing the weight in the same measurement unit every time is the best, since you won't have to update tons of values each time you switch units. I chose to store all the weights in pounds, since that is what the app originally used. Each time the app tries to display a weight value, it first converts from pounds to the selected measurement unit, and any time user input is accepted, it is converted from the selected measurement unit into pounds.

<img src="/assets/images/settings_page.png" width="400">

While working on this enhancement I learned a lot about developing Android apps, such as the different classes used like 'Fragment', 'Activity', 'Context', and the 'binding' variable. I found ways to cleanly organize the code to make it more readable, and made helper functions to help with navigation and unit conversion. I used some references to documentation for help at times, which often made me learn about features or functions that were available to me. I learned how to interface with the bottom navigation bar to navigate the user, and also had to figure out screen transition animations to keep the UI smooth. I didn't encounter too many issues when working through this enhancement, but it was certainly a big task to work through all the old code and figure out how it can be refactored.

**Course Outcomes Reached:**  
Through this enhancement, I reached [course outcomes](#course-outcomes) #1 and #4. Improving the login UI and login process delivered real value to the app since the overall user experience was improved, and users no longer have to sit through entering their login credentials each time. Allowing the users to switch measurement units improved the accessibility of the app, since users who aren't used to pounds or don't have a scale that shows pounds can now use the app more comfortably.

---
## Enhancement 2 - Algorithms and Data Structures
**Original narrative PDF:** [(View Narrative)](https://github.com/michaelTurco/michaelturco.github.io/blob/main/narratives/CS-499%20Milestone%20Three%20Narrative.pdf)

For the second enhancement, I focused on adding a 'graph' page and an algorithm to estimate the time in days until the user reaches their goal weight.

I created a new graph UI page, and added some relevant UI elements so the user can edit their goal weight, or see the prediction time. I used the **MPAndroidChart** library to create the graph UI element, and configured its settings to get it to look how I wanted. This graph had a lot of the features that I was looking for, such as pinch to zoom, drag to pan around, custom graph scale and spacing, and a custom axis name formatter. I looped through all the user's weight data and plotted those points on the graph, with lines connecting each point.

To calculate the estimation time, I made an algorithm to compute the weighted linear regression of the data points, which in the end gives a 'line of best fit'. I use this line to calculate the intercept to the goal weight line, and figure out the time amount from there. I display this estimation in a little UI element on the bottom, which can also show "N/A" if the line doesn't cross at some future date.

<img src="/assets/images/graph_page.png" width="300">

On the home page, I added a UI element to navigate to the graph page, and you can also see the graph's estimation time at a glance, almost like a 'dashboard' page. I also added a simple round button to the 'Weight List' page, to simply navigate to the graph from there as well.

<img src="/assets/images/home_page.png" width="400">

While working on this enhancement, I learned about the MPAndroidChart library, which is used to render a graph with points in the UI. Without this library, it would have been quite a challenge to get the graph working how I wanted it, but it still required some configuring out-of-the-box before it was ready. Implementing the weighted linear regression formula was also a little challenging, since I ran into the issue of precision with my data timestamp values. The graph only worked with floats, and when I tried to pass in my epoch timestamp, the float value would greatly lose precision, down to the nearest 31 whole minutes. This was a pretty tough issue to spot and to fix, but I eventually realized I can 'normalize' the timestamps to 0, and add back the time only when trying to display the date. I learned a lot about setting up a graph in code, performing a complex formula on a set of data, and then plotting that data on the graph.

**Course Outcomes Reached:**  
Through this enhancement, I reached [course outcomes](#course-outcomes) #3 and #1. I implemented an algorithm to calculate the trend line of a graph of data, and used this to estimate when the user will reach their goal weight. This feature lets the user get more use out of the app and their data, since they can quickly check if they are on track to meet their goals without having to do complex computations themselves.

---
## Enhancement 3 - Databases
**Original narrative PDF:** [(View Narrative)](https://github.com/michaelTurco/michaelturco.github.io/blob/main/narratives/CS-499%20Milestone%20Four%20Narrative.pdf)

For the third enhancement, I switched from using a local MySQL database, to an online hosted Firebase database. I added account creation and user authentication, and stored user data in a secured document using Firebase Firestore. I also implemented the 'Account' page, which was previously a blank page, and added some new features there.

For the user authentication, I used Firebase's username and password authentication, which requires an email username. In the image below you can see that I chose a generic email address at the end of their username, but the user never ends up seeing this internal email value anyways. I made a 'LoginAuthentication' class to help out with handling the Firebase interface, and implemented registering, signing in, and parsing an error message into a readable popup message.

<img src="/assets/images/firebase_authentication.png" width="700">

For the data storage, I used Firebase's Firestore database, which lets you create 'user documents' that require authentication with that account in order to read. I stored the list of weight entries, which stores a timestamp and a float weight value for each entry. You can see the Firestore file structure I have set up below:

<img src="/assets/images/firebase_firestore.png" width="700">

I also added some features to the 'Account' page, which was previously left blank when I worked on it last in CS-360. I added a way to change the user's "nickname", which is what the app greets them with in the home page, and also added a 'Sign Out' button to clear the authentication and return to the login screen.

<img src="/assets/images/account_page.png" width="400">

**Course Outcomes Reached:**  
Through this enhancement, I reached [course outcomes](#course-outcomes) #5, and #4. By adding Firebase authentication and a Firestore database, the user accounts are much more secure, and the user data is now hidden from those who don't have access. This is drastically different from storing the user passwords and data in plaintext on the local MySQL database, and it's a big leap towards a more realistic app. Firebase is a professionally used cloud platform for building online databases, and I referenced their official documentation when implementing authentication and data storage.

---
## Course Outcomes

These are the **five** course outcomes that I will be demonstrating mastery in through my project.

1. Employ strategies for building collaborative environments that enable diverse audiences to support organizational decision making in the field of computer science
2. Design, develop, and deliver professional-quality oral, written, and visual communications that are coherent, technically sound, and appropriately adapted to specific audiences and contexts
3. Design and evaluate computing solutions that solve a given problem using algorithmic principles and computer science practices and standards appropriate to its solution, while managing the trade-offs involved in design choices
4. Demonstrate an ability to use well-founded and innovative techniques, skills, and tools in computing practices for the purpose of implementing computer solutions that deliver value and accomplish industry-specific goals
5. Develop a security mindset that anticipates adversarial exploits in software architecture and designs to expose potential vulnerabilities, mitigate design flaws, and ensure privacy and enhanced security of data and resources

---
