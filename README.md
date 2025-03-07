# Google Contacts/People API Integration

Spring Boot application that integrates with Google Contacts (People) API to perform CRUD operations on contacts using a modern REST API architecture with a responsive frontend.

## Overview
This application allows users to:
- Authenticate with their Google account
- View their Google contacts list
- Add new contacts
- Edit existing contacts
- Delete contacts

## Prerequisites
- Java 17 or higher
- Maven
- Google Cloud account
- Google Cloud project with People API enabled

## Google API Setup

### Create a Google Cloud Project:
1. Go to Google Cloud Console
2. Click "Create Project" and follow the steps
3. Note down your Project ID

### Enable the People API:
1. In your project, go to "APIs & Services" > "Library"
2. Search for "Google People API"
3. Click "Enable"

### Configure OAuth 2.0 Credentials:
1. Go to "APIs & Services" > "Credentials"
2. Click "Create Credentials" > "OAuth 2.0 Client ID"
3. Select "Web Application"
4. Set Authorized redirect URIs to include:
   - http://localhost:8080/login/oauth2/code/google
5. Copy the Client ID and Client Secret

### Configure OAuth Consent Screen:
1. Go to "APIs & Services" > "OAuth consent screen"
2. Choose "External" user type
3. Fill in the required information
4. Add the following scopes:
   - https://www.googleapis.com/auth/contacts
   - https://www.googleapis.com/auth/contacts.readonly

## Project Structure
```
src/
├── main/
│   ├── java/
│   │   └── com/
│   │       └── sandiego/
│   │           └── googlecontacts/
│   │               └── integration/
│   │                   ├── Application.java
│   │                   ├── config/
│   │                   │   └── SecurityConfig.java
│   │                   ├── controller/
│   │                   │   ├── CustomErrorController.java
│   │                   │   ├── GoogleContactsController.java
│   │                   │   └── HomeController.java
│   │                   └── service/
│   │                       └── GoogleContactsService.java
│   └── resources/
│       ├── templates/
│       │   ├── contacts.html
│       │   ├── error.html
│       │   └── login.html
│       └── application.properties
```

## Technologies Used
- Spring Boot
- Spring Security with OAuth2
- Google People API
- HTML5
- JavaScript (ES6+)
- Tailwind CSS
- Phosphor Icons
- Maven
- Java 17

## Features

### Authentication
- OAuth2 integration with Google
- Secure login system
- Session management

### Contact Management
- List all contacts
- Add new contacts
- Edit existing contacts
- Delete contacts

### User Interface
- Modern, responsive design using Tailwind CSS
- Interactive modals for CRUD operations
- Real-time form validation
- Error handling and feedback

## Configuration
Update `application.properties`:
```properties
spring.security.oauth2.client.registration.google.client-id=your-client-id
spring.security.oauth2.client.registration.google.client-secret=your-client-secret
spring.security.oauth2.client.registration.google.scope=https://www.googleapis.com/auth/contacts,https://www.googleapis.com/auth/contacts.readonly
```

## Running the Application
1. Clone the repository
2. Configure Google API credentials in `application.properties`
3. Run the application:
   ./mvnw spring-boot:run
4. Access the application at http://localhost:8080

## Security Considerations
- OAuth2 security configuration
- CSRF protection enabled
- Secure session management
- Scope-based authorization

## Error Handling
The application includes comprehensive error handling for:
- API rate limiting
- Network issues
- Authentication failures
- Invalid contact data

## Implementation Challenges

### Update Operation Challenges
- Handling resource versioning required by Google People API
- Managing partial updates while preserving existing contact data
- Synchronizing local state with Google's server state
- Dealing with concurrent modifications
- Preserving field metadata during updates
- Implementing proper error handling for failed updates

### Delete Operation Challenges
- Implementing proper error handling for non-existent contacts
- Managing batch delete operations
- Handling deletion confirmation flows
- Ensuring proper cleanup of related contact data

## Development Process

### Initial Setup
- Project creation with Spring Initializr
- Configuration of OAuth2 security
- Integration with Google People API

### Backend Development
- Implementation of service layer
- REST API controller development
- Google People API integration

### Frontend Development
- Modern UI with Tailwind CSS
- Interactive form handling with JavaScript
- Error handling and user feedback

### Testing and Refinement
- Unit testing
- Integration testing
- UI/UX improvements
