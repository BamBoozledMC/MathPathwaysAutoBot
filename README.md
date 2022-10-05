# ![Logo](/images/mp64.png) Maths Pathways Auto Completer Bot
**Please note this is a proof of concept and I do not intend for it to be used in malicious ways.**

---

## Some Context & info
From the first time I used Math Pathways I've been eager to make some sort of tool that automates the proccess of clicking through all the questions for me. I had tried multiple ways including attempting to make a browser extension, nodeJS script, and python script but all of those had some sort of limitation. This is until I came across a tool called [Power Automate
](https://apps.microsoft.com/store/detail/power-automate/9NFTCH6J7FHV) made by Microsoft. It allows you to automate many things including browsers (via the use of a browser extension added by the program)

## How do I do this Myself?
Below you will find some videos and screenshots of this program working, and a tutorial to set it up yourself.

### What you will need
- A Windows system
- A Microsoft account (required for Power Automate)
- [Power Automate desktop program](https://apps.microsoft.com/store/detail/power-automate/9NFTCH6J7FHV)
- Chrome (for easiest setup) or any other browser
- Math Pathways account
- Decent experience with Windows and/or Programming

### Installing Power Automate
First and foremost, you must install [Power Automate](https://apps.microsoft.com/store/detail/power-automate/9NFTCH6J7FHV) from the Microsoft store.

<details>
  <summary><strong>Show Image(s)</strong></summary>

  ![Power Automate on the Microsoft Store](/images/PAMSStore.png)
</details>

Once installed you'll need to login with your Microsoft account.  
Simply enter the email address associated with your Microsoft Account.

<details>
  <summary><strong>Show Image(s)</strong></summary>

  ![Power Automate Sign In](/images/signinPA.png)
</details>

### Installing browser extension/add-on
For this program to work properly you'll also need the browser extension for your browser of choice
- [Chrome](https://chrome.google.com/webstore/detail/microsoft-power-automate/gjgfobnenmnljakmhboildkafdkicala)
- [Firefox](https://addons.mozilla.org/en-US/firefox/addon/power-automate-desktop/)
- [Edge](https://microsoftedge.microsoft.com/addons/detail/microsoft-power-automate/njjljiblognghfjfpcdpdbpbfcmhgafg)  

Installing the extension should be quite straightforward

<details>
  <summary><strong>Show Image(s)</strong></summary>

  ![Chrome Extension](/images/chromeext.png)
</details>

### Creating the flow
Now we have everything we need setup, it's time to create the flow!  
If you followed the intructions correctly you should be at the Power Automate home/dashboard, simply click "New flow" and then name your flow whatever you wish.

<details>
  <summary><strong>Show Image(s)</strong></summary>

  ![Power Automate home](/images/PAhome.png)
  ![Name your flow](/images/createflow.png)
</details>

### Adding the code
After creating the flow, you should see a window open that says "You don't have any actions here yet".

<details>
  <summary><strong>Show Image(s)</strong></summary>

  ![Your flow window](/images/floweditblank.png)
</details>

If you're at the right place, you're ready to add the code!  

```{css, echo=FALSE}
.scroll-100 {
  max-height: 100px;
  overflow-y: auto;
  background-color: inherit;
}

test asdjhkl fjklasjkld fjhklasdfasjdfhasdjkl fhsjklad fhas jhkldjljhjhadshjkl fljka  jajlsdhkf 
```
```SET MPClass TO $'''https://your-mathpathway-class-URL.com''' WebAutomation.LaunchChrome.LaunchChrome Url: MPClass WindowState: WebAutomation.BrowserWindowState.Normal ClearCache: False ClearCookies: False WaitForPageToLoadTimeout: 60 Timeout: 60 BrowserInstance=> Browser WAIT 2 IF (WebAutomation.IfWebPageContains.WebPageDoesNotContainText BrowserInstance: Browser Text: $'''Continue activity''') THEN     Display.ShowMessageDialog.ShowMessage Title: $'''Login''' Message: $'''Please login then click \"OK\" when done''' Icon: Display.Icon.Information Buttons: Display.Buttons.OK DefaultButton: Display.DefaultButton.Button1 IsTopMost: True ButtonPressed=> ButtonPressed END WebAutomation.GoToWebPage.GoToWebPage BrowserInstance: Browser Url: $'''%MPClass%/work''' WaitForPageToLoadTimeout: 60 WAIT 2 Display.ShowMessageDialog.ShowMessage Title: $'''MP Auto Bot ''' Message: $'''Start the MP Auto Bot by selecting \"OK\". Manually stop this flow to stop the bot''' Icon: Display.Icon.Warning Buttons: Display.Buttons.OK DefaultButton: Display.DefaultButton.Button1 IsTopMost: True ButtonPressed=> runbot LOOP WHILE ($'''true''') = ($'''true''')     MouseAndKeyboard.MoveMouseToTextOnScreenWithOCR.WaitForTextToAppearAndMoveMouseToTextOnScreenWithWindowsOcr TextToFind: $'''Check''' IsRegEx: False WindowsOcrLanguage: MouseAndKeyboard.WindowsOcrLanguage.English Occurence: 1 SearchForTextOn: MouseAndKeyboard.SearchTarget.EntireScreen ImageWidthMultiplier: 1 ImageHeightMultiplier: 1 MovementStyle: MouseAndKeyboard.MovementStyle.Instant Timeout: 5 PositionRelativeToText: MouseAndKeyboard.PositionOnImage.MiddleCenter OffsetX: 0 OffsetY: 0 X=> LocationOfTextFoundX Y=> LocationOfTextFoundY Width=> WidthOfTextFound Height=> HeightOfTextFound     ON ERROR         GOTO skipclick     END     MouseAndKeyboard.SendMouseClick.Click ClickType: MouseAndKeyboard.MouseClickType.LeftClick MillisecondsDelay: 0     WAIT 1     LABEL skipclick     IF (OCR.IfTextOnScreen.TextOnScreenExistsWithWindowsOcr TextToFind: $'''fast''' IsRegex: False WindowsOcrLanguage: OCR.WindowsOcrLanguage.English SearchForTextOn: OCR.SearchTarget.EntireScreen ImageWidthMultiplier: 1 ImageHeightMultiplier: 1 TextLocationX=> LocationOfTextFoundX2 TextLocationY=> LocationOfTextFoundY2) THEN         WAIT 1         MouseAndKeyboard.MoveMouseToTextOnScreenWithOCR.WaitForTextToAppearAndMoveMouseToTextOnScreenWithWindowsOcr TextToFind: $'''Continue''' IsRegEx: False WindowsOcrLanguage: MouseAndKeyboard.WindowsOcrLanguage.English Occurence: 1 SearchForTextOn: MouseAndKeyboard.SearchTarget.EntireScreen ImageWidthMultiplier: 1 ImageHeightMultiplier: 1 MovementStyle: MouseAndKeyboard.MovementStyle.Instant Timeout: 5 PositionRelativeToText: MouseAndKeyboard.PositionOnImage.MiddleCenter OffsetX: 0 OffsetY: 0 X=> LocationOfTextFoundX Y=> LocationOfTextFoundY Width=> WidthOfTextFound Height=> HeightOfTextFound                 ON ERROR                     GOTO skipclick                 END         MouseAndKeyboard.SendMouseClick.Click ClickType: MouseAndKeyboard.MouseClickType.LeftClick MillisecondsDelay: 0         WAIT 1     END     MouseAndKeyboard.MoveMouseToImage.ClickImage Images: [imgrepo['Image_2']] SearchForImageOn: MouseAndKeyboard.SearchTarget.EntireScreen MousePositionOnImage: MouseAndKeyboard.PositionOnImage.MiddleCenter OffsetX: 0 OffsetY: 0 Tolerance: 10 MovementStyle: MouseAndKeyboard.MovementStyle.Instant Occurence: 1 Timeout: 5 ClickType: MouseAndKeyboard.ClickType.LeftClick SecondsBeforeClick: 0 SearchAlgorithm: MouseAndKeyboard.ImageFinderAlgorithm.Legacy X=> X Y=> Y     ON ERROR      END     WAIT 1 END DISABLE END  # [ControlRepository][PowerAutomateDesktop]  {   "ControlRepositorySymbols": [],   "ImageRepositorySymbol": {     "Name": "imgrepo",     "ImportMetadata": {},     "Repository": "{\r\n  \"Folders\": [],\r\n  \"Images\": [\r\n    {\r\n      \"Id\": \"0c8cf720-9f18-4209-91f6-1572cc1779cf\",\r\n      \"Name\": \"Image_2\",\r\n      \"Screenshot\": \"iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAAANSURBVBhXY2BYPvM/AAQrAkD6JlbeAAAAAElFTkSuQmCC\",\r\n      \"ScreenshotPath\": \"imageRepo-screenshots\\\\\\\\cf7be69e-c637-408a-908d-cc78cce1bc20.png\"\r\n    }\r\n  ],\r\n  \"Version\": 1\r\n}"   },   "ConnectionReferences": [] }```
