# JShip
For general information visit the [parent repository](https://github.com/omniti-labs/jsend)

## Changes ##

The fail return type is now the same as error, just with different purposes

<table>
<tr><th>Type</td><th>Description</th><th>Required Keys</th><th>Optional Keys</td></tr>
<tr><td>success</td><td>All went well, and (usually) some data was returned.</td><td>status, data</td><td></td></tr>
<tr><td>fail</td><td>There was a problem with the data submitted, or some pre-condition of the API call wasn't satisfied</td><td>status, message</td><td>code, data</td></tr>
<tr><td>error</td><td>An error occurred in processing the request, i.e. an exception was thrown</td><td>status, message</td><td>code, data</td></tr>
</table>

## Fail ### 
When an API call is rejected due to invalid data or call conditions. For example:
#### POST /posts.json (with data body: "Trying to creating a blog post"): ####
```
{
    "status" : "fail",
    "message" : "A title is required"
}
```
Required keys:
* status: Should always be set to "fail".
* message: A meaningful, end-user-readable (or at the least log-worthy) message, explaining what went wrong.

Optional keys:
* code: A numeric code corresponding to the error, if applicable
* data: A generic container for any other information about the fail, i.e. the conditions that caused the fail, wrong parameters, etc. If the reasons for failure correspond to POST values, the response object's keys SHOULD correspond to those POST values.

## License ##
The JShip specification (this page) is covered under the same license as its parent project: [modified BSD License](LICENSE.md)



