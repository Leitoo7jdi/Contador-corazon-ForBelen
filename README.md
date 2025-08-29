# Contador-corazon-ForBelen
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Días que no nos vimos</title>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
  body {
    margin: 0;
    background: #111;
    color: #eee;
    font-family: "Arial", sans-serif;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    text-align: center;
  }

  .corazon {
    position: relative;
    display: inline-block;
    width: 200px;
    height: 200px;
    background: url('corazon.png') no-repeat center/contain;
  }

  #contador {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 1.8rem;
    font-weight: bold;
    color: #ff4444;
    text-shadow: 0 0 12px rgba(255,0,0,0.8);
  }

  #contadorExacto {
    margin-top: 15px;
    font-size: 1rem;
    color: #ff6666;
    text-shadow: 0 0 8px rgba(255,0,0,0.6);
  }

  .fecha {
    margin-top: 25px;
    font-size: 1rem;
    color: #aaa;
  }
</style>
</head>
<body>
  <div class="corazon">
    <div id="contador">—</div>
  </div>
  <div id="contadorExacto">—</div>
  <p class="fecha">Nuestra ultima interacción fue el 21 de agosto de 2025</p>

  <script>
    const ultimaFecha = new Date(2025, 7, 21, 21, 0, 0); // 21 agosto 2025 21:00

    function actualizar() {
      const ahora = new Date();
      const diferencia = ahora - ultimaFecha; // diferencia en milisegundos

      // Días completos
      const dias = Math.floor(diferencia / (1000 * 60 * 60 * 24));
      document.getElementById("contador").textContent = 
        dias + (dias === 1 ? " día sin ti 💔" : " días sin ti 💔");

      // Horas, minutos y segundos restantes
      const horas = Math.floor((diferencia / (1000 * 60 * 60)) % 24);
      const minutos = Math.floor((diferencia / (1000 * 60)) % 60);
      const segundos = Math.floor((diferencia / 1000) % 60);

      document.getElementById("contadorExacto").textContent =
        horas + "h " + minutos + "m " + segundos + "s";
    }

    actualizar();
    setInterval(actualizar, 1000); // se actualiza cada segundo
  </script>
</body>
</html>
