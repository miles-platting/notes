# Notes for Stephen

# CGI and Web Assembly

A CGI (Common Gateway Interface) provides a simple way to pass a web request to a program and receive a reply for instance to inject or add something to a web page. 

The CGI test 1

The simplest test just creates a simple new page

## Source sample
```c++
using namespace std;
int main ()
{  cout << "Content-type:text/html\r\n\r\n";
   cout << "<html>";
   cout << "<head>\n";
   cout << "<title>Hello World - First CGI Program</title>\n";   
   cout << "</head>\n";
   cout << "<body>\n";
   cout << "<h2>Hello World! This is my first CGI program</h2>\n";
   cout << "</body>\n";
   cout << "</html>\n";
   return 0;
}

1 -> Compile the code:              g++ -o cgi-ex1 cgi-simple.cpp
2 -> I change the execution mode:   chmod 755 cgi-ex1

Then in a web page I add this link:
 
<a href = "cgi-ex1.cgi" target = "_blank">CGI test 1</a>

So basically I am creating a C++ file (or could be C), making it runnable and launching it via the web browser.
  
Clicking the link shows:
  
  Hello World! This is my first CGI program
  
  in a new tab or a new page


# Source sample Lua
#!lua
print("Content-Type: text/html\r\n\r\n")
print("<h2>Hello, world! (Lua) from lua-test3.cgi without io.stdout:write</h2>\r\n")
print("The Lua interpreter is in /Users/dev/bin")
print("This script is in /Users/dev/Sites ")
print("<p><button>The Click me button</button></p>")
print("<h2>Hello World!</h2>")
print("<p>CGI is puzzling. This is a paragraph</p>")
print("<button>Another Click me</button><br/><br/>")
print("---------------\r\n")
print("It's goodbye from him<br/>\r\n")
print("PATH = " .. os.getenv("PATH") .. "<br/>\r\n")
print("SERVER_NAME = "          .. os.getenv("SERVER_NAME") .. "<br/>\r\n")
print("SCRIPT_NAME = "          .. os.getenv("SCRIPT_NAME") .. "<br/>\r\n")
print("GATEWAY_INTERFACE = "    .. os.getenv("GATEWAY_INTERFACE") .. "<br/>\r\n")
print("SERVER_PROTOCOL = "      .. os.getenv("SERVER_PROTOCOL") .. "<br/>\r\n")
print('HTTP_USER_AGENT = '      .. os.getenv("HTTP_USER_AGENT") .. "<br/>\r\n")
print('HTTP_HOST = '            .. os.getenv("HTTP_HOST") .. "<br/>\r\n")
--print('AUTH_TYPE = '          .. os.getenv("AUTH_TYPE") .. "<br/>\r\n")
--if (os.getenv("CONTENT_TYPE")) != nil then 
--    print('CONTENT_TYPE = '         .. os.getenv("CONTENT_TYPE") .. "<br/>\r\n")


print("I need to pass arguments via the URL and get those args")
vars = { 
  'SERVER_SOFTWARE', 
  'SERVER_NAME', 
  'GATEWAY_INTERFACE',
    'SERVER_PROTOCOL', 
    'SERVER_PORT', 
    'REQUEST_METHOD',
    'PATH_INFO', 
    'PATH_TRANSLATED', 
    'SCRIPT_NAME',
    'SCRIPT_FILENAME',
    'QUERY_STRING', 
    'REMOTE_HOST', 
    'REMOTE_ADDR',
    'AUTH_TYPE', 
    'REMOTE_USER', 
    'REMOTE_IDENT',
    'CONTENT_TYPE', 
    'CONTENT_LENGTH', 
    'HTTP_USER_AGENT',
    'HTTP_HOST'
}

local count = 0;

for k, v in pairs(vars) do
        print(tostring(k), " : ", tostring(v), " ", count, "<br/>\r\n")
        print(string.format("-> %03d v %30s %03d",tostring(k),v,tostring(count)),"<br/>")
        count = count + 1
end

