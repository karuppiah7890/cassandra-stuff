# Getting Started

For now I'm just simply getting started with Cassandra. Just reading the website. I'm also learning a bit of Redis. But I was doing too much of it and figured I could do with a slight change of topic and mindset and environment to not get bored with the monotonous thing ;)

https://duckduckgo.com/?t=ffab&q=apache+cassandra&ia=web

https://cassandra.apache.org/_/index.html

I was reading through https://cassandra.apache.org/_/index.html and it felt pretty cool !

I was downloading the PDF linked in the `Performant` section and Firefox showed me a security warning. Apparently the file is coming from a HTTP URL

I tried the HTTPS URL and that works too. I'm planning to create my first PR for Cassandra - for the Docs :D ;) [TODO]

https://vldb.org/pvldb/vol5/p1724_tilmannrabl_vldb2012.pdf link instead of http://vldb.org/pvldb/vol5/p1724_tilmannrabl_vldb2012.pdf

---

I just noticed the word `Masterless architecture` in https://cassandra.apache.org/_/index.html and was wondering what's that supposed to mean. I mean, if there are multiple masters / primaries, that still means there's a concept of master / primary. Does it mean there's no concept of primary AT ALL in Cassandra? Hmm, something to checkout and then think about [TODO]

I noticed the section on Quality

```
Focus on Quality

To ensure reliability and stability, Cassandra is tested on clusters as large as 1,000 nodes and with hundreds of real world use cases and schemas tested with replay, fuzz, property-based, fault-injection, and performance tests.
```

It's cool that they have lot of tests! Of course! I would like to write some tests for Cassandra ;) :D

---

```
Distributed

Cassandra is suitable for applications that can’t afford to lose data, even when an entire data center goes down. There are no single points of failure. There are no network bottlenecks. Every node in the cluster is identical.
```

Hmm. Every node is identical? 🤔 Something to checkout! [TODO]

---

And oh yeah, Cassandra 4.0 is here it seems! https://cassandra.apache.org/_/blog/Apache-Cassandra-4.0-is-Here.html , something to checkout ! [TODO]

---

When I was checking out where the repo is, I was looking for repo link but couldn't find it on the site. I guess I should have just searched it. But anyways, in the journey I found these -

https://cassandra.apache.org/_/community.html#how-to-contribute

https://cassandra.apache.org/_/community.html

I also found there's a Kubernetes SIG ! https://cwiki.apache.org/confluence/display/CASSANDRA/Cassandra+Kubernetes+SIG It's perfect ! I think I would love to know how databases, distributed databases and distributed storage systems run on top of Kubernetes and other similar orchestration platforms ! :D

https://cassandra.apache.org/_/community.html#discussions

I also noticed the SIG update here in main page https://cassandra.apache.org/_/index.html - https://cassandra.apache.org/_/blog/Cassandra-and-Kubernetes-SIG-Update-2.html

and other stuff https://cassandra.apache.org/_/blog/Apache-Cassandra-Changelog-8-June-2021.html

---

Gonna get the code first!

https://duckduckgo.com/?t=ffab&q=cassandra+code&ia=web

https://github.com/apache/cassandra

Finally! Got the mirror at least!

Got the contribution link -

https://cassandra.apache.org/_/development/index.html

Some good suggestions on contributing -

```
Here are some suggestions for ways to contribute:

- Update the documentation
- Answer questions on the user list
- Review and test a submitted patch
- Investigate and fix a reported bug
- Create unit tests and d-tests

```

I'm wondering what `d-tests` are, haha

I think this list makes so much sense! I mean, I know that investigating and fixing bugs are a great way to contribute and learn about a project. Also recently I have been wondering about reviewing PRs too, on some projects. But yeah, I may not know much to review very deep, but I could read the code, understand it, suggest / ensure basic things like - ensuring tests pass etc

Answering questions and updating docs - it requires quite some knowledge actually !

The link for `patches` on this doc is broken ! this doc https://cassandra.apache.org/_/development/index.html

it says https://cassandra.apache.org/_/development/index.html#:patches.adoc

The link is under https://cassandra.apache.org/_/development/index.html#updating-documentation

Another broken link - https://cassandra.apache.org/_/development/index.html#:testing.adoc

and another https://cassandra.apache.org/_/development/index.html#:patches.adoc

both under - https://cassandra.apache.org/_/development/index.html#create-unit-tests-and-dtests

I think I need to fix the broken links [TODO]. Riase issue and fix it. Right links are - https://cassandra.apache.org/_/development/patches.html and below one -

https://cassandra.apache.org/_/development/testing.html

And also add a way to get the link to the different sections of the doc, like, to get this link - https://cassandra.apache.org/_/development/index.html#create-unit-tests-and-dtests , I had to do "inspect" on the web page and use the `id` of the header tag and append it to the URL. Hmm. [TODO] Raise issue and fix it

---

I found out what a D Test is. Like I thought. A distributed test ;)

https://github.com/apache/cassandra-dtest

---

Found the issue hub for Cassandra !

https://issues.apache.org/jira/issues/?jql=project%20%3D%20CASSANDRA%20AND%20Complexity%20%3D%20%22Low%20Hanging%20Fruit%22%20and%20status%20!%3D%20resolved

And of course I already have an account in ASF JIRA. I forgot about it. I need to also tag it as ASF and not just Apache JIRA in my password manager

I was checking if my issue is already reported there, hmm

https://issues.apache.org/jira/browse/CASSANDRA-16838?jql=project%20%3D%20CASSANDRA%20AND%20text%20~%20%22doc%20broken%20link%22

I just saw this

https://issues.apache.org/jira/browse/CASSANDRA-16838

Some new website stuff -

https://issues.apache.org/jira/browse/CASSANDRA-16761

Hmm

Created an issue !! :D

https://issues.apache.org/jira/browse/CASSANDRA-16870

---

ASF Slack!

https://s.apache.org/slack-invite

https://infra.apache.org/slack.html

https://the-asf.slack.com/

Right, I need to contact someone to get access to the Slack, hmm. I'll just do that sometime, I guess

Join slack by getting an invite [TODO]

---

```bash
$ mkdir apache

$ cd apache

$ git clone git@github.com:karuppiah7890/cassandra.git
Cloning into 'cassandra'...
remote: Enumerating objects: 348035, done.
remote: Counting objects: 100% (1186/1186), done.
remote: Compressing objects: 100% (503/503), done.
remote: Total 348035 (delta 465), reused 951 (delta 351), pack-reused 346849
Receiving objects: 100% (348035/348035), 350.32 MiB | 8.33 MiB/s, done.
Resolving deltas: 100% (201475/201475), done.
Updating files: 100% (4116/4116), done.

$ cd cassandra

$ git remote add upstream git@github.com:apache/cassandra.git

$ git remote set-url upstream --push no_push

$ git remote -v
origin	git@github.com:karuppiah7890/cassandra.git (fetch)
origin	git@github.com:karuppiah7890/cassandra.git (push)
upstream	git@github.com:apache/cassandra.git (fetch)
upstream	no_push (push)
```

---

I couldn't find where the site code is

```bash
cassandra $ fd adoc
cassandra $ ls doc/
Dockerfile		convert_yaml_to_rst.py	make.bat		source
Makefile		cql3			native_protocol_v3.spec
README.md		docker-compose.yml	native_protocol_v4.spec
SASI.md			gen-nodetool-docs.py	native_protocol_v5.spec
cassandra $ gst
On branch trunk
Your branch is up to date with 'origin/trunk'.

nothing to commit, working tree clean
cassandra $ g branch -a
* trunk
  remotes/origin/HEAD -> origin/trunk
  remotes/origin/cassandra-1.0
  remotes/origin/cassandra-1.1
  remotes/origin/cassandra-1.2
  remotes/origin/cassandra-2.0
  remotes/origin/cassandra-2.1
  remotes/origin/cassandra-2.2
  remotes/origin/cassandra-3.0
  remotes/origin/cassandra-3.11
  remotes/origin/cassandra-4.0
  remotes/origin/trunk
cassandra $ gco cassandra-4.0
Branch 'cassandra-4.0' set up to track remote branch 'cassandra-4.0' from 'origin'.
Switched to a new branch 'cassandra-4.0'
cassandra $ gst
On branch cassandra-4.0
Your branch is up to date with 'origin/cassandra-4.0'.

nothing to commit, working tree clean
cassandra $ ls doc
Dockerfile		convert_yaml_to_rst.py	make.bat		source
Makefile		cql3			native_protocol_v3.spec
README.md		docker-compose.yml	native_protocol_v4.spec
SASI.md			gen-nodetool-docs.py	native_protocol_v5.spec
cassandra $ ls doc/
Dockerfile               convert_yaml_to_rst.py   make.bat                 source/
Makefile                 cql3/                    native_protocol_v3.spec
README.md                docker-compose.yml       native_protocol_v4.spec
SASI.md                  gen-nodetool-docs.py     native_protocol_v5.spec
cassandra $ ls doc/
Dockerfile               convert_yaml_to_rst.py   make.bat                 source/
Makefile                 cql3/                    native_protocol_v3.spec
README.md                docker-compose.yml       native_protocol_v4.spec
SASI.md                  gen-nodetool-docs.py     native_protocol_v5.spec
cassandra $ fd adoc
cassandra $ ls
CASSANDRA-14092.txt		build-shaded-dtest-jar.sh	lib
CHANGES.txt			build.properties.default	pylib
CONTRIBUTING.md			build.xml			redhat
LICENSE.txt			conf				relocate-dependencies.pom
NEWS.txt			debian				src
NOTICE.txt			doc				test
README.asc			eclipse_compiler.properties	tools
TESTING.md			examples
bin				ide
cassandra $ rg "Becoming a contributor"
cassandra $ rg "Contributors are individuals"
cassandra $
```

Looks like doc is a separate thing

https://cassandra.apache.org/doc/latest/

And when I click on pencil edit button, it takes me to

https://github.com/polandll/cassandra/edit/trunk/doc/modules/ROOT/pages/index.adoc

And that `modules` directory is not there in my git repo, hmm

and older docs look like this

https://cassandra.apache.org/doc/3.11/index.html

I think site code maybe somewhere else? Hmm

https://github.com/apache?q=cassandra&type=&language=&sort=

Right, there's a separate repo, hmm

https://github.com/apache/cassandra-website

```bash
$ git clone git@github.com:karuppiah7890/cassandra-website.git
Cloning into 'cassandra-website'...
remote: Enumerating objects: 33507, done.
remote: Counting objects: 100% (4389/4389), done.
remote: Compressing objects: 100% (326/326), done.
remote: Total 33507 (delta 4277), reused 4122 (delta 4055), pack-reused 29118
Receiving objects: 100% (33507/33507), 48.31 MiB | 6.93 MiB/s, done.
Resolving deltas: 100% (28578/28578), done.
Updating files: 100% (8561/8561), done.

$ cd cassandra-website

$ git remote add upstream git@github.com:apache/cassandra-website.git

$ git remote set-url upstream --push no_push

$ git remote -v
origin	git@github.com:karuppiah7890/cassandra-website.git (fetch)
origin	git@github.com:karuppiah7890/cassandra-website.git (push)
upstream	git@github.com:apache/cassandra-website.git (fetch)
upstream	no_push (push)
```

```bash
cassandra-website $ rg "Contributors are individuals"
cassandra-website $ rg "Becoming a contributor"
```

Wow, no results, hmm

Next steps, check about the steps to contribute and about how to build

https://github.com/apache/cassandra-website#development-cycle

https://github.com/apache/cassandra-website#building-prerequisites

And the `src` has a `index.html` that seems to make sense, hmm!
