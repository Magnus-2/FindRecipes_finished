<template>
  <html lang="en">
      <!-- <div class="profile">
        <h4>City List</h4>
        <br>
        <div class="row">
        <div class="col-xs-8 col-sm-8 col-md-8 col-lg-8">
        <div class="panel panel-info" >
          <div class="panel-heading">
            <h3 class="panel-title">List of Recipes</h3>
          </div>
          <div class="panel-body">
            <div class="row">
          <div class="col-sm-6 col-md-4" v-for="(user, key) in users" :key = 'key' >
            <div class="thumbnail">
              <img src="" width=80%>
              <div class="caption">
                <p><b>Username</b></p>
                <p class="Profile">{{user.Username}}</p>
                <p class="Email">{{user.Email}}</p>
                <p class="Profile">{{user.Diet}}</p>
                <p class="Profile">{{user.Password}}</p>
                
                
              </div>
            </div>
          </div>
        </div>
          </div>
        </div>
        </div>
        </div>
        <div class="row">
        <div class="container">
          <button @click="logout" class="btn btn-default"><span class="glyphicon glyphicon-log-out"></span> Logout</button>
        </div>
        </div>
        <br>
      </div> -->
  
  
  
  
  
  <head>
    <meta charset="utf-8">
      <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
      <meta name="description" content="Start your development with Dorang landing page.">
      <meta name="author" content="Devcrud">
      <title>Profil</title>
  
  </head>
  <body data-spy="scroll" data-target=".navbar" data-offset="40" id="home" class="dark-theme">
  
  
      <div class="theme-selector">
          <a href="javascript:void(0)" class="spinner">
              <i class="ti-paint-bucket"></i>
          </a>
          <div class="body">
              <a href="javascript:void(0)" class="light"></a>
              <a href="javascript:void(0)" class="dark"></a>
          </div>
      </div>  
  
      <br/><br/><br/><br/><br/><br/>
      <!-- page header -->
     
  
      <!-- 1 -->
      <link href="https://maxcdn.bootstrapcdn.com/font-awesome/4.3.0/css/font-awesome.min.css" rel="stylesheet">
  <div class="container bootstrap snippets bootdey">
  <div class="row">
    <div class="profile-nav col-md-3" v-for="(user, key) in users" :key = 'key'>
        <div class="panel">
            <div class="user-heading round">
                <a href="#">
                    <img src="https://bootdey.com/img/Content/avatar/avatar3.png" alt="">
                </a>
                <h1>{{user.Username}}</h1>
                <p>{{user.Email}}</p>
            </div>
  
            <ul class="nav nav-pills nav-stacked">
                <li><a href="editp.html"> <i class="fa fa-calendar"></i> Favorite<span class="label label-warning pull-right r-activity"></span> </a></li>
                <li><a href="#"> <i class="fa fa-edit"></i> Edit profile</a></li>
                
            </ul>
        </div>
    </div>
    <div class="profile-info col-md-9" v-for="(user, key) in users" :key = 'key'>
       
        <div class="panel">
           
            <div class="panel-body bio-graph-info">
                <h1>User Profile</h1>
                <div class="row">
                    <div class="bio-row">
                        <p><span>First Name: </span>Camila</p>
                    </div>
                    <div class="bio-row">
                        <p><span>Last Name: </span>Smith</p>
                    </div>
                    <div class="bio-row">
                        <p><span>Country: </span>Australia</p>
                    </div>
                    <div class="bio-row">
                        <p><span>Diet:</span>{{user.Diet}}</p>
                    </div>
                    <div class="bio-row">
                        <p><span>Email:</span>jsmith@mahidol.com</p>
                    </div>
                    <div class="bio-row">
                        <p><span>Mobile:</span>(12) 03 4567890</p>
                    </div>
                </div>
            </div>
        </div>
        <div>
         
        </div>
    </div>
  </div>
  </div>
  
  <footer class="footer">
                  <p class="infos">&copy;, Made with <i class="ti-heart text-danger"></i> by Celina, Magnus, Till and Kevin</p>       
                  <span>|</span>  
                  <div class="links">
                      <a href="#">About</a>
                      <a href="#">Recipe</a>
                      <a href="#">Profile</a>
                      <button @click="logout" class="btn btn-default" style="color: red; border: solid">Logout</button>
                  </div>
  
                      
               
              </footer>
  
  </body>
  </html>
  
  
  
  
  
  
  
    </template>
    
    <script>
    import {collection, onSnapshot, doc, getFirestore, } from "firebase/firestore"
    import {getAuth, signOut} from 'firebase/auth'
    export default {
      name: 'Profile',
      data () {
        return {
          user: null,
          users: {},
          userIds:{},
          auth: getAuth()
        }
      },
      mounted () {
        console.log('This is the User Profile')
        const db = getFirestore()
        const colRef = collection(db, "User")
        onSnapshot(colRef, snapShot => {
          this.users = snapShot.docs.map(doc => doc.data())
          this.userIds = snapShot.docs.map(doc => doc.id)
        })
      },
      //code from class
      methods: {
        logout () {
          console.log('logout')
          signOut(this.auth)
        .then(()=>{
          this.$router.replace('/signin')
        })
        .catch((error) => {
          alert(error.message)
        })
        }
      }
    }
    </script>
    
    <!-- Add "scoped" attribute to limit CSS to this component only -->
    <style scoped>
    @import '../assets/css/profile.css';
    h1, h2 {
      font-weight: normal;
    }
    ul {
      list-style-type: none;
      padding: 0;
    }
    li {
      /* display: inline-block; */
      margin: 0 10px;
    }
    a {
      color: #ffffff;
    }
    p.citydetail{
      text-align: justify;
    }
    </style>