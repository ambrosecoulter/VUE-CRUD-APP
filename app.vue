const app = Vue.createApp({
  data() {
    return {
      navTitle: 'Vue App',
      footerMessage: 'BEST-Dev.com.au (2021)',
      users: [
        'user1',
        'employee17',
        'bob',
        'sarah',
        'garfield',
        ],
      usersTextColor: [
        'white',
        'white',
        'white',
        'white',
        'white',
      ],
      displayUsers: false,
      newUser: '',
      searchName: '',
      }
    },
    methods: {
      changeDisplay() {
        this.displayUsers = !this.displayUsers;
      },
      addNewUser(newUserInput) {
        if (newUserInput !== ''){
          this.users.push(newUserInput);
          this.newUser = '';
          for (var i = 0; i < this.usersTextColor.length; i++){
            this.usersTextColor[i] = 'white';
          }
          this.usersTextColor.push('lightgreen');
        }
      },
    },
    computed: {
      numberOfUsersText() {
        return 'There are ' + this.users.length + ' users.';
       },
      searchResults() {
        if (this.searchName !== ''){
          return this.users.filter(el => el.match(this.searchName))
        } else {
          return '';
        }
      },
      searchTextClass() {
        if (this.searchName != ''){
          return 'searchTitleBold';
        } else {
          return 'searchTitleNormal';
        }
      },
    }
});
app.component('app-header', {
  template: '<div><h1>Component Title</h1></div>'
});
app.component('app-menulinks', {
  template: '<div><ul><li>Home</li><li>About</li><li>Contact</li></ul></div>'
});
app.component('app-footer', {
  template: '<div><h4>best-dev.com.au (2021)</h4></div>'
})
const mountedApp = app.mount('#vue-app')
