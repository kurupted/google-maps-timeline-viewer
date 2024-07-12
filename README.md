# Google Maps Timeline Viewer
Google has decided to begin storing your Timeline data locally on your device. They'll be deleting all of your location data from their servers, and have discontinued the desktop timeline viewer.

If you're like me, you have years worth of timeline data that you want to be able to view. This project does that.


![Alt text](/screenshot.png?raw=true "Screenshot")

### Features:
- Timeline and map view
- Place info and icons
- Duration of visits ; distance traveled
- Travel modes color-coded
- Direction of travel arrows when clicking a path

#

Setup procedure:

## Obtain a Google Maps API Key

1. **Go to the Google Cloud Console:**
    - Visit [Google Cloud Console](https://console.cloud.google.com/).

2. **Create a New Project:**
    - Click on the project drop-down and select "New Project".
    - Enter a name for your project and click "Create".

3. **Enable APIs:**
    - In the Cloud Console, go to **APIs & Services**.
    - Search for the following APIs and enable them:
        - **Maps JavaScript API**
        - **Maps Embed API**
        - **Places API**

4. **Create API Key:**
    - Go to **APIs & Services > Credentials**.
    - Click "Create Credentials" and select "API Key".
    - Copy the generated API key.

5. **Restrict API Key (Optional):**
    - In the API key's settings, under **API restrictions**, select "Restrict key" and choose the APIs you enabled.



## Get Your Google Timeline Data with Google Takeout
1. **Go to Google Takeout:**
    - Visit [Google Takeout](https://takeout.google.com/).

2. **Select Data to Include:**
    - Click "Deselect all".
    - Scroll down and select **Location History**. (The default format is JSON, which is what we want.)
    - Click "Next step".

3. **Customize Export Format:**
    - Choose the delivery method, etc. Doesn't matter what you choose here.
    - Click "Create export".

4. **Download the Export:**
    - Once the export is ready, download the file.

## Install a Web Server (eg XAMPP)
You'll need to install a local web server. We'll use XAMPP as an example.
1. **Download XAMPP:**
    - Visit [XAMPP Official Website](https://www.apachefriends.org/index.html) and download XAMPP for your operating system.

2. **Install XAMPP:**
    - Run the installer and follow the instructions to install XAMPP.

3. **Start Apache Server:**
    - Open the XAMPP Control Panel.
    - Start the Apache server by clicking the "Start" button next to "Apache".

##  Set Up the Web Folder & Extract Your Data
1. **Locate XAMPP Web Folder:**
    - Navigate to the XAMPP installation directory.
    - Open the `htdocs` folder (typically found at `C:\xampp\htdocs` on Windows).

2. **Create a New Folder for Your Project:**
    - Create a new folder within `htdocs` (e.g., `timeline-viewer`).

3. **Move the HTML File to the Project Folder:**
    - Place this project's `index.html` file in the newly created project folder.
   
4. **Add your API key:**
   - Open the index.html file in a text editor and find the code below, near the top:
     ```html
     <script src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&libraries=places"></script>
     ```
   - Replace `YOUR_API_KEY` with the key you obtained from the Google Cloud Console, and save.

5. **Extract Google Timeline Data:**
    - Extract the contents of the downloaded Takeout zip file to your project folder.

Your project directory should look like this:
```
\xampp
└── \htdocs
   └── \timeline-viewer
      ├── index.html
      └── \Takeout
         └── \Location History (Timeline)
            └── \Semantic Location History
               ├── \2023
                  ├── 2023_January.json
                  ├── 2023_February.json
                  └── ...
               ├── \2024
                  ├── 2024_January.json
                  ├── 2024_February.json
                  └── ...
               └── ...
```


## View Your Timeline
1. **Open Your Web Browser:**
    - Navigate to `http://localhost/timeline-viewer`
