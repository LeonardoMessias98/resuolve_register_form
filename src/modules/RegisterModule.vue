<template>
  <div class="container">
    <div class="content">
      <img src="../shared/assets/logo.svg" />

      <form  @submit="onSubmit" @submit.prevent action="/">
        <label>Nome completo:</label>
        <input type="text" v-model="user.name" placeholder="Digite seu nome completo...">
        <label>Email:</label>
        <input type="text" v-model="user.email" placeholder="Informe seu email...">
        <label>Crie sua senha:</label>
        <input type="text" v-model="user.password" placeholder="Informe sua senha...">
        <label>Telefone / Celular:</label>
        <input type="text" v-model="user.phone" placeholder="(12) 99999-9999">
        <button>Cadastrar</button>
        <a href="/list">
        <button>Ver registros</button>
        </a>
      </form>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        user: {
          name: "",
          email: "",
          password: "",
          phone: "",
        }
      }
    },
    methods: {
      cleanForm() {
        this.user.name = ''
        this.user.email = ''
        this.user.password = ''
        this.user.phone = ''
      },
      storeUser({ currents, user }) {
        if (currents) {
          const newUsers = [...currents, user];

          localStorage.setItem('#res_users', JSON.stringify(newUsers))
          return;
        }

        localStorage.setItem('#res_users', JSON.stringify([user]))
      },
      onSubmit(e) {
        e.preventDefault();

        const user = {
          name: this.user.name,
          email: this.user.email,
          password: this.user.password,
          phone: this.user.phone,
        }

        const users = JSON.parse(localStorage.getItem('#res_users'))

        if(!user.name || !user.email || !user.password || !user.phone) {
          alert('Verifique se todos os campos estão preenchidos')
          return
        }

        this.cleanForm();
        this.storeUser({currents: users, user});
      }
    }
  }
</script>

<style scoped>
  .container {
    display: flex;
    justify-content: center;

    width: 100vw;
    min-height: 100vh;
    height: 100%;

    border: 1px solid red;
    padding: 107px 30px 30px;
  }

  .content {
    display: flex;
    flex-direction: column;
    align-items: center;

    width: 100%;
  }

  .content img {
    width: 451px;
    height: 166px;
  }

  .content form {
    display: flex;
    flex-direction: column;

    width: 100%;
    max-width: 600px;
    margin-top: 30px;
  }

  .content form label {
    font-family: 'Inter';
    font-style: normal;
    font-weight: 600;
    font-size: 18px;
    line-height: 22px;

    color: #130C25;
  }

  .content form input {
    background: rgba(206, 207, 208, 0.2);
    border: 1px solid #3D6999;
    box-sizing: border-box;
    box-shadow: 2px 4px 8px rgba(132, 159, 191, 0.4);
    border-radius: 8px;

    padding: 16px;
    margin: 8px 0 30px;
  }

  .content form button {
    font-family: 'Inter';
    font-style: normal;
    font-weight: 600;
    font-size: 18px;
    line-height: 22px;

    color: #FFFFFF;
    background: #3D6999;

    box-shadow: 2px 4px 8px rgba(132, 159, 191, 0.4);
    border-radius: 8px;
    padding: 14px;

    width: 100%;
    max-width: 300px;
    align-self: center;
    border: none;
  }
</style>
