
# Political Research Application

**Author**: Blaise Clarke, Lena Eivy & Caity Heath
**Version**: 1.0.0

## Overview
This application is designed to make basic civic information more accessible to the public through the use of APIs. It uses information from the Google Civic Information API, the ProPublica Congress API, and the OpenSecrets funding API to map a user's address to their state and federal voting districts, retrieves their representatives and senators from both state and federal levels of government, and provides some detail on their top ten funding sources and their positions on the last twenty congressional votes they voted in. Additionally, the application provides an embedded form that allows a user to check if they are currently registered to vote and allows them to begin the process to register to vote if they are not. 

## Getting Started
This application is available on Heroku at https://politicalresearch301.herokuapp.com/.
To use this application locally, do the following:
- Clone this repository locally.
- Install the following dependencies using the provided package-lock file: cors, dotenv, ejs, express, pg, and superagent.
- Obtain API keys for the following services - Google Civic Information API, ProPublica Congress API, OpenSecrets API. Add these API keys to your personal .env file for the project.
- Create a postgres database through the psql service named 'political'. Use the provided schema.sql file to create the required tables for the application.
- Use the nodemon service to run the server.js application locally, and visit it in your browser at http://localhost:PORT/, where PORT is your environment's default port number (typically 3000).


## Architecture
This application is primarily written in Javascript, using CSS for styling and HTML with embedded javascript for structure and content. It has the following dependencies - 
- "cors": "2.8.4",
- "dotenv": "6.1.0",
- "ejs": "^2.6.1",
- "express": "4.16.4",
- "pg": "7.6.0",
- "superagent": "4.0.0-beta.5"

This application uses a postgres database for data storage/caching using this schema -
TABLE votingdistricts
- id SERIAL PRIMARY KEY,
- address TEXT,
- state TEXT,
- voting_district TEXT
TABLE politicianinfo
- voting_district_id INT NOT NULL REFERENCES votingdistricts(id),
- id SERIAL,
- state TEXT,
- voting_district TEXT,
- official_office TEXT,
- politician TEXT,
- role TEXT,
- image_url TEXT,
- affiliation TEXT,
- contact_phone TEXT,
- contact_address TEXT,
- website TEXT,
- propublica_id TEXT
There are additional tables included for functionality we plan to include in future releases.

This application uses the following APIs and endpoints -
- Google Civic Information: endpoint /civicinfo/v2/representatives/
- Open Secrets: endpoint /api/, using ?method=candContrib as a query
- Open Secrets: endpoint /api/, using ?method=getLegislators as a query
- Propublica: endpoint /congress/v1/members/

## Change Log
All dates and times in PST.
November 9th, 4:00PM:  v1.0.0 - Final touches added, tested on heroku; code freeze start
November 8th, 2:40PM:  v0.3.2 - Finalized base styling
November 8th, 2:30PM:  v0.3.1 - Consistent race condition with rendering fixed
November 8th, 12:35PM: v0.3.0 - Funding chart completely integrated into detail page
November 7th, 4:10PM:  v0.2.2 - Funding chart working consistently on test server
November 7th, 3:00PM:  v0.2.1 - ProPublica IDs retrieved for politicians
November 7th, 1:10PM:  v0.2.0 - Detail page for representatives created and functioning
November 6th, 4:20PM:  v0.1.2 - Database used for all data retrieval functionality
November 6th, 3:30PM:  v0.1.1 - OpenSecrets functionality and postgres database created 
November 5th, 4:55PM:  v0.1.0 - representatives page using Google Civic Info data
November 5th, 3:00PM:  v0.0.3 - intake page and representatives page created
November 5th, 11:45AM: v0.0.2 - rough skeleton created, about page created
November 5th, 10:25AM: v0.0.1 - initial proof of life 
November 2nd, 6:00PM:  v0.0.0 - initial schema and documentation


## Credits and Collaborations
Many thanks to Hannah Sindorf, Catherine Looper, Nicholas Carignan, and John Cokos for their help and support this week in getting this application working.

## Presentation 
https://docs.google.com/presentation/d/1WBPyvRhcp2bIGw_JVT7dMT3f08pwloc0dZiITVqWc30/edit

# PoliticalResearch
Civic Research

## Team Members:
Blaise Clarke
Caity Heath
Lena Eivy

## A description of the project
This app will provide information users can use to research and inform their voting options. It will also help them get set up to vote if they are not already registered. It will also provide information about the politicians who represent them in their districts and how they have voted in the past.

## The overall problem domain and how the project solves those problems
Voter engagement is relatively low currently. One of the reasons for this is because of insufficient information leading to voter apathy. This app is designed to make it super easy for someone to find out who represents them and how they have voted in the past.

## libraries, frameworks, or packages that your application requires in order to properly function
See Getting Started and Architecture sections.

## Instructions that the user may need to follow in order to get your application up and running on their own computer
See the Architecture section.

## Clearly defined API endpoints with sample responses
See the Architecture section.

## Clearly defined database schemas
See the Architecture section.
