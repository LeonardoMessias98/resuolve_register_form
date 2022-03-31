<template>
  <div class="container">
    <div class="content">
      <div class="header">
        <router-link to="/" replace>
          <button>Voltar</button>
        </router-link >
        <h1>Lista de cadastro</h1>
      </div>

      <div class="form">
        <section class="form-head">
          <span>ID</span>
          <span>EMAIL</span>
          <span>NOME</span>
          <span>TELEFONE/CELULAR</span>
        </section>

        <ul>
          <li v-for="user, index in users" :key="user.email">
            <span>{{ ("000" + (index + 1)).slice(-4) }}</span>
            <span>{{ user.email }}</span>
            <span>{{ user.name }}</span>
            <span>{{ user.phone }}</span>
          </li>
        </ul>
      </div>

    </div>
  </div>
</template>

<script>
  const users = JSON.parse(localStorage.getItem('#res_users'))

  console.log(users)

  export default {
    data() {
      return {
        users
      }
    },
    methods: {
     
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

  .content .header {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-column-gap: 20px;

    width: 100%;
    max-width: 1200px;
    margin: 1.5rem 0;
  }

  .content .header h1 { 
    font-family: 'Inter';
    font-style: normal;
    font-weight: 500;
    font-size: 32px;
    line-height: 39px;
    margin: 0;

    text-align: center;

    color: #000000;
  }

  .content .header button {
    background: #849FBF;
    box-shadow: 2px 4px 8px rgba(132, 159, 191, 0.4);
    border-radius: 8px;

    width: max-content;
    height: max-content;
    padding: 0.75rem 3rem;
    border: none;

    font-family: 'Inter';
    font-style: normal;
    font-weight: 600;
    font-size: 18px;
    line-height: 22px;

    color: #FFFFFF;
  }

  .content .form {
    height: 100%;
    max-height: 588px;

    width: 100%;
    max-width:1200px;

    background: #D4DCEB;
    border: 2px solid #3D6999;
    border-radius: 8px;
  }

  .content .form .form-head {
    display: grid;
    grid-template-columns: 80px 1fr 1fr 1fr;

    width: 100%;
    height: max-content;
    padding: 1rem 1.5rem;

    background: #3D6999;
    border-radius: 8px 8px 0px 0px;
  }

  .content .form .form-head span {
    font-family: 'Inter';
    font-style: normal;
    font-weight: 600;
    font-size: 18px;
    line-height: 22px;
    display: flex;
    align-items: center;

    color: #FFFFFF;
  }

  .content .form ul {
    list-style: none;
    padding: 0 1.5rem;
  }

  .content .form ul li {
    display: grid;
    grid-template-columns: 80px 1fr 1fr 1fr;
  }

  .content .form ul li span {
    font-family: 'Inter';
    font-style: normal;
    font-weight: 400;
    font-size: 16px;
    line-height: 19px;
    display: flex;
    align-items: center;

    color: #423D51;
  }
</style>
