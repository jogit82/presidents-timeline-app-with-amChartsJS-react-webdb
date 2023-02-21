# Build a Timeline Generator using amCharts and Kintone

![Banner](./docs/img/banner.png)

Learn how to make an **amCharts Timeline chart** within a **React Project** with a Kintone Database!

Thank you for attending our **Kintone x Timeline** workshop!

Our free, live workshop will walk you through creating a Web Database App, setting up a React project, and using amCharts to generate a dynamic Timeline chart!

## Outline <!-- omit in toc -->
* [Completed Project](#completed-project)
* [Get Started](#get-started)
* [Get Your Free Kintone Database](#get-your-free-kintone-database)
* [Workshop Slides](#workshop-slides)
* [Workshop Steps](#workshop-steps)
* [Create a Kintone Web Database App](#create-a-kintone-web-database-app)
  * [Step 1 - Create a Kintone App using `presidents.csv` file](#step-1---create-a-kintone-app-using-presidentscsv-file)
  * [Step 2 - Create a Custom View](#step-2---create-a-custom-view)
* [Connecting the Project to Kintone](#connecting-the-project-to-kintone)
  * [Step 3 - Grab the Login Credentials, View ID, and App ID](#step-3---grab-the-login-credentials-view-id-and-app-id)
  * [Step 4 - Create a `.env` File](#step-4---create-a-env-file)
  * [Step 5 - Update customize-manifest.json with App ID](#step-5---update-customize-manifestjson-with-app-id)
* [Coding Time](#coding-time)
* [Step 6 - Editing index.js - Input Kintone data into the chart](#step-6---editing-indexjs---input-kintone-data-into-the-chart)
* [Finish the Project](#finish-the-project)
  * [Step 7 - Compile and upload the code to Kintone](#step-7---compile-and-upload-the-code-to-kintone)
  * [Step 8 - Play with the Timeline chart on your Kintone App!](#step-8---play-with-the-timeline-chart-on-your-kintone-app)
* [Debugging](#debugging)
  * [Errors related to .env](#errors-related-to-env)
  * [`npm install` command is not working](#npm-install-command-is-not-working)
  * ["npm run upload" failed?](#npm-run-upload-failed)
  * [Uncaught Error: Target container is not a DOM element](#uncaught-error-target-container-is-not-a-dom-element)
  * [Not seeing all the presidents?](#not-seeing-all-the-presidents)
  * [Not seeing a highlighted `TODO:`?](#not-seeing-a-highlighted-todo)
* [amCharts + Kintone References](#amcharts--kintone-references)
  * [Kintone Customize Uploader](#kintone-customize-uploader)
  * [Kintone Events](#kintone-events)
  * [amCharts Getting Started Tutorials](#amcharts-getting-started-tutorials)
  * [amCharts Animation](#amcharts-animation)
  * [Timeline](#timeline)
  * [Plugin: Bullets](#plugin-bullets)
  * [To have the PinBullets linkable to their Wiki\_URL, take a look at the following docs](#to-have-the-pinbullets-linkable-to-their-wiki_url-take-a-look-at-the-following-docs)
  * [Other Parts](#other-parts)


## Completed Project

Genji TODO: Add a screenshot of the completed project

## Get Started

First, clone the [kintone-workshops/timeline-generator-amcharts](https://github.com/kintone-workshops/timeline-generator-amcharts) repo!  🚀  
Then go inside the folder.

```shell
cd Downloads

git clone https://github.com/kintone-workshops/timeline-generator-amcharts

cd timeline-generator-amcharts

npm install

npm install -g @kintone/customize-uploader
```

⚡ **Notes** ⚡  
* React requires **Node >= 14.0.0** & **npm >= 5.6**  
* Check the versions inside the `timeline-generator-amcharts` folder:
  * `node -v`
  * `npm -v`
* Not the correct versions or Confused? 🤔 → Check out the [Guide on Installing Node.js & npm](docs/Install_NodeJS_npm.md) Doc

⚡ Note: Please ignore the package deprecation warnings ⚡

🔎 The `npm install` command installs the required dependencies defined in the package.json files and generates a node_modules folder with the installed modules.

---

Open the `timeline-generator-amcharts` folder in [VS Code](https://code.visualstudio.com/docs/getstarted/tips-and-tricks#_command-line) as well:

```shell
code .
```

## Get Your Free Kintone Database

[bit.ly/KDP_NEW](http://bit.ly/KDP_NEW)
* ⚡ Only use lowercase, numbers, & hyphens in your subdomain
* ⚠ Do not use uppercase or special characters

|                                                                                         |                                                                                                                   |
| --------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| ![Step 1: Fill out the Kintone Developer license sign-up form](./docs/img/SignUp-1.png) | ![Step 2: Email address will be the login name & the subdomain will be your unique link](./docs/img/SignUp-2.png) |

---

## Workshop Slides

Check out the [slides.pdf](./slides.pdf) file for the workshop slides!

---

## Workshop Steps

1. Create the Kintone App using the `presidents.csv` file
2. Setup a Custom View
3. Grab the Login Credentials, View ID, and App ID
4. Create `.env` file by duplicating the [.env.example](.env.example) file
5. Update line two in the [customize-manifest.json](customize-manifest.json) file with your App ID.
6. Edit [/src/index.js](./src/index.js) to map the data from Kintone to the chart.
7. Run `npm run upload` to upload the JavaScript file to Kintone.
8. Play with the Timeline chart!

---

## Create a Kintone Web Database App

Genji TODO: Update

### Step 1 - Create a Kintone App using `presidents.csv` file

|                                                      |                                                      |
| ---------------------------------------------------- | ---------------------------------------------------- |
| ![Create_CSV_App_01](docs/img/Create_CSV_App_01.png) | ![Create_CSV_App_02](docs/img/Create_CSV_App_02.png) |
| ![Create_CSV_App_03](docs/img/Create_CSV_App_03.png) | ![Create_CSV_App_04](docs/img/Create_CSV_App_04.png) |
| ![Create_CSV_App_05](docs/img/Create_CSV_App_05.png) | ![Create_CSV_App_06](docs/img/Create_CSV_App_06.png) |
| ![Create_CSV_App_07](docs/img/Create_CSV_App_07.png) | ![Create_CSV_App_08](docs/img/Create_CSV_App_08.png) |
| ![Create_CSV_App_09](docs/img/Create_CSV_App_09.png) | ![Create_CSV_App_10](docs/img/Create_CSV_App_10.png) |
| ![Create_CSV_App_11](docs/img/Create_CSV_App_11.png) | ![Create_CSV_App_12](docs/img/Create_CSV_App_12.png) |
| ![Create_CSV_App_13](docs/img/Create_CSV_App_13.png) |                                                      |

⚠️ Warning ⚠️
* Field Code is case sensitive
* Field Code and options must be as specified in the steps, or the code will not work

### Step 2 - Create a Custom View
* From App Settings, click on the **Views** tab
* Click on the Plus Button ⊕ to create a View
* Select `Custom view` under **Visible Fields and Column Order** section
* Get the `View ID`! (Required in `.env` file)
* Under **HTML Code**, input:

   ```HTML
   <div id="root"></div>
   ```

* Save!

Be sure to click the **Save** and **Activate App** buttons! 💪

---

## Connecting the Project to Kintone
### Step 3 - Grab the Login Credentials, View ID, and App ID

Where to get get View ID and App ID?
* Go to your Kintone App's custom view & grab the URL
* Kintone App's URL follows this template:
  * `https://<SUBDOMAIN>.kintone.com/k/<App ID>/?view=<View ID>`

Example:
* `https://example.kintone.com/k/1/?view=1234`
* Subdomain = `example`
* App ID = `1`
* View ID = `1234`

### Step 4 - Create a `.env` File

Using the [.env.example](.env.example) file as a template, create a `.env` file that will contain your login credentials and the Kintone App's View ID.

Here is what your `.env` might look like:

```txt
KINTONE_BASE_URL="https://example.kintone.com"
KINTONE_USERNAME="your_username"
KINTONE_PASSWORD="your_password"
VIEW_ID="1234"
```

#### ⚠️ DO NOT DELETE THE [.env.example](.env.example) FILE!  <!-- omit in toc -->
[.env.example](.env.example) is used by env-cmd to verify that `.env` file is correctly configured.

### Step 5 - Update customize-manifest.json with App ID
The Kintone Customize Uploader uses [customize-manifest.json](customize-manifest.json) to determine where to upload the JavaScript file (_which Kintone App_).

```json
{
    "app": "1",
    "scope": "ALL",
    ...
```

If this is NOT your first Kintone App, update the `app` value to your App ID.

## Coding Time

---

## Step 6 - Editing index.js - Input Kintone data into the chart

File: [/src/index.js](./src/index.js)
* We access the database records from Kintone's `event.records` object.
* We will map the `event.records` object into an object for amCharts to parse.
* Below, we have a basic mapping function, with Kintone's records designated as the `rec` object.
* Kintone's records follow a structure of `objectName`.`fieldCode`.`value`
* Example: To access the `First Name` value of a Kintone record, we will write it as:
  * `rec.first.value` => George (Washington)

<details>
  <summary>Solution to Step 6 ↯</summary>

  ```javascript
  // TODO: Input Kintone data into the chart
  chart.data = event.records.map((rec, index) => {
    return {
      // TODO: Text above the PinBullet; President's name
      'text': rec.first.value,
      // TODO: PinBullet's & time period's color; Party color
      'color': partyColor[rec.party.value],
      // TODO: Time period's start; Term's start
      'start': rec.start.value,
      // TODO: Time period's end; Term's end
      'end': rec.end.value,
      // TODO: Icon inside the PinBullet; President's icon
      'icon': rec.image.value,
      'category': '' // Timeline category; leave as empty string
    }
  });
  ```

Notice anything interesting about the `color` property? We're using a slightly unusual method of object notation here. The reason is, the `partyColor` object we defined on line 29 depends on the variable coming from our Kintone records. Because the color is a variable, standard Javascript object notation such as `partyColor.rec.party.value` would not evaluate correctly. We use bracket notation here in order to have the `partyColor` property depend on the `rec.party.color` value from our app. In short, if you want to use a variable to access an object property, use square brackets!

</details>

---

## Finish the Project

### Step 7 - Compile and upload the code to Kintone
Run the following command to compile the code and upload it to Kintone.

```bash
npm run build && npm run upload
```

### Step 8 - Play with the Timeline chart on your Kintone App! 

---

## Debugging
**Let's Fix Those Problems** 💪

Here is a rundown of common problems that may occur & their solutions!

### Errors related to .env

If you get one of the following error messages, then please verify your `.env` file has been correctly configured, and you have not modified the `.env.example`.

* `Failed to find .env file at default paths: [./.env,./.env.js,./.env.json]`
* `[webpack-cli] Error: Missing environment variable: KINTONE_BASE_URL`
* `[webpack-cli] Error: Missing environment variable: KINTONE_USERNAME`
* `[webpack-cli] Error: Missing environment variable: KINTONE_PASSWORD`
* `[webpack-cli] Error: Missing environment variable: VIEW_ID`

### `npm install` command is not working

1. Verify the Node.js & npm versions **inside** the `timeline-generator-amcharts` folder
2. Just installed Node.js? Verify you configured Node.js versions **inside** the `timeline-generator-amcharts` folder

* Mac: `nodenv local 14.5.0`
* Windows: `nvm use 14.5.0`

### "npm run upload" failed?
_@kintone/customize-uploader not working?_ Let's try the following:

(1) Verify that customize uploader was installed globally
* `npm install -g @kintone/customize-uploader`

(2) Verify that the .env login info is correct (including the password)
* ⚠️ Make sure your login info is inside `.env` file & **NOT** `.env.example` file!
* ⚠️ Verify that KINTONE_BASE_URL input is correctly formatted:
  * ✅ Correct Format: `https://example.kintone.com`
  * ❌ Incorrect Format: `https://example.kintone.com/` or `example.kintone.com`
* ⚠️ Re-run the npm commands after saving the .env file
* ⚙️ Details: [Step 4 - Create a `.env` File](#step-4---create-a-env-file)

(3) Verify your [customize-manifest.json](customize-manifest.json) was updated with the correct App ID
* ⚙️ Details: [Step 5 - Update customize-manifest.json with App ID](#step-5---update-customize-manifestjson-with-app-id)

### Uncaught Error: Target container is not a DOM element
Verify that the Custom View (Gallery View) has the following HTML Code:

```HTML
<div id="root"></div>
```

### Not seeing all the presidents?
Verify that the `# per page` setting is set to 100 in order for the amCharts Timeline to display all the presidents.
* [![Kintone-View-Setting-Record-Count.png](docs/img/Kintone-View-Setting-Record-Count.png)](docs/img/Kintone-View-Setting-Record-Count-HD.png)

### Not seeing a highlighted `TODO:`?
Click on the `Install` button on the VS Code pop-up message to install [TODO Highlight extension](https://marketplace.visualstudio.com/items?itemName=wayou.vscode-todo-highlight).
* [![vscode-setting-extension.png](docs/img/vscode-setting-extension.png)](docs/img/vscode-setting-extension-HD.png)  

---

## amCharts + Kintone References

Here are some references that we used to create the Timeline Chart x Kintone customization.

### Kintone Customize Uploader
What is `@kintone/customize-uploader`?
* NPM: [npmjs.com/package/@kintone/customize-uploader](https://www.npmjs.com/package/@kintone/customize-uploader)
* README: [js-sdk/packages/customize-uploader](https://github.com/kintone/js-sdk/tree/master/packages/customize-uploader#kintone-customize-uploader)
* Tutorial: [Upload JavaScript and CSS files with Customize-uploader - Kintone Developer Program](https://kintone.dev/en/tutorials/tool-guides/upload-javascript-and-css-files-with-customize-uploader/)

### Kintone Events
* [Kintone Events - `app.record.index.show`](https://developer.kintone.io/hc/en-us/articles/212494758-Record-List-Event#events)
* [Get Record List Header Element - `kintone.app.getHeaderSpaceElement`](https://developer.kintone.io/hc/en-us/articles/213148937-Get-Record-List#getHeaderSpaceElement)

### amCharts Getting Started Tutorials
* [amCharts `core.js` & `charts.js` CDN](https://www.amcharts.com/docs/v4/getting-started/basics/#CDN)
* [Working with JavaScript x amCharts](https://www.amcharts.com/docs/v4/getting-started/basics/#Working_with_JavaScript)

### amCharts Animation
* [Animation & `animated.js`](https://www.amcharts.com/docs/v4/concepts/animations/)

### Timeline
* [Timeline](https://www.amcharts.com/demos/timeline/)
* [Anatomy of a TimeLine Chart](https://www.amcharts.com/docs/v4/chart-types/timeline/)
* [Creating Timeline Charts](https://www.amcharts.com/docs/v4/tutorials/creating-timeline-charts/)
* [Customizing chart scrollbar](https://www.amcharts.com/docs/v4/tutorials/customizing-chart-scrollbar/)
* [Setting position of the chart scrollbars](https://www.amcharts.com/docs/v4/tutorials/setting-position-of-the-chart-scrollbars/)
* [Date Axis](https://www.amcharts.com/docs/v4/concepts/axes/date-axis/)

### Plugin: Bullets
* [Plugin: Bullets](https://www.amcharts.com/docs/v4/tutorials/plugin-bullets/)

### To have the PinBullets linkable to their Wiki_URL, take a look at the following docs
* [PinBullet - amCharts 4 Documentation](https://www.amcharts.com/docs/v4/reference/pinbullet/#label_property)
* [Label - amCharts 4 Documentation](https://www.amcharts.com/docs/v4/reference/label/#url_property)

### Other Parts
* [Array.prototype.map() - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
* [Imgur API](https://apidocs.imgur.com/)