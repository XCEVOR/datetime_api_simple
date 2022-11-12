# datetime_api_simple

The purpose of this project is to quickly print the current time in Flutter using the basic API of the "DateTime" class.

## Getting Started

Part 1. Three methods that simply output the current time.

intl: ^0.17.0

import 'package:intl/intl.dart';

  // CASE 1. DateTime directly
  final myDateTimeNowToString = DateTime.now().toString();

  // CASE 2. Custom pattern format
  final myDateTimeNowForFormat = DateTime.now();
  late String formattedMyDateTimeNow1 =
      DateFormat('yyyy/MM/dd - HH:mm:ss').format(myDateTimeNowForFormat);

  // CASE 3. Standard format
  final String formattedMyDateTimeNow2 =
      DateFormat.yMMMEd('en-US').add_jms().format(DateTime.now());


            // OUTPUT 1. DateTime directly
            Text(myDateTimeNowToString),

            // OUTPUT 2. Custom pattern format
            Text(formattedMyDateTimeNow1),

            // OUTPUT 3. Standard format
            Text(formattedMyDateTimeNow2),



Part 2. A method that continuousely outputs the current time.

import 'dart:async';

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


            // UPDATED every second
            Text(
              _timeString,
              style: TextStyle(
                color: Colors.purple,
                fontSize: 32,
                fontWeight: FontWeight.bold,
              ),
            ),