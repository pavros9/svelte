<script>
  export let button = "";
  export let text = "";
  export let colorBack = "";
  export let withCounter = "";
  export let noBordered = "";
  export let forSlider = "";
  export let size = "";
  export let href = "/";
  export let link;

  var classes = "";

  classes += colorBack ? " button_" + colorBack : "";
  classes += withCounter ? " button_" + withCounter : "";
  classes += noBordered ? " button_" + noBordered : "";
  classes += forSlider ? " button_" + forSlider : "";
  classes += size ? " button_" + size : "";
</script>

{#if link}
  <a class="button {classes}" {href}>
    <span class="button__text">{text} </span>
  </a>
{/if}

{#if button}
  <button class="button {classes}">
    <span class="button__text">{text}</span>
  </button>
{/if}

<style lang="scss">
  @import "../scss/const.scss";

  .button {
    border-radius: 4px;
    background-color: transparent;
    border: 1px solid $dark;
    text-decoration: none;
    font-size: 14px;
    cursor: pointer;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    padding: 5px 10px;
    max-height: 32px;
    box-sizing: border-box;
    color: $dark;
    transition-duration: 0.4s;
    transition-property: color, border;
    &:hover {
      border: 1px solid $green;
      color: $green;
    }
    &_no-bordered {
      &:hover {
        border: none;
        color: $green;
      }
      border: none;
    }
    &_green {
      background-color: $green;
      transition: background-color 0.4s;
      &:hover {
        background-color: rgb(40, 211, 126);
      }
    }
    &_white {
      background-color: white;
    }
    &_white-opacity {
      background-color: rgba(255, 255, 255, 0.24);
    }
    &_ocher {
      background-color: #efd678;
    }
    &_with-counter {
      min-height: 54px;
      .button__text {
        margin-right: 4px;
        color: white;
      }
    }
    &_for-slider {
      width: 32px;
      height: 32px;
      border-radius: 50%;
      background-color: white;
      .logo {
        width: 10px;
        height: 15px;
      }
    }
    &_with-ad {
      .button {
        color: white;
        padding: 4px 2px;
        &__text {
          margin-right: 2px;
        }
      }
    }
    &_big {
      min-width: 160px;
      min-height: 40px;
      font-size: 16px;
      font-weight: 500;
    }
    &_middle {
      padding: 12px 24px;
      min-height: 43px;
      font-style: 16px;
    }
    &__text {
      white-space: nowrap;
    }
  }
  .btn-next {
    .logo {
      transform: rotate(-0.25turn);
    }
  }
  .btn-prev {
    .logo {
      transform: rotate(0.25turn);
    }
  }

  .counter {
    width: 20px;
    height: 20px;
    border-radius: 4px;
    background-color: $counterColor;
    font-size: 10px;
    color: white;
    justify-content: center;
    display: flex;
    align-items: center;
  }
</style>
