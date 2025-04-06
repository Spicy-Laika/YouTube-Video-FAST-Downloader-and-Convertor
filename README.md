![Screenshot](https://12388101.xyz/fls/image.jpg)

# YouTube Video FAST Downloader and Convertor
The ✨  YouTube Video/Shorts/Audio FAST Downloader 24/7 offers a reliable solution for downloading videos in MP4 or WEBM formats across various resolutions, from 144p to 1080p. 

### Features:

- **Multiple Formats:** Download Video/Shortus/Audio in MP4 or WEBM, etc formats for compatibility with various devices and platforms. 
- **Custom Resolutions:** Choose from a wide range of resolutions, including 144p, 360p, 720p, and up to 1080p, for optimal viewing quality.
- **Fast and Reliable:** Enjoy quick processing and stable downloads 24/7
- **Ease of Integration**: Simple endpoints and clear documentation for quick implementation.

### Use Cases:
- Build a personal content downloader.
- Integrate YouTube videos to your app.

### Supported Formats:
- **Video**: MP4, WEBM
- **Audio**: MP4, OPUS
- **Resultion**: 144p, 240p, 360p, 480p, 720p, 1080p

[Try the API now and get instant results](https://api999.short.gy/TS3hRV)

How to use? Easy!
-----------

Download video in three steps.

1) Get information about available formats audio and video quality using the **"Get Audio/Video Quality Options"**  or **"Get Audio/Video Details and Quality"** method. Select the required video quality `id`
2. Send a request to download the video using the **"Get Audio/Video/Shorts Download URL"** method. In response, you receive a link with a video file.
3. The video file will return a 404 error initially but will become available within 15-120 seconds, depending on server load and file size. Check availability every 5-10 seconds. Once ready, the file can be downloaded within 10 minutes.


#### What is **videoId**?

The videoId is the unique identifier for a YouTube video.

For example, if the Shorts URL is:
https://www.youtube.com/shorts/86wbvJofPqU

Then the **videoId** is the part of the URL after the last slash:
**86wbvJofPqU**.

Examples
---

Each video has its own available formats, so it is necessary to make a request to obtain the required quality before each download.

### So make first

`/get_available_quality/{VideoId}`

Return 

```
[
{"id":137,
"quality":"1080p",
"bitrate":1923596,
"type": "video",
"size":"13078379",
"mime":"video\\/mp4; codecs=\\\"avc1.640028\\\""},

{"id":243,
"quality":"360p",
"type": "video",
"bitrate":188656,
"size":"1148448\",\"mime\":\"video\\/webm; codecs=\\\"vp9\\\""},

{"id":85,
"bitrate":79426,
"type": "audio",
"size":"436328,
"mime":"audio\\/mp4; codecs=\\\"avc1.4d400c\\\""}
]
```

### Then make

`/download_video/{videoId}?quality=137`

or

`/download_short/{videoId}?quality=137`

or

`/download_audio/{videoId}?quality=251`

Return 
```
{"id":137,
"quality":"720p",
"bitrate":1448651,
"size":"9295813",
"mime":"video/webm;codecs=\"vp9\"",
"file":"https://url.for.down/dl-fgdg33435345.mp4",
"comment":"The file will soon be ready. Until it is ready, attempting to access it will return a 404 error. The file will be available for download only 10 minutes"}
```

Next, you need to check the `file` every 5-10 seconds.

Initially, the file will return a 404 error, but within 15-120 seconds, depending on the file size and server load, the file will be available.

After that, you will have 10 minutes to download the file, after which it will no longer be available.

----
### Methods API:

####  **Get Audio/Video Quality Options - `/get_available_quality/{VideoId}`**
Accepts only one parameter - `VideoId`

Answer:
```
[{"id":243,
"quality":"360p",
"bitrate":188656,
"type": "video",
"size":"1148448\",
"mime":"video\\/webm; codecs=\\\"vp9\\""},

{"id":160,
"quality":"144p",
"bitrate":79426,
"size":"436328,
"type": "video",
"mime":"video\\/mp4; codecs=\\\"avc1.4d400c\\\""},

{"id":140,
"bitrate":79426,
"size":"436328,
"type": "audio",
"mime":"audio\\/mp4; codecs=\\\"avc1.4d400c\\\""}]
```
*Please note that the information about the video file `size` is not accurate because it does not include the size of the audio track.*

####  **Get Audi/Video/Shorts Download Url** 
`/download_video/{VideoId}?quality={quality}` or
`/download_short/{VideoId}?quality={quality}` or
`/download_audio/{VideoId}?quality={quality}`

Accepts only two parameters - `VideoId` *(example DSffICxyj3A)* and `quality` - `id` from "Get Video Quality Options" method 

Answer:
```
{"id":137,
"quality":"720p",
"bitrate":1448651,
"size":"9295813",
"mime":"video/webm;codecs=\"vp9\"",
"file":"https://url.for.down/dl-fgdg33435345.mp4",
"comment":"The file will soon be ready. Until it is ready, attempting to access it will return a 404 error. The file will be available for download only 10 minutes"}
```

####  **Get Video Info - `/get-video-info/{videoId}`**

**title**

Description: The title of the video.

*Example value: "How to create an NFT collection | Thirdweb".*

**description**

Description: The video description, including text information and links.

*Example value: "In this video I show you how to create an NFT collection using Thirdweb. You'll learn how to use Thirdweb's no-code web app to create an ERC-721 smart contract for your NFT...".*

**author**

Description: The author of the video.
*Example value: "Sean Watase".*

**lengthSeconds**

Description: The duration of the video in seconds.



**viewCount**

Description: The number of views for the video.

**keywords**

Description: A list of keywords related to the video.

*Example value: ["thirdweb nft", "erc721 smart contract", "how to make money with nfts"].*

**isLiveContent**

Description: Indicates whether the video is a live stream.

**thumbnail**

Description: A list of video thumbnail images with their resolutions.
Example value:

```
[
  {
    "url": "https://i.ytimg.com/vi/DSffICxyj3A/maxresdefault.jpg",
    "width": 1280,
    "height": 720
  }
]
```

**embed.iframeUrl**

Description: URL for embedding the video in an iframe.

*Example value: "https://www.youtube.com/embed/DSffICxyj3A".*

**embed.width and embed.height**

Description: The width and height of the embedded video.

**ownerProfileUrl**

Description: The profile URL of the video owner.
Example value: "http://www.youtube.com/@SeanWatase".

**externalChannelId**

Description: The external ID of the channel.
Example value: "UChjGu9jkMSz_A2qQV1G-Y9w".

**isFamilySafe**

Description: Indicates whether the video is family-friendly.

**availableCountries**

Description: A list of countries where the video is available.
Example value: ["US", "GB", "CA", "AU"].

**category**

Description: The category of the video.
*Example value: "Science & Technology".*

**publishDate and uploadDate**

Description: The publication and upload dates of the video.
*Example values:
publishDate: "2022-10-14T11:51:29-07:00".
uploadDate: "2022-10-14T11:51:29-07:00".*

**isUnlisted**
Description: Indicates whether the video is unlisted.

**availableQuality**
Description: the same as answer of method ``/get_available_quality/VideoId`` Example:
```
[{"id":243,
"quality":"360p",
"bitrate":188656,
"size":"1148448\",\"mime\":\"video\\/webm; codecs=\\\"vp9\\\""},

{"id":160,
"quality":"144p",
"bitrate":79426,
"size":"436328,
"mime":"video\\/mp4; codecs=\\\"avc1.4d400c\\\""}
]
```

---
 [See the API in action – test it instantly here ](https://api999.short.gy/TS3hRV)

---

### **Feel free to write to me with any questions not listed in the documentation! :)**

If you have any inquiries or need further assistance, don’t hesitate to reach out. I’m here to help!

#### **Telegram Support:**

You can easily reach me on Telegram group for quick support or any additional questions.

https://t.me/+Zlto9kxqYjthYTQy
