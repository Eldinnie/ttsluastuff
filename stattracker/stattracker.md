# Stattracker for TTS mods

I wanted to have a way to know how much a mod got played, and with how many player.
This is an explaination to integrate this yourself.

# Needed

- Google account (to host the script and sheet)
- stats.ttslua

# steps

1) Go to https://docs.google.com/spreadsheets/d/1vupxbU6r8Z8liBI8mpCeyKjNqHc3-Z34krCWUE0q_PY/copy This will ask you to make a copy of this sheet in your own (or a) google account.
1) Change the name of the new document
1) Go to extra -> script editor. This will open a new tab to edit the script associated with the sheet
1) In line `2` and line `29` paste the ID of your sheet. in the document link above, the ide would be: `1vupxbU6r8Z8liBI8mpCeyKjNqHc3-Z34krCWUE0q_PY`
1) Go to publish -> implement as web app set version to 1 (or whatever) run app as youself (or the logged in account) and set acces to everyone (even anonymous)
1) This will prompt you to give acces to this app. It will tell you it's not trusted, but you can accept it anyway. (reviwe the code if you like)
1) it will generate an url like `https://script.google.com/macros/s/SOME_ID_HERE/exec` you need to copy
1) In you mod, `#include` or paste `stats.ttslua`
1) somewhere in your code you must call `loadstats()` with the following paramters:

- save_state - the save state string. if not in `onLoad()` use self.script_state
- stat_url - the url You copied
- initial_wait - how long the mod must be running before it starts logging in seconds (I set it to 10 minutes usually)
- interval - How often it will ping the server in seconds. This is the resolution. I usually set it to two minutes
- debug - Wether it will put debugging information in the console (true or false)
