<script>
    import Main from "./router/Home.svelte";
    import Login from "./router/Login.svelte";
    
    import Last from "./router/Last.svelte";

    import Router from 'svelte-spa-router';
    const routes = {
      '/': Main,
      '/login': Login,
      '/last': Last
    }
  
    let isModalOpen = false;
  
    function openModal() {
      isModalOpen = true;
    }
  
    function closeModal() {
      isModalOpen = false;
    }
  </script>
  
  <style>
    @media screen and (max-width: 500px) {
      .header a {
        display: block;
        text-align: left;
      }
    }
  
    /* Стиль заголовка с серым фоном и некоторыми отступами */
    .header {
      overflow: hidden;
      background-color: white;
      height: 10vh;
    }
  
    /* Стиль ссылок в шапке */
    .header a {
      float: left;
      color: black;
      text-align: center;
      padding: 12px;
      text-decoration: none;
      font-size: 18px;
      line-height: 25px;
      border-radius: 4px;
    }
  
    /* Изменение цвета фона при наведении курсора */
    .header a:hover {
      background-color: #ddd;
      color: black;
    }
  
    /* Переместите раздел ссылок вправо */
    .header-right {
      float: right;
      padding-right: 10vw;
    }
  
    .logo {
      height: 7vh;
    }
  
    /* Стили модального окна и оверлея */
    .modal-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.5);
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 9999;
    }
  
    .modal-content {
      width: 25%;
      background-color: #fff;
      padding-left: 40px;
      padding-right: 40px;
      padding-bottom: 40px;
      border-radius: 5px;
      font-family: 'Conthrax';
      text-align: center;
      display: flex;
      flex-direction: column; /* Новое свойство для расположения сверху вниз */
      align-items: center; /* Дополнительное свойство для выравнивания по центру */
    }
    
    @media screen and (max-width: 500px) {
    .modal-content {
      width: 100%;
    }
    }

    .modal-input {
      font-family: 'Acrom';
      background: #EEEEEE;
      border-radius: 14px;
      margin-bottom: 10px; /* Добавлено свойство для отступа между элементами */
      padding: 8px 16px; /* Изменено свойство для большей высоты */
      width: 100%; /* Добавлено свойство для заполнения ширины */
      box-sizing: border-box; /* Добавлено свойство для правильного учета padding и border */
    }
  
    .login-button {
        display: inline-block;
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center;
        background-color: #EE2E2D;
        border-radius: 14px;
        color: white;
        text-decoration: none;
        margin-top: 10px;
        width: 100%;
        height: 6vh;
    }
  
    @font-face {
      font-family: 'Conthrax';
      src: url('/fonts/conthrax-sb.ttf') format('truetype');
    }
  
    @font-face {
      font-family: 'Acrom';
      src: url('/fonts/Acrom-Regular.ttf') format('truetype');
    }

    .close-button {
        position: relative;
        align-self: flex-end;
        border: 0;
        margin-bottom: 0px;
        padding-bottom: 0px;
        background-color: white;
        align-content: end;
    }

    .profile-button {
        border: none;
        background-color: white;
    }
  </style>
  
  <main>
    <div class="header">
      <a href="/#"><img src="img/logo.png" alt="" class="logo"></a>
      <div class="header-right">
        <button on:click={openModal} class="profile-button"><img src="img/icon_man.png" alt="Reg_button" class='profile'/></button>
      </div>
    </div>
    <Router {routes}/>
  
    {#if isModalOpen}
    <div class="modal-overlay">
      <div class="modal-content">
        <button on:click={closeModal} class="close-button">
            <svg width="27" height="24" viewBox="0 0 27 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M3 3L24 21M3 21L24 3" stroke="#D4D4D4" stroke-width="5" stroke-linecap="round"/>
            </svg>
        </button>
        <h2>Войдите в профиль администратора</h2>
        <form>
          <input type="text" placeholder="Логин" class="modal-input">
          <input type="password" placeholder="Пароль" name="" id="" class="modal-input">
        </form>
        <a href="/#/login" on:click={closeModal} class="login-button">ВОЙТИ</a>
      </div>
    </div>
    {/if}
  </main>
  