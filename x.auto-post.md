# Automating Posts for X.com using X's Free API

## Overview
This document provides a step-by-step implementation guide for automating posts on X.com using X's free API. It covers API setup, authentication, and a Python-based solution for posting content programmatically.

## Prerequisites
- **X (Twitter) Developer Account** with access to the free API tier
- **API Key and Secret** from the X Developer portal
- **Python 3.x** installed on your system
- **`tweepy` Python library** for API interaction

## Step 1: Registering for X API Access
1. Visit the [X Developer Portal](https://developer.x.com/).
2. Sign up and create a new developer project.
3. Navigate to **Apps** and create a new app.
4. Under **Keys and Tokens**, generate the following credentials:
   - API Key
   - API Secret Key
   - Bearer Token
   - Access Token
   - Access Token Secret

## Step 2: Installing Dependencies
Ensure you have Python installed, then install `tweepy` using pip:

```sh
pip install tweepy
```

## Step 3: Configuring Authentication
Create a `config.py` file to store API credentials securely:

```python
# config.py
API_KEY = "your_api_key"
API_SECRET_KEY = "your_api_secret_key"
ACCESS_TOKEN = "your_access_token"
ACCESS_TOKEN_SECRET = "your_access_token_secret"
```

## Step 4: Implementing the Posting Script
Create a script `post_to_x.py` to automate posts with optional media attachments:

```python
import tweepy
import os
from config import API_KEY, API_SECRET_KEY, ACCESS_TOKEN, ACCESS_TOKEN_SECRET

def authenticate():
    """Authenticate with X API"""
    auth = tweepy.OAuthHandler(API_KEY, API_SECRET_KEY)
    auth.set_access_token(ACCESS_TOKEN, ACCESS_TOKEN_SECRET)
    return tweepy.API(auth)

def post_tweet(content, media_path=None):
    """Posts a tweet with optional media attachment"""
    api = authenticate()
    try:
        if media_path and os.path.exists(media_path):
            media = api.media_upload(media_path)
            api.update_status(content, media_ids=[media.media_id])
        else:
            api.update_status(content)
        print("Tweet posted successfully!")
    except tweepy.TweepError as e:
        print("Error posting tweet:", e)

if __name__ == "__main__":
    tweet_content = "Automated post using X API! #Automation"
    media_file = "path/to/your/image_or_video.jpg"  # Set this dynamically if needed
    post_tweet(tweet_content, media_file)
```

## Step 5: Running the Automation Script
Execute the script via terminal:

```sh
python post_to_x.py
```

## Optional: Automating with a Cron Job
To schedule automatic posting, use a cron job on Linux:

```sh
crontab -e
```

Add the following line to post every 12 hours:

```sh
0 */12 * * * /usr/bin/python3 /path/to/post_to_x.py
```

## Associating Media with Posts
- Generate images or videos separately.
- Store media files in a designated folder.
- Modify `post_to_x.py` to select the correct media file per post.
- Ensure file paths are accurate when calling `post_tweet(content, media_path)`.

## Security Considerations
- **Never hardcode API keys in scripts**. Use environment variables or a configuration file.
- **Rotate API keys periodically** for security.
- **Follow X API rate limits** to avoid account restrictions.

## Conclusion
This guide provides a fully functional Python implementation to automate posts on X.com using its free API. Modify the script as needed to include scheduling, randomization, media attachments, or interaction with other services.
