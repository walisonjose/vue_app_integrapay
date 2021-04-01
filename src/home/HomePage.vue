<template>
    <div>
        <h1>Olá {{account.user.firstName}}!</h1>
        
        <!--h3>Users from secure api end point:</h3>
        <em v-if="users.loading">Loading users...</em>
        <span v-if="users.error" class="text-danger">ERROR: {{users.error}}</span>
        <ul v-if="users.items">
            <li v-for="user in users.items" :key="user.id">
                {{user.firstName + ' ' + user.lastName}}
                <span v-if="user.deleting"><em> - Deleting...</em></span>
                <span v-else-if="user.deleteError" class="text-danger"> - ERROR: {{user.deleteError}}</span>
                <span v-else> - <a @click="deleteUser(user.id)" class="text-danger">Delete</a></span>
            </li>
        </ul-->

         <h3>Perfis Github favoritados:</h3>
        <em v-if="users.loading">Loading users...</em>
        <span v-if="users.error" class="text-danger">ERROR: {{users.error}}</span>
        <ul v-if="users.items">
            <li v-for="profile in users.items" :key="profile.id">

             
                {{profile.login + ' '}} <br />


                <img :src='profile.photo_url' alt='' width="100" height="100">
                
            </li>
        </ul>
        <p>
            <router-link to="/login">Sair</router-link>
        </p>
 
    </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'

export default {
    computed: {
        ...mapState({
            account: state => state.account,
            users: state => state.users.all,
         //   profiles: state => state.profiles.all,
        })
    },
    created () {
        this.getAllUsers();
       // this.getAllProfiles();
    },
    methods: {
        ...mapActions('users', {
            getAllUsers: 'getAll',
            deleteUser: 'delete',
          //  getAllProfiles: 'getAllProfiles'
        })
    }
};
</script>