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

* 9gag
* attractive
* bandicam
* brazzers
* dead
* deepfry
* depression
* desert
* disabled
* disguise
* emojiface
* garbage
* hassciencegonetoofar
* hypercam
* ifunny
* imadethis
* jackoff
* laid
* nooseguy
* objector
* picklerick
* spray
* ss
* stock
* uber
* ugly
* wdt
* wrong

These commands take extra (sometimes optional) parameters

* blur

| Argument | Description |
| - | - |
| `radius` | The radius of the circle it should blur with. |

* eyes

| Argument | Description |
| - | - |
| `eye` | The eye image. |

Available eyes: 'big', 'blood', 'blue', 'googly', 'green', 'horror', 'illuminati', 'money', 'normal', 'pink', 'red', 'small', 'spongebob', 'yellow';

* jpeg

| Argument | Description |
| - | - |
| `quality` | The jpeg quality 1-100. |

1% quality is the most compression an 100% quality is no compression.

* pixelate

| Argument | Description |
| - | - |
| `amount` | The amount of pixels to turn into one. |

e.g. 2 means 2x2 pixels would turn into one pixel.

* pornhub

| Argument | Description |
| - | - |
| `title` | The title the video should use. |

* reminder

| Argument | Description |
| - | - |
| `text` | The text that should be on the reminder. |

* rotate

| Argument | Description |
| - | - |
| `amount` | The amount of degrees an image should be rotated with. |

* sharpen

| Argument | Description |
| - | - |
| `amunt` | The amount (1 - 100) an image should be sharpened with. |

* watchmojo

| Argument | Description |
| - | - |
| `title` | The title of the watchmojo video. |

