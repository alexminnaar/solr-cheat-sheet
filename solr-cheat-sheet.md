#Solr Cheat Sheet

###Stopping and Starting Solr
```cd solr-x/bin```

```./solr start``` to start

```./solr stop``` to stop

###Accessing Solr Admin
```localhost:8983:/solr/admin```

###Querying from Admin
Select core > Query

###Query By URL
e.g. ```http://localhost:8983/solr/collection1/select?q=<query terms>&wt=<how to display results e.g. json, xml, etc.>&sort=<field to sort by>%20<asc OR desc>```


###User Interface
```http://localhost:8983/solr/browse```

### /select Interface vs /browse Inferface

```/select``` interface uses the lucene query parser.  Defaults to searching text.  Therefore use ```CopyField``` in ```schema.xml``` to copy the fields you want to query into the text field.

e.g. ```<copyField source="features" dest="text"/>``` in ```schema.xml```

```/browse``` interface uses edismax query parser.  Query fields are defined in the collection's ```solrconfig.xml``` file.  This allows edismax queries to search multiple fields.

e.g.
```<str name="qf">
          text^0.5 name^1.2 sku^1.5 id^10.0 manu^1.1 cat^1.4
          title^10.0 description^5.0 keywords^5.0 author^2.0 resourcename^1.0
       </str>
       ```
       