<script>
  import Icon from "./Icon.svelte";

  document.addEventListener("DOMContentLoaded", function () {
    // const headerBurger = document.querySelector(".header__burger");
    // const headerWrapperBurger = document.querySelector(".header__wrapper-burger");
    // const headerNavigation = document.querySelector(".header__navigation");
    // headerWrapperBurger.onclick = function () {
    //     headerNavigation.classList.toggle("header__navigation_open");
    //     headerBurger.classList.toggle("header__burger_active");
    //     document.body.classList.toggle("body_lock");
    // };
  });
  var active = false;
</script>

<header>
  <header class="header">
    <div class="header__container">
      <div class="header__body">
        <div class="header__left">
          <a class="header__logo link" href="/">
            <Icon text="Кайли" name="logo" />
          </a>
          <nav class="header__navigation" class:header__navigation_open={active} on:click={() => (active = !active)}>
            <ul class="header__nav-list navigation__list">
              <li class="header__nav-item navigation__item">
                <a class="header__nav-link navigation__link link" href="#">Новостройки</a>
              </li>
              <li class="header__nav-item navigation__item">
                <a class="header__nav-link navigation__link link" href="#">Акции</a>
              </li>
              <li class="header__nav-item navigation__item">
                <a class="header__nav-link navigation__link link" href="#">Застройщики</a>
              </li>
              <li class="header__nav-item navigation__item">
                <a class="header__nav-link navigation__link link" href="#">Ипотека</a>
              </li>
              <li class="header__nav-item navigation__item">
                <a class="header__nav-link navigation__link link" href="#">Журнал</a>
              </li>
              <li class="header__nav-item navigation__item">
                <a class="header__nav-link navigation__link link header__dots dots" href="#">
                  <div class="dots__wrapper"><span /></div>
                </a>
              </li>
            </ul>
          </nav>
        </div>
        <div class="header__right">
          <div class="header__like" />
          <a class="header__login link" href="/">Link</a>
          <div class="header__wrapper-burger" class:header__wrapper-burger_active={active} on:click={() => (active = !active)}>
            <div class="header__burger"><span /></div>
          </div>
        </div>
      </div>
    </div>
  </header>
</header>

<style lang="scss">
  .header {
    position: fixed;
    width: 100%;
    border-bottom: 1px solid black;
    top: 0;
    left: 0;
    z-index: 2;
    &::before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: white;
      z-index: 2;
    }
    &__container {
      max-width: 1128px;
      padding: 0 20px;
      margin: auto;
    }
    &__body {
      display: flex;
      align-items: center;
      justify-content: space-between;
      min-height: 65px;
      position: relative;
    }

    &__left {
      display: flex;
      align-items: center;
    }
    @media (max-width: 767px) {
      &__navigation {
        position: fixed;
        top: -100%;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: #6bbb6b;
        transition: top 0.4s;
        text-align: center;
        &_open {
          top: 0;
          overflow: auto;
        }
      }
    }

    &__right {
      display: flex;
      @media (min-width: 768px) {
        z-index: 2;
        position: relative;
      }
    }
    &__logo {
      display: flex;
      align-items: center;
      margin-right: 32px;
      position: relative;
      z-index: 3;
      font-weight: 600;
      font-size: 28px;
    }
    &__wrapper-burger {
      padding: 15px;
      cursor: pointer;
      position: relative;
      z-index: 3;
      @media (max-width: 767px) {
        &_active {
          .header__burger {
            &::before {
              transform: rotate(45deg);
              top: 7px;
            }
            &::after {
              transform: rotate(-45deg);
              bottom: 7px;
            }
            & span {
              transform: scale(0);
            }
          }
        }
      }

      @media (min-width: 768px) {
        display: none;
      }
    }
    &__burger {
      @media (min-width: 768px) {
        margin-bottom: 10px;
        margin-left: auto;
        margin-right: auto;
      }
    }
    @media (max-width: 767px) {
      &__burger {
        display: block;
        position: relative;
        width: 21px;
        height: 16.5px;
        &::before,
        &::after {
          content: "";
          background-color: black;
          position: absolute;
          width: 100%;
          height: 2.5px;
          left: 0;
        }
        &::before {
          top: 0;
          transition: all 0.4s ease 0s;
        }
        &::after {
          bottom: 0;
          transition: all 0.4s ease 0s;
        }
        span {
          content: "";
          background-color: black;
          position: absolute;
          width: 100%;
          height: 2.5px;
          left: 0;
          top: 7px;
          transition: all 0.4s ease 0s;
        }
      }
    }
    &__nav-list {
      @media (max-width: 767.99px) {
        font-size: 20px;
        padding-top: 100px;
        padding-left: 30px;
        display: block;
      }
      @media (min-width: 768px) {
        display: flex;
        z-index: 2;
        position: relative;
        padding-left: 0;
      }
    }
    &__nav-item {
      margin-right: 10px;
      justify-content: center;
      @media (max-width: 767px) {
        margin-bottom: 10px;
        .dots__wrapper {
          &:before,
          &::after,
          span {
            transition: background-color 0.4s;
            background-color: white;
          }
        }
        & .dots__wrapper {
          &:hover {
            &:before,
            &::after,
            span {
              background-color: black;
            }
          }
        }
        &:last-child {
          margin-bottom: 0;
        }
      }
      &:last-child {
        margin-right: 0;
        display: flex;
        align-items: center;
      }
    }
    &__dots {
    }
    &__nav-link {
      @media (max-width: 767px) {
        &.link {
          color: white;
          transition: color 0.4s;
          &:hover {
            color: rgb(0, 0, 0);
          }
        }
      }
    }
    &__like {
      display: flex;
      align-items: center;
      margin-right: 10px;
    }
    &__login {
      display: none;
      @media (min-width: 767px) {
        display: flex;
        align-items: center;
      }
    }
  }
  .navigation {
    &__list {
      list-style-type: none;
      margin: 0;
    }
  }
  .dots {
    span {
      margin: 0 2px;
    }
    &__wrapper {
      display: flex;
      padding: 5px;
      &::before,
      &:after,
      span {
        content: "";
        width: 4px;
        height: 4px;
        border-radius: 50%;
        background-color: black;
        display: block;
        transition: background-color 0.4s;
      }
      &:hover {
        &:before,
        &::after,
        span {
          background-color: green;
        }
      }
    }
  }
</style>
