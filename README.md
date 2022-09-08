![IDLIX (1)](https://user-images.githubusercontent.com/59155826/189171583-8a01b4a5-47bf-42bd-9712-358be5903e3a.png)


A Simple Web API to Generate Temporary Gmail Email. With a Json Response easy to manage messages  and working with IMAP Gmail Provider



## Demo
https://user-images.githubusercontent.com/59155826/189171660-8834e098-18b4-41cd-bb53-c39df8aaed40.mp4

Time To build This Project : [![wakatime](https://wakatime.com/badge/user/4e928ad9-c7b7-4f58-b88a-0f7c3a008f41/project/acf42200-a374-49dd-8369-c6f044b2a6db.svg)](https://wakatime.com/badge/user/4e928ad9-c7b7-4f58-b88a-0f7c3a008f41/project/acf42200-a374-49dd-8369-c6f044b2a6db)\
Wakatime Project : https://wakatime.com/@sandrocods/projects/mtsiyzjnpw?start=2022-09-04&end=2022-09-10



## Notice
This repository is only public for educational purposes! \
All content provided here shall not be used for any kind of illegal activity nor for law enforcement at any time.
This restrictions apply to all cases of usage, no matter whether the whole code or just parts of it are being used.
## Build With

- [Python3](https://www.python.org/)
- [Flask](https://pypi.org/project/Flask/)
- [Imap_tools](https://pypi.org/project/imap_tools)
- [Flask-Limiter](https://pypi.org/project/Flask-Limiter/)
- [Python-dotenv](https://pypi.org/project/python-dotenv/)
## Features

| Feature             | Status                                                                |
| ----------------- | ------------------------------------------------------------------ |
| Limit Request to API | ✅ |
| Use .env file to config Account | ✅ |
| Read Specific Email Body | ✅ |
| Delete Email | ✅ |
| Generate Dot Trick Email | ✅ |
| Web App | Work In Progress |

## Run Locally

Clone the project

```bash
  git clone https://github.com/sandrocods/GTmp
```

Go to the project directory

```bash
  cd GTmp
```

Install dependencies

```bash
   pip3 install -r ./requirements.txt
```

Start the server

```bash
  python3 main.py
```

Access server
```http
  Go to http://127.0.0.1:5000
```


## Environment Variables

To run this project, you will need to add the following environment variables to your .env file

`Email` -> Your Gmail Email

`Password` -> Your Gmail Password


## API Reference

#### Generate Temporary Email

#### Request :

```http
  GET /generate/<type>
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `type` | `string` | **Required**. type (dot/dotplus) |

#### Response :
```json
// http://127.0.0.1:5000/generate/dot
{
    "data": {
        "email": "yo.ur.em.a.il.777@gmail.com",
        "mailbox": "/read/yo.ur.em.a.il.777@gmail.com",
        "status": true
    },
    "message": "Success",
    "status": true
}

// http://127.0.0.1:5000/generate/dotplus
{
     "data": {
          "email": "yo.ur.em.a.il.777+37@gmail.com",
          "mailbox": "/read/yo.ur.em.a.il.777+37@gmail.com",
          "status": true
     },
     "message": "Success",
     "status": true
}
```


#### Read Messages

#### Request :
```http
  GET /read/<email>
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `email`      | `string` | **Required**. Your Email |


#### Response :
```json
// http://127.0.0.1:5000/read/yo.ur.em.a.il.777+37@gmail.com
{
     "data": [
          {
               "body": "Test 1\r\n",
               "date": "Thu, 08 Sep 2022 15:27:42 GMT",
               "from": "yo.ur.em.a.il.777+37@gmail.com",
               "subject": "Test Email Temp",
               "to": [
                    "yo.ur.em.a.il.777+37@gmail.com"
               ],
               "uid": "125"
          }
     ],
     "email": "yo.ur.em.a.il.777+37@gmail.com",
     "message": "Messages appear",
     "status": true
}
```

#### Read Messages by Text in Body

#### Request :
```http
  GET /readby/<email>/<string_in_body>
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `email`      | `string` | **Required**. Your Email |
| `string_in_body`      | `string` | **Required**. specific string in body message |


#### Response :
```json
// http://127.0.0.1:5000/readby/yo.ur.em.a.il.777+37@gmail.com/Test
{
     "data": [
          {
               "body": "Test 1\r\n",
               "date": "Thu, 08 Sep 2022 15:27:42 GMT",
               "from": "yo.ur.em.a.il.777+37@gmail.com",
               "subject": "Test Email Temp",
               "to": [
                    "yo.ur.em.a.il.777+37@gmail.com"
               ],
               "uid": "125"
          }
     ],
     "email": "yo.ur.em.a.il.777+37@gmail.com",
     "message": "Messages appear",
     "status": true
}
```

#### Delete Message

#### Request :
```http
  GET /delete/<uid>
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `uid`      | `string` | **Required**. uid from message |


#### Response :
```json
// http://127.0.0.1:5000/delete/125

true
```

#### Another Response
```json
// Message not exist
{
     "email": "yo.ur.em.a.il.777+37@gmail.com",
     "message": "No messages appear",
     "status": false
}

// Limit Request by Flask_limiter
{
     "message": "You have reached the request limit of 20 per 1 minute requests per day",
     "status": "error"
}
```

## Support

thank you for visiting this repository, if this repository is useful for your project please give a star ⭐️🙏❤️️ 
