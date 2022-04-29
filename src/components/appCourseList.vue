<template>
    <div class="card card-light mt-20">
          <h3>Aktif Kurslarım</h3>
          <ul v-for="item in items" :key="item.id" class="list mt-20">
            <li class="course-item list-item " :style="itemClasses(item)">
              <span>{{item.courseName}}</span>
              <input @click="checkBoxCourse(item)" type="checkbox" />
            </li>
          
          </ul>
        </div>
</template>
<script>
export default {
  data() {
    return {
      courseBackground: {'background-color': 'red'},
    }
  },
  props: {
    items: {
      type: Array,
      required: true,
      default: () => []
    }
  },
  methods: {
    checkBoxCourse(item) {
           this.$emit("checkBox-item", item);
           this.itemClasses(item);
    },
        itemClasses(fruit){
            if(fruit.check === true){
            return  {'background-color': 'green'}
            }
            else{
                return  {'background-color': 'red'}
            }
        }
  }
}
</script>