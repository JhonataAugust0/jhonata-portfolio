<template>
  <div class="container-description" :style="{
    borderRadius: modalBorderRadius,
    backgroundColor: modalBackgroundColor,
    padding: modalPadding,
    border: modalBorderColor,
  }">
    <div class="header">
      <div class="texts">
        <p class="title" v-html="text" />
        <p class="period" v-html="textPeriod" />
      </div>

      <button class="modal-handle" @click="expandModal">
        <span v-if="!expanded">+</span>
        <span v-else>-</span>
      </button>
    </div>

    <div v-if="expanded" class="details">
      <p class="description">{{experienceDescription}}</p>
      <div class="technologies">
        <ul>
          <li v-for="(tech, index) in technologies" :key="index">
            <a :href="tech.link" target="_blank" rel="noopener noreferrer">{{ tech.name }}</a>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

interface Technology {
  name: string;
  link: string;
}

interface ModaExperienceProps {
  modalBorderRadius?: string;
  modalBackgroundColor?: string;
  modalPadding?: string;
  modalBorderColor?: string;
  text: string;
  textPeriod: string;
  experienceDescription: string;
  technologies: Array<Technology>;

}

export default defineComponent({
  name: 'ExperienceContent',
  props: {
    modalBorderRadius: {
      type: String,
      default: '8px'
    },
    modalBackgroundColor: {
      type: String,
      default: 'var(--var-background-color-gray)'
    },
    modalPadding: {
      type: String,
      default: '12px 28px 12px 28px'
    },
    modalBorderColor: {
      type: String,
      default: '1px solid var(--var-background-color-gray)'
    },
    text: {
      type: String,
      required: true
    },
    textPeriod: {
      type: String,
      required: true
    },
    experienceDescriptionProp: {
      type: String,
      default: ''
    },
    technologiesProp: {
      type: Array<Technology>,
      default: () => [] as Technology[]
    }
  },
  mounted() {
    this.experienceDescription = this.experienceDescriptionProp;
    this.technologies = this.technologiesProp;
  },
  methods: {
    expandModal() {
      this.expanded = !this.expanded;
    },
  },
  data () {
    return {
      expanded: false,
      experienceDescription: '',
      technologies: [] as Technology[]
    }
  }
});
</script>

<style scoped>
.container-description {
  margin: 4px;
  min-width: 69.9%;
  max-width: 70%;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
}

.texts {
  flex-grow: 1;
  display: flex;
  justify-content: space-between;
  margin-right: 16px;
}

.texts p {
  font-family: Inter, monospace;
  line-height: normal;
  color: var(--var-color-text-button-white);
  font-weight: 400;
  font-size: 24px;
  text-align: justify;
}

.modal-handle {
  background-color: #1EA678;
  color: white;
  border: none;
  padding: 5px 10px;
  border-radius: 6px;
  cursor: pointer;
  margin-left: auto;
}

.modal-handle:hover {
  filter: brightness(.8);
}

.details {
  margin-top: 10px;
}

.details p {
    font-family: Inter, monospace;
    line-height: normal;
    color: var(--var-color-text-button-white);
    font-weight: 400;
    font-size: 18px;
    text-align: justify;
}

.description {
  width: 100%;
  margin-bottom: 10px;
}

.technologies ul {
  list-style-type: none;
  padding: 0;
  display: flex;
  gap: 32px
}

.technologies ul li {
  margin-right: 10px;
}

.technologies a {
  font-family: Inter, monospace;
  line-height: normal;
  color: var(--var-color-link-text-gray);
  font-weight: 400;
  font-size: 14px;
  text-align: justify;
}

@media (max-width: 768px) {
  .texts {
    flex-direction: column;
    flex-wrap: wrap;
    padding: 12px;
  }

  .period {
    text-align: left;
    margin-top: 5px;
  }

  .title, .period {
    flex-basis: 100%;
    text-align: center;
  }

  .modal-handle {
    margin-top: 10px;
  }

  .details {
    flex-direction: column;
  }

  .technologies ul {
    padding: 4px;
    display: flex;
    flex-wrap: wrap;
  }

  .technologies ul li {
    margin-bottom: 5px;
    margin-right: 18px;
  }
}
</style>