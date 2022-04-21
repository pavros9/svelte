<script>
  import Icon from "./Icon.svelte";
  import Button from "./Button.svelte";

  export let bid;
  export let sum;
  export let term;
  export let payment;
  export let title;
  export let subtitle;
  export let numberLogo;
</script>

<div class="bank-info">
  <div class="bank-info__wrapper">
    <div class="bank-info__top">
      <div class="bank-info__main-info">
        <h3 class="bank-info__title">{title}</h3>
        <h4 class="bank-info__subtitle">{subtitle}</h4>
      </div>
      <div class="bank-info__logo">
        <Icon name="banks-logo--{numberLogo}" isLogo="yes" />
      </div>
    </div>
    <table class="bank-info__bottom">
      <tr class="bank-info__title-conditions">
        <th class="bank-info__item bank-info__title-bid">Ставка</th>
        <th class="bank-info__item bank-info__title-sum">Сумма</th>
        <th class="bank-info__item bank-info__title-payment">Платеж</th>
      </tr>
      <tr class="bank-info__conditions">
        <td class="bank-info__item bank-info__bid"> {bid}</td>
        <td class="bank-info__item bank-info__box">
          <div class="bank-info__sum">{sum}</div>
          <div class="bank-info__term">{term}</div>
        </td>
        <td class="bank-info__item bank-info__payment"> {payment}</td>
      </tr>
    </table>
    <div class="bank-info__button"><Button text="Подробнее" link colorBack="white" /></div>
  </div>
</div>

<style lang="scss">
  .bank-info {
    width: 100%;
    background-color: white;
    border-radius: 4px;
    &__wrapper {
      padding: 12px;
      @media (min-width: 768px) {
        display: flex;
      }
    }
    &__top {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 16px;
      @media (min-width: 768px) {
        margin-bottom: 0;
        flex: 0 0 35%;
        justify-content: start;
        overflow: hidden;
      }
    }
    &__main-info {
      white-space: nowrap;
      min-width: 210px;
      margin-right: 14px;
      @media (min-width: 768px) {
        order: 2;
        margin-right: 0;
        min-width: auto;
        overflow: hidden;
      }
    }
    &__logo {
      @media (min-width: 768px) {
        order: 1;
        margin-right: 12px;
      }
    }
    &__title {
      margin: 0;
      margin-bottom: 8px;
      overflow: hidden;
      text-overflow: ellipsis;
    }
    &__subtitle {
      margin: 0;
      font-weight: normal;
      text-align: left;
    }
    &__bottom {
      width: 100%;
      @media (min-width: 768px) {
        flex: 0 0 50%;
      }
    }
    &__button {
      display: none;
      @media (min-width: 768px) {
        display: flex;
        flex: 0 0 15%;
        justify-content: flex-end;
        align-items: center;
      }
    }
    &__title-conditions {
      text-align: left;
      color: grey;
      @media (min-width: 768px) {
        display: none;
      }
      .bank-info__item {
        font-weight: 400;
      }
    }
    &__conditions {
      @media (min-width: 768px) {
        align-items: flex-start;
        display: flex;
        width: 100%;
      }
      .bank-info__item {
        font-weight: 500;
        @media (min-width: 768px) {
          vertical-align: top;
          display: block;
          width: 100%;
        }
      }
    }
    &__title-bid {
    }
    &__bid {
      &::before {
        content: "от";
        margin-right: 3px;
        @media (min-width: 768px) {
          display: none;
        }
      }
      @media (min-width: 768px) {
        order: 2;
      }
    }
    &__sum {
      display: flex;
      &::before {
        content: "до";
        margin-right: 3px;
        @media (min-width: 768px) {
          display: none;
        }
      }
      &::after {
        content: "млн. ₽";
        display: block;
        padding-left: 3px;
        @media (min-width: 768px) {
          content: "000 000₽";
        }
      }
      @media (min-width: 768px) {
        order: 1;
        margin-bottom: 8px;
      }
    }
    &__payment {
      @media (min-width: 768px) {
        order: 3;
      }
    }
    &__term {
      display: none;
      text-align: left;
      @media (min-width: 768px) {
        display: block;
        font-size: 12px;
        color: grey;
      }
    }
  }
</style>
