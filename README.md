# Spinner
Hola
<script>
  (function () {
    const bar = document.getElementById("barFill");
    if (!bar) return;

    bar.style.width = "0%";

    let p = 0;

    // 🔧 Ajustes de velocidad (puedes cambiarlos)
    const intervalMs = 220;   // más alto = más lento
    const minStep = 0.4;
    const maxStep = 1.6;
    const cap = 88;

    const timer = setInterval(() => {
      if (p < cap) {
        p += (Math.random() * (maxStep - minStep)) + minStep;
        if (p > cap) p = cap;
        bar.style.width = Math.floor(p) + "%";
      }
    }, intervalMs);

    const finishTo100 = () => {
      clearInterval(timer);

      // ✅ FORZAR 100% SIEMPRE
      // (si tu CSS tiene transition: width .25s ease; se verá suave)
      bar.style.width = "100%";
    };

    // 1) Cuando carga el documento completo
    window.addEventListener("load", () => {
      finishTo100();
    });

    // 2) Respaldo extra: si por alguna razón load no se nota, igual se completa
    setTimeout(() => {
      // si ya pasó un rato y sigue < 100, completar
      if (parseInt(bar.style.width || "0", 10) < 100) {
        finishTo100();
      }
    }, 6000);
  })();
</script>

