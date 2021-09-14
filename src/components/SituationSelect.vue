<template>
  <div class="situations select-box-items">
    <SelectBoxItem
       v-for="s in situations"
       :slug="s.slug"
       :title="s.title"
       :icon="s.icon"
       :badge="s.badge"
       :selected="selected === s.slug"
       @selectedItem="selectSituation"
       :key="s.slug"/>
    
  </div>
</template>

<script>
  import SelectBoxItem from './SelectBoxItem.vue';
  export default{
    components: {
      SelectBoxItem,
    },

    props: [
      'selected',
    ],

    data: () => {
      return {
        situations: [
          {
            title: 'I want an expert to do my taxes for me',
            badge: 'New!',
            icon: 'assets/fs-icon.svg',
            slug: 'expert',
          },
          {
            title: 'I want to do my own taxes with expert advice and review',
            badge: false,
            icon: 'assets/talk_to_expert_2.svg',
            slug: 'with-expert',
          },
          {
            title: 'I want to file on my own',
            badge: false,
            icon: 'assets/expert-review-icon.svg',
            slug: 'own'
          }
        ]
      }
    },

    methods: {
      selectSituation(slug) {
        this.$emit('selectSituation', slug);
      }
    }
  }
</script>

<style>
.select-box-items {
  grid-template-columns: repeat(3, 1fr);
  margin-bottom: 200px;
  display: grid;
  gap: 1em;
}

</style>

