---
title: "CloudStack: Crear una VPN de sitio a sitio en una VPC"
slug: cloudstack-crear-vpn-sitio-a-sitio-en-una-vpc
---


Una VPN de sitio a sitio es útil para interconectar una VPC a una oficina remota, otro centro de datos u otra VPC. Para más detalles, consulta [Gestion de VPC](../cloudstack-compute-service/working-with-vpcs.md).

El siguiente ejemplo ilustra cómo conectar dos VPCs con una VPN de sitio a sitio. Los detalles variarán para sus dispositivos particulares.

#### Ejemplo de detalles de VPC
| Nombre de la VPC | Nombre del entorno | VPC CIDR | Fuente NAT IP |
| --- | --- | --- | --- |
| dmz | entorno-dmz | 10.0.0.0/22 | 172.30.200.106 |
| gestion | entorno-gestion | 10.0.4.0/22 | 172.30.200.107 |

#### Configuración de VPN de sitio a sitio
1. Ve al entorno **entorno-dmz**.
1. Ve a la pestaña *Redes*.
1. Haz clic en el menú de engranajes para *VPN de sitio a sitio*.
1. Haz clic en *Agregar VPN de sitio a sitio*.
1. Ingrese los detalles del túnel de **dmz** a **gestion**:
    - **Nombre de esta conexión VPN:** tunel-a-gestion
    - **IP pública remota (si es otra VPC, su NAT de origen):** 172.30.200.107
    - **Lista de CIDR remotos (separados por comas):** 10.0.4.0/22
    - **Clave pre-compartida de IPSec:** Uj2nzrTQ7xkbgun3ZqVFPbyxr9wfQzXZG5ZJ
    - **Algoritmo de encriptación IKE:** AES128
    - **Algoritmo hash IKE:** SHA1
    - **Grupo IKE Diffie-Hellman:** modp1536 (Group-5)
    - **Duracíon de IKE (en segundos):** 86400
    - **Algoritmo de cifrado ESP:** AES128
    - **Algoritmo hash ESP:** SHA1
    - **Reenvio de secreto perfecto ESP:** modp1536 (Group-5)
    - **Duración ESP (en segundos):** 3600
    - **Detección de pares muertos:** Habilitada
    - **Encapsulación a fuerza para NAT transversal:** Deshabilitada
    - **Conexión pasiva (si el remoto aún no está configurado):** Habilitada
1. Haz clic en *Aplicar*
1. Vaya al entorno **entorno-gestion** y repita los pasos 2 a 4.
1. Ingrese los detalles del túnel de **gestion** a **dmz**:
   - **Nombre de esta conexión VPN:** tunel-a-dmz
   - **IP pública remota (si es otra VPC, su NAT de origen):** 172.30.200.106
   - **Lista de CIDR remotos (separados por comas):** 10.0.0.0/22
   - **Clave pre-compartida de IPSec:** Uj2nzrTQ7xkbgun3ZqVFPbyxr9wfQzXZG5ZJ
   - **Algoritmo de encriptación IKE:** AES128
   - **Algoritmo hash IKE:** SHA1
   - **Grupo IKE Diffie-Hellman:** modp1536 (Group-5)
   - **Duracíon de IKE (en segundos):** 86400
   - **Algoritmo de cifrado ESP:** AES128
   - **Algoritmo hash ESP:** SHA1
   - **Reenvio de secreto perfecto ESP:** modp1536 (Group-5)
   - **Duración ESP (en segundos):** 3600
   - **Detección de pares muertos:** Habilitada
   - **Encapsulación a fuerza para NAT transversal:** Deshabilitada
   - **Conexión pasiva (si el remoto aún no está configurado):** Deshabilitada
1. Haz clic en *Aplicar*
1. La lista de VPN de sitio a sitio ahora muestra **tunel-a-dmz**. El estado dirá **Conectado**. En el otro lado de la VPN, la lista de VPN de sitio a sitio en **entorno-dmz** tendrá una entrada, **tunel-a-gestion**, y dirá **Conectado**.
