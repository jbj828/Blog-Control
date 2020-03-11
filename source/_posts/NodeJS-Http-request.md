---
date: '2020/3/11 14:46:25'
tags:
  - NodeJS
categories:
  - NodeJS
thumbnail: ''
permalink: ''
title: HTTP/HTTPS Request without library
---

HTTP Request without library

<!-- more -->


This is the low level access to the NodeJS. Without using library, we can also get the http/https request.

```
const https = require("https");

const url = 'https://api.darksky.net/forecast/924276c331b8a398db96364a44fd10a2/40,-50?units=si'

const request = https.request(url, (response) => {
    let data = '';

    response.on('data', (chunk) => {
        data = data + chunk.toString();
    })

    response.on('end', () => {
        const body = JSON.parse(data);
        console.log(body);
    })
})

request.on('error', (error) => {
    console.log('An error', error)
})

request.end();
```

This is the console result
```
{
  latitude: 40,  
  longitude: -50,
  timezone: 'Etc/GMT+3',
  currently: {
    time: 1583906798,
    summary: 'Partly Cloudy',
    icon: 'partly-cloudy-night',
    precipIntensity: 0,
    precipProbability: 0,
    temperature: 16.48,
    apparentTemperature: 16.48,
    dewPoint: 12.34,
    humidity: 0.77,
    pressure: 1028,
    windSpeed: 5.67,
    windGust: 9.52,
    windBearing: 248,
    cloudCover: 0.41,
    uvIndex: 0,
    visibility: 16.093,
    ozone: 330.9
  },
  hourly: {
    summary: 'Windy in the afternoon and evening.',
    icon: 'partly-cloudy-day',
    data: [
      [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object],
      [Object]
    ]
  },
  daily: {
    summary: 'Rain on Friday through next Wednesday.',
    icon: 'rain',
    data: [
      [Object], [Object],
      [Object], [Object],
      [Object], [Object],
      [Object], [Object]
    ]
  },
  flags: {
    sources: [
      'cmc',   'gfs',
      'icon',  'isd',
      'madis', 'nam',
      'sref'
    ],
    'nearest-station': 0,
    units: 'si'
  },
  offset: -3
}
```