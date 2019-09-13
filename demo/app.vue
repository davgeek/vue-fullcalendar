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
let demoEvents = [
    {
        title : 'Lunfel 1/27-2/2',
        start : '2019-09-27',
        end : '2019-09-29'
    },
  ];

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