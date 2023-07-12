---
title: "CloudStack: Mover una instancia a una VPC diferente"
slug: cloudstack-mover-instancia-a-vpc-diferente
---


Una vez creada, una instancia se vincula a la zona en la que se implementa. Sin embargo, las instancias se pueden mover entre VPC en la misma zona.

Después de pasar a una VPC diferente:
    - Se reiniciará la instancia para que los cambios surtan efecto.
    - La instancia tendrá una nueva IP privada.
    - Todas las reglas de reenvío de puertos a la instancia se eliminarán y deberán volver a crearse.
    - La instancia se eliminará de todas las reglas del balanceador de carga en la antigua VPC.
    - La instancia se desvinculará de cualquier dirección IP pública de la antigua VPC y se deberá asignar una dirección desde la nueva VPC.

### Mover la instancia

1. Navega hasta el entorno donde se encuentra la instancia.
1. En la página *Instancias*, busca la instancia deseada y haz clic en el menú *Acción* en el extremo derecho de la entrada.
1. Selecciona *Cambiar red*.
1. Aparecerá la página *Cambiar red*. Se mostrará el nombre de la instancia y su red actual.
1. El menú emergente *Red de destino* enumerará las redes disponibles, agrupadas por VPC, a las que se puede conectar la instancia. Selecciona la red deseada.
1. Marca la casilla *Entiendo que se reiniciará la instancia*.
1. La instancia se detendrá, se conectará a la nueva red y se iniciará.
1. Cuando la instancia se inicie y se encuentre en estado de **ejecución**, verifica la conectividad de la red.