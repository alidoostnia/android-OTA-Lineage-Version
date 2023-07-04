Updater
=======
Simple application to download and apply OTA packages.


Server requirements
-------------------
The app sends `GET` requests to the URL defined by the `updater_server_url`
resource (or the `lineage.updater.uri` system property) and expects as response
a JSON with the following structure:
```json
{
  "response": [
    {
      "datetime": 1230764400,
      "filename": "ota-package.zip",
      "id": "5eb63bbbe01eeed093cb22bb8f5acdc3",
      "romtype": "nightly",
      "size": 314572800,
      "url": "https://example.com/ota-package.zip",
      "version": "15.1"
    }
  ]
}
```

The `datetime` attribute is the build date expressed as UNIX timestamp.  
The `filename` attribute is the name of the file to be downloaded.  
The `id` attribute is a string that uniquely identifies the update.  
The `romtype` attribute is the string to be compared with the `ro.lineage.releasetype` property.  
The `size` attribute is the size of the update expressed in bytes.  
The `url` attribute is the URL of the file to be downloaded.  
The `version` attribute is the string to be compared with the `ro.lineage.build.version` property.  

Additional attributes are ignored.
