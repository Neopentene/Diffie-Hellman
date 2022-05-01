<template>
  <div class="card simple">
    <h2>Input (📝)</h2>
    <h3>Enter the Value of P (<code>🙏</code>)</h3>
    <label class="input">
      <input
        id="P"
        class="input__field"
        type="number"
        placeholder=" "
        name="P"
        @input="toBigInt('P')"
      />
      <span class="input__label">Enter the Value of P</span>
    </label>
    <h3>Enter the Value of G (<code>🙏</code>)</h3>
    <label class="input">
      <input
        id="G"
        class="input__field"
        type="number"
        placeholder=" "
        name="G"
        @input="toBigInt('G')"
      />
      <span class="input__label">Enter the Value of G</span>
    </label>
    <h3>Enter private key for Alice (<code>a 🕶</code>)</h3>
    <label class="input">
      <input
        id="a"
        class="input__field"
        type="number"
        placeholder=" "
        name="a"
        @input="toBigInt('a')"
      />
      <span class="input__label">Enter private key for Alice</span>
    </label>
    <h3>Enter private key for Bob (<code>b 🕶</code>)</h3>
    <label class="input">
      <input
        id="b"
        class="input__field"
        type="number"
        placeholder=" "
        name="b"
        @input="toBigInt('b')"
      />
      <span class="input__label">Enter private key for Bob</span>
    </label>
  </div>
  <div class="card simple" style="margin-bottom: 2rem">
    <h2>Output (📤)</h2>
    <h3>
      Public value for Alice (<code>x = G<sup>a</sup> mod P</code>)
    </h3>
    <output name="public-value-alice" for="a b">
      <h4>📢: <code>{{ setX(power(G, a, P)) }}</code></h4>
    </output>
    <h3>
      Public value for Bob (<code>y = G<sup>b</sup> mod P</code>)
    </h3>
    <output name="public-value-bob" for="a b">
      <h4>📢: <code>{{ setY(power(G, b, P))  }}</code></h4>
    </output>
    <h3>Symmetric Key for Alice</h3>
    <h3>(<code>key-alice = y<sup>a</sup> mod P</code>)</h3>
    <output name="symmetric-key-alice">
      <h4>📢: <code>{{ setKeyAlice(power(y, a, P)) }}</code></h4>
    </output>
    <h3>Symmetric Key for Bob</h3>
    <h3>(<code>key-bob = x<sup>b</sup> mod P</code>)</h3>
    <output name="symmetric-key-bob">
      <h4>📢: <code>{{ setKeyBob(power(x, b, P)) }}</code></h4>
    </output>
  </div>
</template>

<script>
export default {
  name: 'AlgorithmVue',
  data: function () {
    return {
      P: BigInt(0),
      G: BigInt(0),
      a: BigInt(0),
      b: BigInt(0),
      x: BigInt(0),
      y: BigInt(0),
      key_alice: BigInt(0),
      key_bob: BigInt(0)
    }
  },
  props: {
    msg: String
  },
  methods: {
    power (a, b, p) {
      try {
        console.log(typeof a, typeof b, typeof p)
        if (b === 1) {
          return a
        } else if (b === 0 || b === '') {
          return Number.NaN
        } else {
          return (a ** b) % p
        }
      } catch (error) {
        return Number.NaN
      }
    },
    toBigInt (type) {
      switch (type.toLowerCase()) {
        case 'p':
          this.P = BigInt(document.getElementById('P').value)
          break
        case 'g':
          this.G = BigInt(document.getElementById('G').value)
          break
        case 'a':
          this.a = BigInt(document.getElementById('a').value)
          break
        case 'b':
          this.b = BigInt(document.getElementById('b').value)
          break
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
