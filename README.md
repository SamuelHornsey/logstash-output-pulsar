# Logstash Pulsar Output

A simple logstash pulsar output plugin. Will send logstash messages into an apache pulsar topic.

## Building

To build the plugin for use in logstash

```bash
> bundle install

> bundle exec rake vendor
```

Once dependencies are installed build the gem

```bash
> gem build logstash-output-pulsar.gemspec
```

## Logstash Configuration

Once the gem has been built you can install the gem with logstash. Copy the gem file to /usr/share/logstash directory and run

```bash
> logstash-plugin install /usr/share/logstash/logstash-output-pulsar-{{VERSION}}.gem
```

Use the following conf for your logstash config

```conf
output {
    pulsar {
        bootstrap_servers => "pulsar://pulsar-server:port"
        batch_max_publish_delay => 300
        batch_max_size => 300
        topic_id => "persistent://pulsar-topic"
    }
}
```