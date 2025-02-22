# 3DS Discord Rich Presence

*Display your 3DS game status on Discord!*

This README will be split into two sections:
  - [The quickstart guide](#quick)
  - [In-depth guide](#depth)

### Notice

*By using this app, you agree to the terms listed in [TERMS.md](/TERMS.md).*

### Credits

This project connects to a self-hosted API (or one provided by me) and fetches data received by mimicking a real 3DS connecting to the friends service and receiving friend data.  
I'd like to thank:
- [kinnay](https://github.com/kinnay) and his [NintendoClients](https://github.com/kinnay/NintendoClients)
  - NintendoClients is what this program uses to pretend to be a real 3DS.
- [hax0kartik](https://github.com/hax0kartik) and his [3dsdb](https://github.com/hax0kartik/3dsdb)
  - 3dsdb is an open-source project that includes data about games on the eShop. A modified version of it is used to retrieve the game's name and icon url.
- [HEYimHeroic](https://github.com/HEYimHeroic) and her [mii2studio](https://github.com/HEYimHeroic/mii2studio)
  - mii2studio is a command line tool written in Python that allows the user to convert between various versions of Nintendo Mii formats. I have created a modified version of it internally to convert CFSD (really, `MiiData`) to Mii Studio code.
- [jaames](https://github.com/jaames) and his [mii-qr.py](https://gist.github.com/jaames/96ce8daa11b61b758b6b0227b55f9f78)
  - mii-qr.py is a Python script that converts from the encrypted QR code format to normal CFSD. For whatever reason, a direct connection to the friends service on the 3DS returns a QR code, so this is insanely useful. Thank you.
- [qwerty](https://github.com/qwertyquerty) for her [pypresence](https://github.com/qwertyquerty/pypresence)
  - pypresence is a useful Python module that allows developers to connect their games to Discord via Python. It is how 3DS-RPC sends Rich Presence data to Discord.
- [StartBootstrap](https://github.com/StartBootstrap) for their [startbootstrap-sb-admin](https://github.com/StartBootstrap/startbootstrap-sb-admin)
  - startbootstrap-sb-admin is a template using [bootstrap](https://github.com/twbs/bootstrap) which is how I created the friends network website!

<h1 id = 'quick'>Quickstart Guide</h1>

*\*Until this project has an official release, it is recommended to follow the directions written [here](https://github.com/MCMi460/3DS-RPC/issues/2#issuecomment-1345621523).*

Download the app from the [latest release](https://github.com/MCMi460/3DS-RPC/releases) and run!  
Once ran, the app will ask for you to add a friend on your Nintendo 3DS. This is for the express purpose of pulling your currently playing Nintendo game.

1. Open Discord and 3DS-RPC

2. Add the bot's friend code provided

3. Enter your own friend code

<!--![link](/resources/link.png)-->

4. Profit!
  - Each update is around every ~30 seconds (keep in mind, the backend is updating at a different rate than the client, so this may vary). They are automatic, but it may take upwards of one minute after the program begins. To make certain that everything is in order, check your 3DS' friends list to verify the bot account has added you back.

<!--![display](/resources/display.png)-->

## FAQ

> If none of the below Qs and As help with your problem, feel free to [file an issue](https://github.com/MCMi460/3DS-RPC/issues/new). Alternatively, you can join the [3DS-RPC Discord server](https://discord.gg/pwFASr2NKx) for a better back-and-forth method of communication with me!

<!--

***Q: This is a question?***  
**A:** And this is an answer.

-->

***Q: Whenever I play a game, 3DS-RPC won't change from the home screen!***  
**A:** Firstly, try waiting ~30 seconds, as the application has a fairly slow response time. Secondly, make sure that you've enabled "Show friends what you're playing?" on your 3DS' friends app.

*Please don't DDoS me...*

<h1 id = 'depth'>In-depth guide</h1>

<h2 id = 'building'>Building</h2>

<!--
For Windows, run
```bat
cd .\3DS-RPC\scripts
.\build.bat
```
For MacOS, run
```sh
cd ./3DS-RPC/scripts
chmod +x build.sh
./build.sh
```
For Linux (Ubuntu), run
```sh
cd ./3DS-RPC/scripts
chmod +x install.sh
./install.sh
```

*(Make sure you have `python3` and `pip` installed)
-->

<h2 id = 'understanding'>Understanding</h2>

[cli]: /client/client.py
[api]: /api/love.py
[app]: /client/app.py
[front]: /server/server.py
[back]: /server/backend.py
