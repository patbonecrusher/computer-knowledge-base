---
creation date: 2024-11-04 13:30
tags:
  - dev/language
  - dev/language/python
  - references/best-of
---
---

```cardlink
url: https://python.plainenglish.io/20-python-one-liners-that-will-make-you-a-better-developer-in-2024-d17394326000
title: "20 Python One-Liners That Made Me a Cool Developer 😎"
description: "I wish I knew it earlier"
host: python.plainenglish.io
favicon: https://miro.medium.com/v2/resize:fill:256:256/1*D3hZzYqqsM6-wef-5zzDIA.png
image: https://miro.medium.com/v2/resize:fit:1200/1*5AFGk6o1l8tQHXhE5rwgQw.jpeg
```


You think you are pretty good at Python? Maybe you have conquered a couple of data pipelines, automated a few workflows or even built some mini API.

What if I told you there is still untapped Python magic like spells fitting in one line of code?

Yes, one-liners. Those snappy little gems which not only get the job done but make you look like a coding sorcerer in front of your team.

Let’s dive in.

## 1. Find the 5 Largest Files in a Directory (Say Goodbye to Disk Overload)

```python
print(sorted((os.path.join(dp, f) for dp, _, fn in os.walk('/path/to/folder') for f in fn), key=os.path.getsize, reverse=True)[:5])
```
**Why it’s cool:** No more clicking through folders wondering _what’s eating all my space_. This will return the 5 largest files right away.

## 2. Fetch All H1 Tags from a Webpage in Seconds

```python
print([h.text for h in BeautifulSoup(requests.get('https://example.com').content, 'html.parser').find_all('h1')])
```
**Pro Tip:** Perfect for quickly checking if the SEO team messed up the page structure.

## 3. Flatten Any Nested List Like a Boss

```python
print([item for sublist in [1, 2](1,%202)] for item in (sublist if isinstance(sublist, list) else [sublist])])
```
_Nested lists were fun… for the first 10 minutes of your career. After that? Not so much._

## 4. Download All Images from a Web Page

```python
[open(f'image_{i}.jpg', 'wb').write(requests.get(img['src']).content) for i, img in enumerate(BeautifulSoup(requests.get('https://example.com').content, 'html.parser').find_all('img'))]
```
**Why it’s useful:** Your designer needs assets. Boom, you just automated their entire morning. You’re a hero now.

## 5. Calculate the Size of an Object in Memory (Know What’s Hogging RAM)

```python
print(sum(sys.getsizeof(obj) for obj in locals().values()))
```

_”Memory leak? Never heard of her.”_

## 6. Turn CSV Data into a List of Dicts (Like a Pro)

```python
print([dict(zip(line.split(','))) for line in open('data.csv')])
```
**Fact:** Developers spend more time parsing CSVs than anyone cares to admit.

## 7. Get Yesterday’s Date Without Breaking a Sweat

```python
print((datetime.date.today() - datetime.timedelta(days=1)).isoformat())
```
_Because yes, that feature needs the date from yesterday. Obviously._

## 8. Send a Slack Message with One Line of Code

```python
requests.post('https://slack.com/api/chat.postMessage', json={'channel': '#general', 'text': 'Hello from Python!'}, headers={'Authorization': 'Bearer xoxb-your-slack-token'})
```
**Why this matters:** Now you can send updates _and_ flex your automation skills in one go.

## 9. Extract All Email Addresses from a File

```python
print(re.findall(r'\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b', open('file.txt').read()))
```
_Found 100+ emails in under a second? The IT team will think you’re a genius._

## 10. Get the Most Common Word in a File

```python
print(Counter(open('file.txt').read().split()).most_common(1)[0])
```
**Why it’s useful:** No more eyeballing word counts. You’ll know instantly if the intern overused _“synergy”_ again.

## 11. Serve Files Locally (No Setup Required)

```python
python3 -m http.server 8080
```

_Who needs Dropbox when you can instantly serve files on your network?_

## 12. Check If a Port Is Open

```python
print('Open' if socket.socket().connect_ex(('127.0.0.1', 22)) == 0 else 'Closed')
```
**Pro Tip:** Useful for troubleshooting the “It’s working on my machine” problem. You know the one.

## 13. Create a QR Code from Any Text

```python
qrcode.make('https://example.com').save('qr.png')
```
_You’d be surprised how many random QR codes you’ll generate once you know you can make them._

## 14. Measure Execution Time of Any Block of Code

```python
print(time.time() - (lambda t: (t := time.time(), your_function())[1])(0))
```
**Why it’s brilliant:** Performance bottlenecks? Solved.

## 15. Create a Progress Bar in the Terminal

```python
[print(f'\rProgress: {i+1}/{100}', end='') for i in range(100)]
```
_Finally, make it look like your script is doing something important._

## 16. Convert JSON to a Python Object in One Line

```python
print(json.loads(open('data.json').read()))
```

**Pro Tip:** This will save you from endless copy-pasting in Postman.

## 17. Send Yourself a Daily Motivational Quote

```python
requests.post('https://api.telegram.org/bot<your-bot-token>/sendMessage', data={'chat_id': '<your-chat-id>', 'text': requests.get('https://zenquotes.io/api/random').json()[0]['q']})
```
_Because some days you just need to hear: “Keep going, champ.”_

## 18. Rename All Files in a Folder Based on Their Creation Date

```python
[os.rename(f, time.ctime(os.path.getctime(f)).replace(' ', '_') + os.path.splitext(f)[1]) for f in os.listdir('.')]
```
_Organized folders are the closest thing to inner peace that a developer will ever find._

## 19. Check If Your Internet Connection Is Alive

```python
print('Connected' if requests.get('https://google.com').status_code == 200 else 'Offline')
```
_Why this matters:_ Avoid _that awkward moment_ when you realize you’ve been debugging an offline server.

## 20. Monitor CPU Usage Every 5 Seconds

```python
[print(f'CPU: {psutil.cpu_percent()}%') for _ in range(12)]
```
**Fun Fact:** 30% of programmers start checking CPU usage after their first crash. Don’t be that guy.