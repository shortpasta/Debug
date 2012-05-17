My noVnc WebSockets server is org.shortpasta.novnc.ws.NovncServer.
It uses TooTallNate's Java-WebSocket library to accept connections.
It uses my TcpEndpoint class to proxy data out to the real VNC server.

To test noVNC running against a server running WebSockets:
1. Edit org.shortpasta.novnc.ws.NovncServer.main () and configure NovncServer
   1. IP Address and Port of the machine running the VNC server
   2. Local port on which to start a WebSockets server for noVNC to connect to
   3. Time to run
2. Build by running this in the novnc/build directory
   ant -f github.xml
3. Run the NovncServer by running 
   ant -f github.xml NovncServer
4. Run noVNC within your browser and point it to localhost:10000
5. Now you should be able to see the noVNC logging within the browser console
   and the NovncServer logging to the command console from #3

To test VNC running against a server running WebSockets:
1. Edit org.shortpasta.novnc.net.TcpProxy.main () and configure TcpProxy
   1. IP Address and Port of the machine running the VNC server
   2. Local port on which to start a socket server for the VNC client to connect to
   3. Time to run
2. Build by running this in the novnc/build directory
   ant -f github.xml
3. Run the TcpProxy by running 
   ant -f github.xml TcpProxy
4. Run a VNC client like TightVNC and point it to localhost:10000
5. In my tests, VNC is able to proxy via TcpProxy into the target machine