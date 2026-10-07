<template>
  <q-layout>
    <q-page-container>
      <q-page class="login-page flex flex-center">

        <q-card class="login-card">
          <q-card-section class="text-center q-pb-none">

            <q-avatar
              size="80px"
              color="primary"
              text-color="white"
              icon="description"
              class="q-mb-md"
            />

            <div class="text-h5 text-weight-bold">
              Gestión Documental
            </div>

            <div class="text-grey-7 q-mt-sm">
              Sistema de Gestión y Seguimiento de Documentos
            </div>

          </q-card-section>

          <q-card-section class="q-pa-lg">

            <q-form @submit.prevent="iniciarSesion" class="q-gutter-md">

              <q-input
                outlined
                v-model="usuario"
                label="Usuario"
                prepend-icon="person"
              >
                <template v-slot:prepend>
                  <q-icon name="person" />
                </template>
              </q-input>

              <q-input
                outlined
                v-model="password"
                :type="mostrarPassword ? 'text' : 'password'"
                label="Contraseña"
              >
                <template v-slot:prepend>
                  <q-icon name="lock" />
                </template>

                <template v-slot:append>
                  <q-icon
                    :name="mostrarPassword ? 'visibility_off' : 'visibility'"
                    class="cursor-pointer"
                    @click="mostrarPassword = !mostrarPassword"
                  />
                </template>
              </q-input>

              <q-btn
                label="INICIAR SESIÓN"
                type="submit"
                color="primary"
                class="full-width"
                size="md"
                unelevated
              />

            </q-form>

          </q-card-section>

          <q-card-section class="text-center q-pt-none">
            <div class="text-caption text-grey-6">
              Control de documentos, vigencias y vencimientos
            </div>
          </q-card-section>

        </q-card>

      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import { useRouter } from 'vue-router'

export default defineComponent({
  name: 'LoginPage',

  setup () {
    const router = useRouter()

    const usuario = ref('')
    const password = ref('')
    const mostrarPassword = ref(false)

    const iniciarSesion = () => {
      router.push('/dashboard')
    }

    return {
      usuario,
      password,
      mostrarPassword,
      iniciarSesion
    }
  }
})
</script>

<style scoped>
.login-page {
  min-height: 100vh;
  background: linear-gradient(135deg, #0d47a1 0%, #1976d2 50%, #64b5f6 100%);
}

.login-card {
  width: 420px;
  max-width: 90%;
  padding: 20px;
  border-radius: 14px;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.20);
}
</style>