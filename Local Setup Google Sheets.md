# Local Setup for Google Sheets Schedule ⚒️ UNDER CONSTRUCTION ⚒️ (Currently only provides Empty Schedule Sheets)

0. Firstly Follow this tutorial video to setup Oauth2, get the client-id and credentials.json (end of video) 
  https://github.com/Jaswir/Hackathon-Kickstarter-Kit/assets/15957528/5a04c396-bc87-4a1e-94d7-6cf055ba3523

1. Create a folder named .streamlit in your project. 

2. Paste the following text there: 
   Here you put the Client-ID from the OAuth2 you just created and your huggingface token
  ```
  HUGGINGFACEHUB_API_TOKEN='your huggingface token'
  GOOGLE_SHEETS_API_KEY='your sheets api_key'
  DEPLOYMENT_ENV ='Local'
  ```

  Also make a new file named 'hackathon_kickstarter_kit.json' inside the utils folder
  and paste the json you just downloaded inside of there



3. Setting the DEPLOYMENT_ENV to 'Local' will make the Authorization appear in the sidebar as follows:
   !![image](https://github.com/Jaswir/Hackathon-Kickstarter-Kit/assets/15957528/c5b13c02-eeb4-47ac-bd97-f70c02cdf025)
4. But first you will have to uncomment this piece of code in Home.py this will save the token in the root directory as token.json
   and allow Google OAuth2 to confirm that you have been logged in.
   ``` python
   ### DANGEROUS , this will store your token inside the streamlit project directory
   ### Only to be used locally in deployment it would store your credentials and allow others to upload sheets to your drive. 
    # if DEPLOYMENT_ENV == "Local":
    #     if "code" in st.query_params:
    #         query_params = st.query_params["code"]
    #         google_sheets.save_credentials(query_params)
    #         print("QUERY PARAMS", query_params)

   ```
5. Now it's all set up: go to the link to authorize, you will see this, you can click advanced (verification would require to buy a website domain)
   !![image](https://github.com/Jaswir/Hackathon-Kickstarter-Kit/assets/15957528/2d22e6c0-8920-4480-8382-1de37bd37040)
6. After doing this you will return to the home page, go back to Create Your Kit and you will see:
   !![image](https://github.com/Jaswir/Hackathon-Kickstarter-Kit/assets/15957528/eb0167e8-a332-4cc6-806c-834e6b25222f)
7. You're all set up, Enjoy your empty Google Sheet Schedule!
   !![image](https://github.com/Jaswir/Hackathon-Kickstarter-Kit/assets/15957528/0db95ec1-7523-4a7d-9aef-44ff3998a62f)





