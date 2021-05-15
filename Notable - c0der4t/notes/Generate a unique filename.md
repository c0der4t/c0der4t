---
title: Generate a unique filename
created: '2021-05-12T11:44:22.478Z'
modified: '2021-05-12T11:53:49.906Z'
---

# Generate a unique filename
(BASED ON DATE AND TIME)

First generate a date time string compatible with the file system naming conventions
```c#
string DateString = DateTime.UtcNow.ToShortDateString().Replace("/", "-");
```

Next we generate a random number using the Random engine
```c#
Random Random_Engine = new Random();
string RandomNumber = Random_Engine.Next(0,999999).ToString();
```

Combine strings to render a unique string/filename
```c#
string Filename = RandomNumber + " - " + DateString;
```
