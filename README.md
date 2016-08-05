# Watson Webserver
A simple C# async web server for handling incoming RESTful HTTP/HTTPS requests. 

## Test App
A test project is included which will help you exercise the class library.

## Example
```
using WatsonWebserver;

static void Main(string[] args)
{
   Server s = new Server("127.0.0.1", 9000, false, RequestReceived);
   Console.WriteLine("Press ENTER to exit");
   Console.ReadLine();
}

static HttpResponse RequestReceived(HttpRequest req)
{
   Console.WriteLine(req.ToString());
   HttpResponse resp = new HttpResponse(req, true, 200, null, "text/plain", "Watson says hello!", true);
   return resp;
}
```

## Running under Mono
Watson works well in Mono environments to the extent that we have tested it. It is recommended that when running under Mono, you execute the containing EXE using --server and after using the Mono Ahead-of-Time Compiler (AOT).

```
mono --aot=nrgctx-trampolines=8096,nimt-trampolines=8096,ntrampolines=4048 --server myapp.exe
mono --server myapp.exe
```