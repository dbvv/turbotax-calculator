<template>
  <div class="situations select-box-items">
    <SelectBoxItem
       v-for="s in situations"
       :slug="s.slug"
       :title="s.title"
       :icon="s.icon"
       :badge="s.badge"
       :selected="selected.indexOf(s.slug) !== -1"
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
            title: 'I want to maximize deductions and credits',
            badge: false,
            icon: 'assets/maximize_refinancing_tax_credits.svg',
            slug: 'maximize_refinancing_tax_credits',
          },
          {
            title: 'I donated over $300 to charity',
            badge: false,
            icon: 'assets/charity_donations.svg',
            slug: 'charity_donations',
          },
          {
            title: 'I\'m paying off student loans',
            badge: false,
            icon: 'assets/icon-student-loans.svg',
            slug: 'student-loans'
          },
        ],
      }
    },

    methods: {
      selectSituation(situation) {
        this.$emit('selectSituation', situation, 'add');
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

