<template>
  <!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Kurs Planlaması</title>
  </head>
  <body>
    <header>Kurs Planlaması</header>
    <div class="container">
      <div class="course--planner-app--container">
        
        <appCourseInput @new-item="addNewValue" />
        <appCourseList :items="courseList" @checkBox-item="checkBoxCourse" />

       
        <div class="mt-10">
          <small v-html="totalCount"></small>
        </div>
      </div>
    </div>
  </body>
</html>

</template>
<script>
import appCourseInput from "@/components/appCourseInput"
import appCourseList from "@/components/appCourseList"
export default {
  data() {
    return {
      courseList: [{id: 1, courseName: 'Vue.js', check:false},{id: 1, courseName: 'React.js', check:false}],
      greenCount:0,
      redCount:0
    }
  },
  methods: {
    checkBoxCourse(item) {
            const index = this.courseList.findIndex(x => x === item);
            this.courseList[index].check=!(this.courseList[index].check);   
    },
    addNewValue(newCourse){
      this.courseList.push({
        id:new Date().getTime(),
        courseName: newCourse,
        check:false
      });
    }
  },
  computed : {
        totalCount(){
          var greenCount=0;
          var redCount=0;
            this.courseList.forEach(element => {
                if(element.check===true){
                  
                    greenCount++;
                }else{
                    redCount++;
                }
            });
            return `izlenecek ${redCount} adet ve izlenmiş ${greenCount} adet kursunuz var`
        },
        
    },
  components: {
    appCourseInput,
    appCourseList
  }
  
}
</script>

<style >

@import 'assets/style.css';
</style>