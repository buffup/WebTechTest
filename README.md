# Buff UP LTD JS/TypeScript Dev. Test

# The Task:

Create a JS/TypeScript library using our Rest API to show content of top of an HTML 5 Video Player



## Part A: HTML Player

Create a simple HTML page, that hosts a video stream (use this URL: https://buffup-public.s3.eu-west-2.amazonaws.com/video/toronto+nba+cut+3.mp4) in any HTML5 video player you want.

Import the library you have created in Part B, to display content on top of that player

## Part B: Web SDK

We now want an SDK that allows to display content (Buff's as we call them) over any existing video player.

The Developer using our library should import our library and initialize it with the ID of the player.

The SDK then should locate the HTML player frame, and render on top of that HTML content (our Buffs)

### SDK Requirements

The SDK should have the following features

- Automatically detect the player frame and put a transparent layer on top of that view that will display our content
- Handle all the business and UI logic to display the Buffs over the video in the view

### Buff UI

The Buff UI should look like this:

![Screenshot 2020-02-27 at 11.46.42](/Users/lefteris/Desktop/Screenshot 2020-02-27 at 11.46.42.png)



The UI has 3 sections:

- Top Section that displays the Questions Sender Name and Image
- Middle section where we see the question and the countdown timer
- Bottom Section where we see the answers

**The countdown timer should work and at the end if the user hasn't yet voted, the question should automatically hide**

**The number of answers can vary from 2 to 5, your UI should automatically adapt to the number of answers that the API delivers**

**If the user selects an answer, the timer should stop and you should hide the Buff after 2 seconds**

***We do not care about the UI look, so you can create a skeleton UI that matches our UI***



## What we are looking for:

- A demo website that hosts the video player and the  Javascript/Typescript library  
- Demonstration of coding style and design patterns.
- Error handling.
- Any form of unit testing you see fit.

## How to Submit your solution:

- Clone this repository
- Create a public repo in github, bitbucket or a suitable alternative and provide a link to the repository.
- Provide a readme in markdown which details your code and any libraries that you may have used
- Explain how we should test the solution

## API Usage

This a brief summary of the api endpoints you will need in order to create the SDK. There a lot of other additional properties from the json responses that are not relevant, but you must use these endpoints to retrieve the information needed for this task.

#### Base URL

The base URL is `https://buffup.proxy.beeceptor.com`. 

#### Get  Buff

Gets the data for the Buff to show

```
GET /buffs/:buffId

Buff Id is the id of the buff to fetch
In the sample Rest API Buffs with Id's 1 to 5 are available
```

Sample response:

```
{
    "result": {
        "id": 155,
        "client_id": 1,
        "stream_id": 1,
        "time_to_show": 10,
        "priority": 3,
        "created_at": "2020-01-31T22:19:43.180391Z",
        "author": {
            "first_name": "Pedro",
            "last_name": "Luz"
        },
        "question": {
            "id": 155,
            "title": "Ball Circle Personal Loan Account impactful",
            "category": 1
        },
        "answers": [
            {
                "id": 387,
                "buff_id": 0,
                "title": "324324"
            },
            {
                "id": 388,
                "buff_id": 0,
                "title": "wqewqewq"
            }
        ],
        "language": "en"
    }
}
```

Using the above URL's to fetch the various Buffs, request the Buffs every 30 seconds (from 1 to 5) and display them over the video stream.

The Buff should be displayed with a countdown timer matching the time in the `time_to_show` field of each Buff.
If the user votes before the end of the timer (taps on an answer), you should freeze the timer and hide the Buff after 2 seconds.

If the timer expires and the user doesn't vote, you should hide the Buff.

If the user manually closes the Buff by tapping on the top right `x` close button, you should hide the Buff.



Good luck!
