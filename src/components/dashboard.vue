<template>
    <div class="dashboard-wrapper">
        <div class="dashboard">
            <h3>Dashboard</h3>
        </div>
        <div class="filter">
            <Filter :tasks="tasks" @filter="filteredCards"/>
        </div>
        <div class="cards">
            <div :key="task.id" v-for="task in filteredTasks">
                <Card :task="task" @update="updatelabels"/>
            </div>
        </div>
    </div>
</template>

<script>
    import { getData } from './Data/data';
    import Card from './utils/card.vue';
    import Filter from './utils/filter.vue';
    export default {
        name:'DashBoard',
        data() {
            return{
                tasks: [],
                filteredTasks:[]
            }
        },
        components :{
            Card,
            Filter
        },
        created() {
            this.tasks = getData();
            this.filteredTasks=this.tasks;
        },
        methods:{
            filteredCards(category){
                var filtertag=""
                if (category =="" || category == "all"){
                    filtertag="all"
                    console.log(this.tasks);
                    this.filteredTasks = this.tasks;
                    return this.tasks;
                }else{
                    filtertag=category;
                    const filtereddata = this.tasks.filter((item) => {
                        let tags = item.labels.some((label) => {
                            return label === filtertag;
                        })
                        return tags;
                    })
                    console.log(filtereddata);
                    this.filteredTasks = filtereddata;
                    return filtereddata;
                }
            },
            updatelabels: function(id, labels){
                console.log(id, labels);
                for (var i=0; i<this.tasks.length; i++){
                    if(this.tasks[i].id === id){
                        this.tasks[i].labels = labels;
                        console.log(this.tasks[i].labels);
                        this.filteredTasks = this.tasks;
                    }
                }
            }
        }

    }
</script>
<style scoped>
.dashboard-wrapper{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
.filter{
    width:60%;
    margin-top:2rem;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 2rem;
}
.cards{
    width:75%;
    display: grid;
    gap: 4rem 30px ;
    grid-template-columns: repeat(3, 25vw);
    box-sizing: border-box;
    margin:0 auto;
    margin-bottom:7rem;
    align-items: center;
}

</style>