<script>
  import Header from "./components/Header.svelte";
  import BankInfo from "./components/BankInfo.svelte";
  import Form from "./components/Form.svelte";
  import { formsChange } from "./components/Form.svelte";

  // Слушатели
  window.addEventListener("DOMContentLoaded", function () {
    formsChange();
  });
</script>

<main class="main">
  <Header />
  <!-- <section class="banks">
    <div class="banks__wrapper">
      <div class="banks__bank">
        <BankInfo title="Льготная ипотека на новостройка" numberLogo="logo_1" subtitle="Банк ДомРФ" bid="3,99%" sum="12" payment="9082₽" term="Срок кредита неизвестен" />
      </div>
      <div class="banks__bank">
        <BankInfo title="Семейная ипотека" numberLogo="logo_2" subtitle="Банк ДомРФ" bid="4,00" sum="11" payment="9082₽" term="Срок кредита неизвестен" />
      </div>
      <div class="banks__bank">
        <BankInfo title="Ипотека в Новостройке" numberLogo="logo_3" subtitle="Банк ДомРФ" bid="12,00" sum="11" payment="9082₽" term="Срок кредита неизвестен" />
      </div>
      <div class="banks__bank">
        <BankInfo title="Дальневосточная ипотека" numberLogo="logo_4" subtitle="Банк ДомРФ" bid="7,00" sum="11" payment="9082₽" term="Срок кредита неизвестен" />
      </div>
    </div>
  </section> -->

  <Form />
</main>

<style lang="scss">
  body {
    min-width: 320px;
  }
  .main {
    padding-top: 100px;
    height: 100%;
    background: #f7f8fc;
    &__p {
      color: red;
      font-size: 34px;
    }
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }
  .banks {
    &__wrapper {
      max-width: 1136px;
      margin: auto;
    }
    &__bank {
      margin-bottom: 10px;
      &:last-child {
        margin-bottom: 0;
      }
    }
  }
  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
