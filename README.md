# OGBV-Lexicon

For this project, **OGBV Lexicons** a collection of words and phrases associated with online gender-based violence (OGBV) are gathered and stored to create a dataset. These lexicons play a critical role in detecting and analyzing OGBV-related content. In my implementation, I've chosen to store these terms in a database, as illustrated in the schema screenshot below. Each article, comment, or chatbot message is evaluated and assigned a boolean value (`ogbv_flag`) based on whether it is related to OGBV. This is reflected in the schema by the `ogbv_flag` field, which indicates the status of the content.

You can also view the shareable schema design [here](https://app.quickdatabasediagrams.com/#/d/7jIX45).

![schema](https://github.com/user-attachments/assets/48116645-f636-4ef4-99b5-641d5cc18274)

---

## Technologies and Tools Used

### Wireframe Design

- **Figma**: I utilized Figma to design the wireframe, which facilitates easy sharing and collaboration. This ensures that all stakeholders can review and provide feedback on the design before development is commenced. Some design elements, such as the logo, were created using Photoshop and can be found in the assets directory. The wireframe visualizes the interface of the repository, showing how it will look and function, as depicted in the diagram below.

You can also view the shareable Figma design [here](https://www.figma.com/design/elChN4usl0oCrQL7lr8GiE/Online-Gender-Based-Violence?node-id=0-1&t=n9Buae8R5OejGhdG-1).

![Figma Design](https://github.com/user-attachments/assets/186fc861-c7a7-42f8-8bd4-066ba05847e0)

---

### Frontend Implementation

- **React.js**: For the frontend, I chose to use React.js due to its component-based architecture, which allows for the creation of reusable UI components. This helps to maintain a consistent look and feel across the platform. The React components will be designed based on the wireframe, including components for displaying articles under specific categories, implementing search functionality, and filtering content by language or term using the **OGBV_Lexicons** table.

---

### Backend Implementation

- **Django**: For the backend, I chose Django due to its robust ORM and seamless integration with PostgreSQL. Additionally, Django provides built-in admin functionality, which simplifies managing the repository of terms.
  
- **PostgreSQL**: PostgreSQL is selected as the database management platform due to its support for complex queries, scalability, and compatibility with Django.

Django will be used to build the backend API, with Django ORM interacting with PostgreSQL to store and retrieve OGBV terms in the **OGBV_Lexicons** table. RESTful APIs will be developed to expose endpoints for CRUD operations on the repository.

#### AI and NLP Implementation for Backend

**Data Preprocessing**

- The text from a given dataset is split into individual tokens (words or phrases). These tokens are then converted to lowercase, punctuation is removed, and stemming is applied to reduce words to their root forms. This process helps improve the consistency of the dataset. Additionally, common words like "and," "the," "is," etc., which do not add significant meaning to the text, are removed.

**Feature Extraction**

- During feature extraction with supervised learning models, the content from an article, comment, or message is compared with a dataset that includes examples of text flagged as OGBV-related and non-OGBV-related. For each submission, a prediction is made where the trained model determines whether the content is related to OGBV. A probability threshold is then applied to decide if the content should be flagged as OGBV-related (`ogbv_flag = TRUE`).

**Search Functionality**

- During the search, there is a prioritization of results containing terms from the **OGBV_Lexicons** table, ensuring that relevant content is highlighted.

**Continuous Learning and Model Updating**

- When an article, comment, or message is submitted, it undergoes NLP processing, and the AI model assesses whether the content includes OGBV-related language. If detected, the `ogbv_flag` is set to TRUE. Additionally, chatbot messages and user inputs are analyzed in real-time or batch processing to detect any OGBV-related language, continuously refining the model's accuracy.

---

### Containerization and Deployment

- **Docker**: While optional, I recommend Docker for ensuring consistency across development, testing, and production environments. It enables packaging the application with all dependencies, simplifying deployment across different platforms.
  
- **AWS**: I recommend AWS for deployment due to its reliability, scalability, and comprehensive suite of services, such as RDS for managing PostgreSQL databases and ECS for container orchestration.

Docker will be used to containerize the application, ensuring seamless operation across various environments. AWS will handle deployment, with ECS managing Docker containers and RDS hosting the PostgreSQL database.

---

**Designed and compiled by Matembu Emmanuel Dominic**
