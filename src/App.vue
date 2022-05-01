<template>
  <header
    class="card logo"
    style="display: flex; justify-content: center; align-items: center"
  >
    <h1 style="margin: 0">Diffie Hellman Algorithm</h1>
  </header>
  <Algorithm></Algorithm>
</template>

<script>
import Algorithm from './components/Algorithm.vue'

export default {
  name: 'App',
  components: {
    Algorithm
  }
}
</script>

<style>
* {
  outline-color: #606c38;
}

:root {
  --color-light: #fefae0;
  --color-dark: #283618;
  --color-signal: #bc6c25;
  --color-background: var(--color-light);
  --color-text: var(--color-dark);
  --color-accent: var(--color-signal);
  --size-bezel: 0.5rem;
  --size-radius: 4px;
  line-height: 1.4;
  font-family: "Inter", sans-serif;
  font-size: calc(0.6rem + 0.4vw);
  color: var(--color-text);
  background: var(--color-background);
  font-weight: 300;
  padding: 0 calc(var(--size-bezel) * 3);
}

h1,
h2,
h3,
h4 {
  font-weight: 900;
}

mark {
  background: var(--color-accent);
  color: var(--color-text);
  font-weight: bold;
  padding: 0 0.2em;
}

.card {
  width: 100%;
  background: var(--color-background);
  padding: calc(4 * var(--size-bezel));
  margin-top: calc(4 * var(--size-bezel));
  border-radius: var(--size-radius);
  border: 3px solid var(--color-shadow, currentColor);
  box-shadow: 0.5rem 0.5rem 0 var(--color-shadow, currentColor);
  box-sizing: border-box;
}

.card *:first-child {
  margin-top: 0;
}

.l-design-widht {
  max-width: 40rem;
  padding: 1rem;
}

.card.simple {
  max-width: 70rem;
}

.input {
  position: relative;
}

.input__label {
  position: absolute;
  left: 0;
  top: 0;
  padding: calc(var(--size-bezel) * 0.75) calc(var(--size-bezel) * 0.5);
  margin: calc(var(--size-bezel) * 0.75 + 3px) calc(var(--size-bezel) * 0.5);
  background: pink;
  white-space: nowrap;
  transform: translate(0, 0);
  transform-origin: 0 0;
  background: var(--color-background);
  transition: transform 120ms ease-in;
  font-weight: bold;
  line-height: 1.2;
}

.input__field {
  box-sizing: border-box;
  display: block;
  width: 100%;
  border: 3px solid currentColor;
  padding: calc(var(--size-bezel) * 1.5) var(--size-bezel);
  color: currentColor;
  background: transparent;
  border-radius: var(--size-radius);
}

.input__field:not(:-moz-placeholder-shown) + .input__label {
  transform: translate(0.25rem, -65%) scale(0.8);
  color: var(--color-accent);
}

.input__field:not(:-ms-input-placeholder) + .input__label {
  transform: translate(0.25rem, -65%) scale(0.8);
  color: var(--color-accent);
}

.input__field:focus + .input__label,
.input__field:not(:placeholder-shown) + .input__label {
  transform: translate(0.25rem, -65%) scale(0.8);
  color: var(--color-accent);
}

#app {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

</style>
