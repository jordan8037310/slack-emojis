slack-emojis
============

```bash
pyenv global 2.7
pip install -r requirements.txt
```

*Bulk download emoji from Slack*

```bash
python get_emojis.py -o images {slackteam} {teamtoken}
```

Get the token from https://api.slack.com/web

*Bulk upload emoji into Slack*

Want to create a custom Slack emoji for every pokemon? Slack doesn't currently expose an API endpoint for creating emoji, probably to prevent users from doing exactly what I'm doing, but here's a way to do it anyway.

## Creating Emoji

You'll need Python and `pip` to get started. I recommend using [virtualenv](https://virtualenv.pypa.io/en/latest/) and possibly [virtualenvwrapper](https://virtualenvwrapper.readthedocs.org/en/latest/) as well. Standard best-practice Python stuff.

Prepare a directory that contains an image for each emoji you want to create. Remember to respect Slack's specifications for valid emoji images: no greater than 128px in width or height, no greater than 64K in image size. The base filename of each image file should be the name of the emoji (the bit you'll type inside `:` to display it).


You'll need to provide your team name (the bit before ".slack.com" in your admin URL) and your
session cookie (grab it from the request header in your browser). Copy (quoted) into `.env.example`, fill them in, and source it.

```bash
cp .env.example .env
${EDITOR} .env
source .env
```

Now you're ready to go. Use a shell glob to invoke `upload.py` with the emoji files as ARGV:

```bash
. .env && python upload.py images/*
```

:sparkles:
