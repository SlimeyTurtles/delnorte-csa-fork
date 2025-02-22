---
title: 'Anthony and Sahil: A Reflection on Computer Science'
date: '2022-08-22'
summary: "An article detailing our motivations and accomplishments in computer science. More focused on stories and learning processes than Bria's tips"
tags: []
type: 'page'
---

<script>
	import Runnable from '$components/Runnable.svelte';
	import HeadsTails from './code/HeadsTails.py?raw';
    import HeadsTailsNew from './code/HeadsTailsNew.py?raw';
</script>

### Anthony: Computer Science Before APCSA

Hello! My name is Anthony Vo, and I graduated Del Norte with the class of 2022. 

My computer science journey started when I was in second grade. Khan Academy used to have a coding portion of its website, and I remember spending hours making programs that drew simple images. There was no logic involved in the coding, but as an introduction, it got me hooked on the subject. Here's a recreation of a pig that I made using Khan Academy:

![Pig](https://github.com/nighthawkcoders/APCSP/blob/master/images/pig.PNG?raw=true)

In elementary school, I used Scratch to create a plethora of games. During the summer, I also took ID Tech Camps that taught me more about game design and programming. Though some of these camps weren't *that* helpful in learning computer science (Minecraft mapping isn't a skill I use to day), they furthered my interest in the subject. You can check out some of my scratch projects [here](https://scratch.mit.edu/users/avo12345/).

I took more computer science classes in middle school with the two GTT classes. The classes still worked a lot with Scratch, but in 8th grade, I learned more about HTML, CSS, JavaScript, and Python. Those classes didn't result in the best programs, but it provided a solid foundation for problem solving and syntax that I continue to build off of today. Below are a few programs that I made in eighth grade (updated to conform to modern Python standards).

<Runnable code={HeadsTails} lang={'python'} title={'HeadsTails.py'}/>

<Runnable code={HeadsTailsNew} lang={'java'} title={'HeadsTailsNew.py'}/>

    Following this retaurant's Facebook page will make you prosperous.


The next computer science class that I took was Mr. Mortensen's Intro to Computer Science class (which has since been replaced with CSP). This was probably my favorite class in all of high school; hanging out in fifth period with my friends, coding, and having an overall good time was one of the highlights of high school... which probably says something about me ;). I learned how to use GitHub in this class and really collaborate with my peers, which helped me apply my skills to a practical environment. I also learned C which helped me understand more about how computers processed code. Below is a program I made which creates random questions. You can see how much better my programming got after taking this class!

```java
//
//  main.c
//  parameterFunctionQuestion(s)
//
//  Created by Vo, Anthony on 9/11/19.
//  Copyright © 2019 Vo, Anthony. All rights reserved.
//

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int questionMaker (double arg1, char operator, double arg2) { //function that creates math questions based off of given paramters
    int input, randomizer, answer, i, j, seqChecker[4];
    double answerSeq[4];
    int score = 0, shutOff = 0;
    srand(time(0)); //initializes score, input, and random seed
    
    switch (operator) {
        case '+':
            answer = arg1 + arg2;
            break;
        case '-':
            answer = arg1 - arg2;
            break;
        case '/':
            answer = arg1 / arg2;
            break;
        case '*':
            answer = arg1 * arg2;
            break;
    } //determines correct answer
    
    double answer1 = arg1 + arg2;
    double answer2 = arg1 - arg2;
    double answer3 = arg1 / arg2;
    double answer4 = arg1 * arg2; //gives possible answers
    
    if (answer1 == answer4) {
        if (operator == '+') {
            answer4 = answer1 - (rand() % 100) + 1;
        } else {
            answer1 = answer4 - (rand() % 100) + 1;
        }
    }
    if (answer3 == answer4) {
        if (operator == '*') {
            answer3 = answer4 - (rand() % 100) + 1;
        } else {
            answer4 = answer3 - (rand() % 100) + 1;
        }
    }
    if (answer2 == answer3) {
        if (operator == '-') {
            answer3 = answer2 - (rand() % 100) + 1;
        } else {
            answer2 = answer3 - (rand() % 100) + 1;
        }
    } //failsafe for if two answers are the same (i.e. 4 - 2 = 4 / 2)
    
    for (i = 0; i < 4; i++) {
        seqChecker[i] = 0;
    } //cleans up seqChecker (has some random integers inside of it, not sure why)
    
    for (i = 0; i < 4; i++) {
        while (shutOff == 0) {
            randomizer = rand() % 4;
            if (seqChecker[0] != randomizer + 1 && seqChecker[1] != randomizer + 1 && seqChecker[2] != randomizer + 1 && seqChecker[3] != randomizer + 1) {
                shutOff = 1;
            }
            
        }
        
        shutOff = 0;
        randomizer ++;
        switch(randomizer) {
            case 1:
                answerSeq[i] = answer1;
                seqChecker[i] = 1;
                break;
            case 2:
                answerSeq[i] = answer2;
                seqChecker[i] = 2;
                break;
            case 3:
                answerSeq[i] = answer3;
                seqChecker[i] = 3;
                break;
            case 4:
                answerSeq[i] = answer4;
                seqChecker[i] = 4;
                break;
        }
        
    } //randomizes answers
    
    printf("%lf %c %lf is?\n", arg1, operator, arg2);
    printf("1) %lf\n2) %lf\n3) %lf\n4) %lf\n", answerSeq[0], answerSeq[1], answerSeq[2], answerSeq[3]);
    scanf("%d", &input); //asks question
    
    if (answerSeq[input - 1] == answer) {
        score++;
        printf("Correct!\n");
    } else {
        printf("Incorrect\n");
    } //checks for correct answer
    
    return score; //returns points gained
}

int main(void) {
    srand(time(0));
    int score = 0, questions = 0;
    /* int i, operator;
    for (i = 0; i < (rand() % 5) + 1; i++) {
        operator = rand() % 4;
        switch(operator) {
            case 0:
                score += questionMaker(rand() % 20 + 1, '+', rand() % 20 + 1);
                break;
            case 1:
                score += questionMaker(rand() % 20 + 1, '-', rand() % 20 + 1);
                break;
            case 2:
                score += questionMaker(rand() % 20 + 1, '/', rand() % 20 + 1);
                break;
            case 3:
                score += questionMaker(rand() % 20 + 1, '*', rand() % 20 + 1);
                break;
        }
        questions++;
    } */ //asks random questions (i.e. random arguments and operators)
    questionMaker(10, '*', 8);
    questions++;
    
    printf("Your final score is %d out of %d\n", score, questions);
    
    return 0;
}
```

### Anthony: My AP CSA Experience

Finally, we've reached junior year. I took AP CSA during the quarantine year, and it helped me improve my Object Oriented Programming skills by a lot. My success in the class stemmed mostly from motivation to code; I spent my first periods coding instead of playing Roblox (which was a popular alternative that I did in my English classes), and I made sure to finish all of my assignments on time without copying from others. Mr. Mortensen's AP study plan also helped a lot. We were required to finish a CollegeBoard unit quiz every week, so I would hop in a Discord call with my group members every Friday to do the quiz together. I have a lot of fond memories of staying up until 2 AM with my friends on Friday to meet Mr. Mortensen's assignment deadline (admittedly, it was a lot more fun than it sounds). 

For success in AP CSA, I would recommend completing everything on time. Though there is a grace period for a lot of assignments, if you fall behind one week and don't understand a concept, it can quickly snowball out of control. Get on top of your assignments, make sure you understand each week's concepts, and you'll succeed. You don't need to have had years of prior experience like me; you just need to try your best to understand and work on each week's work.

After junior year, I realized that I had a big hole in my repretoire. I could code well, sure, but I couldn't actually present or make anything of substance. So, as I chose senior classes, I decided on CSP to work on my web development skills. I spent the summer writing college essays, playing League of Legends, and hanging out. I also found out that I got a 5 on the AP CSA exam! When fall came, I was ready to begin creating polished websites. During that first trimester, I met a new friend...

### Sahil: Starting Out

Hey, I'm Sahil Samar. I'm currently a senior at Del Norte, in the graduating class of 2023. 

My computer science journey started out in around 8th grade when I got interested in game development. But game development was a super hard thing to start with! Unity uses a language called C#, and I didn't have any idea how to use it. I didn't really understand the architecture of Unity or C# at first; I just kind of dove in and started making projects. I would look up what I didn't know, and just copy paste in code to get things working. Even this was hard, because when something went wrong I had no idea how to fix it. But with way too many hours, I was able to make some projects. It isn't easy to get started getting into coding! By the time I got to AP CSP, I still had a lot to learn about the coding mindset.

My very first game, 3D Pong:

![3D Pong](https://user-images.githubusercontent.com/64157584/185832344-fecede54-be5d-4dcb-a7e7-b65b50fe49cb.png)

### Sahil: AP CSP

When I got to AP CSP, I still didn't really have an idea of how coding worked. I just knew how to find code and paste it into my project. But slowly, I began moving away from this. I met Anthony Vo, who you just read a little bit about, in my first trimester. Whenever I didn't understand something, he would always help me out. He wouldn't give me code to copy paste though. He would actually explain the code to me, so I could do it myself. This was huge for me, since I actually began to think about my code and be able to develop things on my own. Mr. Mortensen guided me through countless problems, but everytime I asked him for help I walked away with some new understanding of how to debug my code. At the start of the trimester, I would go up to Mr. Mortensen or Anthony as soon as I had a problem. But by the end of the year, I only used them as a last resort, after I had truly tried everything. At that point, I just needed a pair of fresh eyes, and not someone to guide me through the whole process. Moral of the story: you aren't expected to come in an expert at coding! But, if you use your resources properly, you can use this year to grow. You can develop the mindset of a programmer and learn how to create cool projects and debug your issues when things don't work out. 

### Sahil: After AP CSP

AP CSP shaped me to be the coder I am today; but you only get out of it what you put into it. If you work hard, then it can completely change your mindset (if you are a new coder), and teach you plenty of skills. After AP CSP, I was able to land a summer internship working in CS at the San Diego Supercomputer Center. During this internship, I worked with huge supercomputers and began to understand what servers really were and how they worked. Our project was called ICICLE. If you want to learn more about it, you could watch this short video: https://www.youtube.com/watch?v=gNFk5tDTtoU. I developed sophisticated authentication methods, and did a lot of "firsts" in the project. I went from having to be guided through basic code in CSP to creating things that had never been done before. It's possible! After doing a lot of stuff behind the scenes, we got to test our system on massive knowledge graphs and run some machine learning algorithms. 

Picture of one of the computers I worked with, called Expanse:

![Expanse](https://user-images.githubusercontent.com/64157584/185833475-cc0a4cbc-7f03-4129-bf5b-546adcfe33e3.png)

Knowledge Graph of Asteroids, classified using a neural network on being hazarous or not:

![Knowledge Graph](https://user-images.githubusercontent.com/64157584/185832904-9f948eab-7519-40a9-bb36-b39f9ebbf06e.png)

I also never gave up on making games! But now, I don't really need to follow tutorials anymore. I can architect a solution on my own, and when I do need to look something up I learn from it and implement it rather than just copying it. When something goes wrong, I'm not stuck; I know what to do, and I have confidence because I know that every problem has a solution. Here's a peek at one of the games I'm working on now:

![Game](https://user-images.githubusercontent.com/64157584/185833067-7c3aa46b-3c46-4edc-b1dd-49ac306d97b2.png)




### Anthony: After CSP

AP CSP helped immensely with my presentation and web development skills. For reference, here's a website I made for my 10th grade AP European History Final...

![website](https://user-images.githubusercontent.com/54915685/185851569-0e62cdc8-b46b-461d-93ba-1fcc4e33f3a5.PNG)

As you can see, it looks like garbage! You can also check out my extremely great 11th grade website for AP CSA [here](https://csa-project.herokuapp.com/).

After taking AP CSP, my websites looked a lot better. I updated a [website for my golf coach](https://sdjuniorclub.com/) and made some personal websites. Here's a quick one that I made to create basketball teams:

[![image](https://user-images.githubusercontent.com/54915685/185852873-dad6158f-40f6-4a5c-8e48-aca1ee60aadb.png)](https://tonyhieu.github.io/friday-six)

Even if you're new to CS as a whole, knowing how to make websites can help you show off the things you've done. Whether it's a personal portfolio website, an online shop, or anything else, web development is a great skill to have.

### Final Thoughts 

Anthony: 
<br />
I hope you have a great year in this class! If you put in the time and effort, you will be really successful and gain skills that you can use for the rest of your life. Best of luck to you all!

Sahil:
<br />
![image](https://user-images.githubusercontent.com/54915685/185855922-aa749acf-91f7-4282-ab32-5a92737ebd1d.png)

### Hacks
> Per Colin and Mabel Szeto Linked in pages... Responsible for reducing sprint backlog in an agile development team environment ... Participated in sprint meetings working with subject matter experts, product owners, scrum master, and development team.  Colin and Mabel graduated in 2021 and have been working Summers at Northrop Grumman.  As students, we want you to simulate these roles.   The teacher will serve as subject matter expert, product owners can be your own interests/campus interest/or teacher.  Students need to reduce backlog, serve as scrum master, and development team. 

- Students should create a Sprint Backlog.  Here are some focus...
    - Interest/Fun zone, unique idea(s) for learning Java through PBL
    - Educational zone(s), how to prepare for AP Classroom 10 Units (MCQ and FRQ) 
    - Blogging and Review zone(s), showing what you did and how
