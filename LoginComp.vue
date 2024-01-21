<template>
  <div class="login-container">
    <div class="login-content">
      <div class="black-square" @mouseover="changeColor" @mouseout="resetColor">
        <img class="logo" src="@/assets/sing.svg" alt="Logo" />
        <div class="slogan" :style="{ color: textColor }">
          <div class="textblock">
            <p>Não fale dos seus sonhos para as pessoas, <span><br />Simplesmente mostre a elas!</span></p>
          </div>
        </div>

        <div class="cube" ref="cube">
          <div class="face face--front"></div>
          <div class="face face--right"></div>
          <div class="face face--back"></div>
          <div class="face face--left"></div>
          <div class="face face--top"></div>
          <div class="face face--bottom"></div>
        </div>
      </div>

      <div class="login-form">
        <h2>Login</h2>
        <label class="input-label" for="email">
          <i class="fa-solid fa-envelope icon"></i>
          <span class="label-text">Endereço de email :</span>
        </label>
        <input class="input-field" type="email" v-model="email" id="email" placeholder="exemplo@gmail.com" />
        <label class="input-label" for="password">
          <i class="fa-solid fa-lock icon"></i>
          <span class="label-text">Senha de acesso :</span>
        </label>
        <input class="input-field" type="password" v-model="password" id="password" placeholder="*********************" />
        <button class="login-button" @click="login">
          Acessar
        </button>
        <div class="signup-link">
          <p>Não tem conta? <span @click="navigateToSignup">Cadastre-se agora!</span></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import '@fortawesome/fontawesome-free/css/all.css';

export default {
  data() {
    return {
      email: '',
      password: '',
      textColor: 'black',
    };
  },
  methods: {
    changeColor() {
      this.textColor = 'white';
      this.$refs.cube.classList.add('white-cube');
    },
    resetColor() {
      this.textColor = 'black';
      this.$refs.cube.classList.remove('white-cube');
    },
  },
};
</script>

<style scoped>
@import '~typeface-montserrat/index.css';

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Montserrat', sans-serif;
}

.login-container {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.login-content {
  display: flex;
  align-items: center;
  border: 2px solid #8c858557; 
  border-radius: 10px;
  padding: 40px;
}

.black-square {
  width: 609px;
  height: 599px;
  background-color: rgba(245, 245, 245, 0.598);
  text-align: center;
  padding: 20px;
  position: relative;
  transition: background-color 0.3s;
}

.black-square:hover {
  background-color: #000000;
}

.logo {
  width: 80px;
  height: 80px;
  position: absolute;
  top: 50px;
  left: 95px;
}

.slogan {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 14px;
}

.signup-link {
  margin-top: 20px;
  font-size: 14px;
}

.login-form {
  margin-left: 40px;
  text-align: center;
  width: 535px;
  height: 375px;
  padding: 20px;
  margin-top: 90px;
}

h2 {
  margin-bottom: 20px;
}

.textblock p {
  display: flex;
  font-size: 25px;
  white-space: nowrap;
}

.textblock span {
  font-weight: bold;
  display: flex;
  margin-top: 5px;
  position: absolute;
}

.input-label {
  display: flex;
  align-items: center;
  margin-top: 10px;
  font-size: 16px;
  font-weight: bold;
}

.label-text {
  margin-left: 10px;
}

.input-field {
  width: 100%;
  padding: 8px;
  margin-top: 5px;
  margin-bottom: 15px;
  box-sizing: border-box;
}

.login-button {
  background-color: #000000;
  color: #ffffff;
  padding: 15px 40px;
  border: none;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.3s, color 0.3s;
}

.login-button:hover {
  background-color: #c2bbbb;
  color: #000000;
}

.icon {
  font-family: 'Font Awesome 5 Free';
  color: #000000;
  margin-right: 0px;
}

.cube {
  width: 100px;
  height: 100px;
  position: absolute;
  top: 70%;
  right: 68%;
  animation: rotate 10s infinite alternate;
  transform-style: preserve-3d;
}

.face {
  border: 2px solid #000000;
  background: linear-gradient(45deg, #10111153, #0f0f0fde);
  display: flex;
  align-items: center;
  justify-content: center;
  color: #0f0e0e;
  width: 100px;
  height: 100px;
  position: absolute;
}

.face--front {
  transform: translateZ(50px);
}

.face--right {
  transform: rotateY(90deg) translateZ(50px);
}

.face--back {
  transform: rotateY(180deg) translateZ(50px);
}

.face--left {
  transform: rotateY(-90deg) translateZ(50px);
}

.face--top {
  transform: rotateX(90deg) translateZ(50px);
}

.face--bottom {
  transform: rotateX(-90deg) translateZ(50px);
}

.white-cube .face {
  background: linear-gradient(45deg, #ffffff94, whitesmoke);
  border-color: white;
  color: black;
}

@keyframes rotate {
  from {
    transform: rotateX(-20deg) rotateY(-10deg);
  }

  50% {
    transform: rotateX(20deg) rotateY(320deg);
  }

  to {
    transform: rotateX(-20deg) rotateY(-20deg);
  }
}
</style>
