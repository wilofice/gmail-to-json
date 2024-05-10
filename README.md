# gmail-to-json
Export all your Gmail emails to JSON

I’ve noticed that the Gmail API can be somewhat perplexing for those just starting out. While the API’s setup wizard is useful for establishing the project, obtaining credentials, and performing authentication, the subsequent steps are not as straightforwardly outlined.

Therefore, I have created a Python script that does the following:
1. Scrapes all emails from your mailbox
2. Exports all emails to JSON file which includes (Datetime, Sender, Subject, Content)
3. Email content is formatted using bs4
4. Filter emails by their labels ('IMPORTANT', 'INBOX', 'PROMOTIONS', ...)


## Installation

Before anything, make sure to create a project at https://console.developers.google.com/project and 
create a credential for your app/project. Save/Download the generated credentials.json file in the same directory where you saved 'scraper.py'. If not, set the correct file path in the script here,
This youtube video shows how to do it: [link]

```python
flow = InstalledAppFlow.from_client_secrets_file('credentials.json', SCOPES)
```

1. Run the script to install the necessary packages
```
bash install.sh
```
Then

2. Run scraper.py
```
python scraper.py
```

3. Modify these lines to filter the emails and set a maximum number of emails to download
```python
mailFunc.get_msgids_with_labels(label_ids=['IMPORTANT'], max_results = 15)
```

4. Uncomment these lines from 106 to 114  in 'mailhelpers.py' to download all the emails in your inbox