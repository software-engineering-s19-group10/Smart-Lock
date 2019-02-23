<p align="center">
<img src="https://github.com/software-engineering-s19-group10/smart-lock/blob/master/SmartLock_Logo_v2.jpg" height="300">
</p>

<p align="center">
<a href="https://github.com/software-engineering-s19-group10/smart-lock/graphs/contributors">
  <img alt="contributors" src="https://img.shields.io/github/contributors/software-engineering-s19-group10/smart-lock.svg?style=popout" /></a>
<a href="https://github.com/software-engineering-s19-group10/smart-lock/graphs/commit-activity">
  <img alt="last-commit" src="https://img.shields.io/github/last-commit/software-engineering-s19-group10/smart-lock.svg?style=popout"/></a>
<a href="https://github.com/software-engineering-s19-group10/smart-lock/issues">
  <img alt="issues" src="https://img.shields.io/github/issues/software-engineering-s19-group10/smart-lock.svg?style=popout"/></a>
<a href="https://github.com/software-engineering-s19-group10/smart-lock">
  <img alt="languages" src="https://img.shields.io/github/languages/top/software-engineering-s19-group10/smart-lock.svg?style=popout"/></a>
<a href="https://github.com/software-engineering-s19-group10/smart-lock">
  <img alt="languages-ct" src="https://img.shields.io/github/languages/count/software-engineering-s19-group10/smart-lock.svg?style=popout"/></a>
<a href="https://github.com/software-engineering-s19-group10/smart-lock"> 
  <img alt="repo-size" src="https://img.shields.io/github/repo-size/software-engineering-s19-group10/smart-lock.svg?style=popout"/></a>
<a href="https://software-engineering-s19-group10.github.io/website/"> 
  <img alt="website" src="https://img.shields.io/website-up-down-green-red/https/software-engineering-s19-group10.github.io%2Fwebsite%2F.svg?label=website-status"/></a>
</p>

# Smart Lock

## Description:

With a growing number of online retailers and the convenience of having any product delivered to one’s doorstep at the click of a few buttons, the number of packages being delivered each year is on the rise. Unfortunately, these packages are also commonly left unguarded, leaving the perfect opportunity for a malicious individual to steal the package while you’re away from the house. A major issue with package thieves and home burglary type crimes, in general, is the lack of evidence. Only a very small number of such crimes actually have enough evidence to identify a suspect. One existing solution to the package theft issue is Amazon Key, a system by which authorized Amazon deliverers can enter your home to deposit your package. This solution, however, is hindered by both it’s cost and limitation to one online retailer.

A large majority of home security systems today are both expensive and complicated. Two improvements to home security developed in recent years, namely keyless locks and home security cameras, are both sold separately, and individually pricey. We would like a cost-effective system that integrates the keyless lock and home security camera solutions to home security, and use them to simultaneously improve upon a consumer’s experience with package delivery.

Our approach to the aforementioned problems involves the creation of an easy-to-use home security system where a video camera is used to both monitor the house and authenticate users using facial recognition, condensing the functionality of both the keyless lock and home security camera systems. For the purposes of this project, the current plan is to use a computer webcam for the video camera, and the lock will be assumed to already have been set up such that the lock defaults to being locked, and unlocks upon the sending of an unlock signal.  Members of the household will be able to enter their house through facial authentication, while package couriers will be able to scan the package barcode to allow themselves into the house to deposit the package. Records of all authentications will be able to be monitored through the use of a web application tied to the camera, with the option to be notified in the event of suspicious activity. 

## Features:

- Authentication using facial recognition.
>Homeowners will be able to register the faces of any number of individuals who should be capable of opening the door using the web application. The video camera, upon recognition of one of these faces, will unlock the door. Individuals not registered will be treated as visitors or strangers, requiring the homeowner to define the behavior of the security system in these situations, as will be explained below.

>Necessities for detecting and recognizing faces and detecting masked individuals:
>In order for the system’s facial detection to work, the system must train on some organized dataset of faces.  Fortunately, the internet has many public datasets to train on.

>Examples of some include 
>http://tamaraberg.com/faceDataset/index.html
>http://robotics.csie.ncku.edu.tw/Databases/FaceDetect_PoseEstimate.htm
>http://www.wilmabainbridge.com/facememorability2.html

>In order for the homeowner to allow specific faces to be recognized, a private database must be compiled. Specifically, the homeowner must self-compile a dataset to train on, namely providing a set of pictures of the person that is to be authenticated.
>In order for the system to detect masked individuals, we will initially train on photos of black ski masks.  Due to a lack of public data pertaining to black ski masks, the current idea is to manually compile a dataset of black ski masks at different angles and different backgrounds. We will update the training set with other types of masks if time permits.

- Video recording system for home security.
>Records only when motion is detected (that way video doesn’t take up so much memory).
>The recorded video is stored on the server and logged in a database that can be viewed by the owner via their user account.
>Records the date and time of video recording as well.
>Also features an events log which catalogs all events that occured on a given day of the month.

- Data Visualization
>Allows for visualization, and analytics of data that is seperate from a simple events log.
>May answer interesting questions that a user may have such as,
>What time of day are visitors the most active?
>What visitors are the most active? Today? This week? This month?
>Provide suggested “plans” for access to certain users based on their times of access in order to provide an extra layer of security. For example, if a certain person is not visiting the house during the full range of their allowed hours, the system will provide a suggestion to “trim down” the hours to the range in which the user actually visits.

- Smart Package Manager
>Manages the delivery of packages to your door / house.  Almost fully automated.  The only human intervention is entering tracking number in web app.
>Keeps track of packages and actively monitors incoming packages.
>Authenticates mail (wo)men by scanning the barcode (that translates to the tracking number) on the package.  (A barcode that is already on all packages; requires no  cooperation from mail carriers to implement; which makes this compatible with any carrier or website).
>Features a timer that is triggers notification to the owner if the door isn’t relocked after some amount of seconds (user-inputted).  Preventing the deliverer from snooping around home.

- Easy Temporary Authentication System
>Alternative to facial recognition Authentication if that isn’t an option (you don’t have a picture of someone you want to grant access to).
>Create URLs that can be shared with other.  Giving them access to a simple web ui that lets them manually unlock the door with a press of a button from their device.
>Can be configured to allow for X unlocks, or duration of time, etc. etc.

- Notification of deliveries, visitors, and suspicious individuals.
>Receive SMS, push notification and/or email about incoming packages, people accessing the home, etc.
>When a package courier scans an expected package using the video camera, a visitor or household member authenticates themselves
>Potentially suspicious individuals, such as individuals wearing masks, trigger the motion detection system

- Stranger Reporting Network
>Allows for all Smart Lock customers to communicate with each other about strangers in the area, through an interactive map.
>As part of the “Notification of deliveries, visitors, and suspicious individuals”, if a suspicious actor is in front of the door the owner  will be immediately notified.  Upon verification of who is it, if it is someone that the owner does not recognize, they have the option to report to the SRN (with a description if desired).

- Common Database and Backend API
>Allows features to access user information through API calls
>
>Contain tables necessary for other features:
>
>General user information (name, house ID, etc)
>
>Bindings of user information and facial data
>
>Mappings of video files for the playback feature
>
>Packages (dates, barcode values, etc)

(Note that the primary objective of this project is to work on the software behind the smart lock.  The hardware for the lock is not a focus, however if we have enough time we will also design hardware sufficient for live demonstration purposes.  The software will be ready to connect to hardware.)


## Group Members:

- Team One:
>Web App Unlocker (Actually unlocks the door itself without any sort of Face ID or URL.  The frontend and backend)
>
>Create backend and frontend for Auth Permissions (allowing temporary members)
>
>Create temporary Authentication url system (create the url system that is used to authorize ppl temporarily)
>
>Add detail Authentication Configuration (for temporary members from url system) (e.g. u may only want certain ppl to gain access for a certain period of time, certain amount of days)
>
>Smart Package Tracker and BarCode Authentication; More time? R&D additional security measures. 
>
>- [Daniel Nguyen](https://github.com/DanNguyen-CE)
>- [Michael Truong](https://github.com/MichaelTruongZ)
>- [Ted Moseley](https://github.com/tmose1106)

- Team Two (A):
>Database Structuring (Shared Infrastructure) and communicating structure to other subteams.
>
>Assist group 2B with their responsibilities.
>
>- [Eric Lin](https://github.com/Yukirilin)
>- [Mohit Khattar](https://github.com/koml12)


- Team Two (B):
>Data Visualization (be creative; using data on who and when (events log); e.g. how many people visited this month? who visited this month?)
>
>Create backend and frontend for "events log" (a log of significant events (masked person detected, face detected, motion detected, facial recognized))
>
>Create SMS notification handler (handles any sort of notification (notify user of any event))
>
>Make all classes of notifications toggleable
>SRN (Stranger Reporting Network) Server API and connect it to the server
>
>Live feed communication between the server, embedded computer, and web client
>
>- [Mohammad Nadeem](https://github.com/mnadev)
>- [Andrew Sengupta](https://github.com/andrewsengupta)


- Team Three:
>Motion Detection
>
>Facial Detection
>
>Facial Recognition
>
>Masked person Detection (must implement own interface/unlock signal to lock)
>
>Create backend and frontend for Auth Permissions (add active members)
>
>Add detail Authentication Configuration (for people recognized by face) (e.g. you may only want certain people to gain access for a certain period of time, certain amount of days)
>
>- [Amandip Kaler](https://github.com/ak1415)
>- [Jasjit Janda](https://github.com/jandaj)
>- [Jeff Lu](https://github.com/jefflu188)


```
Software Engineering [ECE 452]  
Ivan Marsic  
Rutgers University 2019  
```
