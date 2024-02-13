<script>
import axios from 'axios'
import Navbar from './components/Navbar.vue'
import Char from './components/CharacterList.vue'
import FormChar from './components/FormChar.vue'

export default {
  components: {
    Navbar,
    Char,
    FormChar
  },
  data() {
    return {
      baseUrl: 'http://localhost:3000',
      username: 'Dadang Konelo',
      characterList: [],
      page: 'home',
      editChar: {}
    }
  },
  methods: {
    changePage(page) {
      this.page = page
    },

    fetchCategories() {
      // anggap saja dia nge axios
    },

    async fetchCharacters() {
      try {
        const { data } = await axios({
          url: this.baseUrl + '/characters',
          method: 'get'
        })

        console.log(data, '<<<<< ke fetch')
        this.characterList = data
      } catch (err) {
        console.log(err)
      }
    },

    async deleteChar(id) {
      try {
        await axios.delete(this.baseUrl + '/characters/' + id)
        await this.fetchCharacters()
      } catch (error) {
        console.log(error, '<<<')
      }
    },

    async fetchCharById(id) {
      // console.log(id, '<<<< fetch by id')
      try {
        const { data } = await axios.get(this.baseUrl + '/characters/' + id)
        this.editChar = data
        this.page = 'edit'
      } catch (error) {
        console.log(error, '<<<<')
      }
    },

    async addCharacter(value) {
      console.log(value)
      try {
        await axios({
          url: this.baseUrl + '/characters',
          method: 'post',
          data: {
            name: value.name,
            imageUrl: value.imageUrl
          }
        })
        // this.fetchCharacters()
        this.changePage('home')
      } catch (err) {
        console.log(err)
      }
    }
  },

  created() {
    this.fetchCharacters()
  }
}
</script>

<template>
  <Navbar :username="username" @changePage="changePage" />

  <!-- ADD CHARACTER -->
  <FormChar
    :editChar="editChar"
    v-if="page === 'add' || page === 'edit'"
    :page="page"
    @addCharacter="addCharacter"
  />

  <!-- CHARACTERS LIST -->
  <Char
    v-if="page === 'home'"
    :characterList="characterList"
    @deleteChar="deleteChar"
    @fetchCharById="fetchCharById"
    @fetchCharacter="fetchCharacters"
  />
</template>

<style scoped></style>
