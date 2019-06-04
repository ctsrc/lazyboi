# lazyboi -- the laziest possible way to send raw HTTP POST data

`lazyboi` is a bash script which makes it fast and easy to send raw HTTP POST
requests to servers, for example to send some JSON to an API end-point that you
are developing on your machine, or to send some test-data to an API that you
are integrating with.

Using `curl` for this purpose from the commandline can be cumbersome if you
have multiple headers that need to be specified, or if you are submitting
complex JSON data. Doubly so when you need to make changes to the request
headers and the data. Editing long commandline invocations; no bueno.

Several great tools exist for interacting with HTTP APIs. But sometimes those
tools are overkill and you just want to submit some headers and data, and to
tweak those headers and data a little bit all in one place in raw form.

That is what `lazyboi` lets you do -- it embeds a raw HTTP request that you
can easily edit with your favorite source code editor, and which you then
submit to the server by running the script. Edit and run. Edit and run.

Example embedded HTTP request:

```http
POST /hello/ HTTP/1.1
Host: $host:$port
User-Agent: lazyboi/$script_version
Accept: application/vnd.example.api-v2.hello+json, application/json;q=0.8, */*;q=0.2
Connection: close
Authorization: Bearer ~Un8G-M238/5S/+=
X-Quux: 42
Content-Length: $content_length
Content-Type: application/json

{
  "baz": true,
  "hoge": "Wibble, wobble!"
}
```

## Usage

```bash
lazyboi _dest_ [_port_]
```

```bash
lazyboi -v
```

```bash
lazyboi -h
```

## Options and arguments

`-v`, `--version`: Display the script version.

`-h`, `--help`: Display usage information and examples.

*dest*: Numerical IP address or a symbolic hostname.

*port*: Numeric port number.

## Examples

Send your HTTP request to a server listening on port 8080 of localhost.

```bash
lazyboi 127.0.0.1 8080
```

Send your HTTP request to the default port (80) of www.example.com.

```bash
lazyboi www.example.com
```

## Installation

If you retrieved `lazyboi` by means of git clone then it should already be
executable. Otherwise, make it so that it is; `chmod 755 lazyboi`.

Put `lazyboi` in some directory that is in your `$PATH`. For example,
if you have `~/bin/` in your `$PATH` then that is an appropriate place to
put it.

If `~/bin/` is not in your `$PATH` or `~/bin/` does not exist then you should
crate `~/bin/` and add it to your `$PATH`, and then `~/bin/` is an appropriate
place to put `lazyboi` for you as well.
