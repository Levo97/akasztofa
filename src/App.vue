<template>
  <div id="app">
    <svg width="350px" height="260px" viewBox="0 0 350 275"
      preserveAspectRatio="xMidYMid meet">
      <line v-if="proba > 0" x1="80" y1="257" x2="260" y2="257" style="stroke:black;fill:none;stroke-width:2px;" />
      <line v-if="proba > 1" x1="100" y1="257" x2="100" y2="40" style="stroke:black;fill:none;stroke-width:2px;" />
      <line v-if="proba > 2" x1="100" y1="40" x2="230" y2="40" style="stroke:black;fill:none;stroke-width:2px;" />
      <line v-if="proba > 3" x1="100" y1="80" x2="130" y2="40" style="stroke:black;fill:none;stroke-width:2px;" />
      <line v-if="proba > 4" x1="230" y1="40" x2="230" y2="80" style="stroke:black;fill:none;stroke-width:2px;" />
      <circle v-if="proba > 5" cx="230" cy="90" style="fill:khaki;stroke:black;stroke-width:2px;" r="20" />
      <line v-if="proba > 6" x1="230" y1="110" x2="230" y2="170" style="stroke:black;fill:none;stroke-width:2px;" />
      <line v-if="proba > 7" x1="230" y1="140" x2="250" y2="120" style="stroke:black;fill:none;stroke-width:2px;" />
      <line v-if="proba > 8" x1="230" y1="140" x2="210" y2="120" style="stroke:black;fill:none;stroke-width:2px;" />
      <line v-if="proba > 9" x1="230" y1="170" x2="250" y2="200" style="stroke:black;fill:none;stroke-width:2px;" />
      <line v-if="proba > 10" x1="230" y1="170" x2="210" y2="200" style="stroke:black;fill:none;stroke-width:2px;" />
    </svg>
    <div>
      <div class="betu" v-for="betu in wordDisplaybetus">
        {{betu}}
      </div>
    </div>
    <template v-if="initialized">
      <div>
        <div @click="trybetu(betu)" class="possiblebetu" :class="getStrikethroughClass(betu)" v-for="betu in possiblebetus1">
          {{betu}}
        </div>
      </div>
      <div>
        <div @click="trybetu(betu)" class="possiblebetu" :class="getStrikethroughClass(betu)" v-for="betu in possiblebetus2">
          {{betu}}
        </div>
      </div>
      <div>
        <div @click="trybetu(betu)" class="possiblebetu" :class="getStrikethroughClass(betu)" v-for="betu in possiblebetus3">
          {{betu}}
        </div>
      </div>
    </template>
    <button @click="initialize()">Új Játék</button>
  </div>
</template>

<script>

  export default {
    name: 'app',
    data: function () {
      return {
        proba: 12,
        possiblebetus1: ["A", "Á", "B", "C", "D", "E", "É", "F", "G", "H", "I"],
        possiblebetus2: ["Í", "J", "K", "L", "M", "N", "O","Ó","Ö", "Ő", "P", "Q", "R", "S"],
        possiblebetus3: ["T", "U", "Ú", "Ü", "Ű", "V", "W", "X", "Y", "Z"],
        initialized: false,
        wordBank: ['ALMA', 'KÁVÉ', 'EGYETEM', 'ÖSZTÖNDÍJ', 'LEKVÁR', 'SZILVA', 'TÉL', 'DIPLOMA', 'KERESZTFÉLÉV', 'VUE', 'JAVASCRIPT', 'WINDOWS']
      }
    },
    methods: {
      initialize() {
        this.initialized = true
        this.proba = 0
        this.word = this.getVeletlenSzo()
        this.wordbetus = this.word.split('')
        this.wordDisplaybetus = Array(this.word.length)
        this.usedbetus = []
      },
      getVeletlenSzo() {
        let index = Math.random() * (this.wordBank.length )
        index = Math.floor(index)
        
        let word = this.wordBank[index]
        this.wordBank.splice(index, 1) // kiveszi a betűt, hogy ne ismétlődjön

        return word
      },
      trybetu(betu) {
        if (this.usedbetus.includes(betu)) {
          return
        }

        this.usedbetus.push(betu)
        let match = false
        for (let i = 0; i < this.wordDisplaybetus.length; i++) {
          if (betu === this.wordbetus[i]) {
            this.wordDisplaybetus.splice(i, 1, betu)
            match = true
          }
        }

        if (!match) {
          this.proba++
        }
      },
      getStrikethroughClass(betu) {
        if (this.usedbetus.includes(betu)) {
          return 'diagonal-strike'
        }
        return null
      }
    }
  }
</script>

<style>
  #app {
    text-align: center;
  }

.betu {
  display: inline-block;
  border-bottom: 1px solid;
  margin: 0px 3px 0px 3px;
  font-size: 30px;
  min-width: 30px;
  vertical-align: bottom;
}

.possiblebetu {
  display: inline-block;
  margin: 10px 3px 0px 3px;
  font-size: 30px;
  min-width: 30px;
  cursor: pointer;
}

.diagonal-strike {
  background: linear-gradient(to left top, transparent 47.75%, currentColor 49.5%, currentColor 50.5%, transparent 52.25%);
  color: red;
}

button {
  margin-top: 20px;
  padding: 6px 12px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 15px;
}

button:hover {
    background-color: #e6e6e6;
    border-color: grey;
}
</style>