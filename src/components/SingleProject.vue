<template>
  <div class="project" :class="{complete: project.complete}">
      <div class="actions">
          <h3 @click="toggleDetails = !toggleDetails">{{project.title}}</h3>
          <div class="icons">
              <router-link :to="{name:'EditProject', params: {id: project.id}}">
                   <span class="material-symbols-outlined">
                    edit
                  </span>
              </router-link>
              <span @click="handleDelete" class="material-symbols-outlined">
                delete
              </span>
              <span @click="toggleComplete" class="material-symbols-outlined tick">
                done
              </span>
          </div>
      </div>
      <div class="details" v-if="toggleDetails">
          <h5>{{project.details}}</h5>
      </div>
  </div>
</template>

<script>
export default {
props: ['project'],
data(){
    return{
        toggleDetails: false,
        uri: 'http://localhost:3000/projects/' + this.project.id
    }
},
methods: {
    handleDelete(){
        fetch(this.uri, {
            method: 'DELETE'
        }).then(this.$emit('delete', this.project.id))
        .catch(err => console.log(err.message))
    },
    toggleComplete(){
        fetch(this.uri, {
            method: 'PATCH',
            headers: {'Content-Type' : 'application/json'},
            body: JSON.stringify({complete: !this.project.complete})
        }).then(() => this.$emit('complete', this.project.id))
        .catch(err => console.log(err.message))
    },
    

}
}
</script>

<style>
.project{
    background: white;
    margin-bottom: 10px;
    padding: 10px;
    border-left: 4px solid red;
}
.icons .material-symbols-outlined{
color: rgb(152, 152, 152);
margin-left: 10px;
}
.icons .material-symbols-outlined:hover{
color: rgb(62, 62, 62);
font-size: 25px;
background: rgb(243, 243, 243);
}
/* project complete */
.project.complete{
    border-left: 4px solid aquamarine;
}
.project.complete .tick{
    color:aquamarine
}
.actions{
    display: flex;
    justify-content: space-between;
    align-items: center;

}
.actions h3:hover{
   font-size: 1.3rem;
   transition: ease-in-out;

}
</style>