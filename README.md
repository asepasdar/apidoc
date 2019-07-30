## Introduction API (Application Programming Interface)
### General Overview
Connectivity is an amazing thing, by now we're all used the instant connectivity that puts the world at our fingertips from desktop or devices. We can purchase, post, pin, and pick anything, anywhere, **but how does it happen? how does data get from here to there? how do different devices and applications connect with each other?** The unsung hero of our connected world is **_Application Programming Interface_** or **_API_**

In basic terms, **APIs just allow applications to communicate with one another**. **_API_** is not the database or even the server, it is the code that governs the **_access point(s)_** for the server. To speak plainly an **_API_** is the messenger that takes request and tells the system what you want to do, and then returns the response back to you. . When people talk about **_"API"_**, they sometimes generalize and actually mean "a publicly available web-based API that returns data, likely in JSON or XML".

![How API works](Assets/HowAPIWorks.png)
Think of an **API** like a menu in a restaurant. The menu provides a list of dishes you can order, along with a description of each dish. When you specify what menu items you want, the restaurant’s kitchen does the work and provides you with some finished dishes. You don’t know exactly how the kitchen prepares that food, and you don’t really need to. **_But what's missing is the critical link to communicate your order to the kitchen and deliver your food back to your table,_** that's where the waiter or **_API_** comes in. The waiter is the messenger that takes your order or (let's say this) **_API Request_** to tells the kitchen what to do, and then delivers (let's say this) **_API Response_** back to you, in this case **"food"**.

### Why would we need an API?
Imagine the following scenario: You wants to access another **app’s data** or **functionality**. For example, perhaps you want to access all posts on reddit. You could email Reddit and ask for a spreadsheet file of all posts. But then you’d have to find a way to import that spreadsheet into your application, even if you stored them in a **_database_**, the data would become **outdated very quickly**. It would be impossible to keep it up to date. It would be better and simpler for Reddit to provide you a way to query their application to get that data, so that you can view or use it in your own application. It would stay up to date automatically that way. 

Reddit has **_Public API (meaning one that does not require authentication/login)_** directly in your browser, lets have a look this **_[API REDDIT POSTS](https://www.reddit.com/r/all/.json)_** , and what we get is a **response** to our **_API request_**. Basically we've made an **_API request_** in our browser to **_Reddit's Public API_**.
>These data below are raw version of the information that you can see at **_~~API~~ [REDDIT POSTS](https://www.reddit.com/r/all/)_**.

![Response](Assets/JSON.PNG)
Now what we get might appear to be gibberish to the human eye but it's actually **_JSON (Javascript Object Notation)_ formatted data**, it's structured data organized according to key value pairs. You can make an **_API Request_** with **Postman** [[Download]](https://www.getpostman.com/downloads/) to get more **"easy to read"** result, if already have it you can make an **_API Request_** like this image below
![JSON Formatter](Assets/Postman.PNG)
>Blue pen  : **_HTTP_** method set to **_GET_** (we'll talk about HTTP method later)

>Red pen   : **_Reddit's API_**

>Green pen : Response from **_API_**

### What is JSON and why do we use it in API?
Let's talk about **_JSON_**, as we mentioned before **it's structured data organized according to key value pairs**, let's have a look at this simple **_JSON_**
```
"restaurant": {
	"name": "Fish Witch",
	"address": "Antapani",
	"zipcode": "40291",
	"phone": "08xx-xxxx-xxxx",
	"website": "http://example.com",
	"email": "info@example.com"
}
```
Neat. This is fairly easy to read — our data is stored as key/value pairs. This means that we can see the key on the left, in this case **_name, address, zipcode, website, email_**, and the value on the right, in this case **value of "name" is _Fish Witch_** and so on. A different Restaurant would have a different value, but its key would be the same — it would always have a **_name, address, zipcode, website, email_**.
For example you make an **_API Request_** to get data from restaurant "Puri Purr", **_API Response_** would be like this:
```
"restaurant": {
	"name": "Puri Purr",
	"address": "Arcamanik",
	"zipcode": "40293",
	"phone": "022-xxxx-xxxx",
	"website": "http://puripurr.com",
	"email": "contact@puripurr.com"
}
``` 
As you can see the key stays the same for each restaurant, but the value would be different. Each **_API_** must define its own format for the data that it serves, **developers** typically read documentation provided by the **_API_ “maintainer”** (Reddit in this case) in order to learn the data format and use it properly. The question is **_why JSON?_** because it’s readable, it’s lightweight, but the most important, **it's comparatively easy** to get applications written in **other programming languages** to read it and generate it as well. This means that an **_API_** that returns **_JSON_** can be accessed by an application written in programming languages C#, Java, Ruby, Python, JS, PHP and many more, this makes an API scalable and platform independent.

### HTTP Method
Until now we've only been consuming data from **_API_**, but you can also write/send data to **_API_**, for example you can send **customer information, file upload, etc**, but before we go down that road we need to talk a little bit about the concept of **_HTTP request method_**. There are several **_HTTP method_** but the big two that you really need to know are **_GET_** and **_POST_**. A **_GET request_** is what you used to consumed data, that's what we've done so far by passing **_URL_** in order to get data from the **_API_**. But a **_POST Request_** a little bit different, this method requests that a web server accepts the data enclosed in the body of the request message, most likely for storing it. It is usually used when you need to send file or data/information.
>**Note**: We'll talk about **_body request_** later

Now normal web browser doesn't allow you to put data in the body of a request, but you can make a **_POST Request_** with **Postman** [[Download]](https://www.getpostman.com/downloads/), the nice thing about working with **Postman** is you can make more complex **_API Request_**, for example you can choose any one of the available **_HTTP Methods_** on the list, second you can put data in the body of a request, and finally you can add headers to your **_API Request_**.
>**Note**: We'll talk about **_headers request_** later

