<template>
  <picture class="cubo-picture">
    <source srcset="./assets/images/illustration-box-desktop.svg">
    <img src="./assets/images/illustration-box-desktop.svg" alt="desenho de uma caixa que está sobre outro desenho">
  </picture>

  <main>

    <picture class="woman-picture-desktop">
      <source srcset="./assets/images/illustration-woman-online-desktop.svg">
      <img src="./assets/images/illustration-woman-online-desktop.svg"
        alt="desenho da pagina de uma moça em frente a uma tela grande de computador">
    </picture>

    <picture class="woman-picture-mobile">
      <source srcset="./assets/images/illustration-woman-online-mobile.svg">
      <img src="./assets/images/illustration-woman-online-mobile.svg"
        alt="desnho da pagina de uma moça em frente a uma tela grande de computador">
    </picture>

    <div id="acordeon-area">

      <h1>FAQ</h1>

      <div class="acordeon" v-for="(questionEanswer, index) in listQuestions" :key="index"
        :class="{ open: qualAberto === index }">
        <div class="acord-div">
          <button class="button" @click="AbrirAcordeon(index)">
            <p class="question">{{ questionEanswer.question }}</p>

            <svg width="10" height="5" xmlns="http://www.w3.org/2000/svg">
              <path d="M1 .799l4 4 4-4" stroke="#F47B56" stroke-width="2" fill="none" fill-rule="evenodd" />
            </svg>

          </button>
          <div v-if="qualAberto === index" class="acord">
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
      qualAberto: 0,
    }

  }, methods: {

    AbrirAcordeon(index) {
      this.qualAberto = index
      console.log('imprime ae se tu é o bixão:', index, 'e imprime tbm qual está aberto:', this.qualAberto)
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Kumbh+Sans:wght@400;700&display=swap');

@keyframes crescerAcord {

  0% {
    height: 0px;
  }

  100% {
    height: 90px;
  }

}


:root {


  --titulo-acordeon-aberto: hsl(238, 29%, 16%);
  --hoverEsetas: hsl(14, 88%, 65%);
  --Soft-violet: hsl(273, 75%, 66%);
  --Soft-blue: hsl(240, 73%, 65%);
  --borda-baixo-div: hsl(237, 12%, 33%);
  --Dark-grayish-blue: hsl(240, 6%, 50%);
  --backgroundMain: hsl(240, 5%, 91%);

  --cursorObj: pointer;
}

h1 {
  color: black;
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
  background-image: none;
  background: linear-gradient(to left, var(--Soft-blue), var(--Soft-violet));
  color: transparent;
  font-size: 12px;
  font-family: 'Kumbh Sans', sans-serif;
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

.woman-picture-mobile {
  display: none;
}

#acordeon-area {

  display: flex;
  flex-direction: column;
  gap: 30px;
  padding: 10px;
  padding-bottom: 40px;
}

.acordeon {

  display: flex;
  flex-direction: column;
}

.acord-div {

  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  gap: 5px;
  border-bottom: solid 1px var(--borda-baixo-div);
}

.acordeon.open .question {

  font-weight: bold;
}

.acordeon.open .acord-div svg {

  transform: rotate(180deg);
}

.button {

  display: flex;
  width: 100%;
  cursor: var(--cursorObj);
  background: none;
  border: none;
  align-items: center;
  gap: 10px;
}

.button:hover {

  color: var(--hoverEsetas);
}

.acord {

  display: flex;
  align-items: center;
  justify-content: center;
  color: black;
  animation: crescerAcord infinite;
  transition: ease-in-out 0.3s;
}

.cubo-picture {
  display: flex;
  position: absolute;
  transform: translate(-470px, 90px);
}

.woman-picture-desktop {

  display: flex;
  align-items: center;
}

.woman-picture-desktop img {

  width: 400px;
  object-fit: fill;
  object-position: -60px;

}

@media (max-width: 375px) {

  .cubo-picture{
    display: none;
  }

  .woman-picture-desktop {
    display: none;
  }

  .woman-picture-mobile {
    display: flex;
    align-self: center;
    width: 170px;
    height: 170px;
    transform: translate(-30px, -180px);
    position: absolute;
    
  }

  #app {

    display: flex;
    flex-direction: column;
    padding: 20px;
    gap: 5px;
  }

  h1{
    display: flex;
    align-self: center;
    transform: translateY(10px);
    font-size: 28px;
  }

  main {
    margin-top: 80px;
    display: flex;
    flex-direction: column;
    width: 350px;
    height: 100%;
    background-image: url(./assets/images/bg-pattern-mobile.svg);
    background-position: 50% 20px;
    background-size: 228px;
    padding-top: 80px;
    gap: 5px;
  }

  #acordeon-area{

    margin-top: 40px;
    display: flex;
    gap: 10px;
    padding: 5px;
    padding-inline: 20px;
    margin-bottom: 40px;
    border-bottom-color: var(--Dark-grayish-blue);
  }

  .acordeon{
    display: flex;
    gap: 5px;
    height: 70%;
  }

    

}
</style>
