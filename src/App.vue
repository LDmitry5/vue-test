<script>
export default {
  data() {
    return {
      itemsLeft: [
        {
          id: 1,
          name: "Shoes 1",
        },
        {
          id: 2,
          name: "Shoes 2",
        },
        {
          id: 3,
          name: "Shoes 3",
        },
        {
          id: 4,
          name: "Shoes 4",
        },
        {
          id: 5,
          name: "T-shirt 1",
        },
        {
          id: 6,
          name: "T-shirt 2",
        },
        {
          id: 7,
          name: "T-shirt 3",
        },
        {
          id: 8,
          name: "T-shirt 4",
        },
      ],
      itemsRight: [
        {
          id: 11,
          name: "Jacket 1",
        },
        {
          id: 12,
          name: "Jacket 2",
        },
        {
          id: 13,
          name: "Jacket 3",
        },
        {
          id: 14,
          name: "Jacket 4",
        },
        {
          id: 15,
          name: "Hoodie 1",
        },
        {
          id: 16,
          name: "Hoodie 2",
        },
        {
          id: 17,
          name: "Hoodie 3",
        },
        {
          id: 18,
          name: "Hoodie 4",
        },
      ],
      selectedLeft: [],
      selectedRight: [],
    };
  },
  methods: {
    addLeft(item) {
      if (this.selectedLeft.length < 6 && !this.isSelectedLeft(item)) {
        this.selectedLeft.push(item);
      }
    },
    removeLeft(item) {
      this.selectedLeft = this.selectedLeft.filter((i) => i.id !== item.id);
    },
    selectRight(item) {
      this.selectedRight = item;
    },
    isSelectedLeft(item) {
      return this.selectedLeft.some((i) => i.id === item.id);
    },
    isSelectedRight(item) {
      return this.selectedRight?.id === item.id;
    },
  },
};
</script>

<template>
  <div class="top-section">
    <div class="left-top">
      <div v-for="(item, index) in selectedLeft" :key="index">{{ item.name }}</div>
    </div>
    <div class="right-top">
      <div>{{ selectedRight.name }}</div>
    </div>
  </div>
  <div class="bottom-section">
    <div class="left-bottom">
      <div v-for="item in itemsLeft" :key="item.id" @click="addLeft(item)" :class="{ selected: isSelectedLeft(item) }">{{ item.name }}</div>
    </div>
    <div class="right-bottom">
      <div v-for="item in itemsRight" :key="item.id" @click="selectRight(item)" :class="{ selected: isSelectedRight(item) }">{{ item.name }}</div>
    </div>
  </div>
</template>

<style>
.top-section,
.bottom-section {
  display: flex;
  flex: 1;
  gap: 20px;
  color: white;
}
.left-top,
.right-top,
.left-bottom,
.right-bottom {
  flex: 1;
  padding: 10px;
  border: 2px solid grey;
  border-radius: 10px;
  background: #a6a6a6;
  background: radial-gradient(circle, rgba(166, 166, 166, 1) 0%, rgba(130, 142, 153, 1) 100%);
}
.left-bottom div,
.right-bottom div {
  margin: 5px;
  padding: 10px;
  cursor: pointer;
}
.selected {
  background-color: lightblue;
  border-radius: 10px;
  color: black;
}
</style>
