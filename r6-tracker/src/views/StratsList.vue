<template>
  <div class="tableStrat">
    <div>
      <table class="table table-dark">
        <thead>
          <tr>
            <th scope="col">ID</th>
            <th scope="col">Role</th>
            <th scope="col"></th>
            <th scope="col"></th>
            <th scope="col">Operators</th>
            <th scope="col"></th>
            <th scope="col"></th>
            <th scope="col">Map</th>
            <th scope="col">See Detail</th>
          </tr>
        </thead>
        <tbody>
          <tr  v-for='strat in strats' v-bind:key='strat.id'>
            <td>{{strat.id}}</td>
            <td>{{strat.currentRole}}</td>
            <td v-for='myOperator in strat.myOperators' v-bind:key='myOperator.id'><img v-bind:src='myOperator.iconUrl' style="width:100px"> </td>
            <td><img v-bind:src='strat.Map.imgUrl' style="width:100px"> <br>{{strat.Map.name}}</td>
            <td><button type="button" class="btn btn-warning" style="color:white;" @click.prevent="stratDetail(strat.id)">DETAIL</button></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: 'StratsList',
  created(){
    this.$store.dispatch('getAllStrats')
    if (localStorage.access_token){
      this.$store.commit('SET_ISLOGIN', true)
    }
  },
  computed: {
    strats(){
      return this.$store.state.strats
    }
  },
  methods: {
    stratDetail(id){
      this.$router.push({name: 'StratDetail', params: {id}})
    }
  }
}
</script>

<style>
.tableStrat{
  display: flex;
  flex-direction: row;
  justify-content: center;
  padding-top: 30px;
  height: 70vh;
  overflow: hidden;
  width: 100vw;
  opacity: 0.8;
  /* padding-left: 500px; */
}
</style>