<template>
  <button class="q-button" :class="{[`icon-${iconPosition}`]:true}"
          @click="$emit('click')">
    <q-icon v-if="icon && !loading" :name="icon" class="icon"></q-icon>
    <q-icon v-if="loading" name="loading" class="icon loading"></q-icon>
    <div class="content">
      <slot></slot>
    </div>
  </button>
</template>
<script>
  export default {
    props: {
      icon: {},
      loading: {
        type: Boolean,
        default: false
      },
      iconPosition: {
        type: String,
        default: 'left',
        validator(value) {
          return value === 'left' || value === 'right'
        }
      }
    }
  }
</script>
<style lang="scss">
  @keyframes spin {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }

  .q-button {
    height: var(--button-height);
    font-size: var(--font-size);
    padding: 0 1em;
    border-radius: var(--border-radius);
    border: 1px solid var(--border-color);
    background: var(--button-bg);
    display: inline-flex;
    justify-content: center;
    align-items: center;
    vertical-align: middle;

    &:hover {
      border-color: var(--border-hover-color);
    }

    &:active {
      background-color: var(--button-active-bg);
    }

    &:focus {
      outline: none;
    }

    > .icon {
      order: 1;
      margin-right: .3em;
    }

    > .content {
      order: 2;
    }

    &.icon-right {
      > .icon {
        order: 2;
        margin-left: .3em;
        margin-right: 0;
      }

      > .content {
        order: 1;
      }
    }

    .loading {
      animation: spin 1.2s infinite linear;
    }
  }
</style>
