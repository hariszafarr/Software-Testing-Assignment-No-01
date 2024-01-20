# Software-Testing-Assignment-No-01
TEST CASES FOR BOOK STORE APPLICATION USING ROBOT FRAMEWORK:
TEST CASES FOR BOOK STORE APPLICATION USING ROBOT FRAMEWORK:

Firstly, make sure you have Robot Framework and SeleniumLibrary installed. 
You can install them using the following commands:
pip install robotframework
pip install robotframework-seleniumlibrary

Now, you can create a new Robot Framework test suite for your React application. 
Let's assume your test suite file is named `test_suite.robot`:
Settings
Library    SeleniumLibrary

Variables
${BASE_URL}    http://localhost:3000 

Test Cases :
Open Home Page
    Open Browser    ${BASE_URL}    browser=chrome
    Maximize Browser Window
    Title Should Be    Home
    Close Browser

Create Book
    Open Browser    ${BASE_URL}    browser=chrome
    Maximize Browser Window
    Click Element    
    Title Should Be    Create Book
    Close Browser

Show Book Details
    Open Browser    ${BASE_URL}    browser=chrome
    Maximize Browser Window
    Click Element    
    Title Should Be    Book Details
    # Add steps to verify book details
    Close Browser

Edit Book
    Open Browser    ${BASE_URL}    browser=chrome
    Maximize Browser Window
    Click Element   
    Title Should Be    Edit Book
    # Add steps to edit the book and save changes
    Close Browser

Delete Book
    Open Browser    ${BASE_URL}    browser=chrome
    Maximize Browser Window
    Click Element   
    Title Should Be    Delete Book
    # Add steps to confirm and delete the book
    Close Browser

Switch to Card View
    Open Browser    ${BASE_URL}    browser=${BROWSER}
    Maximize Browser Window
    Click Element    
    Page Should Contain Element    
    # Add additional checks for the card view if needed
    Close Browser

Switch to Table View
    Open Browser    ${BASE_URL}    browser=${BROWSER}
    Maximize Browser Window
    Click Element    
    Page Should Contain Element    
    # Add additional checks for the table view if needed
    Close Browser

Navigate to Create Book Page
    Open Browser    ${BASE_URL}    browser=${BROWSER}
    Maximize Browser Window
    Click Element    
    Title Should Be    Create Book
    Close Browser

Click on Add Book Icon
    Open Browser    ${BASE_URL}    browser=${BROWSER}
    Maximize Browser Window
    Click Element   
    Title Should Be    Create Book
    Close Browser

Open Create Books Page
    Open Browser    ${BASE_URL}/books/create    browser=${BROWSER}
    Maximize Browser Window
    Page Should Contain Element  
    Close Browser
Create Book - Valid Data
    Open Browser    ${BASE_URL}/books/create    browser=${BROWSER}
    Maximize Browser Window
    Input Text        Science
    Input Text        Saad
    Input Text        2022
    Click Element    
    Page Should Contain    Book Created successfully
    Location Should Be    ${BASE_URL}/
    Close Browser

Create Book - Empty Fields
    Open Browser    ${BASE_URL}/books/create    browser=${BROWSER}
    Maximize Browser Window
    Click Element    
    Page Should Contain    Error
    Close Browser

Create Book - Invalid Data
    Open Browser    ${BASE_URL}/books/create    browser=${BROWSER}
    Maximize Browser Window
    Input Text   123
    Input Text    #*&
    Input Text    invalid Year
    Click Element    
    Page Should Contain    Error
    Close Browser
Show Book Details
    Open Browser    ${BASE_URL}/books/details/1    browser=${BROWSER}
    Maximize Browser Window
    Page Should Contain Element    [text()='Id']
    Page Should Contain Element    [text()='Title']
    Page Should Contain Element    [text()='Author']
    Page Should Contain Element    [text()='Publish Year']
    Page Should Contain Element    [text()='Create Time']
    Page Should Contain Element    [text()='Last Update Time']
    Close Browser

Show Book - Valid Data
    Open Browser    ${BASE_URL}/books/details/1    browser=${BROWSER}
    Maximize Browser Window
    Page Should Contain Element    [contains(text(),'Id')]
   # Add similar checks for other book details
    Close Browser

Show Book - Nonexistent ID
    Open Browser    ${BASE_URL}/books/details/nonexistent_id    browser=${BROWSER}
    Maximize Browser Window
    Page Should Contain Element   [text()='Show Book']
    Page Should Contain    Error
    Close Browser

Open Edit Book Page
    Open Browser    ${BASE_URL}/books/edit/1    browser=${BROWSER}
    Maximize Browser Window
    Page Should Contain Element  [text()='Edit Book']
    Close Browser

Edit Book - Valid Data
    Open Browser    ${BASE_URL}/books/edit/1    browser=${BROWSER}
    Maximize Browser Window
    Input Text    My Updated Book
    Input Text    Updated Author
    Input Text       2023
    Click Element    [text()='Save']
    Page Should Contain    Book Edited successfully
    Location Should Be    ${BASE_URL}/
    Close Browser

Edit Book - Empty Fields
    Open Browser    ${BASE_URL}/books/edit/1    browser=${BROWSER}
    Maximize Browser Window
    Click Element   [text()='Save']
    Page Should Contain    Error
    Close Browser

Edit Book - Invalid Data
    Open Browser    ${BASE_URL}/books/edit/1    browser=${BROWSER}
    Maximize Browser Window
    Input Text   Invalid Year
    Click Element    [text()='Save']
    Page Should Contain    Error
    Close Browser


Open Delete Book Page
    Open Browser    ${BASE_URL}/books/delete/1    browser=${BROWSER}
    Maximize Browser Window
    Page Should Contain Element    xpath=//h1[text()='Delete Book']
    Close Browser

Delete Book - Confirm
    Open Browser    ${BASE_URL}/books/delete/1    browser=${BROWSER}
    Maximize Browser Window
    Click Element   [text()='Yes, Delete it']
    Page Should Contain    Book Deleted successfully
    Location Should Be    ${BASE_URL}/
    Close Browser

Delete Book - Cancel
    Open Browser    ${BASE_URL}/books/delete/1    browser=${BROWSER}
    Maximize Browser Window
    Click Element    [text()='Cancel']
    Location Should Be    ${BASE_URL}/books/details/1 
    Close Browser





