![Dream](image/ohtani.png)

# About

A simple self-hosted web app for authorising selected Google API Oauth2 scopes via self-defined API credentials. Supports
Google Drive, Google Photos and Youtube.

# Use Case Scenario

This app provides an intuitive and a straightforward way for user to perform OAuth flow authorisation process to grant certain level of access to specific
parts Google services via self-defined API client credentials to third party app such as rclone and alist etc.

Rclone hardcodes redirect URI to http://localhost:53682 for Google Drive. This means that you'd always need to complete Oauth2 flow on another machine that has GUI environment. With this app, you can throw this concern out the window, you can complete your Oauth2 flow authentication of a new rclone remote remotely here, no machine GUI required. Besides that, you can customize each scope and its respective permission, providing fine-grained control over access.

I built this app with privacy and data protection in mind. I have security and privacy concerns over public services who
offer to generate tokens or refresh code. For one, I might have ended up granting broader scopes than necessary in
public token generator when the app would work just the same by providing just enough privilege and level access. Number
two, the public token generator will definitely have access to the finalized token which can then be used to access whichever
scopes you've granted previously. What he does with it is up to anyone's guess.

Thus, I decided to take it upon my shoulders to provide a GUI option for users who wish to grant third party access to
specific Google services but opt for custom API client instead. 
> [!IMPORTANT]
> Please refrain from using the demo
app I've deployed to generate access token, please deploy **your own** copy instead.

# Features

- supports headless machine, GUI environment is **not** required for completing OAuth 2.0 flow
- self-hosted, full control over your own data
- privacy-oriented, manually clear session anytime you want to start over or exit
- clears record every 12 hours
- open-source
- light-weight design
- cookie support, remembers last used state
- fine-grained control over level of access(read-only or full access)
- convenient deployment via Streamlit

# How to deploy?

<details>
    <summary>Prerequisites</summary>

1. Head over to [Google cloud console](https://console.cloud.google.com), create your project if you haven't already and
   download your client secret. Make sure to select 'Web application' from the 'Application type' dropdown-menu when
   you're creating OAuth client
   ID. ![image](https://github.com/user-attachments/assets/9379b37b-d864-41a4-b146-341bdaedaba7)
2. Under the 'Authorised redirect URIs' section, fill in the redirect URI at which your app is hosted. For example, in
   local streamlit environment, the app is usually hosted at http://localhost:8501. Copy or rename
   `.streamlit/secrets.toml.sample` to `.streamlit/secrets.toml` and ensure the redirect URI specified in Google Cloud
   Project->Credentials->OAuth client ID section match that of `.streamlit/secrets.toml` file. Once again, ensure both
   values are the same and end with this exact trailing path, **/callback**. For example,
   `http://localhost/8501/callback` ![image](https://github.com/user-attachments/assets/1f5fe153-b813-4ac9-82b0-de1179250955)
3. Finally, download the credential json file for your OAuth2 client ID.
   <img width="523" alt="image" src="https://github.com/user-attachments/assets/77d74292-4a07-441b-a670-33bd28047a30" />

</details>

---
<details>
    <summary>Direct Deployment (recommended)</summary>

1. You may deploy this app locally or remotely. Ensure you have python3 installed.
2. Get a copy of this repository via git clone (forking your own copy is recommended) and in your CLI, head over to the project root. 
3. Install packages with `pip install -r requirements.txt`. 
4. Start and execute the app with `streamlit run Home.py`. 
5. You should see your app up and running at port 8501 or whichever port that's specified in the terminal if 8501 has been occupied.

![image](https://github.com/user-attachments/assets/da775800-1395-4e4d-92b3-b997c9121712)
</details>

---
<details>
    <summary>via Streamlit Community Cloud</summary>

1. Sign in or register [here](https://share.streamlit.io).
2. Click the 'fork' button on the top right corner of my [demo](https://shotime.streamlit.app) app to fork and deploy your own copy. ![image](https://github.com/user-attachments/assets/93f6a625-7ee4-448b-bb6d-180748cf25af)
3. Fill in the Github repository containing the source code. For example `eattrenclenhard/Sho-Time` or your own repo.
4. Select 'Home.py' as entry point under 'Main file path'
5. Fill in the base URL of your app, has to match that of step 6.
6. In 'Advanced settings', fill in the URL where your app is going to be hosted on Streamlit, remember, it has to match any of the URIs you filled in earlier in Google Cloud console Client ID section and has to match that of step 5.
![image](https://github.com/user-attachments/assets/66225b2b-78af-439b-b3eb-991beca336ce)
![image](https://github.com/user-attachments/assets/baa29c5a-c601-4b43-878f-047438a0a583)
</details>

---
<details>
    <summary>via Docker</summary>
WIP
</details>

# Preview

https://shotime.streamlit.app
![shotime](https://github.com/user-attachments/assets/5f13cd2a-68e0-4b7c-8b3f-802c404060b7)
