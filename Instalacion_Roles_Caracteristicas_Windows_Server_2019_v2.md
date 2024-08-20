
# Instalación de Roles y Características en Windows Server 2019

## Ejecutar la máquina virtual con privilegios de administrador

Es fundamental que la cuenta utilizada tenga permisos de administrador para realizar todas las configuraciones necesarias.

## Instalar roles y características desde el Administrador del Servidor

### Instalar Active Directory Domain Services
Este rol es necesario para crear y administrar un dominio al que se unirá SharePoint Server. Una vez instalado, será necesario configurar un nuevo dominio si aún no existe.

### Instalar Servidor IIS con .NET Framework 3.5
IIS (Internet Information Services) es esencial para la instalación de SharePoint Server, ya que es la plataforma web que soportará los sitios de SharePoint. Asegurarse de incluir el componente .NET Framework 3.5 al instalar IIS.

### Instalar Servidor DNS
El servidor DNS es fundamental para complementar el funcionamiento de Active Directory y IIS, permitiendo la resolución de nombres y la correcta integración de los servicios.

## Instalar SQL Server y SQL Server Management Studio (SSMS)

### Instalar SQL Server Developer Edition
SQL Server será el motor de base de datos que utilizará SharePoint. Configurar la instancia con las credenciales necesarias.

### Instalar SQL Server Management Studio (SSMS)
SSMS será la herramienta utilizada para administrar las bases de datos de SQL Server. Una vez instalado, abrir SSMS y realizar la conexión al servidor SQL con el usuario que está utilizando actualmente la máquina.

## Instalación de los Prerrequisitos de SharePoint

### Montar la ISO de SharePoint Server en la máquina virtual
Insertar la ISO en la unidad virtual o montar el archivo de imagen para que esté accesible en la máquina virtual.

### Ejecutar el PrerequisiteInstaller.exe desde el medio de instalación
Este instalador descargará e instalará automáticamente los prerrequisitos necesarios para que SharePoint Server funcione correctamente, incluyendo:

- .NET Framework.
- Windows Server AppFabric.
- Microsoft Identity Extensions.
- Microsoft Sync Framework.
- Microsoft SQL Server Native Client.
- Windows Management Framework.
- IIS (Internet Information Services) y sus componentes.

Durante este proceso, es posible que se deba reiniciar la máquina virtual varias veces para completar la instalación de estos componentes.

## Instalación de SharePoint Server

### Ejecutar el setup.exe desde el medio de instalación de SharePoint Server
Una vez que todos los prerrequisitos estén instalados, ejecutar el instalador principal de SharePoint Server.

- Introducir la clave del producto cuando se solicite para proceder con la instalación.

### Seleccionar el Tipo de Instalación
Optar por Instalación Completa si se está configurando un entorno de granja, lo que ofrece mayor flexibilidad. Si se está configurando un entorno de prueba en un solo servidor, se puede optar por Instalación en Modo Independiente.

### Configurar la Conexión a SQL Server
Especificar la instancia de SQL Server a la que se conectará SharePoint. Si SQL Server está instalado en la misma máquina, se puede usar `localhost` o `NOMBRE_DEL_SERVIDOR\INSTANCIA`.

Proporcionar las credenciales necesarias para conectar SharePoint a SQL Server, asegurándose de utilizar la cuenta adecuada.

### Especificar la Cuenta de Servicio
Proporcionar la cuenta de servicio que utilizará SharePoint. Se recomienda utilizar una cuenta de dominio con los permisos necesarios en SQL Server para garantizar la correcta configuración y operación del entorno.

### Completar la Instalación
Una vez que el instalador haya completado su trabajo, se solicitará ejecutar el Asistente de Configuración de Productos de SharePoint para finalizar la configuración.

## Configuración de SharePoint Server

### Ejecutar el Asistente de Configuración de Productos de SharePoint
El asistente se abrirá automáticamente al final de la instalación de SharePoint Server.

- Seleccionar la opción Crear una nueva granja de servidores y especificar la base de datos de configuración.

### Configurar la Granja de SharePoint
Especificar el nombre de la base de datos de configuración y proporcionar las credenciales de la cuenta de granja que tendrá permisos elevados en SharePoint y SQL Server.

Definir los parámetros de seguridad y el servidor en el que se alojará la base de datos de configuración.

### Configurar el Servicio Central de Administración
Elegir un puerto para la Administración Central de SharePoint y configurar la seguridad según sea necesario.

El asistente finalizará la configuración de la granja y lanzará la Administración Central de SharePoint, donde se podrán realizar configuraciones adicionales y gestionar el entorno de SharePoint.
