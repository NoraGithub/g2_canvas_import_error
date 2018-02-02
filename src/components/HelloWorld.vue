<template>
  <div class="hello">
    <canvas
    canvas-id="canvas"
    id="canvas"
    class="canvas"
    style="width: 375px; height: 300px;"
    v-on:click = "tapName"
  />
  </div>
</template>

<script>
import G2 from './g2.js'
//import G2 from '@antv/g2'

export default {
  name: 'HelloWorld',
  data () {
    return {
      rawData: [
      { tem: 10, city: 'tokyo' },
      { tem: 4, city: 'newYork' },
      { tem: 3, city: 'berlin' }
    ]
    }
  },
  methods:{
    tapName (event) {
      var e = {
        currentTarget: event.currentTarget,
        target: event.target,
        clientX: event.detail.x,
        clientY: event.detail.y,
        type: "click",
        _origin: event
      }
      //document.getElementById('canvas').emit('click',e)

      console.log(event,e)
    },
  },
  mounted(){
    const chart = new G2.Chart({
      el: document.getElementById('canvas'),
      width: 180,
      height: 80,
      padding: [10, 10, 10, 25],
    })
    //console.log(this.rawData)
    chart.source(this.rawData);
    chart.interval().position('city*tem').color('city');
    chart.on('interval:click',ev=>{console.log(ev)});
    console.log(chart)
    chart.legend({ position: 'top', textStyle: { fontSize: '10'}})
    chart.render();

  }

}
</script>

