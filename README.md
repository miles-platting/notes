# notes
CGI and Web Assembly

A CGI (Common Gateway Interface) provides a simple way to pass a web request to a program and receive a reply for instance to inject or add something to a web page. 

The CGI test 1

The simplest test just creates a simple new page

#include <iostream>
using namespace std;

int main () {
   cout << "Content-type:text/html\r\n\r\n";
   cout << "<html>\n";
   cout << "<head>\n";
   cout << "<title>Hello World - First CGI Program</title>\n";
   cout << "</head>\n";
   cout << "<body>\n";
   cout << "<h2>Hello World! This is my first CGI program</h2>\n";
   cout << "</body>\n";
   cout << "</html>\n";
   
   return 0;
}

1 -> Compile the code: 
  g++ -o cgi-ex1 cgi-simple.cpp
2 -> I change the execution mode: 
  chmod 755 cgi-ex1
  
  Then in a web page I add this link:
  
  <a href = "cgi-ex1.cgi" target = "_blank">CGI test 1</a>
  
  So basically I am creating a C++ file (or could be C), making it runnable and launching it via the web browser.
  
  
  Clicking the link shows:
  
  Hello World! This is my first CGI program
  
  in a new tab or a new page
