<template>
  <div class="comparision">
    <canvas
    canvas-id="g2_canvas"
    id="g2_canvas"
    class="canvas"
    style="width: 375px; height: 300px;"
    v-on:click = "tapName"
  />
  <div id="g2"></div>
  </div>
</template>

<script>
import G2 from '@antv/g2'
//import G2Canvas from './g2.js'
import G2Canvas from '@geekhacker/g2'

export default {
  name: 'comparision',
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
    renderG2Canvas(){
      const chart = new G2Canvas.Chart({
        el: document.getElementById('g2_canvas'),
        width: 187.5,
        height: 75,
        padding: [10, 10, 10, 25],
      })
      //console.log(this.rawData)
      this.processChart(chart)
    },
    renderG2(){
      const chart = new G2.Chart({
        container: 'g2',
        width: 187.5,
        height: 75,
        padding: [10, 10, 10, 25],
      })
      //console.log(this.rawData)
      this.processChart(chart)
    },
    processChart(chart){
      chart.source(this.rawData);
      chart.interval().position('city*tem').color('city');
      chart.on('interval:click',ev=>{console.log(ev)});
      //console.log(chart)
      chart.legend({ position: 'top', textStyle: { fontSize: '10'}})
      chart.render();
    }
  },
  mounted(){
    this.renderG2Canvas()
    this.renderG2()
  }

}
</script>

