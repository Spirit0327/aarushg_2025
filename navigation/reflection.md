---
layout: page
title: Reflection 
permalink: /reflection/
---

# Reflection on My First Website in AP Computer Science Principles

In our first assignment for AP Computer Science Principles (period 3), we were tasked with creating a basic website using Markdown and Jupyter Notebooks. Going into the project, I was excited but a bit unsure of how the process would unfold. I had some experience with coding, but working with Markdown in a notebook environment was new to me.

## The Process:
Markdown turned out to be a really efficient way to structure content. I appreciated how simple it was to format text with headers, lists, and links, without needing to dive into complicated HTML syntax. It allowed me to focus on the content and structure of my website rather than worrying too much about design elements.

Using Jupyter Notebooks was also an interesting experience. At first, I thought of Jupyter as more of a tool for coding and data science, but integrating it with Markdown made it a surprisingly effective tool for building simple, interactive websites. I especially liked being able to preview my changes right in the notebook as I worked, which made the process feel more dynamic.

## Challenges:
One of the main challenges I faced was figuring out how to balance the content and code in Markdown. I also needed to get comfortable switching between text formatting and adding elements like code blocks or links to make the website functional and easy to navigate. Another hurdle was learning how to display HTML properly inside Jupyter Notebooks, but I overcame that by using `IPython.display` to embed HTML content.

## What I Learned:
This project reinforced the importance of planning out a website’s structure before diving in. I learned how versatile Markdown can be, especially when combined with tools like Jupyter. It was rewarding to see how quickly I could create a functioning website using just a few lines of Markdown. 

I also gained a new appreciation for Jupyter Notebooks, as they can be used not just for coding, but for creating content-rich presentations or even basic websites. I now feel more confident in my ability to use Markdown and Jupyter together to build more complex projects in the future.

## Looking Forward:
I'm excited to see how we’ll build on this foundation in future assignments. This was a great introduction to the power of simple web development, and I can’t wait to explore more advanced techniques and tools as the course progresses.

# Reflection on Sprint 2 in AP Computer Science Principles!
Looking back at the past few weeks of learning both frontend and backend development, the student-led lectures were an effective way to break down complex topics like Python and JavaScript. The teaching segments followed by hands-on hacks allowed us to actively engage with the material and immediately apply it, which reinforced my thought processes.

## Teaching Experience Overview: 
We had to think on our feet to troubleshoot merge conflictions, and working together during the hands-on hack sessions, which boosted my confidence in both the technical and communication aspects of web development. Overall, teaching our peers made me more comfortable with the material and strengthened my teamwork skills. We completed 3.6 Conditionals and 3.7 Nested Conditionals, specifically, introducing Python conditions and worked on a mini quiz that involved the class participating and answering which was definetly a highlight of our presentation. I also learnt a lot of different topics such as Python Lists(3.10), De Morgan's Law(3.3), and more!

## How am I ready for the AP Exam?
My experience working on web development through these student-led lectures and hacks has definitely helped me prepare for the AP exam. Since I already had some prior experience with JavaScript and a bit of Python, I was able to build on that knowledge and get a deeper understanding of the concepts. Teaching the material with my group really reinforced what I knew. It forced me to break down complex topics and explain them in simple terms, which is a skill that will be important for College Board and Project Based Learning.

# Sprint 3 Reflection


## Project Overview:
During this sprint, our team developed an interactive chat room designed as a café-inspired study hall. The platform encourages productive collaboration, where users earn points by helping others—either by answering questions or engaging in meaningful study discussions. These points can be redeemed for virtual "coffees," which are displayed on the webpage using a menu and "buy" feature, creating a fun and engaging reward system.


## Collaboration Evidence:
To divide the workload, we split responsibilities between frontend and backend development. Using an incremental approach, we started by building a basic chatroom interface and then added features layer by layer. For instance, we first implemented the chat functionality, followed by the point system and the menu integration. Regular testing ensured each feature worked before moving to the next step. At the end, we focused on styling and added café-inspired themes to make the interface visually appealing and cohesive.


We utilized inspiration boards to create a consistent design, incorporating soft tones and café elements to foster a relaxed and inviting atmosphere. The code was organized into frontend and backend repositories, with frontend components focusing on the chat interface and menu features (HTML and JavaScript) and backend systems managing user points and interactions (Python).


We also sought feedback from peers, which helped us identify areas to improve, such as enhancing user interactivity and simplifying the process of redeeming points.


## Program Function and Purpose:
The program facilitates a virtual café environment where users can chat, collaborate, and exchange study tips. Key features include the ability to:


Earn points for productive contributions.
Use points to "buy" virtual coffees displayed on a menu.
Redeem items through a simple and interactive process.
Key user interactions involve chatting with others, earning points through participation, and navigating the menu to make purchases. The inputs are user contributions in the chat, while outputs include point updates and the virtual coffee display on the webpage.


## Summary:
This sprint provided me with invaluable experience in creating a functional and visually engaging user interface. I learned how to:


Design a cohesive and aesthetically pleasing UI inspired by real-world environments.
Test backend endpoints effectively using Postman.
Manipulate and update database records to reflect user actions.
Style data dynamically using JavaScript to connect backend functionality to the frontend.
Overall, this project helped me better understand how to integrate complex features while ensuring user engagement and satisfaction.




# MCQ Reflection
I developed the ability to analyze and interpret code to understand its functionality. Additionally, I expanded my knowledge of various computer science concepts and this in turn walked me through general internet safety such as avoiding phishing and cyber security.
I struggle with vocabulary questions related to specific CSP topics, particularly Boolean expressions and calling procedures. These questions often require identifying or explaining concepts and then evaluating their benefits and drawbacks, which I find challenging to analyze in detail.
I mostly made mistakes on questions asking me to specifically analyze boolean expressions and this was very difficult as many intricate images of code were difficult for me to comprehend. However I did learn to fix my mistakes on Skill 4.C: Identify and correct errors in algorithms and programs, including error discovery through testing. This was genuinely challenging for me on the practice exam and I hope to fix these.


# FULL STACK BLOG



## Executive Summary:
For this sprint, I developed a full-stack feature that stores, manages, and analyzes chess moves and their evaluations. I created a backend database to store chess moves, built a RESTful API for CRUD operations, and integrated the backend with a frontend interface. Users can interact with this feature on the analysis page, where they can view, add, update, and delete chess moves dynamically.

## Team Purpose:
Our team is working on a chess-based social media platform where users can discuss chess strategies, analyze their games, and learn from others. My feature complements this vision by providing users with the tools to analyze their games, save key moves, and review them later for improvement and discussion.

## Individual Feature:
My feature focuses on enabling users to store and manage their chess moves and evaluations. Users can upload PGN files to analyze moves and save these moves to a database for later use. The manager page lets users perform CRUD operations, providing full control over their stored data. This feature enhances the user experience by allowing in-depth review and customization of their chess gameplay data.

Key functionalities include:
- **POST:** Automatically saves moves and their evaluations after a game is played or a PGN file is uploaded.
- **GET:** Displays all saved moves in a dynamic table on the analysis page.
- **PUT:** Updates the evaluation or status of a move (e.g., marking it as "played").
- **DELETE:** Removes moves from the database when no longer needed.

## Input/Output Requests:
The evaluation API supports all CRUD operations:
1. **GET:** The analysis page fetches all moves from the backend and displays them in a table dynamically.
2. **POST:** A POST request is triggered when a game is completed, saving new moves and their evaluations to the database.
3. **PUT:** Users can update the status of a move, such as marking it as "played," which sends a PUT request to the API.
4. **DELETE:** A DELETE request is made when a user removes a move using the "Remove" button.

These requests have been tested thoroughly using Postman to ensure correct functionality. Error handling ensures proper HTTP status codes (e.g., 200 for success, 404 for not found) are returned for each request.

## Requests & DOM Integration:
Fetch requests on the frontend dynamically interact with the REST API:
- **GET Requests:** Populate the DOM by fetching data from the backend and rendering it in a table. Loops are used to iterate through the response data, creating rows dynamically.
- **POST Requests:** Send new move data to the backend when a game concludes, and update the DOM to reflect the added move.
- **PUT Requests:** Allow users to edit move details, such as changing the evaluation or marking a move as "played."
- **DELETE Requests:** Dynamically remove moves from the database and the DOM.

The backend uses Flask_SQLAlchemy as an ORM to manage database queries, abstracting SQL operations for ease of development.

## Algorithmic Requests:
My `_CRUD` class in the backend API handles POST, PUT, and DELETE requests:
- The **POST method** takes move data from the frontend, validates it, and adds it to the database. Duplicate checks ensure data integrity.
- The **PUT method** allows partial updates to entries, such as changing the evaluation or marking a move as "played."
- The **DELETE method** removes a move from the database based on its unique ID, returning an appropriate success or error message.

Each method parses incoming request data, performs validation, interacts with the database, and returns a JSON response with a status code.

## Call to Algorithm Requests:
Frontend JavaScript functions handle the integration of the REST API with the UI:
- A **POST request** is triggered when the user finishes a game or uploads a PGN file. This adds new moves to the database and dynamically updates the table.
- **GET requests** populate the moves table on page load, displaying all saved moves.
- **PUT requests** allow users to mark moves as "played" or update their evaluations. These changes are reflected immediately in the DOM.
- **DELETE requests** remove moves from the database and dynamically update the table to reflect the changes.

For example, the "Mark as Played" button sends a PUT request to the API. Once the request is successful, the move is added to the "Played Moves" list and removed from the available moves table.

## Summary:
This feature provided valuable experience in building and integrating a full-stack application:
- **Backend:** Developed a RESTful API with robust CRUD operations and integrated it with a database.
- **Frontend:** Designed a dynamic interface that allows users to manage their chess gameplay data effectively.
- **Testing:** Used Postman for testing API endpoints and ensured smooth interaction between the backend and frontend.

This project helped me better understand the complexities of full-stack development, especially in managing state and ensuring seamless communication between the frontend and backend. I'm excited to refine and expand this feature in future sprints.



