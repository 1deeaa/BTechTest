# Hi there, Best of Luck

Hi PT Bukit Teknologi Digital team, thank you so much for moving me forward to learn more about this opportunity. Here are my answers to the technical test. Please help to review and feel free to let me know if you need any additional details. Thank you!
 
# How to read my test results:

## Manual:
1. Manual test cases are under testcases/manual folder
2. Manual test cases are separated based on each flows 

## Automation:
I prioritize API automation for business rules and integrations, and only automate the most critical E2E user journeys to keep the suite fast, stable, and maintainable. Below are the few example for the most of importances automation test cases:

# API Automation (Playwright) 

## From: Flow 0 - Login Tenant Resolution 
API: /user/who
Why automate:
- Critical auth logic
- Multi-tenant bugs are VERY expensive
Validations:
1. Correct tenant returned
2. Inactive tenant blocked
3. Multiple tenants handled correctly

## From: Flow 1 - Dynamic Form Submission
API: Form submission endpoint
Why automate:
- Backend must accept flexible schemas
- Prevents silent data corruption
Validations:
1. Payload matches form definition
2. Submission stored correctly
3. Images linked

## From: Flow 2 - Hazard Creation Triggers Tasks & Notifications
Why automate:
- Multi-service integration:
    - Safety Service
    - Workflow Service
    - Notification Service
- UI tests are unreliable for notifications
Validations:
1. Hazard created
2. Follow up task generated
3. PIC + area notifications created
4. Supervisor notified after resolution


# E2E Automation (Playwright) 

## From: Flow 0 - Login + Master Data Sync
Why automate: 
- Entry point to the entire system
- Breaks = nobody can use the app
Scenario:
1. Enter username
2. Complete Microsoft login (can be mocked)
3. Fetch /user/me
4. Download master data
5. Show progress bar
6. Show restart prompt
Assertions:
1. Login succeeds
2. Progress bar reaches 100%
3. Restart prompt appears
4. App usable after restart
Why Playwright fits:
1. UI + backend integration check

## From: Flow 1 - Submit Equipment Inspection Form (Dynamic Form)
Why automate:
- Dynamic form = high regression risk
- Form Builder changes often
- Validates form rendering + submission E2E
Scenario:
1. Open Equipment Inspection
2. Create new inspection
3. Fill dynamic fields (text, select, image)
4. Submit form
Assertions:
1. Fields rendered based on Form Code
2. Submission succeeds
3. Entry appears in submission list
Why Playwright fits:
1. Strong form interaction
2. File upload support

## From: Flow 2 - Follow up Task Submission by PIC
Why automate: 
- Cross feature critical path
- Involves permissions
- Business critical safety flow
Scenario:
1. User submits hazard
2. Login as PIC
3. Open follow up task
4. Submit resolution
Assertions:
1. Hazard created
2. Follow up task visible
3. Task completed successfully
Why Playwright fits:
1. E2E ownership flow