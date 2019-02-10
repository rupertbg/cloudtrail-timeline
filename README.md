# cloudtrail-timeline
This is a basic [FullCalendar Scheduler](https://fullcalendar.io/scheduler) implementation for viewing AWS CloudTrail Logs.

## Usage
You can load your data by dragging a `data.json` file (formatted as below) onto the interface. Alternatively, if a `data.json` file is served at the same remote directory as the `index.html`, it will be automatically loaded in via an ajax call.

### Schema
The schema for the `data.json` file is designed so that it can contain multiple users at once. The frontend currently only shows the first user, however additional ability to show multiple or switch between will be added shortly.

The schema is an object with keys for each User ID, the value of which is an array of CloudTrail events.
```json
{
  "id": "123456SOMEID",
  "comment": "Some comment about the data",
  "users": {
    "emailaddress@ofauser.com": [
      {
        "additionalEventData": {
          "LoginTo": "https://console.aws.amazon.com/console/home?state=hashArgs%23&isauthcode=true",
          "MFAUsed": "Yes",
          "MobileVersion": "No"
        },
        "awsRegion": "us-east-1",
        "eventID": "2763afcb-11cc-4105-9231-1de360bcacdb",
        "eventName": "ConsoleLogin",
        "eventSource": "signin.amazonaws.com",
        "eventTime": "2019-01-12T01:40:23Z",
        "eventType": "AwsConsoleSignIn",
        "eventVersion": "1.05",
        "recipientAccountId": "123456789000",
        "requestParameters": null,
        "responseElements": {
          "ConsoleLogin": "Success"
        },
        "sourceIPAddress": "12.12.142.33",
        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36",
        "userIdentity": {
          "accountId": "123456789000",
          "arn": "arn:aws:iam::123456789000:user/emailaddress@ofauser.com",
          "principalId": "AIDAIGBX23AYU1ASDI0ZU",
          "type": "IAMUser",
          "userName": "emailaddress@ofauser.com"
        }
      }
    ]
  }
}
```

## Todo
- User picker
- Multi-user view