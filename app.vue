<template>
  <div class="app">
    <div class="container">
      <input type="checkbox" id="flip">
      <div class="cover">
        <div class="front">
          <img src="https://source.unsplash.com/random/900×700/?food" alt="">
          
        </div>
        <div class="back">
         <img class="backImg" src="https://source.unsplash.com/random/900×700/?food" alt="">
          
        </div>
      </div>
      <!-- LONGIN FORM -->
      <div class="forms">
          <div class="form-content">
            <div class="login-form">
              <div class="title">Inicio de sesión</div>
            <form action="#" id="login" @submit="checkForm" >
              <div class="input-boxes">
                <div class="input-box">
                  <i class="fas fa-envelope"></i>
                  <input type="email" placeholder="Ej: abc@xyz.com" id="email" v-model="email">
                </div>
                <div class="input-box">
                  <i class="fas fa-lock"></i>
                    <input  placeholder="Contraseña" required :rules="[rules.required, rules.min]" :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'" :type="show1 ? 'text' : 'password'" name="input-10-2" label="Contraseña" filled
                  @click:append="show1 = !show1">
                </div>
                <div class="text sign-up-text"><a href="#">Olvidaste tu contraseña?</a></div>
                <div class="button input-box">
                  <input type="submit" value="Ingresar"  @click="index()">
                </div>
                
                <div class="text sign-up-text">No tienes una cuenta? <label for="flip">Registrate aquí</label></div>
              </div>
          </form>
        </div>
        <!-- REGISTER FORM -->
          <div class="signup-form">
            <div class="title">Registro</div>
          <form action="#">
              <div class="input-boxes">
                <div class="input-box">
                  <i class="fas fa-user"></i>
                  <input type="text" placeholder="Nombre/s" required>
                </div>
                <div class="input-box">
                  <i class="fas fa-user"></i>
                  <input type="text" placeholder="Apellidos" required>
                </div>
                <div class="input-box">
                  <i class="fas fa-envelope"></i>
                  <input type="text" placeholder="Ej: abc@xyz.com" required>
                </div>
                <div class="input-box">
                  <i class="fas fa-lock"></i>
                  <input type="password" placeholder="Contraseña" required :rules="[rules.required, rules.min]">
                </div>
                <div class="button input-box">
                  <input type="submit" value="Registrar">
                </div>
                <div class="text sign-up-text">Ya tienes una cuenta? <label for="flip">Inicia sesión aquí</label></div>
              </div>
        </form>
      </div>
      </div>
      </div>
    </div>  

  </div>
    
</template>

<script>
export default {
  methods: {
    index(){
      this.$router.push('./pages/index');
    }
  },
  data(){
    return{
      show1: false,
      password: "Password",
      rules: {
        required: (value) => !!value || "Required",
        min: (v) => v.length >= 8 || "Minimo 8 caracteres",
      }
    };
  }
};

</script>

<style scoped>
/* Google Font Link */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;600;700&display=swap');
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins" , sans-serif;
}
.app{
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #00c1770e;
  padding: 30px;
}
a {
  color: #00a33f;
}
.container{
  position: relative;
  max-width: 1150px;
  width: 100%;
  background: #fff;
  padding: 40px 30px;
  box-shadow: 0 5px 10px rgba(0,0,0,0.2);
  perspective: 2700px;
  top: 50%;

}
.container .cover{
  position: absolute;
  top: 0;
  left: 50%;
  height: 100%;
  width: 50%;
  z-index: 98;
  transition: all 1s ease;
  transform-origin: left;
  transform-style: preserve-3d;
}
.container #flip:checked ~ .cover{
  transform: rotateY(-180deg);
}
 .container .cover .front,
 .container .cover .back{
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
}
.cover .back{
  transform: rotateY(180deg);
  backface-visibility: hidden;
}
.container .cover::before,
.container .cover::after{
  content: '';
  position: absolute;
  height: 100%;
  width: 100%;
  background: #00c176;
  opacity: 0.5;
  z-index: 12;
}
.container .cover::after{
  opacity: 0.3;
  transform: rotateY(180deg);
  backface-visibility: hidden;
}
.container .cover img{
  position: absolute;
  height: 100%;
  width: 100%;
  object-fit: cover;
  z-index: 10;
}
.container .cover .text{
  position: absolute;
  z-index: 130;
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.cover .text .text-1,
.cover .text .text-2{
  font-size: 26px;
  font-weight: 600;
  color: #fff;
  text-align: center;
}
.cover .text .text-2{
  font-size: 15px;
  font-weight: 500;
}
.container .forms{
  height: 100%;
  width: 100%;
  background: #fff;
}
.container .form-content{
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-content .login-form,
.form-content .signup-form{
  width: calc(100% / 2 - 25px);
}
.forms .form-content .title{
  position: relative;
  font-size: 24px;
  font-weight: 500;
  color: #333;
}
.forms .form-content .title:before{
  content: '';
  position: absolute;
  left: 0;
  bottom: 0;
  height: 3px;
  width: 25px;
  background: #00c176;
}
.forms .signup-form  .title:before{
  width: 20px;
}
.forms .form-content .input-boxes{
  margin-top: 30px;
}
.forms .form-content .input-box{
  display: flex;
  align-items: center;
  height: 50px;
  width: 100%;
  margin: 10px 0;
  position: relative;
}
.form-content .input-box input{
  height: 100%;
  width: 100%;
  outline: none;
  border: none;
  padding: 0 30px;
  font-size: 16px;
  font-weight: 500;
  border-bottom: 2px solid rgba(0,0,0,0.2);
  transition: all 0.3s ease;
}
.form-content .input-box input:focus,
.form-content .input-box input:valid{
  border-color: #00c176;
}
.form-content .input-box i{
  position: absolute;
  color: #00c176;
  font-size: 17px;
}
.forms .form-content .text{
  font-size: 14px;
  font-weight: 500;
  color: #333;
}
.forms .form-content .text a{
  text-decoration: none;
}
.forms .form-content .text a:hover{
  text-decoration: underline;
}
.forms .form-content .button{
  color: #fff;
  margin-top: 40px;
}
.forms .form-content .button input{
  color: #fff;
  background: #00c176;
  border-radius: 6px;
  padding: 0;
  cursor: pointer;
  transition: all 0.4s ease;
}
.forms .form-content .button input:hover{
  background: #00a33f;
}
.forms .form-content label{
  color: #00a33f;
  cursor: pointer;
}
.forms .form-content label:hover{
  text-decoration: underline;
}
.forms .form-content .login-text,
.forms .form-content .sign-up-text{
  text-align: center;
  margin-top: 25px;
}
.container #flip{
  display: none;
}
@media (max-width: 730px) {
  .container .cover{
    display: none;
  }
  .form-content .login-form,
  .form-content .signup-form{
    width: 100%;
  }
  .form-content .signup-form{
    display: none;
  }
  .container #flip:checked ~ .forms .signup-form{
    display: block;
  }
  .container #flip:checked ~ .forms .login-form{
    display: none;
  }
}

</style>
