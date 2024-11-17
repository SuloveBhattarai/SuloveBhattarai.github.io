---
layout: default
title: "Keystroke Data Analysis"
date:    2023-09-15 14:00:00
selected: true
---


# Exploring Keystroke Datasets

## Overview
This data analysis will provide insights into various keystroke and behaviors exhibited by students while completing assignments.

---
---
- Most Pressed Keys While Typing
- Latency While Typing Keywords
- Is Taking Breaks Between Assignments and Final Score Related?
- Students' Most Active Sessions
- Time Taken to Complete First Half and Second Half of Assignments
- Who is Effective in Writing Code?

---

## Definition of some important terms used in datasets: 

### 1. **X-Keystroke**
   - Refers to the keys that are **printable** such as alphanumeric keys (letters, numbers, and symbols).
   - Example: `A`, `B`, `1`, `2`, `@`, `#`, etc.

### 2. **X-Action**
   - Refers to the keys that are **non-printable** or **meta-keys**, which are used for actions like editing.
   - Example: `Enter`, `Backspace`, `Shift`, `Ctrl`, etc.


# Most Used Key while Doing Assignment
<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_1.png" alt="Most Used Keys" width="60%">
        <p><b>Fig: Most Pressed Keys</b></p>
    </div>
</div>

**Backspace** is one of the most used keys while doing an assignment. 

---

# General idea of datasets

<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_2.png" alt="Dashboard" width="60%">
        <p><b>Fig: Dashboard</b></p>
    </div>
</div>

- Backspace is the most used meta key. Generally, it is used to correct errors while writing code, which is evident from the data.
- Most of the students who participated in recording the data were enrolled as CS students.
- Student 29 scored the highest marks from the pool of 43 students in the final examination.

# Discovering Latency after pressing ‘p’ key and ‘return’ key
<p><b>As a programmer, I had a hypothetical thought: which key does a student type sooner after  pressing the ‘return’ key or ‘p’ key? </b> I made a hypothesis that students will type another key sooner after pressing the ‘return’ key. 
Now let’s see. We can classify it as latency, since it is the time taken to press another key after pressing one key. I thought the return key had the lower latency </p>
<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_3.png" alt="Thought" width="30%">
    </div>
</div>
---

## Approach to Discover Latency of each Keystroke
<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_4.png" alt="Latency" width="60%">
        <p><b>Fig: Approach to Discover Latency</b></p>
    </div>
</div>
<br>
---

## Distribution of data related to latency of respective keystroke (i.e. 'return key' and 'p key' )
<div style="display: flex; justify-content: space-between;">
    <!-- First Image -->
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_5.png" alt="Latency" width="90%">
        <p><b>Fig: Distribution of value of Latency</b></p>
    </div>
    <!-- Second Image -->
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_6.png" alt="Clustering to show the distribution of data" width="90%">
        <p><b>Fig: Clustering to show the distribution of data</b></p>
    </div>
</div>
<br>

**My hypothesis was wrong.** You can clearly see that the students pressed another key sooner after pressing p 
instead of the return key. You can see it from histogram, median value, and clustering.

## What are keys that were pressed after 'p' key and 'return' key? 
<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_7.png" alt="Most Used Keys" width="60%">
        <br>
        <p><b>Fig: Most Pressed Keys after return and p key</b></p>
    </div>
</div>
---

# Exploring in Depth

## Taking more breaks will result in a high score in assignments? 

Techniques like **Pomodoro claim** that if someone takes a frequent break after 25 minutes, we can do our task effectively. So, taking more breaks results in a high score????? 
<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_8.png" alt="Pomodoro" width="40%">
        <!-- <br>
        <p><b>Fig: Most Pressed Keys after return and p key</b></p> -->
    </div>
</div>
<br>

### Correlation between Breaks and Final Score (X-Attention denotes the number of breaks student took while doing assignments) 
<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_9.png" alt="Breaks" width="40%">
        <!-- <br>
        <p><b>Fig: Most Pressed Keys after return and p key</b></p> -->
    </div>
</div>
<br>
According to the above figure, there is a weak correlation between students gaining good score with number of taking breaks. P value
also indicates it is not statistically significant. 
<br>

### Dividing Total breaks by total keystroke events recorded (Normalized X- Attention) and Final Score relation 
<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_10.png" alt="Breaks" width="40%">
        <!-- <br>
        <p><b>Fig: Most Pressed Keys after return and p key</b></p> -->
    </div>
</div>
<br>
According to the above figure, there is a weak correlation between students gaining good score with number of taking breaks after normalizing breaks. P value also indicates it is not statistically significant. 
<br>

### Counts of each part of the day (Event Count)
<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_11.png" alt="Breaks" width="40%">
        <!-- <br>
        <p><b>Fig: Most Pressed Keys after return and p key</b></p> -->
    </div>
</div>
<br>

From here we can notice that most of the events were recorded in the **afternoon**. Students did most of the tasks in the afternoon. 

### Number of events in each hours of the day
<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_12.png" alt="Breaks" width="40%">
        <!-- <br>
        <p><b>Fig: Most Pressed Keys after return and p key</b></p> -->
    </div>
</div>
<br>

Did you notice something that nobody programmed at **5 o'clock** in the morning? It was an interesting revelation from this dataset.<br>
Most of the codes were done in the **9pm** in the night.
--- 

### Student taking breaks between assignments in different hours 
<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_13.png" alt="Breaks" width="40%">
        <!-- <br>
        <p><b>Fig: Most Pressed Keys after return and p key</b></p> -->
    </div>
</div>
<br>

You can clearly see that, most of the students took break in the **7pm** in the evening. May it's a dinner time around that time. 

--- 
### Counts of data for more than 5 min breaks
<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_14.png" alt="Breaks" width="40%">
        <!-- <br>
        <p><b>Fig: Most Pressed Keys after return and p key</b></p> -->
    </div>
</div>
<br>

From here also if we took consideration of breaks more that **5 mins**. **7 pm** is the time where it is recorded the most. 

---

### Time taken to complete first half and second half of assignments

I have always wondered whether students finish their first half of the assignment sooner or the later part of the assignment sooner. As a student myself, I always feel that we finish the second half of the assignment sooner as compared to the first half because in the later part of the assignment we are clear from the objectives, we do know what outputs we are going to achieve. And most importantly since the deadline will be achieved near, I think students get focussed on the second part of the assignment as compared to the first half. I have taken assignment 13 as a reference to do the analysis. Let’s explore now. 

---

<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_15.png" alt="Breaks" width="40%">
        <br>
        <p><b>Fig: Approach taken to compute the time taken to accomplish first and second half os assignments</b></p>
    </div>
</div>
<br>
<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_16.png" alt="Breaks" width="40%">
        <br>
        <p><b>Fig: Distribution of the time taken to complete first and second half of the assignment</b></p>
    </div>
</div>
<br>
---

### Time taken to complete first half and second half of assignments while they are active (Ignoring all the breaks above 5 mins) 
<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_17.png" alt="Breaks" width="40%">
        <br>
        <p><b>Fig: Distribution of the time taken to complete first and second half of the assignment ignoring break above 5 mins</b></p>
    </div>
</div>
<br>


From this we can clearly see that, **most of the time was taken to accomplish the first half of the assignment** in comparison to the **second half**. 

To make it more interesting, what I have done is **ignored the breaks which are greater than 5 minutes**. After taking this into consideration let’s see what we may get in the result.<br> Students took more time to complete the first half assignment in comparison to the second half. Students are quiet in research phase, understanding the assignments so this may be the reason that they took more time to complete initial phase of assignments

---

### Efficiency in writing codes
<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/keystroke_18.png" alt="Breaks" width="40%">
        <br>
        <!-- <p><b>Fig: Distribution of the time taken to complete first and second half of the assignment ignoring break above 5 mins</b></p> -->
    </div>
</div>
<br>

I have used **delete ratio** as the method to understand the efficiency in writing codes for the students. **Lower the time** they have deleted the text they have written in the code, it means they are **good at managing ideas and presenting it via codes**. 
So from this, **Student 11** seems to be the one who is better at writing codes. 

