<template>
  <div>
    <ul>
        <li v-for="(obj,item) of usuarios" :key="item">
             <nuxt-link 
                :to="`fotos/${obj.id}`">
                {{obj.name}} - {{obj.id}}
             </nuxt-link>
        </li>
    </ul>
  </div>
</template>
<script>
    import axios from 'axios';
export default {
  data() {
    return {
      usuarios: []
    };
  },
  async asyncData({isDev, route, store, env, params, query, req, res, redirect, error}) {
      try {
          let data = await axios.get('http://localhost:1337/user/index')
          const usuarios=data.data.data
      console.log(data.data.data)
      return {usuarios}
    } catch (error) {
        console.log(error)
        return {
            error:error
        }
    }  
  },
};
</script>