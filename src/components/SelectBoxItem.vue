<template>
  <div class="select-box-item"
    :class="{selected: selected}"   
    @click="$emit('selectedItem', slug)">
    <div class="badge" v-if="badge">{{ badge }}</div>
    <img :src="require('@/' + icon)" :alt="title" v-if="!selected">
    <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI1MiIgaGVpZ2h0PSI1MiIgdmlld0JveD0iMCAwIDUyIDUyIj4gICAgPGcgZmlsbD0ibm9uZSIgZmlsbC1ydWxlPSJldmVub2RkIj4gICAgICAgIDxwYXRoIHN0cm9rZT0iIzBEQzM2QSIgc3Ryb2tlLXdpZHRoPSIyIiBkPSJNNTEgMjZjMCAxMy44MDgtMTEuMTkyIDI1LTI1IDI1UzEgMzkuODA4IDEgMjYgMTIuMTkyIDEgMjYgMXMyNSAxMS4xOTIgMjUgMjUiLz4gICAgICAgIDxwYXRoIGZpbGw9IiMwREMzNkEiIGQ9Ik0zOC42OTEgMTZMMjIuODg4IDMxLjc4OSAxNS4wOCAyNC44NCAxMiAyOC4xNThsOS4yNCA4LjE3Mi4wMi0uMDIyTDIzLjA5IDM4IDQyIDE5LjEwN3oiLz4gICAgPC9nPjwvc3ZnPg==" v-if="selected" 
    alt="">
    <div class="item-title">{{ title }}</div>
  </div>
</template>

<script>
  export default{
    props: [
      'slug',
      'title',
      'icon',
      'badge',
      'selected',
    ],
    data: () => {
      return {
        img: null,
      }
    },

    methods: {
      getImage() {
      }
    }
    
  }
</script>

<style scoped>
.select-box-item {
  border-radius: 7.2px;
  padding: 30px 20px 10px 20px;
  display: flex;
  flex-direction: column;
  box-shadow: rgb(212, 215, 220) 0px 2px 9px;
  align-items: center;
  position: relative;
}

.select-box-item:hover {
  box-shadow: 0 2px 28px 0 #d4d7dc;
  cursor: pointer;
}

.badge {
  position: absolute;
  height: 22px;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  align-content: center;
  text-align: center;
  text-transform: uppercase;
  font-size: 12px;
  line-height: 16px;
  font-weight: 700;
  color: #fff;
  top: 0px;
  left: 0px;
  width: 100%;
  background: rgb(213, 43, 30);
  border-radius: 7.2px 7.2px 0 0;
}

img {
  margin-bottom: 10px;
  width: 40px;
  height: 40px;
}

.item-title {
  font-size: 12px;
  line-height: 14px;
  color: #393a3d;
  text-align: center;
}

.select-box-item.selected {
  box-shadow: 0 0 0 2px #0dc36a;
  background-color: rgba(83,194,124,.2);
}

.select-box-item.selected .badge {
  display: none;
}

</style>

