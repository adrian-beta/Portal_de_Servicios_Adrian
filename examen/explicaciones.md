# Comprensión Técnica: Arquitectura Web en Flask

## Actividad 1. Explicación integrada

Todo empieza cuando el empleado abre el navegador de su computadora, que aquí funciona como el **cliente**, y escribe la dirección `http://127.0.0.1:5000/compra`. En esa dirección, `127.0.0.1` es la **dirección IP** local de la propia máquina y `5000` es el **puerto** en el que está corriendo nuestra aplicación. Al darle Enter, el navegador manda una petición o **request** usando el protocolo **HTTP** para pedir que le muestren esa página.

Esa petición llega a nuestro **servidor** local, el cual programamos con **Flask** usando el lenguaje **Python** para manejar toda la parte del **backend**. Lo que hace **Flask** es buscar la **ruta** `/compra` en el archivo `app.py` y cargar el **template** correspondiente. Después, el **servidor** le contesta al navegador con una **response** **HTTP** que trae todo el código **HTML** de la página, junto con los diseños de **CSS** y **Bootstrap** para darle forma al **frontend** y que se vea bien acomodado. En este proyecto, **JavaScript** nada más se usa por medio de **Bootstrap** para cosas visuales como el menú cuando se hace chica la pantalla o el carrusel de fotos, pero no hace ninguna operación matemática.

Ya que aparece el formulario en la pantalla, el empleado pone la cantidad de productos, el precio y le da clic al botón de calcular. Como el formulario está configurado con el método **POST**, los datos que escribió se mandan dentro de un nuevo **request** **HTTP** hacia la misma **ruta** del **servidor**. Ahí en el **backend**, **Python** agarra esos datos con **Flask**, hace las cuentas para sacar el subtotal, revisa si pasa de mil pesos para aplicar el descuento y vuelve a cargar el mismo **template** pero ahora con los resultados. Al final, el **servidor** manda otra **response** **HTTP** con el **HTML** ya actualizado para que el **cliente** vea en su pantalla tanto los datos que metió como el total final.

---

## Actividad 2. Diagrama de comunicación

```mermaid
flowchart LR
    A[Cliente: Navegador] -->|1. HTTP Request GET / POST| B[Servidor: Flask 127.0.0.1:5000]
    B -->|2. Calcula en Python| B
    B -->|3. HTTP Response: HTML + CSS/Bootstrap| A