import socket

def iniciar_servidor():
    # 1. Crear el socket TCP (AF_INET = IPv4, SOCK_STREAM = TCP)
    servidor_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

    # Permitir reutilizar la dirección para evitar errores de puerto ocupado
    servidor_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)

    # 2. Vincular el socket a una IP y puerto locales
    host = '127.0.0.1'
    puerto = 8080
    servidor_socket.bind((host, puerto))

    # 3. Poner el servidor en modo escucha (esperando conexiones entrantes)
    servidor_socket.listen(1)
    print(f"[*] Servidor escuchando en http://{host}:{puerto}")
    print("[*] Esperando a que ocurra el TCP 3-way handshake...")

    while True:
        # 4. Aceptar la conexión (Aquí se completa el Handshake TCP a bajo nivel)
        conexion_cliente, direccion_cliente = servidor_socket.accept()
        print(f"\n[+] ¡Conexión TCP establecida con éxito desde {direccion_cliente}!")

        # 5. Recibir los datos de la solicitud (Tráfico WWW simulado)
        peticion = conexion_cliente.recv(1024).decode('utf-8')
        print(f"--- Solicitud recibida del cliente ---\n{peticion}")

        # 6. Enviar una respuesta simulada de la World Wide Web (HTML)
        respuesta_html = (
            "HTTP/1.1 200 OK\r\n"
            "Content-Type: text/html; charset=utf-8\r\n\r\n"
            "<html><body><h1>¡Hola desde el servidor TCP simulado de la WWW!</h1></body></html>"
        )
        conexion_cliente.sendall(respuesta_html.encode('utf-8'))

        # 7. Cerrar la conexión
        conexion_cliente.close()
        print("[*] Conexión cerrada por el servidor.")

if _name_ == "_main_":
    iniciar_servidor()
