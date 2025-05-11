# Google Maps Timeline Viewer
Google announced in 2024 that they would begin storing your Timeline data (ie your Location History) locally on your device, rather than in the cloud on their systems. The desktop version of their timeline viewer was also discontinued, since the data is now on your phone.

If you're like me, you have years worth of timeline data that you want to be able to view. This project does that. It supports the old data format from Google Takeout, as well as the new on-device data format (which you can export from your device to your computer).



![Alt text](/screenshot.png?raw=true "Screenshot")

![Alt text](/screenshot2.png?raw=true "Screenshot 2")


### Features:
- Supports both Google Takeout data and On-Device data file (Android or iOS)
- Timeline and map view
- Place info and icons
- Duration of visits ; distance traveled
- Travel modes color-coded
- Direction of travel arrows when clicking a path
- View multiple days at once
- Toggle layers on and off, eg to view only places without the travel paths
- Summary of activities by year/month
- Place details retrieved from Google Places API can be saved locally, to reduce future API calls
  
#

Setup procedure:



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
1. Open the Maps app, go to your Timeline, and click ~~the export icon~~ the three dots in the top right, then "Location & privacy settings". Click where it says "Location is on", then click "Location services". Click "Timeline", then "Export Timeline data". Save the file as "Timeline.json". (On non-English devices, the default file name may be different -- be sure to save the file as "Timeline.json")
2. Transfer the JSON file to your computer, and save it anywhere you like, eg My Documents.
   

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
        - **Places API (New)**
    - You'll need to enable Billing to use the APIs. With normal use, you shouldn't incur any charges. See bottom of this doc for more info.

4. **Create API Key:**
    - Go to **APIs & Services > Credentials**.
    - Click "Create Credentials" and select "API Key".
    - Copy the generated API key.

5. **Restrict API Key (Optional):**
    - In the API key's settings, under **API restrictions**, select "Restrict key" and choose the APIs you enabled.


##  Final Set Up
1. **Download The Google Maps Timeline Viewer:**
    - Save this project's [timeline.html](https://raw.githubusercontent.com/kurupted/google-maps-timeline-viewer/refs/heads/main/timeline.html) file anywhere you like, eg My Documents. (Copy/paste to eg Notepad and save as eg "timeline.html")
   
4. **Add your API key:**
   - Open the timeline.html file in a text editor and find the code below, near the top:
     ```html
     <script>
		  window.GOOGLE_MAPS_API_KEY = "YOUR_API_KEY"; // Replace YOUR_API_KEY with your actual key
     ```
   - Replace `YOUR_API_KEY` with the key you obtained from the Google Cloud Console, and save.


## View Your Timeline
1. **Open the timeline.html File:**
    - Double-click the file to open it. Supported browsers include Chrome and Microsoft Edge. Firefox will unfortunately not work.
    - At the top left of the page, click Choose Folder and navigate to the folder that contains your Timeline data.
        - For Google Takeout data: The folder structure should be "Takeout\Location History (Timeline)\Semantic Location History". Once you are within the "Semantic Location History" folder, and see subfolders for each year, click "Select Folder" on the dialog. (Do not navigate into one of the year folders.)
        - For On-Device exported data: Simply choose the folder that contains your exported Timeline.json file.
    - Use the date picker to choose a date that contains timeline data.

## Note on API Usage & Billing
- You can find the free usage limits, and over-the-limit pricing here: https://developers.google.com/maps/billing-and-pricing/pricing#places-pricing
- Depending on what information is requested during the API call, it will fall into tiers, eg Essentials or Pro. Details here:
  https://developers.google.com/maps/billing-and-pricing/sku-details#place-details-pro-sku
- At this time, the monthly free limits are 1,000 Place Photos, 5,000 Pro-level requests, and 10,000 Essentials-level requests.
  
