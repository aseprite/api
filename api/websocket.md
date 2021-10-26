# WebSocket

## WebSocket()

```lua
local ws = WebSocket()
local ws = WebSocket{
    url = string,
    onreceive = function(message, data),
    deflate = bool,
    minreconnectwait=number,
    maxreconnectwait=number
}
```

Creates a websocket client that can be used to communicate with
another program:

* `url` specifies the server to connect.
* `deflate` option enables compression before sending the data - if
  the server is running on the same machine, it might be faster to
  turn it off.
* `onreceive` function will be called for every incoming message, and
  when the connection is established and broken. Its two arguments are
  the event type (see
  [`WebSocketMessageType`](websocketmessagetype.md#websocketmessagetype))
  and the received data (a string, can be empty).
* `minreconnectwait` and `maxreconnectwait` (in seconds) are optional
  values that limit the waiting time to try a reconnection to the
  server.

Example:

```lua
local function handleMessage(mt, data)
  if mt == WebSocketMessageType.OPEN then
    print("Connection open. Sending a message...")
    ws:sendText("Hello!")

  elseif mt == WebSocketMessageType.TEXT then
    print("Message recived: " .. data)
    ws:close()

  elseif mt == WebSocketMessageType.CLOSE then
    print("Connection closed")
  end
end

local ws = WebSocket{
    onreceive = handleMessage,
    url = "http://127.0.0.1:9000",
    deflate = false
}
```

## WebSocket.url

```lua
local server = ws.url
```

Address of the server. Read-only, the url is specified when creating
the websocket.

## WebSocket:connect()

Try connecting to the server. After a successful connection,
`onreceive` function will be called with message type
`WebSocketMessageType.OPEN`. When the server or network breaks the connection,
the client tries reconnecting automatically.

## WebSocket:close()

Disconnects from the server. After a disconnect, `onreceive` function
will be called with message type `WebSocketMessageType.CLOSE`.

## WebSocket:sendText()

```lua
WebSocket:sendText(str1, str2, ...)
```

Sends a text message to the server. If multiple strings are passed,
they will be joined together.

## WebSocket:sendBinary()

```lua
WebSocket:sendBinary(bstr1, bstr2, ...)
```

Sends a binary message to the server. If multiple strings are passed,
they will be joined together. Lua makes no distinction between
character and byte strings, but the websocket protocol does label
them.

## WebSocket:sendPing()

```lua
WebSocket:sendPing(str)
```

Sends a very short ping message to the server. There's a limit to the
length of data that can be sent. It's sometimes used to prevent the
connection from timing out and closing. A standard compliant server
will reply to every "ping" message with a "pong". Client pongs are
sent automatically, and there's no need to control that.
