<h1 align="center">App Xbox Live Api</h1>

## Install
```bash
npm i app-xbox-live
```

## Getting started
First, have your account token, if you don't have a token, try it to get your token:
```javascript
const xls = require("app-xbox-live");

//This method is based on Async/await.
const token = await xls.Token("<your email>", "<your password>");
//output: ["token", "uhs"]
```
Note: The account cannot have 2-step verification. Preferably, use only an account that has only a password as security.

Attention: the token, email and password must be kept secret, do not share or display it to anyone.
The token is reset every 24 hours. Then you will need to obtain another token again after 24 hours.
Microsoft does not allow to generate multiple tokens. Just generate 1 token and use it for 24 hours.


## Logging in with your token
```javascript
const xl = new xls.Account(`XBL3.0 x=${token[1]};${token[0]}`);
```
this done, if there is no error, you can now manipulate data.


<h1 align="center">Manipulating data</h1>
<h2 align="center"> Request </h2>

### Make a custom request on xbox live
```javascript
const opts = {
  url: "<request url>",
  method: "<method>"
}
xl.request(opts).then(data =>{
  console.log(data);
});
```
It is not necessary to add the authorization header because the method automatically adds it.


<h2 align="center"> People </h2>

### Finding user by gamertag
```javascript
const amount = 15;
xl.people.find("<gamertag>", amount).then(user =>{
  console.log(user);
});
```

### Getting user by xuid
```javascript
xl.people.get("<xuid>").then(user =>{
  console.log(user);
});
```

### Getting user profile
```javascript
xl.people.profile.get("<xuid>").then(user =>{
  console.log(user);
});
```

### Getting recommendation users
```javascript
xl.people.recommendation.get().then(user =>{
  console.log(user);
});
```

### Getting user setting
```javascript
xl.people.setting.get("<xuid>").then(user =>{
  console.log(user);
});
```

### Getting user summary
```javascript
xl.people.summary.get("<xuid>").then(user =>{
  console.log(user);
});
```

### Getting all the user achievement
```javascript
xl.people.achievement.all.get("<xuid>").then(user =>{
  console.log(user);
});
```

### Getting specific user achievement
```javascript
xl.people.achievement.get("<xuid>", titleId, amount).then(user =>{
  console.log(user);
});
```

### Getting user achievement stats
```javascript
xl.people.achievement.stats.get("<xuid>", titleId).then(user =>{
  console.log(user);
});
```

### Getting user achievement titles
```javascript
xl.people.achievement.titles.get("<xuid>").then(user =>{
  console.log(user);
});
```

### Getting complete user achievement titles
```javascript
xl.people.achievement.titles.complete.get("<xuid>").then(user =>{
  console.log(user);
});
```

### Getting user activity
```javascript
const amount = 100;
xl.people.activity.get("<xuid>", amount).then(user =>{
  console.log(user);
});
```

### Getting user screenshot
```javascript
const amount = 100;
xl.people.screenshot.get("<xuid>", amount).then(user =>{
  console.log(user);
});
```

### Getting user games
```javascript
xl.people.games.get("<xuid>").then(user =>{
  console.log(user);
});
```

### Getting user presence
```javascript
xl.people.presence.get("<xuid>").then(user =>{
  console.log(user);
});
```

### Adding friend
```javascript
xl.people.add("<xuid>").then(() =>{
  console.log("success");
});
```

### Removing friend
```javascript
xl.people.remove("<xuid>").then(() =>{
  console.log("success");
});
```

### Getting user gameclip
```javascript
xl.people.gameclip.get("<xuid>", amount).then(console.log);
```

### Getting user clubs
```javascript
xl.people.clubs.get("<xuid>").then(console.log);
```

### Getting user friends
```javascript
xl.people.friends.get("<xuid>").then(console.log);
```


<h2 align="center"> Club </h2>

### Finding club by name
```javascript
xl.club.find("<club name>").then(console.log);
```

### Getting club by id
```javascript
xl.club.get("<club id>").then(console.log);
```

### Getting club feed
```javascript
const amount = 50;
xl.club.feed.get("<club id>", amount).then(console.log);
```

### Sending club feed
```javascript
xl.club.feed.send("<club id>", "<message>").then(console.log);
```

### Getting club chat
```javascript
const amount = 50;
xl.club.chat.get("<club id>", amount).then(console.log);
```

<h2 align="center"> Chat </h2>

### Getting inbox
```javascript
xl.chat.inbox.get().then(console.log);
```

### Getting chat auth
```javascript
xl.chat.auth.get("<xuid>").then(console.log);
```

### Getting message
```javascript
const amount = 100;
xl.chat.message.get("<xuid>", amount).then(console.log);
```

### Sending message
```javascript
xl.chat.message.send("<xuid>", "<message>").then(console.log);
```


<h2 align="center"> title </h2>

### Getting title by id
```javascript
xl.title.get("<id>").then(console.log);
```


<h2 align="center"> Me </h2>

### Getting account privacy settings
```javascript
xl.me.account.privacy.settings.get().then(console.log);
```

### Getting profile
```javascript
xl.me.profile.get().then(console.log);
```

### Getting friends
```javascript
xl.me.profile.friends.get().then(console.log);
```

### Getting followers
```javascript
xl.me.followers.get().then(console.log);
```

### Getting family
```javascript
xl.me.profile.family.get("<xuid>").then(console.log);
```

### Getting groups
```javascript
xl.me.groups.get().then(console.log);
```

### Getting reports
```javascript
xl.me.reports.get().then(console.log);
```

### Getting games titles id
```javascript
xl.me.games.titlesId.get().then(console.log);
```# xbox-api
