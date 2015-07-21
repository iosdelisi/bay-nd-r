A Cydia repository template. This template contains sample on how you can easily make depiction pages without replicating your html pages. The pages are styled using [Bootsrap](http://getbootstrap.com/) which is really easy to use. You can see how it looks like by visiting [this sample repo](https://supermamon.github.io/Reposi3/) on your desktop or mobile phone.
3	
4	Most data for this repo is stored on XML files and are loaded on the depiction page dynamically. See the guide below on how to set it up. Note that this guide doesn't cover creating .deb files but will briefly cover assiging depictions.
5	
6	## How to install this template
7	
8	### 1. Download
9	The latest release will always be [here](https://github.com/supermamon/Reposi3/archive/master.zip).
10	
11	### 2. Extract
12	Extract the contents into a subfolder on your website. If you're using [Github Pages](https://pages.github.com/), it should be under `username.github.io/repo`. You can change `repo` to anything you want like `cydia` for example. So your repo url would be `https://username.github.io/cydia`. For this guide we'll assume that you are using github your repo url is `https://username.github.io/repo`.
13	
14	#### 3. Personalize
15	Edit `Release` file. Modify the items pointed by `<--`
16	    
17	    Origin: Reposi3  <-- 
18	    Label: Reposi3   <--
19	    Suite: stable
20	    Version: 1.0
21	    Codename: ios
22	    Architectures: iphoneos-arm
23	    Components: main
24	    Description: Reposi3 - a cydia repo template  <--
25	
26	#### 4. Your repo is ready.
27	At this point your repo is basically ready to be added into Cydia. You can also visit your repo's homepage by going to `https://username.github.io/repo/`. It will come with 2 sample packages, Old Package and New Package. Each of the packages have a link on this page pointing to their depictions. Next guide will show you how to assign and customize your depiction pages.
28	
29	
30	## Depiction pages for your packages
31	
32	#### 1. A basic depiction page
33	Let's start with a simple one. First, of course, add your `.deb` files into the `debs` folder. Then, inside the `depictions` folder, duplicate the folder `com.supermamon.oldpackage`. You will see 2 xml files -- `info.xml` and `changelog.xml`. Edit the 2 files and put in the information regarding you package. The tags are pretty much self-explanatory. Contact [@reposi3](https://twitter.com/reposi3) or [@supermamon](https://twitter.com/supermamon) for questions.
34	
35	`info.xml`. 
36	```xml
37	<package>
38		<id>com.supermamon.oldpackage</id>
39		<name>Old Package</name>
40		<version>1.0.0-1</version>
41		<compatibility>
42			<firmware>
43			    <miniOS>5.0</miniOS>
44				<maxiOS>7.0</maxiOS>
45				<otherVersions>unsupported</otherVersions>
46				<!--
47				for otherVersions, you can put either unsupported or unconfirmed
48				-->
49			</firmware>
50		</compatibility>
51		<dependencies></dependencies>
52		<descriptionlist>
53			<description>This is an old package. Requires iOS 7 and below..</description>
54		</descriptionlist>
55		<screenshots></screenshots>
56		<changelog>
57			<change>Initial release</change>
58		</changelog>
59		<links></links>
60	</package>
61	```
62	Edit `changelog.xml`.
63	```xml
64	<changelog>
65		<changes>
66			<version>1.0.0-1</version>
67			<change>Initial release</change>
68		</changes>
69	</changelog>
70	```
71	
72	#### 2. Edit the depiction footer data
73	This data are the links that appear at the bottom of every depication. The data is stored in `repo.xml` at the root folder of your repo.
74	
75	```xml
76	<repo>
77		<footerlinks>
78			<link>
79				<name>Follow me on Twitter</name>
80				<url>https://twitter.com/reposi3</url>
81				<iconclass>glyphicon glyphicon-user</iconclass>
82			</link>
83			<link>
84				<name>I want this depiction template</name>
85				<url>https://github.com/supermamon/Reposi3</url>
86				<iconclass>glyphicon glyphicon-thumbs-up</iconclass>
87			</link>
88		</footerlinks>
89	</repo>
90	```
91	
92	#### 3. Link the depiction page to your Packages file.
93	Your depiction like should look like this:
94	```text
95	Depiction: https://username.github.io/repo/depictions/?p=[idhere]
96	```
97	Replace `[idhere]` with your actual package id.
98	```text
99	Depiction: https://username.github.io/repo/depictions/?p=com.supermamon.oldpackage
100	```
101	#### 4. Almost there
102	Compress your Packages file to bzip2 and there you have it! In case you haven't done yet, add your repo `https://username.github.io/repo/` to cydia. One final touch is to update `index.html`. Look at line 18 and 19. Change line 18 into your own **brand** and line 19 to have your own URL. Line2 27-44 contains the list of packages. You can edit those too.
103	```html
104	16 <div class="container">
105	17 	<div class="well">
106	18 		<p><span class="text-primary"><b>Reposi3</span></b> is a Cydia repository template.</p>
107	19 		<a class="btn btn-sm btn-default" href="cydia://url/https://cydia.saurik.com/api/share#?source=https://supermamon.github.io/Reposi3/">Add to Cydia</a>
108	20 	</div>
109	21 </div>
110	```
111	
112	#### 5. ALL DONE!
113	**And there you have it! Your first package on your repo!**
114	
115	## What Next?
116	If you want to put more information on your depictions, see the other sample in `\depictions\com.supermamon.newpackage\`. This sample contains all the information that is supported.
117	
118	Also, this guide is mostly a work in progress. I'll add up more details soon -- screenshots, more samples, repo icon, etc. If you have any questions, contact [@reposi3](https://twitter.com/reposi3) or [@supermamon](https://twitter.com/supermamon).
