webevents
=========

A JS utility to easily collect events from websites for metrics

Check the test.html for usage details. event_reactor is the the function that does the work.
Make sure to add jQuery js files and collector.js.

  <script src="jquery-2.0.3.min.js"></script>
	<script src="collector.js"></script> 
	<script>
	$( document ).ready(function() {
		
		//event_reactor: event_name, event, src_object_id, reactor, data_obj_ids
		//event_name: just a name for you to track
		//event: should be a jQuery event like click, hover, submit etc.
		//src_object_id: id of the html element to which we want to bind event listener. Should be in jQuery selector format like #input_box1
		//reactor: this is the js function that will get event details. Use logging_reactor or write your own
		//data_onj_ids: array of ids of the html element whose data needs to be recorder. The id should be in jQuery selector format.
    	event_reactor("page_submit", "click", "#submit", "logging_reactor", ["#fname", "#lname"]);
	});
	</script>

The event_reactor will capture events. You can write your own reactor function based on how you want to react to the event.
For example, you might want to do a http post to a REST server.

The template for your custom reactor is shown inside collector.js 
  
  function example_new_reactor(ev) {
	  //Do what you want!
  }
