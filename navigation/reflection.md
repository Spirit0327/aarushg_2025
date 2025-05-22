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


# FULL STACK BLOG - AARUSH



## Executive Summary:
For this sprint, I developed a full-stack feature that stores, manages, and analyzes chess moves and their evaluations. I created a backend database to store chess moves, built a RESTful API for CRUD operations, and integrated the backend with a frontend interface. Users can interact with this feature on the analysis page, where they can view, add, update, and delete chess moves dynamically.

## Team Purpose:
Our team is working on a chess-based social media platform where users can discuss chess strategies, analyze their games, and learn from others. My feature complements this vision by providing users with the tools to analyze their games, save key moves, and review them later for improvement and discussion.

## Individual Feature:
My feature focuses on enabling users to store and manage their chess moves and evaluations. Users can upload PGN files to analyze moves and save these moves to a database for later use. The manager page lets users perform CRUD operations, providing full control over their stored data. This feature enhances the user experience by allowing in-depth review and customization of their chess gameplay data.

Key functionalities include:
- **POST:** Adds a new evaluation to the database with the move number, move, and evaluation score.
```python
def post(self):
    data = request.get_json()
    if not data or 'evaluation' not in data or 'move' not in data or 'move_number' not in data:
        return {'message': 'Move data is required.'}, 400

    evaluation = Evaluation(
        evaluation=data.get('evaluation'),
        move=data.get('move'),
        move_number=data.get('move_number')
    )

    try:
        evaluation.create()
        return jsonify(evaluation.read()), 201
    except Exception as e:
        return {'message': f'Error saving evaluation: {e}'}, 500
 ```
  ```js
 // Add new move
    addMoveForm.addEventListener('submit', async (event) => {
        event.preventDefault();
        const moveNumber = document.querySelector('#move-number').value;
        const move = document.querySelector('#move').value;
        const evaluation = document.querySelector('#evaluation').value;

        try {
            const response = await fetch(pythonURI, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({
                    move_number: parseInt(moveNumber, 10),
                    move: move,
                    evaluation: parseFloat(evaluation)
                })
            });

            if (response.ok) {
                fetchMoves(); // Refresh the table
                addMoveForm.reset();
            } else {
                console.error('Failed to add move.');
            }
        } catch (error) {
            console.error('Error adding move:', error);
        }
    });
```
- **GET:** Displays all saved moves in a dynamic table on the analysis page.
```python
def get(self):
    all_evaluations = Evaluation.query.all()
    return jsonify([evaluation.read() for evaluation in all_evaluations])
```
- **PUT:** Updates the evaluation or status of a move (e.g., marking it as "played").
```python
def put(self):
    data = request.get_json()
    if not data or 'id' not in data:
        return {'message': 'ID is required to update the evaluation'}, 400

    evaluation = Evaluation.query.get(data['id'])
    if not evaluation:
        return {'message': 'Evaluation not found'}, 404

    try:
        evaluation.update(data)
        return jsonify(evaluation.read())
    except Exception as e:
        return {'message': f'Error updating evaluation: {e}'}, 500
```
```js
    async function markAsPlayed(id, move) {
        try {
            const response = await fetch(pythonURI, {
                method: 'PUT',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ id: id, played: true }),
            });

            if (response.ok) {
                const playedMove = document.createElement('li');
                playedMove.textContent = move;
                playedMovesList.appendChild(playedMove);
                fetchMoves(); // Refresh the table
            } else {
                console.error('Failed to mark move as played.');
            }
        } catch (error) {
            console.error('Error marking move as played:', error);
        }
    }
```
- **DELETE:** Removes moves from the database when no longer needed.
```python
def delete(self):
    data = request.get_json()
    if not data or 'id' not in data:
        return {'message': 'ID is required for deletion'}, 400

    evaluation = Evaluation.query.get(data['id'])
    if not evaluation:
        return {'message': 'Evaluation not found'}, 404

    try:
        evaluation.delete()
        return {'message': 'Evaluation deleted successfully'}, 200
    except Exception as e:
        return {'message': f'Error deleting evaluation: {e}'}, 500
```
```js
    // Remove move
    async function removeMove(id) {
        try {
            const response = await fetch(pythonURI, {
                method: 'DELETE',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ id: id }),
            });

            if (response.ok) {
                fetchMoves(); // Refresh the table
            } else {
                console.error('Failed to remove move.');
            }
        } catch (error) {
            console.error('Error removing move:', error);
        }
    }
```
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
- A **POST request** is triggered when the user adds a move played in the game according to provided pgn file.
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

# FINAL REVIEW BLOG
## 5 Achievements 
- Implemented Stockfish Analysis for Evaluation into main project (Collaboration with Nikhil M)

- Created Evaluation of Chess PGN files for use of viewing played moves

- Created Evaluation API with CRUD for user interaction to add, delete, change status, and view moves played

- Learnt Deployment process to set up pawnsy.stu.nighthawkcodingsociety.com with Vasanth

- Created fully functional user-input based interactive chess board with arrow keys to switch between moves for convenience

## SELF GRADING
 - I believe that my coding and technical skills this trimester were overall improved through the amount of notes and learning I went through to properly understand the material we were meant to learn. I learnt to create my own CRUD features while connecting it to other features and learning the use of API and model files. Resolving errors with databases also helped me gain mastery over the db_init, db_backup, and db_restore commands. A huge improvement that could be made is the amoint of time it takes me to learn this material, I felt I was lagging behind in terms of understanding and this overall made it challenging to keep up with the projects. In the end I was able to make a full functioning feature to present at N@TM and recieved feeback as will be shown below. 
 - Being the deployment admin, for Pawnsy’s deployment, we used AWS EC2 for hosting and Route 53 to configure our domain and subdomains. To secure the site, we added SSL certificates with Certbot and enabled HTTPS using sudo certbot --nginx.
We deployed the application using Docker, defining its setup in a Dockerfile and configuring services in docker-compose.yml. The app was built and launched with docker-compose build and docker-compose up -d. We verified deployment by checking running services with docker ps and testing the web server with curl localhost:8401.
To keep the site updated, we pulled the latest changes from GitHub, rebuilt the Docker container, and restarted it. We also ensured reliable database management using db_backup, db_init, and db_restore for backups and recovery.
I also kept up to date with checking if our data shows on the deployment with the sqlite3 user_management.db command then .schema + SELECT *FROM *insert name of table for example: pgn*; this kept us on track overall.
- My presentation skills the whole trimester were on point, I did gain approval multiple times from Mr.Mortensen as I used correct vocabulary and spoke with confidence as I rehearsed.
- 5 Things Done Over 12 Weeks - 4.7/5
- Full Stack Project Demo & Feedback 1.9/2
- Project Feature Blog (CPT/FRQ Language) - 0.9/1
- MCQ Performance - 0.8/1
- Retrospective & Reflection - 0.4/0.5
- Self-Grade Justification - 0.5/0.5
- Total: 9.2



## IMPROVEMENTS
- Improve code documentation with clear comments and adhere to better programming standards.  
- Avoid bypassing pre-existing systems for short-term gains, as it often leads to long-term complications.  
- Adopt a more modular approach—many standalone endpoints could have been grouped into a separate API file instead of being left in `main.py`, which created a disorganized developer experience.  
- Improve effort estimation to prevent tasks, such as deployment setup, from taking longer than expected and affecting sprint efficiency.  
- Plan API interactions and dependencies earlier in the sprint to prevent last-minute integration challenges.  
- Break down large features into smaller, more manageable components to enhance efficiency and debugging.  
- Improve collaboration by distributing work more effectively—rather than assigning an entire section to one teammate, divide it into smaller, more manageable tasks.
## FOR FUTURE:
- **Project Management:** Improve estimation and planning to avoid last-minute rushes and ensure timely completion of tasks
- **Code Quality:** Enhance code organization, documentation, and adherence to best practices
- **Enhance User convenience based on feedback below.**

![Feedback Image]({{site.baseurl}}/images/feeback1.png)

## USERS COMMENTED 22 RESPONSES: 
- It was really fun
- Very clean looking with nice features
- i liked how you guys incorporated stockfish chess engine into your website and the user experience was really simple and easy to use!
- This website had lots of impressive features and the pictures of the chess game after playing were a great touch to the website. I honestly had no constructive criticism as the website was very well made.
- I loved the chess feature and how you had too lose to play it
- The pawns website can help the user gain a better experience when playing chess such as it can rate each movement.
- Show something other than the chess feature.
- Amazing website and helps people with chess
- It was great, I rlly liked how well designed this site was
- The chess analyzer looked really cool. As a chess player being able to analyze your moves, skill rating, ranking, and power bot all helps me to improve my chess skill. Each moves shows highlighted in yellow box made me happy because it was cool. i think better css styling would be great
- Add an edit feature for chess moves. Very cool idea to download a file and analyze moves based off of a png file!
- UI is a bit buggy and also the ELO selection could be a more elegant UI
- Loved your games and features.
- Very nice UI, I like your features they make a lot of sense! You mentioned there wasn’t token required so maybe consider adding that?
- The website’s functionality is really cool. I like how I can choose the elo level and review my moves and analyze them. I don’t know if you had this, but it would be cool if when I analyze my moves, it gives me a rating on how I did and if it was a good or bad move
- Great project overall, I‘m sure it takes a lot time and effort to code an actual chess bot. I also like how all the moves get recorded and how there is a leaderboard. The only thing I was wondering about was whether or not the bot is programmed to play strategically to play the smartest moves, or if - it simply does random moves. Other than that, great job!
- awesome
- Explain a bit more than just the fact that you can move the pieces around.
- nice site
- i liked how you guys incorporated stockfish chess engine into your website and how the user experience is very simple and easy to to use and navigate. one thing u would improve is making the website have a more consistent theme.
- It was really good and it was interesting to learn about chess
- I would have liked more color in the website but liked the functionality and explanation of how the website works

# Project Feature Writeup: Chess Game Analysis and Move Management

**Chess Game Analysis and Move Management (CPT REQUIREMENTS)**

---

### 1. Program Purpose and Function
The primary purpose of this program is to help chess players analyze and manage their games in real time. Users upload a Portable Game Notation (PGN) file, navigate through the moves, and receive evaluation data—such as score differences and best moves—from the Stockfish chess engine. This feedback helps players identify mistakes, improvements, and notable moves (e.g., “Brilliant,” “Inaccurate,” “Blunder”).

**Input:**  
- A PGN file containing the recorded moves of a chess game.  
- User actions (e.g., navigating moves, adding new moves).

**Output:**  
- A dynamically updated chessboard.  
- A move table displaying evaluation details (score, best move, status).  
- Success or error messages for CRUD operations (e.g., “Move added successfully” or “Invalid move”).

By integrating the board display, engine analysis, and move-management system, the program allows users to explore each move’s impact and store personalized notes or custom moves.

---

### 2. Data Abstraction
A central **data structure** (such as an SQLAlchemy model) manages the moves and their evaluations. Each move record includes fields like:
- `move_id` (unique identifier)
- `notation` (e.g., “Nf3”)
- `score` (evaluation in pawns)
- `status` (e.g., “Excellent,” “Mistake”)
- `played` (boolean indicating if the move is part of the official game)

This abstraction **manages complexity** by grouping all relevant information into a single, accessible structure. Instead of scattering move details across multiple variables, the program consistently stores, retrieves, and updates move information.

**Sample Code Excerpt (Data Structure Definition):**
```python
# Example of how moves might be stored in a database model
class Move(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    notation = db.Column(db.String(10))
    score = db.Column(db.Float)
    status = db.Column(db.String(20))
    played = db.Column(db.Boolean, default=False)

    def __init__(self, notation, score, status, played=False):
        self.notation = notation
        self.score = score
        self.status = status
        self.played = played
```
A core procedure, evaluate_position, processes a FEN string (representing the current board state) and returns an evaluation object containing the score, best move, and status. This function exemplifies input, output, selection, and iteration:

Input: Accepts a FEN string and an optional previous score.
Iteration: Runs the Stockfish engine for a set depth to generate a score and determine the best move.
Selection: Compares the current score with the previous score to classify the move (e.g., “Brilliant” for a significant positive difference, “Blunder” for a significant negative difference).
Output: Returns a dictionary with keys score, best_move, and status.

Algorithm Implementation (Selection, Iteration, Sequencing)
Sequencing: On clicking “Next Move,” the program retrieves the subsequent move from the PGN, updates the chessboard, and calls evaluate_position to update the evaluation.
Selection: The procedure compares score differences to determine and label the move’s status.
Iteration: The Stockfish engine internally iterates to calculate the best move, while the program iterates through moves to display and update the move table.
These constructs ensure a logical flow from user input (e.g., button click) to the final output (updated board and evaluation details).

Input and Output Examples
User Uploads a PGN

Input: PGN text containing moves (e.g., 1. e4 e5 2. Nf3 Nc6 ...)
Output: The board displays the initial position, and the moves table lists the moves from the PGN.
User Navigates to Move #5


Input: Entering details (e.g., notation = “d4”, score = 0.9) via a form.
Output: The new move is added to the moves table, the database is updated, and a confirmation message (e.g., “Move added successfully!”) is shown.

# MCQ REFLECTION
![Feedback Image]({{site.baseurl}}/images/MCQ1.png)
![Feedback Image]({{site.baseurl}}/images/Feedback2.png)
- Q64 + Q65: Forgot to select 2nd answer option
- Q56: My error was in not noticing that Version I calls GetPrediction once per idList element, while Version II calls it twice (plus an extra call), leading to longer execution time.
- Q50: Algorithm 3 is within reasonable time, meaning it should also count as the correct answer here
- Q43: It is possible to have redundant routing in both configurations. In configuration II, some possible routes between computers Q and V include Q-S-V, Q-R-T-V, and Q-P-T-V.
- Q37: Incorrect. This code segment will draw four line segments: one with endpoints (2, 6) and (6, 6), one with endpoints (2, 6) and (4, 4), one with endpoints (2, 6) and (2, 2), and one with endpoints (2, 6) and (0, 0).
- Q28: Code segment I assigns the initial value of alpha to temp, then assigns the initial value of beta to alpha. The initial value of alpha, which has been stored in temp, is then assigned to beta. Therefore, the values of alpha and beta are interchanged. Code segment II assigns the initial value of alpha to temp, then assigns the initial value of alpha to beta. The initial value of alpha, which has been stored in temp, is then assigned to beta. Therefore, both variables are assigned the initial value of alpha. Code segment III assigns the initial value of beta to temp, then assigns the initial value of alpha to beta. The initial value of beta, which has been stored in temp, is then assigned to alpha. Therefore, the values of alpha and beta are interchanged.
- Q23: The flowchart is supposed to set available to true whenever weekday is true and miles is less than 20, and set available to false otherwise. This code statement provides the same functionality.
- Q10: This code segment should initially set costs to 6 (the cheapest possible ticket price), then increases cost by 2 for people whose age is greater than 12. Regardless of the person’s age, cost is increased by 2 for people going on a guided tour.

# Project Reflection & Future Directions

## Reflection on the Project
The project showcased a robust backend and smooth API integration. Key features—such as incorporating the Stockfish chess engine for move analysis, implementing full CRUD operations for game management, and securing user authentication—formed a strong foundation for our dynamic chess platform. Using Docker-Compose for deployment and Amazon S3 for storage enhanced scalability, while the Stockfish evaluation module provided valuable insights for users to improve their gameplay.

## Areas for Enhancement
While the project has many strengths, there are several areas I plan to improve:
- **User Interface:** Refine the overall design and interaction flow for a more engaging experience.
- **Database Efficiency:** Optimize queries and improve indexing to handle higher loads efficiently.
- **Testing Coverage:** Increase automated testing with unit and integration tests (using tools like Jest for JavaScript and PyTest for Python) to catch issues early and boost reliability.

## Future Development Steps
Moving forward, I intend to:
- Develop an advanced analysis mode that offers multi-line evaluations and deeper insights.
- Introduce real-time features, such as WebSocket communication, to support live game tracking and multiplayer interactions.
- Enhance security through improved deployment practices.
- Streamline the deployment process with greater automation.
- Explore advanced database solutions (e.g., Redis) for faster query performance and reduced latency.

## Personal Growth & Process Improvements
Reflecting on my work:
- **Technical Contributions:** I effectively integrated core features and utilized debugging tools like Postman and browser Inspect tools to ensure smooth communication between the frontend and backend. Leading the deployment phase gave me practical experience with Docker-Compose and cloud storage solutions.
- **Documentation:** I plan to improve code documentation using tools like Sphinx for Python and JSDoc for JavaScript, along with structured README files for better maintainability.
- **Project Management:** I aim to refine my workflow by breaking tasks into smaller milestones and leveraging tools like Jira or Trello to track progress more effectively.
- **Team Collaboration:** Fostering regular peer code reviews and structured communication will further enhance team dynamics.
- **Code Organization:** I intend to adopt a more modular, blueprint-based structure in Flask for cleaner code organization.
- **Testing:** Expanding the testing framework with comprehensive unit tests and exploring end-to-end testing options, such as Selenium, is a key focus area.

Overall, this project has been a significant learning experience, and these future steps will help me build even more robust, scalable, and user-friendly applications.

## N@TM INTEREST:
 - I took a look at Scrum Master Kiruthic Selvakumar's group, this project had a lot to do with hotels and convenience for users. I especially liked using the lodging listings feature which definetly seemed very useful, the layout and design of the page was professional and inviting making me enjoy the experience overall. Another group I looked at was Vibha Mandayam's group from Period 2. Their website focused on gift shopping with a feature to search for gifts for my friends and family, you could view the reviews on the gift and add it to your shopping cart for later purchase. There was also a holiday calendar which I loved to use as it could mark all the dates on which I had an event coming up and I could see this easily as it was bright in color.
 ![Feedback Image]({{site.baseurl}}/images/extreme.png)


 I went over my N@TM Demo with Arnav Nadar, a student in AP CSA this year, similar to how some students reviewed with Ms.Pataki. The feedback I recieved was valuable as it enhanced my presentation skills overall. He helped me to showcase my feature in an enticing way and show the continuity between features to overall demonstrate the use of my website. Kudos to him!
  ![Feedback Image]({{site.baseurl}}/images/arnav.png)



# Reflection on My AP CSP Practice MCQ Performance
![Feedback Image]({{site.baseurl}}/images/AP PRACTICE.png)
After completing the AP Computer Science Principles practice multiple-choice exam, I was able to better understand my current strengths and weaknesses based on the skill-by-skill breakdown. **Score: 59/70**

## What I Did Well:
I performed strongly on most units that involved understanding and interpreting program functionality. For example, I scored:
- **100%** on topics like **Random Values (3.15)**, **Developing Algorithms (3.9)**, **The Internet (4.1)**, and **Safe Computing (5.6)**.
- My score on **Iteration (3.8)** was also high at **91%**, showing that I’m comfortable working with loops and repeating patterns in code.
- I answered **all questions** correctly on **Conditionals (3.6)** and **Nested Conditionals (3.7)**, indicating a strong grasp of logical decision-making in Python programs.

## What I Struggled With:
- I struggled the most with **Binary Search (3.11)**, where I scored **0%**, indicating that I may need to revisit how binary search works conceptually and in code.
- **Boolean Expressions (3.5)** and **Data Abstraction (3.2)** also showed lower scores at **50%** and **N/A**, respectively.
- Some difficulty came from questions that involved evaluating or comparing algorithms based on efficiency or output, especially in problems with dense visuals or multiple-step logic.

## How I Plan to Improve:
To address these gaps, I plan to:
- **Rewatch videos and review notes** for Binary Search and Boolean logic, focusing on how binary search narrows search space in sorted lists and how boolean operators work together.
- Practice identifying boolean conditions and rewriting logic using De Morgan’s Law to reinforce expression simplification.
- Use **practice problems** from CodeHS or College Board’s AP CSP question bank to simulate MCQ-style formats, especially ones that require interpreting conditionals or comparing code outputs.
- Work with **interactive tools** or flashcards to reinforce key terms and logic symbols (e.g., `and`, `or`, `not`) in different contexts.
- For algorithm efficiency questions, I’ll review **visual walkthroughs** and step-count analysis so I can more easily determine time complexity at a glance.

## Final Thoughts:
This practice exam was a helpful checkpoint. While I feel confident in most coding-related logic and structure, I now know exactly which areas to focus on in my review. I’m aiming for more consistency across all topics before the AP exam. With targeted review and hands-on problem solving, I’m confident I’ll be fully prepared on exam day.

<a href="https://spirit0327.github.io/aarushg_2025/divide/" style="background-color: #4CAF50; color: white; padding: 10px 20px; text-align: center; text-decoration: none; display: inline-block; border-radius: 8px; font-weight: bold;">Go to Divide Homework</a>

<a href="https://spirit0327.github.io/aarushg_2025/binary/" style="background-color: #4CAF50; color: white; padding: 10px 20px; text-align: center; text-decoration: none; display: inline-block; border-radius: 8px; font-weight: bold;">Go to Binary Search Homework</a>

<a href="https://spirit0327.github.io/aarushg_2025/algorithm/" style="background-color: #4CAF50; color: white; padding: 10px 20px; text-align: center; text-decoration: none; display: inline-block; border-radius: 8px; font-weight: bold;">Go to Algorithm Homework</a>

<a href="https://spirit0327.github.io/aarushg_2025/lists/" style="background-color: #4CAF50; color: white; padding: 10px 20px; text-align: center; text-decoration: none; display: inline-block; border-radius: 8px; font-weight: bold;">Go to Lists and Filtering Homework</a>

<a href="https://github.com/Spirit0327/aarushg_2025/issues/10#issue-2957725549" style="background-color: #4CAF50; color: white; padding: 10px 20px; text-align: center; text-decoration: none; display: inline-block; border-radius: 8px; font-weight: bold;">Go to Crowdsourcing Homework</a>

<a href="https://github.com/Spirit0327/aarushg_2025/issues/9#issue-2955052416" style="background-color: #4CAF50; color: white; padding: 10px 20px; text-align: center; text-decoration: none; display: inline-block; border-radius: 8px; font-weight: bold;">Go to Computing Bias Homework</a>

<a href="https://github.com/Spirit0327/aarushg_2025/issues/12#issue-2970057862" style="background-color: #4CAF50; color: white; padding: 10px 20px; text-align: center; text-decoration: none; display: inline-block; border-radius: 8px; font-weight: bold;">Go to Safe Computing Homework</a>

<a href="https://github.com/Spirit0327/aarushg_2025/issues/11#issue-2968322226" style="background-color: #4CAF50; color: white; padding: 10px 20px; text-align: center; text-decoration: none; display: inline-block; border-radius: 8px; font-weight: bold;">Go to Legal and Ethical Concerns Homework</a>

<a href="https://spirit0327.github.io/aarushg_2025/big/" style="background-color: #4CAF50; color: white; padding: 10px 20px; text-align: center; text-decoration: none; display: inline-block; border-radius: 8px; font-weight: bold;">Go to Big O Notation Homework</a>


#  AP Computer Science Principles Study Plan
**Goal:** Master key topics and practice all question types before the AP CSP Exam.

##  Week 1: April 23 – April 28 (Foundation + Key Topics)

###  Tuesday (April 22)
- Review MCQ performance dashboard 
- Reflect on weak areas: Boolean Expressions, Lists, Binary Search
- Finish `PPR` + upload to AP Digital Portfolio

###  Wednesday (April 23)
- **Practice**: Boolean Expressions & DeMorgan's Law (Unit 3.5)
- **Practice**: Conditionals & Nested Conditionals (3.6–3.7)
- Do 10 MCQs from CodeHS or CollegeBoard

###  Thursday (April 24)
- **Focus:** Lists & Binary Search (3.10–3.11)
- Practice writing code with `append`, `in`, and `set`
- Relearn Binary Search visually and through simulation

###  Friday (April 25)
- **Practice:** Time Complexity (Big-O) & Algorithms (3.8–3.9)
- Create or review notebook with O(1), O(log n), O(n), O(n²) examples
- Do 1 Free Response style question on algorithm tracing

###  Weekend (April 26–27)
- Complete full 30-question AP MCQ practice set
- Write a reflection blog on what was most challenging
- Light review of Internet, Data, Digital Divide (Units 2 & 4)

---

##  Week 2: April 29 – May 7 (Practice, Application, Full Review)

###  Monday (April 28)
- **Practice:** Data Abstraction (Lists + Algorithms)
- Do 5 MCQs and 1 Create Task-style reflection on your project

###  Tuesday (April 30)
- **Practice:** Simulations, Random Values, and Libraries (3.14–3.16)
- Go through examples that involve randomness or simulation logic

###  Wednesday (May 1)
- **Review**: Safe Computing, Computing Bias, Legal & Ethical Effects (Unit 5)
- Flashcards: Types of computing harms, ethical implications

###  Thursday (May 2)
- **Timed Practice:** Full MCQ Section (40 Questions in 75 min)
- Review answers and mistakes in a markdown cell

###  Friday (May 3)
- **Practice**: Algorithmic Efficiency + Undecidable Problems (3.17–3.18)
- Review charts, visual flow logic

###  Weekend (May 4–5)
- **Simulated AP Exam Weekend**
  -  Saturday: Take full-length AP Practice Exam (MCQ + FRQ)
  - Sunday: Go over Create Task details + Review all submissions

###  Monday (May 6)
- **Last Review**: Focused notes, “cheat sheet” creation
- Go over most missed topics again (Lists, Binary Search, Conditionals)

###  Tuesday (May 7)
- Light review, flashcards, rest
- Get good sleep and confidence boost 

---

# Resources
- College Board AP Classroom (MCQs and FRQs)
- CodeHS CSP Practice
- Visual Algo (Binary Search, Sorting Simulators)
- Your own Jupyter notes + Create Task project
