# data-exchangeimport socket

def start_server():
    # Create a TCP/IP socket
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

    # Bind the socket to the address and port
    server_socket.bind(('localhost', 12345))

    # Listen for incoming connections
    server_socket.listen(1)
    print("Server is listening...")

    # Wait for a connection
    conn, addr = server_socket.accept()
    print(f"Connected to {addr}")

    # Receive data from the client
    data = conn.recv(1024).decode('utf-8')
    print(f"Received from client: {data}")

    # Send data back to the client
    conn.send("Hello from server!".encode('utf-8'))

    # Close the connection
    conn.close()

if __name__ == "__main__":
    start_server()
