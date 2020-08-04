# FIREBASE STEPS

go to firebase.google.com->click get started->add project-> enter project name and click continue-> select default account
go to settings-> project settings-> click on web app(logo)-> copy code onto index.html(within head tag)

in visual studio terminal-> npm install -g firebase-tools
firebase login (authenticate ur firebase account)
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope CurrentUser
install firebase extension on vscode
firebase login
firebase init

PS D:\Projects\Firebase> firebase init

     ######## #### ########  ######## ########     ###     ######  ########
     ##        ##  ##     ## ##       ##     ##  ##   ##  ##       ##
     ######    ##  ########  ######   ########  #########  ######  ######
     ##        ##  ##    ##  ##       ##     ## ##     ##       ## ##
     ##       #### ##     ## ######## ########  ##     ##  ######  ########

You're about to initialize a Firebase project in this directory:

D:\Projects\Firebase

? Are you ready to proceed? Yes
? Which Firebase CLI features do you want to set up for this folder? Press Space to select features, then Enter to confirm your choices. Hosting: Configure and deploy Firebase Hosting sites, Emulators: Set up local emulators for Firebase features

=== Project Setup

First, let's associate this project directory with a Firebase project.
You can create multiple project aliases by running firebase use --add,
but for now we'll just set up a default project.

? Please select an option: Use an existing project
? Select a default Firebase project for this directory: fir-learn-e7521 (firebase-learn)
i Using project fir-learn-e7521 (firebase-learn)

=== Hosting Setup

Your public directory is the folder (relative to your project directory) that
will contain Hosting assets to be uploaded with firebase deploy. If you
have a build process for your assets, use your build's output directory.

? What do you want to use as your public directory? public
? Configure as a single-page app (rewrite all urls to /index.html)? Yes
? File public/index.html already exists. Overwrite? No
i Skipping write of public/index.html

=== Emulators Setup
? Which Firebase emulators do you want to set up? Press Space to select emulators, then Enter to confirm your choices. Hosting
? Which port do you want to use for the hosting emulator? 5000
? Would you like to enable the Emulator UI? Yes
? Which port do you want to use for the Emulator UI (leave empty to use any available port)? NaN
? Would you like to download the emulators now? No

i Writing configuration info to firebase.json...
i Writing project information to .firebaserc...
i Writing gitignore file to .gitignore...

- Firebase initialization complete!

to run app locally > firebase serve / firebase
emulators:start

to deploy app > firebase deploy

DEPLOYMENT DONE

# USER AUTHENTICATION

go to firebase console and head on over to authentication tab-> enable google in sign-in method tab
Add user if u want to
code is in app.js for user authentication

# Database Rules

rules_version = '2';
service cloud.firestore {
match /databases/{database}/documents {

match /{document=\*\*} {
allow read, write: if false;
}

match /things/{docId} {
allow write: if request.auth.uid == request.resource.data.uid;
allow read: if request.auth.uid == resource.data.uid;
}
}
}
