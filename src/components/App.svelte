<script>
  import { Alert } from "flowbite-svelte";
  import { APP_STATUS, appStatus } from "../store";
  import SetpUpload from "./SetpUpload.svelte";
  import SetpLoading from "./SetpLoading.svelte";
  import StepChat from "./StepChat.svelte";
</script>

{#if $appStatus === APP_STATUS.INIT}
  <SetpUpload />
{:else if $appStatus == APP_STATUS.LOADING}
  <SetpLoading />
{:else if $appStatus == APP_STATUS.ERROR}
  <Alert>
    <span class="font-medium">Algo malo ha pasado!</span>
    Hay un error en la app.
  </Alert>
{:else if $appStatus == APP_STATUS.CHAT_MODE}
  <StepChat />
{:else}
  <Alert>
    <span class="font-medium">Accion no reconocida</span>
    Este estado de la app no esta reconocido.
  </Alert>
{/if}
