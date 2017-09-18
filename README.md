# Openbet Mocked services

## Services Mocked
- Getting a Ticket Granting Ticket (TGT)

## How to run
Navigate to the Openbet directory (this one) and run `canned` in your terminal or command prompt.

Canned runs by default on port 3000; you can change this if you like (-p 8080).

### Dependencies
This service depends on canned, which runs on node and is available in npm. Install it locally using:

`npm install -g canned`

If you need node and npm (on a mac) then you should use homebrew:

`brew install npm`

On Linux - use your package manager to install node.
On Windows - get the stable release from [nodejs.org](www.nodejs.org).

### Starting the mock service
In this directory you can launch an openbet Oxi API.

## How to create new mocks
Following the structure shown here, along with the documentation available at [canned](https://www.npmjs.com/package/canned) it should be possible to create further mocks.

Need more docs/examples?

official docs: http://sideshowcoder.github.io/canned/
and more examples here: https://github.com/sideshowcoder/canned/blob/master/spec/test_responses/

## Worked example
Run `canned`
Try it out for auth failed:
  `curl -i -H "Accept: application/x-www-form-urlencoded" -X POST -d "MyPassword" http://127.0.0.1:3000/cas/v1/tickets`
 Should show:
```
    HTTP/1.1 400 Bad Request
    Access-Control-Allow-Origin: *
    Access-Control-Allow-Headers: X-Requested-With
    Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS
    Date: Fri, 15 Sep 2017 03:13:53 GMT
    Connection: keep-alive
    Content-Length: 5
```

Try it out for auth success:
  `curl -i -H "Accept: application/x-www-form-urlencoded" -X POST -d "MyInvalidPassword" http://127.0.0.1:3000/cas/v1/tickets`
  Should show:
```
    HTTP/1.1 201 Created
    Access-Control-Allow-Origin: *
    Access-Control-Allow-Headers: X-Requested-With
    Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS
    Date: Fri, 15 Sep 2017 03:31:53 GMT
    Connection: keep-alive
    Content-Length: 483

    <!DOCTYPE HTML PUBLIC \"-//IETF//DTD HTML 2.0//EN\">
    <html>
        <head>
            <title>201 Created</title>
        </head>
        <body>
            <h1>TGT Created</h1>
            <form action="https://10.199.203.38:19501/cas/v1/tickets/TGT-21130-wzzrcbxp0MuhVxbuvJPbbO0y66hl5jXpXaRgB2zxbrJ4Rl2JjD-ip-10-199-203-38." method="POST">Service:
                <input type="text" name="service" value="">
                <br>
                <input type="submit" value="Submit">
            </form>
        </body>
    </html>%                
```
