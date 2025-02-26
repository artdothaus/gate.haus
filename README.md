# Gate.Haus

This project lets you create links that only NFT holders can view.  

## Deployment

Requirements: node-v16.8.0, Google Firebase

1. The whole project runs on Firebase, so to deploy you would first create a Firebase project.
2. Edit src/utils/firebase.js Firebase config
3. Edit src/utils/eth.js config
4. Edit .firebaserc add your Firebase project id
5. Go to your project folder and install packages 
```bash
$ yarn
```
6. Build frontend 
```bash
$ yarn build && firebase deploy --except functions
```
7. Go to ./functions folder and install packages
```bash
$ yarn
```
8. Install Firebase Tools 
```bash
$ sudo npm install -g firebase-tools
```
9. Set firebase as prefix 
```bash
$ alias firebase="`npm config get prefix`/bin/firebase"
```
10. Set env vars on firebase with the following command. Please use your own bugsnag.com API key for a nodejs project and an Infura ethereum https RPC URL.
    read more about it: https://firebase.google.com/docs/functions/config-env
```bash
$ firebase functions:config:set bugsnag.apikey="put_a_bugsnag+apikey_here" infura.url="put_your_infura_url_here"
```
11. Install Firebase backend
```bash
$ firebase deploy --only functions 
```

## Troubleshooting

#### Problem
```bash
$ Failed to authenticate, have you run    ?
```
#### Solution
The command pop up a new window login with the same id that you used for firebase db ,once logged in it will give you a string copy that string and paste in your terminal.
```bash
$ firebase login --no-localhost
```
#### Problem
```bash
$ Cannot read property 'apikey' of undefined
```
#### Solution
You need to set 2 env vars. You need a bugsnag.com key for a nodejs project and an infura eth http rpc URL.
```bash
$ firebase functions:config:set bugsnag.apikey="put_a_bugsnag+apikey_here" infura.url="put_your_infura_url_here"
```

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.
Note that you need the firebase functions to be deployed for this to work.
