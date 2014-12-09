# Glacier Hands-on

Glacier has Java, .NET language binding, or REST API. Here's an example illustrating the use of AWS Javascript SDK to create vault and upload archive to it.

```javascript
var AWS = require('aws-sdk');
var Q = require('q');
var configData = require('./config.json');

var setAWSconfig = function() {
  // global config: update AWS security tokens
  AWS.config.update({
    accessKeyId: configData.accessKeyId,
    secretAccessKey: configData.secretAccessKey
  });

  AWS.config.update({region: configData.region});  
}

var name = 'testVaultBySDK';

var createVaultAndUploadSample = function() {

  setAWSconfig();

  createVault(name)
    .then(uploadSampleArchive)
    .then(describeVault)
    .catch(function(err) {
      console.log("Error happened during processing");
    })
    .done();
};

var createVault = function(vaultName) {

  var glacier = new AWS.Glacier()
    , deferred = Q.defer();

  glacier.createVault({vaultName: vaultName}, function(err, data) {
    if (!err) {
      console.log("Created vault: " + vaultName);
      deferred.resolve(vaultName);
    } else {
      console.log("ERROR creating vault: " + err);
      deferred.reject(err);
    }
  });
  return deferred.promise;
};

var uploadSampleArchive = function(vaultName) {
  var glacier = new AWS.Glacier()
    , deferred = Q.defer()
    , buffer = new Buffer(1.5 * 1024 * 1024) // 1.5MB buffer
    , params = {vaultName: vaultName, body: buffer};

  glacier.uploadArchive(params, function(err, data) {
    if (err) {
      console.log("Error uploading archive!", err);
      deferred.reject(err);
    } else {
      console.log("Uploaded Archive, ID:", data.archiveId);
      deferred.resolve(vaultName);
    }
  });
  return deferred.promise;
};

var describeVault = function(vaultName) {
  var glacier = new AWS.Glacier()
    , deferred = Q.defer()
    , params = {vaultName: vaultName};

  glacier.describeVault(params, function(err, data) {
    if (err) {
      console.log("ERROR describeVault", err);
      deferred.reject(err);
    } else {
      console.log("The vault status is: ", data);
      deferred.resolve(vaultName);
    }
  });
  return deferred.promise;

}

createVaultAndUploadSample();
```