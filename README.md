# sairam


Topic Users

ccloud ksql app create app-stream --api-key HXOAIALDMOLUPWC2 --api-secret rgQ2tQYlW/5iwsOMh1WwIyhbtqUP0pHYNMgxyqt9McbF2nJ0eigSZbafcLQdzruP

CREATE STREAM riderLocations (profileId VARCHAR, latitude DOUBLE, longitude DOUBLE)
  WITH (kafka_topic='users', value_format='json', partitions=1);
  
  
  CREATE STREAM userstream (registertime LONG, userid STRING, regionid STRING,gender STRING) WITH WITH (kafka_topic='inputtopic1', value_format='avro', partitions=2);
  
  
  {
  "@type": "currentStatus",
  "statementText": "CREATE STREAM USERSTREAM (REGISTERTIME DOUBLE, USERID STRING, REGIONID STRING, GENDER STRING) WITH (KAFKA_TOPIC='inputtopic1', KEY_FORMAT='KAFKA', PARTITIONS=2, VALUE_FORMAT='AVRO');",
  "commandId": "stream/`USERSTREAM`/create",
  "commandStatus": {
    "status": "SUCCESS",
    "message": "Stream created",
    "queryId": null
  },
  "commandSequenceNumber": 4,
  "warnings": []
}
  
  CREATE STREAM pagestream (viewtime LONG, userid STRING, pageid STRING) WITH WITH (kafka_topic='inputtopic2', value_format='avro', partitions=2);
  
  
  {
  "@type": "currentStatus",
  "statementText": "CREATE STREAM PAGESTREAM (VIEWTIME DOUBLE, USERID STRING, PAGEID STRING) WITH (KAFKA_TOPIC='inputtopic2', KEY_FORMAT='KAFKA', PARTITIONS=2, VALUE_FORMAT='AVRO');",
  "commandId": "stream/`PAGESTREAM`/create",
  "commandStatus": {
    "status": "SUCCESS",
    "message": "Stream created",
    "queryId": null
  },
  "commandSequenceNumber": 2,
  "warnings": []
}
  
  CREATE STREAM pageviews_enriched AS
  SELECT users_original.id AS userid, pageid, regionid, gender
  FROM pageviews_original
  LEFT JOIN users_original
    ON pageviews_original.userid = users_original.id
  EMIT CHANGES;
 ---------------------------------------------------------------------
    CREATE STREAM newstream AS
  SELECT userstream.id AS userid, pageid, regionid, gender
  FROM pagestream
  LEFT JOIN users_original
    ON pagestream.userid = userstream.id
  EMIT CHANGES;
  
  
  
  https://docs.ksqldb.io/en/0.18.0-ksqldb/developer-guide/ksqldb-reference/create-stream-as-select/
  
  https://docs.confluent.io/platform/current/ksqldb/tutorials/basics-control-center.html
