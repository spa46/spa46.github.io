---
title: "GStreamer"
header:
  image: images/main_doc1_1024.jpg
  teaser: images/main_doc1_1024.jpg
  caption: "Photo credit: [**pixabay**](https://pixabay.com)"
tag:
  - gstreamer
  - porting gstreamer
categories:
  - System
---

{% include toc %}

GStreamer

API:
https://developer.gnome.org/gtk3/

Adaptive Streaming:
https://coaxion.net/blog/2014/05/http-adaptive-streaming-with-gstreamer/

tutorial:
http://docs.gstreamer.com/display/GstSDK/Basic+tutorial+2%3A+GStreamer+concepts

-------------------------------

	GStreamer-CRITICAL **: gst_element_set_state: assertion 'GST_IS_ELEMENT <element>' failed
	GStreamer-CRITICAL **: gst_element_get_bus: assertion 'GST_IS_ELEMENT <element>' failed
	GStreamer-CRITICAL **: gst_bus_timed_pop_filtered: assertion 'GST_IS_BUS <bus>' failed
	GStreamer-CRITICAL **: gst_object_unref: assertion 'object=!NULL' failed
	GStreamer-CRITICAL **: gst_element_set_state: assertion 'GST_IS_ELEMENT <element>' failed
	GStreamer-CRITICAL **: gst_object_unref: assertion 'object=!NULL' failed

To troubleshoot above, These are the steps I checked:

1. Probably the code is compiled as C++, which is a bit more strict at enum casts. Try replacing: GST_MESSAGE_ERROR | GST_MESSAGE_EOS with (GstMessageType)(GST_MESSAGE_ERROR | GST_MESSAGE_EOS)


2. There is high probability that the line:

		pipeline = gst_parse_launch ("playbin2 uri=file://E:/test_1.MOV", NULL);

	returns NULL and and the rest of errors are result of this.

	Why it could return NULL? <br>
	There could be many reasons. For example, you might not installed plugin such as "playbin2".

	Try this:

	Pass a pointer to GError structure as second parameter to gst_parse_launch (it has a message field which can give you some hint)

		Pass --gst-debug-level=4 or even higher as a commandline parameter
		to analyze your error throughout console clearly when running your program.
