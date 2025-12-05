<link rel="stylesheet" href="/assets/custom.css">

[![Artifact GitHub Repository](https://img.shields.io/badge/eportfolio-github-233E56?style=for-the-badge&logo=github)](https://github.com/michaelTurco/michaelturco.github.io)&nbsp;[![Merit Pages - Michael Turco](https://img.shields.io/badge/merit_pages-michael_turco-0A6EB4?style=for-the-badge&logo=merit)](https://meritpages.com/Michael-Turco/8191998)

## Introduction

My name is **Michael Turco**, and this ePortfolio is my capstone project for CS-499 at SNHU. I'll be creating a professional and polished artifact through three different categories of enhancements, and showcase the skills I've learned while attending SNHU. I plan to be graduating with a Bachelor's degree in Computer Science / Software Engineering in December 2025!

## Table of Contents

- [Overview of my Artifact](#overview-of-my-artifact)
- [Informal Code Review Video](#informal-code-review-video)
- [Enhancement 1 - Software Engineering and Design](#enhancement-1---software-engineering-and-design)
- [Enhancement 2 - Algorithms and Data-Structures](#enhancement-2---algorithms-and-data-structures)
- [Enhancement 3 - Databases](#enhancement-3---databases)
- [Course Outcomes](#course-outcomes)

## Overview of my Artifact

The artifact I selected for all three enhancements is my full-stack mobile application called **Track My Weight** from CS-360 Mobile Architecture and Programming. The original app lets the user create an account and login to a local MySQL database, record new weight entries, and view their weight history in a scrollable list.

**Original Artifact:** [(Entire Project)](https://github.com/michaelTurco/CS-360-Mobile-Architecture-And-Programming/tree/10afc06251f83af4ad8769564a242649a72e942c)&nbsp;&nbsp;[(Java Files)](https://github.com/michaelTurco/CS-360-Mobile-Architecture-And-Programming/tree/10afc06251f83af4ad8769564a242649a72e942c/app/src/main/java/com/turco_michael_weight_tracking)  
**Updated Artifact:** [(Entire Project)](https://github.com/michaelTurco/CS-360-Mobile-Architecture-And-Programming)&nbsp;&nbsp;[(Java Files)](https://github.com/michaelTurco/CS-360-Mobile-Architecture-And-Programming/tree/main/app/src/main/java/com/turco_michael_weight_tracking)

I originally completed the first version of the app in February 2025, and chose it for this portfolio because it provided a strong foundation and plenty of opportunities for meaningful improvement. Through the **three enhancements described below**, I turned this project into a much more polished, professional, and user-ready application that I intend to publish on the app store.

---
## Informal Code Review Video

In this video, I walk through the original version of my artifact in Android Studio. This covers the **Track My Weight** appp, and I evaluate the current state of the code, such as coding style and errors, and I also outline the changes I plan to implement across all three enhancement categories.

<iframe width="640" height="360" src="https://www.youtube.com/embed/5ZZaW-F6zio" frameborder="0" allowfullscreen></iframe>

---
## Enhancement 1 - Software Engineering and Design
**Original narrative PDF:** [(View Narrative)](https://github.com/michaelTurco/michaelturco.github.io/blob/main/narratives/CS-499%20Milestone%20Two%20Narrative.pdf)

For the first enhancement to my full-stack application, I've updated the UI and added some new features to improve the user experience while using the app.

In the login screen, I added a custom title and icon, some description text, and a 'Remember Me' button. Users can now automatically be logged in when opening the app, saving them time when quickly trying to access the app. When the 'Remember Me' flag is set, it saves their credentials to the apps storage, and whenever the app opens, it auto populates the username & password and attempts to sign in. These fairly simple changes completely change the feel of this login menu, and makes the app significantly more user friendly and convenient to use.

<img src="/assets/images/login_page.png" width="400">

I applied the custom logo I made to the app's icon, and replaced the name so it displays properly in the users app list. I created an adaptive android icon, with a background and foreground component. Luckily I thought ahead when creating this logo back in CS-360, and saved the original image file with two distinct layers so I didn't have to remake the gradient!

<img src="/assets/images/app_icon.png" width="300">

Lastly, I updated the settings page by adding a custom 'Measurement Unit' feature, which allows the user to switch between pounds and kilograms. This part was a little bit harder than it may seem at first, I had to update every single UI element that was hard-coded to originally work with pounds. I also had to change how the user input was handled when adding a new weight or setting a goal weight, since a value of '50' could either mean 50 pounds or 50 kilograms depending on what setting they had activated.

To help me out with this, I made a helper class called 'UnitConverter', as well as a 'MeasurementUnit' enum, in case I ever wanted to add more measurement units in the future. I made functions to convert from any measurement unit to any other measurement unit, which came in very handy. I figured out that storing the weight in the same measurement unit every time is the best, since you won't have to update tons of values each time you switch units. I chose to store all my weights in pounds, since that is what the app originally used. Each time the app tries to display a weight value, it first converts from pounds to the selected measurement unit, and any time user input is accepted, it is converted from the selected measurement unit into pounds.

<img src="/assets/images/settings_page.png" width="400">

---
## Enhancement 2 - Algorithms and Data Structures
**Original narrative PDF:** [(View Narrative)](https://github.com/michaelTurco/michaelturco.github.io/blob/main/narratives/CS-499%20Milestone%20Three%20Narrative.pdf)

For the second enhancement, I focused on adding a 'graph' page and an algorithm to estimate the time in days until the user reaches their goal weight.

I created a new graph UI page, and added some relevant UI elements so the user can edit their goal weight, or see the prediction time. I used the **MPAndroidChart** library to create the graph UI element, and configured it's settings to get it to look how I wanted. This graph had a lot of the features that I was looking for, such as pinch to zoom, drag to pan around, custom graph scale and spacing, and a custom axis name formatter. I looped through all the user's weight data and plotted those points on the graph, with lines connecting each point.

To calculate the estimation time, I made an algorithm to compute the weighted linear regression of the data points, which in the end gives a 'line of best fit'. I use this line to calculate the intercept to the goal weight line, and figure out the time amount from there. I display this estimation in a little UI element on the bottom, which can also show "N/A" if the line doesn't cross at some future date.

<img src="/assets/images/graph_page.png" width="300">

On the home page, I added a UI element to navigate to the graph page, and you can also see the graph's estimation time at a glance, almost like a 'dashboard' page. I also added a simple round button to the 'Weight List' page, to simply navigate to the graph from there as well.

<img src="/assets/images/home_page.png" width="400">

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

---
## Course Outcomes

These are the **five** course outcomes that I will be demonstrating mastery in through my project.

1. Employ strategies for building collaborative environments that enable diverse audiences to support organizational decision making in the field of computer science
2. Design, develop, and deliver professional-quality oral, written, and visual communications that are coherent, technically sound, and appropriately adapted to specific audiences and contexts
3. Design and evaluate computing solutions that solve a given problem using algorithmic principles and computer science practices and standards appropriate to its solution, while managing the trade-offs involved in design choices
4. Demonstrate an ability to use well-founded and innovative techniques, skills, and tools in computing practices for the purpose of implementing computer solutions that deliver value and accomplish industry-specific goals
5. Develop a security mindset that anticipates adversarial exploits in software architecture and designs to expose potential vulnerabilities, migitage design flaws, and ensure privacy and enhanced security of data and resources

---
