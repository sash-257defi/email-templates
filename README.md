# Email Templates

## Installation

To use this templates, your computer needs [Node.js](https://nodejs.org/en/) 0.12 or greater. 


### Foundation CLI

Install the Foundation CLI with this command:

```bash
npm install foundation-cli --global
```


### Edit templates

To edit templates, clone git repo:

```bash
git clone git@github.com:sashcy/email-templates.git projectname
```

Then open the folder in your command line, and install the needed dependencies:

```bash
cd projectname
npm install
```

To set up a new project:

```bash
foundation new --framework emails
```

The CLI will prompt you to give your project a name. The default Foundation template will be downloaded into a folder with this name.


## Build Commands

`npm start` Start the build process. A new browser tab will open with a server pointing to your project files.

`npm run build` to inline CSS into HTML along with the rest of the build process.

`npm run litmus` to build as above, then submit to litmus for testing. *AWS S3 Account details required (config.json)*

`npm run mail` to build as above, then send to specified email address for testing. *SMTP server details required (config.json)*

`npm run zip` to build as above, then zip HTML and images for easy deployment to email marketing services.


## Testing

Similar to the Litmus tests, you can have the emails sent to a specified email address. Just like with the Litmus tests, you will need to provide AWS S3 account details in `config.json`. You will also need to specify to details of an SMTP server. The email address to send to emails to can either by configured in the `package.json` file or added as a parameter like so: 

```bash
npm run mail -- --to="you@example.com"
```


## config.json


```json
{
  "aws": {
    "region": "us-east-1",
    "accessKeyId": "YOUR_ACCOUNT_KEY",
    "secretAccessKey": "YOUR_ACCOUNT_SECRET",
    "params": {
        "Bucket": "elasticbeanstalk-us-east-1-THIS_IS_JUST_AN_EXAMPLE"
    },
    "url": "https://s3.amazonaws.com/elasticbeanstalk-us-east-1-THIS_IS_JUST_AN_EXAMPLE"
  },
    "litmus": {
    "username": "YOUR_LITMUS@EMAIL.com",
    "password": "YOUR_ACCOUNT_PASSWORD",
    "url": "https://YOUR_ACCOUNT.litmus.com",
    "applications": ["ol2003","ol2007","ol2010","ol2011","ol2013","chromegmailnew","chromeyahoo","appmail9","iphone5s","ipad","android4","androidgmailapp"]
  },
  "mail": {
    "to": [
      "example@domain.com"
    ],
    "from": "Company name <info@company.com",
    "smtp": {
      "auth": {
        "user": "example@domain.com",
        "pass": "12345678"
      },
      "host": "smtp.domain.com",
      "secureConnection": true,
      "port": 465
    }
  }
}
```