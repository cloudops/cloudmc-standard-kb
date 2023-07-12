---
title: "CloudStack: Actualización del kernel en instancias basadas en Ubuntu y Debian"
slug: cloudstack-actualizar-kernel-para-ubuntu-debian
---


### Para actualizar el kernel a la versión 4.4 en una instancia de Ubuntu 14.04.x:

- En la máquina virtual requerida, inicia sesión a través de la consola o ssh.
- Confirma que el kernel en ejecución es 3.13.x. Ejecutar: `uname -a`
- Para instalar un kernel nuevo, ejecuta: `'`sudo apt-get update && sudo apt-get install linux-generic-lts-xenial`
    - NB. Mientras instalas el paquete, es posible que se te solicita conservar o instalar un nuevo archivo del mantenedor del paquete; selecciona *Instalar la versión del mantenedor del paquete*
- Reinicia la instancia. Ejecutar: `sudo shutdown -r now`
- Verifica que la instancia esté ejecutando la versión de kernel 4.x. Ejecutar: `uname -a`
- Eliminar la versión anterior del kernel.
    - Ejecutar: `sudo apt-get autoremove --purge -y`
    - Verificar paquetes restantes. Ejecute: `sudo dpkg -l |grep linux-image`
    - Si hay paquetes restantes que necesitan desinstalación, ejecute: `sudo apt-get remove packagename --purge`

### Para actualizar el kernel a la versión 3.16 en una instancia de Debian 8.x:

- En la máquina virtual requerida, inicia sesión a través de la consola o ssh.
- Confirma que el kernel en ejecución es 3.13.x. Ejecute: `uname -a`. Si ya está ejecutando la versión 3.16, no se requiere nada más.
- Para instalar un kernel nuevo, ejecuta: `sudo apt-get update && sudo apt-get linux-image-amd64 -y`
    - NB. Mientras instalas el paquete, es posible que se te solicita conservar o instalar un nuevo archivo del mantenedor del paquete; selecciona *Instalar la versión del mantenedor del paquete*
- Reinicia la instancia. Ejecutar: `sudo shutdown -r now`
- Verifica que la instancia esté ejecutando la versión 3.16 del kernel. Ejecutar: `uname -a`
- Eliminar la versión anterior del kernel.
    - Ejecutar: `sudo apt-get autoremove --purge -y`
    - Verificar paquetes restantes. Ejecute: `sudo dpkg -l |grep linux-image`
    - Si hay paquetes restantes que necesitan desinstalación, ejecute: `sudo apt-get remove packagename --purge`
