# tvde1-api-documentation
Documentation of the tvde1-api.

This is an api I put together, mainly for image-manipulation commands, but also for other things.  
Most routes require authorization.

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

`"Authentication": "Bearer [token]"`

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
Adds the 9gag watermark.

* `POST` /attractive  
[I find these styles very attractive on guys](https://cdn.discordapp.com/attachments/323084621241909259/381549338943553567/attractive.png)

* `POST` /bandicam  
Adds the bandicam watermark.

* `POST` /brazzers  
Adds the brazzers watermark.

* `POST` /dead  
Adds a minecraft death screen overlay.

* `POST` /deepfry  
"Deep fries".

* `POST` /depression  
[We asked her to draw what depression feels like.](https://media.discordapp.net/attachments/323084621241909259/381557515818762241/depression.png)

* `POST` /desert

* `POST` /disabled

* `POST` /disguise

* `POST` /emojiface

* `POST` /fear

* `POST` /garbage

* `POST` /hassciencegonetoofar

* `POST` /hypercam

* `POST` /ifunny

* `POST` /imadethis

* `POST` /jackoff

* `POST` /laid

* `POST` /nooseguy

* `POST` /objector

* `POST` /picklerick

* `POST` /spray

* `POST` /ss

* `POST` /stock

* `POST` /uber

* `POST` /ugly

* `POST` /wdt

* `POST` /wrong

These commands take extra (sometimes optional) parameters

* `POST` /blur

| Argument | Description |
| - | - |
| `radius` | The radius of the circle it should blur with. |

* `POST` /eyes

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

| Argument | Description |
| - | - |
| `title` | The title the video should use. |

* `POST` /reminder

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

Takes a `url` argument and returns an `image` property (as a base64 string).

---

Someone improve this with examples for me lol
