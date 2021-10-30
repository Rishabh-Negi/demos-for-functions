# 🚮 Clean up files in your storage older than XX days
A sample Swift Cloud Function for deleting files that are older than XX days on a schedule.

## 📝 Environment Variables
Go to Settings tab of your Cloud Function. Add the following environment variables.

* **APPWRITE_ENDPOINT** - Your Appwrite Endpoint
* **APPWRITE_API_KEY** - Your Appwrite API key with `files.read` and `files.write` permissions
* **DAYS_TO_EXPIRE** - Days for files to expire

## 🚀 Building and Packaging

To package this example as a cloud function, follow these steps.

```bash
$ cd demos-for-functions/swift/storage-cleaner
docker run --rm -it -v $(pwd):/app -w /app swift:5.5 swift build
```

* Ensure that your folder structure looks like this 
```
├── .build/x86_64-unknown-linux-gnu/debug/StorageCleaner
├── Sources/
└── Package.swift
```

* Create a tarfile

```bash
$ tar -zcvf code.tar.gz -C .build/x86_64-unknown-linux-gnu/ debug/StorageCleaner

```

* Navigate to the Overview Tab of your Cloud Function > Deploy Tag
* Input the command that will run your function (in this case `./StorageCleaner`) as your entrypoint command
* Upload your tarfile 
* Click 'Activate'

## ⏰ Schedule

Head over to your function in the Appwrite console and under the Settings Tab, enter a reasonable schedule time (cron syntax).

For example:

- `*/30 * * * *` every 30 minutes
- `0 * * * *` every hour
- `0 0 * * *` every day
