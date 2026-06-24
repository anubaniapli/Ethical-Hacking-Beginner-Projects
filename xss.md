# Cross-site Scripting

## Introduction

Cross-site scripting (also known as XSS) is a web security vulnerability that allows an attacker to compromise the interactions that users have with a vulnerable application. Cross-site scripting works by manipulating a vulnerable web site so that it returns malicious JavaScript to users. There are three main types of XSS attacks. These are:

Reflected XSS: the malicious script comes from the current HTTP request.

Stored XSS: the malicious script comes from the website's database.

DOM-based XSS: the vulnerability exists in client-side code rather than server-side code.

## Requirements

Access to a vulnerable website. In this case it is provided through one of portswigger academy's labs.

### Reflected XSS

Reflected cross-site scripting (or XSS) arises when an application receives data in an HTTP request and includes that data within the immediate response in an unsafe way. If another user of the application uses the attacker's URL, then the script supplied by the attacker will execute in the victim user's browser.

#### Task 1: Perform a reflected XSS attack that calls the alert function.

`<script>alert(1)</script>`

Paste that into the search bar and hit enter. A popup window should appear with "1" on it.

### Stored XSS

Stored XSS (also known as persistent or second-order XSS) arises when an application receives data from an untrusted source and includes that data within its later HTTP responses in an unsafe way. This data source could be comments on a blog post, user nicknames in a chat room, or contact details.

#### Task 2: Perform a stored XSS attack that calls the alert function when a blog post is viewed.

`<script>alert(1)</script>`

Enter the above into the comment box and click "Post comment". Go back to the blog to see the popup window.

### DOM-based XSS

The Document Object Model (DOM) is a web browser's hierarchical representation of the elements on the page. DOM XSS arises when an application contains some client-side JavaScript that processes data from an untrusted source in an unsafe way, usually by writing the data back to the DOM. JavaScript takes data from an attacker-controllable source, such as the URL, and passes it to a sink that supports dynamic code execution, such as `eval()` or `innerHTML`.

#### Task 3: Perform a DOM based attack that calls the alert function using the `document.write` sink.

1. Enter a random alphanumeric string into the search box. I can be anything such as `svg`.

2. Right-click and inspect the element, and observe that your random string has been placed inside an img src attribute.

3. Break out of the img attribute by searching for: `"><svg onload=alert(XSS)>` 

#### Task 4: Perform a DOM based attack that calls the alert function using the `document.write` sink inside a select element.

1. Select any product on the page by clicking view details. Notice the options in the drop-down list.

2. Add a `storeId` query parameter to the URL and enter a random alphanumeric string as its value. Request this modified URL. On the product page, notice that your random string is now listed as one of the options in the drop-down list.

3. Right-click and inspect the drop-down list to confirm that the value of your storeId parameter has been placed inside a select element.

4. Change the URL to include a suitable XSS payload inside the `storeId` parameter.

`product?productId=1&storeId=</select><img src=1 onerror=alert(XSS)>`

#### Task 5: DOM XSS in jQuery. The jQuery library's `$` selector changes an anchor element's `href` attribute using data from `location.search`. Make the "back" link alert `document.cookie`.

1. On the Submit feedback page, change the query parameter `returnPath` to `/` followed by a random alphanumeric string.

2. Right-click and inspect the element, and observe that your random string has been placed inside an a `href` attribute.

3. Change `returnPath` to:

`javascript:alert(document.cookie)`

4. Hit enter and click "back". 

-----------------------------------------------------------------------------------------------------------------------------------
