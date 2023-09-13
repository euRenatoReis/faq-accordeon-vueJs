<template>
  <picture class="cubo-picture">
    <source srcset="./assets/images/illustration-box-desktop.svg">
    <img src="./assets/images/illustration-box-desktop.svg" alt="desenho de uma caixa que está sobre outro desenho">
  </picture>

  <main>

    <picture class="woman-picture">
      <source srcset="./assets/images/illustration-woman-online-desktop.svg">
      <img src="./assets/images/illustration-woman-online-desktop.svg"
        alt="desenho da pagina de uma moça em frente a uma tela grande de computador">
    </picture>

    <div id="acordeon-area">

      <h1>FAQ</h1>

      <div class="acordeon" v-for="(question, index) in listQuestions" :key="index">
        <div class="acord-div">
          <input class="button" @click="AbrirAcordeon" type="button" v-model="listQuestions[index].question">
          <div class="acord">
            <p>{{ listQuestions[index].answer }}</p>
          </div>
        </div>
      </div>

    </div>
  </main>
</template>

<script>


export default {
  name: 'App',
  data() {

    return {

      listQuestions:
        [
          { question: "How many team members can I invite?", answer: "You can invite up to 2 additional users on the Free plan. There is no limit on team members for the Premium plan." },
          { question: "What is the maximum file upload size?", answer: "No more than 2GB. All files in your account must fit your allotted storage space." },
          { question: "How do I reset my password?", answer: "Click “Forgot password” from the login page or “Change password” from your profile page. A reset link will be emailed to you." },
          { question: "Can I cancel my subscription?", answer: "Yes! Send us a message and we’ll process your request no questions asked." },
          { question: "Do you provide additional support?", answer: "Chat and email support is available 24/7. Phone lines are open during normal business hours." }
        ],
      aberto: false

    }

  }, methods: {

    AbrirAcordeon() {
      this.aberto = !this.aberto
      if (!aberto) {

        console.log('meuds')
      }
    }
  }
}
</script>

<style>
:root {

  /* text */
  --titulo-acordeon-aberto: hsl(238, 29%, 16%);
  --hoverEsetas: hsl(14, 88%, 65%);
  /* background */
  --Soft-violet: hsl(273, 75%, 66%);
  --Soft-blue: hsl(240, 73%, 65%);
  /* text */
  --borda-baixo-div: hsl(237, 12%, 33%);
  --Dark-grayish-blue: hsl(240, 6%, 50%);
  /* dividers */
  --backgroundMain: hsl(240, 5%, 91%);

  --cursorObj: pointer;
}

#app {

  display: flex;
  font-size: 12px;
  justify-content: center;
  align-items: center;
}

body {

  display: flex;
  justify-content: center;
  align-items: center;
  background-color: darkgoldenrod;
}

main {

  display: flex;
  flex-direction: row;
  background-color: var(--backgroundMain);
  background-image: url(./assets/images/bg-pattern-desktop.svg);
  background-position: left;
  background-repeat: no-repeat;
  background-size: 42%;
  justify-self: center;
  align-self: center;
  width: 900px;
  height: 550px;
  gap: 20px;
  border-radius: 30px;
  margin-top: 10%;
}

#acordeon-area {

  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 10px;
}

.acordeon {

  display: flex;
  flex-direction: column;
}

.acord-div {

  height: 70px;
  gap: 5px;
  border-bottom: solid 1px var(--borda-baixo-div);
}

.button {

  display: flex;
  width: 100%;
  cursor: var(--cursorObj);
  background: none;
  border: none;
}

.button:hover {

  color: var(--hoverEsetas);
}

.acord {

  display: flex;
  height: 0px;
}

.acord.ativo {

  height: 190px;
  display: flex;
  align-items: center;
  justify-content: center;

}

.cubo-picture {
  display: flex;
  position: absolute;
  transform: translate(-470px, 90px);
}

.woman-picture {

  display: flex;
  align-items: center;
}

.woman-picture img {

  width: 400px;
  object-fit: fill;
  object-position: -60px;

}
</style>
