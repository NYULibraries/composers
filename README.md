# NYU Archivesspace DO Plugin
***


This is an ArchivesSpace plugin that extends the ArchivesSpace API to allow real time Digital Object look ups.

This plugin was developed against ArchivesSpace v1.5.1 by [Hudson Molonglo](https://github.com/hudmol/composers) for New York University with generous funding from the Mellon Foundation.

**How to Install**

$ cd /path/to/archivesspace/plugins

$ git clone https://github.com/NYULibraries/Archivesspace-DO-Plugin

Enable the plugin by editing the file in config/config.rb: AppConfig[:plugins] = ['some_exisiting plugin', 'composers']

Add a proxy for your backend url in config/config.rb: AppConfig[:backend_proxy_url] = "http://example.com:8089"

**Archiveit Integration**

The API includes an endpoint, /plugins/composers/archiveit, that generates a json response that can be consumed by Archive-It. 

**example**

A URL can be created that passes the resource identifier for a resource described in archivesspace as a parameter to the /plugins/composers/archiveit endpoint:

http://demo.nyu.edu:8089/plugins/composers/archiveit?resource_id=mss.460

The endpoint will generate a json response that can be consumed by Archive-It by entering the the url in the 'Related Archival Materials' field in the metadata for a seed url archived in Archive-It. 

{ <br/> 
  "title":"Adele Fournet Papers on the Bit Rosie Web Series",<br/>
  "extent":"33 Digital Objects",<br/>
  "display_url":"http://demo.nyu.edu:8089/plugins/composers/summary?resource_id=mss.460&format=html"<br/>
}<br/>

**Endpoint Summary**

The Archivesspace DO plugin adds three GET endpoints to the 

GET /plugins/composers/archiveit
provides a json response with basic data about a collection for integration with Archive-It 

GET /plugins/composers/summary

GET /plugins/composers/detailed

**Demo Application**

A demo application that consumes the data from the API is available at: [https://github.com/NYULibraries/Composers-API-Demo](https://github.com/NYULibraries/Composers-API-Demo)
