# Gestión de Licencias Citrix
## Liberar licencias asignadas a usarios o dispositivos

1. Conectarse al servidor de licencias Citrix.

2. Abrir CMD con privilegios y situarse al siguiente path.  
```cmd
cd "C:\Program Files (x86)\Citrix\Licensing\LS"
```

3. Listar asignación de licencias usuarios/dispositivos
```cmd
udadmin -list -a
```
- -list: lista usuarios/dispositivos desde la última actualización.
- -a: enumera todas las características y versiones.

![script_bypass_ps_executionpolicy](screenshots/licensing_citrix_udadmin.png)

4. Liberar licencias asignadas a usuarios o dispositivos.
```cmd
udadmin -f XDT_ENT_UD -user <USUARIO> -delete
udadmin -f XDT_ENT_UD -device <DISPOSITIVO> -delete
```
- -f: feature
- -user: usuario
- -device: dispositivo
- -delete: liberar licencia usuario, función o dispositivo a la vez.

Después de volver a comprobar con udadmin -list -a hay que tener en cuenta que aunque se eliminara la asignación de la licencia del usuario/dispositivo, los cambios serán actualizados cada 15 minutos.

Otra forma de ver el número de licencias ocupadas y disponibles es a través de la propia consola de Citrix Studio. Desde aquí no podremos ver a que usuarios o dispositivos están asignadas ni liberarlas, simplemente vemos de forma gráfica el estado actual de asignación.

![script_bypass_ps_executionpolicy](screenshots/licensing_citrix_studio.png)