<template>
   <div>
  

    <table border="1" class="table table-bordered table-sm ">
      <thead>
        <th>Carpeta</th>
        <th>Dominio</th>
        <th>Palabras clave</th>
        <th>Proyecto</th>
        <th>Nombre servidor</th>
        <th>Subproyecto</th>
        <th>Namespace</th>
        <th>Infraestructura de despliegue</th>
        <th>Link de contenido</th>
        
      </thead>
      <tbody v-for="(item, capeta) in items" :key="capeta">
        <tr v-for="(itemCarp, index) in item" :key="index">
        
          <td>{{ itemCarp.Carpeta }}</td>
          <td>{{ itemCarp.Dominio }}</td>
          <td>
              <ul v-for="(itempc, index) in itemCarp.PalabrasClave" :key="index">
                <li>{{ itempc }}</li>
              </ul>
          </td>
          <td>{{ itemCarp.Proyecto }}</td>
          <td>{{ itemCarp.NombreServidor }}</td>
          <td>{{ itemCarp.Subproyecto }}</td>
          <td>{{ itemCarp.Namesapce }}</td>
          <td>
            <ul v-for="(itempc, index) in itemCarp.Infradespliegue" :key="index">
              <li>{{ itempc }}</li>
              </ul>
          </td>
           <td><button type="button" class="btn btn-primary" data-toggle="button" aria-pressed="false" autocomplete="off">
  Ver mas
</button></td>




          

        </tr>
      </tbody>
    </table>
    
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Principal',
  data () {
    return {
      mensaje: 'Sin mensaje!',
      items: []
    }
  },
  methods: {
    getMensaje () {
      const path = 'http://192.168.0.105:5000/projects/klczb7u4f5ombypc7t5zxeknhlvf3cthjd4kmkh7nawfo6ac42pq/juancho270'
      axios.get(path).then((respuesta) => {
        this.items = respuesta.data
        console.log(respuesta.data)
        console.log(this.items)
      })
      .catch((error) => {
        console.log(error)
      })
    }
  },
  created () {
    this.getMensaje()
  }
}
</script>
