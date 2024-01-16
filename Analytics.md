# Score Extension Analytics

This file tracks all existing analytics that exist in the [Score browser extension](https://getscore.app). 

Score Users: Your data is never sold, and is used as analytics to make Score more useful. You can view Score's Privacy Policy [here](https://getscore.app/privacy).

Score currently uses Mixpanel to store its analytics. For details on Mixpanel's privacy policy, please click [here](https://mixpanel.com/legal/privacy-policy/).

## Common Properties

These are properties that are tracked for every event that is fired. These help us understand what browser and Score extension version a user is on, for debugging purposes.

### userAgent

1. Example: `Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36`
2. Description: User agent of a browser

### userAgentBrowserName

1. Example: `Chrome`
2. Description: User agent browser name

### userAgentBrowserVersion

1. Example: `120.0.0.0`
2. Description: User agent browser version

### userAgentOSName

1. Example: `Mac OS`
2. Description: User agent OS name

### userAgentOSVersion

1. Example: `10.15.7`
2. Description: User agent OS version

### Score Extension Version

1. Label: `extensionVersion`
2. Example: `1.9.0`
3. Description: Score extension version number

# Events

## modal_performImageSearch

Fired when the extension makes a search automatically.

### windowLocationHref

1. Example: `https://www.amazon.com/dp/B096X9LGJ1`
2. Description: Current URL that the user is on

### imageUrl

1. Example: `https://m.media-amazon.com/images/I/61A3ePViuoL._AC_SX679_.jpg`
2. Description: Image, if any that helps with the search

## modal_performImageSearchRightClick

Fired when the extension makes a search by a right-click initiation from the user.

### windowLocationHref

1. Example: `https://www.amazon.com/dp/B096X9LGJ1`
2. Description: Current URL that the user is on

### imageUrl

1. Example: `https://m.media-amazon.com/images/I/61A3ePViuoL._AC_SX679_.jpg`
2. Description: Image, if any that helps with the search

## modal_performImageSearchCropSearch

Fired when the extension makes a search by a crop search initiation from the user.

### windowLocationHref

1. Example: `https://www.amazon.com/dp/B096X9LGJ1`
2. Description: Current URL that the user is on

### imageUrl

1. Example: `https://m.media-amazon.com/images/I/61A3ePViuoL._AC_SX679_.jpg`
2. Description: Image, if any that helps with the search

## extension_performImageSearchComplete

Fired when the extension is done finding and aggregating results.

### windowLocationHref

1. Example: `https://www.amazon.com/dp/B096X9LGJ1`
2. Description: Current URL that the user is on

### searchType

1. Example: `default`
2. Description: Type of search that user performed (default/automatic, right click or screenshot)

### identicalResultsLength

1. Example: `3`
2. Description: Number of identical results returned by Score

### similarResultsLength

1. Example: `5`
2. Description: Number of similar results returned by Score

### identicalResultsTimeTaken

1. Example: `5.0`
2. Description: Time it took to find identical options

### similarResultsTimeTaken

1. Example: `5.0`
2. Description: Time it took to find similar options

## extension_noSimilarResultsFound

Fired when the extension cannot find any similar results.

No additional properties are attached.

## extension_firstTimeOnboard

Fired when a user installs the extension for the first time.

No additional properties are attached.

## extension_updateVersion

Fired when a user updates the extension.

No additional properties are attached.

## extension_setNewDistinctId

Fired when a user logs in to Score on the web.

### id

1. Example: `123`
2. Description: ID of Score user

## extension_setUserComplete

Fired when a user logs in to Score on the web, and the extension acknowledges it.

No additional properties are attached.

## extension_getToastSuccess

Fired when new notifications are fetched from Score's servers successfully.

### title

1. Example: `Check Out Our Blog`
2. Description: Title of the notification

### link

1. Example: `https://blog.getscore.app`
2. Description: Link that notification goes to when clicked from the extension

## extension_getToastError

Fired when new notifications fail to be fetched from Score's servers.

### errorString

1. Example: `Error: Failed to fetch notification from server`
2. Description: Descriptive error string when the toast fails to be fetched

## extension_getFeatureFlagsSuccess

Fired when new feature flags are fetched from Score's servers successfully.

### featureFlags

1. Example: `{shouldEnableHoverButton: false}`
2. Description: Feature flags that determine experiments within Score.

## extension_getFeatureFlagsError

Fired when new feature flags fail to be fetched from Score's servers.

### errorString

1. Example: `Error: Failed to fetch notification from server`
2. Description: Descriptive error string when the toast fails to be fetched

## modal_didYouFind_1_yes

Fired when clicking Yes in the Did You Find modal after a user navigates back to Score from a product page.

No additional properties are attached.

## modal_didYouFind_1_no

Fired when clicking No in the Did You Find modal after a user navigates back to Score from a product page.

No additional properties are attached.

## modal_didYouFind_review_yes

Fired when clicking Yes in the Did You Find - Review modal after a user navigates back to Score from a product page.

No additional properties are attached.

## modal_didYouFind_review_later

Fired when clicking Later in the Did You Find - Review modal after a user navigates back to Score from a product page.

No additional properties are attached.

## modal_didYouFind_2_no

Fired when clicking an option in the Did Not Find modal after a user navigates back to Score from a product page.

### option

1. Example: `Incorrect price`
2. Description: Reason for why user did not find the right product using Score

## modal_closePostResults

Fired when a user closes the Did You Find Modal.

No additional properties are attached.

## sticky_openExtension

Fired when user clicks the Score sidebar hover button on any product page.

No additional properties are attached.

## modal_openoptions

Fired when user clicks the Score '5 cheaper options' that is located on a product page.

### pageType

1. Example: `amazon`
2. Description: Page that a user is on

### cheaperResultsLength

1. Example: `5`
2. Description: Number of cheaper results

### loading

1. Example: `false`
2. Description: Whether the page is still loading or not when button was clicked

## modal_amazonCannotParseBox

Fired when Score is unable to parse an Amazon product page.

No additional properties are attached.

## modal_cannotParseJsonLd

Fired when Score is unable to parse a product page that has JSON-LD.

No additional properties are attached.

## modal_cannotFindImage

Fired when Score is unable to find an image on the current page.

No additional properties are attached.

## page_cannotLoadOnPageLoadOrChange

Fired when Score is unable to parse current page. Generic error.

### errorName

1. Example: `TypeError`
2. Description: Type of error that Score encountered while parsing

### errorMessage

1. Example: `Unable to understand type on page`
2. Description: Description message of error that Score encountered while parsing

## modal_rateResults

Fired when a user rates the current results that Score provides

### stars

1. Example: `5`
2. Description: Number of stars that a user rates

## extension_clickToast

Fired when a user clicks the notification toast within Score.

### title

1. Example: `Check Out Our Blog`
2. Description: Title of the notification

### link

1. Example: `https://blog.getscore.app`
2. Description: Link that notification goes to when clicked from the extension

## modal_clickLogo

Fired when a user clicks the Score logo within the extension.

No additional properties are attached.

## modal_closeExtension

Fired when a user closes the Score popup window.

No additional properties are attached.

## modal_clickManufacturerSite

Fired when a user clicks through to the manufacturer's site in the result list.
No additional properties are attached.

## modal_clickResult

Fired when a user rates the current results that Score provides

### title

1. Example: `Vera Dress`
2. Description: Title of the result

### urlTitle

1. Example: `asos.com`
2. Description: Merchant name of the result

### price

1. Example: `US$9.40`
2. Description: Price of the result

### url

1. Example: `https://www.asos.com/au/vero-moda/vero-moda-wrap-midi-dress-with-flutter-sleeves-in-pink/prd/204532007`
2. Description: Link of the product that was clicked

### type

1. Example: `2`
2. Description: Result type (Identical / Similar search)

## modal_filterResultsText

Fired when a user filters the results with text.

### filterText

1. Example: `asos`
2. Description: Filter text that a user types
