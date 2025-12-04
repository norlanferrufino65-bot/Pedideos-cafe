# Pedideos-cafe
publicidad
```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Pedidos de Café</title>
  <style>
    body { font-family: Arial; margin: 2em; background: #f9f9f9;}
    input, button { margin: 0.5em 0; padding: 0.5em;}
    #resumen { margin-top: 1em;}
  </style>
</head>
<body>
  <h1>Registro de Pedidos de Café</h1>
  <label>¿Cuántos pedidos deseas registrar?</label>
  <input type="number" id="cantidad" min="1" />
  <button onclick="generarFormulario()">Continuar</button>

  <form id="formularioPedidos"></form>
  <div id="resumen"></div>

  <script>
    const PRECIO_LIBRA = 100;
    let pedidos = [];

    function generarFormulario() {
      pedidos = [];
      const cantidad = parseInt(document.getElementById("cantidad").value);
      const form = document.getElementById("formularioPedidos");
      form.innerHTML = "";

      for (let i = 0; i < cantidad; i++) {
        form.innerHTML += `
          <h3>Cliente #${i + 1}</h3>
          <input type="text" placeholder="Nombre del cliente" id="cliente${i}" required /><br/>
          <input type="number" placeholder="Cantidad de libras" id="libras${i}" min="1" required /><br/>
        `;
}

      form.innerHTML += `<button type="button" onclick="mostrarResumen(${cantidad})">Registrar Pedidos</button>`;
}

    function mostrarResumen(cantidad) {
      const resumen = document.getElementById("resumen");
      resumen.innerHTML = `<h2>Resumen de pedidos (${obtenerFechaActual()})</h2><ul>`;

      for (let i = 0; i < cantidad; i++) {
        const cliente = document.getElementById(`cliente${i}`).value;
        const libras = parseInt(document.getElementById(`libras${i}`).value);
        const total = libras * PRECIO_LIBRA;
        pedidos.push({ cliente, libras});
        resumen.innerHTML += `<li>${cliente}: ${libras} lb @ L.${PRECIO_LIBRA} = L.${total}</li>`;
}

      resumen.innerHTML += "</ul>";
}

    function obtenerFechaActual() {
      const hoy = new Date();
      return hoy.toLocaleDateString("es-ES");
}
  </script>
</body>
</html>
```
