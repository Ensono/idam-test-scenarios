# Registration Scenarios

## Overview

* Should be able to register user with valid registration request payload
* Should not be able to Register user with Malformed JSON payload
* Verify user registration
* Should not be able to register the same user twice
* Should not be able to register user with restricted passwords
* Should not be able to register user with easy to guess passwords
* Should not be able to set password the same as username

| Registration Scenarios                                                  | Input                                                                                                | Response Code                        | Checks                                     | Notes                                                                                                                                               |
|-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|--------------------------------------|--------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
 |
| Should be able to register user with valid registration request payload | All fields                                                                                           | 200                                  | Check user exists in DB                    |
| All required fields                                                     |
 |
| Should not be able to Register user with Malformed JSON payload         | Missing/Empty Headers                                                                                | 400                                  | Check no record is created in DB           |
| Missing/Empty Required Fields                                           |
| "Incorrect values/Incorrect Format                                      |
| for Required Fields"                                                    |
| Various combinations of invalid email formats\.                         |
| Verify user registration                                                | Valid request                                                                                        | 200                                  | "Check user status changes from            |
| unverified to verified"                                                 | Following registration, users normally need to click a link in email to verify their email account\. |
| Invalid request                                                         | 400/403                                                                                              | "Check user status doesn't change\.  |
| User should still be unverified\."                                      |
 |
| Should not be able to register the same user twice                      | valid payload in both cases                                                                          | Depends                              | Error message saying user already exists\. |
 |
| Security Controls                                                       |
 |
| Should not be able to register user with restricted passwords           | All fields valid, but restricted passwords                                                           | 400                                  | Check error message is apporpriate         | Restricted passwords are the ones that have already been hacked and put on pastebins\. HIBP \(HaveIBeenPawned\.com\) has a list of hacked passwords |
| Should not be able to register user with easy to guess passwords        | All fields valid, but easy to guess password                                                         | 400                                  | Check error message is apporpriate         | There are a list of top xx list of passwords that are common and easy to hack so should be avoided in registration\.                                |
| Should not be able to set password the same as username                 | All fields valid, but password same as username                                                      | 400                                  | Check error message is apporpriate         |
