---
title: "Grouping_data"
include_toc : true
---
### Grouping data using d3.nest


    
         let store = []
         d3.csv("routes.csv").then(d => groupby(d))

         let ky = "AirlineID"
         let kname = "AirlineName"
         let kc = "AirlineCountry"


         let byid = []
         let results = d3.select("#out1")
         let x = ""
         let gd = []


         function groupby(d) {
             store = Array.from(d)
             alert("done")
             byid = d3.nest()
                 .key(function (d) { return d.AirlineID; })
                 .key(function (d) { return d.AirlineName; })
                 .rollup(function (v) {
                     return {
                         count: v.length,
                         country:
                             v.AirlineCountry

                     };
                 })
                 .entries(store);
             byid.forEach(function (d) {
                 d.AirlineID = d.key;
                 d.Airline = d.values[0];
                 d.AirlineName = d.Airline.key
                 d.count = d.Airline.value.count
             });
             byid.flatMap(e => (e))

             document.getElementById("out2").innerHTML=JSON.stringify(byid)

### another section
