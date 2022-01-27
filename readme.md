-  A cookie can be set by a server including the `set-cookie` header in a response
- Cookie uses key value pair 
`set-cookie: userid=1234` = set userid value of 1234

- Setting a cookie with Express
```
server.get("/example", (request, response) => {
  response.cookie("hello", "this is my cookie", {
    httpOnly: true,
    maxAge: 1000 * 60, // 60,000ms (60s)
    sameSite: "lax",
  });
  response.redirect("/");
});
```

- Reading a cookie with cookie-parser
```
npm install cookie-parser
const cookieParser = require("cookie-parser");

server.use(cookieParser());

server.get("/", (request, response) => {
  console.log(request.cookies);
  // ...
});
```

- Removing cookies
```
server.get("/remove", (request, response) => {
  response.clearCookie("hello");
  response.redirect("/");
});

```
