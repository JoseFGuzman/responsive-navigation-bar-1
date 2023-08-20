# Codigo inicial CSS.

## Primer paso: Definir variables.

Lo primero que debemos hacer es declarar variables sin olvidar de importar las fuentes que sean necesarias. Las variables las definimos dentro de :root{}.

1. _--header-height_: Altura del header definida en REM.
1. **Colores**: Color mode HSL(hue, saturation, lightness).  
   _Color principal_:Se define el matiz del color como una variable porque definiremos un color principal y uno alternativo. Utilizando el sistema HSL utilizaremos el mismo matiz pero disminuiremos la saturación y la luminucidad para obtener un color un poco mas claro.  
   _Color textos_: Se define dos colores para el texto un color para el titulo y otro para el texto en general.El color del segundo tiene el mismo matiz y la misma saturación que el primero pero menor en cuanto a luminisidad.  
   _Color de fondo_: Se definen dos colores para el fondo con valores de saturación y luminosidad similares en ambos colores ("--body-color" y "--container-color") sugiere una coherencia y armonía visual entre ellos. Esta similitud ayudará a crear una continuidad visual y a mantener una apariencia consistente en las secciones de la página.

   - _--hue_:162;
   - _--first-color_: hsl(var(--hue), 100%, 40%); Color principal.
   - _--first-color-alt_: hsl(var(--hue), 56%, 35%); Variante del color principal.
   - _--title-color_: hsl(228, 8%, 95%);
   - _--text-color_: hsl(228, 8%, 65%);
   - _--body-color_: hsl(228, 15%, 20%);
   - _--container-color_: hsl(228, 15%, 15%);

1. **Font and typography**: 0.5rem = 8px | 1rem = 16px. Definimos la fuente y los tamaños que usaremos. El tamaño esta definido en REMs.
   - _--body-font_: "Poppins", sans-serif;
   - _--biggest-font-size_: 2rem;
   - _--bigger-font-size_: 1.25rem;
   - _--h1-font-size_: 1.5rem;
   - _--h2-font-size_: 1.25rem;
   - _--h3-font-size_: 1rem;
   - _--normal-font-size_: 0.938rem;
   - _--small-font-size_: 0.813rem;
   - _--smaller-font-size_: 0.75rem;
1. **Font weight**: Definimos 3 pesos de fuente:
   - _--font-regular_: 400;
   - _--font-medium_: 500;
   - _--font-semi-bold_: 600;
1. **z index**: Definimos 2 valores para z-index, uno para elementos posicionados como fixed y otro para...
   - _--z-tooltip_: 10;
   - _--z-fixed_: 100;
1. **Responsive typography**: Definimos en una media queri valores más grandes para las fuentes destinadas a desktop.
   - ````css
        @media screen and (min-width: 1152px) {
       :root {
         --biggest-font-size: 4rem;
         --bigger-font-size: 2rem;
         --h1-font-size: 2.25rem;
         --h2-font-size: 1.5rem;
         --h3-font-size: 1.25rem;
         --normal-font-size: 1rem;
         --small-font-size: 0.875rem;
         --smaller-font-size: 0.813rem;
         }
      }
     ```
     ````

## Segundo paso: Codigo CSS BASE.

1. Hacemos un reset para todos los elementos (\*): las propiedades padding y margen a cero y colocamos box-sizing en border-box.

```css
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
```

2. Establemos en _none_ el estilo de las listas y la decoración de los elementos anclas. Tambien nos aseguramos de que los elementos de formularios (input, textare y button) no tengan borde ni contorno.

```css
ul {
  list-style: none;
}

a {
  text-decoration: none;
}
input,
textarea,
button {
  outline: none;
  border: none;
}
```

3. Asignamos la fuente y el tamaño de fuente al body y a los elementos de formulario (input, textarea y button). Estas propiedades se heredarán por defecto a los elementos de bloque y de texto en línea a menos que se anulen explícitamente en reglas CSS específicas para esos elementos.

Es importante tener en cuenta que cada elemento puede tener su propia especificación de fuente y tamaño de fuente a través de reglas CSS. Al establecer estilos personalizados para un elemento en particular, esos estilos anularán la herencia de body para esa propiedad específica.

Recuerda que esta herencia no se aplica automáticamente a todos los elementos en HTML. Algunos elementos, como los elementos de formulario (_input_, _textarea_, _button_) y elementos semánticos (_nav_, _section_, _article_, etc.), no heredan propiedades de fuente y tamaño de fuente de body por defecto.

```css
input,
textarea,
button,
body {
  font-family: var(--body-font);
  font-size: var(--normal-font-size);
}
```

4. La propiedad scroll-behavior se utiliza en CSS para especificar el comportamiento de desplazamiento suave de un contenedor o un elemento que tiene barras de desplazamiento.

Cuando se establece scroll-behavior: smooth;, el desplazamiento dentro del contenedor o elemento se realiza de forma suave y animada, en lugar de un desplazamiento brusco y abrupto.

Esto para que el desplazamiento entre secciones sea suave.

```css
html {
  scroll-behavior: smooth;
}
```

5. Establecemos el color de fondo del body y el color del texto.

```css
body {
  background-color: var(--body-color);
  color: var(--text-color);
}
```

6. Establecemos los estilos de fuente para los encabezados. Recordemos que heredan la fuente del body, definimos el color de los encabezado y el font-weight.

```css
h1,
h2,
h3,
h4 {
  color: var(--title-color);
  font-weight: var(--font-medium);
}
```

7.

```css
img,
svg {
  max-width: 100%;
  height: auto;
}
```

Estas reglas se utilizan comúnmente para asegurar que las imágenes y los gráficos vectoriales escalen correctamente dentro de su contenedor.

Aquí está el significado de cada regla:

- _max-width_: 100%;: Esta regla establece el ancho máximo de los elementos _img_ y _svg_ en el 100% del ancho de su contenedor. Esto significa que las imágenes y los gráficos vectoriales se ajustarán automáticamente al ancho disponible del contenedor sin excederlo. Esto ayuda a evitar que las imágenes se desborden o distorsionen si su tamaño original es mayor que el contenedor.

- _height_: auto;: Esta regla establece la altura de los elementos _img_ y _svg_ en "auto". Esto permite que la altura se ajuste de forma proporcional al ancho, manteniendo la relación de aspecto original de la imagen o el gráfico vectorial. De esta manera, los elementos se escalarán correctamente sin deformarse visualmente.

En resumen, estas reglas CSS aseguran que las imágenes y los gráficos vectoriales se muestren de manera responsiva y se adapten al tamaño de su contenedor sin perder su proporción o calidad. Esto es útil para lograr un diseño adaptable y receptivo en diferentes tamaños de pantalla y dispositivos.

```CSS



```
