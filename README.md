# CGI.lua

A CGI module for the Lua scripting language. 
This supports features such as GET/POST, Cookies, Upload/Download, HTML Tag Generation and more!
You may view some of the examples below, or, check out the **cgi.lua** file yourself!

Since this is posted on GitHub, it means that this is FOSS. 
You may do whatever you'd like to this module, However, I'd prefer you'd give some sort of attribution to me. It's the least you can do.

I aim for this to be a fast and succinct module for everybody to use. 
If there are any performance issues or improvements to the code you'd like to bring up, please create a **Issue** or **Pull Request**.

You can also use this in conjunction with WebSockets, or a Lua templating engine like <https://github.com/tarantool/template>

However, the performance of the CGI module alongside these technologies have _not_ been tested. If they do cause an issue, create an **Issue**. I cannot determine if your issue would be 100% fixable, especially if the module is closed source or has been abandoned.

### If there are any features you'd like to add:
Do not create an issue! Instead, Fork the repo, add your changes, and create a Pull Request!
This will make it easier for me to determine whether or not your issue is an actual issue.

With all of that read, have fun with this module! Luarocks support will be added within the near future. For now, you could drag the cgi.lua file right next to your script, or drag it to your Lua modules folder.

```lua
local cgi = require("cgi")

-- Example 1: Parsing CGI Parameters
local params = cgi.params()
-- Use the parsed parameters

-- Example 2: Getting HTTP Headers
cgi.header(200, {["Content-Type"] = "text/html"})

-- Example 3: Handling Cookies
local cookies = cgi.cookies()
-- Access the cookie values

-- Example 4: Generating an HTTP Cookie
local cookie = cgi.cookie("name", "value", 3600, true)
-- Use the generated cookie

-- Example 5: Handling File Uploads
local success, message = cgi.upload("path/to/file.ext")
if success then
    -- File uploaded successfully
else
    -- Handle upload failure
end

-- Example 6: Encoding HTML Special Characters
local encodedStr = cgi.enchtml("<html>")
-- Use the encoded string

-- Example 7: Custom HTML Tag Generation
local tag = cgi.tag("div", {class = "container"}, "Hello, World!")
-- Use the generated HTML tag

-- Example 8: Retrieving HTTP Method
local method = os.getenv("REQUEST_METHOD")
-- Use the HTTP method

-- Example 9: Handling Errors with Stack Trace
local errorPage = cgi.trace("An error occurred.")
-- Display the error page

-- Example 10: Redirecting to Another URL
local redirectURL = "/new-page.html"
cgi.header(301, {["Location"] = redirectURL})
