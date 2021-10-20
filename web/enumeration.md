# Enumeration

### Checks

* View page source
  * Check for interesting comments, other URL paths, etc.
  * Check for JavaScript script functions that may provide interesting information especially for things like input fields
    * Try executing part of the function into the web browser console
* Click on links of the webpage
* Check for default usernames
  * admin:admin etc. or Google default credentials for known application
* Check for being able to register new account
  * Login and look for additional information
* Check for valid usernames
  * Via Login, Signup, Forgot password. Check for response
  * Check Socials i.e. LinkedIn, Twitter to see if the link to actual users
  * Check other pages i.e. About, blog, contact etc.
* Check input boxes
  * For SSRF, RCE, LFI, HTML, SQLi, XSS
    * `iframe src='file:///etc/passwd' style='width:100%;height:100px' />`
    * `iframe src='195.254.170.2/v2/metadata' style='width:100%;height:100px' />`
* Intercept login/register request for token i.e. JWT
  * See if you can decode the token and replace the login information with new values such as for the admin user.

### Tools

* Use `gobuster` to directory bust
  * Use multiple wordlists including any that may have been provided.

###

### Examples

* Hacky Holidays - Knock knock knocking on shuttles door
