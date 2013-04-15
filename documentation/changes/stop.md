---
layout: default
title: Change stop
---

<!-- ====================================================== -->
<!-- GENERATED BY ChangeDocGenerator DO NOT MODIFY MANUALLY -->
<!-- ====================================================== -->

  <script>
  $(function() {
    $( "#changelog-tabs" ).tabs();
  });
</script>

# Change: 'stop'

Stops Liquibase execution with a message. Mainly useful for debugging and stepping through a changelog

## Available Attributes ##

<table>
<tr><th>Name</th><th>Description</th><th>Required&nbsp;For</th><th>Since</th></tr>
<tr><td style='vertical-align: top'>dbms</td><td>null</td><td style='vertical-align: top'></td><td style='vertical-align: top'>3.0</td></tr>
<tr><td style='vertical-align: top'>message</td><td>Message to output when execution stops</td><td style='vertical-align: top'></td><td style='vertical-align: top'></td></tr>
</table>

<div id='changelog-tabs'>
<ul>
    <li><a href="#tab-xml">XML Sample</a></li>
    <li><a href="#tab-yaml">YAML Sample</a></li>
    <li><a href="#tab-json">JSON Sample</a></li>
  </ul>
<div id='tab-xml'>
{% highlight xml %}
<changeSet author="liquibase-docs" id="stop-example">
    <stop dbms="h2, oracle" message="What just happened???"/>
</changeSet>
{% endhighlight %}
</div>
<div id='tab-yaml'>
{% highlight yaml %}
changeSet:
  id: stop-example
  author: liquibase-docs
  changes:
  - stop:
      dbms: h2, oracle
      message: What just happened???

{% endhighlight %}
</div>
<div id='tab-json'>
{% highlight json %}
{
  "changeSet": {
    "id": "stop-example",
    "author": "liquibase-docs",
    "changes": [
      {
        "stop": {
          "dbms": "h2, oracle",
          "message": "What just happened???"
        }
      }]
    
  }
}

{% endhighlight %}
</div>
</div>


## Database Support

<table style='border:1;'>
<tr><th>Database</th><th>Notes</th><th>Auto Rollback</th></tr>
<tr><td>Cache</td><td><b>Supported</b></td><td>No</td></tr>
<tr><td>DB2</td><td><b>Supported</b></td><td>No</td></tr>
<tr><td>DB2i</td><td><b>Supported</b></td><td>No</td></tr>
<tr><td>Derby</td><td><b>Supported</b></td><td>No</td></tr>
<tr><td>Firebird</td><td><b>Supported</b></td><td>No</td></tr>
<tr><td>H2</td><td><b>Supported</b></td><td>No</td></tr>
<tr><td>HyperSQL</td><td><b>Supported</b></td><td>No</td></tr>
<tr><td>Informix</td><td><b>Supported</b></td><td>No</td></tr>
<tr><td>MySQL</td><td><b>Supported</b></td><td>No</td></tr>
<tr><td>Oracle</td><td><b>Supported</b></td><td>No</td></tr>
<tr><td>PostgreSQL</td><td><b>Supported</b></td><td>No</td></tr>
<tr><td>SAP DB</td><td><b>Supported</b></td><td>No</td></tr>
<tr><td>SQL Server</td><td><b>Supported</b></td><td>No</td></tr>
<tr><td>SQLite</td><td><b>Supported</b></td><td>No</td></tr>
<tr><td>Sybase</td><td><b>Supported</b></td><td>No</td></tr>
<tr><td>Sybase Anywhere</td><td><b>Supported</b></td><td>No</td></tr>
</table>