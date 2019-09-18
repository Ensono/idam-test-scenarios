# Update User Scenarios

## Overview
The update scenarios require an existing registered and verified user in BD.

* Update user with all fields valid
* Update user with all fields the same
* Update user with just one field
* Attempt to update user with malformed request [Empty request, some fields missing, some fileds empty, incorrect format]
* Attempt to update user without bearer token
* Attempt to update user with expired bearer token
* All downstream system should be synchronized with any update.


### Change Password
This is when a user is logged in and wishes to change their password.
Normally an access token is required in the header field, and the request body is current password and new password.

* Attempt to change password with invalid access token [empty, invalid]
* Attempt to change password with the new password same as current password
* Attempt to change password, with current password being different in the request body.
* Attempt to change password with the new password not compliant with the password rules [easy-to-guess-passwords, restricted-passwords, password-same-as-username]
* Change password with a valid request (Should current session terminate?)
* User should be able to login with the new password
* User should not be able to login with the old password
* All downstream system should be synchronized with password update.

### Forgot Password
This is when a user is not logged in and requests a password reset via forgotten password route.
Normally an email is sent with a link containing a reset token.

* Create new password by following the link in the email
* User should be able to login with the new password
* User should not be able to login with the old password
* Attempt to set a new password by manipulating the token in the email link
* Attempt to set a new password which doesn't meet the password rules

### Change Email
This is when a user is logged in and wishes to change their email.
Normally an access token is required in the header field, and the request body is current email and new email.

* Attempt to change email with invalid access token [empty, invalid]
* Attempt to change email with the new email same as current email
* Attempt to change email, with current email being different in the request body.
* Attempt to change email with invalid formatted email.
* Change email with a valid request (Should current session terminate?)
* User should be able to login with the new email
* User should not be able to login with the old email
* All downstream system should be synchronized with email update.