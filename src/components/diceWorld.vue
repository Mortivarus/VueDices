<script>

export default{
    data(){
        return{
            totalCount:{
                1: 0,
                2: 0,
                3: 0,
                4: 0,
                5: 0,
                6: 0
            },

            outcome: []
        }
    },
    methods:{
        throwDice(){
                this.outcome = []

                for(i = 0; i < 6; i++){
                    this.outcome.push(Math.floor(Math.random()*6) +1)
                }

                for(let number in this.totalCount){
                    const countNumber = this.outcome.filter(thrown => thrown == number).length;
                    this.totalCount[number] += countNumber
                }
            }

        }
}
</script>

<template>
    <table>
        <thead>
        <tr>
            <th>Getal</th>
            <th>Aantal</th>
        </tr>
        </thead>
        <tbody>
            <tr v-for="(value, key) in totalCount">
                <td>{{key}}</td>
                <td>{{value}}</td>
            </tr>
        </tbody>
    </table>
        <button  v-on:click="throwDice()">Gooi!</button>

        <div>Uitkomst van je worp: {{outcome.join(', ')}}</div>
</template>
