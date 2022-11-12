# datetime_api_simple

The purpose of this project is to quickly print the current time in Flutter using the basic API of the "DateTime" class.

## Getting Started

Part 1. Three methods that simply output the current time.
<pre>
intl: ^0.17.0
</pre>
<pre>
import 'package:intl/intl.dart';
</pre>
<pre>
  // CASE 1. DateTime directly
  final myDateTimeNowToString = DateTime.now().toString();

  // CASE 2. Custom pattern format
  final myDateTimeNowForFormat = DateTime.now();
  late String formattedMyDateTimeNow1 =
      DateFormat('yyyy/MM/dd - HH:mm:ss').format(myDateTimeNowForFormat);

  // CASE 3. Standard format
  final String formattedMyDateTimeNow2 =
      DateFormat.yMMMEd('en-US').add_jms().format(DateTime.now());
</pre>
<pre>
            // OUTPUT 1. DateTime directly
            Text(myDateTimeNowToString),

            // OUTPUT 2. Custom pattern format
            Text(formattedMyDateTimeNow1),

            // OUTPUT 3. Standard format
            Text(formattedMyDateTimeNow2),
</pre>


Part 2. A method that continuousely outputs the current time.
<pre>
import 'dart:async';
</pre>
<pre>
  late String _timeString;
  @override
  void initState() {
    _timeString = _formatDateTime(DateTime.now());
    Timer.periodic(Duration(seconds: 1), (Timer t) => _getTime());
    super.initState();
  }

  void _getTime() {
    final DateTime now = DateTime.now();
    final String formattedDateTime = _formatDateTime(now);
    setState(() {
      _timeString = formattedDateTime;
    });
  }

  String _formatDateTime(DateTime dateTime) {
    return DateFormat('yyyy-MM-dd hh:mm:ss a').format(dateTime);
  }
</pre>
<pre>
            // UPDATED every second
            Text(
              _timeString,
              style: TextStyle(
                color: Colors.purple,
                fontSize: 32,
                fontWeight: FontWeight.bold,
              ),
            ),
</pre>

<img height="600" src="https://user-images.githubusercontent.com/111336041/201457351-9d30d9e1-3c32-4b15-9d7b-b0315cafbc47.gif"/>
