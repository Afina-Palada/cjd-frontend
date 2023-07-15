<script>
    let searchFrom = '';
    let searchTo = '';
    let searchDate = '';
  
    let cities = ['Москва', 'Адлер', 'Ростов', 'Санкт-Петербург', 'Краснодар', 'Казань', 'Нижний Новгород', 'Воронеж', 'Екатеринбург', 'Новосибирск', 'Кемерово', 'Новороссийск', 'Владимир',];
    let searchResults = [];

    let showSearchFromResults = false;
    let filteredCities = [];

    let showSearchToResults = false;
    let filteredToCities = [];

    import { onMount } from 'svelte';

    function handleClickOutside(event) {
        const target = event.target;

        // Проверяем, был ли кликнут элемент вне списка результатов поиска
        if (!target.closest(".search-results-list") && !target.closest(".search-select")) {
        showSearchFromResults = false;
        showSearchToResults = false;
        }
    }

    onMount(() => {
        document.body.style.background = 'linear-gradient(180deg, #ED3433 41.54%, rgba(232, 83, 83, 0.28) 108.99%)';

        // Добавляем обработчик события click для всей страницы
        document.addEventListener("click", handleClickOutside);
    });
    
    function handleSearchToInput(event) {
        const searchText = event.target.value.toLowerCase();
        filteredToCities = cities.filter(city => city.toLowerCase().startsWith(searchText));
        showSearchToResults = true;
    }

    function handleSearchToSelect(city) {
        searchTo = city;
        showSearchToResults = false;
    }

    function handleSearchFromInput(event) {
        const searchText = event.target.value.toLowerCase();
        filteredCities = cities.filter(city => city.toLowerCase().startsWith(searchText));
        showSearchFromResults = true;
    }

    function handleSearchFromSelect(city) {
        searchFrom = city;
        showSearchFromResults = false;
    }
  
    function handleSearchDateInput(event) {
      searchDate = event.target.value;
    }
  </script>
<style>


  /* Добавьте стили, в которых используется шрифт Acrom */

    .search-container {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-left: 4%;
      margin-right: 4%;
      height: 20vh;
    }
  
    .search-field {
      flex: 1 1 100%;
      display: flex;
      align-items: center;
      margin-bottom: 10px;
    }
  
    .search-field label {
      margin-right: 5px;
    }
  
    .search-select,
    .search-date-input {
      flex: 1;
      padding: 5px;
      width: 100%;
    }
  
    .search-button {
      flex: 1 1 100%;
    }

  /*Кнопка*/

    .submit {
        border: 1px solid #3b3b3b;
        cursor: pointer;
        background-color: #3b3b3b;
        border-radius: 20px;
        border: 1px solid #000000;
        color: white;
        display: inline-block;
      flex: 1;
    padding: 5px;
    width: 100%;
    font-size: 1.1em;
    }

    button
    {
        font-family: 'Acrom', sans-serif;

    }

    .submit:hover {background-color: red}

    .submit:active {
    background-color: red;
    box-shadow: 0 5px #666;
    transform: translateY(4px);
    }

    .search-select
    {
        font-family: 'Acrom', sans-serif;
        border: 1px solid;
        cursor: pointer;
        border-radius: 20px;
        border-color: black;
        height: 12vh;
    }

    .search-date-input
    {
        font-family: 'Acrom', sans-serif;
    }
        .search-date-input
        {
            border: 1px solid ;
            cursor: pointer;
            border-radius: 20px;
            border: 1px solid;
        }

    @media (min-width: 768px) {
      .search-field {
        flex: 1 1 auto;
        margin-bottom: 0;
      }
  
      .search-button {
        flex: 0 0 auto;
      }
    }
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

    .search-results-list {
        position: relative;
        top: 100%;
        background-color: #fff;
        border: 1px solid #ccc;
        border-radius: 4px;
        width: 100%;
        max-height: 200px;
        overflow-y: auto;
        z-index: 1;
    }

    .search-field {
        display: inline-block;
        flex: 1;
        padding: 5px;
        width: 100%;
        font-size: 2em;
    }

    .search-results-list {
        position: absolute;
        top: 100%;
        right: 0;
        background-color: #fff;
        border: 1px solid #ccc;
        border-radius: 4px;
        width: 100%;
        max-height: 200px;
        overflow-y: auto;
        z-index: 1;
    }

    .logo {
        height: 7vh;
    }

    /*текст*/
    .centered-text {
        font-family: 'Conthrax', sans-serif;
        font-weight: 600;
        font-size: 2.5em;
        line-height: 80px;
        text-align: center;
        color: #fff;
        text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
        margin: 0%;
        margin-top: 5%;
    }

    .bot-text {
        font-family: 'Acrom', sans-serif;
        font-weight: 600;
        font-size: 1.15em;
        line-height: 50px;
        text-align: center;
        color: #fff;
        text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
        margin: 0px;
        margin-bottom: 10.5%;
    }

    input::placeholder {
        text-align: center;
    }
  </style>
  


  

<div class="wrapper">
    <div class="greeting">
        <p class="centered-text">Поиск дешевых жд билетов</p>
        <p class="bot-text">16 лет помогаем вам экономить</p>
    </div>

  <div class="search-container">
    <div class="search-field">
      <div class="search-input-container">
        <input type="text" id="search-from" placeholder="Откуда" bind:value={searchFrom} on:input={handleSearchFromInput} class="search-select">
        {#if showSearchFromResults && filteredCities.length > 0}
          <div class="search-results-list">
            {#each filteredCities as city}
              <!-- svelte-ignore a11y-click-events-have-key-events -->
              <div class="search-results-list-item" on:click={() => handleSearchFromSelect(city)}>
                {city}
              </div>
            {/each}
          </div>
        {/if}
      </div>
    </div>
    <div class="search-field">
        <div class="search-input-container">
            <input type="text" id="search-to" placeholder="Куда"  bind:value={searchTo} on:input={handleSearchToInput} class="search-select">
            {#if showSearchToResults && filteredToCities.length > 0}
            <div class="search-results-list">
                {#each filteredToCities as city}
                <!-- svelte-ignore a11y-click-events-have-key-events -->
                <div class="search-results-list-item" on:click={() => handleSearchToSelect(city)}>
                    {city}
                </div>
                {/each}
            </div>
            {/if}
        </div>
    </div>
    <div class="search-field">
      <input class="search-date-input search-select" type="date" id="search-date" bind:value={searchDate} on:input={handleSearchDateInput}>
    </div>

    <div class="search-field search-button">
      <button class="submit search-select" type="submit">поиск</button>
    </div>
  </div>
</div>