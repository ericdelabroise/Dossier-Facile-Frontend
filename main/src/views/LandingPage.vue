<template>
  <div>
    <section class="s0-background fr-pb-md-5w fr-pt-md-9w fr-pt-3w">
      <div class="fr-container">
        <div class="fr-col-md-8">
          <div class="fr-grid-col">
            <h1 :class="getH1Class()" class="fr-mt-3w color--white">
              {{ $t("s0.title") }}
            </h1>
            <p class="text-bold color--white">
              {{ $t("s0.text") }}<br />
              {{ $t("s0.text2") }}
            </p>
            <p>
            <DfButton
              primary="true"
              @on-click="gotoTenant"
            >
              {{ $t("button") }}
            </DfButton>
            </p>
          </div>
        </div>
      </div>
    </section>
    <section class="fr-pb-md-5w fr-pt-md-9w fr-pt-3w">
      <div class="fr-container">
        <div class="fr-grid-row">
          <div class="fr-col-md-4 fr-grid-col fr-p-2w">
            <div class="fr-tile fr-enlarge-link">
              <div class="fr-tile__body">
                <h2 class="fr-tile__title">
                  <div class="fr-tile__link" href="#">{{ $t("s1.h1") }}</div>
                </h2>
                <p class="fr-tile__desc">{{ $t("s1.p1") }}</p>
              </div>
              <div class="fr-tile__img">
                <img src="../assets/icons/approval.svg" class="fr-responsive-img" alt="">
              </div>
            </div>
          </div>
          <div class="fr-col-md-4 fr-grid-col fr-p-2w">
            <div class="fr-tile fr-enlarge-link">
              <div class="fr-tile__body">
                <h2 class="fr-tile__title">
                  <div class="fr-tile__link" href="#">{{ $t("s1.h2") }}</div>
                </h2>
                <p class="fr-tile__desc">{{ $t("s1.p2") }}</p>
              </div>
              <div class="fr-tile__img">
                <img src="../assets/icons/sports.svg" class="fr-responsive-img" alt="">
              </div>
            </div>
          </div>
          <div class="fr-col-md-4 fr-grid-col fr-p-2w">
            <div class="fr-tile fr-enlarge-link">
              <div class="fr-tile__body">
                <h2 class="fr-tile__title">
                  <div class="fr-tile__link" href="#">{{ $t("s1.h3") }}</div>
                </h2>
                <p class="fr-tile__desc">{{ $t("s1.p3") }}</p>
              </div>
              <div class="fr-tile__img">
                <img src="../assets/icons/reading.svg" class="fr-responsive-img" alt="">
              </div>
            </div>

          </div>
        </div>
      </div>
    </section>
    <section class="fr-pb-md-5w fr-pt-md-9w fr-pt-3w bg-blue-grey">
      <div class="fr-container">
        <h2 class="fr-h2 s2-title">{{ $t("s2.title") }}</h2>
        <div class="fr-grid-row reverse-mobile">
          <div class="fr-col-md-6 fr-grid-col">
            <div class="fr-grid-row align-items--center">
              <div class="step-number">1</div>
              <h2 class="fr-h4 fr-mb-0">{{ $t("s2.h1") }}</h2>
            </div>
            <p>{{ $t("s2.p1") }}
              <ul class="fr-pt-2w">
                <li>{{ $t("s2.u1a") }}</li>
                <li>{{ $t("s2.u1b") }}</li>
                <li>{{ $t("s2.u1c") }}</li>
                <li>{{ $t("s2.u1d") }}</li>
                <li>{{ $t("s2.u1e") }}</li>
              </ul>
            </p>

            <div class="fr-grid-row align-items--center">
              <div class="step-number">2</div>
              <h2 class="fr-h4 fr-mb-0">{{ $t("s2.h2") }}</h2>
            </div>
            <p>{{ $t("s2.p2") }}</p>

            <div class="fr-grid-row align-items--center">
              <div class="step-number">3</div>
              <h2 class="fr-h4 fr-mb-0">{{ $t("s2.h3") }}</h2>
            </div>
            <p>{{ $t("s2.p3") }}</p>
            <DfButton class="fr-mt-2w"
              @on-click="gotoDocs"
            >
              <span class="text-center full-width">
                {{ $t("docs") }}
              </span>
            </DfButton>
            <DfButton class="fr-mt-2w"
              primary="true"
              @on-click="gotoTenant"
            >
              <span class="text-center full-width">
                {{ $t("button") }}
              </span>
            </DfButton>
          </div>
          <div class="fr-col-md-6">
            <img src="../assets/icons/justif.webp" alt="" />
          </div>
        </div>
      </div>
    </section>
    <section class="bg--orange fr-pb-md-5w fr-pt-md-9w fr-pt-3w">
      <div class="fr-pt-7w fr-pb-7w">
        <div class="fr-container">
          <h2 class="fr-h2 s3-title">{{ $t("s3.title") }}</h2>
          <p>
            {{ $t("s3.text1") }}
            <br />
            {{ $t("s3.text2") }}
          </p>
          <p>
            {{ $t("s3.text3") }}
          </p>
          <!--           <router-link to="/tenant">
            {{ $t("s3.link") }}
          </router-link> -->
        </div>
      </div>
    </section>
    <section class="fr-pb-md-5w fr-pt-md-9w fr-pt-3w">
      <div class="fr-container fr-mb-7w">
        <h2 class="fr-h2 text-center">
          {{ $t("s4.title1") }}
          <span class="color--secondary">{{ $t("s4.title2") }}</span>
          {{ $t("s4.title3") }}
        </h2>
        <div class="text-center">
          <router-link to="/stats">
            <img src="../assets/icons/stats.webp" class="stats-icon" alt="" />
            {{ $t("s4.link") }}
          </router-link>
        </div>
        <div class="fr-grid-row">
          <div class="col fr-p-2w">
            <blockquote class="bg--blue color--primary quote fr-p-2w">
              <p class="fr-m-0 fr-mb-3w">{{ $t("s4.t1") }}</p>
              <cite>{{ $t("s4.author1") }}</cite>
            </blockquote>
          </div>
          <div class="col fr-p-2w">
            <blockquote class="bg--blue color--primary quote fr-p-2w">
              <p class="fr-m-0 fr-mb-3w">{{ $t("s4.t2") }}</p>
              <cite>{{ $t("s4.author2") }}</cite>
            </blockquote>
          </div>
          <div class="col fr-p-2w">
            <blockquote class="bg--blue color--primary quote fr-p-2w">
              <p class="fr-m-0 fr-mb-3w">{{ $t("s4.t3") }}</p>
              <cite>{{ $t("s4.author3") }}</cite>
            </blockquote>
          </div>
        </div>
        <div class="text-center fr-mt-5w fr-mb-5w">
          <p>
            <DfButton
              primary="true"
              @on-click="gotoTenant"
            >
              {{ $t("button") }}
            </DfButton>
          </p>
        </div>
      </div>
    </section>
    <section class="fr-pb-md-5w fr-pt-md-9w fr-pt-3w">
      <div class="fr-container fr-mb-7w">
        <h2 class="fr-h2 text-center">
          {{ $t("s5.title1") }}
          <span class="color--secondary">{{ $t("s5.title2") }}</span>
        </h2>
        <div class="fr-grid-row">
          <div
            class="fr-col-lg-3 fr-col-md-4 fr-col-sm-6 fr-col-12 text-center fr-p-2w logo-container"
          >
            <a
              target="_blank"
              href="https://www.monsieurhugo.com/"
              class="logo-link"
              rel="noreferrer"
            >
              <img
                alt="logo monsieur hugo"
                class="partner-logo"
                src="../assets/logos/monsieur_hugo.webp"
              />
            </a>
          </div>
          <div
            class="fr-col-lg-3 fr-col-md-4 fr-col-sm-6 fr-col-12 text-center fr-p-2w logo-container"
          >
            <a target="_blank" href="https://www.visale.fr/" class="logo-link"
              rel="noreferrer"
            >
              <img
                alt="logo visale"
                class="partner-logo"
                src="../assets/logos/visale.webp"
              />
            </a>
          </div>
          <div
            class="fr-col-lg-3 fr-col-md-4 fr-col-sm-6 fr-col-12 text-center fr-p-2w logo-container"
          >
            <a
              target="_blank"
              href="https://www.locservice.fr/"
              class="logo-link"
              rel="noreferrer"
            >
              <img
                alt="logo locservice"
                class="partner-logo"
                src="../assets/logos/loc_service.webp"
              />
            </a>
          </div>
          <div
            class="fr-col-lg-3 fr-col-md-4 fr-col-sm-6 fr-col-12 text-center fr-p-2w logo-container"
          >
            <a target="_blank" href="https://colivme.com/" class="logo-link"
              rel="noreferrer"
            >
              <img
                alt="logo colivme"
                class="partner-logo"
                src="../assets/logos/colivme.webp"
              />
            </a>
          </div>
          <div
            class="fr-col-lg-3 fr-col-md-4 fr-col-sm-6 fr-col-12 text-center fr-p-2w logo-container"
          >
            <a target="_blank" href="https://whoomies.com/" class="logo-link"
              rel="noreferrer"
            >
              <img
                alt="logo whoomies"
                class="partner-logo"
                src="../assets/logos/whoomies.webp"
              />
            </a>
          </div>
          <div
            class="fr-col-lg-3 fr-col-md-4 fr-col-sm-6 fr-col-12 text-center fr-p-2w logo-container"
          >
            <a target="_blank" href="https://www.anil.org/" class="logo-link"
              rel="noreferrer"
            >
              <img
                alt="logo anil"
                class="partner-logo"
                src="../assets/logos/anil.webp"
              />
            </a>
          </div>
          <div
            class="fr-col-lg-3 fr-col-md-4 fr-col-sm-6 fr-col-12 text-center fr-p-2w logo-container"
          >
            <a target="_blank" href="https://www.clickandrent.fr/" class="logo-link"
              rel="noreferrer"
            >
              <img
                alt="logo click and rent"
                class="partner-logo"
                src="../assets/logos/clickandrent.webp"
              />
            </a>
          </div>
        </div>
        <div class="text-center fr-mt-5w fr-mb-5w">
          <p>
            <DfButton
              primary="true"
              @on-click="gotoTenant"
            >
              {{ $t("button") }}
            </DfButton>
          </p>
        </div>
      </div>
    </section>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import DfButton from "df-shared/src/Button/Button.vue";

@Component(
  {
    components: {
      DfButton
    }
  }
)
export default class LandingPage extends Vue {
  TENANT_URL = `//${process.env.VUE_APP_TENANT_URL}`;
  DOCS_URL = `//${process.env.VUE_APP_DOCS_URL}`;

  getH1Class() {
    return window.innerWidth < 992 ? "fr-h2" : "fr-h1";
  }

  gotoTenant() {
    window.location.href = `${this.TENANT_URL}/signup?lang=${this.$i18n.locale}`;
  }

  gotoDocs() {
    window.open(`${this.DOCS_URL}`, "_blank");
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.s0-background {
  width: 100%;
  top: 0;
  left: 0;
  background-size: cover !important;
  background-position: 50% 50% !important;
  background-image: url("../assets/cover-features.webp");

  @media (max-width: 768px) {
    background-image: url("../assets/cover-features-mobile.webp");
  }

  z-index: 0;
}

.s1-icons {
  height: 48px;
}

cite {
  font-weight: bold;
}

.col {
  flex: 1;
  @media (max-width: 768px) {
    flex: auto;
  }
}

blockquote {
  margin: 0;
  height: 100%;
}

.quote {
  border-radius: 6px;
}

.s2-title {
  &:before {
    margin-right: 10px;
    content: url("../assets/icons/survey.svg");
  }
}

.s3-title {
  &:before {
    margin-right: 10px;
    content: url("../assets/icons/lock.svg");
  }
}

ul li {
  display: flex;
  margin-bottom: 0;
}

ul li:before {
  content: "";
  display: inline-block;
  color: limegreen;
  font-size: 1rem;
}

.step-number {
  background-color: var(--primary);
  color: white;
  margin-right: 10px;
  border-radius: 50%;
  display: inline-block;
  height: 25px;
  width: 25px;
  min-width: 25px;
  text-align: center;
  z-index: 1;
}

img {
  max-width: 100%;
  display: block;
}

.partner-logo {
  max-width: 100%;
  max-height: 60px;
  margin: auto;
}

a[target="_blank"].logo-link::after {
  content: none;
}

.stats-icon {
  display: inline;
  height: 3rem;
  vertical-align: -0.75rem;
}

.logo-container {
  display: flex;
  align-items: center;
  justify-content: center;
}

.bg-blue-grey {
  background-color: #f2f2f9;
}

.full-width {
  width: 100%;
}

.reverse-mobile {
  @media (max-width: 768px) {
    flex-direction: column-reverse;
  }
}
</style>

<i18n>
{
  "en": {
    "button": "Build my rental file",
    "docs": "How to prepare my rental file",
    "s0": {
      "title": "Build a concrete rental file to find the accommodation of your dreams",
      "text": "DossierFacile helps you build a high-quality digital rental",
      "text2": "file to ensure you have the best possible results."
    },
    "s1": {
      "h1": "Stand out thanks to a quality file",
      "p1": "Send owners a clear, complete and coherent file to maximize your chances.",
      "h2": "Be the first to respond to an ad",
      "p2": "Be the most responsive by sending your digital file with one click.",
      "h3": "Reassure your future owner",
      "p3": "After a battery of tests by our operators, your file is certified by the State."
    },
    "s2": {
      "title": "Build your rental file in three steps",
      "h1": "I upload my documents",
      "p1": "DossierFacile asks you for the necessary documents and just those!",
      "u1a": "Identity card",
      "u1b": "Proof of address",
      "u1c": "Proof of professional situation",
      "u1d": "Tax notice",
      "u1e": "Proof of resources",
      "h2": "DossierFacile validates my file",
      "p2": "Our agents check your file and help you correct it if necessary.",
      "h3": "My file is ready to be sent",
      "p3": "Your secure file as a URL link or in PDF format is ready to be sent to the owners."
    },
    "s3": {
      "title": "Protect your personal information",
      "text1": "With DossierFacile, no more identity papers scattered around the countryside!",
      "text2": "Your documents are covered with watermarks to protect you against fraud by unscrupulous owners.",
      "text3": "You can configure the opening of your folder link: you can delete it at any time!",
      "link": "Learn more about data security at DossierFacile"
    },
    "s4": {
      "title1": "Already",
      "title2": "65 000",
      "title3": "certified dossiers thanks to DossierFacile",
      "t1": "Karim's file immediately stood out: it was the only file received that was complete!",
      "author1": "Joseph, owner in Nantes",
      "t2": "Simple, efficient and practical: it saved me a lot of time in my apartment search.",
      "author2": "Caroline, student",
      "t3": "I never managed to visit an apartment with my foreign file. With DossierFacile, I finally had more visits!",
      "author3": "Irina, Erasmus student",
      "link": "Consult our statistics"
    },
    "s5": {
      "title1": "They",
      "title2": "trust us"
    }
  },
  "fr": {
    "button": "Monter mon dossier de location",
    "docs": "Comment préparer mon dossier de location",
    "s0": {
      "title": "Montez un dossier de location en béton pour trouver le logement de vos rêves",
      "text": "DossierFacile vous aide à constituer un dossier de location numérique ",
      "text2": "de qualité pour mettre toutes les chances de votre côté."
    },
    "s1": {
      "h1": "Démarquez-vous grâce à un dossier de qualité",
      "p1": "Transmettez aux propriétaires un dossier clair, complet et cohérent pour maximiser vos chances.",
      "h2": "Soyez le premier à répondre à une annonce",
      "p2": "Soyez le plus réactif en envoyant en un clic votre dossier numérique.",
      "h3": "Rassurez votre futur·e propriétaire",
      "p3": "Après une batterie de tests par nos opérateurs, votre dossier est labellisé par l'État."
    },
    "s2": {
      "title": "Constituez votre dossier de location en trois étapes",
      "h1": "Je télécharge mes pièces",
      "p1": "DossierFacile vous demande les pièces nécessaires et rien que celles-là !",
      "u1a": "Pièce d'identité",
      "u1b": "Justificatif de domicile",
      "u1c": "Justificatif de situation professionnelle",
      "u1d": "Avis d'imposition",
      "u1e": "Justificatif de ressources",
      "h2": "DossierFacile valide mon dossier",
      "p2": "Nos agents vérifient votre dossier et vous aident à le corriger si besoin.",
      "h3": "Mon dossier est prêt à être envoyé",
      "p3": "Votre dossier sécurisé sous forme de lien URL ou au format PDF est prêt à être envoyé aux propriétaires."
    },
    "s3": {
      "title": "Protégez vos informations personnelles",
      "text1": "Avec DossierFacile, plus de papiers d'identité éparpillés dans la nature !",
      "text2": "Vos documents sont recouverts de filigranes pour vous protéger contre la fraude de propriétaires peu scrupuleux.",
      "text3": "Vous pouvez paramétrer l'ouverture de votre lien dossier : vous pouvez le supprimer à tout moment !",
      "link": "En savoir plus sur la sécurité des données chez DossierFacile"
    },
    "s4": {
      "title1": "Déjà",
      "title2": "65 000",
      "title3": "Dossiers labellisés grâce à DossierFacile",
      "t1": "Le dossier de Karim s'est tout de suite démarqué : c'était le seul dossier reçu complet !",
      "author1": "Joseph, propriétaire à Nantes",
      "t2": "Simple, efficace et pratique : ça m'a fait gagner beaucoup de temps dans ma recherche d'appartement.",
      "author2": "Caroline, étudiante",
      "t3": "Je ne réussissais jamais à visiter un appartement avec mon dossier étranger. Avec DossierFacile, j'ai enfin eu plus de visites !",
      "author3": "Irina, étudiante en Erasmus",
      "link": "Consulter nos statistiques"
    },
    "s5": {
      "title1": "Ils nous font",
      "title2": "confiance"
    }
  }
}
</i18n>
