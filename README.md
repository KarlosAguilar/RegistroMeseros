# RegistroMeseros
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registro de meseros</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>

    <h1>Registro de Meseros</h1>
    <h3>Datos de trabajador</h3>
    <p>Complete los datos del trabajador que se solicita</p>

    <form>
        <div class="formulario-section">
            <label for="nombre">Nombre:</label>
            <input type="text" id="nombre" name="nombre" placeholder="Ej. Raul" required>
            
            <label for="paterno">Apellido Paterno:</label>
            <input type="text" id="paterno" name="paterno" placeholder="Ej. Lopez" required>

            <label for="materno">Apellido Materno:</label>
            <input type="text" id="materno" name="materno" placeholder="Ej. Garcia" required>
        </div>

        <div class="formulario-section">
            <label for="curp">CURP:</label>
            <input type="text" id="curp" name="curp" placeholder="Ingrese el CURP del mesero" required oninput="obtenerFechaNacimiento(this.value)">
    
            <label for="fechaNacimiento">Fecha de Nacimiento:</label>
            <input type="date" id="fechaNacimiento" name="fechaNacimiento" required>
        </div>

        <div class="formulario-section">
            <label for="telefono">Número Telefónico:</label>
            <input type="tel" id="telefono" name="telefono" placeholder="Ingrese el número telefónico" required>
    
            <label for="confirmarTelefono">Confirmación de Número Telefónico:</label>
            <input type="tel" id="confirmarTelefono" name="confirmarTelefono" placeholder="Repita el número telefónico" required>
        </div>

        <div class="formulario-section">
            <label for="correoElectronico">Correo Electrónico:</label>
            <input type="email" id="correoElectronico" name="correoElectronico" placeholder="ejemplo@ejemplo.com" required>
    
            <label for="confirmarCorreo">Confirmación de Correo Electrónico:</label>
            <input type="email" id="confirmarCorreo" name="confirmarCorreo" placeholder="ejemplo@ejemplo.com" required>
        </div>

        <div class="formulario-section">
            <label for="edad">Edad:</label>
            <input type="text" id="edad" name="edad" placeholder="Edad" readonly>
        </div>
    
        <button type="button" onclick="limpiarFormulario()">Limpiar</button>
        <button type="submit">Guardar</button>

        <footer>
            <p>© 2023 Registro de Meseros.</p>
        </footer>
    </form>

    <script>
        function obtenerFechaNacimiento(curp) {
            if (curp.length === 18) {
                const anioInicio = curp.substring(4, 6);
                let anio = parseInt(anioInicio, 10);
                const mes = curp.substring(6, 8);
                const dia = curp.substring(8, 10);

                if (anio >= 0 && anio <= 21) {
                    anio += 2000;
                } else {
                    anio += 1900;
                }

                const fechaNacimiento = `${anio}-${mes}-${dia}`;
                document.getElementById('fechaNacimiento').value = fechaNacimiento;
                calcularEdad(new Date(fechaNacimiento));
            }
        }

        function calcularEdad(fechaNacimiento) {
            const hoy = new Date();
            let edad = hoy.getFullYear() - fechaNacimiento.getFullYear();
            const mes = hoy.getMonth() - fechaNacimiento.getMonth();

            if (mes < 0 || (mes === 0 && hoy.getDate() < fechaNacimiento.getDate())) {
                edad--;
            }

            document.getElementById('edad').value = edad;
        }

        function limpiarFormulario() {
            document.getElementById("nombre").value = "";
            document.getElementById("paterno").value = "";
            document.getElementById("materno").value = "";
            document.getElementById("curp").value = "";
            document.getElementById("fechaNacimiento").value = "";
            document.getElementById("telefono").value = "";
            document.getElementById("confirmarTelefono").value = "";
            document.getElementById("correoElectronico").value = "";
            document.getElementById("confirmarCorreo").value = "";
            document.getElementById("edad").value = "";
        }
    </script>

</body>
</html>
