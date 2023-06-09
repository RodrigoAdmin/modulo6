from http.server import HTTPServer, BaseHTTPRequestHandler

class Mf(BaseHTTPRequestHandler):
    def do_GET(self):
        self.send_response(200)
        self.send_header('Content-type', 'text/plain')
        self.end_headers()
        self.wfile.write(b'Servidor levantado mediante http.server')

def server():
    host = 'localhost'
    port = 8000
    server_address = (host, port)

    httpd = HTTPServer(server_address, Mf)
    print('Servidor levantado mediante http.server')
    httpd.serve_forever()

server()