Client library for the thingspeak.com API
=========================================

ThingSpeak is an open source “Internet of Things” application and API to store and retrieve data from things using HTTP over the Internet or via a Local Area Network. With ThingSpeak, you can create sensor logging applications, location tracking applications, and a social network of things with status updates. https://thingspeak.com https://github.com/iobridge/ThingSpeak

This repository is contains Python module that helps in talking to ThingSpeak API.

.. warning::

   This is a complete redesign of the library as compared to v0.1.1.
   Previous version is available in https://github.com/bergey/thingspeak
   and is no longer maintained.

   To install old version you can still use::

      pip install thingspeak==0.1.1


Example usage
-------------

It is possible to view the channel directly:

.. code-block:: shell

   $ thingspeak -q -r 2 9
   {
     "channel": {
       "created_at": "2010-12-14T01:20:06Z",
       "description": "Netduino Plus connected to sensors around the house",
       "field1": "Light",
       "field2": "Outside Temperature",
       "id": 9,
       "last_entry_id": 9680334,
       "latitude": "40.44",
       "longitude": "-79.9965",
       "name": "my_house",
       "updated_at": "2016-02-09T20:11:45Z"
     },
     "feeds": [
       {
         "created_at": "2016-02-09T20:11:31Z",
         "entry_id": 9680333,
         "field1": "199",
         "field2": "29.978768577494691"
       },
       {
         "created_at": "2016-02-09T20:11:45Z",
         "entry_id": 9680334,
         "field1": "213",
         "field2": "29.723991507430998"
       }
     ]
   }

Or through Python interface:

.. code-block:: Python

   >>> import thingspeak
   >>> ch = thingspeak.Channel(9)
   >>> ch.get({'results': 2})
   u'{"channel":{"id":9,"name":"my_house","description":"Netduino Plus connected to sensors around the house","latitude":"40.44","longitude":"-79.9965","field1":"Light","field2":"Outside Temperature","created_at":"2010-12-14T01:20:06Z","updated_at":"2016-02-09T20:13:45Z","last_entry_id":9680342},"feeds":[{"created_at":"2016-02-09T20:13:30Z","entry_id":9680341,"field1":"199","field2":"29.554140127388536"},{"created_at":"2016-02-09T20:13:45Z","entry_id":9680342,"field1":"193","field2":"27.855626326963908"}]}'


For valid parameters refer to https://de.mathworks.com/help/thingspeak/channels-and-charts.html
