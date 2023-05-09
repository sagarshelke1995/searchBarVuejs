<template>
    <div class="py-20">
        {{ posts.data }}
        <div class="bg-red-200 px-2 text-white w-max" @click="fetch()"> check console</div>
        <div class="max-w-xl mx-auto">
            <input type="text" placeholder="search here" v-model="myInput" @keyup="liKeyDown" class="border-2 border-blue-200 w-full px-2 py-2 outline-none rounded-md">
            <div class="grid grid-cols-4 pt-5">
                <div class="border-[1px] p-2">First Name</div>
                <div class="border-[1px] p-2">Last Name</div>
                <div class="border-[1px] p-2">Salary</div>
                <div class="border-[1px] p-2">Age</div>
            </div>
            <div class="a">
                <div class="a" v-for="emp in posts.data" :key="emp.id">
                    <div class="grid grid-cols-4">
                        <div class="border-[1px] p-2">{{ emp.employee_name.split(" ")[0] }}</div>
                        <div class="border-[1px] p-2">{{ emp.employee_name.split(" ")[1] }}</div>
                        <div class="border-[1px] p-2">{{ emp.employee_salary }}</div>
                        <div class="border-[1px] p-2">{{ emp.employee_age }}</div>
                    </div>
                </div>
            </div>

            <!-- for loading  -->
            <div class="bg-white flex items-center space-x-5 sm:p-5 px-2 py-5" :class="loading ? 'hidden' : 'flex'">
          <span class="sm:text-lg test-sm"> Loading</span>
          <span>
            <svg class="animate-spin h-5 w-5 text-white" xmlns="http://www.w3.org/2000/svg" fill="none"
              viewBox="0 0 24 24">
              <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
              <path class="opacity-75" fill="#021258"
                d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z">
              </path>
            </svg>
          </span>
        </div>
        </div>
    </div>
</template>

<script>
export default{
    data(){
        return{
            posts : [],
            myInput: "",
            loading: true,
            data : [
                {
                "id": 1,
                "employee_name": "Tiger Nixon",
                "employee_salary": 320800,
                "employee_age": 61,
                "profile_image": ""
                },
                {
                "id": 2,
                "employee_name": "Garrett Winters",
                "employee_salary": 170750,
                "employee_age": 63,
                "profile_image": ""
                },
                {
                "id": 3,
                "employee_name": "Ashton Cox",
                "employee_salary": 86000,
                "employee_age": 66,
                "profile_image": ""
                },
                {
                "id": 4,
                "employee_name": "Cedric Kelly",
                "employee_salary": 433060,
                "employee_age": 22,
                "profile_image": ""
                },
                {
                "id": 5,
                "employee_name": "Airi Satou",
                "employee_salary": 162700,
                "employee_age": 33,
                "profile_image": ""
                },
]
        }
    },
    methods:{

        async fetch(error) {
            this.loading = false
        this.posts = await this.$axios.$get('https://dummy.restapiexample.com/api/v1/employees')
        console.log(this.posts)
        this.loading = true
    },
    async liKeyDown(){
       
    }
    }
}
</script>