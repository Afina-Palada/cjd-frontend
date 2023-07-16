<script>
  import { Line } from 'svelte-chartjs';
  import { data } from './data.js';

  import {
    Chart as ChartJS,
    Title,
    Tooltip,
    Legend,
    LineElement,
    LinearScale,
    PointElement,
    CategoryScale,
  } from 'chart.js';

  ChartJS.register(
    Title,
    Tooltip,
    Legend,
    LineElement,
    LinearScale,
    PointElement,
    CategoryScale
  );
</script>

<style>
  .content {
    margin-left: 10%;
    margin-right: 10%;
  }

  .h-txt {
    margin-bottom: 0;
    padding-bottom: 0;

    color: black;
    font-family: 'Conthrax';
    font-style: normal;
    font-weight: 600;
    font-size: 3em;
    letter-spacing: 0.3px;
    line-height: 10vh;
    color: #FCFCFC;
    text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    text-align: start;
  }

  .h2-txt {
    margin-top: 0;
    padding-top: 0;


    width: 724px;
    height: auto;

    font-family: 'Acrom';
    font-style: normal;
    font-weight: 400;
    font-size: 35px;
    line-height: 42px;
    display: flex;
    align-items: center;

    color: #FFFFFF;
  }

  .city-input {
      width: 25%;
      height: 8vh;

      background: #F1F1F1;
      border-radius: 20px;

      font-family: 'Acrom', sans-serif;
      font-size: 2em;
  }

  .top-btns {
    text-align: center;
  }

  .graphic {
    text-align: center;
    background-color: white;
    border-radius: 20px;
  }
</style>
<div class="content">
<div>
  <h1 class="h-txt">Afina AI</h1>
  <p class="h2-txt">Рекомендации по направлению Краснодар-Адлер</p>
</div>

<div class="top-btns">
  <button class="city-input">Плацкарт</button>
  <button class="city-input">Купе</button>
  <button class="city-input">СВ</button>
</div>
<div class="graphic">
  <Line {data} options={{ responsive: true }} height="82vh"/>
</div>
</div>