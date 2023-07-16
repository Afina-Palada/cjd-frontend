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

    function handleSearchDateInput(event) {
      searchDate = event.target.value;
    }

    let currentDate;

    onMount(() => {
        const today = new Date();
        const day = String(today.getDate()).padStart(2, '0');
        const month = String(today.getMonth() + 1).padStart(2, '0');
        const year = today.getFullYear();

        currentDate = `${day}.${month}.${year}`;
    });
  </script>

<style>
    marquee {
        font-family: 'Conthrax', sans-serif;
        font-size: 4em;
        color: white;
        padding-top: 2.5%;
        padding-bottom: 2.5%;
        text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    }

    .center-container {
        width: 70%;
        height: 20vh;
        margin-left: auto;
        margin-right: auto;
        text-align: center;
        background: #FFFFFF;
        border-radius: 20px;
        padding: 5%;
    }


    .city-input {
        width: 40%;
        height: 60%;

        background: #F1F1F1;
        border-radius: 20px;

        font-family: 'Acrom', sans-serif;
        font-size: 2em;
    }

    .arrows {
        display: inline-block;
    }

    .prognose {
        width: 30%;
        height: 10%;
        margin-left: auto;
        margin-right: auto;
        margin-top: 3%;
        background: #3B3B3B;
        border-radius: 20px;
        color: white;
        text-align: center;
        font-family: 'Acrom', sans-serif;
        font-size: 2em;
    }

    input::placeholder {
        text-align: center;
    }

    .prognose-container {
        margin-left: auto;
        margin-right: auto;
        text-align: center;
    }

    .search-select {
        margin-left: 4%;
    }
    
    @media screen and (max-width: 500px) {
        .center-container {
            width: 80%;
            padding: 5%;

            height: auto;
        }

        .arrows {
            display: block;
        }

        .city-input {
            width: 80%;
            height: 15%;

            background: #F1F1F1;
            border-radius: 20px;

            font-family: 'Acrom', sans-serif;
            font-size: 2em;
        }

        .prognose {
            width: auto;
            height: 15%;
            margin-left: auto;
            margin-right: auto;
            margin-top: 3%;
            background: #3B3B3B;
            border-radius: 20px;
            color: white;
            text-align: center;
            font-family: 'Acrom', sans-serif;
            font-size: 1.5em;
        }
    }
</style>

<!-- svelte-ignore a11y-distracting-elements -->
<marquee scrollamount="20">Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Afina AI</marquee>

<div class="center-container">
    <input class="city-input" placeholder="Откуда">
    <div class="arrows">
        <svg width="33" height="18" viewBox="0 0 33 18" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M2 9.53846H31M31 9.53846L23.75 16M31 9.53846L23.75 2" stroke="#ED3433" stroke-width="4" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
        <br>
        <svg width="34" height="19" viewBox="0 0 34 19" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M31.0311 9.07658L2.46031 9.5002M2.46031 9.5002L9.5077 2.96586M2.46031 9.5002L9.71422 16.8941" stroke="#ED3433" stroke-width="4" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
    </div>    
    <input class="city-input" placeholder="Куда">
    <br>
    <div class="search-field">
        <input class="city-input" placeholder="{currentDate}" disabled>
        <input class="search-select city-input" type="date" id="search-date" bind:value={searchDate} on:input={handleSearchDateInput}>
    </div>
</div>
<div type="text" class="prognose-container"><a href="/#/last"><button class="prognose">СПРОГНОЗИРОВАТЬ</button></a></div>