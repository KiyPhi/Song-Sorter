# Song Sorter

A simple, browser-based tool for creating ranked lists of songs using a Glicko-2 rating system. This app is for nerds who like ranked lists, made by a fellow nerd who thought others might like it as well.

---

## Frequently Asked Questions (FAQ)

### Getting Started

**Q: How do I add songs to the list? What format does the YouTube URL need to be in?**

A: Any YouTube URL format should be fine. The app automatically finds the unique video ID from the link, so you can copy and paste directly from your browser, even if the URL includes extra information like playlists or timestamps.

**Q: What's the difference between "Import List" and "Import Progress"?**

A: "Import List (.txt)" allows you to import a clean song list created by others (or yourself) to start a new sorting session from scratch. "Import Progress (.json)" loads a previously saved session, including the full song list, all your current rankings, and your undo history so you can continue exactly where you left off.

**Q: What do the "Export List" and "Export Progress" buttons do?**

A: "Export List (.txt)" saves only the song list itself (title, artist, URL). This is useful for sharing a clean list with others so they can sort it themselves and compare results with you. "Export Progress (.json)" saves your entire session. This is important for longer lists, as sorting can take a while and this allows you to save your work and come back later.

### The Sorting Process

**Q: What algorithm does this use? Why did you choose it?**

A: This app uses a Glicko-2 rating system, which is an evolution of the Elo system famous in chess. I chose it because it's highly accurate. I initially tried a simpler sorting method, but found it wasn't very precise. Glicko-2 is much better at handling uncertainty and producing a reliable final list.

**Q: What does the "Confidence" percentage mean? When should I stop sorting?**

A: Confidence is a rating of how stable ("non-volatile") the rankings are. You can technically stop sorting at any time and view the current rankings. I recommend going until at least 60% confidence for shorter lists (around 50 song). The returns on accuracy after 75% are pretty low, but you can go as high as you want for a more finely-tuned list. For much longer lists, you may need to go as high as 85-90%.

**Q: What happens if I make a mistake? Can I undo a choice?**

A: Yes. The app stores the last 100 choices you've made, and you can click the "Undo" button to go back. The history is limited to 100 steps to prevent the progress file from becoming excessively large, which could cause issues on some devices.

**Q: Why does the app sometimes show me the same two songs multiple times?**

A: The algorithm tries to be efficient by showing you pairs that it is most uncertain about. If two songs are very close in your personal ranking, the system may show them to you multiple times to be sure of the correct order. There is also a small chance of a completely random pairing to prevent the sorting from getting stuck.

### Managing Your List

**Q: Can I add more songs to my list after I've already started sorting?**

A: Yes. From the "Current Rankings" page, you can click the "Add/Remove Songs" button to go back to the list and make changes.

**Q: How does the "Edit" feature work?**

A: The "Edit" button lets you change the title, artist, or URL of a song. If you only edit the title or artist, your sorting progress for that song is kept. If you change the URL, the app will ask if you want to keep the song's progress (useful for re-uploads, region blocked videos, or quality upgrades) or reset it.

**Q: What's the best way to share my final ranked list with friends?**

A: The best way to share your visual, numbered list is to simply take a screenshot of the "Current Rankings" page or click the "Export Numbered List" button at the bottom of the rankings for longer lists. If you want a friend to be able to sort the same list you did, go to the "Add Songs" page and use the "Export List (.txt)" button to give them a clean list they can import.

### Technical Questions

**Q: On the final rankings page, what does the "±" number next to the rating mean?**

A: That is the "Rating Deviation" (RD). It's a measure of how certain the system is about that specific song's rating. A smaller number means the system is very confident in that song's position, while a larger number means its position is still likely to change with more comparisons. I wouldn't worry about it too much though, just as long as your final list looks okay to you.

**Q: Why do some YouTube videos not show a preview?**

A: YouTube sometimes restricts certain videos from being embedded on third-party websites. If a video doesn't show up in the preview, it's due to the uploader's settings. You can use the "Edit" button to try and find an alternative link for that song.

**Q: What happens if I close the browser? Is my progress saved automatically?**

A: No, progress is **not** saved automatically. You must remember to click "Export Progress" to save your session before closing the browser tab.

**Q: I'm sorting a huge list. Why is the "Export Progress" file so big?**

A: The progress file stores your complete song list and your undo history. To keep the file size manageable, the undo history is limited to the last 100 choices. While a very large list of songs will naturally create a larger file, this limit should prevent it from becoming too big to load on most devices.
