# FoundU 🏆

FoundU is a mobile application built with React Native that streamlines the process of returning lost UMass UCards to their owners. By leveraging AI-powered text recognition and automated web scraping, the app instantly notifies students when their card is found. This project was awarded the **Wolfram Award** at HackUMass.

[**Devpost Link**](https://devpost.com/software/foundu)

## The Problem
Every UMass student has experienced or witnessed the stress of losing a UCard. These cards are essential for accessing dorms, meal plans, and other campus facilities. When a UCard is found, the current methods for returning it are inefficient, often relying on Snapchat stories where the post can easily get lost, or dropping it in a random lost-and-found box. This results in a frustrating and time-consuming recovery process for the owner.

## Our Solution
FoundU simplifies this entire process into a few easy steps:

1.  **Scan the UCard:** A user who finds a UCard simply opens the app and takes a photo of it.
2.  **AI-Powered Name Extraction:** The app uses Google Vision API to perform Optical Character Recognition (OCR) and automatically extract the student's name from the image.
3.  **Automated Email Lookup:** The backend system uses Puppeteer to perform an automated search on the UMass People Finder directory to retrieve the student's email address.
4.  **Instant Notification:** An email is automatically sent to the card's owner via Nodemailer, containing a picture of their UCard and details about where it was found or how to retrieve it.

## Technical Architecture

### Mobile Application (Frontend)
The cross-platform mobile app is built using **React Native** and the **Expo** framework.
* **UI/UX:** A clean, intuitive interface with a dark theme and maroon accents. Interactive animations are implemented using React Native’s Animated API for a polished user experience.
* **OCR Integration:** The app integrates the **Google Vision API** to perform on-device text detection. An image of the UCard is converted to base64 and sent to the API, which returns the extracted text. A custom parsing function then identifies the student's full name.

### Backend Server & Automation
The backend is a **Node.js** server using the **Express** framework. It orchestrates the core logic of the application.
* **API:** A simple REST API endpoint handles image uploads from the mobile client using `multer`.
* **Web Scraping:** Upon receiving a student's name, the server launches a headless browser instance using **Puppeteer**. It navigates to the UMass People Finder, logs in with stored credentials, and scrapes the search results to find the corresponding student email address(es).
* **Email Notifications:** The server uses **Nodemailer** to send automated emails to the identified student. The email includes a custom message, the student's name, and the picture of the found UCard as an attachment.

## Demo

https://github.com/user-attachments/assets/6d979bfc-7518-4a55-94d7-6a15694d06ad

## App Flow & Features

### 1. Home Screen
A simple and clear entry point for a user who has found a UCard.

<img width="422" height="900" alt="Image" src="https://github.com/user-attachments/assets/3d85aa06-3d44-4ff3-9053-636809b3c854" />

### 2. UCard Scanning & Name Confirmation
The user takes a photo, and the app uses OCR to extract the name, which the user then confirms.

<img width="423" height="900" alt="Image" src="https://github.com/user-attachments/assets/d1c5d464-377b-4a24-9e53-41a2d6adbc31" />
<img width="419" height="900" alt="Image" src="https://github.com/user-attachments/assets/9780966b-1c42-452f-8440-2dd82ebdfce3" />

### 3. Action Selection & Location Input
The user specifies whether they left the card somewhere or will hold onto it for the owner.

<img width="423" height="900" alt="Image" src="https://github.com/user-attachments/assets/749fde31-074f-4311-b8de-fdae258a6894" />
<img width="423" height="900" alt="Image" src="https://github.com/user-attachments/assets/67153e4b-0a41-4afd-8f78-2db406e8ad57" />

### 4. Automated Email Notification
The system automatically finds the owner's email and sends a notification with the UCard image and retrieval information.

<img width="424" height="900" alt="Image" src="https://github.com/user-attachments/assets/d0cad5c7-c2c0-44c7-a66b-6c44b9d8edb8" />

### 5. Success!
The email is sent (Email Template)!

<img width="1119" height="489" alt="Image" src="https://github.com/user-attachments/assets/1aabc6e1-8449-479d-a557-e6c32c0a2597" />

## What's Next for FoundU
Our goal is to collaborate with UMass administration to integrate FoundU into official university systems. We are exploring potential integrations with platforms like GETMobile to make this a seamless, university-sanctioned solution for all students.

## Built With
* React Native (Expo)
* Node.js
* Express
* Google Vision API
* Puppeteer
* Nodemailer
* MongoDB
* Firebase
