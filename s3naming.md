# The World of S3

The naming syntax has been designed to accommodate Infochimps data, and to make it easy to find and store data in S3.

## Bucket Conventions and Rules

Following the style guide is important to perpetuate consistency and to set a precedence in future cataloging and indexing of our data.

**Naming Conventions**

1. Underscoring naming convention is used, absolutely no camel casing y’all 

2. Everything is to remain lowercase 

3. When naming, dots are to be used over dashes.  Unless, there is an extra special reason to do so, that you’ll have to run by the cataloger. Dots are preferred because S3’s practice is to translate bucket names into DNS. An example of an exceptional cause is when a name may have an underscore that we have to switch to a dash

4. All bucket names have the suffix chimpy.us/...

5. Abbreviating, a practice you may have witnessed or practiced in past naming, is being cut in almost all cases.  For example, it was common practice to write tw in place of twitter or soc for social.  Unless, there is an extra special reason to do so, that you’ll have to run by the cataloger.

**S3 Rules**

< 10,000 objs/bucket
~ 1 gb partitions
> 100 MB   
< 4.5 GB (a dvd)


##Buckets

### scraped.[ ].chimpy.us/...

**What is scraped?**

Freshly freshly scraped data direct from an API response, formatted as json and stored compressed is what will live in a scraped.[].chimpy.us bucket. ****rawd or ripd data. 


<pre><code>agent.org/realm/source/data version or partition/anything</pre></code>

****choose data version or partition
****Anything might be changed to Automatic instead, or another term that does not sound so arbitrary.

<pre><code>agent.org/</pre></code>
 
An agent is the method used to conceive the bucket’s contents.  For example the contents that are living in scraped.chimpy.us/..., were scraped.  The org is the organization responsible for the fabrication of the bucket.  In our case, it will always be chimpy.us.
****Should we change agent to....tool?

<pre><code>realm/source/</pre></code>

The realm is the world where the original data resides.  The source is the pipe through which Infochimps gets the data.

<pre><code>data version or partition/anything</pre></code>

The data version will vary according to the data type.  For some types of data, it will be the year, month, and date the scrape occurred, e.g. yyyymmdd, for others it might only be the month and year and for for others it could be another reasonable method of presenting versions of data.  In some cases it is he	lpful to split things up by date because writes are going to be happening to the same place
this means that if i’ve processed, batch processed, done everything up to 2012 februrary, this way of paritioning means i only have to come in and do 2012 march

<pre><code>anything</pre></code>

Anything means the information after the data version will be automatically assigned by a machine.  that might be up to the machine, will probably not be up to us

****Anything might be changed to Automatic instead, or another term that does not sound so arbitrary.

**Examples:**

_scraped.chimpy.us/twitter/api_
_scraped.chimpy.us/twitter/stream/201220207/anything_
_scraped.chimpy.us/twitter/search_
_scraped.chimpy.us/foursquare/stream_


### [ ].models.chimpy.us/..

**What are models?**

Models are fully parsed, ready to be downloaded, and interacted.  It is likely they will be in a compressed TSV’s format.

realm.models/underscored model name/data version or partition/at most 1 nest ([files] or [dir/files])

realm.models/
The realm is the world where the original data resides, twitter, for example. 

model_name/
The model name may sometimes be underscored, for example when it is a country, city, or state, i.e. geographical names.

data version or partition/anything
The data version will vary according to the data type.  For some types of data, it will be the year, month, and date the scrape occurred, for others it might only be the month and year and for for others it could be another reasonable method of presenting versions of data.  helpful to split things up by date because writes are going to be happening to the same place
this means that if i’ve processed, batch processed, done everything up to 2012 februrary, this way of paritioning means i only have to come in and do 2012 march

/[files] or [dir/files]
The files will contain total sorted items, when available, and at most one nest.

Examples:
twitter.models.chimpy.us/tweet/data
twitter.models.chimpy.us/tweet/20110207
twitter.models.chimpy.us/tweet/20110207/[file]
twitter.models.chimpy.us/trstrank/201102
foursquare.models.chimpy.us/name of model (ie place)
coregeo.models.chimpy.us/



have to split things because of permission issues, can’t split permissions

there will never be a sequel bucket, things will graduate


**What is in the sandbox bucket?**
The sandbox bucket is a place to play freely, in other words, not a place save irreplaceable work.  Any developer who wants to play in the sandbox may create their own sub-directory (suggested name: SourceForge ID, or given name + family initial), but project directories are recommended over personal directories as they discourage collaboration.  A project-specific sub-directory should be created for each new project.  Get as messy as you want, but make it in your own area and be aware that your mess could be cleaned up at short notice or without notice.  There is only one sandbox bucket, therefore permissions will be the same for all users.

**What is in the misc bucket?**
Nothing new will go in the misc bucket, and this bucket will be phased out eventually.  Currently it will serve as the bucket where data without homes will be moved.  Once that data is destroyed or re-homed accordingly the bucket will no longer serve a purpose.

<pre><code>misc.[grandfathered from current dirs name]/handle/[simple]</pre></code>

**What is in a logs bucket?**
Logs will have multiple logs buckets.  It is very important for logs not to collide or break anything.  It is imperative that one have the ability to go in and know exactly where the logs are, therefore a relatively direct copy of the source domain hierarchy is necessary.  
The same permissions of these will stay for each machine, so for security reasons we need different log buckets.


like where it was in the source

<pre><code>cluster.logs.chimpy.us/physical machine/agent/log_path</pre></code>


<pre><code>cluster.logs.chimpy.us/</pre></code>

The cluster name 

<pre><code>physical machine/</pre></code>
	
The physical machine's name, the agent or source, the version.  The reason that the machine’s name is repeated to secure that the right cluster is writing the set of logs, and so so we do not have to worry about it getting tramped on by another set of logs.	

note: Everything to the right of machine-version-#, i.e. gordo-datanode-0, gordo-datanode-1, etc are all going to make the same files.



<pre><code>[anything]</pre></code>
<pre><code>[anything]</pre></code>


Anything might be changed to Automatic instead, or another term that does not sound so arbitrary.

everything after the var/log is named after the program


Examples:
_bonobo.logs.chimpy.us/bonobo-master-0/elasticsearch/var/log/elasticsearch/20120305/..._



**What is in the snapshots bucket?**

Backup files are inside of snapshots.

****db-snapsots or database.backups or backups?

db-snapshots.chimpy.us 

db-snapshots.chimpy.us/cluster/es/...    - not going to get big because it is updated once a time, not historical data

**What is in an AMI bucket?**

In the AMI bucket you will find the image for our machines.




<pre><code>ami.chimpy.us</pre></code>


**What about the downloadable data?**

The old standards will be grandfathered in for downloadable data, like the yuploader and also george related data and infochimps hackboxen.  

####Future buckets...
* reports
* scrapereqs  - que for what is being scraped should be put somewhere
* datascience
* intermediate output/data science - flip wants a science cluster...no one but flip needs it, he is going to make its own readme, saying why he named it and what exactly can go in there
intermediate output stuff will hopefully go away, we need them temporarily, like multigraph...it’s part of travis’s cleanup.  will hopefully start doing things where we don’t need an intermediate output and some stuff will land int he science clustery thingy
* george and georgebackup