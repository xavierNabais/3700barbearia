<template>


    <Header />
    
    <div class="section2">
      <div class="content2">
        <span class="title2">INICIAR SESSÃO</span>
      </div>
    </div>



<!-- DESKTOP -->


    <div style="width: 100%; height: 1000px; background-color: white; padding-bottom: 10%;" class="desktop">
      



      <div class="profile-container" style="margin-top: 0;padding-top:5%">
        <div class="profile-section-left" style="text-align: left;margin-left:10%;">
            <div class="personal-info">
              <div class="info-header login">
                INICIAR SESSÃO
              </div>
              <hr class="small-divider">
              <div class="info-description">
                Por favor, insira suas credenciais para iniciar sessão e acessar sua conta.
              </div>

              <div style="margin: 30px 0px;">

                <GoogleLogin :callback="googleCallback" prompt/>
            </div>

            </div>
            <form id="loginForm" @submit.prevent="login">
            <div class="form-container">
            <div class="input-group">
                <div>
                  <label for="nome" class="login-label">Endereço de Email</label>
                  <br>
                  <input type="email" id="email" name="email" v-model="email" class="login">
                </div>
              </div>
              <div class="input-group">
                <label for="username" class="login-label">Password</label>
                <br>
                <input type="password" id="password" name="password" v-model="password" class="login">
              </div>
            </div>
            <a href=""><p style="font-size:15px; text-decoration:underline;color:#F2B709">Perdeu a senha?</p></a>
            <button type="submit" class="login-button">INICIAR SESSÃO</button>

              <div class="success-message" v-if="login_success">
                A iniciar sessão...
              </div>
              <div class="success-message" v-if="login_error">
                Email ou password incorretos.
              </div>
            </form>
        </div>

        <div class="profile-section-right">
            <div class="personal-info">
              <div class="info-header login">
                CRIAR NOVA CONTA
              </div>
              <hr class="small-divider">
              <div class="info-description">
                Para criar uma nova conta, preencha o formulário com suas informações pessoais e escolha um nome de usuário e senha únicos.
              </div>
            </div>
            <form id="loginForm" @submit.prevent="registo">
            <div class="form-container">
            <div class="input-group">
                <div>
                  <label for="email" class="login-label">Endereço de email</label>
                  <br>
                  <input type="text" id="email" class="login" v-model="r_email"> 
                </div>
              </div>
              <div class="input-group">
                <label for="password" class="login-label">Password</label>
                <br>
                <input type="password" id="password" class="login" v-model="r_password">
              </div>
            </div>
            <p>Os seus dados pessoais serão usados para apoiar a sua experiência no site 3700barbershop.pt
            Serão utilizados para gerir o acesso à sua conta e outros fins descritos na nossa política de privacidade</p>
            <button type="submit" class="login-button">REGISTAR NOVA CONTA</button>
            <div class="success-message" v-if="registo_success">
                A criar conta...
            </div>
            <div class="success-message" v-if="registo_error">
                Endereço de email existente!
            </div>
          </form>
        </div>


      </div>




    </div>



    <!-- MOBILE -->

    <div style="text-align:center;background-color: white; padding-bottom: 10%;" class="mobile">
      



      <div style="margin-top: 0;padding:5%">
        <div>
            <div class="personal-info">
              <div class="info-header login">
                INICIAR SESSÃO
              </div>
              <hr class="small-divider" style="margin:auto">
              <div class="info-description" style="margin-top:5%">
                Por favor, insira suas credenciais para iniciar sessão e acessar sua conta.
              </div>

              <div style="margin: 30px 0px;">

                <GoogleLogin :callback="googleCallback" prompt/>
            </div>

            </div>
            <form id="loginForm" @submit.prevent="login">
            <div>
            <div class="input-group">
                <div>
                  <label for="nome" class="login-label">Endereço de Email</label>
                  <br>
                  <input type="email" id="email" name="email" v-model="email" class="login">
                </div>
              </div>
              <div class="input-group">
                <label for="username" class="login-label">Password</label>
                <br>
                <input type="password" id="password" name="password" v-model="password" class="login">
              </div>
            </div>
            <a href=""><p style="font-size:15px; text-decoration:underline;color:#F2B709">Perdeu a senha?</p></a>
            <button type="submit" class="login-button">INICIAR SESSÃO</button>

              <div class="success-message" v-if="login_success">
                A iniciar sessão...
              </div>
              <div class="success-message" v-if="login_error">
                Email ou password incorretos.
              </div>
            </form>
        </div>
      </div>

      <div style="margin-top: 0;padding:5%">
            <div class="personal-info">
              <div class="info-header login">
                CRIAR NOVA CONTA
              </div>
              <hr class="small-divider" style="margin:auto">
              <div class="info-description" style="margin-top:5%">
                Para criar uma nova conta, preencha o formulário com suas informações pessoais e escolha um nome de usuário e senha únicos.
              </div>
            </div>
            <form id="loginForm" @submit.prevent="registo">
            <div>
            <div class="input-group">
                <div>
                  <label for="email" class="login-label">Endereço de email</label>
                  <br>
                  <input type="text" id="email" class="login" v-model="r_email" required> 
                </div>
              </div>
              <div class="input-group">
                <label for="password" class="login-label">Password</label>
                <br>
                <input type="password" id="password" class="login" v-model="r_password" required>
              </div>
            </div>
            <p>Os seus dados pessoais serão usados para apoiar a sua experiência no site 3700barbershop.pt
            Serão utilizados para gerir o acesso à sua conta e outros fins descritos na nossa política de privacidade</p>
            <button type="submit" class="login-button">REGISTAR NOVA CONTA</button>
            <div class="success-message" v-if="registo_success">
                A criar conta...
            </div>
            <div class="success-message" v-if="registo_error">
                Endereço de email existente!
            </div>
          </form>
        </div>

    </div>

    
    <Footer />
    
      </template>
      
      <script>
      import Header from '../../components/Header.vue';
      import Footer from '../../components/Footer.vue';
      import { decodeCredential } from 'vue3-google-login';
      
      export default {
        components: {
          Header,
          Footer,
        },
        name: 'loginPage',
        data() {
          return {
            email: '',
            password: '',
            r_email: '',
            r_password: '',
            login_error: false,
            login_success: false,
            registo_success: false,
            registo_error: false,
          };
        },
        methods: {

          // Função para autenticação do Google
          async googleCallback(response) {
            const accessData = decodeCredential(response.credential);


              try {
              const response = await fetch('https://3700barbearia-api.vercel.app/login/google', {
                method: 'POST',
                headers: {
                  'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                  accessData
                })
              });
              const data = await response.json();
              
              if (response.ok) {
                localStorage.setItem('token', data.token); 
                this.login_error = false;
                this.login_success = true;
                setTimeout(() => {
                    this.login_error = false;
                    window.location.href= '/';
                }, 1500);
              } else {
                this.login_error = true;
              }
            } catch (error) {
              console.error('Erro ao efetuar login:', error);
            }
          },

          // Função para realizar o login com email e password
          async login() {
            try {
              const response = await fetch('https://3700barbearia-api.vercel.app/login', {
                method: 'POST',
                headers: {
                  'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                  email: this.email,
                  password: this.password
                })
              });
              const data = await response.json();
              
              if (response.ok) {
                localStorage.setItem('token', data.token); 
                this.login_error = false;
                this.login_success = true;
                setTimeout(() => {
                    this.login_error = false;
                    window.location.href= '/';
                }, 1500);
              } else {
                this.login_error = true;
              }
            } catch (error) {
              console.error('Erro ao efetuar login:', error);
            }
          },

          // Função para realizar o registo de um novo utilizador
          async registo() {
            try {
              const response = await fetch('https://3700barbearia-api.vercel.app/registo', {
                method: 'POST',
                headers: {
                  'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                  email: this.r_email,
                  password: this.r_password
                })
              });
              const data = await response.json();
              
              if (response.ok) {
                localStorage.setItem('token', data.token); 
                this.registo_success = true;
                setTimeout(() => {
                    this.registo_success = false;
                    window.location.href= '/';
                }, 1500);
              } else {
                this.registo_error = true;
                console.log(data); 
              }
            } catch (error) {
              console.error('Erro ao efetuar registo:', error);
            }
          }
        }
      };
      </script>
      

      <style scoped>
      .success-message {
      color: black;
      font-weight: bold;
      font-size:18px;
      border-bottom:1px solid #F4B604;
      padding: 15px 20px;
      border-radius: 5px;
      margin-top: 20px;
      text-align: center;
      width:300px;
    }
      </style>