<template>

    <Header />
    
    <div class="section2">
      <div class="content2">
        <span class="title2">EDITAR PERFIL</span>
      </div>
    </div>



    <div style="width: 100%; height: 1200px; background-color: white; padding-bottom: 10%;" class="desktop">
      
      <div v-if="alertMessage" style="left: 42vw; top:10%; position: fixed; background-color: black; color: white; padding: 20px 20px;border-radius:20px">
        <i class="fas fa-info-circle" style="color:#F4B604"></i> <span style="margin-left:20px"> {{ alertMessage }} </span>
      </div>


      <div class="single-title">
        <p>Para Agendar ou Cancelar Agendamentos, clique no botão abaixo.</p>
        <a href="/perfil/marcacoes"><button style="cursor: pointer;">VER MARCAÇÕES</button></a>
      </div>


      <div class="profile-container">
        <div class="profile-section-left">
          <div class="item-container">

            <div class="item bold">
              Editar Perfil
            </div>
              <hr class="divider">
            <div class="item">
              <a href="/perfil/marcacoes" style="color:Black">Marcações</a>
            </div>
              <hr class="divider">
            <div class="item">
              <a href="/perfil/recompensa" style="color:Black">Recompensa</a>
            </div>
            <hr class="divider">
          </div>

        </div>

        <div class="profile-section-right">
            <div class="personal-info">
              <div class="info-header">
                Informações pessoais
              </div>
              <hr class="small-divider">
              <div class="info-description">
                Personalize o seu perfil facilmente! Atualize as suas informações pessoais de forma rápida e simples para garantir que sua conta esteja sempre atualizada.
              </div>
            </div>
            
            <div class="form-container">
              <form @submit.prevent="submitForm1">
              <div class="input-group" style="display:flex; flex-direction: row;">
                <div>
                  <label for="nome">Nome</label>
                  <br>
                  <input type="text" id="nome" v-model="utilizador.Nome" style="text-indent: 10px; color:grey">
                </div>
                <div style="margin-left: 5%;">
                  <label for="apelido">Apelido</label>
                  <br>
                  <input type="text" id="apelido" v-model="utilizador.Apelido" style="text-indent: 10px; color:grey">
                </div>
              </div>
              <div class="input-group">
                <label for="username">Username</label>
                <br>
                <input type="text" id="username" name="username" v-model="utilizador.Username" style="text-indent: 10px; color:grey">
              </div>
              <button class="save-button" @click.prevent="saveConfirmation()">Guardar</button>
              <transition name="fade" appear style="margin:15px 0px;">
                <p v-if="showConfirmationMessage" class="confirmation-message">
                  Tem a certeza que quer editar o perfil?
                  <br>
                  <button type="submit" class="save-button" style="margin-top:2%;">
                    Sim
                  </button>
                  <button class="save-button" @click.prevent="saveConfirmation()" style="margin-top:2%;margin-left:20px">
                    Não
                  </button>
                </p>
              </transition>
              <div class="success-message" v-if="perfilAtualizado1">
                A atualizar perfil...
              </div>  
                            <div class="success-message" v-if="erro1">
                              {{  erro1Message.message }}
                            </div>  
            </form>


            </div>



            <hr style="border: 1px solid #0000002d;margin-top: 5%; margin-bottom: 5%;">

                <div class="bottom-division">
                        <div class="left-division">
                          <form @submit.prevent="submitForm2">
                            <div class="personal-info">
                              <div class="info-header">
                                Email
                              </div>
                              <hr class="small-divider">
                              <div class="info-description">
                                Gerencie o seu email com facilidade! Mantenha o seu contato atualizado alterando o seu endereço de email sempre que necessário.
                              </div>
                            </div>
                            <div class="form-container">
                              <div class="input-group" style="display:flex; flex-direction: row;">
                                <div>
                                  <label for="email" class="email">Endereço de email atual*</label>
                                  <br>
                                  <input type="email" id="old_email" v-model=" email.Old">
                                </div>
                              </div>
                              <div class="input-group">
                                <label for="emailNew" class="email">Novo endereço de email*</label>
                                <br>
                                <input type="email" id="email" v-model="email.New">
                              </div>
                              <button @click.prevent="saveMailConfirmation()" class="save-button">Guardar</button>

                              <transition name="fade" appear style="margin:15px 0px;">
                                <p v-if="showEmailConfirmationMessage" class="confirmation-message" style="width:300px">
                                  Tem a certeza que quer alterar o email?
                                  <br>
                                  <button type="submit" class="save-button" style="margin-top:2%;">
                                    Sim
                                  </button>
                                  <button class="save-button" @click.prevent="saveMailConfirmation()" style="margin-top:2%;margin-left:20px">
                                    Não
                                  </button>
                                </p>
                              </transition>

                            </div>
                              <div class="success-message" v-if="perfilAtualizado2">
                              A atualizar endereço de email...
                              </div>
                              <div class="success-message" v-if="erro2">
                              {{  erro2Message.message }}
                            </div>  
                            </form>
                        </div>


                        <div class="right-division">
                          <form @submit.prevent="submitForm3">
                          <div class="personal-info">
                            <div class="info-header">
                              Password
                            </div>
                            <hr class="small-divider">
                            <div class="info-description">
                              Proteja a sua conta! Mantenha a sua senha segura e atualizada alterando-a regularmente para garantir a segurança dos seus dados
                            </div>
                          </div>
                          <div class="form-container">
                            <div class="input-group" style="display:flex; flex-direction: row;">
                              <div>
                                <label for="password" class="password">Password atual*</label>
                                <br>
                                <input type="password" id="password" v-model="password.Old">
                              </div>
                            </div>
                            <div class="input-group">
                              <label for="emailNew" class="email">Nova password*</label>
                              <br>
                              <input type="password" id="new_password" v-model="password.New">
                            </div>
                            <button @click.prevent="savePasswordConfirmation()" class="save-button">Guardar</button>
                            <transition name="fade" appear style="margin:15px 0px;">
                                <p v-if="showPasswordConfirmationMessage" class="confirmation-message" style="width:300px">
                                  Tem a certeza que quer alterar a password?
                                  <br>
                                  <button type="submit" class="save-button" style="margin-top:2%;">
                                    Sim
                                  </button>
                                  <button class="save-button" @click.prevent="savePasswordConfirmation()" style="margin-top:2%;margin-left:20px">
                                    Não
                                  </button>
                                </p>
                              </transition>
                            <div class="success-message" v-if="perfilAtualizado3">
                            A atualizar password...
                            </div>  
                            <div class="success-message" v-if="erro3">
                              {{  erro3Message.message }}
                            </div>  
                          </div>
                          </form>

                      </div>

                </div>

          </div>







      </div>








    </div>






    <div style="width: 100%; height: auto; background-color: white; padding-bottom: 10%;" class="mobile">
      
      <div class="single-title">
        <p>Para Agendar ou Cancelar Agendamentos, clique no botão abaixo.</p>
        <a href="/perfil/marcacoes"><button style="cursor: pointer;">VER MARCAÇÕES</button></a>
      </div>

      <div class="profile-section-left" style="padding:10% 0%">
          <div class="item-container">

            <div class="item bold">
              Editar Perfil
            </div>
              <hr class="divider">
            <div class="item">
              <a href="/perfil/marcacoes" style="color:Black">Marcações</a>
            </div>
              <hr class="divider">
            <div class="item">
              <a href="/perfil/recompensa" style="color:Black">Recompensa</a>
            </div>
            <hr class="divider">
          </div>

        </div>
      <div>
        <div style="text-align:center;padding:5%">
            <div class="personal-info">
              <div class="info-header">
                Informações pessoais
              </div>
              <hr class="small-divider" style="margin:auto">
              <div class="info-description" style="margin-top:5%">
                Personalize o seu perfil facilmente! Atualize as suas informações pessoais de forma rápida e simples para garantir que sua conta esteja sempre atualizada.
              </div>
            </div>
            
            <div>
              <form @submit.prevent="submitForm1">
              <div class="input-group" style="text-align:left;">
                <div style="margin:5% 0%">
                  <label for="nome">Nome</label>
                  <br>
                  <input type="text" id="nome" v-model="utilizador.Nome" style="text-indent: 10px; color:grey">
                </div>
                <div style="margin:5% 0%">
                  <label for="apelido">Apelido</label>
                  <br>
                  <input type="text" id="apelido" v-model="utilizador.Apelido" style="text-indent: 10px; color:grey">
                </div>
              </div>
              <div class="input-group" style="text-align:left;">
                <label for="username">Username</label>
                <br>
                <input type="text" id="username" name="username" v-model="utilizador.Username" style="text-indent: 10px; color:grey">
              <button class="save-button" @click.prevent="saveConfirmation()">Guardar</button>
              <transition name="fade" appear style="margin:15px 0px;">
                <p v-if="showConfirmationMessage" class="confirmation-message">
                  Tem a certeza que quer editar o perfil?
                  <br>
                  <button type="submit" class="save-button" style="margin-top:2%;">
                    Sim
                  </button>
                  <button class="save-button" @click.prevent="saveConfirmation()" style="margin-top:2%;margin-left:20px">
                    Não
                  </button>
                </p>
              </transition>
            </div>
              <div class="success-message" v-if="perfilAtualizado1">
                A atualizar perfil...
              </div>  
                            <div class="success-message" v-if="erro1">
                              {{  erro1Message.message }}
                            </div>  
            </form>


            </div>

        </div>


        </div>
            <hr style="border: 1px solid #0000002d;margin-top: 5%; margin-bottom: 5%;">

            <div style="text-align:center;padding:5%">
                          <form @submit.prevent="submitForm2">
                            <div class="personal-info">
                              <div class="info-header">
                                Email
                              </div>
                              <hr class="small-divider" style="margin:auto">
                              <div class="info-description" style="margin-top:5%">
                                Gerencie o seu email com facilidade! Mantenha o seu contato atualizado alterando o seu endereço de email sempre que necessário.
                              </div>
                            </div>
                            <div>
                              <div class="input-group" style="text-align:left;">
                                <div>
                                  <label for="email" class="email">Endereço de email atual*</label>
                                  <br>
                                  <input type="email" id="old_email" v-model=" email.Old">
                                </div>
                              </div>
                              <div class="input-group" style="text-align:left;">
                                <label for="emailNew" class="email">Novo endereço de email*</label>
                                <br>
                                <input type="email" id="email" v-model="email.New">
                              <button @click.prevent="saveMailConfirmation()" class="save-button">Guardar</button>

                              <transition name="fade" appear style="margin:15px 0px;">
                                <p v-if="showEmailConfirmationMessage" class="confirmation-message" style="width:300px">
                                  Tem a certeza que quer alterar o email?
                                  <br>
                                  <button type="submit" class="save-button" style="margin-top:2%;">
                                    Sim
                                  </button>
                                  <button class="save-button" @click.prevent="saveMailConfirmation()" style="margin-top:2%;margin-left:20px">
                                    Não
                                  </button>
                                </p>
                              </transition>
                            </div>

                            </div>
                              <div class="success-message" v-if="perfilAtualizado2">
                              A atualizar endereço de email...
                              </div>
                              <div class="success-message" v-if="erro2">
                              {{  erro2Message.message }}
                            </div>  
                            </form>
                        </div>

                        <div style="text-align:center;padding:5%">
                          <form @submit.prevent="submitForm3">
                          <div class="personal-info">
                            <div class="info-header">
                              Password
                            </div>
                            <hr class="small-divider" style="margin:auto">
                            <div class="info-description" style="margin-top:5%">
                              Proteja a sua conta! Mantenha a sua senha segura e atualizada alterando-a regularmente para garantir a segurança dos seus dados
                            </div>
                          </div>
                          <div class="form-container">
                            <div class="input-group" style="text-align:left;">
                              <div>
                                <label for="password" class="password">Password atual*</label>
                                <br>
                                <input type="password" id="password" v-model="password.Old">
                              </div>
                            </div>
                            <div class="input-group" style="text-align:left;">
                              <label for="emailNew" class="email">Nova password*</label>
                              <br>
                              <input type="password" id="new_password" v-model="password.New">
                            <button @click.prevent="savePasswordConfirmation()" class="save-button">Guardar</button>
                            <transition name="fade" appear style="margin:15px 0px;">
                                <p v-if="showPasswordConfirmationMessage" class="confirmation-message" style="width:300px">
                                  Tem a certeza que quer alterar a password?
                                  <br>
                                  <button type="submit" class="save-button" style="margin-top:2%;">
                                    Sim
                                  </button>
                                  <button class="save-button" @click.prevent="savePasswordConfirmation()" style="margin-top:2%;margin-left:20px">
                                    Não
                                  </button>
                                </p>
                              </transition>
                            </div>
                            <div class="success-message" v-if="perfilAtualizado3">
                            A atualizar password...
                            </div>  
                            <div class="success-message" v-if="erro3">
                              {{  erro3Message.message }}
                            </div>  
                          </div>
                          </form>

                      </div>

          </div>






    
    <Footer />
    
      </template>
      
      <script>
      import Header from '../../components/Header.vue';
      import Footer from '../../components/Footer.vue';
      import {jwtDecode} from 'jwt-decode';

      export default {
        data() {
          return {
            showConfirmationMessage: false,
            showEmailConfirmationMessage: false,
            showPasswordConfirmationMessage: false,
            utilizador: [],
            email: [], 
            password: [],
            alertStatus: false,
            alertMessage: '',
            perfilAtualizado2: false,
            perfilAtualizado3: false,
            erro1: false,
            erro1Message: '',
            erro2: false,
            erro2Message: '',
            erro3: false,
            erro3Message: '',
            };
        },
        methods: {
          saveConfirmation() {
            this.showConfirmationMessage = !this.showConfirmationMessage;
          },
          saveMailConfirmation() {
            this.showEmailConfirmationMessage = !this.showEmailConfirmationMessage;
          },
          savePasswordConfirmation() {
            this.showPasswordConfirmationMessage = !this.showPasswordConfirmationMessage;
          },
                async submitForm1() {
                  try {
                    const token = localStorage.getItem('token');

                    const decoded = jwtDecode(token);
                    const userId = decoded.userId;

                    if (!userId) {
                      console.error('UserId não encontrado na sessionStorage.');
                      return;
                    }
                    const url = `https://3700barbearia-api.vercel.app/perfil/editar/1/${userId}`;
                    const response = await fetch(url, {
                      method: 'PUT',
                      headers: {
                        'Content-Type': 'application/json'
                      },
                      body: JSON.stringify(this.utilizador),
                    });
                    if (response.ok) {
                      this.alertStatus = true;
                      this.alertMessage = 'Perfil atualizado com sucesso!'
                      setTimeout(() => {
                        this.perfilAtualizado1 = false;
                        window.location.reload();
                      }, 1500);
                     } else {
                      const responseData1 = await response.json(); 
                      this.erro1 = true;
                      this.erro1Message = responseData1;
                      console.error('Erro ao editar o perfil.');
                    }
                  } catch (error) {
                    console.error('Erro ao enviar o formulário:', error);
                  }
                },
                async submitForm2() {
                try {
                  const token = localStorage.getItem('token');

                  const decoded = jwtDecode(token);
                  const userId = decoded.userId;
                  if (!userId) {
                        console.error('UserId não encontrado na sessionStorage.');
                        return;
                    }
                    
                    const data = {
                        Old: this.email.Old,
                        New: this.email.New,
                        Id: userId
                    };

                    const url = `https://3700barbearia-api.vercel.app/perfil/editar/2/${userId}`;
                    const response = await fetch(url, {
                        method: 'PUT',
                        headers: {
                            'Content-Type': 'application/json'
                        },
                        body: JSON.stringify(data),
                    });
                    if (response.ok) {
                        this.erro2 = false;
                        this.alertStatus = true;
                        this.alertMessage = 'Email atualizado com sucesso!'
                        setTimeout(() => {
                            this.perfilAtualizado2 = false;
                            window.location.reload();
                        }, 1500);
                    } else {
                      const responseData2 = await response.json(); 
                      console.error('Erro ao editar o perfil.');
                      this.erro2 = true;
                      this.erro2Message = responseData2;
                    }
                } catch (error) {
                    console.error('Erro ao enviar o formulário:', error);
                }
            },
            async submitForm3() {
                try {
                  const token = localStorage.getItem('token');

                  const decoded = jwtDecode(token);
                  const userId = decoded.userId;

                  if (!userId) {
                        console.error('UserId não encontrado na sessionStorage.');
                        return;
                    }
                    
                    const data = {
                        Old: this.password.Old,
                        New: this.password.New,
                        Id: userId 
                    };

                    const url = `https://3700barbearia-api.vercel.app/perfil/editar/3/${userId}`;
                    const response = await fetch(url, {
                        method: 'PUT',
                        headers: {
                            'Content-Type': 'application/json'
                        },
                        body: JSON.stringify(data),
                    });

                    if (response.ok) {
                        this.erro3 = false;
                        this.alertStatus = true;
                        this.alertMessage = 'Password atualizada com sucesso!'
                        setTimeout(() => {
                            this.perfilAtualizado3 = false;
                            window.location.reload();
                        }, 1500);
                    } else {
                      const responseData3 = await response.json(); 
                      console.error('Erro ao editar o perfil.');
                      this.erro3 = true;
                      this.erro3Message = responseData3;
                    }
                } catch (error) {
                    console.error('Erro ao enviar o formulário:', error);
                }
            },

            async fetchUtilizador() {
              try {
                const token = localStorage.getItem('token');

                const decoded = jwtDecode(token);
                const userId = decoded.userId;

                  if (!userId) {
                      console.error('UserId não encontrado na sessionStorage.');
                      return;
                  }
                  const url = `https://3700barbearia-api.vercel.app/painel/utilizadores/${userId}`;
                  const response = await fetch(url);
                  const data = await response.json();

                  if (data && data.length > 0) {
                      const userData = data[0];

                      this.utilizador = {
                          Nome: userData.Nome ? userData.Nome : '',
                          Apelido: userData.Apelido ? userData.Apelido : '',
                          Username: userData.Username ? userData.Username : ''
                      };
                  } else {
                      this.utilizador = { Nome: '', Apelido: '', Username: '' };
                  }
              } catch (error) {
                  console.error('Erro ao buscar os dados dos serviços:', error);
              }
          },


        },
        mounted() {
          this.fetchUtilizador();    
        },
        components: {
          Header,
          Footer
        },
        name:'editarPerfil',
    
      }
      </script>

<style scoped>
.success-message {
  color: black;
  font-weight: bold;
  border-bottom:1px solid #F4B604;
  padding: 15px 20px;
  border-radius: 5px;
  margin-top: 20px;
  text-align: center;
  width:250px;
}
</style>