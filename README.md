## Validación del Formulario

 Se agrega un evento de escucha al elemento con el ID "formulario" para capturar el evento de envío.

    document.getElementById('formulario').addEventListener('submit', (event) => {
      event.preventDefault();
      // Código de validación del formulario
    });

Dentro del evento de envío, realizamos la validación de los campos del formulario uno por uno.

### Validación del campo de nombre

    let entradaNombre = document.getElementById('name');
    let errorNombre = document.getElementById('nameError');
    
    if (entradaNombre.value.trim() === '') {
      errorNombre.textContent = 'Por favor, introducí tu nombre';
      errorNombre.classList.add('error-message');
    } else {
      errorNombre.textContent = '';
      errorNombre.classList.remove('error-message');
    }

Se verifica si el valor del campo de nombre está en blanco. Si es así, mostramos un mensaje de error y aplicamos una clase CSS para resaltar el error. De lo contrario, eliminamos cualquier mensaje de error y la clase CSS correspondiente.

### Validación correo electrónico

    let emailEntrada = document.getElementById('email');
    let emailError = document.getElementById('emailError');
    let emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/; // Patrón de validación básico
    
    if (!emailPattern.test(emailEntrada.value)) {
      emailError.textContent = 'Por favor, introducí un mail válido';
      emailError.classList.add('error-message');
    } else {
      emailError.textContent = '';
      emailError.classList.remove('error-message');
    }

Utilización una expresión regular (`emailPattern`) para validar el formato básico de una dirección de correo electrónico. Si el valor del campo de correo electrónico no cumple con el patrón, mostramos un mensaje de error y aplicamos la clase CSS correspondiente.

### Validación de la contraseña

    let contrasenaEntrada = document.getElementById('password');
    let contrasenaError = document.getElementById('passwordError');
    let contrasenaPattern = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[$@$!%*?&#.$($)$-$_])[A-Za-z\d$@$!%*?&#.$($)$-$_]{8,15}$/;
    
    if (!contrasenaPattern.test(contrasenaEntrada.value)) {
      contrasenaError.textContent = 'La contraseña debe tener al menos 8 caracteres, números, mayúsculas y minúsculas y caracteres especiales';
      contrasenaError.classList.add('error-message');
    } else {
      contrasenaError.textContent = '';
      contrasenaError.classList.remove('error-message');
    }

Utilización de otra expresión regular (`contrasenaPattern`) para validar la contraseña. La contraseña debe tener entre 8 y 15 caracteres, al menos una letra minúscula, una letra mayúscula, un número y un carácter especial. Si la contraseña no cumple con el patrón, mostramos un mensaje de error y aplicamos la clase CSS correspondiente.

Si no hay mensajes de error en ninguno de los campos, procedemos a enviar el formulario, devuelve una alerta de envío y resetea el formulario. 
