<template lang="pug">
  .App

    HeaderView

    .Columns
      Notes
      Tasks
      Calendar

</template>

<script>
  import 'quill/dist/quill.bubble.css'
  import Header from './components/global/header'
  import Notes from './components/note'
  import Tasks from './components/task'
  import Calendar from './components/calendar'

  export default {
    name: 'App',

    components: {
      HeaderView: Header,
      Notes,
      Tasks,
      Calendar
    }
  }
</script>

<style>
  :root {
    --border-radius: 5px;
    --transition: 130ms;
    --border-line-height: 1px;
    --border-line-color: rgba(0, 0, 0, .1);
    --color-note: #FFFBF2;
    --color-task: #21B663;
    --color-calander: #D9453D;
    --color-shadow: rgba(0, 0, 0, .1);
    --color-lighter: rgba(0, 0, 0, .2);
    --color-light: rgba(0, 0, 0, .5);
    --color-note-primary: #D3B41E;
    --font-size-normal: 16px;
    --font-size-small: 14px;
  }

  * {
    margin: 0;
    padding: 0;
    border: 0;
    outline: 0;

    &,
    &:before,
    &:after {
      box-sizing: inherit;
    }
  }

  html {
    box-sizing: border-box;
  }

  input,
  textarea,
  select,
  button {
    font: inherit;
  }

  table {
    border-spacing: 0;
    width: 100%;
  }

  svg {
    display: inline-block;
    vertical-align: middle;
  }

  button {
    cursor: pointer;
    background-color: transparent;
  }

  body {
    font-size: var(--font-size-normal);
    line-height: 1.4;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
    color: #232323;
    background-color: #E1E1E1;
    height: 100vh;
    overflow: hidden;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale
  }

  .btn {
    display: flex;
    align-items: center;
    padding-left: 12px;
    padding-right: 12px;
    padding-bottom: 1px; /* turkish charecter fix */
    height: 38px;
    line-height: 1;

    .icon {
      margin-right: 3px;
    }

    &.small {
      height: 30px;

      .icon {
        margin-right: 0;
      }
    }
  }

  .App {
    overflow: hidden;
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100vh;
    padding: 20px;
    display: flex;
    flex-direction: column;
  }

  .Columns {
    flex-grow: 1;
    display: flex;
    overflow: auto;
    margin-left: -20px;
  }

  .Column {
    flex: 1 0 calc(33.33% - 20px);
    margin-left: 20px;
    display: flex;
    flex-direction: column;
    overflow: auto;
    background-color: #FFF;
    box-shadow: 0 2px 4px 0 rgba(0, 0, 0, .1);
    border-radius: 10px;

    &-header {
      flex-shrink: 0;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 30px;

      .title {
        font-size: 25px;
        line-height: 1;
      }

      .new {
        transition: var(--transition);
        opacity: 0;
        border-radius: 20px;
        color: white;
        font-size: var(--font-size-small);
        text-decoration: none;

        .icon {
          margin-left: -4px;
          margin-right: 3px;
          width: 18px;
          height: 18px;
        }
      }
    }

    &-body {
      overflow: auto;
      flex-grow: 1;
      padding-bottom: 50px;
    }

    &:hover &-header .new {
      opacity: 1;
    }

    &-shadow {
      height: 100%;
      border: 4px dashed var(--color-shadow);
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 50px;

      .note {
        text-align: center;
        font-size: 18px;
        color: var(--color-lighter);
      }
    }
  }

  .empty-state {
    margin-left: 30px;
    margin-right: 30px;
    margin-bottom: 30px;
    padding: 20px;
    color: var(--color-light);
    border: 2px dashed var(--color-shadow);
    border-radius: var(--border-radius);
  }
</style>
