---
title: "אנטרופיק: AI חוקתי, מניקור ומה שביניהם 🤖"
author: aviram
date: 2023-07-04 00:34:00 +0800
categories: [Anthropic, GPT]
tags: [LLMs]
---

שלום!
בבלוג זה ננסה לעקוב אחר ההתפתחויות המהירות בתחום ה- NLP, פוסט אחד בכל פעם!
הפעם נשתף איך בחרנו את שם הבלוג הזה באמצעות **אנטרופיק**.
## רקע
אנטרופיק היא חברת מחקר שפיתחה מודל שפה גדול הנקרא Claude (קלוד), מתחרה ל- ChatGPT, שהוא לכאורה בטיחותי יותר. את נושא הבטיחות עיגנה Anthropic תחת הקונספט של Constitutional AI, ובעברית - "AI חוקתי״. השימוש במנוח ״חוקה״ בא להדגיש את שהמודל צריך להיות כפוף לאוסף עקרונות מסויים.
 
המודל נגיש לשימוש דרך אפליקציית סלאק, או דרך API באמצעות Access Key.

## איך בחרנו את שם הבלוג?
באמת שניסינו לבד, אבל בסוף פנינו לקלוד. וכך זה נראה שלב אחרי שלב:



הפנייה הבסיסית לקלוד באמצעות ה-API מתבצעת באופן הבא:
בקריאה זו מציינים את השם והגרסא של המודל, claude-v1.2, ואת ה- prompt.
בנוסף, יש פרמטר של טמפרטורה, אשר משפיעה על מידת האקראיות של התוצאות <האם דרוש ֿֿֿביהור?>

```python

from anthropic import Anthropic, HUMAN_PROMPT, AI_PROMPT

resp = c.completion(
    prompt=f"{anthropic.HUMAN_PROMPT} {prompt}{anthropic.AI_PROMPT}",\
    stop_sequences=[anthropic.HUMAN_PROMPT],
    model="claude-v1.2",
    temperature=1,
    max_tokens_to_sample=max_tokens_to_sample,
)
print(resp['completion'])
```

הפרומפט הראשון ששלחנו לקלוד היה בנוסח הבא

```python
prompt = "Please suggest data science blog names for two female data scientists"
```

הופתענו לקבל תשובות מגניבות ומקוריות, מוזמנות להתרשם מהרשימה🍿

```
 Here are some suggestions for data science blog names for two female data scientists:

• The Data Duo - Simple but captures that it's two data scientists running the blog.

• Algorithm Amazons - Amazons highlights powerful female figures, paired with algorithm shows the data science and machine learning focus.

• Codin' Chicks - Play on coding combined with chicks, could be a lighthearted brand for two female data scientists.

• Binary BFFs - BFFs is a popular acronym for "best friends forever", combined with binary the digital data focus.

• Glamorous Geeks - Blends technical skills of geeks with glamorous to add a feminine twist. 

• AI Allies - Short name showing partnership as allies, with AI highlighting their machine learning capabilities.

Does any of these options resonate with you? I can provide some additional suggestions if those do not quite fit.
```

בהמשך ביצענו prompt engineering כדי שנקבל שמות לבלוג שהם gender-aware

```python
prompt = "Please suggest data science blog names for two female data scientists. Make sure that the names indicate that we are female"
```

כאן קלוד לקח את זה לכיוון של עקבים ומניקור

```
 Here are some suggestions for data science blog names indicating female authors:

• The Data Dolls 
• Code and Cocoa 
• Algorithms and Accessories 
• Data Divas 
• Modeling and Manicures 
• Machine Learning and Mimosas 
• Neural Networks and Nail Polish 
• Predictive Pumps 
• Data Darlings 
• Algos and Heels

```

אז החלטנו להדגיש את הפן המקצועי בפרומפט. ועשינו שרשרת ניסויים בהן הוספנות בכל פעם מילות מפתח לתחום המקצועי (Machine Learning, NLP וכד׳)


```python
prompt = "Please suggest data science blog names for two female data scientists. Make sure that the names has a professional female gender indication"
```

וכך נולד השם - Semantic Sisters!



## השוואה בין המודלים 


קריטריון    | OpenAI's ChatGPT(3.5)      | Anthropic's Claude          
--------------------- | --------------------- | --------------------- 
גודל ה- Context    | 4k // 16k tokens   | 100k tokens (אורך של ספרון!)     
lorem ipsum dolor sit | lorem ipsum dolor sit | lorem ipsum dolor sit 
שיטת אימון | Reinforcement Learning from Human Feedback (RLHF) | Constitutional AI (Supervised Learning + RL)
גישה חופשית | ממשק ה- web | slack
תמחור | $1.5 / million tokens, $2 / million tokens |  $1.63/ million tokens, $5.51/ million tokens
גודל המודל  | 175 מיליארד פרמטרים | 52 מיליארד פרמטרים



## הטייקים של Semantic Sisters

נראה שמדובר במודל שנותן תוצרים ברמת איכות גבוהה והיה קל לשימוש
המודל אמנם בטיחותי, אבל עדיין לוקה בסטריאוטיפיות. אנחנו היינו מוסיפות לחוקה כמה תיקונים בנושא הזה

## רפרנסים

לינק לסקירה שלנו בפייסבוק

מאמר של חברת Anthropic על Constitutional AI

https://arxiv.org/pdf/2212.08073.pdf

