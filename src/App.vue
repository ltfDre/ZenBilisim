<template>
  <div id="app">
    <b-navbar type="dark" variant="dark">
      <b-container>
        <b-navbar-nav class="d-flex align-items-center">
          <b-img class="mt-2" src="@/assets/gog-logo.jpg" height="50" width="75" rounded></b-img>
          <b-nav-item class="text-uppercase ml-3" size="lg" href="#">store <fa-icon :icon="chevronDown"/></b-nav-item>
          <b-nav-item class="text-uppercase ml-3">about <fa-icon :icon="chevronDown"/></b-nav-item>
          <b-nav-item class="text-uppercase ml-3">community <fa-icon :icon="chevronDown"/></b-nav-item>
          <b-nav-item class="text-uppercase ml-3">support <fa-icon :icon="chevronDown"/></b-nav-item> 
          <b-nav-item class="text-uppercase ml-3">
            <b-nav-text class="text-success">
              sign in
              <fa-icon :icon="chevronDown"/>
            </b-nav-text>
          </b-nav-item>
        </b-navbar-nav>
      </b-container>
    </b-navbar>

    <b-container class="mt-2 mb-2">
      <b-row class="d-flex align-items-center">
        <fa-icon :icon="penIcon"/>
        <span class="ml-2 text-secondary">
          <strong>Highlights</strong>
        </span>
      </b-row>
      <hr>
    </b-container>

    <b-container>
      <b-carousel
        :interval="2500"
        controls
        indicators
        img-width="1024"
        img-height="480"
        style="text-shadow: 1px 1px 2px #333;">
        <b-carousel-slide>
          <img
            slot="img"
            class="d-block m-auto"
            width="1024"
            height="480"
            src="https://picsum.photos/1024/480/?image=50"
            alt="image slot">
        </b-carousel-slide>
        <b-carousel-slide>
          <img
            slot="img"
            class="d-block m-auto"
            width="1024"
            height="480"
            src="https://picsum.photos/1024/480/?image=51"
            alt="image slot">
        </b-carousel-slide>
      </b-carousel>
    </b-container>

    <b-container class="mt-3">
      <b-card-group deck>
        <b-card img-top img-src="https://picsum.photos/720/300/?image=55">
          <b-card-text>Thief</b-card-text>
        </b-card>
        <b-card img-top img-src="https://picsum.photos/720/300/?image=54">
          <b-card-text>Minoria</b-card-text>
        </b-card>
        <b-card img-top img-src="https://picsum.photos/720/300/?image=53">
          <b-card-text>Gears</b-card-text>
        </b-card>
        <b-card img-top img-src="https://picsum.photos/720/300/?image=52">
          <b-card-text>Frostpunk</b-card-text>
        </b-card>
      </b-card-group>
    </b-container>

    <b-container class="mt-3">
      <b-row class="d-flex align-items-center">
        <fa-icon :icon="fireIcon"/>
        <span class="ml-2 text-secondary">
          <strong>Hot Sellers</strong>
        </span>
      </b-row>
      <hr>
      <b-row>
        <b-col cols="6">
          <b-row class="mb-3">
            <b-col>
              <b-card  img-top img-src="https://picsum.photos/720/300/?image=56">
                <b-card-text>Thief</b-card-text>
              </b-card>
            </b-col>
            <b-col>
              <b-card  img-top img-src="https://picsum.photos/720/300/?image=57">
                <b-card-text>Frostpunk</b-card-text>
              </b-card>
            </b-col>
          </b-row>
          <b-row>
            <b-col>
              <b-card  img-top img-src="https://picsum.photos/720/300/?image=58">
                <b-card-text>Minoria</b-card-text>
              </b-card>
            </b-col>
            <b-col>
              <b-card  img-top img-src="https://picsum.photos/720/300/?image=55">
                <b-card-text>Gears</b-card-text>
              </b-card>
            </b-col>
          </b-row>          
        </b-col>
        <b-col cols="6">
          <b-card  img-top img-src="https://picsum.photos/720/395/?image=51">
            <b-card-text>Thief</b-card-text>
          </b-card>
        </b-col>
      </b-row>
    </b-container>

    <b-container class="mt-3">
         <b-row class="d-flex align-items-center">
        <fa-icon :icon="DiscoverIcon"/>
        <span class="ml-2 text-secondary">
          <strong>Discover Games</strong>
        </span>
      </b-row>
      <hr>
      <template v-if="userCount === 0">
        <b-spinner label="Yükleniyor..."></b-spinner>
      </template>
      <template v-else>
        <b-card v-for="user in users" :key="user.id" :img-src="`https://placekitten.com/100/100/?image=${user.id}`" img-left class="mb-3">
          <b-card-text>
            #{{ user.id }} - {{ user.company.catchPhrase }}
          </b-card-text>
        </b-card>
      </template>
    </b-container>

    <b-container class="mt-3">
      <b-row class="d-flex align-items-center">
        <fa-icon :icon="newsIcon"/>
        <span class="ml-2 text-secondary">
          <strong>News</strong>
        </span>
      </b-row>
      <hr>
      <b-card-group deck>
        <b-card img-top img-src="https://picsum.photos/720/300/?image=55">
          <b-card-text>Thief</b-card-text>
        </b-card>
        <b-card img-top img-src="https://picsum.photos/720/300/?image=54">
          <b-card-text>Frostpunk</b-card-text>
        </b-card>
        <b-card img-top img-src="https://picsum.photos/720/300/?image=53">
          <b-card-text>Gears</b-card-text>
        </b-card>
      </b-card-group>
    </b-container>
  </div>
</template>


<script>
import axios from 'axios'
import { faChevronDown, faPen, faSearch, faFire, faNewspaper, faPager } from '@fortawesome/free-solid-svg-icons'

export default {
  name: 'app',
  data () {
    return {
      chevronDown: faChevronDown,
      penIcon: faPen,
      searchIcon: faSearch,
      fireIcon: faFire,
      newsIcon: faNewspaper,
      users: []
    }
  },
  mounted () {
    axios.get('https://jsonplaceholder.typicode.com/users')
      .then(res => this.users = res.data)
  },
  computed: {
    userCount () {
      return this.users.length
    }
  }
}
</script>

<style>
span {
  display: block;
}
</style>
