# POSTMAN-API-Testing

# Manual API Testing using Postman

This repo contains my practice work for learning API testing manually using Postman.

## Tools Used
- Node.js
- JSON Server
- Postman
- Chai Assertion
- JSONPath

## What I Practiced
- Created mock APIs using JSON Server (`employee.json`)
- Used Postman to test GET, POST, PUT, DELETE
- Validated:
  - Status code
  - Headers, cookies, response time
  - Response body, JSON fields
  - JSON Schema
- Wrote post-response test scripts using Chai (normal and arrow functions)
- Used JSONPath to check specific values

## Files
- `employee.json` – Mock API data
- `Employee data.postman_collection` – All Postman requests
- `PostMan-Post Response vadliation scripts` – Test scripts and notes

---

# Scripts & Variables in Postman

## Scripts in Postman

Today I explored how to use scripts in Postman to automate API workflows and validations.

### Script Types
- **Pre-request Scripts**: Run *before* a request is sent.
- **Post-response Scripts (Tests)**: Run *after* the response is received.

### Script Levels Applied
| Level      | Description                            |
|------------|----------------------------------------|
| Collection | Affects all requests in a collection   |
| Folder     | Affects requests inside the folder     |
| Request    | Affects only the specific request      |

## Variables in Postman

Postman supports various types of variables that help manage dynamic data across requests.

### Variable Types Practiced
| Type          | Description                                 | Created Using   |
|---------------|---------------------------------------------|-----------------|
| Global        | Available across all collections & requests | UI & Scripts    |
| Environment   | Specific to the active environment          | UI & Scripts    |
| Collection    | Scoped to a particular collection           | UI & Scripts    |
| Local         | Scoped to a single request                  | Script          |

---

## Variable Handling via Script
###  Setting Variablesin Pre-request Script
//local variables
pm.variables.set("url_local","http://localhost:3000");
//global variables
pm.globals.set("students_Global", "1");
//collection variable
pm.collectionVariables.set("students_collection", "2");
//environment variable
pm.environment.set("dev_qa_environment", "3");

## Deleting Variables in Post-response Script:
//local variables
pm.variables.unset("url_local",);
//global variables
pm.globals.unset("students_Global");
//Environment variables
pm.environment.unset("dev_qa_environment");
//collection variable
pm.collectionVariables.unset("students_collection","1");

## Validated Variable data and deleted variables.
•	Retrieved variable values in post-response scripts using the Postman `pm` API.
•	Validated the data of those variables to ensure they contain expected values.
•	Then deleted those variables within the same script to clean up after execution.
•	This ensures a clean testing environment and avoids conflicts between requests.

 ## Validated Variables in Post-response Script: 
console.log(pm.globals.get("students_Global"));
console.log(pm.collectionVariables.get("students_collection"));
console.log(pm.environment.get("dev_qa_environment"));
console.log(pm.variables.get("url_local"));

## Deleted Variables After Validation:
//local variables
pm.variables.unset("url_local",);
//global variables
pm.globals.unset("students_Global");
//Environment variables
pm.environment.unset("dev_qa_environment");
//collection variable
pm.collectionVariables.unset("students_collection","1");

## Summary:
• Understood the scope and lifetime of different variable types.
• Practiced dynamic value assignment and cleanup using scripts.
• Improved test control by managing variables in script logic.
----------

**API Chaining using Real-Time APIs**
  - Captured response body
  - Created and managed variables dynamically using pre-request and test scripts
  - Cleared variables post-response to maintain a clean test environment

## Pre-Request scripts for chaining APIS    
//random string to create unique user each time
var random=Math.random().toString(36).substring(2);

//variables
var useremail="jet"+random+"@gmail.com";
var username = "jet" + random;

//environment variables
pm.environment.set("user_env", useremail);
pm.environment.set("name_env", username);

## Post-Response scripts for chaining APIS
//to capture resposne body 
var jsonData=JSON.parse(responseBody);

//to extract id
pm.environment.set("userid_env",jsonData.id);

- **Authorization Implementation**
  - Applied authorization at both **collection** and **request** levels

#### Key Takeaways:
- Chaining APIs allows for end-to-end workflow simulation
- Dynamic variable management improves flexibility and efficiency
- Centralized authorization setup enhances security and reusability


# API Testing with Postman – Data-Driven Testing & Chaining

This repository contains a Postman project demonstrating real-world API testing using a live **Books API**. The focus is on **Data-Driven Testing**, **Chaining Requests**, and validating different API operations (POST, GET, DELETE).

## Features

- **Data-Driven Testing** using external files (JSON & CSV)
- **POST**, **GET**, and **DELETE** requests to interact with the Books API
- **Chaining**: Passing dynamic values (e.g., Book ID) between requests
- **Assertions & Validations** to verify response codes, body content, and headers
- **Organized Collections** and **Environment Variables** for reusability
---------------

# API Testing Practice with Postman & Spring Boot

This repository contains hands-on practice and learning exercises related to API testing using Postman, Spring Boot, Swagger, and cURL. It demonstrates practical knowledge of file upload APIs, various authentication mechanisms, and API documentation tools.

---

## Project Overview

### File Upload API – Setup & Execution
- Installed Java and set up a Spring Boot application using an executable JAR file.
- Ran a local Spring Boot server hosting file upload endpoints.
- Performed both **Single File Upload** and **Multiple File Upload** requests using Postman.
- Tested various file types to validate correct API upload behavior and error handling.

### Authentication Types Practiced in Postman
- No Authentication (No Auth)
- Basic Authentication
- Bearer Token Authentication
- API Key Authentication
- Digest Authentication
- OAuth 1.0 & OAuth 2.0
- Gained practical understanding of when and how to use each authentication type.
- Tested authentication workflows thoroughly using Postman.

### Swagger & cURL Exploration
- Explored Swagger API documentation to understand endpoint references and request/response schemas.
- Executed cURL commands directly in the terminal and within Postman.
- Practiced converting API requests between Postman format and cURL command line syntax.

---

## Tools & Technologies
- **Java** (JDK 11+)
- **Spring Boot** (for building and running the file upload API)
- **Postman** (API testing and automation)
- **Swagger** (API documentation)
- **cURL** (command line HTTP requests)

---

## How to Run

1. **Setup Java and Spring Boot:**
   - Ensure Java is installed and configured on your machine.
   - Run the Spring Boot application using the provided JAR file:
     ```bash
     java -jar file-upload-api.jar
     ```

2. **File Upload Testing:**
   - Open Postman and import the collection for file upload.
   - Execute Single and Multiple File Upload requests to `http://localhost:8080/upload`.
   - Test different file types and observe responses.

3. **Authentication Testing:**
   - Use Postman to test various authentication types on sample endpoints.
   - Configure authentication as per the request requirements.

4. **Swagger & cURL:**
   - Explore Swagger UI (if hosted) for API endpoint documentation.
   - Execute API calls via cURL commands in terminal or convert Postman requests to cURL.

---

## Notes
- This repository is for educational and practice purposes.
- File upload API endpoints are running locally; ensure the Spring Boot app is active before sending requests.
- Authentication examples cover a range of common mechanisms useful for real-world API testing.

---













