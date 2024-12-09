# University Partner Onboarding Process

process from start to finnish to onboard a university with minimal customizations

# Partner Application Spin up

### 1. Validating University Information

- University Name Field
  - Required
- University Acronym
  - Required
  - Unique
- Logo Image
  - Required

### 2. Generating University Site

- Posts University site model
  - post request to sanity to create a site named provided University name

### 3. Generating Home Page Layout

- Posts multiple University sections
  - post request to sanity to generate sections and return a list of their ID's

### 4. Generating Sanity Layout

- Posts University layout (page)
  - post request to sanity to create a page named home

### 5. Generating Sanity Template

- Put University layout (page)
  - PUT request to sanity to associate section ids to the home layout

### 6. Creating University Database

- POST University Database
  - Creates university database names provided university acronym
  - Generates from TEMPLATE
  - Adds listing of univertiy to MASTER databse table universities
    - includes name, acronym, created date, ect

### 7. Creating DNS Records

- Post Sub Domain to Vercel (Hosting Platform)
  - Generate SSL provided by vercel
  - POST request to Vercel to add university acronyms
    - uniAcronym.ednet.com
    - uniAcronym-student.ednet.com
    - uniAcronym-faculty.ednet.com
- POST DNS records to cloud flare to confirm newly created domain ownership

### 8. Creating Cart Management System

- POST request to AWS Dynimo DB to create required tables for cart management and auto clear of abandoned carts

### 9. Compiling Uni Information

    - dasdawdasdw

### 10. Registering Email Subdomain

    - kjsldkjdalskdja
