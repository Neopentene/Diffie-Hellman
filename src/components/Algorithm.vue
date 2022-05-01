<template>
  <div class="card simple">
    <h2>Input (📝)</h2>
    <h3>Enter the Value of P (<code>🙏</code>)</h3>
    <label class="input">
      <input
        class="input__field"
        type="number"
        placeholder=" "
        name="P"
        v-model="P"
      />
      <span class="input__label">Enter the Value of P</span>
    </label>
    <h3>Enter the Value of G (<code>🙏</code>)</h3>
    <label class="input">
      <input
        class="input__field"
        type="number"
        placeholder=" "
        name="G"
        v-model="G"
      />
      <span class="input__label">Enter the Value of G</span>
    </label>
    <h3>Enter private key for Alice (<code>a 🕶</code>)</h3>
    <label class="input">
      <input
        class="input__field"
        type="number"
        placeholder=" "
        name="a"
        v-model="a"
      />
      <span class="input__label">Enter private key for Alice</span>
    </label>
    <h3>Enter private key for Bob (<code>b 🕶</code>)</h3>
    <label class="input">
      <input
        class="input__field"
        type="number"
        placeholder=" "
        name="b"
        v-model="b"
      />
      <span class="input__label">Enter private key for Bob</span>
    </label>
  </div>
  <div class="card simple">
    <h2>Output (📤)</h2>
    <h3>
      Public value for Alice (<code>x = G<sup>a</sup> mod P</code>)
    </h3>
    <output name="public-key-alice" for="a b">
      <h4>📢: <code>{{ setX(power(G, a, P)) }}</code></h4>
    </output>
    <h3>
      Public value for Bob (<code>y = G<sup>b</sup> mod P</code>)
    </h3>
    <output name="public-key-alice" for="a b">
      <h4>📢: <code>{{ setY(power(G, b, P))  }}</code></h4>
    </output>
    <h3>
      Symmetric Key for Alice (<code>key-alice = y<sup>a</sup> mod P</code>)
    </h3>
    <output name="public-key-alice" for="a b">
      <h4>📢: <code>{{ setKeyAlice(power(y, a, P)) }}</code></h4>
    </output>
    <h3>
      Symmetric Key for Bob (<code>key-bob = x<sup>b</sup> mod P</code>)
    </h3>
    <output name="public-key-alice" for="a b">
      <h4>📢: <code>{{ setKeyBob(power(x, b, P)) }}</code></h4>
    </output>
  </div>
</template>

<script>
export default {
  name: 'AlgorithmVue',
  data: function () {
    return {
      P: Number,
      G: Number,
      a: Number,
      b: Number,
      x: Number,
      y: Number,
      key_alice: Number,
      key_bob: Number
    }
  },
  props: {
    msg: String
  },
  methods: {
    power (a, b, p) {
      if (b === 1) {
        return a
      } else if (b === 0 || b === '') {
        return Number.NaN
      } else {
        return ((Math.pow(a, b)) % p)
      }
    },
    setX (val) {
      this.x = val
      return this.x
    },
    setY (val) {
      this.y = val
      return this.y
    },
    setKeyAlice (val) {
      this.key_alice = val
      return this.key_alice
    },
    setKeyBob (val) {
      this.key_bob = val
      return this.key_bob
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
