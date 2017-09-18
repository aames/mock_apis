# Mock services

## Services Mocked
- Getting a Token

## How to run
Navigate to the root directory (this one) and run `canned` in your terminal or command prompt.

Canned runs by default on port 3000; you can change this if you like (-p 8080).

### Dependencies
This service depends on canned, which runs on node and is available in npm. Install it locally using:

`npm install -g canned`

If you need node and npm (on a mac) then you should use homebrew:

`brew install npm`

On Linux - use your package manager to install node.
On Windows - get the stable release from [nodejs.org](www.nodejs.org).

### Starting the mock service
In this directory you can launch a fake API. Just run `canned`

## How to create new mocks
Following the structure shown here, along with the documentation available at [canned](https://www.npmjs.com/package/canned) it should be possible to create further mocks.

Need more docs/examples?

official docs: http://sideshowcoder.github.io/canned/
and more examples here: https://github.com/sideshowcoder/canned/blob/master/spec/test_responses/

## Worked example
Run `canned`
Try it out for a GET:
  `curl -i -H "Accept: application/json" -X GET http://127.0.0.1:3000/content/foo`
 Should show:
```
    HTTP/1.1 200 OK
    Content-Type: application/json
    Access-Control-Allow-Origin: *
    Access-Control-Allow-Headers: X-Requested-With
    Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS
    Date: Mon, 18 Sep 2017 00:32:43 GMT
    Connection: keep-alive
    Content-Length: 13

    {"foo":"bar"}%   
```

Try it out for a POST:
  `curl -i -H "Accept: application/json" -X POST -d "token" http://127.0.0.1:3000/content/foo`
  Should show:
```
    HTTP/1.1 201 Created
    Content-Type: application/json
    Access-Control-Allow-Origin: *
    Access-Control-Allow-Headers: X-Requested-With
    Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS
    Date: Mon, 18 Sep 2017 00:33:46 GMT
    Connection: keep-alive
    Content-Length: 17

    {"Token":"fubar"}%               
```
