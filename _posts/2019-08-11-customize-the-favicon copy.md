---
title: Customize the Favicon
author: cotes
date: 2019-08-11 00:34:00 +0800
categories: [Blogging, Tutorial]
tags: [favicon]
---

# אנטרופיק: AI חוקתי, מניקור ומה שביניהם 🤖
שלום!
בבלוג זה ננסה לעקוב אחר ההתפתחויות המהירות בתחום ה- NLP, פוסט אחד בכל פעם! הפעם נשתף איך בחרנו שם לבלוג באמצעות אנטרופיק.
רקע
אנטרופיק היא חברת מחקר שפיתחה מודל שפה גדול הנקרא Claude (קלוד), מתחרה ל- ChatGPT, שהוא לכאורה בטיחותי יותר. את נושא הבטיחות עיגנה Anthropic תחת הקונספט של Constitutional AI, ובעברית - "AI חוקתי״. השימוש במנוח ״חוקה״ בא להדגיש את שהמודל צריך להיות כפוף לאוסף עקרונות מסויים.
 
המודל נגיש לשימוש דרך אפליקציית סלאק, או דרך API באמצעות Access Key.

איך בחרנו את שם הבלוג?
ספוילר - באמצעות קלוד, כמובן.
וככה זה נראה שלב אחרי שלב:
```python
resp = c.completion(
    prompt=f"{anthropic.HUMAN_PROMPT} {prompt}{anthropic.AI_PROMPT}",\
    stop_sequences=[anthropic.HUMAN_PROMPT],
    model="claude-v1.2",
    temperature=1,
    max_tokens_to_sample=max_tokens_to_sample,
)
print(resp['completion'])
```

.

### Tables

OpenAI's ChatGPT(3.5)               | Anthropic's Claude               | קריטריון               
--------------------- | --------------------- | --------------------- 
lorem                 | lorem ipsum           | lorem ipsum dolor     
lorem ipsum dolor sit | lorem ipsum dolor sit | lorem ipsum dolor sit 
