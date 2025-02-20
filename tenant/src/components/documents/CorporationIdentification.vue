<template>
  <div>
    <ValidationObserver>
      <validation-provider rules="required" v-slot="{ errors }">
        <div
          class="fr-input-group"
          :class="errors[0] ? 'fr-input-group--error' : ''"
        >
          <label class="fr-label" for="organismName"
            >{{ $t("organism-name") }} :</label
          >
          <input
            v-model="organismName"
            class="form-control fr-input validate-required"
            id="organismName"
            name="organismName"
            :placeholder="$t('organism-name-placeholder')"
            type="text"
            required
          />
          <span class="fr-error-text" v-if="errors[0]">{{ errors[0] }}</span>
        </div>
      </validation-provider>
      <div>
        <div class="fr-mb-3w">
          {{ $t("kbis-label") }}
        </div>
        <div class="fr-mb-3w">
          <FileUpload
            :current-status="fileUploadStatus"
            @add-files="addFiles"
            @reset-files="resetFiles"
          ></FileUpload>
        </div>
      </div>
      <div class="fr-col-lg-8 fr-col-md-12 fr-mb-3w">
        <ListItem
          v-for="(file, k) in listFiles()"
          :key="k"
          :file="file"
          @remove="remove(file)"
          :uploadState="
            uploadProgress[file.id] ? uploadProgress[file.id].state : 'idle'
          "
          :percentage="
            uploadProgress[file.id] ? uploadProgress[file.id].percentage : 0
          "
        />
      </div>
      <div class="fr-col-12 fr-mb-2w">
        <button
          class="fr-btn"
          type="submit"
          @click="save"
          :disabled="!organismName || files.length <= 0"
        >
          {{ $t("register") }}
        </button>
      </div>
      <div class="fr-mb-5w">
        <DocumentInsert
          :allow-list="acceptedProofs"
          :block-list="refusedProofs"
        ></DocumentInsert>
      </div>
    </ValidationObserver>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { mapState } from "vuex";
import DocumentInsert from "@/components/documents/DocumentInsert.vue";
import FileUpload from "@/components/uploads/FileUpload.vue";
import { UploadStatus } from "../uploads/UploadStatus";
import ListItem from "@/components/uploads/ListItem.vue";
import { ValidationObserver, ValidationProvider } from "vee-validate";
import { extend } from "vee-validate";
import { required } from "vee-validate/dist/rules";
import { DfDocument } from "df-shared/src/models/DfDocument";
import { DfFile } from "df-shared/src/models/DfFile";
import { RegisterService } from "../../services/RegisterService";
import { Guarantor } from "df-shared/src/models/Guarantor";

extend("required", {
  ...required,
  message: "Ce champ est requis"
});

@Component({
  components: {
    DocumentInsert,
    FileUpload,
    ListItem,
    ValidationProvider,
    ValidationObserver
  },
  computed: {
    ...mapState({
      selectedGuarantor: "selectedGuarantor"
    })
  }
})
export default class CorporationIdentification extends Vue {
  organismName = "";
  acceptedProofs = [
    this.$i18n.t("kbis"),
    this.$i18n.t("status"),
    this.$i18n.t("all-accepted")
  ];
  refusedProofs = [
    this.$i18n.t("balance-sheet"),
    this.$i18n.t("urssaf"),
    this.$i18n.t("all-other")
  ];

  selectedGuarantor!: Guarantor;

  files: File[] = [];
  fileUploadStatus = UploadStatus.STATUS_INITIAL;
  uploadProgress: {
    [key: string]: { state: string; percentage: number };
  } = {};

  mounted() {
    this.organismName = this.selectedGuarantor.legalPersonName || "";
  }

  addFiles(fileList: File[]) {
    this.files = [...this.files, ...fileList];
  }

  save() {
    this.uploadProgress = {};
    const fieldName = "documents";
    const formData = new FormData();
    if (!this.files.length) return;
    Array.from(Array(this.files.length).keys()).map(x => {
      formData.append(`${fieldName}[${x}]`, this.files[x], this.files[x].name);
    });

    formData.append("legalPersonName", this.organismName);
    if (this.$store.getters.guarantor.id) {
      formData.append("guarantorId", this.$store.getters.guarantor.id);
    }

    this.fileUploadStatus = UploadStatus.STATUS_SAVING;
    const loader = this.$loading.show();
    RegisterService.saveCorporationIdentification(formData)
      .then(() => {
        this.files = [];
        this.fileUploadStatus = UploadStatus.STATUS_INITIAL;
        this.$store.dispatch("loadUser");
        Vue.toasted.global.save_success();
      })
      .catch(() => {
        this.fileUploadStatus = UploadStatus.STATUS_FAILED;
        Vue.toasted.global.save_failed();
      })
      .finally(() => {
        loader.hide();
      });
  }

  resetFiles() {
    this.fileUploadStatus = UploadStatus.STATUS_INITIAL;
  }

  remove(file: DfFile) {
    if (file.path && file.id) {
      RegisterService.deleteFile(file.id);
    } else {
      this.files = this.files.filter((f: DfFile) => {
        return f.name !== file.name;
      });
    }
  }

  listFiles() {
    const newFiles = this.files.map(f => {
      return {
        id: f.name,
        name: f.name,
        size: f.size
      };
    });
    const existingFiles =
      this.$store.getters.getDocuments?.find((d: DfDocument) => {
        return d.documentCategory === "IDENTIFICATION_LEGAL_PERSON";
      })?.files || [];
    return [...newFiles, ...existingFiles];
  }
}
</script>

<style scoped lang="scss">
table {
  border-collapse: collapse;
}

table,
th,
td {
  border: 1px solid #ececec;
}
</style>

<i18n>
{
"en": {
  "organism-name": "Company name",
  "organism-name-placeholder": "Company name",
  "kbis-label": "I add a K bis of the company, or any other document justifying the legal existence of the company.",
  "kbis": "Original Kbis of the company",
  "status": "Company statuses",
  "all-accepted": "Any other document justifying the legal existence of the company.",
  "balance-sheet": "Balance sheet",
  "urssaf": "Urssaf certificate",
  "all-other": "Any other document",
  "register": "Register documents"
},
"fr": {
  "organism-name": "Nom de la personne morale",
  "organism-name-placeholder": "Nom de la personne morale",
  "kbis-label": "J’ajoute un extrait K bis de la société, ou toute autre pièce justifiant de l'existence légale de la personne.",
  "kbis": "Extrait K bis original de la société",
  "status": "Statuts de la personne morale",
  "all-accepted": "Toute autre pièce justifiant de l'existance légale de la personne, prouvant qu'une déclaration a été effectuée auprès d'une administration, une juridiction ou un organisme professionnel.",
  "balance-sheet": "Bilan comptable",
  "urssaf": "Attestation cotisation Urssaf",
  "all-other": "Toute autre pièce",
  "register": "Enregistrer la pièce"
}
}
</i18n>
