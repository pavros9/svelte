<script context="module">
  export function formsChange() {
    let inputs = document.querySelectorAll(".form-change");

    inputs.forEach(function (element) {
      new FormChange(element);
      console.log(element);
    });
  }

  function FormChange(container) {
    let wrapper = container.querySelector(".form__wrapper");
    let inputs = container.querySelectorAll(".label__input");
    let buttonChange = container.querySelector(".button-change");
    let buttonSave = container.querySelector(".button-save");
    let buttonCancel = container.querySelector(".button-cancel");
    let buttonAdd = container.querySelector(".button-add");

    buttonChange.addEventListener("click", function (e) {
      e.preventDefault();
      console.log(buttonChange);
      changeStateInputs(container, inputs);
    });

    buttonSave.addEventListener("click", function (e) {
      e.preventDefault();
      console.log("Save");
      changeStateInputs(container, inputs);
    });

    buttonCancel.addEventListener("click", function (e) {
      e.preventDefault();
      console.log("Cancel");
      changeStateInputs(container, inputs);
    });

    buttonAdd.addEventListener("click", function (e) {
      e.preventDefault();
      console.log("Add");
    });
  }

  function changeStateInputs(form, inputs) {
    form.classList.toggle("active");
    if (form.classList.contains("active")) {
      for (let i = 0; i < inputs.length; i++) {
        inputs[i].removeAttribute("readonly");
      }
    } else {
      for (let i = 0; i < inputs.length; i++) {
        inputs[i].setAttribute("readonly", "readonly");
      }
    }
  }
</script>

<script>
  import { onDestroy } from "svelte";
  import { inputsDate } from "../store/store.js";

  let inputs = {};
  const unsubscribe = inputsDate.subscribe((value) => {
    inputs = value;
    console.log(inputs);
  });

  onDestroy(() => {
    unsubscribe();
  });
</script>

<form class="form form-change">
  <div class="form__wrapper">
    <label class="label">
      <span class="label__text">Имя</span>
      <input class="label__input" value={inputs.name} readonly />
    </label>

    <label class="label">
      <span class="label__text ">Телефон</span>
      <input class="label__input immutable" value={inputs.number} readonly />
    </label>

    <label class="label">
      <span class="label__text">Email</span>
      <input class="label__input" value={inputs.email} readonly />
    </label>

    <div class="form__buttons">
      <button class="button-change">Изменить</button>
      <button class="button-save">Сохранить</button>
      <button class="button-cancel">Отмена </button>
    </div>

    <div class="form__add-data">
      <input type="text" />
      <button class="button-add">Добавить данные</button>
    </div>
  </div>
</form>

<style lang="scss">
  .form {
    padding-top: 50px;
    font-size: 28px;
    &__wrapper {
      max-width: 500px;
      margin: auto;
      .label:last-of-type {
        margin-bottom: 50px;
      }
    }
    &__buttons {
      .button-cancel,
      .button-save {
        display: none;
      }
    }
    &.active {
      .form__buttons {
        .button-cancel,
        .button-save {
          display: inline;
        }
        .button-change {
          display: none;
        }
      }
    }
  }

  .label {
    display: flex;
    justify-content: space-between;
    align-items: center;
    &__text {
      margin-right: 15px;
      font-size: 34px;
      font-weight: 600;
    }
    &__input[readonly] {
      border: none;
      background: none;
      padding-bottom: 0;
      outline: none;
      &:focus {
        outline: 0;
      }
    }
    &__input {
      border: none;
      padding-bottom: 0;
      outline: 1px solid black;
    }
  }

  .button-change {
    background-color: #caffff;
    border-radius: 10px;
    padding: 5px 40px;
    font-size: 34px;
    transition: background-color 0.4s, color 0.4s;
    cursor: pointer;
    &:hover {
      background-color: #7df3f3;
      color: white;
    }
    &:focus {
      border-color: #ccc;
    }
  }
  .button-cancel {
  }
</style>
