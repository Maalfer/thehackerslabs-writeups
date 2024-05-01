Hacemos el escaneo de nmap donde vemos el puerto 80 y 22 abiertos:

![image](https://github.com/Maalfer/thehackerslabs-writeups/assets/96432001/458a2103-af71-4417-9b19-46c6c37e0641)

Esto corre por el puerto 80:

![image](https://github.com/Maalfer/thehackerslabs-writeups/assets/96432001/acdc8c55-673d-44d4-8872-3af7855d8ba0)

Viendo el código fuente vemos el usuario melanie:

![image](https://github.com/Maalfer/thehackerslabs-writeups/assets/96432001/35749144-0ea5-449e-9d6f-ba92323545f7)

Por lo que hacemos fuerza bruta al puerto 22 con hydra:

![image](https://github.com/Maalfer/thehackerslabs-writeups/assets/96432001/5973cd5d-b0f7-4ad5-8c42-aae5c82d7516)

Accedemos por SSH con las credenciales obtenidas y estamos dentro:

![image](https://github.com/Maalfer/thehackerslabs-writeups/assets/96432001/fff6cf5b-2d47-49bb-8829-249357c7c000)

Una vez dentro, ejecutando el comando sudo -l, vemos un archivo que genera claves id_rsa:

![image](https://github.com/Maalfer/thehackerslabs-writeups/assets/96432001/3eaa0bb7-101a-45d9-a924-382ef0c0ec26)

Generamos una clave ssh:

![image](https://github.com/Maalfer/thehackerslabs-writeups/assets/96432001/be35e60d-dc93-4742-ab28-6cf90d565ca3)

Y esta clave pública generada con puttygen la podemos exportar:

sudo /usr/bin/puttygen id_rsa.pub -O public-openssh -o /root/.ssh/authorized_keys

![image](https://github.com/Maalfer/thehackerslabs-writeups/assets/96432001/aaf20d38-a716-4ecc-8481-54dbcd771587)

Y ahora desde esta propia máquina podemos acceder como root por ssh sin proporcionar contraseña:

![image](https://github.com/Maalfer/thehackerslabs-writeups/assets/96432001/47e6805f-4cf6-4d47-ad2d-42df8ee0b022)
