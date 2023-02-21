# Simple Mock Server with Wiremock

MockServer is designed to simplify integration testing, by mocking API responses, to a team to develop against a service that is incomplete or is unstable.

** WireMock

* WireMock is a popular and flexible open source mock server tool for HTTP-based APIs.
* It works by creating an actual HTTP server that your code under test can connect to as it would a real web service.
* It supports HTTP response stubbing, request verification, proxy/intercept, record/playback of stubs and fault injection, and can be used from within a unit test or deployed into a test environment.
* Download jar and start server locally. __files and mappings folders are automatically created under the root directory once the server is started.
* Add stubbed responses under __files and rules for matching under mappings. Directory structure should not matter.
* Restart server and send the mapped request from any client like Postman.


To run the mockserver:

1. Clone the repo. 
2. Download standalone jar file by running this command from terminal:
curl -fsSL "https://repo1.maven.org/maven2/com/github/tomakehurst/wiremock-jre8-standalone/2.35.0/wiremock-jre8-standalone-2.35.0.jar" -o "wiremock-standalone.jar"
3. Start the server locally
java -jar wiremock-standalone.jar --port 9000 --global-response-templating --verbose --root-dir app

** Request URL matching logic
* Equality matching on the path only : "urlPath": "/your/url/"
* Equality matching on path and query: "url": "/your/url?and=query/"
* Regex matching on the path only    : "urlPathPattern": "/your/([a-z]*)"
* Regex matching on path and query   : "urlPattern": "/your/([a-z]*)\\?and=query"


* Match query parameters with regular expression: 
{
  "request": {
  ...
  "queryParameters" : {
  "search_term" : {
  "matches" : "^(.*)wiremock([A-Za-z]+)$"
  }
  }
  ...
  }

More info: https://wiremock.org/docs/request-matching/

