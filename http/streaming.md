# What is HTTP Streaming?
HTTP Streaming is a push-style data transfer technique that allows a web server to continuously send data to a client over a single HTTP connection that remains open indefinitely. Technically, this goes against HTTP convention, but HTTP Streaming is an efficient method to transfer all kinds of dynamic or otherwise streamable data between the server and client without reinventing HTTP.

# How HTTP Streaming Works
With HTTP Streaming, the server is configured to hold on to a specific request from a client and keep the response open so that it can push data through it. When updates pertaining to the request are available server-side, the server sends a response through the request-response channel, and only closes the connection when explicitly told to do so. In such a manner, a client can listen for updates from the server and receive them instantly with none of the overhead associated with HTTP headers and the opening/closing of connections. It also eliminates the need for polling.

To achieve an indefinite response, the server must respond to client requests by specifying Transfer Encoding: chunked in the header. This sets up a persistent connection from server to client and allows the server to send response data in chunks of newline-delimited strings. These chunks of data can then be received and processed on-the-fly by the client.

Alternatively, the data may be streamed via the Server-Sent Events (SSE) method, for which there is a standardized HTML5 API called EventSource. With SSE, data is encoded as text/event-stream in the header.

# Refs

- [HTTP Streaming](https://www.pubnub.com/learn/glossary/what-is-http-streaming/)
