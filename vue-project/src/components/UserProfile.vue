<template>
  <div id="app">
    <div class="prfle-form">
      <div class="username">
        @{{ user.username }} - {{ fullName }}<br />
        <br />
      </div>
      <div class="admin" v-if="user.isAdmin">
          Admin
      </div>

      <div class="userfollwer"><strong>Followers: </strong>{{ followers }}</div>
         <div class="count" v-for="count in user.count" :key="count.id">
          {{count.place}}
      </div>
      <div class="btn">
        <button @click="followUser">
          Follow Me
        </button>
      </div>

     
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: "Roet43",
        firstName: "Rohit",
        lastName: "Thapa",
        email: "rohitthapa43@gmail.com",
        isAdmin: true,
        count:[
            {id: 1, place: 'Its Amazing'},
            {id: 2, place: 'Hey listen'},
        ]
      },
    };
  },
  watch: {
    followers(newCount, oldCount) {
      if (oldCount < newCount) {
        console.log(`${this.user.username} has a new follower!`);
      }
    },
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    },
  },
  methods: {
    followUser() {
      this.followers++;
    },
  },
  mounted() {
    this.followUser();
  },
};
</script>

<style>
*
.prfle-form {
  border: 2px solid #333;
  padding: 20px;
  box-shadow: 2px 3px 5px #49ebf4;
  display: flex;
  flex-direction: column;
  max-width: 330px;
}
.username
{
    font-size: 20px;
}
.btn
{
    margin-top: 30px;
}
.btn button
{
        padding: 10px;

}
.admin
{
    background: purple;
    padding: 5px 20px;
    margin-right: auto;
    color: #fff;
    border-radius: 7px;
    margin-bottom: 15px;
}
</style>
