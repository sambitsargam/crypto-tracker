<h1>Features of the bot:</h1>
<ul>In this project, i built a python script that will keep track of the
latest bitcoin price.</ul>
<ul>it will send you a telegram message every 30 minutes with the
latest 6 bitcoin prices. You can set a minimum threshold value so that if the BTC price goes below that threshold, then the script will send an
immediate alert message showing the price. </ul>

<h1>What will we need ? </h1>
<ul>A coinmarketcap.com API key. Because we are going to make use of their API to get the latest bitcoin price.</ul>
<ul>The telegram app, and your account's <code>chat_id.</code></ul>
<ul>Then a telegram bot and it's token key. Without a bot, you will not be able to send programmatic messages. In short, if you want to send price notifications from our python script to your telegram account, then you need a telegram bot.</ul>
<ul>Finally Python3, pip3, and a Text editor of your choice.</ul>

<h2>I know most of you may not have the first three things, that's why I broke down this tutorial into three parts for making life easier:</h2>
<p>1.Getting Coinmarketcap API Key<br>
2.Telegram Bot and your Chat ID<br>
3.Fitting everything together
</p>

<h1>1). Getting Coinmarketcap API Key</h1>
<p>Coinmarketcap.com no longer provides cryptocurrency data for anonymous users. So we need an API key to use their service. If you don't have an account on their website, then first do <a href="https://coinmarketcap.com/api/" target="_blank">Signup or Login</a></p>
<p>When you do so you will be taken to your account dashboard which will look something like this:</p>
<img src="https://github.com/sambitsargam/crypto-tracker/blob/main/1.png">
<p>As you can see there is a limit in using their API with their Basic Plan. But 333 requests a day is a lot for us! If you want to use their paid plan, then feel free to do so.</p>
<p>Remember we made this account to get the Coinmarketcap API Key. Now you can get that by clicking on that COPY KEY button which will pop up when you hover over that API Key box.</p>
<p>Awesome, now we have our Coinmarketcap API Key. Bookmark this page, because we will need this later.</p>

<h1>2). Telegram Bot and your Chat ID</h1>
<p>Before continuing this step, please make sure you have the Telegram app installed on your mobile phone/computer and you have an account created.</p>
<p>Now to the logic. As we all know, to send a message, there should be two entities, the sender and the receiver. Here the sender is the bot that we are going to create and the receiver is you or, to be exact, your chat_id.</p>
<p>See that's why you need your own telegram bot and your <code>chat_id.</code></p>
<p>In fact, telegram bots are so awesome. You can know more about how awesome telegram bots are from their official <a href="https://core.telegram.org/bots" target="_blank">Docs</a> </p>


<h2>But How do I create a bot?</h2>
<p>Just talk to BotFather and follow a few simple steps!</p>
<img src="https://github.com/sambitsargam/crypto-tracker/blob/main/2.png">
<p>BotFather is the one bot to rule them all. You can use it to create new bot accounts and manage your existing bots.</p>


<p> Now let's make our own bot:</p>
<p>First, search for BotFather in the telegram app. You will see the BotFather with a blue verified tick next to it.<br>

Click on that bot and type the message <code>/command</code> <code>/newbot</code> and send it.<code> /newbot</code> command is used to create a new bot. See whenever you enter a command to a bot you should always use the forward-slash (/) in front of the command.<br>

Now the BotFather will ask you for a <code>name</code> and a <code>username</code>, provide it.<br>


Then it will send you a congratulations message which contains the link to your bot and the authorization token for your bot.<br>

Now let's activate your bot. To do that:<br>

Click on the link to your bot which the BotFather gave you<br> 

Click on that link and send a <code>/start</code> command to activate it.<br></p>

<p>That's it, you have created your own bot and successfully activated it!</p>
<p>The token you got for your bot is a string that will look something like this - <code>110201543:AAHdqTcvCH1vGWJxfSeofSAs0K5PALDsaw.</code> This token is required to authorize the bot and send requests to the Bot API. Keep your token secure and store it safely, it can be used by anyone to control your bot 😱.</p>
<p>Awesome! Now you have your bot and importantly its token key. Save it for later use. </p>


<h1>Getting your chat_id</h1>
<p>The next step is to obtain your telegram chat_id. You can get that easily through a ready-made bot called 'IDBot':</p>
<p>Search in the telegram app for 'IDBot'. Its icon will be something like this:

IDBot's icon<br>
Now click on that bot and type a message exactly like this /getid. This /getid command will get your chat_id.<br>
Awesome again! Now you have your chat_id, save this somewhere because we will need this later.<br></p>

<h1>3). Fitting everything together</h1>
<h3>Make sure you have Python3.4+ and pip3 installed.</h3>
<h1>Initial Setups</h1>
<h4>Before starting, we need to set up a folder, virtual environment, and all that stuff. Why? Because it is a good practice! So</h4>
<p>First, create a folder named crypto_tracker anywhere on your computer.
</p>
<p>Then open pycharm</p>
<p>Create a file named tracker.py</p>
<p>Then we are setting some global variables:

api_key = 'put_your_coinmarketcap_api_key_here_which_we_first_obtained'
bot_token = 'put_your_own_telegram_bot_token'
chat_id = 'put_your_telegram_chat_id'
threshold = put the minimum threshold bitcoin price
time_interval = in seconds. Here I used 5 minutes. That means, my script will make an API request every 5 minutes and stores the price in a python list. Remember you can only make 333 free requests per day, keep that always in mind.</p>
