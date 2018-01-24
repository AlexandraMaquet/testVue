<template>
  <div class="first-container">
    <div class="header">
      <div class="buttons">
        <div class="button" @click="$router.go(-1)">
          Précédent
        </div>
        <div class="button" style="visibility: hidden">
          Suivant
        </div>
      </div>
      <div class="title">
        Ton dernier défi, un peu de javascript.
      </div>
      <div class="content">
        <p>Le but de cet exercice est d'évaluer ton sens de l'algorithmie'.</p>
        <p>créer un algorithme pour déchiffrer le message secret</p>
        <p>Le chiffre de césar, tu connais?</p>
        <p>un chiffre de césar te permet de cripter une chaine de caractère en décalant la lettre,</p>
        <p>du nombre de lettre défini par une variable (aucune lettre avec un accent)</p>
        <p>ex: cesar(2, "salut") retournera "ucnqv"</p>
        <p>a toi de jouer (et ne triche pas, on le vera!!!)</p>
      </div>
    </div>
    <div class="body">
      <div class="left">
        <ul class="themes">
          Thèmes:
          <li>Algorithme</li>
          <li>JavaScript</li>
          <li>César</li>
        </ul>
      </div>
      <div class="separator">
      </div>
      <div class="right">
        <div>
          <p><span>Ex codice :</span> "{{phrase}}"</p>
          <p><span>Ex numerus :</span> <input type="number" name="" value="" v-model="number"></p>
        </div>
        <div class="caesar">
          <p> ====> {{caesar(number, phrase)}}
            <==== </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        number: 0,
        phrase: 'Salve, ego Julius Caesar.'
      }
    },
    methods: {
      caesar: function(number, text) {
        this.number = Number(number);
        let i = 0;
        let result = "";
        while (i < text.length) {
          let char = text[i].charCodeAt();
          if (this.isLetter(char)) {
            char += this.number;
            if (this.isAfterZ(char)) {
              char -= 26;
            }
            if (this.isBeforeA(char)) {
              char += 26;
            }
          }
          let newChar = String.fromCharCode(char);
          result += newChar;
          i++;
        }
        return result;
      },
      isLetter: function(char) {
        return (
          this.isLowestCaseLetter(char) ||
          this.isUpperCaseLetter(char)
        );
      },
      isBeforeA: function(char) {
        let aLetter = "a".charCodeAt(0);
        let aUpperLetter = "A".charCodeAt(0);
        return (
          (aLetter > char && char >= aLetter + this.number) || (aUpperLetter > char && char >= aUpperLetter + this.number)
        );
      },
      isAfterZ: function(char) {
        let zLetter = "z".charCodeAt(0);
        let zUpperLetter = "Z".charCodeAt(0);
        return (
          (zLetter < char && char <= zLetter + this.number) || (zUpperLetter < char && char <= zUpperLetter + this.number)
        );
      },
      isLowestCaseLetter: function(char) {
        let minLetter = "a".charCodeAt();
        let maxLetter = "z".charCodeAt();
        return minLetter <= char && char <= maxLetter;
      },
      isUpperCaseLetter: function(char) {
        let minUpperCaseLetter = "A".charCodeAt();
        let maxUpperCaseLetter = "Z".charCodeAt();
        return (
          minUpperCaseLetter <= char && char <= maxUpperCaseLetter
        );
      }
    },
    components: {}
  }
</script>

<style scoped>
  .right input {
    width: 30px;
    border: none;
  }
  
  .right {
    color: #726951;
  }

  .right span {
    text-decoration: underline;
    font-weight: bold;
  }
  
  .caesar {
    width: 500px;
    height: 200px;
    margin-top: 50px;
    background: url("../../../../assets/Caesar.jpg") no-repeat;
    background-size: 300px;
    background-position: right top;
    border: 2px solid #726951;
  }
  
  .caesar p {
    padding-left: 15px;
  }
</style>
