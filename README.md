# Logstash Plugin Output - Enhanced Kafka (efile)

This is an input plugin for [Logstash](https://github.com/elasticsearch/logstash).

It is more or less follows the built-in logstash kafka input except it differs in a couple key ways:
  1. The plugin listens for offsets tagged to events and keeps a running track of the largest offsets from each source
  2. The plugin will write the offsets to a file upon a graceful shutdown 


## Disclaimer

Again, this plugin more or less follows the logstash [kafka-output plugin code](https://github.com/logstash-plugins/logstash-output-kafka). The majority of the code is the same; I just injected some small amounts of code. 

Also note, that this must be used in combination with some sort of 'enhanced' input plugin. 

## Documentation

Since this code is just juryrigged from the logstash file plugin, the [logstash official documentation](https://www.elastic.co/guide/en/logstash/current/plugins-inputs-file.html) covers most of the config possibilities 

The key differences you should see in the config file are:
  - `offset_path` - where the offsets will be stored after shutdown. This requires an *absolute* path to a *file*. If undeclared the plugin will assume that it does not have any offsets
  - `offset_indicator` - the attribute in the event that indicates from where/who does the offset come from. 
