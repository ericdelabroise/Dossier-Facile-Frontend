<template>
  <div class="fr-container">
    <div class="fr-grid-row fr-grid-row--center">
      <div class="fr-col-md-8 fr-col-lg-6">
        <Login @on-login="onLogin" />
      </div>
      <div class="fr-col-12 text-center fr-mb-3w">
        <router-link to="/forgotten-password">{{
          $t("forgotten-password")
        }}</router-link>
      </div>
      <div class="fr-col-12 text-center fr-mb-12w">
        <router-link to="/signup">{{ $t("no-account") }}</router-link>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Login from "df-shared/src/Authentification/Login.vue";
import { User } from "df-shared/src/models/User";
import DfButton from "df-shared/src/Button/Button.vue";

@Component({
  components: {
    Login,
    DfButton
  }
})
export default class LoginPage extends Vue {
  onLogin(user: User) {
    if (user.email && user.password) {
      this.$store.dispatch("login", { user }).then(
        () => {
          if (this.$route.query.nextUrl !== undefined) {
            this.$router.push(this.$route.query.nextUrl.toString());
          } else {
            this.$router.push("/account");
          }
        },
        error => {
          if (error.response.status === 401) {
            this.$toasted.show(this.$i18n.t("password-error").toString(), {
              type: "error",
              duration: 7000
            });
          } else {
            this.$toasted.show(error.message, {
              type: "error",
              duration: 5000
            });
          }
        }
      );
    }
  }
}
</script>

<i18n>
{
  "en": {
    "password-error": "Incorrect username or password",
    "forgotten-password": "Forgotten password",
    "no-account": "I don't have an account yet",
    "try-again": "Try again",
    "old-version": "DossierFacile v1"
  },
  "fr": {
    "password-error": "Utilisateur ou mot de passe incorrect",
    "forgotten-password": "mot de passe oublié",
    "no-account": "je n'ai pas encore de compte",
    "try-again": "Réessayer",
    "old-version": "DossierFacile v1"
  }
}
</i18n>
