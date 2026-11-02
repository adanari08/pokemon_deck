
# Pokémon Deck

Proyecto desarrollado con Vue.js que permite generar un deck de 40 cartas Pokémon aleatorias utilizando la PokeAPI.

## Descripción

La aplicación muestra 40 cartas Pokémon con información obtenida directamente de la PokeAPI. Cada carta incluye una imagen, características, habilidades especiales y cuatro ataques.

También cuenta con un botón para generar un nuevo deck de Pokémon aleatorios y un diseño personalizado en tonos rosas.

## Funcionalidades

- Generación de 40 Pokémon aleatorios sin repetir.
- Consulta de información mediante la PokeAPI.
- Visualización del nombre y número de cada Pokémon.
- Imagen oficial del Pokémon.
- Puntos de salud (HP).
- Tipo, altura y peso.
- Mínimo dos habilidades especiales.
- Cuatro ataques por carta.
- Botón para generar otro deck.
- Diseño de cartas con componentes de Vue.

## Tecnologías utilizadas

- Vue.js 3
- Vite
- JavaScript
- HTML
- CSS
- PokeAPI

## Instalación

### 1. Clonar el repositorio

```bash
git clone https://github.com/adanari08/pokemon_deck.git
```

### 2. Entrar al proyecto

```bash
cd pokemon_deck
```

### 3. Instalar las dependencias

```bash
npm install
```

### 4. Ejecutar el proyecto

```bash
npm run dev
```

### 5. Abrir en el navegador

Abrir la dirección que muestre Vite en la terminal, normalmente:

http://localhost:5173/

## Estructura del proyecto

```text
pokemon_deck/
├── public/
├── src/
│   ├── assets/
│   ├── components/
│   │   └── PokemonCard.vue
│   ├── App.vue
│   ├── main.js
│   └── style.css
├── index.html
├── package.json
└── vite.config.js
```

## Funcionamiento

Al iniciar la aplicación, se generan números aleatorios para consultar diferentes Pokémon mediante la PokeAPI.

Se verifica que cada Pokémon tenga una imagen disponible, al menos dos habilidades y cuatro movimientos.

Los Pokémon seleccionados se muestran utilizando el componente `PokemonCard.vue`, encargado de presentar la información de cada carta.

El botón **Generar otro deck** permite consultar y mostrar 40 Pokémon diferentes de forma aleatoria.

## API utilizada

[PokeAPI](https://pokeapi.co/)

Endpoint utilizado:

```text
https://pokeapi.co/api/v2/pokemon/{id}
```

## Autor

**adanari08**

Proyecto académico desarrollado con Vue.js.
