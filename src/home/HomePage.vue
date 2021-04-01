<template>
    <div>
        <h1>Hi {{account.user.firstName}}!</h1>
        <p>You're logged in with Vue + Vuex & JWT!!</p>
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

         <h3>Perfis salvos:</h3>
        <em v-if="users.loading">Loading users...</em>
        <span v-if="users.error" class="text-danger">ERROR: {{users.error}}</span>
        <ul v-if="users.items">
            <li v-for="profile in users.items" :key="profile.id">
                {{profile.login + ' '}}
                
            </li>
        </ul>
        <p>
            <router-link to="/login">Logout</router-link>
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