<template>
  <div>
  	<p>
  		Here is the demo of vue-fullcalendar, no jquery fullcalendar.js required!
  	</p>
    <full-calendar class="test-fc" :events="fcEvents" :noWorkables="[5,6]"
      first-day='1' locale="es"
      @changeMonth="changeMonth"
      @eventClick="eventClick"
      @dayClick="dayClick"
      @moreClick="moreClick">
        <template slot="fc-event-card" scope="p">
            <p><i class="fa"></i> {{ p.event.title }} pepepepep</p>
        </template>
        <!-- <template slot="fc-show-more-view">
          fc-show-more-view
        </template> -->
    </full-calendar>
  </div>
</template>
<script>
let demoEvents = [{"id":1,"metadata":"Día de la Revolución","start":"2019-11-18T00:00:00.000+0000","end":"2019-11-18T00:00:00.000+0000","type":"HOLIDAY","title":"Día de la Revolución","color":null,"employeeName":null,"canSee":true,"cssClass":["holiday"],"cellIndex":4,"isShow":true},{"id":99,"metadata":"Fuera de la ciudad para presentar un artículo en un congreso. Previamente acordado con Nancy. ","start":"2019-11-01T07:00:00.000+0000","end":"2019-11-01T15:00:00.000+0000","type":"LEAVE","title":"Laura Elena Cervantes Cervantes Permiso con goce de sueldo","color":"blue","employeeName":"Laura Elena Cervantes Cervantes","canSee":true,"cssClass":["blue"],"cellIndex":1,"isShow":true},{"id":101,"metadata":"Revisar pendientes","start":"2019-11-04T13:30:00.000+0000","end":"2019-11-04T16:00:00.000+0000","type":"LEAVE","title":"Aylin Fernanda Gonzalez Serna Trabajo Remoto","color":"teal","employeeName":"Aylin Fernanda Gonzalez Serna","canSee":true,"cssClass":["teal"],"cellIndex":1,"isShow":true},{"id":105,"metadata":"Tramites en ITSON","start":"2019-11-05T13:10:00.000+0000","end":"2019-11-05T14:10:00.000+0000","type":"LEAVE","title":"Néstor Arturo Zepeda Negrete Permiso con goce de sueldo","color":"blue","employeeName":"Néstor Arturo Zepeda Negrete","canSee":true,"cssClass":["blue"],"cellIndex":1,"isShow":true},{"id":116,"metadata":"Poder revisar pendientes de uADMIN2.0","start":"2019-11-06T00:00:00.000+0000","end":"2019-11-06T00:00:00.000+0000","type":"LEAVE","title":"Aylin Fernanda Gonzalez Serna Trabajo Remoto","color":"teal","employeeName":"Aylin Fernanda Gonzalez Serna","canSee":true,"cssClass":["teal"],"cellIndex":1,"isShow":true},{"id":132,"metadata":"Trabajare desde casa","start":"2019-11-08T00:00:00.000+0000","end":"2019-11-08T00:00:00.000+0000","type":"LEAVE","title":"David Lizarraga Martinez Trabajo Remoto","color":"teal","employeeName":"David Lizarraga Martinez","canSee":true,"cssClass":["teal"],"cellIndex":1,"isShow":true},{"id":121,"metadata":"Viaje - desde la 1:00 pm a 5:00 pm","start":"2019-11-08T00:00:00.000+0000","end":"2019-11-08T00:00:00.000+0000","type":"LEAVE","title":"Glenda Marisol Huidobro  Hernandez Permiso con goce de sueldo","color":"blue","employeeName":"Glenda Marisol Huidobro  Hernandez","canSee":true,"cssClass":["blue"],"cellIndex":2,"isShow":true},{"id":136,"metadata":"Trabajaré desde casa de 7AM a 3PM para concentrarme en la revisión de los algoritmos de regresión que se van a utilizar en los datos de los clientes de sistemas de facturación. ","start":"2019-11-11T00:00:00.000+0000","end":"2019-11-11T00:00:00.000+0000","type":"LEAVE","title":"Laura Elena Cervantes Cervantes Trabajo Remoto","color":"teal","employeeName":"Laura Elena Cervantes Cervantes","canSee":true,"cssClass":["teal"],"cellIndex":1,"isShow":true},{"id":103,"metadata":"Buen día , me gustaría solicitar esta semana para trabajarlo remoto desde casa de mis padres\n\nDe necesitarse que algún día de estos venga no hay problema \nSaludos","start":"2019-11-11T08:00:00.000+0000","end":"2019-11-15T17:00:00.000+0000","type":"LEAVE","title":"Janet Lepe Fernández Trabajo Remoto","color":"teal","employeeName":"Janet Lepe Fernández","canSee":true,"cssClass":["teal"],"cellIndex":2,"isShow":true},{"id":21,"metadata":"Esto es real","start":"2019-11-15T00:00:00.000+0000","end":"2019-11-22T00:00:00.000+0000","type":"LEAVE","title":"Nancy Priscila Chávez Arredondo Vacaciones","color":"pink","employeeName":"Nancy Priscila Chávez Arredondo","canSee":true,"cssClass":["pink"],"cellIndex":3,"isShow":true},{"id":51,"metadata":"Porque me forzaron","start":"2019-11-15T00:00:00.000+0000","end":"2019-11-15T00:00:00.000+0000","type":"LEAVE","title":"Carlos Adán Ramírez Almeida Vacaciones","color":"pink","employeeName":"Carlos Adán Ramírez Almeida","canSee":true,"cssClass":["pink"],"cellIndex":4,"isShow":true},{"id":58,"metadata":"Vacaciones cumple my love.","start":"2019-11-15T00:00:00.000+0000","end":"2019-11-15T00:00:00.000+0000","type":"LEAVE","title":"Alejandra Ibarra Valenzuela Vacaciones","color":"pink","employeeName":"Alejandra Ibarra Valenzuela","canSee":true,"cssClass":["pink"],"cellIndex":5,"isShow":true},{"id":107,"metadata":"Saldré de la ciudad ese día, y ocuparía salir a la 1 de la tarde, lo platique con Nancy y estaria reponiendo las horas antes de ese día  ","start":"2019-11-15T13:00:00.000+0000","end":"2019-11-15T18:00:00.000+0000","type":"LEAVE","title":"Arturo Damian Ocampo Baca Permiso con goce de sueldo","color":"blue","employeeName":"Arturo Damian Ocampo Baca","canSee":true,"cssClass":["blue"],"cellIndex":6,"isShow":true}];

export default {
	data () {
		return {
            name:'Sunny!',
            fcEvents : demoEvents
        }
	},
  methods : {
    'changeMonth' (start, end, current) {
      console.log('changeMonth', start.format(), end.format(), current.format())
    },
    'eventClick' (event, jsEvent, pos) {
       console.log('eventClick', event, jsEvent, pos)
    },
    'dayClick' (day, jsEvent) {
      console.log('dayClick', day, jsEvent)
    },
    'moreClick' (day, events, jsEvent) {
      console.log('moreCLick', day, events, jsEvent)
    }
  },
  components : {
    'full-calendar' : require('src/fullCalendar')
  }
}
</script>
<style lang='scss'>
  .app{
    color:green;
  }
</style>