# tvde1-api-documentation
Documentation of the tvde1-api.

This is an api I put together, mainly for image-manipulation commands, but also for other things.  

Base url:
##### `https://tvde1-api.herokuapp.com/api/` (Note: will probably change soon.)

Responses:
-

When an error has occured (not authorized or bad parameters) you'll get this body:

```json
{
    "success": false,
    "message": "the reason"
}
```

When a request has succeded you'll get a response like this:

```json
{
    "success": true,
    "result": {
    }
}
```
The result object will contain a route-specific property.

Authentication:
-

Most routes require you to have an auth token. You can obtain it at `/account/authenticate`.  
You must include it in your headers like this:  

`"Authorization": "Bearer [token]"`

Routes:
-

All requests have to be sent with `Content-Type: application/json` as they take json body.

/account
-

* `POST` /register

You can create a new account with this route.

JSON body:

```json
{
    "username": "your username",
    "password": "your password",
    "email":    "your email"
}
```

Result body:
```json
{
    "user": {
        "_id": "...",
        "username": "...",
        "email": "..."
    }
}
```

* `POST` /authenticate

You use this route to obtain your auth token.

JSON body:

```json
{
    "username": "your username",
    "password": "your password"
}
```

Request body:
```json
{
    "token": "...",
    "user": {
        "__id": "...",
        "username": "...",
        "email": "..."
    }
}
```

* `POST` /edit

This endpoint allows you to change your password/email.

JSON Body:

```json
{
    "username": "your username",
    "password": "your password",
    "newPassword": "your optional new password",
    "email": "your optional new email"
}
```
You can leave `newPassword` and `email` out.

The result will contain your new user object.

* `POST` /delete

This endpoint will delete your account.

JSON Body:

```json
{
    "username": "your username",
    "password": "your password"
}
```

This will respond with `success: true`.

/image-manipulation
-

You need to supply an auth token to use these routes.  

Image-manipulation commands take this json body:

```
{
    "images": [],
    "args" {}
}
```
`images` is an array of urls.  
`args` is an object with keys and values.

The returned `result` will be:
```json
{
    "image": "..."
}
```
The image will be encoded in a base64 string.

These are the routes that use the standard format:

* `POST` /9gag
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/9gag.png)

* `POST` /attractive
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/attractive.png)

* `POST` /bandicam
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/bandicam.png)

* `POST` /brazzers
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/brazzers.png)

* `POST` /dead
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/dead.png)

* `POST` /deepfry
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/deepfry.png)

* `POST` /depression
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/depression.png)

* `POST` /desert
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/desert.png)

* `POST` /disabled
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/disabled.png)

* `POST` /disguise // Requires face
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/disguise.png)

* `POST` /emojiface // Requires face
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/emojiface.png)

* `POST` /fear
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/fear.png)

* `POST` /garbage
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/garbage.png)

* `POST` /hassciencegonetoofar
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/hassciencegonetoofar.png)

* `POST` /hypercam
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/hypercam.png)

* `POST` /ifunny
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/ifunny.png)

* `POST` /imadethis
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/imadethis.png)

* `POST` /jackoff
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/jackoff.png)

* `POST` /laid
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/laid.png)

* `POST` /nooseguy
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/nooseguy.png)

* `POST` /objector
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/objector.png)

* `POST` /picklerick
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/picklerick.png)

* `POST` /spray
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/spray.png)

* `POST` /ss
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/ss.png)

* `POST` /stock
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/stock.png)

* `POST` /uber
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/uber.png)

* `POST` /ugly
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/ugly.png)

* `POST` /wdt
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/wdt.png)

* `POST` /wrong
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/wrong.png)

These commands take extra (sometimes optional) parameters

* `POST` /blur

| Argument | Description |
| - | - |
| `radius` | The radius of the circle it should blur with. |

* `POST` /eyes
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/eyes.png)

| Argument | Description |
| - | - |
| `eye` | The eye image. |

Available eyes: 'big', 'blood', 'blue', 'googly', 'green', 'horror', 'illuminati', 'money', 'normal', 'pink', 'red', 'small', 'spongebob', 'yellow';

* `POST` /jpeg

| Argument | Description |
| - | - |
| `quality` | The jpeg quality 1-100. |

1% quality is the most compression an 100% quality is no compression.

* `POST` /pixelate

| Argument | Description |
| - | - |
| `amount` | The amount of pixels to turn into one. |

e.g. 2 means 2x2 pixels would turn into one pixel.

* `POST` /pornhub
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/pornhub.png)

| Argument | Description |
| - | - |
| `title` | The title the video should use. |

* `POST` /reminder
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/reminder.png)

| Argument | Description |
| - | - |
| `text` | The text that should be on the reminder. |

* `POST` /rotate

| Argument | Description |
| - | - |
| `amount` | The amount of degrees an image should be rotated with. |

* `POST` /sharpen

| Argument | Description |
| - | - |
| `amount` | The amount (1 - 100) an image should be sharpened with. |

* `POST` /watchmojo
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/watchmojo.png)

| Argument | Description |
| - | - |
| `title` | The title of the watchmojo video. |

/other
-

These are some more tools that don't fit in the other categories.  
They also require authentication.

* `POST` /captionbot

Takes one image and returns a `message` property with what it thinks is in the image.

* `POST` /screenshot
[Image](https://raw.githubusercontent.com/Tvde1/tvde1-api-documentation/master/Images/screenshot.png)

Takes a `url` argument and returns an `image` property (as a base64 string).
