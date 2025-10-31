UsuarioRed
Aplicación Java Swing para crear usuarios en Active Directory de Windows Server mediante LDAP.
📋 Descripción
UsuarioRed es una herramienta de escritorio que permite a los administradores crear nuevos usuarios en Active Directory de forma sencilla a través de una interfaz gráfica. La aplicación se conecta al servidor de dominio mediante protocolo LDAP y gestiona la creación de cuentas de usuario con sus respectivas contraseñas.
✨ Características

Interfaz gráfica intuitiva desarrollada con Java Swing
Creación de usuarios en Active Directory vía LDAP
Validación de campos obligatorios
Verificación de coincidencia de contraseñas
Configuración de atributos básicos del usuario:

Nombre de usuario (sAMAccountName)
Contraseña con cifrado UTF-16LE
Descripción personalizada
userPrincipalName
displayName y givenName


Habilitación automática de la cuenta creada

🔧 Requisitos

Java JDK 24 o superior
Maven 3.x
Apache NetBeans (opcional, para editar la interfaz gráfica)
Acceso a un servidor Active Directory
Credenciales de administrador del dominio
Conectividad de red al controlador de dominio (puerto 389 LDAP)

🚀 Instalación

Clona el repositorio:

bashgit clone https://github.com/tuusuario/UsuarioRed.git
cd UsuarioRed

Configura las credenciales de tu dominio en Inicio.java:

javaenv.put(javax.naming.Context.PROVIDER_URL, "ldap://DC1.midominio.local:389");
env.put(javax.naming.Context.SECURITY_PRINCIPAL, "Administrador@midominio.local");
env.put(javax.naming.Context.SECURITY_CREDENTIALS, "TuPasswordDeAdministrador");

Ajusta la ruta del contenedor de usuarios:

javaString userDN = "CN=" + username + ",OU=Usuarios,DC=midominio,DC=local";

Compila el proyecto:

bashmvn clean compile

Ejecuta la aplicación:

bashmvn exec:java
📖 Uso

Inicia la aplicación
Completa los campos del formulario:

Nombre de Usuario: Identificador único del usuario
Contraseña: Contraseña inicial del usuario
Verificar Contraseña: Confirmación de la contraseña
Descripción: Información adicional sobre el usuario (opcional)


Haz clic en Crear Usuario
La aplicación mostrará un mensaje confirmando la creación exitosa

Botones

Crear Usuario: Valida los datos y crea el usuario en Active Directory
Cancelar: Limpia todos los campos del formulario

⚙️ Configuración
Estructura del Proyecto
UsuarioRed/
├── src/main/java/com/mycompany/usuariored/
│   ├── UsuarioRed.java          # Clase principal
│   ├── Inicio.java               # Ventana principal y lógica LDAP
│   └── Inicio.form               # Diseño de la interfaz (NetBeans)
├── pom.xml                       # Configuración Maven
└── README.md
Parámetros LDAP
Modifica estos valores según tu entorno:

PROVIDER_URL: ldap://[servidor-dc]:[puerto] (predeterminado: 389)
SECURITY_PRINCIPAL: Usuario con permisos para crear objetos en AD
SECURITY_CREDENTIALS: Contraseña del usuario administrador
userDN: Ruta completa donde se crearán los usuarios (Distinguished Name)

🔒 Seguridad
⚠️ Advertencias importantes:

Las credenciales del administrador están hardcodeadas en el código. Para producción, considera:

Usar variables de entorno
Implementar un sistema de gestión de secretos
Solicitar credenciales en tiempo de ejecución


La contraseña se establece usando UTF-16LE según los requisitos de Active Directory
El código establece userAccountControl = 512 para habilitar la cuenta

🛠️ Tecnologías

Java 24
Maven - Gestión de dependencias
Swing - Interfaz gráfica
JNDI - Java Naming and Directory Interface para LDAP
Apache NetBeans - IDE para desarrollo visual

📝 Notas

La aplicación crea usuarios con las clases de objeto: top, person, organizationalPerson y user
Los usuarios se crean en la OU especificada en el código
Es necesario tener permisos de administrador del dominio para ejecutar correctamente la aplicación
Asegúrate de que el firewall permita conexiones al puerto 389 (LDAP)

🐛 Solución de Problemas
Error de conexión LDAP:

Verifica que el servidor DC esté accesible
Confirma que las credenciales sean correctas
Revisa que el puerto 389 esté abierto

Error al crear usuario:

Verifica que la OU de destino exista
Confirma que el usuario no exista previamente
Revisa los permisos del usuario administrador

Error de contraseña:

Asegúrate de que la contraseña cumpla con las políticas del dominio
La longitud mínima y complejidad dependen de las políticas de AD

📄 Licencia
Este proyecto se encuentra bajo una licencia de código abierto. Consulta el archivo LICENSE para más detalles.
👥 Contribuciones
Las contribuciones son bienvenidas. Por favor:

Haz un Fork del proyecto
Crea una rama para tu característica (git checkout -b feature/NuevaCaracteristica)
Commit tus cambios (git commit -m 'Añadir nueva característica')
Push a la rama (git push origin feature/NuevaCaracteristica)
Abre un Pull Request

✉️ Contacto
Para preguntas o sugerencias, abre un issue en el repositorio.
