
# Welcome To 🚀 Hackathon Kickstarter Kit 🚀( Powered by Agile Loop's Synapse Copilot )

This application provides an interactive Streamlit interface for creating and managing various resources, including GitHub repositories, Discord servers, Trello Kanban boards, Google Sheets schedules, and Slack channels.

## Table of Contents

- [Setup Instructions](#setup-instructions)
- [Application Structure](#application-structure)
- [User Interface](#user-interface)
- [Integrations](#integrations)
- [How to Setup API Keys](#how-to-setup-api-keys)
- [Example Usage](#example-usage)

## Setup Instructions

### Install Dependencies
To install the required dependencies, run the following command:
```bash
pip install -r requirements.txt
```

### Environment Variables
Create a `.env` file in the root directory of your project and add the necessary API tokens and keys:
```env
GITHUB_TOKEN=your_github_token
TRELLO_API_KEY=your_trello_api_key
TRELLO_TOKEN=your_trello_token
SLACK_API_TOKEN=your_slack_token
```

### To Get The Keys you can follow these videos:
* Trello: https://www.youtube.com/watch?v=ndLSAD3StH8 (by 
Rasmus Wulff Jensen)
* Github: 
https://github.com/Jaswir/Hackathon-Kickstarter-Kit/assets/15957528/e3e71954-673a-4752-b177-8391507586a3
* Slack: 
https://github.com/Jaswir/Hackathon-Kickstarter-Kit/assets/15957528/d02e3c78-aef0-4bf8-bc06-ee593ce6eebb


### Run the Application
To start the application, execute:
```bash
streamlit run "Create Your Kit.py"
```

## Application Structure

- **Imported Modules:**
    - `github.py`: Manages GitHub repository creation and collaboration.
    - `discord.py`: Manages Discord server creation.
    - `trello.py`: Manages Trello Kanban board creation and member addition.
    - `slack.py`: Manages Slack channel messages.
    - `google_sheets.py`: Manages Google Sheets creation.

## User Interface

### Sidebar Configuration

The sidebar allows users to select the kickstarter services they'd like to use with their team !

- **Services Options:**
    - GitHub Repository & Collaborators
    - Discord Server Template
    - Trello Kanban Board 
    - Google Sheets Schedule ⚒️ UNDER CONSTRUCTION ⚒️
    - Slack Channel ⚒️ UNDER CONSTRUCTION ⚒️

### Credentials & API Keys

Users should input their credentials (AKA API/TOKENS) on the left sidebar for the services they'd want to use.

- GitHub Token
- Trello API Key
- Trello Token
- Slack Token

### Google Sheets Authorization

Users must authorize Google Sheets integration through an authorization URL.


## Integrations

### GitHub
Currently with GitHub integration, users can create a repository and add collaborators powered by agile loop's synapse copilot.

- **Repository Options:**
    - Visibility: Private or Public
    - Repository Name
    - GitHub Username

- **Collaborators:**
    - Number of collaborators
    - Collaborator usernames

### Discord

Currently users can create a minimal pre-defined discord server templates for their hackathon team to start hacking ASAP!

### Trello

For Trello integration, users can create a Kanban board and add members.
- **Board Options:**
    - Board Name
    - Member ID/Username
- **Members:**
    - Number of members
    - Member usernames


### Google Sheets
Users can create a schedule in Google Sheets. ( more updates on the way ! ) 
- **Schedule Options:**
    - Spreadsheet Title

### Slack

For Slack integration, users can send messages to a specified channel.
- **Message Options:**
    - Channel (e.g., #general)
    - Message Content

## How to Setup API Keys

### To Get The Keys you can follow these videos:
* Trello: https://www.youtube.com/watch?v=ndLSAD3StH8 (by 
Rasmus Wulff Jensen)
* Github: 
https://github.com/Jaswir/Hackathon-Kickstarter-Kit/assets/15957528/e3e71954-673a-4752-b177-8391507586a3
* Slack: 
https://github.com/Jaswir/Hackathon-Kickstarter-Kit/assets/15957528/d02e3c78-aef0-4bf8-bc06-ee593ce6eebb

### GitHub API Key

1. Go to GitHub and log in to your account.
2. Navigate to **Settings** by clicking on your profile picture in the top right corner.
3. In the left sidebar, click on **Developer settings**.
4. Click on **Personal access tokens** and then **Generate new token**.
5. Give your token a descriptive name and select the scopes or permissions you'd like to grant this token.
6. Click **Generate token** and copy the token. Add it to your `.env` file as `GITHUB_TOKEN`.

For more detailed instructions, refer to the [GitHub documentation](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

### Trello API Key and Token

1. Go to the [Trello API Key page](https://trello.com/app-key) and log in to your Trello account.
2. Click "Go to the Power-Up Admin Portal"
3. Copy your API Key and add it to your `.env` file as `TRELLO_API_KEY`.
4. On the same page, click on **Token** under the API Key.
5. Authorize the application and copy the Token. Add it to your `.env` file as `TRELLO_TOKEN`.

For more detailed instructions, refer to the [Trello documentation](https://developer.atlassian.com/cloud/trello/guides/rest-api/authorization/).

### Slack API Token

1. Go to the [Slack API](https://api.slack.com/) and log in to your account.
2. Click on **Create an App** and choose **From scratch**.
3. Fill in the App Name and choose the Development Slack Workspace.
4. Navigate to **OAuth & Permissions** in the left sidebar.
5. Scroll down to **Scopes** and add the necessary scopes under **Bot Token Scopes** aka **User Token Scopes** .
7. Click on **Install App to Workspace** and authorize the app.
8. Copy the User OAuth Token and add it to your `.env` file as `SLACK_API_TOKEN`.


**Note:** add **"chat::write"** scope as minimum to be able to use the functionalities ! 



For more detailed instructions, refer to the [Slack documentation](https://api.slack.com/tutorials/tracks/getting-a-token).

### Google Sheets API Key

1. Go to the [Google Cloud Console](https://console.cloud.google.com/) and log in to your account.
2. Create a new project or select an existing one.
3. Navigate to **APIs & Services** > **Credentials**.
4. Click on **Create Credentials** and select **OAuth client ID**.
5. Configure the consent screen if prompted.
6. Select **Application type** as **Web application** and fill in the required fields.
7. Click **Create** and copy the Client ID and Client Secret.
8. Set up the OAuth consent screen and add the authorized redirect URIs.
9. Download the credentials JSON file and use it in your application.

For more detailed instructions, refer to the [Google Sheets API documentation](https://developers.google.com/sheets/api/guides/authorizing).

---





## Example Usage

The following code snippet demonstrates the creation of a GitHub repository, including the option to add collaborators:

```python
if github_:
    st.subheader("- GitHub repo:")
    private = st.radio("Private or Public", key="visibility", options=["Private", "Public"])
    repo_name = st.text_input("Repository Name").replace(" ", "-")
    github_user = st.text_input("GitHub Username")
    st.subheader("Add Collaborators:")
    number_of_products = st.number_input(label="How many collaborators would you like to add?", min_value=0, max_value=21, value=1)
    github_collaborator_keys = [str("product" + str(x + 1)) for x in range(number_of_products)]
    github_collaborator_values = [st.text_input(label=f"Collaborator {x+1}", value="") for x in range(number_of_products)]
```

This snippet collects necessary information for creating a GitHub repository and adding collaborators for the Agile Looop Synapse Copilot.

---

