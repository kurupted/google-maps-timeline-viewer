# Google Maps Timeline Viewer
Google has decided to begin storing your Timeline data locally on your device. They'll be deleting all of your location data from their servers, and have discontinued the desktop timeline viewer.

If you're like me, you have years worth of timeline data that you want to be able to view. This project does that.


![Alt text](/screenshot.png?raw=true "Screenshot")

### Features:
- Supports both Google Takeout data and new (as of late 2024) On-Device data file
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



## Get Your Data: Option 1, Google Takeout (for data prior to the change to on-device)
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
    - Extract the archive to anywhere you like, eg My Documents.
  
## Get Your Data: Option 2, On-Device data export
1. Open the Maps app, go to your Timeline, and click the export icon in the top right.
2. Transfer the JSON file to your computer, and save it anywhere you like, eg My Documents.
Note: On English-language devices, the filename is "Timeline.json", but this may differ on other systems. Rename the file to "Timeline.json" if needed.
   

##  Final Set Up
1. **Download The Google Maps Timeline Viewer:**
    - Save this project's `index.html` file anywhere you like, eg My Documents. (Click the index.html file, then click on "Raw" in the top-right of the content area. Copy/paste to eg Notepad and save as index.html)
   
4. **Add your API key:**
   - Open the index.html file in a text editor and find the code below, near the top:
     ```html
     <script src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&libraries=places"></script>
     ```
   - Replace `YOUR_API_KEY` with the key you obtained from the Google Cloud Console, and save.


## View Your Timeline
1. **Open the index.html File:**
    - Double-click the file to open it. Supported browsers include Chrome and Microsoft Edge. Firefox will unfortunately not work.
    - At the top left of the page, click Choose Folder and navigate to the folder that contains your Timeline data.
        - For Google Takeout data: The folder structure should be "Takeout\Location History (Timeline)\Semantic Location History". Once you are within the "Semantic Location History" folder, and see subfolders for each year, click "Select Folder" on the dialog. (Do not navigate into one of the year folders.)
        - For On-Device exported data: Simply choose the folder that contains your exported Timeline.json file.
    - Use the date picker to choose a date that contains timeline data.
