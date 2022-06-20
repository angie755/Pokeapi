<template>
    <div id="PokeItem" v-if="datos != null">
        <el-card :body-style="{ padding: '0px' }">
            <img 
                :src=datos.sprites.front_default
                class="image" :style="{backgroundColor: colorType(datos.types[0].type.name)}">
            <div style="padding: 14px;">
                <span>{{dato.name}}</span>
            </div>
        </el-card>
    </div>
    
</template>

<script>
import axios from 'axios';
export default {
    name:'PokeItem',
    methods:{
        colorType(type){
            switch(type){
                case 'grass': return '#48d0b1';
                case 'fire': return '#fb6c6c';
                case 'water': return '#76bdfe';
                case 'bug': return '#f7786b';
                case 'normal': return '#b1736c';
            }
        }
    },
    props:{
        dato:Object
    },
    data(){
        return{
            datos:null
        }
    },
    mounted(){
        axios.get(this.dato.url).then(response=>{
            this.datos = response.data;
        });
    }
}
</script>

<style>
.time {
    font-size: 13px;
    color: #999;
  }
  
  .bottom {
    margin-top: 13px;
    line-height: 12px;
  }

  .button {
    padding: 0;
    float: right;
  }

  .image {
    width: 100%;
    display: block;
  }

  .clearfix:before,
  .clearfix:after {
      display: table;
      content: "";
  }
  
  .clearfix:after {
      clear: both
  }
</style>