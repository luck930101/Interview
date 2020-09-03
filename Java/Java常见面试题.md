Java􁶎􁦶􀲋􀙙
􁍓􀭯
1.1􀌵tomcat􀯔􁚆􀕽􀛸􀷆􁉘
1.2􀌵JVM􀯔􁚆􀕽􀛸􀷆􁉘
1.3􀌵Mysql􀯔􁚆􀕽􀛸􀷆􁉘
2.1􀌵SpringCloud􁶎􁦶􀷆􁉘
2.2􀌵SpringBoot􁶎􁦶􀷆􁉘
2.3􀌵Dubbo􁶎􁦶􀷆􁉘
4.1􀌵Spring􁶎􁦶􀷆􁉘
4.2􀌵SpringMVC􁶎􁦶􀷆􁉘
4.3􀌵MyBatis􁶎􁦶􀷆􁉘
5.1􀌵􀚓􀫲􀭗􁴴􁁞􁶎􁦶􀷆􁉘
􀓞􀌵􀯔􁚆􀕽􀛸􁶎􁦶􀓫􀻄
􀔫􀌵􀮙􀹐􀛓􀺝􀺅􁶎􁦶􀓫􀻄
􀓣􀌵􀬚􀝎􁖫􁑕􁹛􁕆􁶎􁦶􀓫􀻄
􀢥􀌵􀭏􁃠􀻛􀺝􁶎􁦶􁷌􀓫􀻄
􀔲􀌵􀚓􀫲􀭗􁶎􁦶􀓫􀻄
5.2􀌵􀚓􀫲􀭗􁭗􁦔􁶎􁦶􀷆􁉘
5.3􀌵􀚓􀫲􀭗􀷄􀴝􀬪􁶎􁦶􀷆􁉘
􀾋􀷈
1.1􀌵tomcat􀯔􁚆􀕽􀛸􀷆􁉘
1􀌵􀖦􀯆􀻏􁕳tomcat􁧣􀕽
1. JVM􀝇􀷄􁧣􀕽􀒓 -Xms<size> 􁤒􁐏 JVM 􀚡􀦤􀛸􀤞􁌱􀥟􀩜􀒅 -
Xmx<size> 􁤒􁐏 JVM 􀤞􁌱􀹋􀥟􊧊􀌶􁬯􀓷􀓻􊧊􁌱􀥟􀩜􀓞􁛱􀻑􀴝􁵱􁥝􁬰􁤈􁦡
􁗝􀌶􀭮􀬫􁊠􁑕􀬧􁵱􁥝􁌱􀙖􀨂􁩻􀚊􀤞􁌱􀹋􀥟􊧊􀷸􁡦􀳙􀹢􀩪􀕿􀵉􁐏􀙖􀨂􁃤􀚊􀒅
􀬚􀓬􀩕􁛘􀬫􁊠􀹐􀛓􀫄􁃛􀌶􀢩􀾌􀓞􁛱􀭌􁦓􀤞􁌱􀹋􀥟􊧊􁦡􁗝􀔅􀝢􁊠􀙖􀨂􁌱􀹋􀥟􊧊􁌱80%􀌶􀣁 catalina.bat 􀓾􀒅􁦡􁗝 JAVA_OPTS='-Xms256m-
Xmx512m' 􀒅􁤒􁐏􀚡􀦤􀛸􀙖􀨂􀔅256MB􀒅􀝢􀕦􀖵􁊠􁌱􀹋􀥟􀙖􀨂􀔅512MB􀌶
2.􁐬􁊠DNS􀺱􁧃
􀭮web􀬫􁊠􁑕􀬧􀝻􁥝􁦕􀭯􀨮􀲁􁒒􁌱􀗞􀯳􀷸􀒅􀨙􀔞􀕿􁦕􀭯􀨮􀲁􁒒􁌱IP􀣈􀣎􀱲
􁘏􁭗􁬦􀤒􀝷􀹐􀛓􀢏􀺱􀲤􀹢􀢏􀝷􁫨􀴘􀔅IP􀣈􀣎􀌶DNS􀺱􁧃􁵱􁥝􀜛􁊠􁗑􁕶􀒅􀬚
􀓬􀛱􀳡􀝢􁚆􀕗􀮉􀥚􀮉􁬱􁌱􀹐􀛓􀢏􀱲􁘏􀓧􁩸􀖢􁊠􁌱􀹐􀛓􀢏􀓤􀝄􁞴􀝐􀩒􀬫􁌱IP
􁌱􁬦􁑕􀒅􁬯􀻏􀕿􁁾􁘙􀓞􀨧􁌱􀷸􁳵􀌶􀔅􀔧􁁾􁴻DNS􀺱􁧃􀩒􀯔􁚆􁌱􀭽􀟥􀱯􀕪􀝢
􀕦􀙉􁳮DNS􀺱􁧃􀒅􀷜􀭗􀸎􀗥􀶯 server.xml 􀷈􀕯􀓾􁌱 enableLookups 􀝇
􀓞􀌵􀯔􁚆􀕽􀛸􀓫􀻄
􀷄􊧊􀒓
Tomcat4
<Connector
className="org.apache.coyote.tomcat4.CoyoteConnector"port="80"
minProcessors="5"maxProcessors="75"enableLookups="false"redire
ctPort="8443"
acceptCount="100"debug="0"connectionTimeout="20000"
useURIValidationHack="false"disableUploadTimeout="true"/>
Tomcat5
<Connectorport="80"maxThreads="150"minSpareThreads="25"
maxSpareThreads="75"enableLookups="false"redirectPort="8443"
acceptCount="100"debug="0"connectionTimeout="20000"
disableUploadTimeout="true"/>
3.􁧣􀷆􁕚􁑕􀷄
􁭗􁬦􀬫􁊠􁑕􀬧􁌱􁬳􀴳􀢏 􀒁Con nector􀒂 􁬰􁤈􀯔􁚆􀴴􀚫􁌱􁌱􀝇􀷄􀸎􀚠􀭌􁌱
􀥒􁉘􁧗􀿢􁌱􁕚􁑕􀷄􀌶 Tomcat 􀖵􁊠􁕚􁑕􀿰􀛒􁭛􀟥􀬫􁭛􀬶􀹶􀥒􁉘􁧗􀿢􀌶􀣁
Java􀓾􁕚􁑕􀸎􁑕􀬧􁬩􁤈􀷸􁌱􁪠􀮆􀒅􀸎􀣁􀓞􀓻􁑕􀬧􀓾􀓨􀙌􀨙􀴴􀚫􁕚􁑕􀷫􀙉
􁌱􀌵􁚆􀥜􁇿􁒈􁬩􁤈􁌱􀕤􁎱􀾧􀌶􀨙􀕪􀙈􀕁􁍘􀝶􁌱􀣈􀣎􁑮􁳵􀌶􀥚􁕚􁑕􀬆􀛗􁑕􀬧
􀞧􀙟􀚊CPU􀹋􀥟􀚥􁊠􁈲􁌱􁹛􀶴􁑕􀬧􀒅􀖵􁑮􁳳􀷸􁳵􀗛􀳮􀹋􀖗􀒅􀕗􁘒􀴳􀹅􀥚􁌱
􁧗􀿢􀌶
Tomcat4 􀓾􀝢􀕦􁭗􁬦􀗥􀶯 minProcessors 􀞾 maxProcessors 􁌱􊧊􀹶􀴴
􀚫􁕚􁑕􀷄􀌶􁬯􀔶􊧊􀣁􀨞􁤰􀝸􀩪􀫪􁕪􁦡􀨧􀔅􁼕􁦊􊧊􀬚􀓬􀸎􁪃􀥜􀖵􁊠􁌱􀒅􀖕􀸎
􁵋􁍳􁒊􁅩􁌱􀲘􀨻􁘒􀶯􀥟􁬯􀔶􊧊􀌶 minProcessors 􀹐􀛓􀢏􀞐􀛖􀷸􀚠􀭌􁌱􀥒
􁉘􁧗􀿢􁌱􁕚􁑕􀷄􀬫􁧆􁪃􀥜􀥒􁉘􀓞􀓻􀩜􁰁􁌱􁨮􁫹􀌶􀔞􀩪􀸎􁧔􀒅􀦇􀺎􀓞􀥠􀙖􀾯
􁑁􀕐􀝎􁊞5􀽺􀜔􀚋􀔪􀕯􀒅􀬚􀓬􀾯􀓻􁧗􀿢􀕱􀛓􀥒􁉘􁵱􁥝1􁑁􁰦􀒅􁮎􀔍􁶼􀘶􁦡􁗝
􁕚􁑕􀷄􀔅5􀩪􁪃􀥜􀔧􀌶􀖕􀣁􀖦􁌱􁒊􁅩􁦢􁳯􁰁􁫾􀥟􀷸􀩪􁵱􁥝􁦡􁗝􀹅􀥟􁌱􁕚􁑕
􀷄􀒅􀳰􀨧􀔅􀝇􀷄 maxProcessors 􁌱􊧊􀌶 maxProcessors 􁌱􊧊􀔞􀸎􀹍􀓤
􁴴􁌱􀒅􀬫􁴠􀾊􁁞􁰁􀓧􀝢􀴴􀚫􀒁􀱲􁘏􀯶􀰺􁌱􀹐􀛓􀶰􀚋􀒂􀒅􀕗􁘒􀩕􁛘􁩻􀚊􀔧􁡦
􀳙􀹢􀖵􁊠􀙖􀨂􁌱􀥟􀩜􀌶􀦇􀺎􁥝􀛒􀥟􀬚􀝎􁬳􀴳􀷄􀒅􀬫􀝶􀷸􀛒􀥟􁬯􀓷􀓻􀝇
􀷄􀌶 web server 􊧋􁦜􁌱􀹋􀥟􁬳􀴳􀷄􁬮􀝑􀚫􀔭􀶙􀖢􁔮􁕹􁌱􀙖􀻐􀝇􀷄􁦡􁗝􀒅
􁭗􀬉Windows􀸎2000􀓻􀫢􀝦􀒅Linux􀸎1000􀓻􀫢􀝦􀌶
􀣁 Tomcat5 􀩒􁬯􀔶􀝇􀷄􁬰􁤈􀔧􁧣􀷆􀒅􁧗􁍡􀓥􁶎􀪂􀯔􀒓
maxThreads Tomcat 􀖵􁊠􁕚􁑕􀹶􀥒􁉘􀴳􀶭􁌱􀾯􀓻􁧗􀿢􀌶􁬯􀓻􊧊􁤒􁐏
Tomcat􀝢􀚠􀭌􁌱􀹋􀥟􁌱􁕚􁑕􀷄􀌶
acceptCount 􀳰􀨧􀭮􀲅􀹍􀝢􀕦􀖵􁊠􁌱􀥒􁉘􁧗􀿢􁌱􁕚􁑕􀷄􁮷􁤩􀖵􁊠􀷸􀒅􀝢
􀕦􀶱􀚩􀥒􁉘􁴚􀚜􀓾􁌱􁧗􀿢􀷄􀒅􁩻􁬦􁬯􀓻􀷄􁌱􁧗􀿢􀩙􀓧􀔨􀥒􁉘􀌶
connnection Timeout 􁗑􁕶􁬳􀴳􁩻􀷸􀒅􀜔􀖖􀒓􀾺􁑁􀌶􁦡􁗝􀔅0􁤒􁐏􀿞􀓧
􁩻􀷸􀒅􁬯􀻏􁦡􁗝􀹍􁵌􀰋􁌱􀌶􁭗􀬉􀝢􁦡􁗝􀔅30000􀾺􁑁􀌶
minSpareThreadsTomcat 􀚡􀦤􀛸􀷸􀚠􀭌􁌱􁕚􁑕􀷄􀌶
maxSpareThreads 􀓞􀷮􀚠􀭌􁌱􁕚􁑕􁩻􁬦􁬯􀓻􊧊􀒅 Tomcat 􀩪􀕿􀙉􁳮􀓧􀙚
􁵱􁥝􁌱 socket 􁕚􁑕􀌶
􀹋􀦅􁌱􀷜􀭗􀸎􀥚􁦡􁗝􀙾􀽺􀬚􀓬􁬰􁤈􁁥􁦶􀒅􁥡􀩊􀟥􀬫􀷸􁳵􀞾􀙖􀨂􀖵􁊠􀰘􀙭􀌶
􀣁􀓧􀝶􁌱􀹢􀢏􀌵􀶙􀖢􁔮􁕹􀱲􁡦􀳙􀹢􁕟􀝳􁌱􀰘􀙭􀓥􀝢􁚆􀕿􀓧􀝶􀒅􁘒􀓬􀬚􀓧􀸎
􀲅􀹍􀕈􁌱web􁒊􁅩􁌱􁁞􁰁􁮷􀸎􀓞􀻏􁌱􀒅􀢩􀾌􁀌􀹍􀓞􀚏􀚔􁌱􀷜􀻜􀹶􁏟􀨧􁕚􁑕
􀷄􁌱􊧊􀌶
2􀌵􀦇􀖜􀛒􀥟comcat􁬳􀴳􀷄
􀣁 tomcat 􁯈􁗝􀷈􀕯 server.xml 􀓾􁌱 <Connector/>
􁯈􁗝􀓾􀒅􀞾􁬳􀴳􀷄􁍘􀙉􁌱􀝇􀷄􀹍􀒓
minProcessors 􀒓􀹋􀩜􁑮􁳳􁬳􀴳􁕚􁑕􀷄􀒅􁊠􀔭􀵉􁹛􁔮􁕹􀥒􁉘􀯔􁚆􀒅􁼕􁦊
􊧊􀔅10
maxProcessors 􀒓􀹋􀥟􁬳􀴳􁕚􁑕􀷄􀒅􀜨􀒓􀬚􀝎􀥒􁉘􁌱􀹋􀥟􁧗􀿢􀷄􀒅􁼕􁦊
􊧊􀔅75
acceptCount 􀒓􊧋􁦜􁌱􀹋􀥟􁬳􀴳􀷄􀒅􀬫􀥟􀔭􁒵􀔭 maxProcessors 􀒅􁼕
􁦊􊧊􀔅100
enableLookups 􀒓􀸎􀞈􀝍􀺱􀤒􀝷􀒅􀝐􊧊􀔅􀒓true􀱲false􀌶􀔅􀔧􀵉􁹛􀥒􁉘􁚆
􀛎􀒅􀬫􁦡􁗝􀔅false
connectionTimeout 􀒓􁗑􁕶􁬳􀴳􁩻􀷸􀒅􀜔􀖖􀒓􀾺􁑁􀌶􁦡􁗝􀔅0􁤒􁐏􀿞􀓧
􁩻􀷸􀒅􁬯􀻏􁦡􁗝􀹍􁵌􀰋􁌱􀌶􁭗􀬉􀝢􁦡􁗝􀔅30000􀾺􁑁􀌶
􀙌􀓾􀞾􀹋􀥟􁬳􀴳􀷄􁍘􀙉􁌱􀝇􀷄􀔅maxProcessors􀞾acceptCount􀌶􀦇􀺎􁥝􀛒
􀥟􀬚􀝎􁬳􀴳􀷄􀒅􀬫􀝶􀷸􀛒􀥟􁬯􀓷􀓻􀝇􀷄􀌶
web server 􊧋􁦜􁌱􀹋􀥟􁬳􀴳􀷄􁬮􀝑􀚫􀔭􀶙􀖢􁔮􁕹􁌱􀙖􀻐􀝇􀷄􁦡􁗝􀒅􁭗􀬉
Windows􀸎2000􀓻􀫢􀝦􀒅Linux􀸎1000􀓻􀫢􀝦􀌶tomcat5􀓾􁌱􁯈􁗝􁐏􀖺􀒓
<Connectorport="8080"
maxThreads="150"minSpareThreads="25"maxSpareThreads="75"
enableLookups="false"redirectPort="8443"acceptCount="100"
debug="0"connectionTimeout="20000"
disableUploadTimeout="true"/>
􀩒􀔭􀙌􀕜􁒒􀝗􁌱􀗅􀞍􁯈􁗝􀒅􀕦􀾌􁔄􀴵􀌶
3􀌵􀯆􀻏􀛒􀥟tomcat􁌱􀙖􀨂
􁸒􀘶􀼄􀺱􁑕􀬧􀹍􁀌􀹍􁴴􀙁􀾒􀮗􁈾
􁬯􀓻􁳯􁷌􀔆􁥝􁬮􀸎􁊧􁬯􀓻􁳯􁷌 java.lang.OutOfMemoryError:Java
heap space
􀭚􁩸􁌱􀌶􁒫􀓞􀽺􀚊􁈿􁬯􀻏􁌱􁌱􁳯􁷌􀕦􀝸􀒅􀭚􀝎􀔧􀙌􀕜􁌱􁳯􁷌􀌶􀣁􁗑􀓤􀓞􀺱
􀝢􁚆􀸎JAVA􁌱􀤞􀺾􁦡􁗝􀥡􀩜􁌱􀜻􀢩􀌶
􁪙􀴝􁗑􀓤􁌱􁒼􀻜􀥟􁛘􀹍􁬯􀓷􁐿􁥴􀙬􀷜􁀩􀒓
1􀌵􁦡􁗝􁈾􀤹􀝒􁰁
􁥴􀙬􀷜􁀩􀒓􀲋􀛖􁦡􁗝 Heap size
􀗥􀶯 TOMCAT_HOME/bin/catalina.sh
setJAVA_OPTS=-Xms32m-Xmx512m
􀝢􀕦􀻑􀴝􁛔􀫩􀹢􀢏􁌱􀙖􀨂􁬰􁤈􀹅􀶯􀌶
2􀌵 java-Xms32m-Xmx800m className
􀩪􀸎􀣁􀲗􁤈JAVA􁔄􀷈􀕯􀷸􀛒􀓤􁬯􀓻􀝇􀷄􀒅􀙌􀓾className
􀸎􁵱􁥝􀲗􁤈􁌱􁏟􁔄􀝷􀌶􀒁􀛱􀳡􀛱􀝷􀒂􁬯􀓻􁥴􀙬􁳯􁷌􀔧􀌶􁘒􀓬􀲗􁤈􁌱􁭛􀬶􀾲
􁀌􀹍􁦡􁗝􁌱􀷸􀗲􀮳􀮉􀥚􀌶􀦇􀺎􀣁􁁥􁦶􁌱􀷸􀗲􀝢􁚆􀕿􁊠Eclispe􁬯􀷸􀗲􀩪􁵱􁥝
􀣁 Eclipse->run-arguments 􀓾􁌱 VM arguments 􀓾􁬌􀙁 -Xms32m-
Xmx800m 􁬯􀓻􀝇􀷄􀩪􀝢􀕦􀔧􀌶
􀝸􀹶􀣁Eclilpse􀓾􀗥􀶯􀔧􀞐􀛖􀝇􀷄􀒅􀣁 VMarguments
􀛒􀙁􀔧 -Xms32m-Xmx800m 􀒅􁳯􁷌􁥴􀙬􀌶
􀓞􀌵 java.lang.OutOfMemoryError:PermGen space
PermGen space 􁌱􀙂􁑍􀸎 Permanent Generation space ,􀸎􀳰􀙖􀨂􁌱
􀿞􀔋􀗛􀨂􀜄􀤒,
􁬯􀣘􀙖􀨂􀔆􁥝􀸎􁤩JVM􀨂􀶱Class􀞾Meta􀗞􀯳􁌱,Class􀣁􁤩Loader􀷸􀩪􀕿􁤩
􀶱􀚩 PermGen space 􀓾,􀨙􀞾􀨂􀶱􁔄􀨫􀖺(Instance)􁌱Heap􀜄􀤒􀓧
􀝶, GC(Garbage Collection) 􀓧􀕿􀣁􀔆􁑕􀬧􁬩􁤈􀹗􀩒 PermGen space
􁬰􁤈􁂴􁉘􀒅􀲅􀕦􀦇􀺎􀖦􁌱􀬫􁊠􀓾􀹍􀮉􀥚CLASS􁌱􁦾,
􀩪􀮉􀝢􁚆􀚊􁈿 PermGen space 􁲙􁧏,􁬯􁐿􁲙􁧏􀬉􁥠􀣁web􀹐􀛓􀢏􀩒JSP􁬰
􁤈 preco mpile 􁌱􀷸􀗲􀌶􀦇􀺎􀖦􁌱 WEB APP 􀓥􁮷􁊠􀔧􀥟􁰁􁌱􁒫􀓣􀷜jar,
􀙌􀥟􀩜􁩻􁬦􀔧jvm􁼕􁦊􁌱􀥟􀩜(4M)􁮎􀔍􀩪􀕿􀔾􁊞􀾌􁲙􁧏􀗞􀯳􀔧􀌶
􁥴􀙬􀷜􁀩􀒓􀲋􀛖􁦡􁗝MaxPermSize􀥟􀩜􀗥
􀶯 TOMCAT_HOME/bin/catalina.sh
􀣁 “echo"Using CATALINA_BASE:$CATALINA_BASE"” 􀓤􁶎􀛒􀙁􀕦􀓥
􁤈􀒓 JAVA_OPTS="-server-XX:PermSize=64M-XX:MaxPermSize=128m
􀭌􁦓􀒓􀩙􁍘􀝶􁌱􁒫􀓣􀷜jar􀷈􀕯􁑏􁗝􀚩 tomcat/shared/lib 􁍓􀭯􀓥􀒅􁬯􀻏
􀝢􀕦􁬡􀚩􀙺􀩝jar􀷈􀻩􁯿􀥔􀜛􁊠􀙖􀨂􁌱􁍓􁌱􀌶
􀔫􀌵 java.lang.OutOfMemoryError:Java heap space
Heap size 􁦡􁗝
JVM􀤞􁌱􁦡􁗝􀸎􀳰java􁑕􀬧􁬩􁤈􁬦􁑕􀓾JVM􀝢􀕦􁧣􁯈􀖵􁊠􁌱􀙖􀨂􁑮􁳵􁌱􁦡
􁗝.JVM􀣁􀞐􀛖􁌱􀷸􀗲􀕿􁛔􀛖􁦡􁗝 Heap size 􁌱􊧊􀒅
􀙌􀚡􀦤􁑮􁳵 (􀜨-Xms) 􀸎􁇔􁉘􀙖􀨂􁌱1/64􀒅􀹋􀥟􁑮􁳵 (-Xmx) 􀸎􁇔􁉘􀙖􀨂
􁌱1/4􀌶􀝢􀕦􀚥􁊠JVM􀵉􀗀􁌱 -Xmn-Xms-Xmx 􁒵􁭌􁶱􀝢􁬰􁤈􁦡􁗝􀌶 Heap
size 􁌱􀥟􀩜􀸎 Young Generation 􀞾 TenuredGeneraion
􀔏􀞾􀌶
􀵉􁐏􀒓􀣁JVM􀓾􀦇􀺎98􀑾􁌱􀷸􁳵􀸎􁊠􀔭GC􀓬􀝢􁊠􁌱 Heap size 􀓧􁪃2􀑾
􁌱􀷸􀗲􀩙􀲲􀚊􀾌􀭑􀬉􀗞􀯳􀌶
􀵉􁐏􀒓 Heap Size 􀹋􀥟􀓧􁥝􁩻􁬦􀝢􁊠􁇔􁉘􀙖􀨂􁌱80􀑾􀒅􀓞􁛱􁌱􁥝􀩙 -
Xms 􀞾 -Xmx 􁭌􁶱􁦡􁗝􀔅􁍘􀝶􀒅􁘒 -Xmn 􀔅1/4􁌱 -Xmx 􊧊􀌶
􁥴􀙬􀷜􁀩􀒓􀲋􀛖􁦡􁗝 Heap size
􀗥􀶯 TOMCAT_HOME/bin/catalina.sh
􀣁 “echo"Using CATALINA_BASE:$CATALINA_BASE"” 􀓤􁶎􀛒􀙁􀕦􀓥􁤈􀒓
JAVA_OPTS="-server-Xms800m-Xmx800m-XX:MaxNewSize=256m"
􀓣􀌵􀨫􀖺􀒅􀕦􀓥􁕳􀚊1G􀙖􀨂􁈾􀤹􀓥 java jvm 􁌱􀝇􀷄􁦡􁗝􀝇􁘍􀒓
JAVA_OPTS="-server-Xms800m-Xmx800m-XX:PermSize=64MXX:
MaxNewSize=256m-XX:MaxPermSize=128m-
Djava.awt.headless=true"
􀮉􀥟􁌱web􀫡􁑕􀒅􁊠tomcat􁼕􁦊􀚓􁯈􁌱􀙖􀨂􁑮􁳵􀷫􁀩􀞐􀛖􀒅􀦇􀺎􀓧􀸎􀣁
myeclipse􀓾􀞐􀛖tomcat􀝢􀕦􀩒tomcat
􁬯􀻏􁦡􁗝􀒓
TOMCAT_HOME/bin/catalina.bat 􀓾􁂲􀛒􁬯􀻏􀓞􀝙􁦾􀒓
set JAVA_OPTS=-server-Xms2048m-Xmx4096m-XX:PermSize=512MXX:
MaxPermSize=1024M-Duser.timezone=GMT+08
􀱲􁘏
set JAVA_OPTS=-Xmx1024M-Xms512M-XX:MaxPermSize=256m
􀦇􀺎􁥝􀣁myeclipse􀓾􀞐􀛖􀒅􀓤􁬿􁌱􀗥􀶯􀩪􀓧􁩸􀖢􁊠􀔧􀒅􀝢􀦇􀓥􁦡􁗝􀒓
Myeclipse->preferences->myeclipse->servers->tomcat-
>tomcat×.×->JDK 􁶎􀺃􀓾􁌱 Optional Java VM arguments 􀓾􁂲􀛒􀒓 -
Xmx1024M-Xms512M-XX:MaxPermSize=256m
􀕦􀓤􀸎􁫨􁩂􀒅􀖕􀹜􀕈􁭬􁥠􁌱􁳯􁷌􀸎􀒓􀣁myeclipse􀓾􀞐􀛖Tomcat􀷸􀒅􀵉
􁐏 "ava.lang.OutOfMemoryError:Java heap space" 􀒅􁥴􀙬􀛐􁀩􀩪
􀸎􀒓 Myeclipse->preferences->myeclipse>servers->tomcat-
tomcat×.×->JDK 􁶎􀺃􀓾􁌱
Optional Java VM arguments 􀓾􁂲􀛒􀒓 -Xmx1024M-Xms512MXX:
MaxPermSize=256m
4􀌵tomcat􀓾􀦇􀖜􁐬􀾊􀚜􁍓􀭯􀓥􁌱􀷈􀕯
􀣁 {tomcat_home}/conf/web.xml 􀓾􀒅􀲩listings􀝇􀷄􁦡􁗝􀱮false􀜨􀝢􀒅
􀦇􀓥􀒓
<init-param>
<param-name>listings</param-name>
<param-value>false</param-value>
</init-param>
<init-param>
<param-name>listings</param-name>
<param-value>false</param-value>
</init-param>
5􀌵Tomcat􀹍􀙾􁐿􁮱􁗟􀷜􀭗
tomcat􀓾􀢥􁐿􁮱􁗟􁶱􁍓􀷜􁀩
􁒫􀓞􁐿􀷜􁀩􀒓
􀣁 tomcat 􀓾􁌱 conf 􁍓􀭯􀓾􀒅􀣁 server.xml 􀓾􁌱􀒅 <host/> 􁜓􁅩􀓾
􁂲􀛒􀒓
<Context path="/hello"
docBase="D:/eclipse3.2.2/forwebtoolsworkspacehello/WebRoot"deb
ug="0"
privileged="true">
</Context>
􁛗􀔭 Context 􁜓􁅩􀪂􀯔􀒅􀝢􁧇􁕡􁥠􁍘􀙉􀷈􀻩􀌶
􁒫􀔫􁐿􀷜􁀩􀒓
􀩙 web 􁶱􁍓􀷈􀕯􀕯􀳩􁨬􀚩 webapps 􁍓􀭯􀓾􀌶
􁒫􀓣􁐿􀷜􁀩􀒓
􀮉􁅎􁁚􀒅􀣁 conf 􁍓􀭯􀓾􀒅􀷛􀭌 Catalina 􀒁􁀳􀰺􀥟􀩜􀙟􀒂
􀒵 localhost 􁍓􀭯􀒅􀣁􁧆􁍓􀭯􀓾􀷛􀭌􀓞􀓻 xml 􀷈􀕯􀒅􀝷􀨁􀝢􀕦􁵋􀰺􀝐􀒅
􀝝􁥝􀞾􀭮􀚹􀷈􀕯􀓾􁌱􀷈􀕯􀝷􀓧􁯿􀥔􀩪􁤈􀔧􀒅􁧆 xml 􀷈􀕯􁌱􀙖􀨻􀔅􀒓
<Context path="/hello"docBase="D:eclipse3.2.2forwebtoolsworksp
aceheloWebRoot"
debug="0"privileged="true">
</Context>
􁒫3􀓻􀷜􁀩􀹍􀓻􀕽􁅩􀒅􀝢􀕦􀨧􀔎􀚦􀝷􀌶􀹐􀛓􀢏􁒒􁬩􁤈􁌱􁶱􁍓􀝷􁑍
􀔅 path 􀒅􀥘􁮱􁦢􁳯􁌱 URL 􀚞􀖵􁊠 XML 􁌱􀷈􀕯􀝷􀌶􁬯􀓻􀷜􁀩􀮉􀷜􀗎􁌱􁵌
􁡐􀔧􁶱􁍓􁌱􀝷􁑍􀒅􀩒􀓞􀔶􁶱􁍓􀝷􁑍􁤩􀢴􀨧􀓧􁚆􀹅􀴘􀒅􀖕􀥘􁮱􁦢􁳯􀷸􀝈􀰮􀴘
􀓻􁪠􀮆􀒅􁶋􀬉􀹍􀶴􀌶
􁒫2􀌵3􁬮􀹍􀕽􁅩􀒅􀝢􀕦􀨧􀔎􀓞􀔶􀓻􀯔􁯈􁗝􀒅􀦇􀷄􀴝􁃠􁌱􁯈􁗝􁒵􀌶
􁒫􀢥􁐿􀛐􁀩:
􀝢􀕦􁊠 tomcat 􀣁􁕚􀝸􀝣􁓕􁉘􀢏􀒅􀓞􁛱 tomcat 􁮷􀲑􀭏􀔧􀒅􁍗􀴳􀓤􀖃 war
􀩪􀝢􀕦
6􀌵Tomcat􁌱􀕽􀛸􁕪􁸵
Tomcat 􀖢􀔅 web 􀹐􀛓􀢏􀒅􀨙􁌱􀥒􁉘􀯔􁚆􁍗􀴳􀙉􁔮􀚩􁊠􀲁􀖛􁸵􀒅􀓥􁶎􀸎􁐿
􀬉􁥠􁌱􀕽􀛸􀴷􀷞:
• 􀝄􀴧􀩒 web.xml 􁌱􁍊􁥤􀒅􀲩 jsp 􀵉􀚹􁖫􁬋􀱮 Servlet 􀌶􀹍􀩄􀖟􁇔􁉘􀙖
􀨂􁌱􀰘􀙭􀒅􀛒􀥟tomcat 􀖵􁊠􁌱 jvm 􁌱􀙖􀨂􀌶
• 􀹐􀛓􀢏􁩒􁃠
􀹐􀛓􀢏􀲅􁚆􀵉􀗀CPU􀌵􀙖􀨂􀌵􁏝􁍏􁌱􀯔􁚆􀩒􀥒􁉘􁚆􀛎􀹍􀙬􀨧􀯔􀭽􀟥􀌶
• 􀩒􀔭􁹛􀬚􀝎􀰘􀙭􀓥􀕿􀹍􀥟􁰁􁌱􁬩􁓒􀒅􁮎􀔍CPU􁌱􁭛􀬶􀕿􁍗􀴳􀭽􀟥􀚩􀥒􁉘
􁭛􀬶􀌶
• 􀙖􀨂􀣁􀥟􁰁􀷄􀴝􀥒􁉘􁌱􀰘􀙭􀓥􀒅􀩙􀕿􀹍􁫾􀥟􁌱􀙖􀨂􀨻􁰁􁵱􀿢􀒅􀝢􀕦􁊠
-Xmx-Xms-XX:MaxPermSize 􁒵􀝇􀷄􀩒􀙖􀨂􀓧􀝶􀛑􁚆􀣘􁬰􁤈􀚚􀚓􀌶􀱯􀕪􀔏
􀚹􀩪􁭬􀚩􁬦􀙖􀨂􀚓􁯈􀓧􁪃􀒅􀩕􁛘􁡦􀳙􀹢􀓞􁍗􀥒􀔭 full GC 􀒅􀕗􁘒􀩕􁛘􀥒
􁉘􁚆􀛎􀓸􁯿􀓥􁴳􀌶
• 􁏝􁍏􀔆􁥝􁳯􁷌􀩪􀸎􁧛􀙟􀯔􁚆􀒅􀭮􀥟􁰁􀷈􀕯􁬰􁤈􁧛􀙟􀷸􀒅􁏺􁍏􀺄􀨻􀸃􀱮􀔅
􀯔􁚆􁊒􁷀􀌶􀹋􀦅􁌱􀛐􁀩􁬮􀸎􀚥􁊠􀓥􁶎􀵉􀚩􁌱􁖨􀨂􀌶
• 􀚥􁊠􁖨􀨂􀞾􀜴􁖽
􀩒􀔭􁶉􀮾􁶭􁶎􀹋􀦅􀸎􁚆􀥜􁖨􀨂􁩸􀹶􀒅􁬯􀻏􀩪􀓧􀮠􀾯􀽺􀕗􁏺􁍏􀓤􁧛􀌶􁬯􁯾􀱯
􀕪􁯻􁊠􀔧Nginx􀖢􀔅􁖨􀨂􀹐􀛓􀢏􀒅􀩙􀢶􁇆􀌵css􀌵js􀷈􀕯􁮷􁬰􁤈􀔧􁖨􀨂􀒅􀹍
􀶴􁌱􀙺􀩝􀔧􀝸􁒒tomcat􁌱􁦢􁳯􀌶􀝚􀥘􀒅􀔅􀔧􁚆􀛒􀮳􁗑􁕶􀖃􁬌􁭛􀬶􀒅􀭏􀞐
gzip􀜴􁖽􀔞􀸎􀮠􀓧􀝢􀩝􁌱􀌶􀖕􁘍􁡤􀚩tomcat􀫪􁕪􁵱􁥝􀥒􁉘􀮉􀥚􀓳􁥜􀔧􀒅􀲅
􀕦􀲩􁬯􀓻􀜴􁖽􁌱􀫡􀖢􀩪􀔻􁕳􀚹􁒒􁌱Nginx􀹶􀨠􀱮􀌶
􁴻􀔧􀷈􀹜􀝢􀕦􁊠gzip􀜴􁖽􀒅􀙌􀨫􀮉􀥚􀢶􁇆􀔞􀝢􀕦􁊠􀢶􀘟􀥒􁉘􀫡􀙍􁶼􀘶􁬰􁤈
􀜴􁖽􀒅􀲤􀚩􀓞􀓻􀬘􁤍􁅩􀝢􀕦􁦏􁊮􁨶􀴖􀥦􀮉􀩜􁘒􀷈􀕯􀝢􀕦􀙺􀩜􀮉􀥚􀌶􀹉􁕪􀱯
􀩪􁥠􁬦􀓞􀓻􀢶􁇆􀕗300􀥚kb􀜴􁖽􀚩􀙾􀜈kb􀒅􁛔􀫩􀙾􀔒􁍡􀓧􀚊􀹶􀜄􀚦􀌶
• 􁯻􁊠􁵞􁗭
􀜔􀓻􀹐􀛓􀢏􀯔􁚆􀯛􀸎􀹍􁴴􁌱􀒅􀹋􀦅􁌱􀛐􁀩􁛔􁆐􀸎􀨫􁈿􀽞􀝻􀲘􀪀􀒅􁮎􀔍􁕟􀭌
tomcat􁵞􁗭􀸎􀹍􀶴􀵉􀜋􀯔􁚆􁌱􀲋􀾧􀌶􀱯􀕪􁬮􀸎􁯻􁊠􀔧Nginx􀹶􀖢􀔅􁧗􀿢􀚓
􁁞􁌱􀹐􀛓􀢏􀒅􀝸􁒒􀥚􀓻tomcat􀙈􀕁session􀹶􀜐􀝶􀫡􀖢􀌶􀝢􀕦􀝇􁘍􀔏􀚹􀙟􁌱
􀌽􀚥􁊠nginx+tomcat+memcached􁕟􀭌web􀹐􀛓􀢏􁨮􁫹􀣐􁤍􀌾􀌶
• 􀕽􀛸tomcat􀝇􀷄
􁬯􁯾􀕦tomcat7􁌱􀝇􀷄􁯈􁗝􀔅􀖺􀒅􁵱􁥝􀗥􀶯conf/server.xml􀷈􀕯􀒅􀔆􁥝􀸎􀕽
􀛸􁬳􀴳􁯈􁗝􀒅􀙉􁳮􀨮􀲁􁒒dns􀺱􁧃􀌶
<Connector port="8080"
protocol="org.apache.coyote.http11.Http11NioProtocol"
connectionTimeout="20000"
redirectPort="8443"
maxThreads="500"
minSpareThreads="20"
acceptCount="100"
disableUploadTimeout="true"
enableLookups="false"
URIEncoding="UTF-8"/>
1.2􀌵JVM􀯔􁚆􀕽􀛸􀓫􁷌
1􀌵Java􁔄􀛒􁫹􁬦􁑕
Java 􁔄􀛒􁫹􁵱􁥝􁕪􀜲􀓞􀓥7 􀓻􁬦􁑕􀒓
1 . 􀛒􁫹
􀛒􁫹􀸎􁔄􀛒􁫹􁌱􁒫􀓞􀓻􁬦􁑕􀒅􀣁􁬯􀓻􁴤􀾧􀒅􀩙􀨠􀱮􀓞􀓥􀓣􀕯􀔪􀰘􀒓
• 􁭗􁬦􀓞􀓻􁔄􁌱􀙂􁴴􀨧􀝷􁞴􀝐􁧆􁔄􁌱􀔫􁬰􀚫􁁞􀌶
• 􀩙􁧆􀔫􁬰􀚫􁁞􀓾􁌱􁶉􀮾􀨂􀘙􁕮􀺅􁫨􀛸􀔅􀷜􁀩􀝄􁬩􁤈􀷸􀷄􀴝􁕮
􀺅􀌶
• 􀣁􀙖􀨂􀓾􁊞􀱮􁧆􁔄􁌱 Class 􀩒􁨝􀒅􀖢􀔅􁧆􁔄􁌱􀷄􀴝􁦢􁳯􀙁􀝗􀌶
2 . 􁸵􁦤
􁸵􁦤􁌱􁍓􁌱􀸎􀔅􀔧􁏟􀗛 Class 􀷈􀕯􁌱􀨁􁜓􁁞􀓾􁌱􀗞􀯳􀓧􀢧􀜧􀨶􀚩
􁡦􀳙􀹢.􀣁􁧆􁴤􀾧􀔆􁥝􀨠􀱮􀕦􀓥􀢥􁰦􁸵􁦤:
• 􀷈􀕯􀻒􀭗􁸵􁦤􀒓􁸵􁦤􀨁􁜓􁁞􀸎􀞈􁒧􀝳 Class 􀷈􀕯􁌱􁥢􁝜􀒅􀦇􀔆􀽺􁇇􀹜􀝩
􀸎􀞈􀣁􀭮􀚹􁡦􀳙􀹢􁝜􀢱􀙖􀒅􀬉􁰁􀿰􀓾􁌱􀬉􁰁􀸎􀞈􀹍􀓧􁤩􀶪􀳮􁌱􁔄􀣳.
• 􀘲􀷄􀴝􁸵􁦤:􀩒􀨁􁜓􁎱􀵈􁬿􁌱􀗞􀯳􁬰􁤈􁧍􀔎􀚓􀺉􀒅􀦇􁬯􀓻􁔄􀸎􀞈􀹍􁆿􁔄􀒅
􀸎􀞈􁵞􀱮􀔧􀓧􁤩􁖀􀲥􁌱􁔄􁒵􀌶
• 􀨁􁜓􁎱􁸵􁦤􀒓􀸎􀷆􀓻􁸵􁦤􁬦􁑕􀓾􀹋􀥔􀹥􁌱􀓞􀓻􁴤􀾧􀒅􁭗􁬦􁸵􁦤􀷄􀴝􁁞􀞾
􀴴􀚫􁁞􁌱􀚓􀺉􀒅􁏟􀨧􁑕􀬧􁧍􀔎􀸎􀞈􀾋􁏟􀒅􀔆􁥝􁰒􀩒􀷜􁀩􀖛􁌱􁸵􁦤􀌶􀦇􀒓􀷜
􁀩􀓾􁌱􁔄􀣳􁫨􀴘􀸎􀞈􀾋􁏟􀒅􁪡􁫨􀳰􀕥􀸎􀞈􀾋􁏟􁒵􀌶
• 􁒧􀝩􀭚􁊠􁸵􁦤􀒓􁬯􀓻􀛖􀖢􀣁􀝸􁶎􁌱􁥴􀺉􁬦􁑕􀓾􀝎􁊞􀒅􀔆􁥝􀸎􀔅􀔧􁏟􀗛􁥴
􀺉􀛖􀖢􁚆􀾋􁏟􀲗􁤈􀌶
3 . 􀙵􀥓
􀙵􀥓􁴤􀾧􀸎􀔅􁔄􁌱􁶉􀮾􀝒􁰁􀚓􁯈􀙖􀨂􀬚􀩙􀙌􀚡􀦤􀛸􀔅􁼕􁦊􊧊􀒅􁬯􀔶􀙖􀨂􁮷
􀩙􀣁􀷜􁀩􀜄􀓾􁬰􁤈􀚓􁯈􀌶􀙵􀥓􁴤􀾧􀓧􀚓􁯈􁔄􀓾􁌱􀨫􀖺􀝒􁰁􁌱􀙖􀨂􀒅􀨫􀖺􀝒
􁰁􀩙􀕿􀣁􀩒􁨝􀨫􀖺􀛸􀷸􁵋􁍳􀩒􁨝􀓞􁩸􀚓􁯈􀣁Java 􀤞􀓾􀌶
public static int value=123;//􀣁􀙵􀥓􁴤􀾧value􀚡􀦤􊧊􀔅0 􀌶􀣁􀚡􀦤􀛸􁴤
􀾧􀲍􀕿􀝒􀔅123 􀌶
4 . 􁥴􀺉
􁧆􁴤􀾧􀔆􁥝􀨠􀱮􁒧􀝩􀭚􁊠􀚩􁍗􀴳􀭚􁊠􁌱􁫨􀴘􀛖􀖢􀌶􁥴􀺉􀛖􀖢􀬚􀓧􀓞􀨧􀣁􀚡
􀦤􀛸􀛖􀖢􀨠􀱮􀔏􀚹􀒅􀔞􀹍􀝢􁚆􀣁􀚡􀦤􀛸􀔏􀝸􀌶
5 . 􀚡􀦤􀛸
􀚡􀦤􀛸􀷸􁔄􀛒􁫹􁌱􀹋􀝸􀓞􀾍􀒅􀚹􁶎􁌱􁔄􀛒􁫹􁬦􁑕􀒅􁴻􀔧􀣁􀛒􁫹􁴤􀾧􁊠􀲁􀬫
􁊠􁑕􀬧􀝢􀕦􁭗􁬦􁛔􀨧􀔎􁔄􀛒􁫹􀢏􀝇􀓨􀔏􀥘􀒅􀙌􀖟􀛖􀖢􀨠􀙂􁊧􁡦􀳙􀹢􀔆􀩕􀞾
􀴴􀚫􀌶􀚩􀔧􀚡􀦤􀛸􁴤􀾧􀒅􀲍􁍥􀾋􀭏􀦤􀲗􁤈􁔄􀓾􁌱􀨧􀔎􁌱java􁑕􀬧􀕤􁎱􀌶
6.􀖵􁊠
7.􀜬􁫹
2􀌵java􀙖􀨂􀚓􁯈
• 􀩀􀨂􀢏􀒓􀱯􀕪􀷫􁀩􀴴􀚫􀌶
• 􁶉􀮾􀤒􀒓 static 􀨧􀔎􁌱􁶉􀮾􀱮􀞧􀌶
• 􀬉􁰁􀿰􀒓􁖫􁦲􀷸􁤩􁏟􀨧􀬚􀗛􀨂􀣁. class 􀷈􀕯􀓾􁌱 􀒁final􀒂 􀬉􁰁􊧊􀞾
􀓞􀔶􀷈􀹜􀗥􁷶􁌱􁒧􀝩􀭚􁊠􀒁􁔄􀞾􀴳􀝗􁌱􀙂􁴴􀨧􀝷􀒅􀨁􀾧􁌱􀝷􁑍􀞾􀵈􁬿􁒧􀒅
􀷜􁀩􀞾􀝷􁑍􀞾􀵈􁬿􁒧􀒂􀌶
• 􁶋 RAM 􀨂􀘙􀒓􁏝􁍏􁒵􀿞􀔋􀨂􀘙􁑮􁳵􀌶
• 􀤞􀙖􀨂􀒓new 􀚠􀭌􁌱􀩒􁨝􀞾􀷄􁕟􀒅􁊧Java 􁡦􀳙􀹢􁛔􀛖􀣯􀣍􀢧􀶭􀢏􁓕􁉘,
􀨂􀝐􁭛􀬶􀱌􀌶
• 􀺾􀙖􀨂􀒓􀤚􀹜􁔄􀣳􁌱􀝒􁰁􀞾􀩒􁨝􁌱􀭚􁊠􀝒􁰁􀒁􀤞􀙖􀨂􁑮􁳵􁌱􁦢􁳯􀣈
􀣎􀒂􀒅􁭛􀬶􀮳􀒅􀝢􀕦􀙈􀕁􀒅􀖕􀸎􀥟􀩜􀓨􁊞􀨂􀹗􀮠􁶳􁏟􀨧􀒅􁗌􀔓􁅎􁁚􀯔􀌶
1.Java 􀤞􁌱􁕮􀺅􀸎􀕋􀔍􀻏􀧼􁌱􀒘􀕋􀔍􀸎􀤞􀓾􁌱􀿞􀔋􀕤 􀒁Perm Gen
space􀒂 ?
JVM 􁌱􀤞􀸎􁬩􁤈􀷸􀷄􀴝􀜄􀒅􀲅􀹍􁔄􁌱􀨫􀖺􀞾􀷄􁕟􁮷􀸎􀣁􀤞􀓤􀚓􁯈􀙖􀨂􀌶􀨙
􀣁 JVM 􀞐􀛖􁌱􀷸􀗲􁤩􀚠􀭌􀌶􀩒􁨝􀲅􀜛􁌱􀤞􀙖􀨂􀸎􁊧􁛔􀛖􀙖􀨂􁓕􁉘􁔮􁕹􀔞􀩪
􀸎􀣯􀣍􀶭􁵞􀢏􀢧􀶭􀌶
􀤞􀙖􀨂􀸎􁊧􀨂􁁚􀞾􀾒􀔹􁌱􀩒􁨝􁕟􀱮􁌱􀌶􀨂􁁚􁌱􀩒􁨝􀸎􀬫􁊠􀝢􀕦􁦢􁳯􁌱􀒅􀓧
􀕿􁤩􀣯􀣍􀢧􀶭􀌶􀾒􀔹􁌱􀩒􁨝􀸎􀬫􁊠􀓧􀝢􁦢􁳯􀩢􀓬􁬮􁀌􀹍􁤩􀣯􀣍􀶭􁵞􀢏􀢧􀶭
􀴧􁌱􀩒􁨝􀌶􀓞􁍗􀚩􀣯􀣍􀶭􁵞􀢏􀲩􁬯􀔶􀩒􁨝􀢧􀶭􀴧􀔏􀚹􀒅􀕜􀕪􀕿􀓞􁍗􀜛􀴝􀤞
􀙖􀨂􁑮􁳵􀌶
3􀌵􀵈􁬿􀓞􀓥JVM􀛒􁫹Class􀷈􀕯􁌱􀜻􁉘􀹢􀚫􀒘
Java 􁧍􁥺􀸎􀓞􁐿􀙍􀹍􀛖􀮾􀯔􁌱􁥴􁯽􀣳􁧍􁥺􀒅􁔄􀒁Class􀒂􀝝􀹍􁤩􀛒
􁫹􀚩JVM 􀝸􀲍􁚆􁬩􁤈􀌶􀭮􁬩􁤈􀳰􀨧􁑕􀬧􀷸􀒅JVM 􀕿􀩙􁖫􁦲􁊞􀱮􁌱 .class
􀷈􀕯􀳲􁆙􁵱􀿢􀞾􀓞􀨧􁌱􁥢􀚞􀛒􁫹􀚩􀙖􀨂􀓾􀒅􀬚􁕟􁕢􀱮􀔅􀓞􀓻􀨠􀷆􁌱Java 􀬫
􁊠􁑕􀬧􀌶􁬯􀓻􀛒􁫹􁬦􁑕􀸎􁊧􁔄􀛒􁫹􀢏􀨠􀱮􀒅􀙍􀖛􀹶􁧔􀒅􀩪􀸎􁊧
ClassLoader 􀞾􀨙􁌱􀧼􁔄􀹶􀨫􁈿􁌱􀌶􁔄􀛒􁫹􀢏􀹜􁫝􀔞􀸎􀓞􀓻􁔄􀒅􀙌􀨫􁨶􀸎
􀲩􁔄􀷈􀕯􀕗􁏝􁍏􁧛􀝐􀚩􀙖􀨂􀓾􀌶
􁔄􁌱􀛒􁫹􀷜􀭗􀚓􀔅􁵌􀭗􀛒􁫹􀞾􀸔􁐏􀛒􁫹􀌶􁵌􀭗􀛒􁫹􀳰􁌱􀸎􁑕􀬧􀣁􀖵􁊠new
􁒵􀷜􀭗􀚠􀭌􀩒􁨝􀷸􀒅􀕿􁵌􀭗􀣈􁧣􁊠􁔄􁌱􀛒􁫹􀢏􀲩􀩒􀬫􁌱􁔄􀛒􁫹􀚩JVM 􀓾􀌶
􀸔􁐏􀛒􁫹􀳰􁌱􀸎􁭗􁬦􁍗􀴳􁧣􁊠 class.forName() 􀷜􁀩􀹶􀲩􀲅􁵱􁌱􁔄􀛒􁫹
􀚩JVM 􀓾􀌶
􀕱􀖜􀓞􀓻􀫡􁑕􁶱􁍓􁮷􀸎􁊧􁦜􀥚􁔄􁕟􀱮􁌱􀒅􀭮􁑕􀬧􀞐􀛖􀷸􀒅􀝝􀲩􁵱􁥝􁌱􁔄􀛒
􁫹􀚩JVM 􀓾􀒅􀙌􀕜􁔄􀝝􀹍􁤩􀖵􁊠􀚩􁌱􀷸􀗲􀲍􀕿􁤩􀛒􁫹􀒅􁯻􁊠􁬯􁐿􀷜􁀩􀓞􀷜
􁶎􀝢􀕦􀛒􀮳􀛒􁫹􁭛􀬶􀒅􀝚􀓞􀷜􁶎􀝢􀕦􁜓􁕅􁑕􀬧􁬩􁤈􀷸􀩒􀙖􀨂􁌱􀭏􁲀􀌶􀾌
􀥘􀒅􀣁Java 􁧍􁥺􀓾􀒅􀾯􀓻􁔄􀱲􀴳􀝗􁮷􀩒􀬫􀓞􀓻 .class 􀷈􀕯􀒅􁬯􀔶􀷈􀕯
􀝢􀕦􁤩􁍡􀱮􀸎􀓞􀓻􀓻􀝢􀕦􁤩􀛖􀮾􀛒􁫹􁌱􀜔􀘲􀒅􀢩􀾌􀭮􀝝􀹍􁮱􀚓􁔄􁤩􀗥􀶯
􀷸􀒅􀝝􁵱􁥝􁯿􀷛􁖫􁦲􀝒􀛸􁌱􁔄􀜨􀝢􀒅􁘒􀓧􁵱􁥝􁯿􀷛􁖫􁦲􀲅􀹍􀷈􀕯􀒅􀢩􀾌􀛒
􀮳􀔧􁖫􁦲􁭛􀬶􀌶
􀣁Java 􁧍􁥺􀓾􀒅􁔄􁌱􀛒􁫹􀸎􀛖􀮾􁌱􀒅􀨙􀬚􀓧􀕿􀓞􀽺􀯔􀩙􀲅􀹍􁔄􀙂
􁮱􀛒􁫹􀝸􀙚􁬩􁤈􀒅􁘒􀸎􀗛􁦤􁑕􀬧􁬩􁤈􁌱􀤚􁏐􁔄􀒁􀖺􀦇􀤚􁔄􀒂􀨠􀙂􀛒
􁫹􀚩JVM 􀓾􀒅􁛗􀔭􀙌􀕜􁔄􀒅􀚞􀣁􁵱􁥝􁌱􀷸􀗲􀲍􀛒􁫹􀌶
􁔄􀛒􁫹􁌱􀔆􁥝􀾍􁹈􀒓
• 􁤰􁫹􀌶􀻑􀴝􀺱􀲤􁪠􀮆􀲤􀚩􁍘􀬫􁌱class 􀷈􀕯􀒅􁆐􀝸􀩕􀙁􀌶
• 􁱾􀴳􀌶􁱾􀴳􀝈􀝢􀚓􀔅3 􀓻􀩜􀾍􀒓
• 􀼄􀺱􀒅􀼄􀺱􀮇􀛒􁫹􁌱class 􀷈􀕯􁌱􀾋􁏟􀯔􀌶
• 􀙵􀥓􀒅􁕳􁔄􀓾􁌱􁶉􀮾􀝒􁰁􀚓􁯈􀨂􀘙􁑮􁳵􀌶
• 􁥴􀺉􀒅􀩙􁒧􀝩􀭚􁊠􁫨􀴘􀔅􁍗􀴳􀭚􁊠􀒁􁬯􀓞􀾍􀝢􁭌􀒂
• 􀚡􀦤􀛸􀌶􀩒􁶉􀮾􀝒􁰁􀞾􁶉􀮾􀕤􁎱􀣘􀲗􁤈􀚡􀦤􀛸􀫡􀖢􀌶
4􀌵GC 􀸎􀕋􀔍? 􀔅􀕋􀔍􁥝􀹍 GC?
GC 􀸎􀣯􀣍􀶭􁵞􁌱􀰺􀯏(GabageCollection)􀒅􀙖􀨂􀥒􁉘􀸎􁖫􁑕 􀕈􀞧􀨻􀸃􀚊􁈿
􁳯􁷌􁌱􀣈􀷜􀒅􀮫􁦕􀱲􁘏􁲙􁧏􁌱􀙖􀨂􀢧􀶭􀕿􀩕􁛘􁑕􀬧􀱲 􁔮􁕹􁌱􀓧􁑞􀨧􁊜􁛗􀫄
􁃛􀒅Java 􀵉􀗀􁌱 GC 􀛑􁚆􀝢􀕦􁛔􀛖􁍊􁁥􀩒􁨝 􀸎􀞈􁩻􁬦􀖢􁊠􀤒􀕗􁘒􁬡􀚩􁛔
􀛖􀢧􀶭􀙖􀨂􁌱􁍓􁌱􀒅Java 􁧍􁥺􁀌􀹍􀵉 􀗀􁯽􀶱􀫪􀚓􁯈􀙖􀨂􁌱􀸔􁐏􀶙􀖢􀷜
􁀩􀌶
5􀌵􁓌􁬿 Java 􀣯􀣍􀢧􀶭􀹢􀚫􀌶
􀣁 Java 􀓾􀒅􁑕􀬧􀞧􀸎􀓧􁵱􁥝􀸔􁐏􁌱􀝄􁯽􀶱􀓞􀓻􀩒􁨝􁌱􀙖􀨂􁌱􀒅􁘒 􀸎􁊧􁡦
􀳙􀹢􁛔􁤈􀲗􁤈􀌶􀣁 JVM 􀓾􀒅􀹍􀓞􀓻􀣯􀣍􀢧􀶭􁕚􁑕􀒅􀨙􀸎􀖗 􀕽􀘶􁕆􁌱􀒅􀣁
􀾋􀬉􀰘􀙭􀓥􀸎􀓧􀕿􀲗􁤈􁌱􀒅􀝝􀹍􀣁􁡦􀳙􀹢􁑮􁳳􀱲􁘏􀭮 􀚹􀤞􀙖􀨂􀓧􁪃􀷸􀒅􀲍
􀕿􁥶􀝎􀲗􁤈􀒅􀲚􁶎􁮎􀔶􁀌􀹍􁤩􀕱􀖜􀭚􁊠􁌱􀩒􁨝􀒅 􀬚􀩙􀨙􀕪􁂲􀛒􀚩􁥝􀢧􀶭􁌱
􁵞􀝳􀓾􀒅􁬰􁤈􀢧􀶭􀌶
6􀌵 􀦇􀖜􀚣􀷙􀓞􀓻􀩒􁨝􀸎􀞈􀨂􁁚?(􀱲􁘏 GC 􀩒􁨝􁌱􀚣􀨧􀷜􁀩)
􀚣􀷙􀓞􀓻􀩒􁨝􀸎􀞈􀨂􁁚􀹍􀓷􁐿􀷜􁀩:
1 . 􀭚􁊠􁦇􀷄􁀩
􀲅􁧲􀭚􁊠􁦇􀷄􁀩􀩪􀸎􁕳􀾯􀓞􀓻􀩒􁨝􁦡􁗝􀓞􀓻􀭚􁊠􁦇􀷄􀢏􀒅􀾯􀭮􀹍􀓞 􀓻􀣈􀷜
􀭚􁊠􁬯􀓻􀩒􁨝􀷸􀒅􀩪􀩙􁦇􀷄􀢏􀛒􀓞􀒅􀭚􁊠􀥦􀶴􀷸􀒅􁦇􀷄􀢏􀩪 􀙺􀓞􀌶􀭮􀓞􀓻
􀩒􁨝􁌱􀭚􁊠􁦇􀷄􀢏􀔅􁵭􀷸􀒅􁧔􀸁􀾌􀩒􁨝􁀌􀹍􁤩􀭚􁊠􀒅 􀔞􀩪􀸎“􀾒􀩒􁨝”,􀩙􀕿
􁤩􀣯􀣍􀢧􀶭.
􀭚􁊠􁦇􀷄􁀩􀹍􀓞􀓻􁗌􁵅􀩪􀸎􀷫􁀩􁥴􀙬􀮗􁈾􀭚􁊠􁳯􁷌􀒅􀔞􀩪􀸎􁧔􀭮􀩒 􁨝 A
􀭚􁊠􀩒􁨝 B􀒅􀩒􁨝 B 􀝈􀭚􁊠􁘏􀩒􁨝 A􀒅􁮎􀔍􀾌􀷸 A􀌵B 􀩒 􁨝􁌱􀭚􁊠􁦇􀷄􀢏
􁮷􀓧􀔅􁵭􀒅􀔞􀩪􁭜􀱮􀷫􁀩􀨠􀱮􀣯􀣍􀢧􀶭􀒅􀲅􀕦􀔆􁁞 􁌱􁡦􀳙􀹢􁮷􁀌􀹍􁯻􁊠􁬯
􁐿􁓒􁀩􀌶
2 . 􀝢􁬡􀯔􁓒􁀩(􀭚􁊠􁱾􁀩)
􁧆􁓒􁀩􁌱􀯏􀰮􀸎:􀕗􀓞􀓻􁤩􁑍􀔅 GC Roots 􁌱􀩒􁨝􀭏􀦤􀝻􀓥􀵤􁔱􀒅 􀦇􀺎􀓞
􀓻􀩒􁨝􀚩 GC Roots 􁀌􀹍􀕱􀖜􀭚􁊠􁱾􁍘􁬳􀷸􀒅􀚞􁧔􀸁􀾌􀩒 􁨝􀓧􀝢􁊠􀌶
􀣁 Java 􀓾􀝢􀕦􀖢􀔅 GC Roots 􁌱􀩒􁨝􀹍􀕦􀓥􀙾􁐿:
• 􁡦􀳙􀹢􀺾􀓾􀭚􁊠􁌱􀩒􁨝
• 􀷜􁀩􀜄􁔄􁶉􀮾􀪂􀯔􀭚􁊠􁌱􀩒􁨝 • 􀷜􁀩􀜄􀬉􁰁􀿰􀭚􁊠􁌱􀩒􁨝
• 􀹜􀣈􀷜􁀩􀺾 JNI 􀭚􁊠􁌱􀩒􁨝
􁡱􁆐􁬯􀔶􁓒􁀩􀝢􀕦􀚣􀨧􀓞􀓻􀩒􁨝􀸎􀞈􁚆􁤩􀢧􀶭􀒅􀖕􀸎􀭮􁃿􁪃􀓤􁬿􀹵 􀕯􀷸􀒅
􀓞􀓻􀩒􁨝􀾲􀓧􀓞􀨧􀕿􁤩􀢧􀶭􀌶􀭮􀓞􀓻􀩒􁨝􀓧􀝢􁬡 GC Root 􀷸􀒅􁬯􀓻􀩒􁨝􀬚
􀓧􀕿􁒈􁸘􁤩􀢧􀶭􀒅􁘒􀸎􀚊􀔭􀓞􀓻􀾒􁖨􁌱􁴤􀾧􀒅􁝑􁥝 􁤩􁍥􀾋􁌱􀢧􀶭􁵱􁥝􁕪􀜲
􀓷􀽺􀺽􁦕.
􀦇􀺎􀩒􁨝􀣁􀝢􁬡􀯔􀚓􀺉􀓾􁀌􀹍􀓨 GC Root 􁌱􀭚􁊠􁱾􀒅􁮎􀔍􀾌􀷸􀩪 􀕿􁤩􁒫
􀓞􀽺􀺽􁦕􀬚􀓬􁬰􁤈􀓞􀽺􁓀􁭌􀒅􁓀􁭌􁌱􀹵􀕯􀸎􀸎􀞈􀹍􀮠􁥝􀲗􁤈
finalize() 􀷜􁀩􀌶􀭮􀩒􁨝􁀌􀹍􁥟􁍍 finalize() 􀷜􁀩􀱲􁘏􀫪􁤩􁡦􀳙􀹢
􁧣􁊠􁬦􀒅􁮎􀔍􀩪􁦊􀔅􀸎􁀌􀮠􁥝􁌱􀌶 􀦇􀺎􁧆􀩒􁨝􀹍􀮠􁥝􀲗􁤈 finalize()
􀷜􁀩􀒅􁮎􀔍􁬯􀓻􀩒􁨝􀩙􀕿􀶱􀣁􀓞􀓻􁑍􀔅 F-Queue 􁌱􀩒 􁴚􀚜􀓾􀒅􁡦􀳙􀹢􀕿
􁥶􀝎􀓞􀓻 Finalize() 􁕚􁑕􀝄􀲗􁤈􀒅􀾌􁕚􁑕􀸎􀖗 􀕽􀘶􁕆􁌱􀒅􀬚􀓬􁡦􀳙􀹢
􀓧􀕿􀲥􁧚􀓞􁍗􁒵􀮇􀨙􁬩􁤈􀨠􀒅􁬯􀸎􀢩􀔅􀦇􀺎 finalize() 􀲗􁤈􁖨􀱌􀱲􁘏􀝎􁊞􀔧
􀾒􁲁􀒅􁮎􀔍􀩪􀕿􁭜􀱮 F-Queue 􁴚􀚜􀓞􁍗􁒵􀮇􀒅􁭜􀱮􀔧􀙖􀨂􀢧􀶭􁔮􁕹􁌱􀫄
􁃛􀌶GC 􀩒􀥒􀔭 F-Queue 􀓾􁌱􀩒􁨝􁬰􁤈􁒫􀔫􀽺􁤩􀺽􁦕􀒅􁬯􀷸􀒅􁧆􀩒􁨝􀩙􁤩
􁑏􁴻” 􀜨􀩙􀢧􀶭” 􁵞􀝳􀒅􁒵􀮇􀢧􀶭􀌶
7􀌵􀣯􀣍􀢧􀶭􁌱􀕽􁅩􀞾􀜻􁉘􀌶􀬚􁘍􁡤 2 􁐿􀢧􀶭􀹢􀚫􀌶
Java 􁧍􁥺􀓾􀓞􀓻􀸔􁟪􁌱􁇙􁅩􀩪􀸎􀭚􀙁􀔧􀣯􀣍􀢧􀶭􀹢􀚫􀒅􀖵 C++ 􁑕􀬧􀞧􀹋
􀥧􁋢􁌱􀙖􀨂􁓕􁉘􁌱􁳯􁷌􁬨􀚒􁘒􁥴􀒅􀨙􀖵􀮑 Java 􁑕􀬧􀞧􀣁 􁖫􀙟􁑕􀬧􁌱􀷸􀗲
􀓧􀙚􁵱􁥝􁘍􁡤􀙖􀨂􁓕􁉘􀌶􁊧􀔭􀹍􀓻􀣯􀣍􀢧􀶭􀹢􀚫􀒅 Java 􀓾􁌱􀩒􁨝􀓧􀙚
􀹍“􀖢􁊠􀤒”􁌱􀼷􀮷􀒅􀝝􀹍􀩒􁨝􁌱􀭚􁊠􀲍􀹍"􀖢􁊠􀤒"􀌶􀣯􀣍􀢧􀶭􀝢􀕦􀹍􀶴􁌱
􁴠􀾊􀙖􀨂􁀡􁶂􀒅􀹍􀶴􁌱􀖵􁊠􀝢􀕦􀖵 􁊠􁌱􀙖􀨂􀌶􀣯􀣍􀢧􀶭􀢏􁭗􀬉􀸎􀖢􀔅􀓞􀓻
􀜔􁇿􁌱􀖗􁕆􀚦􁌱􁕚􁑕􁬩􁤈􀒅 􀓧􀝢􁶼􁎣􁌱􀰘􀙭􀓥􀩒􀙖􀨂􀤞􀓾􀫪􁕪􀾒􀔹􁌱􀱲􁘏
􁳩􀷸􁳵􁀌􀹍􀖵􁊠􁌱 􀩒􁨝􁬰􁤈􁂴􀼩􀞾􀢧􀶭􀒅􁑕􀬧􀞧􀓧􁚆􀨫􀷸􁌱􁧣􁊠􀣯􀣍􀢧􀶭
􀢏􀩒􀺤􀓻􀩒 􁨝􀱲􀲅􀹍􀩒􁨝􁬰􁤈􀣯􀣍􀢧􀶭􀌶
􀢧􀶭􀹢􀚫􀹍􀚓􀕤􀥔􀚫􀣯􀣍􀢧􀶭􀞾􀺽􁦕􀣯􀣍􀢧􀶭􀒅􀥀􁰁􀣯􀣍􀢧􀶭􀌶
8􀌵􀣯􀣍􀢧􀶭􀢏􁌱􀤚􀹜􀜻􁉘􀸎􀕋􀔍?􀣯􀣍􀢧􀶭􀢏􀝢􀕦􁸘􀓤􀢧􀶭􀙖􀨂􀞀?
􀹍􀕋􀔍􀛐􁀩􀔆􀛖􁭗􁎣􁡦􀳙􀹢􁬰􁤈􀣯􀣍􀢧􀶭?
􀩒􀔭 GC 􀹶􁧔􀒅􀭮􁑕􀬧􀞧􀚠􀭌􀩒􁨝􀷸􀒅GC 􀩪􀭏􀦤􁍊􀴴􁬯􀓻􀩒􁨝 􁌱􀣈􀣎􀌵
􀥟􀩜􀕦􀝊􀖵􁊠􀰘􀙭􀌶􁭗􀬉􀒅GC 􁯻􁊠􀹍􀝻􀢶􁌱􀷜􀭗􁦕􀭯􀞾 􁓕􁉘􀤞(heap)􀓾
􁌱􀲅􀹍􀩒􁨝􀌶􁭗􁬦􁬯􁐿􀷜􀭗􁏟􀨧􀟺􀔶􀩒􁨝􀸎” 􀝢􁬡􁌱”􀒅􀟺􀔶􀩒􁨝􀸎”􀓧􀝢􁬡
􁌱”􀌶􀭮 GC 􁏟􀨧􀓞􀔶􀩒􁨝􀔅“􀓧 􀝢􁬡”􀷸􀒅GC 􀩪􀹍􁨱􀕱􀢧􀶭􁬯􀔶􀙖􀨂􁑮
􁳵􀌶􀝢􀕦􀌶􁑕􀬧􀞧􀝢􀕦􀲋􀛖􀲗􁤈 System.gc() 􀒅􁭗􁎣 GC 􁬩􁤈􀒅􀖕􀸎
Java 􁧍􁥺􁥢􁝜􀬚􀓧 􀗛􁦤 GC 􀓞􀨧􀕿􀲗􁤈􀌶
9􀌵Java 􀓾􀕿􀨂􀣁􀙖􀨂􁀡􁄋􀞀􀒅􁧗􁓌􀜔􀵈􁬿􀌶
􀲅􁧲􀙖􀨂􁀡􁶂􀩪􀸎􀳰􀓞􀓻􀓧􀙚􁤩􁑕􀬧􀖵􁊠􁌱􀩒􁨝􀱲􀝒􁰁􀓞􁍗􁤩􀜛 􀴝􀣁􀙖􀨂
􀓾􀌶Java 􀓾􀹍􀣯􀣍􀢧􀶭􀹢􀚫􀒅􀨙􀝢􀕦􀗛􁦤􀓞􀩒􁨝􀓧􀙚􁤩 􀭚􁊠􁌱􀷸􀗲􀒅􀜨
􀩒􁨝􀝒􀱮􀔧􀨋􀘯􁌱􀷸􀗲􀒅􀩒􁨝􀩙􁛔􀛖􁤩􀣯􀣍􀢧􀶭􀢏 􀕗􀙖􀨂􀓾􁂴􁴻􀴧􀌶􁊧􀔭
Java 􀖵􁊠􀹍􀝻􀢶􁌱􀷜􀭗􁬰􁤈􀣯􀣍􀢧􀶭􁓕􁉘􀒅 􀝢􀕦􁁾􁴻􀭚􁊠􀮗􁈾􁌱􁳯􁷌􀒅
􀖺􀦇􀹍􀓷􀓻􀩒􁨝􀒅􁍘􀔰􀭚􁊠􀒅􀝝􁥝􀨙􀕪 􀞾􀻑􁬰􁑕􀓧􀝢􁬡􁌱􀒅􁮎􀔍 GC 􀔞􀸎
􀝢􀕦􀢧􀶭􀨙􀕪􁌱􀒅􀖺􀦇􀓥􁶎􁌱 􀕤􁎱􀝢􀕦􁍡􀚩􁬯􁐿􀰘􀙭􁌱􀙖􀨂􀢧􀶭:
import java.io.IOException; public class GarbageTest {
/**
* @param args
* @throws IOException
*/
public static void main(String[] args) throws IOException {
// TODO Auto-generated method stub
try { gcTest();
} catch (IOException e) {
// TODO Auto-generated catch block
e.printStackTrace();
}
System.out.println("has exited gcTest!"); System.in.read();
System.in.read(); System.out.println("out begin gc!"); for(int
i=0;i<100;i++)
{
System.gc();
System.in.read();
System.in.read(); }
}
private static void gcTest() throws IOException {
System.in.read();
System.in.read();
Person p1 = new Person(); System.in.read();
System.in.read();
Person p2 = new Person();
p1.setMate(p2);
p2.setMate(p1);
System.out.println("before exit gctest!"); System.in.read();
System.in.read();
System.gc(); System.out.println("exit gctest!");
}
private static class Person {
byte[] data = new byte[20000000]; Person mate = null;
public void setMate(Person other) {
mate = other;
}
}
}
Java 􀓾􁌱􀙖􀨂􁀡􁶂􁌱􀰘􀙭:􁳩􁊞􀞸􀞮􀹗􁌱􀩒􁨝􀳮􀹍􁎨􁊞􀞸􀞮􀹗􀩒 􁨝􁌱􀭚􁊠
􀩪􀮉􀝢􁚆􀝎􁊞􀙖􀨂􁀡􁶂􀒅􀩱􁓕􁎨􁊞􀞸􀞮􀹗􀩒􁨝􀫪􁕪􀓧􀙚􁵱 􁥝􀒅􀖕􀸎􀢩􀔅􁳩
􁊞􀞸􀞮􀹗􀩒􁨝􀳮􀹍􀨙􁌱􀭚􁊠􁘒􀩕􁛘􀓧􁚆􁤩􀢧􀶭􀒅􁬯 􀩪􀸎 Java 􀓾􀙖􀨂􁀡􁶂
􁌱􀝎􁊞􀣋􀸧􀒅􁭗􀗗􀣈􁧔􀒅􀩪􀸎􁑕􀬧􀞧􀝢􁚆􀚠 􀭌􀔧􀓞􀓻􀩒􁨝􀒅􀕦􀝸􀓞􁍗􀓧􀙚
􀖵􁊠􁬯􀓻􀩒􁨝􀒅􁬯􀓻􀩒􁨝􀜩􀓞􁍗􁤩􀭚 􁊠􀒅􀜨􁬯􀓻􀩒􁨝􀷫􁊠􀖕􀸎􀜩􀷫􁀩􁤩􀣯
􀣍􀢧􀶭􀢏􀢧􀶭􁌱􀒅􁬯􀩪􀸎 java 􀓾􀝢􁚆􀚊􁈿􀙖􀨂􁀡􁶂􁌱􀰘􀙭􀒅􀖺􀦇􀒅􁖨􀨂􁔮
􁕹􀒅􀱯􀕪􀛒􁫹􀔧􀓞􀓻􀩒 􁨝􀶱􀣁􁖨􀨂􀓾 (􀖺􀦇􀶱􀣁􀓞􀓻􀙂􀩴 map 􀩒􁨝􀓾)􀒅
􁆐􀝸􀓞􁍗􀓧􀙚 􀖵􁊠􀨙􀒅􁬯􀓻􀩒􁨝􀓞􁍗􁤩􁖨􀨂􀭚􁊠􀒅􀖕􀜩􀓧􀙚􁤩􀖵􁊠􀌶
􀼄􀺱 Java 􀓾􁌱􀙖􀨂􁀡􁶂􀒅􀓞􀨧􁥝􁦏􁑕􀬧􀩙􀝱􁐿􀚓􀶪􀰘􀙭􁮷􀨠􀷆􀲗 􁤈􀚩􁑕
􀬧􁕮􀹳􀒅􁆐􀝸􁍡􀺤􀓻􀩒􁨝􀸎􀞈􁤩􀖵􁊠􁬦􀒅􀦇􀺎􁀌􀹍􀒅􀚞􀲍􁚆 􀚣􀨧􁬯􀓻􀩒􁨝
􀪂􀔭􀙖􀨂􁀡􁶂􀌶
􀦇􀺎􀓞􀓻􀥘􁮱􁔄􁌱􀨫􀖺􀩒􁨝􁌱􀷜􁀩􁬬􀢧􀔧􀓞􀓻􀙖􁮱􁔄􁌱􀨫􀖺􀩒􁨝􀒅 􁬯􀓻􀙖
􁮱􁔄􀩒􁨝􁤩􁳩􀹗􀭚􁊠􀔧􀒅􀜨􀖵􁮎􀓻􀥘􁮱􁔄􀨫􀖺􀩒􁨝􀓧􀙚􁤩􀖵 􁊠􀒅􀖕􁊧􀔭􀙖
􁮱􁔄􀳮􀔋􀥘􁮱􁔄􁌱􀨫􀖺􀩒􁨝􀒅􁬯􀓻􀥘􁮱􁔄􀩒􁨝􀩙􀓧􀕿 􁤩􀣯􀣍􀢧􀶭􀒅􁬯􀔞􀕿
􁭜􀱮􀙖􀨂􁀡􁶂􀌶
􀓥􁶎􀙖􀨻􀹶􁛔􀔭􁗑􀓤(􀔆􁥝􁇙􁅩􀩪􀸎􁂴􁑮􀤞􀺾􀓾􁌱􀺤􀓻􀘲􁔰􀒅􀬚􀓧 􀸎􀮁􀬬
􀲩􀨙􀕗􀷄􁕟􀓾􀳭􀴧􀒅􁘒􀸎􀲩􀨂􀘙􁌱􀯛􀷄􀙺􀩝􀒅􀹜􀕈􀙟􀮑􀝢􀕦 􀾲􁬯􀓻􀦅􀒅􀣁
􀳭􀴧􀺤􀓻􀘲􁔰􀷸􀒅􁶲􀗎􀔞􁦏􀨙􀕗􀷄􁕟􀓾􁁾􀥦􀒅􀩙􁮎􀓻 􀘲􁔰􀲅􀣁􁌱􀖖􁗝􁌱􊧊
􁦡􁗝􀔅 null 􀜨􀝢):
􀱯􀨫􀣁􀰮􀓧􀚩􀾲􁮎􀓻􀤞􀺾􀹅􁕪􀙎􁌱􀖺􀧼􀔧􀒅􀕦􁛘􀔭􀱯􁬮􁥝􀭚􁊠􀚦􀕈 􁌱􀖺
􀧼􀒅􀓥􁶎􁌱􀖺􀧼􀓧􀸎􀱯􀰮􀚩􁌱􀒅􀸎􀔡􀓤􁍡􀚩􁌱􀒅􀭮􁆐􀦇􀺎􁀌􀹍 􀣁􀔡􀓤􁍡
􀚩􀒅􀝢􁚆􁬦􀓞􀾧􀷸􁳵􀱯􁛔􀫩􀔞􀰮􁌱􀚩􀒅􀝢􀸎􁮎􀷸􀱯􁧔􀸎􀱯 􁛔􀫩􀰮􀚩􁌱􀔞􁀌
􀹍􀕈􁍘􀗞􁌱􀌶
public class Stack {
private Object[] elements=new Object[10]; private int size = 0
;
public void push(Object e){
ensureCapacity();
elements[size++] = e;
}
public Object pop(){
if( size == 0) throw new EmptyStackException(); return element
s[--size];
}
private void ensureCapacity(){ if(elements.length == size){
Object[] oldElements = elements;
elements = new Object[2 * elements.length+1]; System.arraycopy
(oldElements,0, elements, 0,
size);
}
}
}
􀓤􁶎􁌱􀜻􁉘􀬫􁧆􀮉􁓌􀜔􀒅􀘃􀦇􀤞􀺾􀛒􀔧 10 􀓻􀘲􁔰􀒅􁆐􀝸􀙂􁮱􀭨 􀚊􀹶􀒅􁡱
􁆐􀤞􀺾􀸎􁑮􁌱􀒅􁀌􀹍􀱯􀕪􁥝􁌱􀓳􁥜􀒅􀖕􀸎􁬯􀸎􀓻􀩒􁨝􀸎􀷫 􁀩􀢧􀶭􁌱􀒅􁬯􀓻
􀲍􁒧􀝳􀔧􀙖􀨂􁀡􁶂􁌱􀓷􀓻􀹵􀕯:􀷫􁊠􀒅􀷫􁀩􀢧􀶭􀌶 􀖕􀸎􀩪􀸎􀨂􀣁􁬯􀻏􁌱􀓳
􁥜􀔞􀓧􀓞􀨧􀕿􀩕􁛘􀕋􀔍􀻏􁌱􀝸􀺎􀒅􀦇􀺎􁬯􀓻 􀤞􀺾􁊠􁌱􀾲􁫾􀩝􀒅􀔞􀩪􁁵􁩇􀔧
􀙾􀓻 K 􀙖􀨂􁘒􀫪􀒅􀝍􀾋􀱯􀕪􁌱􀙖􀨂􁮷 􀓤 G 􀔧􀒅􀟺􁯾􀕿􀹍􀕋􀔍􀭽􀟥􀒅􀙚􁧔
􁬯􀓻􀓳􁥜􀮉􀮳􀩪􀕿􁤩􀢧􀶭􁌱􀒅 􀹍􀕋􀔍􀙉􁔮􀌶􀓥􁶎􁍡􀓷􀓻􀖺􀧼􀌶
public class Bad{
public static Stack s=Stack(); static{
s.push(new Object());
s.pop(); //􁬯􁯾􀹍􀓞􀓻􀩒􁨝􀝎􁊞􀙖􀨂􁀡􁶂
s.push(new Object()); //􀓤􁶎􁌱􀩒􁨝􀝢􀕦􁤩􀢧􀶭􀔧􀒅􁒵􀔭􀸎􁛔 􀰶􀔧
}
}
􀢩􀔅􀸎 static􀒅􀩪􀓞􁍗􀨂􀣁􀚩􁑕􀬧􁭅􀚊􀒅􀖕􀸎􀱯􀕪􀔞􀝢􀕦􁍡􀚩􀨙􀹍 􁛔􀰶􀛑
􁚆􀒅􀩪􀸎􁧔􀦇􀺎􀖦􁌱 Stack 􀹋􀥚􀹍 100 􀓻􀩒􁨝􀒅􁮎􀔍􀹋 􀥚􀔞􀩪􀝝􀹍 100
􀓻􀩒􁨝􀷫􁀩􁤩􀢧􀶭􀙌􀨫􁬯􀓻􀬫􁧆􀮉􀨻􀸃􁉘􁥴􀒅 Stack 􀙖􁮱􀳮􀹍 100 􀓻􀭚
􁊠􀒅􀹋􀣕􁌱􀰘􀙭􀩪􀸎􀕜􀕪􁮷􀸎􀷫􁊠􁌱􀒅 􀢩􀔅􀱯􀕪􀓞􀷮􀶱􀷛􁌱􁬰􀝐􀒅􀕦􀚹􁌱
􀭚􁊠􁛔􁆐􁁾􀥦!
􀙖􀨂􁀡􁶂􁌱􀝚􀥘􀓞􁐿􀰘􀙭:􀭮􀓞􀓻􀩒􁨝􁤩􀨂􀘙􁬰 HashSet 􁵞􀝳􀓾 􀕦􀝸􀒅􀩪
􀓧􁚆􀗥􀶯􁬯􀓻􀩒􁨝􀓾􁌱􁮎􀔶􀝇􀓨􁦇􁓒􀟢􀫶􊧊􁌱􀨁􀾧􀔧􀒅􀞈 􀚞􀒅􀩒􁨝􀗥􀶯􀝸
􁌱􀟢􀫶􊧊􀓨􀹋􀚡􀨂􀘙􁬰 HashSet 􁵞􀝳􀓾􀷸􁌱􀟢􀫶 􊧊􀩪􀓧􀝶􀔧􀒅􀣁􁬯􁐿􀰘
􀙭􀓥􀒅􀜨􀖵􀣁 contains 􀷜􁀩􀖵􁊠􁧆􀩒􁨝􁌱 􀭮􀚹􀭚􁊠􀖢􀔅􁌱􀝇􀷄􀝄
HashSet 􁵞􀝳􀓾􀼄􁔱􀩒􁨝􀒅􀔞􀩙􁬬􀢧􀲤􀓧 􀚩􀩒􁨝􁌱􁕮􀺎􀒅􁬯􀔞􀕿􀩕􁛘􀷫􁀩
􀕗 HashSet 􁵞􀝳􀓾􀜔􁇿􀚢􁴻􀭮􀚹 􀩒􁨝􀒅􁭜􀱮􀙖􀨂􁀡􁶂􀌶
10􀌵􁂮􀳩􁨬􀞾􁁠􀳩􁨬􀌶
􁓌􀜔􀹶􁦖􀩪􀸎􀥔􀚫􀌵􀘸􁵇􀌶
Person p=new Person(“􀭟􀓣”);
􁁠􀳩􁨬􀩪􀸎􀩒􀩒􁨝􀓾􁌱􀷄􀴝􀱮􀞧􁬰􁤈􁓌􀜔􁩙􊧊􀒅􀦇􀺎􀨂􀣁􀛖􀮾􀱮􀞧
􀱲􁘏􀳰􁰒􀩪􀕿􀲸􁲙􀌶
􁂮􀳩􁨬􀩪􀸎􀩒􀩒􁨝􀓾􀨂􀣁􁌱􀛖􀮾􀱮􀞧􀱲􀳰􁰒􁯿􀷛􀭏􁬗􀙖􀨂􁑮􁳵􀌶
11􀌵System.gc() 􀞾 Runtime.gc() 􀕿􀘉􀕋􀔍􀔪􀰘?
􁬯􀓷􀓻􀷜􁀩􁊠􀹶􀵉􁐏 JVM 􁥝􁬰􁤈􀣯􀣍􀢧􀶭􀌶􀖕􀸎􀒅􁒈􀜨􀭏􀦤􁬮􀸎 􀭊􁬴􁬰
􁤈􀣯􀣍􀢧􀶭􀸎􀝐􀙬􀔭 JVM 􁌱􀌶
12􀌵finalize() 􀷜􁀩􀕋􀔍􀷸􀗲􁤩􁧣􁊠?􀺉􀺅􀚍􀷄 (finalization) 􁌱 􁍓􁌱􀸎􀕋
􀔍?
􀣯􀣍􀢧􀶭􀢏(garbage colector)􀙬􀨧􀢧􀶭􀺤􀩒􁨝􀷸􀒅􀩪􀕿􁬩􁤈􁧆 􀩒􁨝􁌱
finalize() 􀷜􁀩 􀖕􀸎􀣁 Java 􀓾􀮉􀓧􀬛􀒅􀦇􀺎􀙖􀨂􀯛􀸎􊧌 􁪃􁌱􀒅􁮎􀔍􀣯􀣍􀢧
􀶭􀝢􁚆􀿞􁬱􀓧􀕿􁬰􁤈􀒅􀔞􀩪􀸎􁧔 filalize() 􀝢􁚆 􀿞􁬱􀓧􁤩􀲗􁤈􀒅􀸔􁆐􀳰􀹕􀨙
􀘉􀶭􀩲􀫡􀖢􀸎􁶌􀓧􀖘􁌱􀌶 􁮎􀔍 finalize() 􁑪􁒌􀸎􀘉􀕋􀔍􁌱􀞫? 􀨙􀹋􀔆􁥝􁌱􁊠
􁭔􀸎􀢧􀶭􁇙􀾛􁃀􁭲 􁊩􁧗􁌱􀙖􀨂􀌶Java 􁑕􀬧􀹍􀣯􀣍􀢧􀶭􀢏􀒅􀲅􀕦􀓞􁛱􀰘􀙭
􀓥􀙖􀨂􁳯􁷌 􀓧􁊠􁑕􀬧􀞧􀶙􀮞􀌶􀖕􀹍􀓞􁐿 JNI(Java Native Interface)􁧣􁊠
non-Java 􁑕􀬧(C 􀱲 C++)􀒅 finalize() 􁌱􀫡􀖢􀩪􀸎􀢧􀶭􁬯􁮱 􀚓􁌱􀙖􀨂􀌶
13􀌵􀦇􀺎􀩒􁨝􁌱􀭚􁊠􁤩􁗝􀔅 null􀒅􀣯􀣍􀶭􁵞􀢏􀸎􀞈􀕿􁒈􀜨􁯽􀶱􀩒􁨝􀜛 􁊠􁌱
􀙖􀨂?
􀓧􀕿􀒅􀣁􀓥􀓞􀓻􀣯􀣍􀢧􀶭􀞮􀹗􀓾􀒅􁬯􀓻􀩒􁨝􀩙􀸎􀝢􁤩􀢧􀶭􁌱􀌶
14􀌵􀕋􀔍􀸎􀚓􀫲􀭗􀣯􀣍􀢧􀶭(DGC)?􀨙􀸎􀦇􀖜􀫡􀖢􁌱?
DGC 􀝞􀘉􀚓􀫲􀭗􀣯􀣍􀢧􀶭􀌶RMI 􀖵􁊠 DGC 􀹶􀘉􁛔􀛖􀣯􀣍􀢧􀶭􀌶 􀢩􀔅 RMI
􀛱􀞌􀔧􁪜􁡦􀳙􀹢􁌱􁬱􁑕􀩒􁨝􁌱􀭚􁊠􀒅􀣯􀣍􀢧􀶭􀸎􀮉􀢯􁵙 􁌱􀌶DGC 􀖵􁊠􀭚
􁊠􁦇􀷄􁓒􁀩􀹶􁕳􁬱􁑕􀩒􁨝􀵉􀗀􁛔􀛖􀙖􀨂􁓕􁉘􀌶
15􀌵􀔀􁤈(serial)􀶭􁵞􀢏􀞾􀞃􀝺􁰁(throughput)􀶭􁵞􀢏􁌱􀜄􀚦 􀸎􀕋􀔍?
􀞃􀝺􁰁􀶭􁵞􀢏􀖵􁊠􀬚􁤈􁇇􀹜􁌱􀷛􁊞􀕤􀣯􀣍􀶭􁵞􀢏􀒅􀨙􁊠􀔭􀓾􁒵􁥢􀽜 􀞾􀥟􁥢
􀽜􀷄􀴝􁌱􀬫􁊠􁑕􀬧􀌶 􁘒􀔀􁤈􀶭􁵞􀢏􀩒􀥟􀥚􀷄􁌱􀩜􀬫􁊠(􀣁 􁈿􀕤􀥒􁉘􀢏􀓤􁵱
􁥝􀥟􀼷 100M 􀫢􀝦􁌱􀙖􀨂)􀩪􁪃􀥜􀔧􀌶
16􀌵􀣁 Java 􀓾􀒅􀩒􁨝􀕋􀔍􀷸􀗲􀝢􀕦􁤩􀣯􀣍􀢧􀶭?
􀭮􀩒􁨝􀩒􀭮􀚹􀖵􁊠􁬯􀓻􀩒􁨝􁌱􀬫􁊠􁑕􀬧􀝒􀮑􀓧􀝢􁥶􀝊􁌱􀷸􀗲􀒅􁬯􀓻 􀩒􁨝􀩪
􀝢􀕦􁤩􀢧􀶭􀔧􀌶
17􀌵􁓌􁬿 Java 􀙖􀨂􀚓􁯈􀓨􀢧􀶭􁒽􁈲􀕦􀝊 Minor GC 􀞾 Major GC􀌶
• 􀩒􁨝􀕽􀘶􀣁􀤞􁌱 Eden 􀜄􀚓􁯈
• 􀥟􀩒􁨝􁍗􀴳􁬰􀙁􁘌􀬙􀕤
• 􁳩􀹗􀨂􁁚􁌱􀩒􁨝􀩙􁍗􀴳􁬰􀙁􁘌􀬙􀕤
􀭮 Eden 􀜄􁀌􀹍􁪃􀥜􁌱􁑮􁳵􁬰􁤈􀚓􁯈􀷸􀒅􁡦􀳙􀹢􀕿􀲗􁤈􀓞􀽺 Minor GC􀌶
Minor GC 􁭗􀬉􀝎􁊞􀣁􀷛􁊞􀕤􁌱 Eden 􀜄􀒅􀣁􁬯􀓻􀜄 􁌱􀩒􁨝􁊞􀨂􀹗􁎨􀒅􀮃
􀮃􀝎􁊞 Gc 􁌱􁷇􁈲􁫾􁹛􀒅􀢧􀶭􁭛􀬶􀾲􁫾􀮳; Full GC/Major GC 􀝎􁊞􀣁􁘌􀬙
􀕤􀒅􀓞􁛱􀰘􀙭􀓥􀒅􁥶􀝎􁘌􀬙􀕤 GC 􁌱􀷸􀗲􀓧􀕿􁥶􀝎 Minor GC􀒅􀖕􀸎􁭗􁬦
􁯈􁗝􀒅􀝢􀕦􀣁 Full GC 􀔏 􀚹􁬰􁤈􀓞􀽺 Minor GC 􁬯􀻏􀝢􀕦􀛒􀮳􁘌􀬙􀕤􁌱􀢧
􀶭􁭛􀬶􀌶
18􀌵JVM 􁌱􀿞􀔋􀕤􀓾􀕿􀝎􁊞􀣯􀣍􀢧􀶭􀔍?
􀣯􀣍􀢧􀶭􀓧􀕿􀝎􁊞􀣁􀿞􀔋􀕤􀒅􀦇􀺎􀿞􀔋􀕤􁃿􀔧􀱲􁘏􀸎􁩻􁬦􀔧􀔁􁊴􊧊􀒅 􀕿􁥶
􀝎􀨠􀙂􀣯􀣍􀢧􀶭(Full GC)􀌶
􁀳: Java 8 􀓾􀫪􁕪􁑏􁴻􀔧􀿞􀔋􀕤􀒅􀷛􀛒􀔧􀓞􀓻􀝞􀘉􀘲􀷄􀴝􀜄􁌱 native 􀙖􀨂
􀜄􀌶
19􀌵Java 􀓾􀣯􀣍􀶭􁵞􁌱􀷜􁀩􀹍􀟺􀔶?
􀺽􁦕 - 􁂴􁴻:􁬯􀸎􀣯􀣍􀶭􁵞􁓒􁀩􀓾􀹋􀤚􁏐􁌱􀒅􀻑􀴝􀝷􀨁􀩪􀝢􀕦􁎣 􁭲􀒅􀨙􁌱
􀯏􀰮􀩪􀸎􀺽􁦕􀟺􀔶􁥝􁤩􀢧􀶭􁌱􀩒􁨝􀒅􁆐􀝸􁕹􀓞􀢧􀶭􀌶􁬯􁐿 􀷜􁀩􀮉􁓌􀜔􀒅􀖕
􀸎􀕿􀹍􀓷􀓻􀔆􁥝􁳯􁷌:
1. 􀶴􁈲􀓧􁹛􀒅􀺽􁦕􀞾􁂴􁴻􁌱􀶴􁈲􁮷􀮉􀖗;
2. 􀕿􀔾􁊞􀥟􁰁􀓧􁬳􁖅􁌱􀙖􀨂􁏦􁇆􀒅􀩕􁛘􀕦􀝸􁑕􀬧􀣁􀚓􁯈􁫾􀥟􁌱
􀩒􁨝􀷸􀒅􁊧􀔭􁀌􀹍􊧌􁪃􁌱􁬳􁖅􀙖􀨂􁘒􀵉􀚹􁥶􀝎􀓞􀽺 GC 􀛖􀖢􀌶
􀥔􀚫􁓒􁀩:􀔅􀔧􁥴􀙬􀶴􁈲􁳯􁷌􀒅􀥔􀚫􁓒􁀩􀩙􀝢􁊠􀙖􀨂􀳲􀨻􁰁􀚚􀚓􀔅􁍘􁒵􁌱􀓷
􁮱􀚓􀒅􁆐􀝸􀾯􀽺􀝝􀖵􁊠􀙌􀓾􁌱􀓞􀣘􀒅􀭮􀓞􀣘􀙖􀨂􁊠􀨠􀷸􀒅􀩪􀩙􁬮􀨂􁁚􁌱􀩒
􁨝􀥔􀚫􀚩􁒫􀔫􀣘􀙖􀨂􀓤􀒅􁆐􀝸􀓞􀽺􀯔􁂴􀼩􀨠􁒫􀓞􀣘􀙖􀨂􀒅􀙚􀩙􁒫􀔫􀣘􀓤􁌱
􀩒􁨝􀥔􀚫􀚩􁒫􀓞􀣘􀌶􀖕􀸎􁬯􁐿􀷜􀭗􀒅􀙖􀨂􁌱􀕤􀕰􀥡􁹛􀒅􀾯􀽺􀤚􀹜􀓤􁮷􁥝􁁵
􁩇􀓞􁛱􁌱􀙖􀨂􀌶
􀔭􀸎􀩙􁧆􁓒􁀩􁬰􁤈􀔧􀶯􁬰􀒅􀙖􀨂􀜄􀤒􀓧􀙚􀸎􀳲􁆙 1:1 􀝄􀚚􀚓􀒅􁘒 􀸎􀩙􀙖􀨂
􀚚􀚓􀔅 8:1:1 􀓣􁮱􀚓􀒅􁫾􀥟􁮎􀕲􀙖􀨂􀔻 Eden 􀜄􀒅􀙌􀖟 􀸎􀓷􀣘􁫾􀩜􁌱􀙖􀨂
􀜄􀝞 Survior 􀜄􀌶􀾯􀽺􁮷􀕿􀕽􀘶􀖵􁊠 Eden 􀜄􀒅 􁝑 Eden 􀜄􁃿􀒅􀩪􀩙􀩒􁨝
􀥔􀚫􀚩􁒫􀔫􀣘􀙖􀨂􀜄􀓤􀒅􁆐􀝸􁂴􁴻 Eden 􀜄􀒅􀦇􀺎􀾌􀷸􀨂􁁚􁌱􀩒􁨝􀥡􀥚􀒅
􀕦􁛗􀔭 Survivor 􀓧􀥜􀷸􀒅􀕿􀩙􁬯 􀔶􀩒􁨝􁭗􁬦􀚓􁯈􀳅􀗛􀹢􀚫􀥔􀚫􀚩􁘌􀬙􀕤
􀓾􀌶(java 􀤞􀝈􀚓􀔅􀷛􁊞􀕤􀞾􁘌􀬙􀕤)
􀺽􁦕 - 􀷆􁉘:􁧆􁓒􁀩􀔆􁥝􀸎􀔅􀔧􁥴􀙬􀺽􁦕 - 􁂴􁴻􀒅􀔾􁊞􀥟􁰁􀙖􀨂 􁏦􁇆􁌱􁳯
􁷌;􀭮􀩒􁨝􀨂􁁚􁈲􁫾􁹛􀷸􀒅􀔞􁥴􀙬􀔧􀥔􀚫􁓒􁀩􁌱􀶴􁈲􁳯􁷌􀌶 􀨙􁌱􀓧􀝶􀔏􀥒
􀩪􀸎􀣁􁂴􁴻􀩒􁨝􁌱􀷸􀗲􁈿􀩙􀝢􀢧􀶭􀩒􁨝􁑏􀛖􀚩􀓞􁒒􀒅 􁆐􀝸􁂴􁴻􀴧􁒒􁬟􁊴􀕦
􀥘􁌱􀩒􁨝􀒅􁬯􀻏􀩪􀓧􀕿􀔾􁊞􀙖􀨂􁏦􁇆􀔧􀌶
􀚓􀕤􀶭􁵞:􁈿􀣁􁌱􁡦􀳙􀹢􀣯􀣍􀶭􁵞􀥟􀥚􁯻􁊠􁬯􁐿􀷜􀭗􀒅􀨙􀻑􀴝􀩒􁨝􁌱􁊞􀨂􀞮
􀹗􀒅􀩙􀤞􀚓􀔅􀷛􁊞􀕤􀞾􁘌􀬙􀕤􀌶􀣁􀷛􁊞􀕤􀓾􀒅􁊧􀔭􀩒􁨝􁊞􀨂􀹗􁎨􀒅􀾯􀽺􀢧
􀶭􁮷􀕿􀹍􀥟􁰁􀩒􁨝􀾒􀝄􀒅􁮎􀔍􁬯􀷸􀩪􁯻􁊠􀥔􀚫􁓒􁀩􀌶 􁘌􀬙􀕤􁯾􁌱􀩒􁨝􀨂􁁚
􁈲􁫾􁹛􀒅􁀌􀹍􁷐􀥘􁌱􁑮􁳵􁬰􁤈􀚓􁯈􀳅􀗛􀌶
20􀌵􀕋􀔍􀸎􁔄􀛒􁫹􀢏􀒅􁔄􀛒􁫹􀢏􀹍􀟺􀔶?
􀨫􁈿􁭗􁬦􁔄􁌱􀹦􁴴􀨧􀝷􁞴􀝐􁧆􁔄􁌱􀔫􁬰􀚫􀨁􁜓􁁞􁌱􀕤􁎱􀣘􀝞􀘉􁔄􀛒􁫹􀢏􀌶
􀔆􁥝􀹍􀓞􀓥􀢥􁐿􁔄􀛒􁫹􀢏:
• 􀞐􀛖􁔄􀛒􁫹􀢏(BootstrapClassLoader)􁊠􀹶􀛒􁫹Java􀻐 􀮞􁔄􀬪􀒅􀷫􁀩􁤩
Java 􁑕􀬧􁍗􀴳􀭚􁊠􀌶
• 􀲘􀪀􁔄􀛒􁫹􀢏(extensions class loader):􀨙􁊠􀹶􀛒􁫹 Java 􁌱􀲘􀪀􀬪􀌶Java
􁡦􀳙􀹢􁌱􀨫􁈿􀕿􀵉􀗀􀓞􀓻􀲘􀪀􀬪􁍓􀭯􀌶􁧆􁔄 􀛒􁫹􀢏􀣁􀾌􁍓􀭯􁯾􁶎􀺱􀲤􀬚􀛒
􁫹 Java 􁔄􀌶
• 􁔮􁕹􁔄􀛒􁫹􀢏(system class loader):􀨙􀻑􀴝 Java 􀬫􁊠 􁌱􁔄􁪠􀮆
(CLASSPATH)􀹶􀛒􁫹 Java 􁔄􀌶􀓞􁛱􀹶􁧔􀒅Java 􀬫􁊠􁌱􁔄􁮷􀸎􁊧􀨙􀹶􀨠􀱮
􀛒􁫹􁌱􀌶􀝢􀕦􁭗􁬦 ClassLoader.getSystemClassLoader() 􀹶􁞴􀝐􀨙􀌶
• 􁊠􀲁􁛔􀨧􀔎􁔄􀛒􁫹􀢏􀒅􁭗􁬦􁖀􀲥 java.lang.ClassLoader 􁔄 􁌱􀷜􀭗􀨫􁈿􀌶
21􀌵􁔄􀛒􁫹􀢏􀝌􀕅􀦩􁁝􀽜􀣳􀹢􀚫?
􀭮􀓞􀓻􁔄􀶭􀚩􀔧􁔄􀛒􁫹􁧗􀿢􀷸􀒅􀓧􀕿􁛔􀫩􀘶􀝄􀛒􁫹􁬯􀓻􁔄􀒅􁘒􀸎􀩙􀙌􀦩􁁝
􁕳􁆿􁔄􀒅􁊧􁆿􁔄􀝄􀛒􁫹􀒅􀦇􀺎􀾌􀷸􁆿􁔄􀓧􁚆􀛒􁫹􀒅􀝍􁸇􁕳􀧼􁔄􀒅􁊧􀧼􁔄􀝄
􀨠􀱮􁔄􁌱􀛒􁫹􀌶
3􀌵Mysql􀯔􁚆􀕽􀛸􀷆􁉘
1􀌵SpringCloud􁶎􁦶􀷆􁉘
1􀌵􀕋􀔍􀸎 Spring Cloud?
􀔫􀌵􀮙􀹐􀛓􀺝􀺅􁶎􁦶􀓫􀻄
Spring cloud 􁁞􀬫􁊠􁑕􀬧􀞐􀛖􀢏􀸎􀤚􀔭 Spring Boot 􁌱 Spring 􁵞􀱮􀬫􁊠􁑕
􀬧􀒅􀵉􀗀􀓨􀥘􁮱􁔮􁕹􁌱􁵞􀱮􀌶 Spring cloud Task􀒅􀓞􀓻􁊞􀞸􀞮􀹗􁎨􀸮􁌱􀮙
􀹐􀛓􀻛􀺝􀒅􁊠􀔭􀮳􁭛􀺅􀭌􀲗􁤈􀹍􁴴􀷄􀴝􀥒􁉘􁌱􀬫􁊠􁑕􀬧􀌶
2􀌵􀖵􁊠 Spring Cloud 􀹍􀕋􀔍􀕽􀛠?
􀖵􁊠 Spring Boot 􀭏􀝎􀚓􀫲􀭗􀮙􀹐􀛓􀷸􀒅􀱯􀕪􁶎􀔁􀕦􀓥􁳯􁷌
• 􀓨􀚓􀫲􀭗􁔮􁕹􁍘􀙉􁌱􀥔􀹥􀯔-􁬯􁐿􀭏􁲀􀛱􀳡􁗑􁕶􁳯􁷌􀒅􀭊􁬴􀭏􁲀􀒅􀬃􀨼􁳯
􁷌􀒅􀨞􀙂􁳯􁷌􀌶
• 􀹐􀛓􀝎􁈿-􀹐􀛓􀝎􁈿􀫡􀙍􁓕􁉘􁗭􁵞􀓾􁌱􁁞􁑕􀞾􀹐􀛓􀦇􀖜􀺱􀲤􀞾􀔰􁍘􀔻􁧨􀌶
􀨙􁁿􀝊􀓞􀓻􀹐􀛓􁍓􀭯􀒅􀣁􁧆􁍓􀭯􀓾􁀳􀙙􀹐􀛓􀒅􁆐􀝸􁚆􀥜􀺱􀲤􀬚􁬳􀴳􀚩􁧆􁍓
􀭯􀓾􁌱􀹐􀛓􀌶
• 􀙞􀖟-􀚓􀫲􀭗􁔮􁕹􀓾􁌱􀙞􀖟􁳯􁷌􀌶
• 􁨮􁫹􀬘􁤍 --􁨮􁫹􀬘􁤍􀶯􀠺􁪜􀥚􀓻􁦇􁓒􁩒􁃠􁌱􀫡􀖢􁨮􁞚􀒅􁧘􀦇􁦇􁓒􀹢􀒅􁦇
􁓒􀹢􁵞􁗭􀒅􁗑􁕶􁱾􁪠􀒅􀓾􀥤 􀥒􁉘􀜔􀘲􀒅􀱲􁏺􁍏􁸝􀛖􀢏􁌱􀚓􀫲􀌶
• 􀯔􁚆-􁳯􁷌 􁊧􀔭􀝱􁐿􁬩􁟠􀭏􁲀􀩕􁛘􁌱􀯔􁚆􁳯􁷌􀌶
• 􁮱􁗟􀥔􀹥􀯔-Devops 􀲦􁚆􁌱􁥝􀿢􀌶
3􀌵􀹐􀛓􁀳􀙙􀞾􀝎􁈿􀸎􀕋􀔍􀰺􀯏?Spring Cloud 􀦇􀖜􀨫􁈿?
􀭮􀱯􀕪􀭏􀦤􀓞􀓻􁶱􁍓􀷸􀒅􀱯􀕪􁭗􀬉􀣁􀪂􀯔􀷈􀕯􀓾􁬰􁤈􀲅􀹍􁌱􁯈􁗝􀌶􁵋􁍳􁩼
􀹶􁩼􀥚􁌱􀹐􀛓􀭏􀝎􀞾􁮱􁗟􀒅􁂲􀛒􀞾􀗥􀶯􁬯􀔶􀪂􀯔􀝒􀮑􀹅􀛒􀥔􀹥􀌶􀹍􀔶􀹐􀛓
􀝢􁚆􀕿􀓥􁴳􀒅􁘒􀺤􀔶􀖖􁗝􀝢􁚆􀕿􀝎􁊞􀝒􀛸􀌶􀲋􀛖􀹅􀶯􀪂􀯔􀝢􁚆􀕿􀔾􁊞􁳯
􁷌􀌶 Eureka 􀹐􀛓􁀳􀙙􀞾􀝎􁈿􀝢􀕦􀣁􁬯􁐿􀰘􀙭􀓥􀵉􀗀􀬆􀛗􀌶􁊧􀔭􀲅􀹍􀹐􀛓
􁮷􀣁 Eureka 􀹐􀛓􀢏􀓤􁀳􀙙􀬚􁭗􁬦􁧣􁊠 Eureka 􀹐􀛓􀢏􀨠􀱮􀺱􀲤􀒅􀢩􀾌􀷫􁵱
􀥒􁉘􀹐􀛓􀣈􁅩􁌱􀕱􀖜􀹅􀶯􀞾􀥒􁉘􀌶
4􀌵􁨮􁫹􀬘􁤍􁌱􀰺􀔎􀕋􀔍?
􀣁􁦇􁓒􀓾􀒅􁨮􁫹􀬘􁤍􀝢􀕦􀶯􀠺􁪜􁦇􁓒􀹢􀒅􁦇􁓒􀹢􁵞􁗭􀒅􁗑􁕶􁱾􀴳􀒅􀓾􀥤􀥒
􁉘􀜔􀘲􀱲􁏺􁍏􁸝􀛖􀢏􁒵􀥚􁐿􁦇􁓒
􁩒􁃠􁌱􀫡􀖢􁨮􁫹􀚓􀫲􀌶􁨮􁫹􀬘􁤍􀷰􀣁􀕽􀛸􁩒􁃠􀖵􁊠􀒅􀹋􀥟􀛸􀞃􀝺􁰁􀒅􀹋􀩜
􀛸􀟥􀬫􀷸􁳵􀬚􁭿􀘹􀕱􀖜􀜔􀓞􁩒􁃠
􁌱􁬦􁫹􀌶􀖵􁊠􀥚􀓻􁕟􀕯􁬰􁤈􁨮􁫹􀬘􁤍􁘒􀓧􀸎􀜔􀓻􁕟􀕯􀝢􁚆􀕿􁭗􁬦􀙞􀖟􀹶􀵉
􁹛􀝢􁶌􀯔􀞾􀝢􁊠􀯔􀌶􁨮􁫹􀬘􁤍􁭗􀬉􁁿􀝊􀓫􁊠􁫫􀕯􀱲􁏝􀕯􀒅􀖺􀦇􀥚􀩶􀔻􀴘􀹢
􀱲􀤒􀝷􁔮􁕹􀹐􀛓􀢏􁬰􁑕􀌶
5􀌵􀕋􀔍􀸎 Hystrix?􀨙􀦇􀖜􀨫􁈿􀨻􁲙?
Hystrix 􀸎􀓞􀓻􀭊􁬴􀞾􀨻􁲙􀬪􀒅􀷰􀣁􁵍􁐶􁬱􁑕􁔮􁕹􀒅􀹐􀛓􀞾􁒫􀓣􀷜􀬪􁌱􁦢􁳯
􁅩􀒅􀭮􀚊􁈿􀶳􁵑􀸎􀓧􀝢􁭿􀘹􁌱􀶳􁵑􀷸􀒅􀘊􀾊􁕆􁘶􀶳􁵑􀬚􀣁􀥔􀹥􁌱􀚓􀫲􀭗􁔮
􁕹􀓾􀨫􁈿􀭨􀯔􀌶
􁭗􀬉􀩒􀔭􀖵􁊠􀮙􀹐􀛓􀺝􀺅􀭏􀝎􁌱􁔮􁕹􀒅􁁿􀝊􀚩􁦜􀥚􀮙􀹐􀛓􀌶􁬯􀔶􀮙􀹐􀛓􀮂
􀾌􀜐􀖢􀌶
􀯏􁘍􀕦􀓥􀮙􀹐􀛓
􀘃􁦡􀦇􀺎􀓤􀢶􀓾􁌱􀮙􀹐􀛓 9 􀥦􁨳􀔧􀒅􁮎􀔍􀖵􁊠􀖃􁕹􀷜􁀩􀱯􀕪􀩙􀖃􀶎􀓞􀓻􀭑
􀬉􀌶􀖕􁬯􀕖􁆐􀕿􀩕􁛘􀷆􀓻􁔮􁕹􀫄􁃛􀌶
􁵋􁍳􀮙􀹐􀛓􀷄􁰁􁌱􀥀􀛒􀒅􁬯􀓻􁳯􁷌􀝒􀮑􀹅􀛒􀥔􀹥􀌶􀮙􀹐􀛓􁌱􀷄􁰁􀝢􀕦􁹛􁬡
1000.􁬯􀸎 hystrix 􀚊􁈿􁌱􀣈􀷜􀒅 􀱯􀕪􀩙􀖵􁊠 Hystrix 􀣁􁬯􁐿􀰘􀙭􀓥􁌱
Fallback 􀷜􁀩􀛑􁚆􀌶􀱯􀕪􀹍􀓷􀓻􀹐􀛓 employee-consumer 􀖵􁊠􁊧
employee-consumer 􀙄􀭏􁌱􀹐􀛓􀌶
􁓌􀛸􀢶􀦇􀓥􀲅􁐏
􁈿􀣁􀘃􁦡􁊧􀔭􀺤􁐿􀜻􀢩􀒅employee-producer 􀙄􀭏􁌱􀹐􀛓􀕿􀲲􀚊􀭑􀬉􀌶􀱯
􀕪􀣁􁬯􁐿􀰘􀙭􀓥􀖵􁊠 Hystrix 􀨧􀔎􀔧􀓞􀓻􀢧􁭅􀷜􁀩􀌶􁬯􁐿􀝸􀥓􀷜􁀩􀬫􁧆􀙍
􀹍􀓨􀙄􀭏􀹐􀛓􁍘􀝶􁌱􁬬􀢧􁔄􀣳􀌶􀦇􀺎􀸹􁶂􀹐􀛓􀓾􀚊􁈿􀭑􀬉􀒅􀚞􀢧􁭅􀷜􁀩􀩙
􁬬􀢧􀓞􀔶􊧊􀌶
6􀌵􀕋􀔍􀸎 Hystrix 􀷙􁪠􀢏?􀱯􀕪􁵱􁥝􀨙􀞀?
􁊧􀔭􀺤􀔶􀜻􀢩􀒅employee-consumer 􀙄􀭏􀹐􀛓􀕿􀭚􀝎􀭑􀬉􀌶􀣁􁬯􁐿􀰘􀙭􀓥
􀖵􁊠 Hystrix 􀱯􀕪􀨧􀔎􀔧􀓞􀓻 􀢧􁭅􀷜􁀩􀌶􀦇􀺎􀣁􀙄􀭏􀹐􀛓􀓾􀝎􁊞􀭑􀬉􀒅􀚞
􀢧􁭅􀷜􁀩􁬬􀢧􀓞􀔶􁼕􁦊􊧊􀌶
􀦇􀺎 firstPage method() 􀓾􁌱􀭑􀬉􁖀􁖅􀝎􁊞􀒅􀚞 Hystrix 􁊪􁪠􀩙􀓾􀷙􀒅􀬚􀓬
􀞧􀫡􀖵􁊠􁘏􀩙􀓞􁩸􁪡􁬦 firtsPage 􀷜􁀩􀒅􀬚􁍗􀴳􁧣􁊠􀢧􁭅􀷜􁀩􀌶 􀷙􁪠􀢏􁌱
􁍓􁌱􀸎􁕳􁒫􀓞􁶭􀷜􁀩􀱲􁒫􀓞􁶭􀷜􁀩􀝢􁚆􁧣􁊠􁌱􀙌􀕜􀷜􁀩 􁊸􀚊􀷸􁳵􀒅􀬚􀩕􁛘
􀭑􀬉􀯩􀥔􀌶􀝢􁚆􀝎􁊞􁌱􀰘􀙭􀸎􀒅􀣁􁨮􁫹􁫾􀩜􁌱􀰘􀙭􀓥􀒅􀩕􁛘􀭑􀬉􁌱􁳯􁷌􀹍
􀹅􀦅􁌱􀯩􀥔􀹢􀕿􀌶
7􀌵􀕋􀔍􀸎 Netflix Feign?􀨙􁌱􀕽􁅩􀸎􀕋􀔍?
Feign 􀸎􀝑􀚩 Retrofit􀒅JAXRS-2.0 􀞾 WebSocket 􀞐􀝎􁌱 java 􀨮􀲁􁒒􁘶􁖫
􁑕􀬧􀌶Feign 􁌱􁒫􀓞􀓻􁍓􀺽􀸎􀩙􁕅􀹳􀚓􀾮􁌱􀥔􀹥􀯔􁕹􀓞􀚩 http apis􀒅􁘒􀓧
􁘍􁡤􀙌􁑞􀨧􀯔􀌶􀣁 employee-consumer 􁌱􀖺􀧼􀓾􀒅􀱯􀕪􀖵􁊠􀔧 employeeproducer
􀖵􁊠 REST 􀽜􀺃􀙄􀭏􁌱 REST 􀹐􀛓􀌶
􀖕􀸎􀱯􀕪􀮠􁶳􁖫􀙟􀥟􁰁􀕤􁎱􀲍􁚆􀲗􁤈􀕦􀓥􀾍􁹈
• 􀖵􁊠􀛑􁚆􀜄􁬰􁤈􁨮􁫹􀬘􁤍􀌶
• 􁞴􀝐􀹐􀛓􀨫􀖺􀒅􁆐􀝸􁞴􀝐􀤚􀹜 URL􀌶
• 􀚥􁊠 REST 􀽜􀺃􀹶􀖵􁊠􀹐􀛓􀌶􀚹􁶎􁌱􀕤􁎱􀦇􀓥
1. @Controller
2. public class ConsumerControllerClient {
3.
4. @Autowired
5. private LoadBalancerClient loadBalancer;
6.
7. public void getEmployee() throws RestClientException, IOExc
eption {
8.
9. ServiceInstance serviceInstance=loadBalancer.choose("employ
ee-producer"); 10.
11. System.out.println(serviceInstance.getUri());
12.
13. String baseUrl=serviceInstance.getUri().toString();
14.
15. baseUrl=baseUrl+"/employee";
16.
17. RestTemplate restTemplate = new RestTemplate();
18. ResponseEntity<String> response=null;
19. try{
20. response=restTemplate.exchange(baseUrl,
21. HttpMethod.GET, getHeaders(),String.class);
22. }catch (Exception ex)
23. {
24. System.out.println(ex);
25. }
26. System.out.println(response.getBody());
27. }
􀔏􀚹􁌱􀕤􁎱􀒅􀹍􀘟 NullPointer 􁬯􀻏􁌱􀖺􀥘􁌱􀹢􀕿􀒅􀬚􀓧􀸎􀹋􀕽􁌱􀌶􀱯􀕪􀩙
􁍡􀚩􀦇􀖜􀖵􁊠 Netflix Feign 􀖵􀞷􀝞􀝒􀮑􀹅􀛒􁫷􀺂􀞾􁂴􁁄􀌶􀦇􀺎 Netflix
Ribbon 􀗁􁩢􀙉􁔮􀔞􀣁􁔄􁪠􀮆􀓾􀒅􁮎􀔍 Feign 􁼕􁦊􀔞􀕿􁨮􁨱􁨮􁫹􀬘􁤍􀌶
8􀌵􀕋􀔍􀸎 Spring Cloud Bus?􀱯􀕪􁵱􁥝􀨙􀞀?
􁘍􁡤􀕦􀓥􀰘􀙭:􀱯􀕪􀹍􀥚􀓻􀬫􁊠􁑕􀬧􀖵􁊠 Spring Cloud Config 􁧛􀝐􀪂􀯔􀒅
􁘒 Spring Cloud Config 􀕗 GIT 􁧛􀝐􁬯􀔶􀪂􀯔􀌶
􀓥􁶎􁌱􀖺􀧼􀓾􀥚􀓻􀞧􀫡􁊞􀔾􁘏􀽜􀣘􀕗 Employee Config Module 􁞴􀝐
Eureka 􁀳􀙙􁌱􁨰􀔾􀌶
􀦇􀺎􀘃􁦡 GIT 􀓾􁌱 Eureka 􁀳􀙙􀪂􀯔􀹅􀶯􀔅􀳰􀝻􀝚􀓞􀝣 Eureka 􀹐􀛓􀢏􀒅􀕿
􀝎􁊞􀕋􀔍􀰘􀙭􀌶􀣁􁬯􁐿􀰘􀙭􀓥􀒅􀱯􀕪􀩙􀓧􀮑􀓧􁯿􀷛􀞐􀛖􀹐􀛓􀕦􁞴􀝐􀹅􀷛􁌱
􀪂􀯔􀌶
􁬮􀹍􀝚􀓞􁐿􀖵􁊠􀲗􁤈􀢏􁒒􁅩/􀚬􀷛􁌱􀷜􀭗􀌶􀖕􀸎􀱯􀕪􀩙􀓧􀮑􀓧􀔅􀾯􀓻􀽜􀣘􀜔
􁇿􁧣􁊠􁬯􀓻 url􀌶􀖺􀦇􀒅􀦇􀺎 Employee Producer1 􁮱􁗟􀣁􁒒􀝗 8080 􀓤􀒅
􀚞􁧣􁊠 http:// localhost:8080 / refresh􀌶􀝶􀻏􀩒􀔭 Employee Producer2
http:// localhost:8081 / refresh 􁒵􁒵􀌶􁬯􀝈􀮉􁼋􁅸􀌶􁬯􀩪􀸎 Spring Cloud
Bus 􀝎􀴀􀖢􁊠􁌱􀣈􀷜􀌶
Spring Cloud Bus 􀵉􀗀􀔧􁪜􀥚􀓻􀨫􀖺􀚬􀷛􁯈􁗝􁌱􀛑􁚆􀌶􀢩􀾌􀒅􀣁􀓤􁶎􁌱􁐏
􀖺􀓾􀒅􀦇􀺎􀱯􀕪􀚬􀷛 Employee Producer1􀒅􀚞􀕿􁛔􀛖􀚬􀷛􀲅􀹍􀙌􀕜􀮠􁵱􁌱
􀽜􀣘􀌶􀦇􀺎􀱯􀕪􀹍􀥚􀓻􀮙􀹐􀛓􀞐􀛖􀬚􁬩􁤈􀒅􁬯􁇙􀚦 􀹍􁊠􀌶􁬯􀸎􁭗􁬦􀩙􀲅􀹍
􀮙􀹐􀛓􁬳􀴳􀚩􀜔􀓻􁁾􀯳􀕤􁉘􀹶􀨫􁈿􁌱􀌶􀷫􁦞􀖜􀷸􀚬􀷛􀨫􀖺􀒅􀾌􀔪􀕯􁮷􀕿􁦈
􁴅􀚩􀗅􀞍 􀾌􀕤􁉘􁌱􀲅􀹍􀮙􀹐􀛓􀒅􀬚􀓬􀨙􀕪􀔞􀕿􀚬􀷛􀌶􀝢􀕦􁭗􁬦􀖵􁊠􁒒􁅩/
􀯛􁕚/􀚬􀷛􀹶􀨫􁈿􀩒􀕱􀖜􀜔􀓻􀨫􀖺􁌱􀚬􀷛􀌶
2􀌵SpringBoot􁶎􁦶􀷆􁉘
1􀌵􀕋􀔍􀸎 Spring Boot?
􀥚􀬙􀹶􀒅􁵋􁍳􀷛􀛑􁚆􁌱􀥀􀛒􀒅spring 􀝒􀮑􁩼􀹶􁩼􀥔􀹥􀌶􀝝􁵱􁦢􁳯
https://spring.io/projects 􁶭􁶎􀒅􀱯􀕪􀩪􀕿􁍡􀚩􀝢􀕦􀣁􀱯􀕪􁌱􀬫􁊠􁑕􀬧􀓾􀖵
􁊠􁌱􀲅􀹍 Spring 􁶱􁍓􁌱􀓧􀝶􀛑􁚆􀌶􀦇􀺎􀮠􁶳􀞐􀛖􀓞􀓻􀷛􁌱 Spring 􁶱􁍓􀒅
􀱯􀕪􀮠􁶳􁂲􀛒􀺅􀭌􁪠􀮆􀱲􁂲􀛒 Maven 􀗁􁩢􀙉􁔮􀒅􁯈􁗝􀬫􁊠􁑕􀬧􀹐􀛓􀢏􀒅
􁂲􀛒 spring 􁯈􁗝􀌶􀢩􀾌􀒅􀭏􀦤􀓞􀓻􀷛􁌱 spring 􁶱􁍓􁵱􁥝􀮉􀥚􀛘􀛎􀒅􀢩􀔅
􀱯􀕪􁈿 􀣁􀮠􁶳􀕗􀥧􀭏􀦤􀘉􀲅􀹍􀔪􀰘􀌶
Spring Boot 􀸎􁥴􀙬􁬯􀓻􁳯􁷌􁌱􀷜􁀩􀌶Spring Boot 􀫪􁕪􀭌􁒈􀣁􁈿􀹍 spring
􀻛􀺝􀔏􀓤􀌶􀖵􁊠spring 􀞐􀛖􀒅􀱯􀕪􁭿􀘹􀔧􀔏􀚹􀱯􀕪􀮠􁶳􀘉􁌱􀲅􀹍􀻏􀺃􀕤􁎱
􀞾􁯈􁗝􀌶􀢩􀾌􀒅Spring Boot􀝢􀕦􀬆􀛗􀱯􀕪􀕦􀹋􀩝􁌱􀫡􀖢􁰁􀒅􀹅􀛒􀘋􀥌􀣈􀖵
􁊠􁈿􀹍􁌱 Spring 􀛑􁚆􀌶
2􀌵Spring Boot 􀹍􀟺􀔶􀕽􁅩?
Spring Boot 􁌱􀕽􁅩􀹍:
􀙺􀩝􀭏􀝎􀒅􁁥􁦶􀷸􁳵􀞾􀛘􀛎􀌶
􀖵􁊠 JavaConfig 􀹍􀛗􀔭􁭿􀘹􀖵􁊠 XML􀌶
􁭿􀘹􀥟􁰁􁌱 Maven 􀩕􀙁􀞾􀝱􁐿􁇇􀹜􀙫􁑱􀌶
􀵉􀗀􀰺􁥠􀝎􀪀􀷜􁀩􀌶
􁭗􁬦􀵉􀗀􁼕􁦊􊧊􀮳􁭛􀭏􀦤􀭏􀝎􀌶
􁀌􀹍􀜔􁇿􁌱 Web 􀹐􀛓􀢏􁵱􁥝􀌶􁬯􀰺􀞱􁍳􀖦􀓧􀙚􁵱􁥝􀞐􀛖 Tomcat􀒅
Glassfish 􀱲􀙌􀕜􀕱􀖜􀓳􁥜􀌶
􁵱􁥝􀹅􀩝􁌱􁯈􁗝 􀢩􀔅􁀌􀹍 web.xml 􀷈􀕯􀌶􀝝􁵱􁂲􀛒􁊠@ Configuration 􁀳
􁯽􁌱􁔄􀒅􁆐􀝸􁂲􀛒􁊠@Bean 􁀳􁯽􁌱􀷜􁀩􀒅Spring 􀩙􁛔􀛖􀛒􁫹􀩒􁨝􀬚􀘟􀕦
􀚹􀓞􀻏􀩒􀙌􁬰􁤈􁓕􁉘􀌶􀰍􁊜􁛗􀝢􀕦􀩙 @Autowired 􁂲􀛒􀚩 bean 􀷜􁀩􀓾􀒅
􀕦􀖵 Spring 􁛔􀛖􁤰􀙁􁵱􁥝􁌱􀗁􁩢􀙉􁔮􀓾􀌶 􀤚􀔭􁈾􀤹􁌱􁯈􁗝􀖵􁊠􁬯􀔶􀪂
􀯔􀒅􀰍􀝢􀕦􀩙􀰍􀾋􀣁􀖵􁊠􁌱􁈾􀤹􀖃􁭓􀚩􀬫􁊠􁑕􀬧:- Dspring.profiles.active =
{enviornment}􀌶􀣁􀛒􁫹􀔆􀬫􁊠􁑕􀬧􀪂􀯔􀷈􀕯􀝸􀒅Spring 􀩙􀣁
(application{environment} .properties)􀓾􀛒􁫹􀝸􁖅􁌱􀬫􁊠􁑕􀬧􀪂􀯔􀷈􀕯􀌶
3􀌵􀕋􀔍􀸎 JavaConfig?
Spring JavaConfig􀸎Spring􁐒􀜄􁌱􀔾􀟝􀒅􀨙􀵉􀗀􀔧􁯈􁗝Spring IoC􀨻􀢏􁌱􁕍
Java􀷜􁀩􀌶􀢩􀾌􀨙􀹍􀛗􀔭􁭿􀘹􀖵􁊠 XML 􁯈􁗝􀌶􀖵􁊠 JavaConfig 􁌱􀕽􁅩􀣁
􀔭:
􁶎􀝻􀩒􁨝􁌱􁯈􁗝􀌶􁊧􀔭􁯈􁗝􁤩􀨧􀔎􀔅 JavaConfig 􀓾􁌱􁔄􀒅􀢩􀾌􁊠􀲁􀝢􀕦􊧌
􀚓􀚥􁊠 Java 􀓾􁌱􁶎􀝻􀩒􁨝􀛑􁚆􀌶􀓞􀓻􁯈􁗝􁔄􀝢􀕦􁖀􀲥􀝚􀓞􀓻􀒅􁯿􀙟􀨙􁌱
@Bean 􀷜􁀩􁒵􀌶
􀙺􀩝􀱲􁁾􁴻 XML 􁯈􁗝􀌶􀤚􀔭􀗁􁩢􁀳􀙁􀜻􀚞􁌱􀥘􀛸􁯈􁗝􁌱􀦅􀥒􀫪􁤩􁦤􀸁􀌶
􀖕􀸎􀒅􁦜􀥚􀭏􀝎􀕈􀞧􀓧􀫶􀹕􀣁 XML 􀞾 Java 􀔏􁳵􀹶􀢧􀚔􀴘􀌶JavaConfig 􀔅
􀭏􀝎􀕈􀞧􀵉􀗀􀔧􀓞􁐿􁕍 Java 􀷜􁀩􀹶􁯈 􁗝􀓨 XML 􁯈􁗝􀼷􀮷􁍘􀖒􁌱 Spring
􀨻􀢏􀌶􀕗􀲦􀹞􁥯􀬶􀹶􁦖􀒅􀝝􀖵􁊠 JavaConfig 􁯈􁗝􁔄􀹶􁯈􁗝 􀨻􀢏􀸎􀝢􁤈
􁌱􀒅􀖕􀨫􁴬􀓤􀮉􀥚􀕈􁦊􀔅􀩙 JavaConfig 􀓨 XML 􁂰􀝳􀜃􁯈􀸎􁉘􀰮􁌱􀌶 􁔄􀣳
􀨞􀙂􀞾􁯿􀺅􀝋􀦅􀌶JavaConfig 􀵉􀗀􀔧􀓞􁐿􁔄􀣳􀨞􀙂􁌱􀷜􁀩􀹶􁯈􁗝 Spring
􀨻􀢏􀌶􁊧􀔭 Java 5.0 􀩒􁀬􀣳􁌱􀶪􀳮􀒅􁈿􀣁􀝢􀕦􀳲􁔄􀣳􁘒􀓧􀸎􀳲􀝷􁑍􀼄􁔱
bean􀒅􀓧􁵱􁥝􀕱􀖜􀭩􀚫􁫨􀴘􀱲 􀤚􀔭􀨁􁒧􀔀􁌱􀺱􀲤􀌶
4􀌵􀦇􀖜􁯿􀷛􀛒􁫹 Spring Boot 􀓤􁌱􀹅􀶯􀒅􁘒􀷫􁵱􁯿􀷛􀞐􀛖􀹐􀛓􀢏?
􁬯􀝢􀕦􀖵􁊠 DEV 􀫡􀙍􀹶􀨫􁈿􀌶􁭗􁬦􁬯􁐿􀗁􁩢􀙉􁔮􀒅􀰍􀝢􀕦􁜓􁍜􀕱􀖜􀹅
􀶯􀒅􀫍􀙁􀭗 tomcat 􀩙􁯿􀷛􀞐􀛖􀌶Spring Boot 􀹍􀓞􀓻􀭏􀝎􀫡􀙍(DevTools)􀽜
􀣘􀒅􀨙􀹍􀛗􀔭􀵉􁹛􀭏􀝎􀕈􀞧􁌱􁊞 􀔾􀛎􀌶Java 􀭏􀝎􀕈􀞧􁶎􀔁􁌱􀓞􀓻􀔆􁥝􀳴
􀱴􀸎􀩙􀷈􀕯􀹅􀶯􁛔􀛖􁮱􁗟􀚩􀹐􀛓􀢏􀬚􁛔􀛖􁯿􀞐􀹐􀛓 􀢏􀌶􀭏􀝎􀕈􀞧􀝢􀕦􁯿􀷛
􀛒􁫹Spring Boot􀓤􁌱􀹅􀶯􀒅􁘒􀷫􁵱􁯿􀷛􀞐􀛖􀹐􀛓􀢏􀌶􁬯􀩙􁁾􁴻􀾯􀽺􀲋􀛖􁮱
􁗟􀹅􀶯􁌱􁵱􁥝􀌶Spring Boot 􀣁􀝎􀫲􀨙􁌱􁒫􀓞􀓻􁇇􀹜􀷸􁀌􀹍􁬯􀓻􀛑􁚆􀌶􁬯
􀸎􀭏􀝎􀕈􀞧􀹋􁵱􁥝􁌱􀛑􁚆􀌶DevTools 􀽜􀣘􀨠􀙂􁃿􁪃􀭏􀝎􀕈􀞧􁌱􁵱􀿢􀌶􁧆􀽜
􀣘􀩙􀣁􁊞􀔾􁈾􀤹􀓾􁤩􁐬􁊠􀌶􀨙􁬮􀵉􀗀 H2 􀷄􀴝􀬪􀴴􀚫􀝣􀕦􀹅􀦅􀣈􁁥􁦶􀬫􁊠
􁑕􀬧􀌶
org.springframework.boot spring-boot-devtools true
5􀌵Spring Boot 􀓾􁌱􁍊􁥤􀢏􀸎􀕋􀔍?
Spring boot actuator􀸎spring􀞐􀛖􀻛􀺝􀓾􁌱􁯿􁥝􀛑􁚆􀔏􀓞􀌶Spring boot􁍊
􁥤􀢏􀝢􀬆􀛗􀰍􁦢 􁳯􁊞􀔾􁈾􀤹􀓾􀾋􀣁􁬩􁤈􁌱􀬫􁊠􁑕􀬧􁌱􀭮􀚹􁇫􀮾􀌶􀹍􀙾􀓻􀳰
􀺽􀮠􁶳􀣁􁊞􀔾􁈾􀤹􀓾􁬰􁤈􀼄􀺱􀞾 􁍊􀴴􀌶􀜨􀖵􀓞􀔶􀥘􁮱􀬫􁊠􁑕􀬧􀝢􁚆􀾋􀣁􀖵
􁊠􁬯􀔶􀹐􀛓􀹶􀝻􁍘􀙉􀕈􀞧􁥶􀝎􁦄􀲸􁁾􀯳􀌶􁍊􁥤􀢏 􀽜􀣘􀙄􀭏􀔧􀓞􁕟􀝢􁍗􀴳􀖢
􀔅 HTTP URL 􁦢􁳯􁌱 REST 􁒒􁅩􀹶􀼄􀺱􁇫􀮾􀌶
6􀌵􀦇􀖜􀣁 Spring Boot 􀓾􁐬􁊠 Actuator 􁒒􁅩􀨞􀙂􀯔?
􁼕􁦊􀰘􀙭􀓥􀒅􀲅􀹍􀶷􀰽􁌱 HTTP 􁒒􁅩􁮷􀸎􀨞􀙂􁌱􀒅􀝝􀹍􀙍􀹍 ACTUATOR
􁥯􁜋􁌱􁊠􀲁􀲍􁚆􁦢􁳯􀨙􀕪􀌶􀨞􀙂􀯔􀸎􀖵􁊠􀺽􀙵􁌱
HttpServletRequest.isUserInRole 􀷜􁀩􀨫􀷞􁌱􀌶􀱯􀕪􀝢􀕦􀖵􁊠
management.security.enabled = false
􀹶􁐬􁊠􀨞􀙂􀯔􀌶􀝝􀹍􀣁􀲗􁤈􀹢􀺅􁒒􁅩􀣁􁴠􁅉􀤾􀝸􁦢􁳯􀷸􀒅􀲍􀭌􁦓􁐬􁊠􀨞􀙂
􀯔􀌶
7􀌵􀦇􀖜􀣁􁛔􀨧􀔎􁒒􀝗􀓤􁬩􁤈 Spring Boot 􀬫􁊠􁑕􀬧?
􀔅􀔧􀣁􁛔􀨧􀔎􁒒􀝗􀓤􁬩􁤈 Spring Boot 􀬫􁊠􁑕􀬧􀒅􀰍􀝢􀕦􀣁
application.properties 􀓾􀳰􀨧􁒒􀝗􀌶
server.port = 8090
8􀌵􀕋􀔍􀸎 YAML?
YAML 􀸎􀓞􁐿􀕈􁔄􀝢􁧛􁌱􀷄􀴝􀬧􀚜􀛸􁧍􁥺􀌶􀨙􁭗􀬉􁊠􀔭􁯈􁗝􀷈􀕯􀌶
􀓨􀪂􀯔􀷈􀕯􁍘􀾲􀒅􀦇􀺎􀱯􀕪􀰮􁥝􀣁􁯈􁗝􀷈􀕯􀓾􁂲􀛒􀥔􀹥􁌱􀪂􀯔􀒅YAML 􀷈
􀕯􀩪􀹅􀛒􁕮􀺅􀛸􀒅􁘒􀓬􀹅􀩝􁂰􁂝􀌶􀝢􀕦􁍡􀚊 YAML 􀙍􀹍􀚓􀩶􁯈􁗝􀷄􀴝􀌶
9􀌵􀦇􀖜􀨫􁈿 Spring Boot 􀬫􁊠􁑕􀬧􁌱􀨞􀙂􀯔?
􀔅􀔧􀨫􁈿Spring Boot􁌱􀨞􀙂􀯔􀒅􀱯􀕪􀖵􁊠 spring-boot-starter-security􀗁􁩢
􁶱􀒅􀬚􀓬􀮠􁶳􁂲􀛒􀨞􀙂􁯈􁗝􀌶􀨙􀝝􁵱􁥝􀮉􀩝􁌱􀕤􁎱􀌶􁯈􁗝􁔄􀩙􀮠􁶳􀲘􀪀
WebSecurityConfigurerAdapter 􀬚􁥟 􁍍􀙌􀷜􁀩􀌶
10􀌵􀦇􀖜􁵞􀱮 Spring Boot 􀞾 ActiveMQ?
􀩒􀔭􁵞􀱮 Spring Boot 􀞾 ActiveMQ􀒅􀱯􀕪􀖵􁊠
spring-boot-starter-activemq
􀗁􁩢􀙉􁔮􀌶 􀨙􀝝􁵱􁥝􀮉􀩝􁌱􁯈􁗝􀒅􀬚􀓬􀓧􁵱􁥝􀻏􀺃􀕤􁎱􀌶
11􀌵􀦇􀖜􀖵􁊠 Spring Boot 􀨫􁈿􀚓􁶭􀞾􀴭􀬧?
􀖵􁊠 Spring Boot 􀨫􁈿􀚓􁶭􁶋􀬉􁓌􀜔􀌶􀖵􁊠 Spring Data-JPA 􀝢􀕦􀨫􁈿􀩙
􀝢􀚓􁶭􁌱 org.springframework.data.domain.Pageable
􀖃􁭓􁕳􀨂􀘙􀬪􀷜􁀩􀌶
12􀌵􀕋􀔍􀸎 Swagger?􀖦􁊠 Spring Boot 􀨫􁈿􀔧􀨙􀞀?
Swagger 􀬠􁀬􁊠􀔭􀝢􁥤􀛸 API􀒅􀖵􁊠 Swagger UI 􀔅􀚹􁒒􀭏􀝎􀕈􀞧􀵉􀗀􀣁
􁕚􁀉􁓟􀌶Swagger 􀸎􁊠􀔭􁊞􀱮 RESTful Web 􀹐􀛓􁌱􀝢􁥤􀛸􁤒􁐏􁌱􀫡􀙍􀒅􁥢
􁝜􀞾􀨠􀷆􀻛􀺝􀨫􁈿􀌶􀨙􀖵􀷈􀻩􁚆􀥜􀕦􀓨􀹐􀛓􀢏􁍘􀝶􁌱􁭛􀬶􀹅􀷛􀌶􀭮􁭗􁬦
Swagger 􀾋􁏟􀨧􀔎􀷸􀒅􁁾􁩇􁘏􀝢􀕦􀖵􁊠􀹋􀩝􁰁􁌱􀨫􁈿􁭦 􁬋􀹶􁉘􁥴􁬱􁑕􀹐
􀛓􀬚􀓨􀙌􁬰􁤈􀔻􀔰􀌶􀢩􀾌􀒅Swagger 􁁾􁴻􀔧􁧣􁊠􀹐􀛓􀷸􁌱􁈖􁁥􀌶
13􀌵􀕋􀔍􀸎 Spring Profiles?
Spring Profiles 􊧋􁦜􁊠􀲁􀻑􀴝􁯈􁗝􀷈􀕯(dev􀒅test􀒅prod 􁒵)􀹶􁀳􀙙 bean􀌶
􀢩􀾌􀒅􀭮􀬫􁊠􁑕􀬧􀣁􀭏􀝎􀓾􁬩􁤈􀷸􀒅􀝝􀹍􀺤􀔶 bean 􀝢􀕦􀛒􁫹􀒅􁘒􀣁
PRODUCTION 􀓾􀒅􀺤􀔶􀙌􀕜 bean 􀝢􀕦􀛒􁫹􀌶􀘃􁦡􀱯􀕪􁌱􁥝􀿢􀸎
Swagger 􀷈􀻩􀕐􁭇􁊠􀔭 QA 􁈾􀤹􀒅􀬚􀓬􁐬􁊠􀲅􀹍􀙌􀕜􀷈􀻩􀌶􁬯􀝢􀕦􀖵􁊠􁯈
􁗝􀷈􀕯􀹶􀨠􀱮􀌶Spring Boot 􀖵􀮑􀖵􁊠􁯈􁗝􀷈􀕯􁶋􀬉􁓌􀜔􀌶
14􀌵􀕋􀔍􀸎 Spring Batch?
Spring Boot Batch􀵉􀗀􀝢􁯿􁊠􁌱􀚍􀷄􀒅􁬯􀔶􀚍􀷄􀣁􀥒􁉘􀥟􁰁􁦕􀭯􀷸􁶋􀬉􁯿
􁥝􀒅􀛱􀳡􀷭􀮪/􁪙 􁪵􀒅􀔪􀛓􁓕􁉘􀒅􀖢􀓱􀥒􁉘􁕹􁦇􀗞􀯳􀒅􀖢􀓱􁯿􀷛􀞐􀛖􀒅􁪡
􁬦􀞾􁩒􁃠􁓕􁉘􀌶􀨙􁬮􀵉􀗀􀔧􀹅􀘶􁬰􁌱􀲦􀹞􀹐􀛓􀞾􀛑􁚆􀒅􁭗􁬦􀕽􀛸􀞾􀚓􀜄􀲦
􀹞􀒅􀝢􀕦􀨫􁈿􀺄􁹛􀲢􁰁􀞾􁹛􀯔􁚆􀲢􀥒􁉘􀖢􀓱􀌶􁓌􀜔􀕦􀝊􀥔􀹥􁌱􀥟􀲢􁰁􀲢􀥒
􁉘􀖢􀓱􀝢􀕦􁹛􀬶􀝢􀲘􀪀􁌱􀷜􀭗􀚥􁊠􀻛􀺝􀥒􁉘􁯿􁥝􀥟􁰁􁌱􀗞􀯳􀌶
15􀌵􀕋􀔍􀸎 FreeMarker 􀽜􀺃?
FreeMarker 􀸎􀓞􀓻􀤚􀔭 Java 􁌱􀽜􀺃􀭚􀶚􀒅􀹋􀚡􀓫􁀳􀔭􀖵􁊠 MVC 􁫫􀕯􀺝􀺅
􁬰􁤈􀛖􀮾􁗑􁶭􁊞􀱮􀌶􀖵􁊠 Freemarker 􁌱􀔆􁥝􀕽􁅩􀸎􁤒􁐏􀩶􀞾􀓱􀛓􀩶􁌱􀨠
􀙂􀚓􁐶􀌶􁑕􀬧􀞧􀝢􀕦􀥒􁉘􀬫􁊠􁑕􀬧􀕤􁎱􀒅􁘒􁦡􁦇􀕈􀞧􀝢􀕦􀥒􁉘 html 􁶭􁶎
􁦡􁦇􀌶􀹋􀝸􀖵􁊠 freemarker 􀝢􀕦􀩙􁬯􀔶􁕮􀝳􁩸􀹶􀒅􁕳􀚊􀹋􁕣􁌱􁬌􀚊􁶭􁶎􀌶
16􀌵􀦇􀖜􀖵􁊠 Spring Boot 􀨫􁈿􀭑􀬉􀥒􁉘?
Spring􀵉􀗀􀔧􀓞􁐿􀖵􁊠ControllerAdvice􀥒􁉘􀭑􀬉􁌱􁶋􀬉􀹍􁊠􁌱􀷜􁀩􀌶 􀱯􀕪
􁭗􁬦􀨫􁈿􀓞􀓻 ControlerAdvice 􁔄􀒅􀹶􀥒􁉘􀴴􀚫􀢏􁔄􀲲􀚊􁌱􀲅􀹍􀭑􀬉􀌶
17􀌵􀰍􀖵􁊠􀔧􀟺􀔶 starter maven 􀗁􁩢􁶱?
􀖵􁊠􀔧􀓥􁶎􁌱􀓞􀔶􀗁􁩢􁶱
spring-boot-starter-activemq spring-boot-starter-security
spring-boot-starter-web 􁬯􀹍􀛗􀔭􀥀􀛒􀹅􀩝􁌱􀗁􁩢􀙉􁔮􀒅􀬚􀙺􀩝􁇇􀹜􁌱􀙫
􁑱􀌶
18􀌵􀕋􀔍􀸎 CSRF 􀶰􀚋?
CSRF 􀕤􁤒􁪜􁒊􁧗􀿢􀖉􁭜􀌶􁬯􀸎􀓞􁐿􀶰􀚋􀒅􁬼􀖵􀹋􁕣􁊠􀲁􀣁􀭮􀚹􁭗􁬦􁫝􀕲
􁸵􁦤􁌱 Web 􀬫􁊠 􁑕􀬧􀓤􀲗􁤈􀓧􁵱􁥝􁌱􀶙􀖢􀌶CSRF 􀶰􀚋􀓫􁳪􁰒􀩒􁇫􀮾􀶯
􀝒􁧗􀿢􀒅􁘒􀓧􀸎􀷄􀴝􁑲􀝐􀒅􀢩􀔅􀶰􀚋􁘏􀷫􁀩􀺱􁍡􀩒􀖉􁭜􁧗􀿢􁌱􀟥􀬫􀌶
19􀌵􀕋􀔍􀸎 WebSockets?
WebSocket 􀸎􀓞􁐿􁦇􁓒􀹢􁭗􀗞􀜐􁦓􀒅􁭗􁬦􀜔􀓻 TCP 􁬳􀴳􀵉􀗀􀙂􀝌􀫡􁭗􀗞
􀗞􁭲􀌶
WebSocket 􀸎􀝌􀝻􁌱 -􀖵􁊠 WebSocket 􀨮􀲁􁒒􀱲􀹐􀛓􀢏􀝢􀕦􀝎􁩸􁁾􀯳􀝎
􁭆􀌶
WebSocket 􀸎􀙂􀝌􀫡􁌱 -􀨮􀲁􁒒􀞾􀹐􀛓􀢏􁭗􀗞􀸎􁍘􀔰􁇿􁒈􁌱􀌶
􀜔􀓻TCP􁬳􀴳 -􀚡􀦤􁬳􀴳􀖵􁊠HTTP􀒅􁆐􀝸􀩙􀾌􁬳􀴳􀜋􁕆􀚩􀤚􀔭􀥺􀴳􀨁􁌱􁬳
􀴳􀌶􁆐􀝸􁬯􀓻􀜔􀓞􁬳􀴳􁊠􀔭􀲅􀹍􀹚􀹶􁌱􁭗􀗞
Light -􀓨 http 􁍘􀾲􀒅WebSocket 􁁾􀯳􀷄􀴝􀔻􀴘􁥝􁫷􀮑􀥚􀌶
20􀌵􀕋􀔍􀸎 AOP?
􀣁􁫫􀕯􀭏􀝎􁬦􁑕􀓾􀒅􁪜􁩼􀬫􁊠􁑕􀬧􀥚􀓻􁅩􁌱􀛑􁚆􁑍􀔅􀔻􀝉􁳯􁷌􀌶􁬯􀔶􀔻􀝉
􁳯􁷌􀓨􀬫􁊠􁑕􀬧􁌱􀔆􁥝􀓱􀛓􁭦􁬋􀓧􀝶􀌶􀢩􀾌􀒅􀩙􁬯􀔶􀽞􀚔􀙉􁀳􀓨􀓱􀛓􁭦􁬋
􀚓􀭏􀸎􁶎􀝻􀷜􁶎􁖫􁑕(AOP)􁌱 􀣈􀷜􀌶
21􀌵􀕋􀔍􀸎 Apache Kafka?
Apache Kafka 􀸎􀓞􀓻􀚓􀫲􀭗􀝎􀫲 - 􁦈􁴅􁁾􀯳􁔮􁕹􀌶􀨙􀸎􀓞􀓻􀝢􀲘􀪀􁌱􀒅􀨻
􁲙􁌱􀝎􀫲 - 􁦈􁴅 􁁾􀯳􁔮􁕹􀒅􀨙􀖵􀱯􀕪􁚆􀥜􀺅􀭌􀚓􀫲􀭗􀬫􁊠􁑕􀬧􀌶􁬯􀸎􀓞􀓻
Apache 􁶮􁕆􁶱􁍓􀌶Kafka 􁭇􀝳􁐶 􁕚􀞾􀣁􁕚􁁾􀯳􁁾􁩇􀌶
22􀌵􀱯􀕪􀦇􀖜􁍊􁥤􀲅􀹍 Spring Boot 􀮙􀹐􀛓?
Spring Boot 􀵉􀗀􁍊􁥤􀢏􁒒􁅩􀕦􁍊􀴴􀝱􀓻􀮙􀹐􀛓􁌱􀬶􁰁􀌶􁬯􀔶􁒒􁅩􀩒􀔭􁞴
􀝐􀹍􀙉􀬫􁊠􁑕􀬧􁌱􀗞􀯳(􀦇􀨙􀕪􀸎􀞈􀫪􀞐􀛖)􀕦􀝊􀨙􀕪􁌱􁕟􀕯(􀦇􀷄􀴝􀬪􁒵)􀸎
􀞈􀾋􀬉􁬩􁤈􀮉􀹍􀬆􀛗􀌶􀖕􀸎􀒅􀖵􁊠􁍊􁥤􀢏􁌱􀓞􀓻􀔆􁥝􁗌􁅩􀱲􀢯􁵙􀸎􀒅􀱯􀕪
􀮠􁶳􀜔􁇿􀲑􀭏􀬫􁊠􁑕􀬧􁌱􁎣􁦩􁅩􀕦􀔧􁥴􀙌􁇫􀮾􀱲􀘋􀬼􁇫􀙭􀌶􀰮􁨝􀓞􀓥􁁿􀝊
50 􀓻􀬫􁊠􁑕􀬧􁌱􀮙􀹐􀛓􀒅􁓕􁉘􀞧􀩙􀓧􀮑􀓧􀚋􀓾􀲅􀹍 50 􀓻􀬫􁊠􁑕􀬧􁌱􀲗􁤈
􁕣􁒒􀌶
3􀌵Dubbo􁶎􁦶􀷆􁉘
1􀌵Dubbo 􀓾 zookeeper 􀘉􁀳􀙙􀓾􀮞􀒅􀦇􀺎􁀳􀙙􀓾􀮞􁵞􁗭􁮷􀳯􀴧􀒅􀝎􀫲
􁘏􀞾􁦈􁴅􁘏􀔏􁳵􁬮􁚆􁭗􀗞􀔍?
􀝢􀕦􁭗􀗞􁌱􀒅􀞐􀛖 dubbo 􀷸􀒅􁁾􁩇􁘏􀕿􀕗 zk 􀳉􀝐􁀳􀙙􁌱􁊞􀔾􁘏􁌱􀣈􀣎􀴳
􀝗􁒵􀷄􀴝􀒅􁖨􀨂􀣁􀹜􀣈􀌶􀾯􀽺􁧣􁊠􀷸􀒅􀳲􁆙􀹜􀣈􀨂􀘙􁌱􀣈􀣎􁬰􁤈􁧣􁊠; 􁀳
􀙙􀓾􀮞􀩒􁒵􁵞􁗭􀒅􀕱􀰺􀓞􀝣􀨣􀹢􀝸􀒅􀩙􀕿􀚔􀴘􀚩􀝚􀓞􀝣;􁀳􀙙􀓾􀮞􀙂􁮱􀨣􀹢
􀝸􀒅􀹐􀛓􁌱􀵉􀗀􁘏􀞾􁁾􁩇􁘏􀕖􁚆􁭗􁬦􀹜􀣈􁖨􀨂􁭗􁦔􀌶􀹐􀛓􀵉􀗀􁘏􀷫􁇫􀮾􀒅
􀕱􀓞􀝣􀨣􀹢􀝸􀒅􀓧􀭽􀟥􀖵􁊠;􀹐􀛓􀵉􀗀􁘏􀙂􁮱􀨣􀹢􀒅􀹐􀛓􁁾􁩇􁘏􀕿􀷫􁀩􀖵
􁊠􀒅􀬚􀷫􁴴􀽺􁯿􁬳􁒵􀮇􀹐􀛓􁘏􀯩􀥔; 􀳯􀴧􀸎􀓧􁥝􁔲􁌱􀒅􀖕􀚹􀵉􀸎􀖦􁀌􀹍􀥀
􀛒􀷛􁌱􀹐􀛓􀒅􀦇􀺎􀖦􁥝􁧣􁊠􀷛􁌱􀹐􀛓􀒅􀚞􀸎􀓧􁚆􀛐􀚩􁌱􀌶
2􀌵dubbo 􀹐􀛓􁨮􁫹􀣐􁤍􁒽􁊼?
l Random LoadBalance
􁵋􀹢􀒅􀳲􀹦􁯿􁦡􁗝􁵋􀹢􀼷􁈲􀌶􀣁􀓞􀓻􀱼􁶎􀓤􁏳􀶊􁌱􀼷􁈲􁹛􀒅􀖕􁧣􁊠􁰁􁩼􀥟􀚓􀫲􁩼􀣐􀛰􀒅􁘒􀓬􀳲􀼷􁈲􀖵􁊠􀹦􁯿􀝸􀔞􀾲 􁫾􀣐􀛰􀒅􀹍􀚥􀔭􀛖􀮾􁧣􀷆􀵉􀗀􁘏
􀹦􁯿􀌶(􀹦􁯿􀝢􀕦􀣁 dubbo 􁓕􀴴􀝣􁯈􁗝)
l RoundRobin LoadBalance
􁫪􀮗􀒅􀳲􀙄􁕅􀝸􁌱􀹦􁯿􁦡􁗝􁫪􀮗􀾲􁈲􀌶􀨂􀣁􀱌􁌱􀵉􀗀􁘏􁔴􁑌􁧗􀿢􁳯􁷌􀒅􀾲
􀦇:􁒫􀔫􀝣􀹢􀢏􀮉􀱌􀒅􀖕􁀌􀳯􀒅􀭮􁧗􀿢􁧣
􀚩􁒫􀔫􀝣􀷸􀩪􀜜􀣁􁮎􀒅􀔋􁘒􀔋􀔏􀒅􀲅􀹍􁧗􀿢􁮷􀜜􀣁􁧣􀚩􁒫􀔫􀝣􀓤􀌶
l LeastActive LoadBalance
􀹋􀩝􁁚􁪋􁧣􁊠􀷄􀒅􁍘􀝶􁁚􁪋􀷄􁌱􁵋􀹢􀒅􁁚􁪋􀷄􀳰􁧣􁊠􀚹􀝸􁦇􀷄􀫧􀌶􀖵􀱌􁌱
􀵉􀗀􁘏􀶭􀚩􀹅􀩝􁧗􀿢􀒅􀢩􀔅􁩼􀱌􁌱􀵉􀗀􁘏􁌱
􁧣􁊠􀚹􀝸􁦇􀷄􀫧􀕿􁩼􀥟􀌶
l ConsistentHash LoadBalance
􀓞􁛘􀯔 Hash􀒅􁍘􀝶􀝇􀷄􁌱􁧗􀿢􀯛􀸎􀝎􀚩􀝶􀓞􀵉􀗀􁘏􀌶􀭮􀺤􀓞􀝣􀵉􀗀􁘏􀳯
􀷸􀒅􀜻􀹜􀝎􀮃􁧆􀵉􀗀􁘏􁌱􁧗􀿢􀒅􀤚􀔭􁡦􀳙􁜓􁅩􀒅􀬘􀵶􀚩􀙌􀨙􀵉􀗀􁘏􀒅􀓧􀕿
􀭚􁩸􀛂􁅱􀝒􀛖􀌶􁗌􁍜􀝝􀩒􁒫􀓞􀓻􀝇􀷄 Hash􀒅􀦇􀺎􁥝􀗥􀶯􀒅􁧗􁯈􁗝
<dubbo:parameter key="hash.arguments" value="0,1" />
􁗌􁍜􁊠 160 􀕲􁡦􀳙􁜓􁅩􀒅􀦇􀺎􁥝􀗥􀶯􀒅􁧗􁯈􁗝
<dubbo:parameter key="hash.nodes" value="320" />
3􀌵 Dubbo 􀣁􀨞􀙂􀹢􀚫􀷜􁶎􀸎􀦇􀖜􁥴􀙬􁌱
Dubbo 􁭗􁬦 Token 􀕥􁇈􁴠􀾊􁊠􀲁􁕰􁬦􁀳􀙙􀓾􀮞􁍗􁬳􀒅􁆐􀝸􀣁􁀳􀙙􀓾􀮞􀓤􁓕
􁉘􀴦􀹦􀌶Dubbo 􁬮􀵉􀗀􀹐􀛓􁼓􁌮􀝷􀜔􀒅􀹶􀴴􀚫􀹐􀛓􀲅􊧋􁦜􁌱􁧣􁊠􀷜􀌶
4􀌵dubbo 􁬳􀴳􁀳􀙙􀓾􀮞􀞾􁍗􁬳􁌱􀜄􀚦
􀣁􀭏􀝎􀝊􁁥􁦶􁈾􀤹􀓥􀒅􁕪􀬉􁵱􁥝􁕰􁬦􁀳􀙙􀓾􀮞􀒅􀝝􁁥􁦶􀳰􀨧􀹐􀛓􀵉􀗀􁘏􀒅
􁬯􀷸􀗲􀝢􁚆􁵱􁥝􁅩􀩒􁅩􁍗􁬳􀒅􁅩􀩒􁅩􁍗􁘶􀷜􀭗􀒅􀩙􀕦􀹐􀛓􀴳􀝗􀔅􀜔􀖖􀒅􀮺
􁊼􁀳􀙙􀓾􀮞􁌱􀵉􀗀􁘏􀚜􁤒􀒅
l Failsafe Cluster
􀥦􁨳􀨞􀙂􀒅􀚊􁈿􀭑􀬉􀷸􀒅􁍗􀴳􀮺􁊼􀌶􁭗􀬉􁊠􀔭􀙟􀙁􀨭􁦇􀷭􀮪􁒵􀶙􀖢􀌶
[AppleScript] 􁕍􀷈􀹜􀺱􁍡􀥔􀚫􀕤􁎱 ?
􀹐􀛓􁀳􀙙􀓾􀮞􀒅􀛖􀮾􁌱􁀳􀙙􀞾􀝎􁈿􀹐􀛓􀒅􀖵􀹐􀛓􁌱􀖖􁗝􁭐􀸁􀒅􀬚􁭗􁬦􀣁􁁾
􁩇􀷜􁞴􀝐􀹐􀛓􀵉􀗀􀷜􀣈􀣎􀚜􁤒􀒅􀨫􁈿􁫫􁨮􁫹􀣐􁤍􀞾 Failover􀒅 􁀳􀙙􀓾􀮞􁬬
􀢧􀹐􀛓􀵉􀗀􁘏􀣈􀣎􀚜􁤒􁕳􁁾􁩇􁘏􀒅􀦇􀺎􀹍􀝒􀹅􀒅􁀳􀙙􀓾􀮞􀩙􀤚􀔭􁳩􁬳􀴳􀴵
􁭆􀝒􀹅􀷄􀴝􁕳 􁁾􁩇􁘏􀌶􀹐􀛓􁁾􁩇􁘏􀒅􀕗􀵉􀗀􁘏􀣈􀣎􀚜􁤒􀓾􀒅􀤚􀔭􁫫􁨮􁫹􀣐
􁤍􁓒􁀩􀒅􁭌􀓞􀝣􀵉􀗀􁘏􁬰􁤈􁧣􁊠􀒅􀦇􀺎􁧣􁊠􀥦􁨳􀒅􀙚􁭌􀝚􀓞􀝣􁧣􁊠􀌶􁀳􀙙
􀓾􀮞􁨮􁨱􀹐􀛓􀣈􀣎􁌱􁀳􀙙􀓨􀺱􀲤􀒅􁍘􀭮􀔭􁍓􀭯􀹐􀛓􀒅􀹐􀛓􀵉􀗀􁘏􀞾􁁾􁩇􁘏
􀝝􀣁􀞐􀛖􀷸􀓨􁀳􀙙􀓾􀮞􀔻􀔰􀒅􁀳􀙙􀓾􀮞􀓧􁫨􀝎􁧗􀿢􀒅􀹐􀛓􁁾􁩇􁘏􀝻􁀳􀙙􀓾
􀮞􁞴􀝐􀹐􀛓􀵉􀗀􁘏􀣈􀣎􀚜􁤒􀒅􀬚􀻑􀴝􁨮􁫹􁓒􁀩􁍗􀴳􁧣􁊠􀵉􀗀􁘏􀒅􁀳􀙙􀓾
􀮞􀒅􀹐􀛓􀵉􀗀􁘏􀒅􀹐􀛓􁁾􁩇􁘏􀓣􁘏􀔏􁳵􀣐􀔅􁳩􁬳􀴳􀒅􁍊􀴴􀓾􀮞􁴻􀥘􀒅􁀳􀙙
􀓾􀮞􁭗􁬦􁳩􁬳􀴳􀰽􁎣􀹐􀛓􀵉􀗀􁘏􁌱􀨂􀣁􀒅􀹐􀛓􀵉􀗀􁘏􀨣􀹢􀒅􁀳􀙙􀓾􀮞􀩙􁒈
􀜨􀴵􁭆􀔪􀕯􁭗􁎣􁁾􁩇􁘏 􁀳􀙙􀓾􀮞􀞾􁍊􀴴􀓾􀮞􀙂􁮱􀨣􀹢􀒅􀓧􀭽􀟥􀫪􁬩􁤈􁌱􀵉
􀗀􁘏􀞾􁁾􁩇􁘏􀒅􁁾􁩇􁘏􀣁􀹜􀣈􁖨􀨂􀔧􀵉􀗀􁘏􀚜􁤒 􁀳􀙙􀓾􀮞􀞾􁍊􀴴􀓾􀮞􁮷􀸎
􀝢􁭌􁌱􀒅􀹐􀛓􁁾􁩇􁘏􀝢􀕦􁍗􁬳􀹐􀛓􀵉􀗀􁘏􀌶
1. dubbo 􀹐􀛓􁵞􁗭􁯈􁗝(􁵞􁗭􀨻􁲙􀽜􀭗)
􀣁􁵞􁗭􁧣􁊠􀥦􁨳􀷸􀒅Dubbo 􀵉􀗀􀔧􀥚􁐿􀨻􁲙􀷜􀻜􀒅􁗌􁍜􀔅 failover 􁯿􁦶􀌶
􀝢􀕦􁛔􁤈􀲘􀪀􁵞􁗭􀨻􁲙􁒽􁊼 l Failover Cluster(􁼕􁦊)
􀥦􁨳􁛔􀛖􀚔􀴘􀒅􀭮􀚊􁈿􀥦􁨳􀒅􁯿􁦶􀙌􀨙􀹐􀛓􀢏􀌶(􁗌􁍜)􁭗􀬉􁊠􀔭􁧛􀶙􀖢􀒅
􀖕􁯿􁦶􀕿􀬃􀹶􀹅􁳩􀭊􁬴􀌶􀝢􁭗􁬦 retries="2"􀹶􁦡􁗝􁯿􁦶􀽺􀷄(􀓧􀞌􁒫􀓞􀽺)􀌶
<dubbo:service retries="2" cluster="failover"/>
􀱲:
<dubbo:reference retries="2" cluster="failover"/> cluster="fai
lover"􀝢􀕦􀓧􁊠􀙟,􀢩􀔅􁼕􁦊􀩪􀸎 failover
l Failfast Cluster
􀮳􁭛􀥦􁨳􀒅􀝝􀝎􁩸􀓞􀽺􁧣􁊠􀒅􀥦􁨳􁒈􀜨􀲸􁲙􀌶􁭗􀬉􁊠􀔭􁶋􀬍􁒵􀯔􁌱􀙟􀶙
􀖢􀒅
􀾲􀦇􀷛􀥀􁦕􀭯􀌶
dubbo:service cluster="failfast" />
􀱲:
<dubbo:reference cluster="failfast" />
cluster="failfast"􀞾 􀲩 cluster="failover"􀌵retries="0"􀸎􀓞􀻏􁌱􀶴
􀺎,retries="0"􀩪􀸎􀓧􁯿􁦶
l Failsafe Cluster
􀥦􁨳􀨞􀙂􀒅􀚊􁈿􀭑􀬉􀷸􀒅􁍗􀴳􀮺􁊼􀌶􁭗􀬉􁊠􀔭􀙟􀙁􀨭􁦇􀷭􀮪􁒵􀶙􀖢􀌶
<dubbo:service cluster="failsafe" />
􀱲:
<dubbo:reference cluster="failsafe" />
l Failback Cluster
􀥦􁨳􁛔􀛖􀯩􀥔􀒅􀝸􀝣􁦕􀭯􀥦􁨳􁧗􀿢􀒅􀨧􀷸􁯿􀝎􀌶􁭗􀬉􁊠􀔭􁁾􀯳􁭗􁎣􀶙􀖢􀌶
<dubbo:service cluster="failback" />
􀱲:
<dubbo:reference cluster="failback" />
l Forking Cluster
􀬚􁤈􁧣􁊠􀥚􀓻􀹐􀛓􀢏􀒅􀝝􁥝􀓞􀓻􀱮􀛑􀜨􁬬􀢧􀌶􁭗􀬉􁊠􀔭􀨫􀷸􀯔􁥝􀿢􁫾􁹛􁌱
􁧛􀶙􀖢􀒅􀖕􁵱􁥝􁁵􁩇􀹅􀥚􀹐􀛓􁩒􁃠􀌶􀝢􁭗􁬦 forks="2"􀹶􁦡􁗝􀹋􀥟􀬚􁤈􀷄􀌶
<dubbo:service cluster=“forking" forks="2"/>
􀱲:
<dubbo:reference cluster=“forking" forks="2"/>
l 􁯈􁗝
􀹐􀛓􁒒􀹐􀛓􁕆􀚦
<dubbo:service interface="..." loadbalance="roundrobin" />
􀨮􀲁􁒒􀹐􀛓􁕆􀚦
<dubbo:reference interface="..." loadbalance="roundrobin"
/> 􀹐􀛓􁒒􀷜􁀩􁕆􀚦 <dubbo:service interface="..."> <dubbo:meth
od name="..." loadbalance 􀨮􀲁􁒒􀷜􁀩􁕆􀚦 <dubbo:reference interf
ace="..."> <dubbo:method name="..." loadbalance="
1. dubbo 􁭗􀗞􀜐􁦓 dubbo 􀜐􁦓􀔅􀕋􀔍􁥝􁁾􁩇􁘏􀾲􀵉􀗀􁘏􀓻􀷄􀥚: 􀢩 dubbo
􀜐􁦓􁯻􁊠􀜔􀓞􁳩􁬳􀴳􀒅􀘃􁦡􁗑􁕶􀔅􀜉􀘵􁗑􀜜(1024Mbit=128MByte)􀒅􀻑
􀴝􁁥􁦶􁕪􁸵􀷄􀴝􀾯􀹵􁬳􀴳􀹋􀥚􀝝􁚆􀜴􁃿 7MByte(􀓧􀝶􁌱􁈾􀤹􀝢􁚆􀓧􀓞
􀻏􀒅􀗀􀝇􁘍)􀒅􁉘􁦞􀓤 1 􀓻􀹐􀛓􀵉􀗀􁘏􁵱􁥝 20 􀓻􀹐􀛓􁁾􁩇􁘏􀲍􁚆􀜴􁃿􁗑
􀜜􀌶
2. dubbo 􁭗􀗞􀜐􁦓 dubbo 􀜐􁦓􀔅􀕋􀔍􀓧􁚆􀖃􀥟􀛱: 􀢩 dubbo 􀜐􁦓􁯻􁊠􀜔
􀓞􁳩􁬳􀴳􀒅 􀦇􀺎􀾯􀽺􁧗􀿢􁌱􀷄􀴝􀛱􀥟􀩜􀔅 500KByte􀒅􀘃􁦡􁗑􁕶􀔅􀜉􀘵
􁗑􀜜(1024Mbit=128MByte)􀒅􀾯􀹵􁬳􀴳􀹋􀥟 7MByte(􀓧􀝶􁌱􁈾􀤹􀝢􁚆􀓧
􀓞􀻏􀒅􀗀􀝇􁘍)􀒅 􀜔􀓻􀹐􀛓􀵉􀗀􁘏􁌱 TPS(􀾯􁑁􀥒􁉘􀔪􀛓􀷄)􀹋􀥟􀔅:128MByte / 500KByte = 262􀌶 􀜔􀓻􁁾􁩇􁘏􁧣􁊠􀜔􀓻􀹐􀛓􀵉􀗀􁘏􁌱
TPS(􀾯􁑁􀥒􁉘􀔪􀛓􀷄)􀹋􀥟􀔅:7MByte / 500KByte = 14􀌶 􀦇􀺎􁚆􀴳􀝑􀒅
􀝢􀕦􁘍􁡤􀖵􁊠􀒅􀞈􀚞􁗑􁕶􀩙􀱮􀔅􁊒􁷀􀌶
3. dubbo 􁭗􀗞􀜐􁦓 dubbo 􀜐􁦓􀔅􀕋􀔍􁯻􁊠􀭑􀾍􀜔􀓞􁳩􁬳􀴳: 􀢩􀔅􀹐􀛓􁌱􁈿
􁇫􀥟􁮷􀸎􀹐􀛓􀵉􀗀􁘏􀩝􀒅􁭗􀬉􀝝􀹍􀙾􀝣􀹢􀢏􀒅􁘒􀹐􀛓􁌱􁁾􁩇􁘏􀥚􀒅􀝢􁚆
􀷆􀓻􁗑􁒊􁮷􀣁􁦢􁳯􁧆􀹐􀛓􀒅 􀾲􀦇 Morgan 􁌱􀵉􀗀􁘏􀝝􀹍 6 􀝣􀵉􀗀􁘏􀒅􀜩
􀹍􀓤􁌯􀝣􁁾􁩇􁘏􀒅􀾯􀥠􀹍 1.5 􀕊􀽺􁧣􁊠􀒅􀦇􀺎􁯻􁊠􀬉􁥢􁌱 hessian 􀹐
􀛓􀒅􀹐􀛓􀵉􀗀􁘏􀮉􀨻􀸃􀩪􁤩􀜴􁪜􀒅􁭗􁬦􀜔􀓞􁬳􀴳􀒅􀗛􁦤􀜔􀓞􁁾􁩇􁘏􀓧􀕿
􀜴􀾒􀵉􀗀􁘏􀒅 􁳩􁬳􀴳􀒅􀙺􀩝􁬳􀴳􀵎􀲋􁸵􁦤􁒵􀒅 􀬚􀖵􁊠􀭑􀾍 IO􀒅􀥔􁊠􁕚
􁑕􀿰􀒅􁴠􀾊 C10K 􁳯􁷌􀌶
4. dubbo 􁭗􀗞􀜐􁦓 dubbo 􀜐􁦓􁭇􁊠􁝜􀢱􀞾􁭇􁊠􀣋􀸧􁭇􁊠􁝜􀢱:􀖃􀙁􀖃􀚊􀝇
􀷄􀷄􀴝􀛱􁫾􀩜(􀭌􁦓􀩜􀔭 100K)􀒅􁁾􁩇􁘏􀾲􀵉􀗀􁘏􀓻􀷄􀥚􀒅􀜔􀓞􁁾􁩇􁘏􀷫
􁀩􀜴􁃿􀵉􀗀􁘏􀒅􀩱􁰁􀓧􁥝􁊠 dubbo 􀜐􁦓􀖃􁬌􀥟􀷈􀕯􀱲􁩻􀥟􀨁􁒧􀔀􀌶 􁭇
􁊠􀣋􀸧:􀬉􁥢􁬱􁑕􀹐􀛓􀷜􁀩􁧣􁊠 dubbo 􀜐􁦓􁤑􊧌: 􁬳􀴳􀓻􀷄:􀜔􁬳􀴳􁬳􀴳
􀷜􀭗:􁳩􁬳􀴳􀖃􁬌􀜐􁦓:TCP 􀖃􁬌􀷜􀭗:NIO 􀭑􀾍􀖃􁬌􀬧􀚜􀛸:Hessian 􀔫􁬰
􀚫􀬧􀚜􀛸
5. RMI 􀜐􁦓 RMI 􀜐􁦓􁯻􁊠 JDK 􀺽􀙵􁌱 java.rmi.*􀨫􁈿􀒅􁯻􁊠􁴥􀤲􀭗􁎨􁬳􀴳
􀞾 JDK 􀺽􀙵􀬧􀚜 􀛸􀷜􀭗􀒅Java 􀺽􀙵􁌱􁬱􁑕􁧣􁊠􀜐􁦓􀌶 􁬳􀴳􀓻􀷄:􀥚􁬳
􀴳􁬳􀴳􀷜􀭗:􁎨􁬳􀴳 􀖃􁬌􀜐􁦓:TCP 􀖃􁬌􀷜􀭗:􀝶􀾍􀖃􁬌 􀬧􀚜􀛸:Java 􀺽􀙵
􀔫􁬰􀚫􀬧􀚜􀛸 􁭇􁊠􁝜􀢱:􀖃􀙁􀖃􀚊􀝇􀷄􀷄􀴝􀛱􀥟􀩜􁂰􀝳􀒅􁁾􁩇􁘏􀓨􀵉􀗀
􁘏􀓻􀷄􀫧􀓧􀥚􀒅􀝢􀖃􀷈􀕯􀌶 􁭇􁊠􀣋􀸧:􀬉􁥢􁬱􁑕􀹐􀛓􀷜􁀩􁧣􁊠􀒅􀓨􀜻􁊞
RMI 􀹐􀛓􀔰􀶙􀖢
6. Hessian 􀜐􁦓 Hessian 􀜐􁦓􁊠􀔭􁵞􀱮 Hessian 􁌱􀹐􀛓􀒅Hessian 􀬬􀩶􁯻
􁊠 Http 􁭗􁦔􀒅􁯻􁊠 Servlet 􀸹􁶂􀹐􀛓􀒅Dubbo 􁗌􁍜􀙖􀫍 Jetty 􀖢􀔅􀹐􀛓
􀢏􀨫􁈿 􀤚􀔭 Hessian 􁌱􁬱􁑕􁧣􁊠􀜐􁦓􀌶 􁬳􀴳􀓻􀷄:􀥚􁬳􀴳 􁬳􀴳􀷜􀭗:􁎨
􁬳􀴳 􀖃􁬌􀜐􁦓:HTTP 􀖃􁬌􀷜􀭗:􀝶􀾍􀖃􁬌􀬧􀚜􀛸:Hessian 􀔫􁬰􀚫􀬧􀚜􀛸
􁭇􁊠􁝜􀢱:􀖃􀙁􀖃􀚊􀝇􀷄􀷄􀴝􀛱􁫾􀥟􀒅􀵉􀗀􁘏􀾲􁁾􁩇􁘏􀓻􀷄􀥚􀒅􀵉􀗀􁘏
􀜴􀛎􁫾􀥟􀒅􀝢􀖃􀷈􀕯􀌶 􁭇􁊠􀣋􀸧:􁶭􁶎􀖃􁬌􀒅􀷈􀕯􀖃􁬌􀒅􀱲􀓨􀜻􁊞
hessian 􀹐􀛓􀔰􀶙􀖢
7. http 􁯻􁊠 Spring 􁌱 HttpInvoker 􀨫􁈿 􀤚􀔭 http 􁤒􀜔􁌱􁬱􁑕􁧣􁊠􀜐􁦓􀌶
􁬳􀴳􀓻􀷄:􀥚􁬳􀴳 􁬳􀴳􀷜􀭗:􁎨􁬳􀴳 􀖃􁬌􀜐􁦓:HTTP 􀖃􁬌􀷜􀭗:􀝶􀾍􀖃􁬌
􀬧􀚜􀛸:􁤒􀜔􀬧􀚜􀛸(JSON) 􁭇􁊠􁝜􀢱:􀖃􀙁􀖃􀚊􀝇􀷄􀷄􀴝􀛱􀥟􀩜􁂰􀝳􀒅􀵉
􀗀􁘏􀾲􁁾􁩇􁘏􀓻􀷄􀥚􀒅􀝢􁊠􁁨􁥦􀢏􀺱􁍡􀒅􀝢􁊠􁤒􀜔􀱲 URL 􀖃􀙁􀝇􀷄􀒅
􀸮􀓧􀶪􀳮􀖃􀷈􀕯􀌶􁭇􁊠􀣋􀸧:􁵱􀝶􀷸􁕳􀬫􁊠􁑕􀬧􀞾􁁨􁥦􀢏 JS 􀖵􁊠􁌱􀹐
􀛓􀌶
8. Webservice 􀤚􀔭 CXF 􁌱 frontend-simple 􀞾 transports-http 􀨫􁈿 􀤚􀔭
WebService 􁌱􁬱􁑕􁧣􁊠􀜐􁦓􀌶 􁬳􀴳􀓻􀷄:􀥚􁬳􀴳 􁬳􀴳􀷜􀭗:􁎨􁬳􀴳 􀖃􁬌
􀜐􁦓:HTTP 􀖃􁬌􀷜􀭗:􀝶􀾍􀖃􁬌 􀬧􀚜􀛸:SOAP 􀷈􀹜􀬧􀚜􀛸􁭇􁊠􀣋􀸧:􁔮􁕹
􁵞􀱮􀒅􁪜􁧍􁥺􁧣􁊠􀌶
9. Thrif Thrift 􀸎 Facebook 􀴓􁕳 Apache 􁌱􀓞􀓻 RPC 􀻛􀺝􀒅􀭮􀚹 dubbo 􀶪
􀳮􁌱 thrift 􀜐􁦓􀸎􀩒 thrift 􀜻􁊞􀜐􁦓􁌱􀲘􀪀􀒅􀣁􀜻􁊞􀜐􁦓􁌱􀤚􁏐􀓤􁂲􀛒􀔧
􀓞􀔶􁷐􀥘􁌱􀥧􀗞 􀯳􀒅􀾲􀦇 service name􀒅magic number 􁒵
1􀌵Synchronized􁊠􁬦􀞀􀒅􀙌􀜻􁉘􀸎􀕋􀔍􀒘
􁬯􀸎􀓞􁭲Java􁶎􁦶􀓾􀙾􀔒􁌯􀚓􁌯􀕿􁳯􀚩􁌱􁳯􁷌􀒅􀢩􀔅􁀌􀹍􀕱􀖜􀙟􁬦􀬚􀝎􁑕
􀬧􁌱􀭏􀝎􁘏􀕿􁀌􀞍􁧔􀱲􁘏􁀌􀴳􁥶􁬦Synchronized􀌶Synchronized􀸎􁊧JVM
􀨫􁈿􁌱􀓞􁐿􀨫􁈿􀔰􀷕􀝶􀾍􁌱􀓞􁐿􀷜􀭗􀒅􀦇􀺎􀖦􀺱􁍡􁤩Synchronized􀗥􁷶􁬦
􁌱􁑕􀬧􀣘􁖫􁦲􀝸􁌱􀨁􁜓􁎱􀒅􀕿􀝎􁈿􀒅􁤩Synchronized􀗥􁷶􁬦􁌱􁑕􀬧􀣘􀒅􀣁
􁖫􁦲􀚹􀝸􁤩􁖫􁦲􀢏􁊞􀱮􀔧monitorenter􀞾monitorexit􀓷􀓻􀨁􁜓􁎱􀳰􀕥􀌶􁬯􀓷
􀓻􀳰􀕥􀸎􀕋􀔍􀰺􀯏􀞫􀒘􀣁􁡦􀳙􀹢􀲗􁤈􀚩monitorenter􀳰􀕥􀷸􀒅􁸒􀘶􁥝􀩤􁦶
􀓣􀌵􀬚􀝎􁖫􁑕􁹛􁕆􁶎􁦶􀓫􀻄
􁞴􀝐􀩒􁨝􁌱􁲁􀒓􀦇􀺎􁬯􀓻􀩒􁨝􁀌􀹍􁲁􀨧􀒅􀱲􁘏􀭮􀚹􁕚􁑕􀫪􁕪􀳜􀹍􀔧􁬯􀓻􀩒
􁨝􁌱􁲁􀒅􀲩􁲁􁌱􁦇􀷄􀢏+ 1􀒔􀭮􀲗􁤈monitorexit􀳰􀕥􀷸􀩙􁲁􁦇􀷄􀢏-1􀒔􀭮􁦇
􀷄􀢏􀔅0􀷸􀒅􁲁􀩪􁤩􁯽􀶱􀔧􀌶􀦇􀺎􁞴􀝐􀩒􁨝􀥦􁨳􀔧􀒅􁮎􀭮􀚹􁕚􁑕􀩪􁥝􁴥􀤲
􁒵􀮇􀒅􁍗􀚩􀩒􁨝􁲁􁤩􀝚􀥘􀓞􀓻􁕚􁑕􁯽􀶱􀔅􀾊􀌶Java􀓾Synchronize􁭗􁬦􀣁􀩒
􁨝􀥧􁦡􁗝􀺽􁦕􀒅􁬡􀚩􀔧􁞴􀝐􁲁􀞾􁯽􀶱􁲁􁌱􁍓􁌱􀌶
2􀌵􀖦􀚟􀲍􀵉􀚩􁞴􀝐􀩒􁨝􁌱􁲁􀒅􁬯􀓻 “􁲁 ”􀚩􀬬􀸎􀕋􀔍􀒘􀦇􀖜􁏟􀨧􀩒􁨝􁌱
􁲁􀒘
“􁲁 ”􁌱􀹜􁨶􀙌􀨫􀸎monitorenter􀞾monitorexit􀨁􁜓􁎱􀳰􀕥􁌱􀓞􀓻Reference
􁔄􀣳􁌱􀝇􀷄􀒅􀜨􁥝􁲁􀨧􀞾􁥴􁲁􁌱􀩒􁨝􀌶􀱯􀕪􁎣􁭲􀒅􀖵􁊠Synchronized 􀝢􀕦
􀗥􁷶􀓧􀝶􁌱􀩒􁨝􀒅􀢩􀾌􀒅􀩒􀬫􁌱􀩒􁨝􁲁􀝢􀕦􁬯􀔍􁏟􀨧􀌶
1. 􀦇􀺎 Synchronized 􀸁􁏟􀳰􀨧􀔧􁲁􀩒􁨝􀒅􀾲􀦇 Synchronized(􀝒􁰁􀝷)􀌵
Synchronized(this) 􁒵􀒅􁧔􀸁􀛒􁥴􁲁􀩒􁨝􀔅􁧆􀩒􁨝􀌶
2. 􀦇􀺎􁀌􀹍􀸁􁏟􀳰􀨧:
􁝑 Synchronized 􀗥􁷶􁌱􀷜􁀩􀔅􁶋􁶉􀮾􀷜􁀩􀒅􁤒􁐏􀾌􀷜􁀩􀩒􀬫􁌱􀩒􁨝􀔅 􁲁
􀩒􁨝;
􁝑 Synchronized 􀗥􁷶􁌱􀷜􁀩􀔅􁶉􀮾􀷜􁀩􀒅􀚞􁤒􁐏􀾌􀷜􁀩􀩒􀬫􁌱􁔄􀩒􁨝 􀔅
􁲁􀩒􁨝􀌶
􁀳􀰺􀒅􀭮􀓞􀓻􀩒􁨝􁤩􁲁􀖘􀷸􀒅􀩒􁨝􁯾􁶎􀲅􀹍􁊠 Synchronized 􀗥􁷶􁌱 􀷜􁀩
􁮷􀩙􀔾􁊞􀤫􀤲􀒅􁘒􀩒􁨝􁯾􁶋 Synchronized 􀗥􁷶􁌱􀷜􁀩􀝢􀾋􀬉􁤩 􁧣􁊠􀒅􀓧
􀝑􁲁􀭽􀟥􀌶
3􀌵􀕋􀔍􀸎􀝢􁯿􀙁􀯔􀒅􀔅􀕋􀔍􁧔 Synchronized 􀸎􀝢􁯿􀙁􁲁?
􀝢􁯿􀙁􀯔􀸎􁲁􁌱􀓞􀓻􀤚􀹜􁥝􀿢􀒅􀸎􀔅􀔧􁥴􀙬􁛔􀫩􁲁􀾒􁛔􀫩􁌱􀰘􀙭􀌶
􀾲􀦇􀓥􁶎􁌱􀖉􀕤􁎱􀒅􀓞􀓻􁔄􀓾􁌱􀝶􀾍􀷜􁀩􁧣􁊠􀝚􀓞􀓻􀝶􀾍􀷜􁀩􀒅􀘃􀦇
Synchronized 􀓧􀶪􀳮􁯿􀙁􀒅􁬰􀙁 method2 􀷜􁀩􀷸􀭮􀚹􁕚􁑕􁞴􀮑􁲁􀒅
method2 􀷜􁀩􁯾􁶎􀲗􁤈 method1 􀷸􀭮􀚹􁕚􁑕􀝈􁥝􀝄􀩤􁦶􁞴􀝐􁲁􀒅􁬯 􀷸􀦇
􀺎􀓧􀶪􀳮􁯿􀙁􀒅􀨙􀩪􁥝􁒵􁯽􀶱􀒅􀲩􁛔􀫩􁴥􀤲􀒅􀩕􁛘􁛔􀫩􁲁􀾒􁛔􀫩􀌶
􀩒 Synchronized 􀹶􁧔􀒅􀝢􁯿􀙁􀯔􀸎􀸔􁘒􀸃􁥠􁌱􀒅􀚟􀲍􀵉􀚩􀒅􀣁􀲗􁤈
monitorenter 􀳰􀕥􀷸􀒅􀦇􀺎􁬯􀓻􀩒􁨝􁀌􀹍􁲁􀨧􀒅􀱲􁘏􀭮􀚹􁕚􁑕􀫪􁕪􀳜􀹍􀔧
􁬯􀓻􀩒􁨝􁌱􁲁(􁘒􀓧􀸎􀫪􀳜􀹍􀔧􁲁􀚞􀓧􁚆􁖀􁖅􁞴􀝐)􀒅􀩪􀲩􁲁􁌱􁦇 􀷄􀢏 +1􀒅
􀙌􀨫􀹜􁨶􀓤􀩪􁭗􁬦􁬯􁐿􀷜􀭗􀨫􁈿􀔧􀝢􁯿􀙁􀯔􀌶
4􀌵JVM 􀩒 Java 􁌱􀜻􁊞􁲁􀘉􀔧􀟺􀔶􀕽􀛸?
􀣁 Java 6 􀔏􀚹􀒅Monitor 􁌱􀨫􁈿􀨠􀙂􀗁􁩢􀬬􀩶􀶙􀖢􁔮􁕹􁌱􀔰􀷕􁲁􀹶 􀨫􁈿􀒅
􀔞􀩪􀸎􀱯􀕪􀚟􀲍􀣁􁳯􁷌􀔫􀓾􀲅􁴏􁬿􁌱􁞴􀝐/􁯽􀶱􁲁􁌱􁭦􁬋􀌶
􁊧􀔭 Java 􀩶􁶎􁌱􁕚􁑕􀓨􀶙􀖢􁔮􁕹􁌱􀜻􁊞􁕚􁑕􀹍􀸉􀩘􀙉􁔮􀒅􀦇􀺎􁥝􀩙􀓞 􀓻
􁕚􁑕􁬰􁤈􁴥􀤲􀱲􀠏􁩸􁮷􁵱􁥝􀶙􀖢􁔮􁕹􁌱􀜐􀛗􀒅􁬯􀩪􁵱􁥝􀕗􁊠􀲁􀮾􀚔􀴘 􀚩􀙖
􀻐􀮾􀹶􀲗􁤈􀒅􁬯􁐿􀚔􀴘􀕤􀕰􀜈􀚓􀷼􁩃􀒅􀮉􁘙􀥒􁉘􀢏􀷸􁳵􀒅􁈿􀕤 JDK 􀓾􀘉
􀔧􀥟􁰁􁌱􀕽􀛸􀌶 􀓞􁐿􀕽􀛸􀸎􀖵􁊠􁛔􀷤􁲁􀒅􀜨􀣁􀲩􁕚􁑕􁬰􁤈􁴥􀤲􀶙􀖢􀔏􀚹􀘶
􁦏􁕚􁑕􁛔􀷤􁒵 􀮇􀓞􀾧􀷸􁳵􀒅􀝢􁚆􀣁􁒵􀮇􀹗􁳵􀙌􀕜􁕚􁑕􀫪􁕪􁥴􁲁􀒅􁬯􀷸􀩪􀷫
􁵱􀙚􁦏􁕚􁑕 􀲗􁤈􁴥􀤲􀶙􀖢􀒅􁭿􀘹􀔧􁊠􀲁􀮾􀚩􀙖􀻐􀮾􁌱􀚔􀴘􀌶
􁈿􀕤 JDK 􀓾􁬮􀵉􀗀􀔧􀓣􁐿􀓧􀝶􁌱 Monitor 􀨫􁈿􀒅􀔞􀩪􀸎􀓣􁐿􀓧􀝶􁌱 􁲁:
• 􀘇􀝻􁲁(Biased Locking)
• 􁫷􁰁􁕆􁲁
• 􁯿􁰁􁕆􁲁
􁬯􀓣􁐿􁲁􀖵􀮑 JDK 􀮑􀕦􀕽􀛸 Synchronized 􁌱􁬩􁤈􀒅􀭮 JVM 􀼄􁁥 􀚩􀓧􀝶
􁌱􁒋􀔩􁇫􀙭􀷸􀒅􀕿􁛔􀛖􀚔􀴘􀚩􁭇􀝳􁌱􁲁􀨫􁈿􀒅􁬯􀩪􀸎􁲁􁌱􀜋􁕆􀌵 􁴳􁕆􀌶
• 􀭮􁀌􀹍􁒋􀔩􀚊􁈿􀷸􀒅􁼕􁦊􀕿􀖵􁊠􀘇􀝻􁲁􀌶
JVM 􀕿􀚥􁊠 CAS 􀶙􀖢􀒅􀣁􀩒􁨝􀥧􀓤􁌱 Mark Word 􁮱􀚓􁦡􁗝􁕚􁑕 ID􀒅􀕦􁤒
􁐏􁬯􀓻􀩒􁨝􀘇􀝻􀔭􀭮􀚹􁕚􁑕􀒅􀲅􀕦􀬚􀓧􁁿􀝊􁍥􀾋􁌱􀔰􀷕􁲁􀒅􀢩 􀔅􀣁􀮉􀥚􀬫
􁊠􀣋􀸧􀓾􀒅􀥟􁮱􀚓􀩒􁨝􁊞􀞸􀞮􀹗􀓾􀹋􀥚􀕿􁤩􀓞􀓻􁕚􁑕􁲁􀨧􀒅 􀖵􁊠􀘇􀷑􁲁􀝢
􀕦􁴳􀖗􀷫􁒋􀔩􀭏􁲀􀌶
• 􀦇􀺎􀹍􀝚􀓞􁕚􁑕􁦶􀢶􁲁􀨧􀺤􀓻􁤩􀘇􀷑􁬦􁌱􀩒􁨝􀒅JVM 􀩪􀶋􁲀􀘇􀷑􁲁􀒅 􀚔
􀴘􀚩􁫷􁰁􁕆􁲁􀨫􁈿􀌶
• 􁫷􁰁􁕆􁲁􀗁􁩢 CAS 􀶙􀖢 Mark Word 􀹶􁦶􀢶􁞴􀝐􁲁􀒅􀦇􀺎􁯿􁦶􀱮􀛑􀒅 􀩪
􀖵􁊠􀸦􁭗􁌱􁫷􁰁􁕆􁲁;􀞈􀚞􀒅􁬰􀓞􀾍􀜋􁕆􀔅􁯿􁰁􁕆􁲁􀌶
5􀌵􀔅􀕋􀔍􁧔 Synchronized 􀸎􁶋􀙄􀬘􁲁?
􁶋􀙄􀬘􀔆􁥝􁤒􁈿􀣁􁞴􀝐􁲁􁌱􁤈􀔅􀓤􀒅􀬚􁶋􀸎􀳲􁆙􁊩􁧗􁲁􁌱􀷸􁳵􀚹􀝸􁕳􁒵 􀮇
􁕚􁑕􀚓􁯈􁲁􁌱􀒅􀾯􀭮􁲁􁤩􁯽􀶱􀝸􀒅􀕱􀖜􀓞􀓻􁕚􁑕􁮷􀹍􀹢􀕿􁒋􀔩􀚩􁲁􀒅 􁬯􀻏
􀘉􁌱􁍓􁌱􀸎􀔅􀔧􀵉􁹛􀲗􁤈􀯔􁚆􀒅􁗌􁅩􀸎􀝢􁚆􀕿􀔾􁊞􁕚􁑕􁷬􁸀􁈿􁨝􀌶
6􀌵􀕋􀔍􀸎􁲁􁁾􁴻􀞾􁲁􁔋􀛸?
• 􁲁􁁾􁴻:􀳰􁡦􀳙􀹢􀜨􀷸􁖫􁦲􀢏􀣁􁬩􁤈􀷸􀒅􀩒􀓞􀔶􀕤􁎱􀓤􁥝􀿢􀝶􀾍􀒅􀖕􁤩 􀼄
􁁥􀚩􀓧􀝢􁚆􀨂􀣁􀙈􀕁􀷄􀴝􁒋􀔩􁌱􁲁􁬰􁤈􁁾􁴻􀌶􀔆􁥝􀻑􀴝􁭈􁭥􀚓􀺉􀌶
􁑕􀬧􀞧􀯆􀔍􀕿􀣁􀸁􁎣􁭲􀓧􀨂􀣁􀷄􀴝􁒋􀔩􁌱􀰘􀙭􀓥􀖵􁊠􀝶􀾍􀞫?􀮉􀥚􀓧􀸎 􁑕
􀬧􀞧􁛔􀫩􀛒􀙁􁌱􀌶
• 􁲁􁔋􀛸:􀜻􀚞􀓤􀒅􀝶􀾍􀣘􁌱􀖢􁊠􁝜􀢱􁥝􀩱􁰁􀩜􀌶􀖕􀸎􀦇􀺎􀓞􁔮􀚜􁌱􁬳􁖅 􀶙
􀖢􁮷􀩒􀝶􀓞􀓻􀩒􁨝􀝍􀥔􀛒􁲁􀞾􁥴􁲁􀒅􁊜􁛗􀛒􁲁􀶙􀖢􀣁􀮗􁈾􀖛􀙖􀒅􁷇􁔺 􀣈􁬰
􁤈􀔰􀷕􀝶􀾍􀶙􀖢􀔞􀕿􀩕􁛘􀓧􀮠􁥝􁌱􀯔􁚆􀴖􁘙􀌶
􁲁􁔋􀛸􀩪􀸎􀥀􀥟􁲁􁌱􀖢􁊠􀤒􀌶
7􀌵􀔅􀕋􀔍􁧔 Synchronized 􀸎􀓞􀓻􀰓􁥡􁲁?􀔔􁥡􁲁􁌱􀨫􁈿􀜻􁉘 􀝈􀸎􀕋􀔍?
􀕋􀔍􀸎 CAS􀒅􀨙􀹍􀕋􀔍􁇙􀯔?
Synchronized 􀸔􁆐􀸎􀓞􀓻􀰓􁥡􁲁􀒅􀢩􀔅􀨙􁌱􀬚􀝎􁒽􁊼􀸎􀰓􁥡􁌱: 􀓧􁓕􀸎􀞈
􀕿􀔾􁊞􁒋􀔩􀒅􀕱􀖜􁌱􀷄􀴝􀶙􀖢􁮷􀮠􁶳􁥝􀛒􁲁􀌵􁊠􀲁􀮾􀻐􀮞􀮾􁫨 􀴘􀌵􁖌􀲷􁲁
􁦇􀷄􀢏􀞾􀼄􀺱􀸎􀞈􀹍􁤩􁴥􀤲􁌱􁕚􁑕􁵱􁥝􁤩􀠏􁯯􁒵􀶙􀖢􀌶􁵋􁍳􁏝􀕯􀳰􀕥􁵞􁌱
􀝎􀪀􀒅􀱯􀕪􀝢􀕦􀖵􁊠􀤚􀔭􀙫􁑱􀼄􁁥􁌱􀔔􁥡􀬚􀝎􁒽􁊼􀌶􀘶􁬰􁤈􀶙􀖢􀒅􀦇􀺎􁀌
􀹍􀙌􀕜􁕚􁑕􀮄􁊠􀷄􀴝􀒅􁮎􀶙􀖢􀩪􀱮􀛑􀔧; 􀦇􀺎􀙈􀕁􀷄􀴝􀹍􀮄􁊠􀒅􀔾􁊞􀔧􀙫
􁑱􀒅􁮎􀩪􀙚􁬰􁤈􀙌􀕜􁌱􁤑􀘑􀴷􀷞􀌶􁬯􁐿􀔔􁥡􁌱􀬚􀝎􁒽􁊼􁌱􁦜􀥚􀨫􁈿􀓧􁵱􁥝
􁕚􁑕􀳯􁩸􀒅􀲅􀕦􁤩􁑍􀔅􁶋􁴥􀤲􀝶􀾍􀌶􀔔􁥡􁲁􁌱􀻐􀮞􁓒􁀩􀸎
CAS(Compareand Swap􀒅􀾲􁫾􀬚􀔻􀴘)􀒅􀨙􁁿􀝊􀚩􀓣􀓻􀶙􀖢􀷄:􀙖􀨂􊧊􀌵􁶼
􀹗􊧊􀌵􀷛􊧊􀌶􀭮􀓬􀕐􀭮􁶼􀹗􊧊􀞾􀙖􀨂􊧊􁍘􁒵􀷸􀲍􀩙􀙖􀨂􊧊􀗥􀶯􀔅􀷛􊧊􀌶
􁬯􀻏􀥒􁉘􁌱􁭦􁬋􀸎􀒅􁸒􀘶􀼄􀺱􀺤􀣘􀙖􀨂􁌱􊧊􀸎􀞈􁪙􀔏􀚹􀱯􁧛􀝐􀷸􁌱􀓞 􀻏􀒅
􀦇􀓧􀓞􀻏􀚞􁤒􁐏􀹗􁳵􀾌􀙖􀨂􊧊􀫪􁕪􁤩􀚦􁌱􁕚􁑕􀹅􀶯􁬦􀒅􁛣􀭒􀹜􀽺􀶙 􀖢􀒅􀞈
􀚞􁧔􀸁􀹗􁳵􁀌􀹍􀙌􀕜􁕚􁑕􀩒􀾌􀙖􀨂􊧊􀶙􀖢􀒅􀝢􀕦􀲩􀷛􊧊􁦡􁗝􁕳􀾌 􀣘􀙖􀨂􀌶
CAS 􀙍􀹍􀜻􀧼􀯔􀒅􀨙􁌱􀜻􀧼􀯔􁊧 CPU 􁏝􀕯􀳰􀕥􀨫􁈿􀗛􁦤􀒅􀜨􀖵􁊠 JNI 􁧣
􁊠 Native 􀷜􁀩􁧣􁊠􁊧 C++ 􁖫􀙟􁌱􁏝􀕯􁕆􀚦􀳰􀕥􀒅JDK 􀓾􀵉 􀗀􀔧 Unsafe
􁔄􀲗􁤈􁬯􀔶􀶙􀖢􀌶
8􀌵􀔔􁥡􁲁􀓞􀨧􀩪􀸎􀦅􁌱􀞀?
􀔔􁥡􁲁􁭿􀘹􀔧􀰓􁥡􁲁􁇿􀜛􀩒􁨝􁌱􁈿􁨝􀒅􀝶􀷸􀔞􀵉􁹛􀔧􀬚􀝎􀯔􁚆􀒅􀖕􀨙􀔞􀹍
􁗌􁅩:
1. 􀔔􁥡􁲁􀝝􁚆􀗛􁦤􀓞􀓻􀙈􀕁􀝒􁰁􁌱􀜻􀧼􀶙􀖢􀌶􀦇􀺎􀥚􀓞􀓻􀱲􀙾􀓻􀝒􁰁􀒅􀔔
􁥡􁲁􀩙􀝒􀮑􀛎􀓧􀕗􀮞􀒅􀖕􀔰􀷕􁲁􁚆􁫷􀸃􁥴􀙬􀒅􀓧􁓕􀩒􁨝􀷄􁰁􀥚􀩝􀝊􀩒􁨝􁷋
􁔉􀬶􀥟􀩜􀌶
2. 􁳩􀷸􁳵􁛔􀷤􀝢􁚆􀩕􁛘􀭏􁲀􀥟􀌶􀘃􀦇 CAS 􁳩􀷸􁳵􀓧􀱮􀛑􁘒􀓞􁍗􁛔􀷤􀒅􀕿
􁕳 CPU 􀬃􀹶􀮉􀥟􁌱􀭏􁲀􀌶
3. ABA 􁳯􁷌􀌶CAS 􁌱􀻐􀮞􀯏􀰮􀸎􁭗􁬦􀾲􀩒􀙖􀨂􊧊􀓨􁶼􀹗􊧊􀸎􀞈􀓞􀻏􁘒􀚣
􀷙􀙖􀨂􊧊􀸎􀞈􁤩􀶯􁬦􀒅􀖕􁬯􀓻􀚣􀷙􁭦􁬋􀓧􀓸􁨆􀒅􀘃􀦇􀙖􀨂􊧊􀜻􀹶􀸎 A􀒅 􀝸
􀹶􁤩􀓞􀹵􁕚􁑕􀶯􀔅 B􀒅􀹋􀝸􀝈􁤩􀶯􀱮􀔧 A􀒅􀚞 CAS 􁦊􀔅􀾌􀙖􀨂􊧊􀬚􁀌􀹍􀝎
􁊞􀶯􀝒􀒅􀖕􀨫􁴬􀓤􀸎􀹍􁤩􀙌􀕜􁕚􁑕􀶯􁬦􁌱􀒅􁬯􁐿􀰘􀙭􀩒􀗁􁩢􁬦􁑕􊧊􁌱􀰘􀸧
􁌱􁬩􁓒􁕮􀺎􀭽􀟥􀮉􀥟􀌶􁥴􀙬􁌱􀯏􁪠􀸎􀭚􀙁􁇇􀹜􀝩􀒅􀾯􀽺􀝒􁰁􀹅􀷛􁮷􀲩􁇇􀹜
􀝩􀛒􀓞􀌶
9􀌵􁪙 Synchronized 􁍘􀾲􀒅􀝢􁯿􀙁􁲁 ReentrantLock 􀙌􀨫􁈿 􀜻􁉘􀹍􀕋
􀔍􀓧􀝶?
􀙌􀨫􀒅􁲁􁌱􀨫􁈿􀜻􁉘􀤚􀹜􀸎􀔅􀔧􁬡􀚩􀓞􀓻􁍓􁌱: 􁦏􀲅􀹍􁌱􁕚􁑕􁮷􁚆􁍡􀚩􀺤
􁐿􀺽􁦕􀌶
Synchronized 􁭗􁬦􀣁􀩒􁨝􀥧􀓾􁦡􁗝􀺽􁦕􀨫􁈿􀔧􁬯􀓞􁍓􁌱􀒅􀸎􀓞􁐿 JVM 􀜻
􁊞􁌱􁲁􀨫􁈿􀷜􀭗􀒅􁘒 ReentrantLock 􀕦􀝊􀲅􀹍􁌱􀤚􀔭 Lock 􀴳􀝗􁌱 􀨫􁈿
􁔄􀒅􁮷􀸎􁭗􁬦􁊠􀓞􀓻 volitile 􀗥􁷶􁌱 int 􀣳􀝒􁰁􀒅􀬚􀗛􁦤􀾯􀓻􁕚 􁑕􁮷􁚆􀳜􀹍
􀩒􁧆 int 􁌱􀝢􁥠􀯔􀞾􀜻􀧼􀗥􀶯􀒅􀙌􀹜􁨶􀸎􀤚􀔭􀲅􁧲􁌱 AQS 􀻛􀺝􀌶
10􀌵􁮎􀔍􁧗􁧨􁧨 AQS 􀻛􀺝􀸎􀯆􀔍􀢧􀔪􀘯?
AQS(AbstractQueuedSynchronizer 􁔄)􀸎􀓞􀓻􁊠􀹶􀺅􀭌􁲁􀞾􀝶􀾍􀢏􁌱􀻛􀺝􀒅
􀝱􁐿 Lock 􀛱􀓾􁌱􁲁(􀬉􁊠􁌱􀹍 ReentrantLock􀌵 ReadWriteLock) 􀒅􀕦􀝊􀙌
􀕜􀦇 Semaphore􀌵CountDownLatch􀒅 􁊜􁛗􀸎􀷱􀹗􁌱 FutureTask 􁒵􀒅􁮷􀸎
􀤚􀔭 AQS 􀹶􀺅􀭌􀌶
1. AQS 􀣁􀙖􁮱􀨧􀔎􀔧􀓞􀓻 volatile int state 􀝒􁰁􀒅􁤒􁐏􀝶􀾍􁇫􀮾:􀭮􁕚􁑕􁧣
􁊠 lock 􀷜􁀩􀷸 􀒅􀦇􀺎 state=0􀒅􁧔􀸁􁀌􀹍􀕱􀖜􁕚􁑕􀜛􀹍􀙈􀕁􁩒􁃠 􁌱
􁲁􀒅􀝢􀕦􁞴􀮑􁲁􀬚􀩙 state=1;􀦇􀺎 state=1􀒅􀚞􁧔􀸁􀹍􁕚􁑕􁍓􀚹􀾋􀣁 􀖵
􁊠􀙈􀕁􀝒􁰁􀒅􀙌􀕜􁕚􁑕􀮠􁶳􀛒􀙁􀝶􀾍􁴚􀚜􁬰􁤈􁒵􀮇􀌶
2. AQS 􁭗􁬦 Node 􀙖􁮱􁔄􀺅􀱮􁌱􀓞􀓻􀝌􀝻􁱾􁤒􁕮􀺅􁌱􀝶􀾍􁴚􀚜􀒅􀹶􀨠􀱮􁕚
􁑕􁞴􀝐􁲁􁌱􀴭􁴚􀫡􀖢􀒅􀭮􀹍􁕚􁑕􁞴􀝐􁲁􀥦􁨳􀝸􀒅􀩪􁤩􁂲􀛒􀚩􁴚􀚜􀹛􀩲􀌶
• Node 􁔄􀸎􀩒􁥝􁦢􁳯􀝶􀾍􀕤􁎱􁌱􁕚􁑕􁌱􀩗􁤰􀒅􀛱􀞌􀔧􁕚􁑕􀹜􁫝􀝊􀙌􁇫
􀮾􀝞
waitStatus(􀹍􀔲􁐿􀓧􀝶􀝐􊧊􀒅􀚓􀚦􁤒􁐏􀸎􀞈􁤩􁴥􀤲􀒅􀸎􀞈􁒵􀮇􀠏􁯯􀒅 􀸎
􀞈􀫪􁕪􁤩􀝐􁁾􁒵)􀒅􀾯􀓻 Node 􁕮􁅩􀙉􁘶􀙌 prev 􁕮􁅩􀞾 next 􁕮 􁅩􀒅􀷜􀗎
􁕚􁑕􁯽􀶱􁲁􀝸􀮳􁭛􀠏􁯯􀓥􀓞􀓻􀣁􁒵􀮇􁌱􁕚􁑕􀒅􀸎􀓞􀓻 FIFO 􁌱􁬦􁑕􀌶
• Node 􁔄􀹍􀓷􀓻􀬉􁰁􀒅SHARED 􀞾 EXCLUSIVE􀒅􀚓􀚦􀕤􁤒􀙈􀕁􀽜􀭗􀞾
􁇿􀜛􀽜􀭗􀌶􀲅􁧲􀙈􀕁􀽜􀭗􀸎􀓞􀓻􁲁􊧋􁦜􀥚􀹵􁕚􁑕􀝶􀷸􀶙􀖢(􀗞􀝩􁰁
Semaphore 􀩪􀸎􀤚􀔭 AQS 􁌱􀙈􀕁􀽜􀭗􀨫􁈿􁌱)􀒅􁇿􀜛􀽜􀭗􀸎􀝶􀓞􀓻􀷸
􁳵􀾧􀝝􁚆􀹍􀓞􀓻􁕚􁑕􀩒􀙈􀕁􁩒􁃠􁬰􁤈􀶙􀖢􀒅􀥚􀖟􁌱􁧗􀿢􁕚􁑕􁵱􁥝􀴭􁴚􁒵
􀮇 ( 􀦇 ReentranLock) 􀌶
3. AQS 􁭗􁬦􀙖􁮱􁔄 ConditionObject 􀺅􀭌􁒵􀮇􁴚􀚜(􀝢􀹍􀥚􀓻)􀒅􀭮
Condition 􁧣􁊠 wait() 􀷜􁀩􀝸􀒅􁕚􁑕􀩙􀕿􀛒􀙁􁒵􀮇􁴚􀚜􀓾􀒅􁘒􀭮
Condition 􁧣􁊠 signal() 􀷜􁀩􀝸􀒅􁕚􁑕􀩙􀕗􁒵􀮇􁴚􀚜􁫨􁑏􀛖􀝶􀾍􁴚􀚜􀓾􁬰
􁤈􁲁􁒋􀔩􀌶
4. AQS 􀞾 Condition 􀝱􁛔􁖌􀲷􀔧􀓧􀝶􁌱􁴚􀚜􀒅􀣁􀖵􁊠 Lock 􀞾 Condition
􁌱􀷸􀗲􀒅􀙌􀨫􀩪􀸎􀓷􀓻􁴚􀚜􁌱􀔰􁍘􁑏􀛖􀌶
11􀌵􁧗􀩱􀝢􁚆􁧇􀩱􀣈􀩒􀾲􀓥 Synchronized 􀞾 ReentrantLock 􁌱􀭑􀝶􀌶
ReentrantLock 􀸎 Lock 􁌱􀨫􁈿􁔄􀒅􀸎􀓞􀓻􀔰􀷕􁌱􀝶􀾍􁲁􀌶􀕗􀛑􁚆􁥯􀬶􀒅
ReentrantLock 􀾲 Synchronized 􁌱􀝶􀾍􀶙􀖢􀹅􁔜􁕡(􀢩􀔅􀝢􀕦􀘟􀸦􁭗􀩒􁨝􀓞
􀻏􀖵􁊠)􀒅􁊜􁛗􀨫􁈿 Synchronized 􁀌􀹍􁌱􁹛􁕆􀛑􁚆􀒅􀦇:
• 􁒵􀮇􀝢􀓾􀷙:􀭮􀳮􀹍􁲁􁌱􁕚􁑕􁳩􀹗􀓧􁯽􀶱􁲁􁌱􀷸􀗲􀒅􀾋􀣁􁒵􀮇􁌱􁕚􁑕􀝢􀕦
􁭌􀳠􀶱􀭒􁒵􀮇􀒅􀩒􀥒􁉘􀲗􁤈􀷸􁳵􁶋􀬉􁳩􁌱􀝶􀾍􀣘􀮉􀹍􁊠􀌶
• 􀬃􁩻􀷸􁌱􁞴􀝐􁲁􀩤􁦶:􀣁􀳰􀨧􁌱􀷸􁳵􁝜􀢱􀙖􁞴􀝐􁲁􀒅􀦇􀺎􀷸􁳵􀚩􀔧􀕖􁆐􀷫
􁀩􁞴􀝐􀚞􁬬􀢧􀌶
• 􀝢􀕦􀚣􀷙􀸎􀞈􀹍􁕚􁑕􀣁􀴭􁴚􁒵􀮇􁞴􀝐􁲁􀌶
• 􀝢􀕦􀟥􀬫􀓾􀷙􁧗􀿢:􀓨 Synchronized 􀓧􀝶􀒅􀭮􁞴􀝐􀚩􁲁􁌱􁕚􁑕􁤩􀓾􀷙
􀷸􀒅􁚆􀥜􀟥􀬫􀓾􀷙􀒅􀓾􀷙􀭑􀬉􀩙􀕿􁤩􀲲􀚊􀒅􀝶􀷸􁲁􀕿􁤩􁯽􀶱􀌶
• 􀝢􀕦􀨫􁈿􀙄􀬘􁲁􀌶
􀕗􁲁􁯽􀶱􁥯􀬶􀒅Synchronized 􀣁 JVM 􀩶􁶎􀓤􀨫􁈿􁌱􀒅􀓧􀖕􀝢􀕦􁭗􁬦􀓞􀔶
􁍊􀴴􀫡􀙍􁍊􀴴 Synchronized 􁌱􁲁􀨧􀒅􁘒􀓬􀣁􀕤􁎱􀲗􁤈􀚊􁈿􀭑􀬉 􀷸􀒅JVM
􀕿􁛔􀛖􁯽􀶱􁲁􀨧;􀖕􀸎􀖵􁊠 Lock 􀚞􀓧􁤈􀒅Lock 􀸎􁭗􁬦􀕤􁎱􀨫􁈿􁌱􀒅􁥝􀗛􁦤
􁲁􀨧􀓞􀨧􀕿􁤩􁯽􀶱􀒅􀩪􀮠􁶳􀩙 unLock() 􀶱􀚩 finally{} 􀓾 􀌶
􀕗􀯔􁚆􁥯􀬶􀒅Synchronized 􀷱􀹗􀨫􁈿􀾲􁫾􀖗􀶴􀒅􀩒􀾲ReentrantLock􀒅􀥟􀥚􀷄􀣋􀸧􀯔􁚆􁮷􁍘􀫧􁫾􀥟􀌶
􀖕􀸎􀣁 Java 6 􀓾􀩒􀙌􁬰􁤈􀔧􁶋􀬉􀥚􁌱􀶯􁬰􀒅􀣁􁒋􀔩􀓧􁄶􁅱􀷸􀒅
Synchronized 􁌱􀯔􁚆􁥝􀕽􀔭 ReetrantLock;􀣁􁹛􁒋􀔩􀰘􀙭􀓥􀒅
Synchronized 􁌱􀯔􁚆􀕿􀓥􁴳􀙾􀜈􀗭􀒅􀖕􀸎 ReetrantLock 􁌱􀯔􁚆􁚆􁖌􀳮􀬉
􀮾􀌶
12􀌵ReentrantLock 􀸎􀦇􀖜􀨫􁈿􀝢􁯿􀙁􀯔􁌱?
ReentrantLock 􀙖􁮱􁛔􀨧􀔎􀔧􀝶􀾍􀢏 Sync(Sync 􀷬􀨫􁈿􀔧 AQS􀒅 􀝈􀨫􁈿􀔧
AOS􀒅􁘒 AOS 􀵉􀗀􀔧􀓞􁐿􀔰􀷕􁲁􀳮􀹍􁌱􀷜􀭗)􀒅􀙌􀨫􀩪􀸎 􀛒􁲁􁌱􀷸􀗲􁭗􁬦
CAS 􁓒􁀩􀒅􀩙􁕚􁑕􀩒􁨝􀶱􀚩􀓞􀓻􀝌􀝻􁱾􁤒􀓾􀒅􀾯􀽺􁞴 􀝐􁲁􁌱􀷸􀗲􀒅􁍡􀓥
􀭮􀚹􁖌􀲷􁌱􁮎􀓻􁕚􁑕 ID 􀞾􀭮􀚹􁧗􀿢􁌱􁕚􁑕 ID 􀸎􀞈 􀓞􀻏􀒅􀓞􀻏􀩪􀝢􁯿􀙁
􀔧􀌶
13􀌵􁴻􀔧 ReetrantLock􀒅􀖦􁬮􀴳􁥶􁬦 JUC 􀓾􁌱􀟺􀔶􀬚􀝎􀫡􀙍?
􁭗􀬉􀲅􁧔􁌱􀬚􀝎􀛱(JUC)􀔞􀩪􀸎 java.util.concurrent 􀝊􀙌􀧼􀛱􀒅􁵞􀓾􀔧 Java
􀬚􀝎􁌱􀝱􁐿􀤚􁏐􀫡􀙍􁔄􀒅􀙍􀖛􀔆􁥝􀛱􀳡􀙾􀓻􀷜􁶎:
• 􀵉􀗀􀔧 CountDownLatch􀌵CyclicBarrier􀌵Semaphore􁒵􀒅􀾲
Synchronized 􀹅􀛒􁹛􁕆􀒅􀝢􀕦􀨫􁈿􀹅􀛒􀓿􀩄􀥚􁕚􁑕􀶙􀖢􁌱􀝶􀾍􁕮􀺅􀌶
• 􀵉􀗀􀔧 ConcurrentHashMap􀌵􀹍􀬧􁌱 ConcunrrentSkipListMap􀒅􀱲􁘏􁭗
􁬦􁔄􀖒􀮳􁆙􀹢􀚫􀨫􁈿􁕚􁑕􀨞􀙂􁌱􀛖􀮾􀷄􁕟 CopyOnWriteArrayList 􁒵􀝱􁐿􁕚
􁑕􀨞􀙂􁌱􀨻􀢏􀌶
• 􀵉􀗀􀔧 ArrayBlockingQueue􀌵 SynchorousQueue 􀱲􁰒􀩒􁇙􀨧􀣋􀸧􁌱
PriorityBlockingQueue 􁒵􀒅􀝱􁐿􀬚􀝎􁴚􀚜􀨫􁈿􀌶
• 􀭩􀥟􁌱 Executor 􀻛􀺝􀒅􀝢􀕦􀚠􀭌􀝱􁐿􀓧􀝶􁔄􀣳􁌱􁕚􁑕􀿰􀒅􁧣􀬶􀕱􀛓􁬩􁤈
􁒵􀌶
14􀌵􁧗􁧨􁧨 ReadWriteLock 􀞾 StampedLock􀌶
􁡱􁆐 ReentrantLock 􀞾 Synchronized 􁓌􀜔􀨫􁊠􀒅􀖕􀸎􁤈􀔅􀓤􀹍􀓞􀨧􀩴􁴴
􀯔􀒅􁥝􀔍􀓧􀜛􀒅􁥝􀔍􁇿􀜛􀌶􀨫􁴬􀬫􁊠􀣋􀸧􀓾􀒅􀹍􀷸􀗲􀓧􁵱􁥝􀥟􁰁 􁒋􀔩􁌱􀙟􀶙􀖢􀒅􁘒􀸎􀕦􀬚􀝎􁧛􀝐􀔅􀔆􀒅􀔅􀔧􁬰􀓞􀾍􀕽􀛸􀬚􀝎􀶙􀖢􁌱􁔉 􀬶􀒅Java 􀵉
􀗀􀔧􁧛􀙟􁲁􀌶􁧛􀙟􁲁􀤚􀔭􁌱􀜻􁉘􀸎􀥚􀓻􁧛􀶙􀖢􀓧􁵱􁥝􀔰􀷕􀒅􀦇􀺎􁧛􁲁􁦶􀢶
􁲁􀨧􀷸􀒅􀙟􁲁􀸎􁤩􀺤􀓻􁕚􁑕􀳮􀹍􀒅􁧛􁲁􀩙􀷫􁀩􁞴􀮑􀒅􁘒􀝝􀦅􁒵􀮇􀩒􀷜􀶙􀖢
􁕮􀹳􀒅􁬯􀻏􀩪􀝢􀕦􁛔􀛖􀗛􁦤􀓧􀕿􁧛􀝐􀚩􀹍􀔩􁦓􁌱􀷄􀴝􀌶
ReadWriteLock 􀕤􁤒􀔧􀓞􀩒􁲁􀒅􀓥􁶎􀸎􀓞􀓻􀤚􀔭􁧛􀙟􁲁􀨫􁈿􁌱􀷄􀴝􁕮 􀺅􀒅
􀭮􀷄􀴝􁰁􁫾􀥟􀒅􀬚􀝎􁧛􀥚􀌵􀬚􀝎􀙟􀩝􁌱􀷸􀗲􀒅􁚆􀥜􀾲􁕍􀝶􀾍􁇇􀹜􀚈 􀸔􀚊􀕽
􀛠:
􁧛􀙟􁲁􁍡􁩸􀹶􀾲 Synchronized 􁌱􁔉􀬶􀖒􀔒􁕡􀓞􀔶􀒅􀖕􀣁􀨫􁴬􀬫􁊠 􀓾􀒅􀙌
􁤒􁈿􀔞􀬚􀓧􀩱􀦇􀕈􀰺􀒅􀔆􁥝􁬮􀸎􀢩􀔅􁍘􀩒􀾲􁫾􀥟􁌱􀭏􁲀􀌶􀲅􀕦􀒅JDK 􀣁􀝸
􀹗􀭚􀙁􀔧 StampedLock􀒅􀣁􀵉􀗀􁔄􀖒􁧛􀙟􁲁􁌱􀝶􀷸􀒅􁬮􀶪􀳮􀕽􀛸􁧛􀽜􀭗􀌶
􀕽􀛸􁧛􀤚􀔭􀘃􁦡􀒅􀥟􀥚􀷄􀰘􀙭􀓥􁧛􀶙􀖢􀬚􀓧􀕿􀞾􀙟 􀶙􀖢􀙫􁑱􀒅􀙌􁭦􁬋􀸎􀘶
􁦶􁍳􀗥􀶯􀒅􁆐􀝸􁭗􁬦 validate 􀷜􁀩􁏟􁦊􀸎􀞈􁬰􀙁􀔧􀙟􀽜􀭗􀒅􀦇􀺎􁀌􀹍􁬰
􀙁􀒅􀩪􀱮􀛑􁭿􀘹􀔧􀭏􁲀;􀦇􀺎􁬰􀙁􀒅􀚞􀩤􁦶􁞴􀝐􁧛􁲁􀌶
15􀌵􀦇􀖜􁦏 Java 􁌱􁕚􁑕􀮂􀾌􀝶􀾍?􀖦􀔧􁥴􁬦􀟺􀔶􀝶􀾍􀢏?􁧗􀚓􀚦 􀕕􁕨􀓥􀌶
JUC 􀓾􁌱􀝶􀾍􀢏􀓣􀓻􀔆􁥝􁌱􀱮􀞧:CountDownLatch􀌵CyclicBarrier 􀞾
Semaphore􀒅􁭗􁬦􀨙􀕪􀝢􀕦􀷜􀗎􀣈􀨫􁈿􀮉􀥚􁕚􁑕􀔏􁳵􀜐􀖢􁌱􀛑􁚆􀌶
CountDownLatch 􀝞􀗯􁦇􀷄􀒅􊧋􁦜􀓞􀓻􀱲􀥚􀓻􁕚􁑕􁒵􀮇􀺤􀔶􀶙􀖢􀨠􀱮􀌶􁍡
􀙾􀓻􀣋􀸧:
• 􁪒􀾍􀾲􁩦􀒅􁤮􀚣􁵱􁥝􁒵􀚩􀲅􀹍􁌱􁬩􀛖􀞧(“􀙌􀕜􁕚􁑕”)􁮷􁪒􀚩􁕣􁅩 (􁬡􀚩􁍓
􀺽)􀒅􀲍􁚆􀝄􁓒􀴭􀝷􀞾􁶹􀥹􀌶
• 􀽜􀳙􀬚􀝎􀒅􀱯􁵱􁥝􀞐􀛖 100 􀓻􁕚􁑕􀝄􀝶􀷸􁦢􁳯􀺤􀓞􀓻􀣈􀣎􀒅􀱯􀫶􀹕􀨙 􀕪
􁚆􀝶􀷸􀬚􀝎􀒅􁘒􀓧􀸎􀓞􀓻􀓞􀓻􁌱􀝄􀲗􁤈􀌶
􁊠􁀩:CountDownLatch 􀺅􁭜􀷜􁀩􀳰􀸁􁦇􀷄􀷄􁰁􀒅􁤩􁒵􀮇􁕚􁑕􁧣􁊠
countDown 􀩙􁦇􀷄􀢏􀙺 1􀒅􁒵􀮇􁕚􁑕􀖵􁊠 await 􁬰􁤈􁕚􁑕􁒵􀮇􀌶􀓞 􀓻􁓌􀜔
􁌱􀖺􀧼:
CyclicBarrier 􀝞􀮗􁈾􀺼􀻄􀒅􀨙􀨫􁈿􁦏􀓞􁕟􁕚􁑕􁒵􀮇􁛗􀺤􀓻􁇫􀮾􀔏􀝸􀙚􀙂􁮱
􀝶􀷸􀲗􁤈􀒅􁘒􀓬􀭮􀲅􀹍􁒵􀮇􁕚􁑕􁤩􁯽􀶱􀝸􀒅CyclicBarrier 􀝢􀕦􁤩 􁯿􀥔􀖵
􁊠􀌶CyclicBarrier 􁌱􀙎􀣳􀬫􁊠􀣋􀸧􀸎􁊠􀹶􁒵􀮇􀬚􀝎􁕚􁑕􁕮􀹳􀌶CyclicBarrier
􁌱􀔆􁥝􀷜􁀩􀸎 await()􀒅await() 􀾯􁤩􁧣􁊠􀓞􀽺􀒅􁦇􀷄􀗎 􀕿􀙺􀩝 1􀒅􀬚􁴥􀤲􀖘
􀭮􀚹􁕚􁑕􀌶􀭮􁦇􀷄􀙺􁛗 0 􀷸􀒅􁴥􀤲􁥴􁴻􀒅􀲅􀹍􀣁 􀾌 CyclicBarrier 􀓤􁶎􁴥􀤲
􁌱􁕚􁑕􀭏􀦤􁬩􁤈􀌶
􀣁􁬯􀔏􀝸􀒅􀦇􀺎􀙚􀽺􁧣􁊠 await()􀒅􁦇􀷄􀩪􀝈􀕿􀝒􀱮 N-1􀒅􀷛􀓞􁫪􁯿􀷛􀭏
􀦤􀒅􁬯􀗎􀸎 Cyclic 􁌱􀞌􀔎􀲅􀣁􀌶CyclicBarrier.await() 􀬃􀹍􁬬􀢧􊧊􀒅􁊠􀹶􁤒
􁐏􀭮􀚹􁕚􁑕􀸎􁒫􀙾􀓻􀚩􁬡􁬯􀓻 Barrier 􁌱􁕚􁑕􀌶
􀔈􀖺􁧔􀸁􀦇􀓥:
Semaphore􀒅Java 􁇇􀹜􁌱􀗞􀝩􁰁􀨫􁈿􀒅􁊠􀔭􀴴􀚫􀝶􀷸􁦢􁳯􁌱􁕚􁑕􀓻􀷄􀒅􀹶
􁬡􀚩􁴴􀚫􁭗􁊠􁩒􁃠􁦢􁳯􁌱􁍓􁌱􀒅􀙌􀜻􁉘􀸎􁭗􁬦 acquire() 􁞴􀝐􀓞􀓻􁦜􀝢􀒅􀦇
􀺎􁀌􀹍􀩪􁒵􀮇􀒅􁘒 release() 􁯽􀶱􀓞􀓻􁦜􀝢􀌶
􀦇􀺎 Semaphore 􁌱􀷄􊧊􁤩􀚡􀦤􀛸􀔅1􀒅􁮎􀔍􀓞􀓻􁕚􁑕􀩪􀝢􀕦􁭗􁬦 acquire
􁬰􀙁􀔰􀷕􁇫􀮾􀒅􀹜􁨶􀓤􀞾􀔰􀷕􁲁􀸎􁶋􀬉􁍘􀖒􁌱􀌶􀖕􀸎􀜄􀚦􀔞􁶋􀬉􀸁􀸔􀒅􀾲
􀦇􀔰􀷕􁲁􀸎􀹍􀳮􀹍􁘏􁌱􀒅􁘒􀩒􀔭 Semaphore 􁬯􁐿􁦇􀷄􀢏􁕮􀺅􀒅􁡱􁆐􀹍􁔄
􀖒􀛑􁚆􀒅􀖕􀙌􀨫􀓧􀨂􀣁􁍥􀾋􀰺􀔎􁌱􀳮􀹍􁘏􀒅􁴻􁶋􀱯􀕪􁬰􁤈􀲘􀪀􀛱􁤰􀌶
16􀌵CyclicBarrier 􀞾 CountDownLatch 􁍡􁩸􀹶􀮉􁍘􀖒􀒅􁧗􀩒􀾲 􀓥􀞫?
􀨙􀕪􁌱􁤈􀔅􀹍􀓞􀨧􁍘􀖒􀬶􀒅􀜄􀚦􀔆􁥝􀣁􀔭:
• CountDownLatch 􀸎􀓧􀝢􀕦􁯿􁗝􁌱􀒅􀲅􀕦􀷫􁀩􁯿􁊠􀒅CyclicBarrier 􁀌􀹍􁬯
􁐿􁴴􀚫􀒅􀝢􀕦􁯿􁊠􀌶
• CountDownLatch 􁌱􀤚􀹜􀶙􀖢􁕟􀝳􀸎 countDown/await􀒅􁧣􁊠 await 􁌱􁕚
􁑕􁴥􀤲􁒵􀮇 countDown 􁪃􀥜􁌱􀽺􀷄􀒅􀓧􁓕􀖦􀸎􀣁􀓞􀓻􁕚􁑕􁬮􀸎􀥚􀓻􁕚􁑕
􁯾 countDown􀒅􀝝􁥝􀽺􀷄􁪃􀥜􀜨􀝢􀌶 CyclicBarrier 􁌱􀤚􀹜􀶙􀖢􁕟􀝳􀩪􀸎
await􀒅􀭮􀲅􀹍􁌱􀕾􀖎􁮷􁧣􁊠􀔧 await􀒅􀲍􀕿􁖀􁖅􁬰􁤈􀕱􀛓􀒅􀬚􁛔􀛖􁬰􁤈􁯿
􁗝􀌶
CountDownLatch 􁍓􁌱􀸎􁦏􀓞􀓻􁕚􁑕􁒵􀮇􀙌􀕜 N 􀓻􁕚􁑕􁬡􀚩􀺤􀓻􀹵􀕯􀝸􀒅
􁛔􀫩􀙚􀝄􀘉􀺤􀓻􀔪(􁭗􁬦 CyclicBarrier 􁌱􁒫􀔫􀓻􀺅􁭜􀷜􁀩 public
CyclicBarrier(int parties, Runnable barrierAction)􀒅􀣁􀷛􁕚􁑕􁯾􀘉􀔪􀝢􀕦􁬡
􀚩􀝶􀻏􁌱􀶴􀺎)􀌶􁘒 CyclicBarrier 􁌱􁍓􁌱􀸎􁦏 N 􀥚 􁕚􁑕􀔰􁍘􁒵􀮇􁍗􀚩􀲅􀹍
􁌱􁮷􁬡􀚩􀺤􀓻􁇫􀮾􀒅􁆐􀝸􁬯 N 􀓻􁕚􁑕􀙚􁖀􁖅􀲗􁤈􀝱􁛔􀝸􁖅(􁭗􁬦
CountDownLatch 􀣁􀺤􀔶􀣋􀝳􀔞􁚆􀨠􀱮􁔄􀖒􁌱􀶴􀺎)􀌶
17􀌵Java 􀓾􁌱􁕚􁑕􀿰􀸎􀦇􀖜􀨫􁈿􁌱?
• 􀣁 Java 􀓾􀒅􀲅􁧲􁌱􁕚􁑕􀿰􀓾􁌱“􁕚􁑕”􀒅􀙌􀨫􀸎􁤩􀳁􁨝􀔅􀔧􀓞􀓻􁶉􀮾 􀙖􁮱
􁔄 Worker􀒅􀨙􀤚􀔭 AQS 􀨫􁈿􀒅􀨂􀶱􀣁􁕚􁑕􀿰􁌱
HashSet workers 􀱮􀞧􀝒􁰁􀓾;
• 􁘒􁵱􁥝􀲗􁤈􁌱􀕱􀛓􀚞􀨂􀶱􀣁􀱮􀞧􀝒􁰁 workQueue(BlockingQueue
workQueue)􀓾􀌶
􁬯􀻏􀒅􀷆􀓻􁕚􁑕􀿰􀨫􁈿􁌱􀤚􀹜􀯏􀰮􀩪􀸎:􀕗 workQueue 􀓾􀓧􀷙􀝐􀚊 􁵱􁥝􀲗
􁤈􁌱􀕱􀛓􀒅􀶱􀣁 Workers 􀓾􁬰􁤈􀥒􁉘􀌶
18􀌵􀚠􀭌􁕚􁑕􀿰􁌱􀙾􀓻􀻐􀮞􀺅􁭜􀝇􀷄?
Java 􀓾􁌱􁕚􁑕􀿰􁌱􀚠􀭌􀙌􀨫􁶋􀬉􁅎􁁚􀒅􀱯􀕪􀝢􀕦􁭗􁬦􁯈􁗝􀓧􀝶􁌱􀝇 􀷄􀒅
􀚠􀭌􀚊􁤈􀔅􀓧􀝶􁌱􁕚􁑕􀿰􀒅􁬯􀙾􀓻􀝇􀷄􀛱􀳡:
• corePoolSize:􁕚􁑕􀿰􁌱􀻐􀮞􁕚􁑕􀷄􀌶
• maximumPoolSize:􁕚􁑕􀿰􊧋􁦜􁌱􀹋􀥟􁕚􁑕􀷄􀌶
• keepAliveTime:􁩻􁬦􀻐􀮞􁕚􁑕􀷄􀷸􁳳􁗝􁕚􁑕􁌱􀨂􁁚􀷸􁳵􀌶
• workQueue:􀕱􀛓􀲗􁤈􀚹􀗛􀨂􀕱􀛓􁌱􁴚􀚜􀒅􀗛􀨂􁊧 execute 􀷜􁀩􀵉􀔻􁌱
Runnable 􀕱􀛓 􀌶
19􀌵􁕚􁑕􀿰􀓾􁌱􁕚􁑕􀸎􀯆􀔍􀚠􀭌􁌱?􀸎􀓞􀭏􀦤􀩪􁵋􁍳􁕚􁑕􀿰􁌱􀞐􀛖 􀚠􀭌􀦅
􁌱􀞀?
􀸔􁆐􀓧􀸎􁌱􀌶􁕚􁑕􀿰􁼕􁦊􀚡􀦤􀛸􀝸􀓧􀞐􀛖 Worker􀒅􁒵􀮇􀹍􁧗􀿢􀷸􀲍􀞐
􀛖􀌶
􀾯􀭮􀱯􀕪􁧣􁊠 execute() 􀷜􁀩􁂲􀛒􀓞􀓻􀕱􀛓􀷸􀒅􁕚􁑕􀿰􀕿􀘉􀦇􀓥􀚣 􀷙:
• 􀦇􀺎􀾋􀣁􁬩􁤈􁌱􁕚􁑕􀷄􁰁􀩜􀔭 corePoolSize􀒅􁮎􀔍􁸘􀓤􀚠􀭌􁕚􁑕􁬩􁤈􁬯
􀓻􀕱􀛓;
• 􀦇􀺎􀾋􀣁􁬩􁤈􁌱􁕚􁑕􀷄􁰁􀥟􀔭􀱲􁒵􀔭 corePoolSize􀒅􁮎􀔍􀩙􁬯􀓻􀕱􀛓􀶱
􀙁􁴚􀚜;
• 􀦇􀺎􁬯􀷸􀗲􁴚􀚜􁃿􀔧􀒅􁘒􀓬􀾋􀣁􁬩􁤈􁌱􁕚􁑕􀷄􁰁􀩜􀔭
maximumPoolSize􀒅􁮎􀔍􁬮􀸎􁥝􀚠􀭌􁶋􀻐􀮞􁕚􁑕􁒈􀚰􁬩􁤈􁬯􀓻􀕱􀛓;
• 􀦇􀺎􁴚􀚜􁃿􀔧􀒅􁘒􀓬􀾋􀣁􁬩􁤈􁌱􁕚􁑕􀷄􁰁􀥟􀔭􀱲􁒵􀔭
maximumPoolSize􀒅􁮎􀔍􁕚􁑕􀿰􀕿􀲲􀚊􀭑􀬉 RejectExecutionException􀌶
􀭮􀓞􀓻􁕚􁑕􀨠􀱮􀕱􀛓􀷸􀒅􀨙􀕿􀕗􁴚􀚜􀓾􀝐􀓥􀓞􀓻􀕱􀛓􀹶􀲗􁤈􀌶 􀭮􀓞􀓻􁕚􁑕
􀷫􀔪􀝢􀘉􀒅􁩻􁬦􀓞􀨧􁌱􀷸􁳵(keepAliveTime)􀷸􀒅􁕚􁑕􀿰􀕿􀚣􀷙􀌶
􀦇􀺎􀭮􀚹􁬩􁤈􁌱􁕚􁑕􀷄􀥟􀔭 corePoolSize􀒅􁮎􀔍􁬯􀓻􁕚􁑕􀩪􁤩􀘊􀴧􀌶􀲅􀕦
􁕚􁑕􀿰􁌱􀲅􀹍􀕱􀛓􀨠􀱮􀝸􀒅􀨙􀹋􁕣􀕿􀶭􁖽􀚩 corePoolSize 􁌱􀥟􀩜􀌶
20􀌵􀷬􁆐􀵉􀚩􀝢􀕦􁭗􁬦􁯈􁗝􀓧􀝶􀝇􀷄􀚠􀭌􀚊􀓧􀝶􁌱􁕚􁑕􀿰􀒅􁮎􀔍 Java 􀓾
􁼕􁦊􀨫􁈿􀦅􁌱􁕚􁑕􀿰􀝈􀹍􀟺􀔶􀞫?􁧗􀾲􁫾􀨙􀕪􁌱􀭑􀝶􀌶
1. SingleThreadExecutor 􁕚􁑕􀿰
􁬯􀓻􁕚􁑕􀿰􀝝􀹍􀓞􀓻􀻐􀮞􁕚􁑕􀣁􀫡􀖢􀒅􀔞􀩪􀸎􁍘􀭮􀔭􀜔􁕚􁑕􀔀􁤈􀲗􁤈􀲅 􀹍
􀕱􀛓􀌶􀦇􀺎􁬯􀓻􀠔􀓞􁌱􁕚􁑕􀢩􀔅􀭑􀬉􁕮􀹳􀒅􁮎􀔍􀕿􀹍􀓞􀓻􀷛􁌱􁕚􁑕􀹶 􀹊􀕤
􀨙􀌶􀾌􁕚􁑕􀿰􀗛􁦤􀲅􀹍􀕱􀛓􁌱􀲗􁤈􁶲􀬧􀳲􁆙􀕱􀛓􁌱􀵉􀔻􁶲􀬧􀲗􁤈􀌶
• corePoolSize:1􀒅􀝝􀹍􀓞􀓻􀻐􀮞􁕚􁑕􀣁􀫡􀖢􀌶
• maximumPoolSize: 1􀌶
• keepAliveTime: 0L􀌶
• workQueue:new LinkedBlockingQueue<Runnable>() 􀒅􀙌􁖨􀙫􁴚􀚜
􀸎􀷫􁊴􁌱􀌶
2. FixedThreadPool 􁕚􁑕􀿰
FixedThreadPool 􀸎􀢴􀨧􀥟􀩜􁌱􁕚􁑕􀿰􀒅􀝝􀹍􀻐􀮞􁕚􁑕􀌶􀾯􀽺􀵉􀔻􀓞􀓻􀕱
􀛓􀩪􀚠􀭌􀓞􀓻􁕚􁑕􀒅􁍗􀚩􁕚􁑕􁬡􀚩􁕚􁑕􀿰􁌱􀹋􀥟􀥟􀩜􀌶􁕚􁑕􀿰􁌱􀥟􀩜􀓞􀷮
􁬡􀚩􀹋􀥟􊧊􀩪􀕿􀗛􀳮􀓧􀝒􀒅􀦇􀺎􀺤􀓻􁕚􁑕􀢩􀔅􀲗􁤈􀭑􀬉􁘒􁕮􀹳􀒅􁮎􀔍􁕚􁑕
􀿰􀕿􁤑􊧌􀓞􀓻􀷛􁕚􁑕􀌶
FixedThreadPool 􀥚􀷄􁰒􀩒􀓞􀔶􀮉􁑞􀨧􀮉􀢴􀨧􁌱􀾋􁥢􀬚􀝎􁕚􁑕􀒅􀥚􁊠􀔭􀹐
􀛓􀢏􀌶
• corePoolSize: nThreads
• maximumPoolSize: nThreads
• keepAliveTime: 0L
• workQueue:new LinkedBlockingQueue<Runnable>() 􀒅􀙌􁖨􀙫􁴚􀚜
􀸎􀷫􁊴􁌱􀌶
3. CachedThreadPool 􁕚􁑕􀿰
CachedThreadPool 􀸎􀷫􁊴􁕚􁑕􀿰􀒅􀦇􀺎􁕚􁑕􀿰􁌱􀥟􀩜􁩻􁬦􀔧􀥒􁉘􀕱􀛓􀲅
􁵱􁥝􁌱􁕚􁑕􀒅􁮎􀔍􀩪􀕿􀢧􀶭􁮱􀚓􁑮􁳳(60􁑁􀓧􀲗􁤈􀕱􀛓)􁕚􁑕􀒅􀭮 􀕱􀛓􀷄􀥀
􀛒􀷸􀒅􀾌􁕚􁑕􀿰􀝈􀝢􀕦􀸬􁚆􁌱􁂲􀛒􀷛􁕚􁑕􀹶􀥒􁉘􀕱􀛓􀌶􁕚􁑕􀿰􀥟􀩜􀨠􀙂􀗁
􁩢􀔭􀶙􀖢􁔮􁕹(􀱲􁘏􁧔 JVM)􁚆􀥜􀚠􀭌􁌱􀹋􀥟􁕚􁑕􀥟􀩜􀌶SynchronousQueue
􀸎􀓞􀓻􀸎􁖨􀙫􀜄􀔅 1 􁌱􁴥􀤲􁴚􀚜􀌶􁖨􀨂􀣳􀿰􀧼􁭗􀬉􁊠􀔭􀲗􁤈􀓞􀔶􁊞􀨂􀹗􀮉
􁎨􁌱􀭑􀾍􀣳􀕱􀛓􀒅􀢩􀾌􀣁􀓞􀔶􁶎􀝻􁬳􀴳􁌱 daemon 􀣳 SERVER 􀓾􁊠􀮑􀓧
􀥚􀌶􀖕􀩒􀔭􁊞􀨂􀹗􁎨􁌱􀭑􀾍􀕱􀛓􀒅􀨙􀸎 Executor 􁌱􁸒􁭌􀌶
• corePoolSize: 0
• maximumPoolSize: Integer.MAX_VALUE
• keepAliveTime: 60L
• workQueue:new SynchronousQueue<Runnable>() 􀒅􀓞􀓻􀸎􁖨􀙫􀜄􀔅
1 􁌱􁴥􀤲􁴚􀚜􀌶
4. ScheduledThreadPool 􁕚􁑕􀿰
ScheduledThreadPool :􀻐􀮞􁕚􁑕􀿰􀢴􀨧􀒅􀥟􀩜􀷫􁴴􁌱􁕚􁑕􀿰􀌶􀾌􁕚􁑕􀿰
􀶪􀳮􀨧􀷸􀕦􀝊􀞮􀹗􀯔􀲗􁤈􀕱􀛓􁌱􁵱􀿢􀌶􀚠􀭌􀓞􀓻􀞮􀹗􀯔􀲗􁤈􀕱􀛓􁌱􁕚􁑕
􀿰􀌶􀦇􀺎􁳳􁗝􀒅􁶋􀻐􀮞􁕚􁑕􀿰􀕿􀣁 DEFAULT_KEEPALIVEMILLIS 􀷸􁳵􀙖
􀢧􀶭􀌶
• corePoolSize: corePoolSize
• maximumPoolSize: Integer.MAX_VALUE
• keepAliveTime: DEFAULT_KEEPALIVE_MILLIS
• workQueue:new DelayedWorkQueue()
21􀌵􀦇􀖜􀣁 Java 􁕚􁑕􀿰􀓾􀵉􀔻􁕚􁑕?
􁕚􁑕􀿰􀹋􀬉􁊠􁌱􀵉􀔻􀕱􀛓􁌱􀷜􁀩􀹍􀓷􁐿:
1. execute(): ExecutorService.execute 􀷜􁀩􀴳􀶭􀓞􀓻􀖺􀒅􀨙􁊠􀹶􀲗􁤈􀓞􀓻
􀕱􀛓:
2. submit(): ExecutorService.submit() 􀷜􁀩􁬬􀢧􁌱􀸎 Future 􀩒􁨝􀌶􀝢􀕦􁊠
isDone() 􀹶􀺱􁧃 Future 􀸎􀞈􀫪􁕪􀨠􀱮􀒅􀭮􀕱􀛓􀨠􀱮􀷸􀒅 􀨙􀙍􀹍􀓞􀓻􁕮􀺎􀒅
􀝢􀕦􁧣􁊠 get() 􀹶􁞴􀝐􁕮􀺎􀌶􀔞􀝢􀕦􀓧􁊠 isDone() 􁬰􁤈􀼄􀺱􀩪􁍗􀴳􁧣􁊠
get()􀒅􀣁􁬯􁐿􀰘􀙭􀓥􀒅get() 􀩙􁴥􀤲􀒅􁍗􁛗􁕮􀺎􀙵􀥓􀩪􁖃􀌶
22􀌵􀕋􀔍􀸎 Java 􁌱􀙖􀨂􀽜􀣳􀒅Java 􀓾􀝱􀓻􁕚􁑕􀸎􀯆􀔍􀮂􀾌􁍡􀚩 􀩒􀷜􁌱
􀝒􁰁􁌱?
Java 􁌱􀙖􀨂􀽜􀣳􀨧􀔎􀔧􁑕􀬧􀓾􀝱􀓻􀝒􁰁􁌱􁦢􁳯􁥢􀚞􀒅􀜨􀣁􁡦􀳙􀹢􀓾􀩙 􀝒
􁰁􀨂􀘙􀚩􀙖􀨂􀞾􀕗􀙖􀨂􀓾􀝐􀚊􁬯􀻏􁌱􀬬􀩶􁕡􁜓􀌶􀾌􀥒􁌱􀝒􁰁􀛱􀳡􀨫􀖺􀨁
􀾧􀌵􁶉􀮾􀨁􀾧􀞾􀺅􀱮􀷄􁕟􀩒􁨝􁌱􀘲􁔰􀒅􀖕􀸎􀓧􀛱􀳡􀩴􁮱􀝒􁰁􀞾􀷜􁀩􀝇􀷄􀒅
􀢩􀔅􁬯􀔶􀸎􁕚􁑕􁐺􀹍􁌱􀒅􀓧􀕿􁤩􀙈􀕁􀒅􀲅􀕦􀓧􀨂􀣁􁒋􀔩􁳯􁷌􀌶
Java 􀓾􀝱􀓻􁕚􁑕􀸎􀯆􀔍􀮂􀾌􁍡􀚩􀩒􀷜􁌱􀝒􁰁􁌱􀞫?Java 􀓾􀨧􀔎􀔧􀔆􀙖 􀨂􀓨
􀫡􀖢􀙖􀨂􁌱􀼷􀮷:
􀲅􀹍􁌱􀝒􁰁􁮷􀨂􀘙􀣁􀔆􀙖􀨂􀒅􀾯􀹵􁕚􁑕􁬮􀹍􁛔􀫩􁌱􀫡􀖢􀙖􀨂􀒅􀗛􀨂􀔧􁤩 􁧆
􁕚􁑕􀖵􁊠􀚩􁌱􀝒􁰁􁌱􀔆􀙖􀨂􀛅􀹜􀳩􁨬􀌶
􁕚􁑕􀩒􀝒􁰁􁌱􀲅􀹍􀶙􀖢(􁧛􀝐􀌵􁩙􊧊)􁮷􀮠􁶳􀣁􀫡􀖢􀙖􀨂􀓾􁬰􁤈􀒅􀓧􁚆􁍗􀴳
􁧛􀙟􀔆􀙖􀨂􁌱􀝒􁰁􀌶􀓧􀝶􁌱􁕚􁑕􀔏􁳵􀔞􀷫􁀩􁍗􀴳􁦢􁳯􀩒􀷜􀫡􀖢􀙖􀨂􁌱􀝒
􁰁􀒅􁕚􁑕􁳵􀝒􁰁􊧊􁌱􀖃􁭓􁵱􁥝􁭗􁬦􀔆􀙖􀨂􀌶
23􀌵􁧗􁧨􁧨 volatile 􀹍􀕋􀔍􁇙􁅩􀒅􀔅􀕋􀔍􀨙􁚆􀗛􁦤􀝒􁰁􀩒􀲅􀹍􁕚 􁑕􁌱􀝢􁥠
􀯔?
􀙉􁲫􀨁 volatile 􀸎 Java 􁡦􀳙􀹢􀵉􀗀􁌱􀹋􁫷􁰁􁕆􁌱􀝶􀾍􀹢􀚫􀌶􀭮􀓞􀓻 􀝒􁰁􁤩
􀨧􀔎􀱮 volatile 􀔏􀝸􀒅􀙍􀥓􀓷􁐿􁇙􀯔:
1. 􀗛􁦤􀾌􀝒􁰁􀩒􀲅􀹍􁕚􁑕􁌱􀝢􁥠􀯔􀌶􀭮􀓞􀹵􁕚􁑕􀗥􀶯􀔧􁬯􀓻􀝒􁰁􁌱􊧊􀒅􀷛
􊧊􀩒􀔭􀙌􀕜􁕚􁑕􀸎􀝢􀕦􁒈􀜨􀮑􁎣􁌱􀌶􁘒􀸦􁭗􀝒􁰁􀘉􀓧􀚩􁬯􀓞􁅩􀌶
2. 􁐬􀾊􀳰􀕥􁯿􀴭􀬧􀕽􀛸􀌶􀸦􁭗􀝒􁰁􀕐􀕐􁚆􀗛􁦤􀣁􁧆􀷜􁀩􀲗􁤈􁬦􁑕􀓾􀒅􀮑􀚩
􀾋􁏟􁕮􀺎􀒅􀖕􀸎􀓧􀗛􁦤􁑕􀬧􀕤􁎱􁌱􀲗􁤈􁶲􀬧􀌶
Java 􁌱􀙖􀨂􀽜􀣳􀨧􀔎􀔧 8 􁐿􀙖􀨂􁳵􀶙􀖢:
lock 􀞾 unlock
• 􀲩􀓞􀓻􀝒􁰁􀺽􁦩􀔅􀓞􀹵􁕚􁑕􁇿􀜛􁌱􁇫􀮾􀌶
• 􀲩􀓞􀓻􀥒􀔭􁲁􀨧􁇫􀮾􁌱􀝒􁰁􁯽􀶱􀚊􀹶􀒅􁯽􀶱􀔏􀝸􁌱􀝒􁰁􀲍􁚆􁤩􀙌􀕜􁕚􁑕
􁲁􀨧􀌶
read 􀞾 write
• 􀲩􀓞􀓻􀝒􁰁􊧊􀕗􀔆􀙖􀨂􀖃􁬌􀚩􁕚􁑕􁌱􀫡􀖢􀙖􀨂􀒅􀕦􀗎 load􀌶
• 􀲩 store 􀶙􀖢􀕗􀫡􀖢􀙖􀨂􀮑􀚩􁌱􀝒􁰁􁌱􊧊􀒅􀶱􀙁􀔆􀙖􀨂􁌱􀝒􁰁􀓾􀌶
load 􀞾 store
• 􀲩 read 􀶙􀖢􀕗􀔆􀙖􀨂􀮑􀚩􁌱􀝒􁰁􊧊􀶱􀙁􀫡􀖢􀙖􀨂􁌱􀝒􁰁􀛅􀹜􀓾􀌶 • 􀲩􀫡
􀖢􀙖􀨂􁌱􀝒􁰁􊧊􀖃􁭆􀚩􀔆􀙖􀨂􀒅􀕦􀗎 write􀌶
use 􀞾 assgin
• 􀲩􀫡􀖢􀙖􀨂􀝒􁰁􊧊􀖃􁭓􁕳􀲗􁤈􀭚􀶚􀌶
• 􀩙􀲗􁤈􀭚􀶚􊧊􀖃􁭓􁕳􀫡􀖢􀙖􀨂􀝒􁰁􊧊􀌶
volatile 􁌱􀨫􁈿􀤚􀔭􁬯 8 􁐿􀙖􀨂􁳵􀶙􀖢􀒅􀗛􁦤􀔧􀓞􀓻􁕚􁑕􀩒􀺤􀓻 volatile 􀝒
􁰁􁌱􀗥􀶯􀒅􀓞􀨧􀕿􁤩􀝚􀓞􀓻􁕚􁑕􁍡􁥠􀒅􀜨􀗛􁦤􀔧􀝢􁥠􀯔􀌶
24􀌵􀷬􁆐 volatile 􁚆􀥜􀗛􁦤􁕚􁑕􁳵􁌱􀝒􁰁􀝢􁥠􀯔􀒅􀸎􀓧􀸎􀩪􀰺􀞱 􁍳􀤚􀔭
volatile 􀝒􁰁􁌱􁬩􁓒􀩪􀸎􀬚􀝎􀨞􀙂􁌱?
􀸔􁆐􀓧􀸎􁌱􀌶􀤚􀔭 volatile 􀝒􁰁􁌱􁬩􁓒􀣁􀬚􀝎􀓥􀓧􀓞􀨧􀸎􀨞􀙂􁌱􀌶 volatile
􀝒􁰁􀣁􀝱􀓻􁕚􁑕􁌱􀫡􀖢􀙖􀨂􀒅􀓧􀨂􀣁􀓞􁛘􀯔􁳯􁷌(􀝱􀓻􁕚􁑕􁌱􀫡􀖢􀙖􀨂􀓾
volatile 􀝒􁰁􀒅􀾯􀽺􀖵􁊠􀚹􁮷􁥝􀚬􀷛􀚩􀔆􀙖􀨂)􀌶
􀖕􀸎 Java 􁯾􁶎􁌱􁬩􁓒􀬚􁶋􀜻􀧼􀶙􀖢􀒅􀩕􁛘 volatile 􀝒􁰁􁌱􁬩􁓒􀣁􀬚􀝎􀓥􀓞
􀻏􀸎􀓧􀨞􀙂􁌱􀌶
25􀌵􁧗􀩒􀾲􀓥 volatile 􀩒􀾲 Synchronized 􁌱􀭑􀝶􀌶
Synchronized 􀷬􁚆􀗛􁦤􀝢􁥠􀯔􀒅􀝈􁚆􀗛􁦤􀜻􀧼􀯔􀒅􁘒 volatile 􀝝􁚆􀗛􁦤􀝢
􁥠􀯔􀒅􀷫􁀩􀗛􁦤􀜻􀧼􀯔􀌶
ThreadLocal 􀞾 Synchonized 􁮷􁊠􀔭􁥴􀙬􀥚􁕚􁑕􀬚􀝎􁦢􁳯􀒅􁴠􀾊􀕱􀛓􀣁􀙈
􀕁􁩒􁃠􀓤􀔾􁊞􀙫􁑱􀌶􀖕􀸎 ThreadLocal 􀓨 Synchronized 􀹍􀹜􁨶􁌱􀜄􀚦􀌶
Synchronized 􁊠􀔭􀨫􁈿􀝶􀾍􀹢􀚫􀒅􀸎􀚥􁊠􁲁􁌱􀹢􀚫􀖵􀝒􁰁􀱲􀕤􁎱􀣘􀣁􀺤􀓞
􀷸􁧆􀝝􁚆􁤩􀓞􀓻􁕚􁑕􁦢􁳯􀒅􀸎􀓞􁐿 “􀕦􀷸􁳵􀴘􁑮􁳵” 􁌱􀷜􀭗􀌶
􁘒 ThreadLocal 􀔅􀾯􀓞􀓻􁕚􁑕􁮷􀵉􀗀􀔧􀝒􁰁􁌱􀛅􀹜􀒅􀖵􀮑􀾯􀓻􁕚􁑕􀣁􀺤􀓞
􀷸􁳵􁦢􁳯􀚩􁌱􀬚􀓧􀸎􀝶􀓞􀓻􀩒􁨝􀒅􀻑􁴻􀔧􀩒􀝒􁰁􁌱􀙈􀕁􀒅􀸎􀓞􁐿 “􀕦􁑮􁳵
􀴘􀷸􁳵” 􁌱􀷜􀭗􀌶
26􀌵􁧗􁧨􁧨 ThreadLocal 􀸎􀯆􀔍􁥴􀙬􀬚􀝎􀨞􀙂􁌱?
ThreadLocal 􁬯􀸎 Java 􀵉􀗀􁌱􀓞􁐿􀗛􀨂􁕚􁑕􁐺􀹍􀗞􀯳􁌱􀹢􀚫􀒅􀢩􀔅 􀙌􀣁
􀷆􀓻􁕚􁑕􁊞􀞸􀞮􀹗􀙖􀹍􀶴􀒅􀲅􀕦􀝢􀕦􀷜􀗎􀣈􀣁􀓞􀓻􁕚􁑕􀙉􁘶􁌱􀓧􀝶􀓱􀛓􀽜
􀣘􀔏􁳵􀖃􁭓􀗞􀯳􀒅􀾲􀦇􀔪􀛓 ID􀌵Cookie 􁒵􀓤􀓥􀷈􁍘􀙉􀗞􀯳􀌶
ThreadLocal 􀔅􀾯􀓞􀓻􁕚􁑕􁖌􀲷􀝒􁰁􁌱􀛅􀹜􀒅􀲩􀙈􀕁􀷄􀴝􁌱􀝢􁥠􁝜􀢱􁴴 􀚫
􀣁􀝶􀓞􀓻􁕚􁑕􀔏􀙖􀒅􀙌􀨫􁈿􀜻􁉘􀸎􀒅􀣁 ThreadLocal 􁔄􀓾􀹍􀓞􀓻 Map􀒅􁊠
􀔭􀨂􀘙􀾯􀓞􀓻􁕚􁑕􁌱􀝒􁰁􁌱􀛅􀹜􀌶
27􀌵􀮉􀥚􀕈􁮷􁧔􁥝􀱈􁊠 ThreadLocal􀒅􁧨􁧨􀖦􁌱􁉘􁥴􀒅􀖵􁊠
ThreadLocal 􁵱􁥝􁀳􀰺􀔶􀕋􀔍?
􀖵􁊠 ThreadLocal 􁥝􁀳􀰺 remove!
ThreadLocal 􁌱􀨫􁈿􀸎􀤚􀔭􀓞􀓻􀲅􁧲􁌱 ThreadLocalMap􀒅􀣁
ThreadLocalMap 􀓾􀒅􀨙􁌱 key 􀸎􀓞􀓻􀭧􀭚􁊠􀌶
􁭗􀬉􀭧􀭚􁊠􁮷􀕿􀞾􀭚􁊠􁴚􀚜􁯈􀝳􁂴􁉘􀹢􀚫􀖵􁊠􀒅􀖕􀸎 ThreadLocal 􀸎􀓻􀖺
􀥘􀒅􀨙􀬚􁀌􀹍􁬯􀔍􀘉􀌶
􁬯􀰺􀞱􁍳􀒅􀬳􀭒􁶱􁍓􁌱􀢧􀶭􀗁􁩢􀔭􀸔􀭗􀣈􁥶􀝎􀒅􀞈􀚞􀩪􁥝􁒵􀮇􁕚􁑕􁕮􀹳􀒅
􁬰􁘒􀢧􀶭􁍘􀬫 ThreadLocalMap!􁬯􀩪􀸎􀮉􀥚 OOM 􁌱􀹶􁃠􀒅􀲅 􀕦􁭗􀬉􁮷􀕿
􀭌􁦓􀒅􀬫􁊠􀓞􀨧􁥝􁛔􀫩􁨮􁨱 remove􀒅􀬚􀓬􀓧􁥝􀞾􁕚􁑕􀿰􁯈 􀝳􀒅􀢩􀔅
worker 􁕚􁑕􀮃􀮃􀸎􀓧􀕿􁭅􀚊􁌱􀌶
4.1􀌵Spring􁶎􁦶􀷆􁉘
1􀌵􀕋􀔍􀸎 Spring 􀻛􀺝?Spring 􀻛􀺝􀹍􀟺􀔶􀔆􁥝􀽜􀣘?
Spring 􀻛􀺝􀸎􀓞􀓻􀔅 Java 􀬫􁊠􁑕􀬧􁌱􀭏􀝎􀵉􀗀􀔧􁖓􀝳􀌵􀬠􁀬􁌱􀤚􁏐􀯔􀶪
􀳮􁌱 Java 􀬘􀝣􀌶 Spring 􀬆􀛗􀭏􀝎􁘏􁥴􀙬􀔧􀭏􀝎􀓾􀤚􁏐􀯔􁌱􁳯􁷌􀒅􀖵􀮑􀭏
􀝎􀕈􀞧􀝢􀕦􀓫􁀳􀔭􀬫􁊠􁑕􀬧􁌱􀭏􀝎􀌶
Spring 􀻛􀺝􀹜􁫝􀔽􀸎􀳲􁆙􁦡􁦇􀽜􀭗􁔜􀮞􀲑􁭜􀒅􁬯􀖵􀮑􀱯􀕪􀝢􀕦􀣁􀭏􀝎􁈾􀤹
􀓾􀨞􀮞􁌱􁵞􀱮 Spring 􀻛􀺝􀒅􀓧􀮠􀳅􀮞 Spring 􀸎􀦇􀖜􀣁􀝸􀝣􁬰􁤈􀫡􀖢􁌱􀌶
Spring 􀻛􀺝􁛗􀕔􀫪􁵞􀱮􀔧 20 􀥚􀓻􀽜􀣘􀌶􁬯􀔶􀽜􀣘􀔆􁥝􁤩􀚓􀦇􀓥􀢶􀲅􁐏􁌱
􀻐􀮞􀨻􀢏􀌵􀷄􀴝􁦢􁳯/􁵞􀱮,􀌵Web􀌵AOP(􁶎􀝻􀚔􁶎􁖫􁑕)􀌵􀫡􀙍􀌵􁁾􀯳􀞾􁁥
􁦶􀽜􀣘􀌶
2􀌵􀖵􁊠 Spring 􀻛􀺝􁚆􀬃􀹶􀟺􀔶􀦅􀥒?
􀓥􁶎􀚜􀔈􀔧􀓞􀔶􀖵􁊠 Spring 􀻛􀺝􀬃􀹶􁌱􀔆􁥝􀦅􀥒:
• Dependency Injection(DI) 􀷜􁀩􀖵􀮑􀺅􁭜􀢏􀞾 JavaBean properties 􀷈􀕯􀓾
􁌱􀗁􁩢􀙉􁔮􀓞􁍓􀔧􁆐􀌶
• 􀓨 EJB 􀨻􀢏􁍘􀾲􁫾􀒅IoC 􀨻􀢏􀹅􀛒􁩽􀝻􀔭􁫷􁰁􁕆􀌶􁬯􀻏􀓞􀹶 IoC 􀨻􀢏􀣁
􀹍􁴴􁌱􀙖􀨂􀞾 CPU 􁩒􁃠􁌱􀰘􀙭􀓥􁬰􁤈􀬫􁊠􁑕􀬧􁌱􀭏􀝎􀞾􀝎􀫲􀩪􀝒􀮑􀜈􀚓
􀹍􀚥􀌶
• Spring 􀬚􁀌􀹍􁳮􁳪􁭜􁫣􀒅Spring 􀚥􁊠􀔧􀫪􀹍􁌱􀲦􀹞􀾲􀦇 ORM 􀻛􀺝􀌵
logging 􀻛􀺝􀌵J2EE􀌵Q uartz􀞾JDK Timer􀒅􀕦􀝊􀙌􀕜􁥤􀢶􀲦􀹞􀌶
• Spring 􀻛􀺝􀸎􀳲􁆙􀽜􀣘􁌱􀭵􀭗􀹶􁕟􁕢􁌱􀌶􁊧􀛱􀞾􁔄􁌱􁖫􀝩􀩪􀝢􀕦􁍡􀚊􀙌
􀲅􀪂􁌱􀽜􀣘􀒅􀭏􀝎􁘏􀕐􀕐􁵱􁥝􁭌􁊠􀕜􀕪􁵱􁥝􁌱􀽜􀣘􀜨􀝢􀌶
􀢥􀌵􀭏􁃠􀻛􀺝􁶎􁦶􁷌􀓫􀻄
• 􁥝􁁥􁦶􀓞􁶱􁊠 Spring 􀭏􀝎􁌱􀬫􁊠􁑕􀬧􀜈􀚓􁓌􀜔􀒅􀢩􀔅􁁥􁦶􁍘􀙉􁌱􁈾􀤹􀕤
􁎱􁮷􀫪􁕪􀢡􀳡􀣁􀻛􀺝􀓾􀔧􀌶􀹅􀛒􁓌􀜔􁌱􀸎􀒅􀚥􁊠 JavaBean 􀭵􀭗􁌱 POJO
􁔄􀒅􀝢􀕦􀮉􀷜􀗎􁌱􀚥􁊠􀗁􁩢􁀳􀙁􀹶􀙟􀙁􁁥􁦶􀷄􀴝􀌶
• Spring 􁌱 Web 􀻛􀺝􀔽􀸎􀓞􀓻􁔜􀮞􁦡􁦇􁌱 Web MVC 􀻛􀺝􀒅􀔅􀭏􀝎􁘏􀕪􀣁
web 􀻛􀺝􁌱􁭌􀳠􀓤􀵉􀗀􀔧􀓞􀓻􁴻􀔧􀔆􁁞􀻛􀺝􀾲􀦇 Struts􀌵􁬦􀬶􁦡􁦇􁌱􀌵􀓧
􁁞􁤈 web 􀻛􀺝􁌱􀕦􀥘􁌱􀹍􀛎􁭌􁶱􀌶
• Spring 􀵉􀗀􀔧􀓞􀓻􀗎􀴠􁌱􀔪􀛓􁓕􁉘􀴳􀝗􀒅􁭇􁊠􀔭􀩜􀣳􁌱􀹜􀣈􀔪􁇔􀥒􁉘(􀾲
􀦇􀣁􀜔 DB 􁌱􁈾􀤹􀓥)􀞾􀥔􀹥􁌱􀙈􀝶􀔪􁇔􀥒􁉘(􀾲􀦇􀚥􁊠 JTA 􁌱􀥔􀹥 DB 􁈾
􀤹)􀌶
3􀌵􀕋􀔍􀸎􀴴􀚫􀝍􁫨(IOC)?􀕋􀔍􀸎􀗁􁩢􁀳􀙁?
􀴴􀚫􀝍􁫨􀸎􀬫􁊠􀔭􁫫􀕯􀫡􁑕􁶾􀤒􀓾􁌱􀒅􀣁􁬩􁤈􀷸􁤩􁤰􁯈􀢏􀩒􁨝􀹶􁕬􀨧􁘠􀝳
􀩒􁨝􁌱􀓞􁐿􁖫􁑕􀲦􀫣􀒅􀩒􁨝􀔏􁳵􁘠􀝳􀙉􁔮􀣁􁖫􁦲􀷸􁭗􀬉􀸎􀹚􁎣􁌱􀌶􀣁􀖃􁕹
􁌱􁖫􁑕􀷜􀭗􀓾􀒅􀓱􀛓􁭦􁬋􁌱􁁞􁑕􀸎􁊧􀬫􁊠􁑕􀬧􀓾􁌱􀷱􀫪􁤩􁦡􀨧􀦅􀙉􁘶􀙉􁔮
􁌱􀩒􁨝􀹶􀙬􀨧􁌱􀌶􀣁􀖵􁊠􀴴􀚫􀝍􁫨􁌱􀰘􀙭􀓥􀒅􀓱􀛓􁭦􁬋􁌱􁁞􁑕􀸎􁊧􀩒􁨝􀙉
􁔮􀢶􀹶􀙬􀨧􁌱􀒅􁧆􀩒􁨝􀙉􁔮􀢶􁊧􁤰􁯈􀢏􁨮􁨱􀨫􀖺􀛸􀒅􁬯􁐿􀨫􁈿􀷜􀭗􁬮􀝢􀕦
􀩙􀩒􁨝􀔏􁳵􁌱􀙉􁘶􀙉􁔮􁌱􀨧􀔎􀳁􁨝􀛸􀌶􁘒􁕬􀨧􁌱􁬦􁑕􀸎􁭗􁬦“􀗁􁩢􁀳􀙁”􀨫
􁈿􁌱􀌶
􀴴􀚫􀝍􁫨􀸎􀓞􁐿􀕦􁕳􀔨􀬫􁊠􁑕􀬧􀓾􁍓􀺽􁕟􀕯􀹅􀥚􀴴􀚫􀔅􁍓􁌱􁦡􁦇􁝜􀭗􀒅􀬚
􀣁􀱯􀕪􁌱􀨫􁴬􀫡􀖢􀓾􁩸􀚩􀔧􀹍􀶴􁌱􀖢􁊠􀌶
􀗁􁩢􁀳􀙁􀸎􀣁􁖫􁦲􁴤􀾧􀩢􀹚􁎣􀲅􁵱􁌱􀛑􁚆􀸎􀹶􁛔􀟺􀓻􁌱􁔄􁌱􀰘􀙭􀓥􀒅􀩙􀙌
􀕜􀩒􁨝􀲅􀗁􁩢􁌱􀛑􁚆􀩒􁨝􀨫􀖺􀛸􁌱􀽜􀭗􀌶􁬯􀩪􁵱􁥝􀓞􁐿􀹢􀚫􁊠􀹶􁄶􁁚􁍘􀬫
􁌱􁕟􀕯􀕦􀵉􀗀􁇙􀨧􁌱􀛑􁚆􀒅􀲅􀕦􀗁􁩢􁀳􀙁􀸎􀴴􀚫􀝍􁫨􁌱􀤚􁏐􀌶􀞈􀚞􀦇􀺎􀣁
􁕟􀕯􀓧􀝑􀻛􀺝􀴴􀚫􁌱􀰘􀙭􀓥􀒅􀻛􀺝􀝈􀯆􀔍􁎣􁭲􁥝􀚠􀭌􀟺􀓻􁕟􀕯?
􀣁 Java 􀓾􀗁􁆐􁀳􀙁􀹍􀕦􀓥􀓣􁐿􀨫􁈿􀷜􀭗:
1. 􀺅􁭜􀢏􁀳􀙁
2. Setter 􀷜􁀩􁀳􀙁
3. 􀴳􀝗􁀳􀙁
4􀌵􁧗􁥴􁯽􀓥 Spring 􀻛􀺝􀓾􁌱 IoC?
Spring 􀓾􁌱 org.springframework.beans 􀛱􀞾 org.springframework.context
􀛱
􀺅􀱮􀔧 Spring 􀻛􀺝 IoC 􀨻􀢏􁌱􀤚􁏐􀌶
BeanFactory 􀴳􀝗􀵉􀗀􀔧􀓞􀓻􀘶􁬰􁌱􁯈􁗝􀹢􀚫􀒅􀖵􀮑􀕱􀖜􁔄􀣳􁌱􀩒􁨝􁌱􁯈
􁗝􀱮􀔅􀝢􁚆􀌶 ApplicationContex 􀴳􀝗􀩒 BeanFactory(􀸎􀓞􀓻􀧼􀴳􀝗)􁬰􁤈
􀔧􀲘􀪀􀒅􀣁 BeanFactory 􁌱􀤚􁏐􀓤􁂲􀛒􀔧􀙌􀕜􀛑􁚆􀒅􀾲􀦇􀓨 Spring 􁌱
AOP 􀹅􀨻􀸃􁵞􀱮􀒅􀔞􀵉􀗀􀔧􀥒􁉘 message resource 􁌱􀹢􀚫(􁊠􀔭􀢵􁴬􀛸)􀌵
􀔪􀕯􀖃􀶎􀕦􀝊􀬫􁊠􀩶􁌱􁇙􀚦􁯈􁗝􀒅􀾲􀦇􁰒􀩒 Web 􀬫􁊠􁌱
WebApplicationContext􀌶
org.springframework.beans.factory.BeanFactory 􀸎 Spring IoC 􀨻􀢏􁌱􀙍􀖛
􀨫􁈿􀒅􁊠􀹶􀛱􁤰􀞾􁓕􁉘􀚹􁶎􀵉􀚩􁌱􀝱􁐿 bean􀌶BeanFactory 􀴳􀝗􀸎 Spring
IoC 􀨻􀢏􁌱􀻐􀮞􀴳􀝗􀌶
IOC:􀲩􀩒􁨝􁌱􀚠􀭌􀌵􀚡􀦤􀛸􀌵􁲀􀾪􀔻􁕳 spring 􀹶􁓕􁉘􀒅􁘒􀓧􀸎􁊧􀭏􀝎􁘏􀴴
􀚫􀒅􀨫􁈿􀴴􀚫􀝍􁫨􀌶
5􀌵BeanFactory 􀞾 ApplicationContext 􀹍􀕋􀔍􀜄􀚦?
BeanFactory 􀝢􀕦􁉘􁥴􀔅􀞌􀹍 bean 􁵞􀝳􁌱􀫡􀜯􁔄􀌶BeanFactory 􀛱􀞌􀔧􁐿
bean 􁌱􀨧􀔎􀒅􀕦􀗎􀣁􀴳􀶭􀚩􀨮􀲁􁒒􁧗􀿢􀷸􀩙􀩒􀬫􁌱 bean 􀨫􀖺􀛸􀌶
BeanFactory 􁬮􁚆􀣁􀨫􀖺􀛸􀩒􁨝􁌱􀷸􁊞􀱮􀜐􀖢􁔄􀔏􁳵􁌱􀙉􁔮􀌶􀾌􀔈􀩙 bean
􁛔􁫝􀓨 bean 􀨮􀲁􁒒􁌱 􁯈􁗝􀓾􁥴􀶱􀚊􀹶􀌶BeanFactory 􁬮􀛱􀞌􀔧 bean 􁊞
􀞸􀞮􀹗􁌱􀴴􀚫􀒅􁧣􁊠􀨮􀲁􁒒􁌱􀚡􀦤􀛸􀷜􁀩 (initialization methods)􀞾􁲀􀾪􀷜
􁀩(destruction methods)􀌶
􀕗􁤒􁶎􀓤􁍡􀒅application context 􀦇􀝶 bean factory 􀓞􀻏􀙍􀹍 bean 􀨧􀔎􀌵
bean 􀙉􁘶􀙉􁔮􁌱􁦡􁗝􀒅􀻑􀴝􁧗􀿢􀚓􀝎 bean 􁌱􀛑􁚆􀌶􀖕 applicationcontext
􀣁􀾌􀤚􁏐􀓤􁬮􀵉􀗀􀔧􀙌􀕜􁌱􀛑􁚆􀌶
1. 􀵉􀗀􀔧􀶪􀳮􀢵􁴬􀛸􁌱􀷈􀹜􁁾􀯳
2. 􁕹􀓞􁌱􁩒􁃠􀷈􀕯􁧛􀝐􀷜􀭗
3. 􀫪􀣁􁍊􀞍􀢏􀓾􁀳􀙙􁌱bean􁌱􀔪􀕯
􀕦􀓥􀸎􀓣􁐿􁫾􀬉􁥠􁌱 ApplicationContext 􀨫􁈿􀷜􀭗:
1􀌵ClassPathXmlApplicationContext:􀕗 classpath 􁌱 XML 􁯈􁗝􀷈􀕯􀓾􁧛􀝐
􀓤􀓥􀷈􀒅􀬚􁊞􀱮􀓤􀓥􀷈􀨧􀔎􀌶􀬫􁊠􁑕􀬧􀓤􀓥􀷈􀕗􁑕􀬧􁈾􀤹􀝒􁰁􀓾
ApplicationContext context = new ClassPathXmlApplicationContex
t(“bean.xml”);
2􀌵FileSystemXmlApplicationContext :􁊧􀷈􀕯􁔮􁕹􀓾􁌱 XML 􁯈􁗝􀷈􀕯􁧛􀝐
􀓤􀓥􀷈􀌶
ApplicationContext context = new FileSystemXmlApplicationConte
xt(“bean.xml”);
3􀌵XmlWebApplicationContext:􁊧 Web 􀬫􁊠􁌱 XML 􀷈􀕯􁧛􀝐􀓤􀓥􀷈􀌶
4􀌵AnnotationConfigApplicationContext(􀤚􀔭 Java 􁯈􁗝􀞐􀛖􀨻􀢏)
6􀌵Spring 􀹍􀙾􁐿􁯈􁗝􀷜􀭗?
􀩙 Spring 􁯈􁗝􀚩􀬫􁊠􀭏􀝎􀓾􀹍􀕦􀓥􀓣􁐿􀷜􀭗:
1. 􀤚􀔭XML􁌱􁯈􁗝
2. 􀤚􀔭􁀳􁥴􁌱􁯈􁗝
3. 􀤚􀔭Java􁌱􁯈􁗝
7􀌵􀦇􀖜􁊠􀤚􀔭 XML 􁯈􁗝􁌱􀷜􀭗􁯈􁗝 Spring?
􀣁 Spring 􀻛􀺝􀓾􀒅􀗁􁩢􀞾􀹐􀛓􁵱􁥝􀣁􀓫􁳪􁌱􁯈􁗝􀷈􀕯􀹶􀨫􁈿􀒅􀱯􀬉􁊠􁌱
XML 􀻒􀭗􁌱􁯈􁗝􀷈􀕯􀌶􁬯 􀔶􁯈􁗝􀷈􀕯􁌱􀻒􀭗􁭗􀬉􁊠 <beans> 􀭏􀥧􀒅􁆐􀝸
􀓞􁔮􀚜􁌱 bean 􀨧􀔎􀞾􀓫􁳪􁌱􀬫􁊠􁯈􁗝􁭌􁶱􁕟􀱮􀌶
SpringXML 􁯈􁗝􁌱􀔆􁥝􁍓􁌱􀷸􀗲􀸎􀖵􀲅􀹍􁌱 Spring 􁕟􀕯􁮷􀝢􀕦􁊠 xml 􀷈
􀕯􁌱􀭵􀭗􀹶􁬰􁤈􁯈􁗝􀌶􁬯􀰺􀞱􁍳􀓧􀕿􀚊􁈿􀙌􀕜􁌱 Spring 􁯈􁗝􁔄􀣳(􀾲􀦇􀥍
􀸁􁌱􀷜􀭗􀱲􀤚􀔭 Java Class 􁌱􁯈􁗝􀷜􀭗)
Spring 􁌱 XML 􁯈􁗝􀷜􀭗􀸎􀖵􁊠􁤩 Spring 􀞸􀝷􁑮􁳵􁌱􀲅􀶪􀳮􁌱􀓞􁔮􀚜􁌱
XML 􀺽􁓋􀹶􀨫􁈿􁌱􀌶Spring 􀹍􀕦􀓥􀔆􁥝􁌱􀞸􀝷􁑮􁳵:context􀌵beans􀌵
jdbc􀌵tx􀌵aop􀌵mvc 􀞾 aso􀌶
􀦇:
􀓥􁶎􁬯􀓻 web.xml 􀕐􀕐􁯈􁗝􀔧 DispatcherServlet􀒅􁬯􀕯􀹋􁓌􀜔􁌱􁯈􁗝􀗎􁚆
􁃿􁪃􀬫􁊠􁑕􀬧􁯈􁗝􁬩􁤈􀷸􁕟􀕯􁌱􁵱􀿢􀌶
8􀌵􀦇􀖜􁊠􀤚􀔭 Java 􁯈􁗝􁌱􀷜􀭗􁯈􁗝 Spring?
pring 􀩒 Java 􁯈􁗝􁌱􀶪􀳮􀸎􁊧@Configuration 􁀳􁥴􀞾@Bean 􁀳􁥴􀹶􀨫􁈿
􁌱􀌶􁊧@Bean 􁀳􁥴􁌱􀷜􁀩􀩙􀕿􀨫􀖺􀛸􀌵􁯈􁗝􀞾􀚡􀦤􀛸􀓞􀓻 􀷛􀩒􁨝􀒅􁬯􀓻
􀩒􁨝􀩙􁊧 Spring 􁌱 IoC 􀨻􀢏􀹶􁓕􁉘􀌶@Bean 􀥍􀸁􀲅􁩸􀚩􁌱􀖢􁊠
􀓨 <bean/> 􀘲􁔰􁔄􀖒􀌶􁤩 @Configuration 􀲅􁀳􁥴􁌱􁔄􀚞􁤒􁐏􁬯􀓻􁔄􁌱􀔆
􁥝􁍓􁌱􀸎􀖢􀔅 bean 􀨧􀔎􁌱􁩒􁃠􀌶􁤩@Configuration 􀥍􀸁􁌱􁔄􀝢􀕦􁭗􁬦􀣁
􀝶􀓞􀓻􁔄􁌱􀙖􁮱􁧣 􁊠@bean 􀷜􁀩􀹶􁦡􁗝􀫍􀙁 bean 􁌱􀗁􁩢􀙉􁔮􀌶
􀹋􁓌􀜔􁌱@Configuration 􀥍􀸁􁔄􁧗􀝇􁘍􀓥􁶎􁌱􀕤􁎱:
􀩒􀔭􀓤􁶎􁌱@Beans 􁯈􁗝􀷈􀕯􁍘􀝶􁌱 XML 􁯈􁗝􀷈􀕯􀦇􀓥:
<beans>
<bean id="myService" class="com.somnus.services.MyServiceI
mpl"/>
</beans>
􀓤􁬿􁯈􁗝􀷜􀭗􁌱􀨫􀖺􀛸􀷜􀭗􀦇􀓥:􀚥􁊠 AnnotationConfigApplicationContext
􁔄􁬰􁤈􀨫􀖺􀛸
public static void main(String[] args) {
ApplicationContext ctx = new
AnnotationConfigApplicationContext(AppConfig.class);
MyService myService = ctx.getBean(MyService.class);
myService.doStuff();
}
􁥝􀖵􁊠􁕟􀕯􁕟􀭌􀲚􀵈􀒅􀕐􁵱􁊠@Configuration 􁬰􁤈􁀳􁥴􀜨􀝢:
@Configuration
@ComponentScan(basePackages = "com.somnus")
public class AppConfig {
... }
􀣁􀓤􁶎􁌱􀖺􀧼􀓾􀒅com.acme 􀛱􁸒􀘶􀕿􁤩􀲚􀚩􀒅􁆐􀝸􀙚􀨻􀢏􀙖􀺱􀲤􁤩
@Component 􀥍􀸁􁌱􁔄􀒅􀲤􀚩􀝸􀩙􁬯􀔶􁔄􀳲􁆙 Sring bean 􀨧􀔎􁬰􁤈􁀳
􀙙􀌶
􀦇􀺎􀖦􁥝􀣁􀖦􁌱 web 􀬫􁊠􀭏􀝎􀓾􁭌􁊠􀓤􁬿􁌱􁯈􁗝􁌱􀷜􀭗􁌱􁦾􀒅􁵱􁥝􁊠
AnnotationConfigWebApplicationContext 􁔄􀹶􁧛􀝐􁯈􁗝􀷈􀕯􀒅􀝢􀕦􁊠􀹶􁯈
􁗝 Spring 􁌱 Servlet 􁍊􀞍􀢏 ContextLoaderListener 􀱲􁘏 Spring MVC 􁌱
DispatcherServlet􀌶
<web-app>
<!-- Configure ContextLoaderListener to use
AnnotationConfigWebApplicationContext
instead of the default XmlWebApplicationContext -->
<context-param>
<param-name>contextClass</param-name>
<param-value>
org.springframework.web.context.support.AnnotationConfigWebApp
licatio
nContext
</param-value>
</context-param>
<!-- Configuration locations must consist of one or more comma
- or space-delimited
fully-qualified @Configuration classes. Fully-qualifie
d
packages may also be
specified for component-scanning -->
<context-param>
<param-name>contextConfigLocation</param-name>
<param-value>com.howtodoinjava.AppConfig</param-value>
</context-param>
<!-- Bootstrap the root application context as usual using
ContextLoaderListener -->
<web-app>
<!-- Configure ContextLoaderListener to use
AnnotationConfigWebApplicationContext
instead of the default XmlWebApplicationContext -->
<context-param>
<param-name>contextClass</param-name>
<param-value>
org.springframework.web.context.support.AnnotationConfigWebApp
licatio
nContext
</param-value>
</context-param>
<!-- Configuration locations must consist of one or more comma
- or space-delimited
fully-qualified @Configuration classes. Fully-qualifie
d
packages may also be
specified for component-scanning -->
<context-param>
<param-name>contextConfigLocation</param-name>
<param-value>com.howtodoinjava.AppConfig</param-value>
</context-param>
<!-- Bootstrap the root application context as usual using
ContextLoaderListener -->
9􀌵􀯆􀻏􁊠􁀳􁥴􁌱􀷜􀭗􁯈􁗝 Spring?
Spring 􀣁 2.5 􁇇􀹜􀕦􀝸􀭏􀦤􀶪􀳮􁊠􁀳􁥴􁌱􀷜􀭗􀹶􁯈􁗝􀗁􁩢􁀳􀙁􀌶􀝢􀕦􁊠􁀳
􁥴􁌱􀷜􀭗􀹶􀹊􀕤 XML 􀷜􀭗􁌱 bean 􀵈􁬿􀒅􀝢􀕦􀩙 bean 􀵈􁬿􁫨􁑏􀚩􁕟􀕯􁔄
􁌱􀙖􁮱􀒅􀝝􁵱􁥝􀣁􁍘􀙉􁔄􀓤􀌵􀷜􁀩􀓤􀱲􁘏􀨁􀾧􀥍􀸁􀓤􀖵􁊠􁀳􁥴􀜨􀝢􀌶􁀳􁥴
􁀳􀙁􀩙􀕿􁤩􀨻􀢏􀣁 XML 􁀳􀙁􀔏􀚹􁤩􀥒􁉘􀒅􀲅􀕦􀝸􁘏􀕿􁥟􁍍􀴧􀚹􁘏􀩒􀔭􀝶
􀓞􀓻􀪂􀯔􁌱􀥒􁉘􁕮 􀺎􀌶
􁀳􁥴􁤰􁯈􀣁 Spring 􀓾􀸎􁼕􁦊􀙉􁳮􁌱􀌶􀲅􀕦􁵱􁥝􀣁 Spring 􀷈􀕯􀓾􁯈􁗝􀓞􀓥
􀲍􁚆􀖵􁊠􀤚􀔭􁀳􁥴􁌱􁤰􁯈􀽜􀭗􀌶􀦇􀺎􀖦􀰮􁥝􀣁􀖦􁌱􀬫􁊠􁑕􀬧􀓾􀖵􁊠􀙉􀔭􁀳
􁥴􁌱􀷜􁀩􁌱􁦾􀒅􁧗􀝇􁘍􀦇􀓥􁌱􁯈􁗝􀌶
<beans>
<context:annotation-config/>
<!-- bean definitions go here -->
</beans>
􀣁 <context:annotation-config/> 􀺽􁓋􁯈􁗝􀨠􀱮􀕦􀝸􀒅􀩪􀝢􀕦􁊠􁀳􁥴
􁌱􀷜􀭗􀣁 Spring 􀓾􀝻􀪂􀯔􀌵􀷜􁀩􀞾􀺅􁭜􀷜􁀩􀓾􁛔􀛖􁤰􁯈􀝒􁰁􀌶
􀓥􁶎􀸎􀙾􁐿􀾲􁫾􁯿􁥝􁌱􁀳􁥴􁔄􀣳:
1. @Required:􁧆􁀳􁥴􀬫􁊠􀔭􁦡􊧊􀷜􁀩􀌶
2. @Autowired:􁧆􁀳􁥴􀬫􁊠􀔭􀹍􊧊􁦡􊧊􀷜􁀩􀌵􁶋􁦡􊧊􀷜􁀩􀌵􀺅􁭜􀷜􁀩􀞾􀝒
􁰁􀌶
3. @Qualifier:􁧆􁀳􁥴􀞾@Autowired 􁀳􁥴􀵫􁯈􀖵􁊠􀒅􁊠􀔭􁁾􁴻􁇙􀨧 bean 􁛔
􀛖􁤰􁯈􁌱􀾏􀔎􀌶
4. JSR-250 Annotations:Spring 􀶪􀳮􀤚􀔭 JSR-250 􁀳􁥴􁌱􀕦􀓥􁀳􁥴􀒅
@Resource􀌵 @PostConstruct 􀞾 @PreDestroy􀌶
10􀌵􁧗􁥴􁯽 Spring Bean 􁌱􁊞􀞸􀞮􀹗?
Spring Bean 􁌱􁊞􀞸􀞮􀹗􁓌􀜔􀸃􀱜􀌶􀣁􀓞􀓻 bean 􀨫􀖺􁤩􀚡􀦤􀛸􀷸􀒅􁵱􁥝􀲗
􁤈􀓞􁔮􀚜􁌱􀚡􀦤􀛸􀶙􀖢􀕦􁬡􀚩􀝢􁊠􁌱􁇫􀮾􀌶􀝶􀻏􁌱􀒅􀭮􀓞􀓻 bean 􀓧􀣁􁤩
􁧣􁊠􀷸􁵱􁥝􁬰􁤈􁍘􀙉􁌱􀺉􀺅􀶙􀖢􀒅􀬚􀕗 bean 􀨻 􀢏􀓾􁑏􁴻􀌶
Spring bean factory 􁨮􁨱􁓕􁉘􀣁 spring 􀨻􀢏􀓾􁤩􀚠􀭌􁌱 bean 􁌱􁊞􀞸􀞮
􀹗􀌶Bean 􁌱􁊞􀞸􀞮􀹗􁊧􀓷􁕟􀢧􁧣(call back)􀷜􁀩􁕟􀱮􀌶
1. 􀚡􀦤􀛸􀔏􀝸􁧣􁊠􁌱􀢧􁧣􀷜􁀩􀌶
2. 􁲀􀾪􀔏􀚹􁧣􁊠􁌱􀢧􁧣􀷜􁀩􀌶
Spring 􀻛􀺝􀵉􀗀􀔧􀕦􀓥􀢥􁐿􀷜􀭗􀹶􁓕􁉘 bean 􁌱􁊞􀞸􀞮􀹗􀔪􀕯:
• InitializingBean 􀞾 DisposableBean 􀢧􁧣􀴳􀝗
• 􁰒􀩒􁇙􀾛􁤈􀔅􁌱􀙌􀕜 Aware 􀴳􀝗
• Bean􁯈􁗝􀷈􀕯􀓾􁌱Custom init()􀷜􁀩􀞾destroy()􀷜􁀩
• @PostConstruct 􀞾@PreDestroy 􁀳􁥴􀷜􀭗
􀖵􁊠 customInit()􀞾 customDestroy()􀷜􁀩􁓕􁉘 bean 􁊞􀞸􀞮􀹗􁌱􀕤􁎱􀻏􀖺􀦇
􀓥:
<beans>
<bean id="demoBean" class="com.somnus.task.DemoBean" initmethod="
customInit" destroy-method="customDestroy"></bean>
</beans>
11􀌵Spring Bean 􁌱􀖢􁊠􀤒􀔏􁳵􀹍􀕋􀔍􀜄􀚦?
Spring 􀨻􀢏􀓾􁌱 bean 􀝢􀕦􀚓􀔅 5 􀓻􁝜􀢱􀌶􀲅􀹍􁝜􀢱􁌱􀝷􁑍􁮷􀸎􁛔􁧔􀸁
􁌱􀒅􀖕􀸎􀔅􀔧􁭿􀘹􁂰􁂝􀒅􁬮􀸎􁦏􀱯􀕪􀹶􁥴􁯽􀓞􀓥:
1. singleton:􁬯􁐿 bean 􁝜􀢱􀸎􁼕􁦊􁌱􀒅􁬯􁐿􁝜􀢱􁏟􀗛􀓧􁓕􀴳􀝑􀚩􀥚􀩝􀓻􁧗
􀿢􀒅􀾯􀓻􀨻􀢏􀓾􀝝􀹍􀓞􀓻 bean 􁌱􀨫􀖺􀒅􀜔􀖺􁌱􀽜􀭗􁊧 bean factory 􁛔􁫝
􀹶􁖌􀲷􀌶
2. prototype:􀜻􀭵􁝜􀢱􀓨􀜔􀖺􁝜􀢱􁍘􀝍􀒅􀔅􀾯􀓞􀓻 bean 􁧗􀿢􀵉􀗀􀓞􀓻􀨫
􀖺􀌶
3. request:􀣁􁧗􀿢 bean 􁝜􀢱􀙖􀕿􀾯􀓞􀓻􀹶􁛔􀨮􀲁􁒒􁌱􁗑􁕶􁧗􀿢􀚠􀭌􀓞􀓻􀨫
􀖺􀒅􀣁􁧗􀿢􀨠􀱮􀕦􀝸􀒅bean 􀕿􀥦􀶴􀬚􁤩􀣯􀣍􀢧􀶭􀢏􀢧􀶭􀌶
4. Session:􀓨􁧗􀿢􁝜􀢱􁔄􀖒􀒅􁏟􀗛􀾯􀓻 session 􀓾􀹍􀓞􀓻 bean 􁌱􀨫􀖺􀒅􀣁
session 􁬦􀹗􀝸􀒅bean 􀕿􁵋􀔏􀥦􀶴􀌶
5. global- session:global-session 􀞾 Portlet 􀬫􁊠􁍘􀙉􀌶􀭮􀖦􁌱􀬫􁊠􁮱􁗟􀣁
Portlet 􀨻􀢏􀓾􀫡􀖢􀷸􀒅􀨙􀛱􀞌􀮉􀥚 portlet􀌶􀦇􀺎􀖦􀰮􁥝􀥍􀸁􁦏􀲅􀹍􁌱
portlet 􀙈􁊠􀙂􀩴􁌱􀨂􀘙􀝒􁰁􁌱􁦾􀒅􁮎􀔍􁬯􀙂􀩴􀝒􁰁􁵱􁥝􀨂􀘙􀣁 globalsession
􀓾􀌶
􀙂􀩴􀖢􁊠􀤒􀓨 Servlet 􀓾􁌱 session 􀖢􁊠􀤒􀶴􀺎􁍘􀝶􀌶
12􀌵􀕋􀔍􀸎 Spring inner beans?
􀣁 Spring 􀻛􀺝􀓾􀒅􀷫􁦞􀖜􀷸 bean 􁤩􀖵􁊠􀷸􀒅􀭮􀕐􁤩􁧣􁊠􀔧􀓞􀓻􀪂􀯔􀌶􀓞
􀓻􀸁􀸬􁌱􀘉􁀩􀸎􀩙􁬯􀓻 bean 􀥍􀸁􀔅􀙖􁮱 bean􀌶􀙖􁮱 bean 􀝢􀕦􁊠 setter
􁀳􀙁“􀪂􀯔”􀞾􀺅􁭜􀷜􁀩􁀳􀙁“􀺅􁭜􀝇􀷄”􁌱􀷜􀭗􀹶 􀨫􁈿􀌶
􀾲􀦇􀒅􀣁􀱯􀕪􁌱􀬫􁊠􁑕􀬧􀓾􀒅􀓞􀓻 Customer 􁔄􀭚􁊠􀔧􀓞􀓻 Person 􁔄􀒅
􀱯􀕪􁌱􁥝􀘉􁌱􀸎􀚠􀭌􀓞􀓻 Person 􁌱􀨫􀖺􀒅􁆐􀝸􀣁 Customer 􀙖􁮱􀖵􁊠􀌶
public class Customer{
private Person person;
//Setters and Getters
}
public class Person{
private String name;
private String address;
private int age;
//Setters and Getters
}
􀙖􁮱 bean 􁌱􀥍􀸁􀷜􀭗􀦇􀓥:
<bean id="CustomerBean" class="com.somnus.common.Customer">
<property name="person">
<!-- This is inner bean -->
<bean class="com.howtodoinjava.common.Person">
<property name="name" value="lokesh" />
<property name="address" value="India" />
<property name="age" value="34" />
</bean>
</property>
</bean>
13􀌵Spring 􀻛􀺝􀓾􁌱􀜔􀖺 Beans 􀸎􁕚􁑕􀨞􀙂􁌱􀔍?
Spring 􀻛􀺝􀬚􁀌􀹍􀩒􀜔􀖺 bean 􁬰􁤈􀕱􀖜􀥚􁕚􁑕􁌱􀩗􁤰􀥒􁉘􀌶􀙉􀔭􀜔􀖺
bean 􁌱􁕚􁑕􀨞􀙂􀞾􀬚􀝎􁳯􁷌􁵱􁥝􀭏􀝎􁘏􁛔􁤈􀝄􀵥􀨧􀌶􀖕􀨫􁴬􀓤􀒅􀥟􁮱􀚓
􁌱 Spring bean 􀬚􁀌􀹍􀝢􀝒􁌱􁇫􀮾(􀾲􀦇 Serview 􁔄􀞾 DAO 􁔄)􀒅􀲅􀕦􀣁􀺤
􁐿􁑕􀬶􀓤􁧔 Spring 􁌱􀜔􀖺 bean 􀸎􁕚􁑕􀨞􀙂􁌱􀌶􀦇􀺎􀖦􁌱 bean 􀹍􀥚􁐿􁇫
􀮾􁌱􁦾(􀾲􀦇 View Model 􀩒􁨝)􀒅􀩪􁵱􁥝􁛔􁤈􀗛􁦤􁕚􁑕􀨞􀙂􀌶
􀹋􁁠􀸔􁌱􁥴􀙬􀛐􁀩􀩪􀸎􀩙􀥚􀮾 bean 􁌱􀖢􁊠􀤒􁊧“singleton”􀝒􀹅
􀔅“prototype”􀌶
14􀌵􁧗􀔈􀖺􁧔􀸁􀦇􀖜􀣁 Spring 􀓾􁀳􀙁􀓞􀓻 Java Collection?
Spring 􀵉􀗀􀔧􀕦􀓥􀢥􁐿􁵞􀝳􁔄􁌱􁯈􁗝􀘲􁔰:
• <list> : 􁧆􀺽􁓋􁊠􀹶􁤰􁯈􀝢􁯿􀥔􁌱 list 􊧊􀌶
• <set> : 􁧆􀺽􁓋􁊠􀹶􁤰􁯈􁀌􀹍􁯿􀥔􁌱 set 􊧊􀌶
• <map> : 􁧆􀺽􁓋􀝢􁊠􀹶􁀳􀙁􁲫􀞾􊧊􀝢􀕦􀔅􀕱􀖜􁔄􀣳􁌱􁲫􊧊􀩒􀌶
• <props> : 􁧆􀺽􁓋􀶪􀳮􁀳􀙁􁲫􀞾􊧊􁮷􀸎􀨁􁒧􀔀􁔄􀣳􁌱􁲫􊧊􀩒􀌶
􀓥􁶎􁍡􀓞􀓥􀙍􀖛􁌱􀖺􀧼:
<beans>
<!-- Definition for javaCollection -->
<bean id="javaCollection" class="com.howtodoinjava.JavaCollect
ion">
<!-- java.util.List -->
<property name="customList">
<list>
<value>INDIA</value>
<value>Pakistan</value>
<value>USA</value>
<value>UK</value>
</list>
</property>
<!-- java.util.Set -->
<property name="customSet">
<set>
<value>INDIA</value>
<value>Pakistan</value>
<value>USA</value>
<value>UK</value>
</set>
</property>
<!-- java.util.Map -->
<property name="customMap">
<map>
<entry key="1" value="INDIA"/>
<entry key="2" value="Pakistan"/>
<entry key="3" value="USA"/>
<entry key="4" value="UK"/>
</map>
</property>
<!-- java.util.Properties -->
<property name="customProperies">
<props>
<prop key="admin">admin@nospam.com</prop>
<prop key="support">support@nospam.com</prop>
</props>
</property>
</bean>
</beans>
15􀌵􀦇􀖜􀝻 Spring Bean 􀓾􁀳􀙁􀓞􀓻 Java.util.Properties?
􁒫􀓞􁐿􀷜􁀩􀸎􀖵􁊠􀦇􀓥􁶎􀕤􁎱􀲅􁐏􁌱 <props> 􀺽􁓋:
<bean id="adminUser" class="com.somnus.common.Customer">
<!-- java.util.Properties -->
<property name="emails">
<props>
<prop key="admin">admin@nospam.com</prop>
<prop key="support">support@nospam.com</prop>
</props>
</property>
</bean>
􀔞􀝢􁊠”util:”􀞸􀝷􁑮􁳵􀹶􀕗 properties 􀷈􀕯􀓾􀚠􀭌􀚊􀓞􀓻 propertiesbean􀒅
􁆐􀝸􀚥􁊠 setter 􀷜 􁀩􁀳􀙁 bean 􁌱􀭚􁊠􀌶
16􀌵􁧗􁥴􁯽 Spring Bean 􁌱􁛔􀛖􁤰􁯈?
􀣁 Spring 􀻛􀺝􀓾􀒅􀣁􁯈􁗝􀷈􀕯􀓾􁦡􀨧 bean 􁌱􀗁􁩢􀙉􁔮􀸎􀓞􀓻􀮉􀦅􁌱􀹢
􀚫􀒅Spring 􀨻􀢏􁬮􀝢􀕦􁛔 􀛖􁤰􁯈􀝳􀖢􀙉􁔮 bean 􀔏􁳵􁌱􀙉􁘶􀙉􁔮􀌶􁬯􀰺􀞱
􁍳 Spring 􀝢􀕦􁭗􁬦􀝻 Bean Factory 􀓾􁀳􀙁􁌱􀷜 􀭗􁛔􀛖􀵥􀨧 bean 􀔏􁳵􁌱
􀗁􁩢􀙉􁔮􀌶􁛔􀛖􁤰􁯈􀝢􀕦􁦡􁗝􀣁􀾯􀓻 bean 􀓤􀒅􀔞􀝢􀕦􁦡􀨧􀣁􁇙􀨧􁌱 bean
􀓤􀌶
􀓥􁶎􁌱 XML 􁯈􁗝􀷈􀕯􁤒􀸁􀔧􀦇􀖜􀻑􀴝􀝷􁑍􀩙􀓞􀓻 bean 􁦡􁗝􀔅􁛔􀛖􁤰􁯈:
<bean id="employeeDAO" class="com.howtodoinjava.EmployeeDAOImp
l"
autowire="byName" />
􁴻􀔧 bean 􁯈􁗝􀷈􀕯􀓾􀵉􀗀􁌱􁛔􀛖􁤰􁯈􀽜􀭗􀒅􁬮􀝢􀕦􀖵􁊠@Autowired 􁀳􁥴
􀹶􁛔􀛖􁤰􁯈􀳰􀨧 􁌱 bean􀌶􀣁􀖵􁊠@Autowired 􁀳􁥴􀔏􀚹􁵱􁥝􀣁􀳲􁆙􀦇􀓥􁌱
􁯈􁗝􀷜􀭗􀣁 Spring 􁯈􁗝􀷈􀕯􁬰􁤈􁯈􁗝􀲍􀝢􀕦􀖵􁊠􀌶
<context:annotation-config />
􀔞􀝢􀕦􁭗􁬦􀣁􁯈􁗝􀷈􀕯􀓾􁯈􁗝 AutowiredAnnotationBeanPostProcessor 􁬡
􀚩􁍘􀝶􁌱􀶴􀺎􀌶
<bean class
="org.springframework.beans.factory.annotation.AutowiredAnnota
tionBea
nPostProcessor"/>
􁯈􁗝􀦅􀕦􀝸􀩪􀝢􀕦􀖵􁊠@Autowired 􀹶􀺽􁀳􀔧􀌶
@Autowired
public EmployeeDAOImpl ( EmployeeManager manager ) {
this.manager = manager;
}
17􀌵􁧗􁥴􁯽􁛔􀛖􁤰􁯈􀽜􀭗􁌱􀜄􀚦?
􀣁 Spring 􀻛􀺝􀓾􀙈􀹍 5 􁐿􁛔􀛖􁤰􁯈􀒅􁦏􀱯􀕪􁭑􀓞􀚓􀺉􀌶
1. no:􁬯􀸎 Spring 􀻛􀺝􁌱􁼕􁦊􁦡􁗝􀒅􀣁􁧆􁦡􁗝􀓥􁛔􀛖􁤰􁯈􀸎􀙉􁳮􁌱􀒅􀭏􀝎
􁘏􁵱􁥝􁛔􁤈􀣁 bean 􀨧􀔎 􀓾􁊠􀺽􁓋􀸁􁏟􁌱􁦡􁗝􀗁􁩢􀙉􁔮􀌶
2. byName:􁧆􁭌􁶱􀝢􀕦􀻑􀴝 bean 􀝷􁑍􁦡􁗝􀗁􁩢􀙉􁔮􀌶􀭮􀝻􀓞􀓻 bean 􀓾
􁛔􀛖􁤰􁯈􀓞􀓻􀪂􀯔􀷸􀒅􀨻􀢏􀩙􀻑􀴝 bean 􁌱􀝷􁑍􁛔􀛖􀣁􀣁􁯈􁗝􀷈􀕯􀓾􀺱􁧃
􀓞􀓻􀜃􁯈􁌱 bean􀌶􀦇􀺎􀲤􀚩􁌱􁦾􀒅􀩪􁤰􁯈􁬯􀓻􀪂􀯔􀒅􀦇􀺎􁀌􀲤􀚩􁌱􁦾􀩪
􀲸􁲙􀌶
3. byType:􁧆􁭌􁶱􀝢􀕦􀻑􀴝 bean 􁔄􀣳􁦡􁗝􀗁􁩢􀙉􁔮􀌶􀭮􀝻􀓞􀓻 bean 􀓾􁛔
􀛖􁤰􁯈􀓞􀓻􀪂􀯔􀷸􀒅􀨻􀢏􀩙􀻑􀴝 bean 􁌱􁔄􀣳􁛔􀛖􀣁􀣁􁯈􁗝􀷈􀕯􀓾􀺱􁧃􀓞
􀓻􀜃􁯈􁌱 bean􀌶􀦇􀺎􀲤􀚩􁌱􁦾􀒅􀩪􁤰􁯈􁬯􀓻􀪂􀯔􀒅􀦇􀺎􁀌􀲤􀚩􁌱􁦾􀩪􀲸
􁲙􀌶
4. constructor:􁭜􀢏􁌱􁛔􀛖􁤰􁯈􀞾 byType 􀽜􀭗􁔄􀖒􀒅􀖕􀸎􀕐􀕐􁭇􁊠􀔭􀓨􀹍
􀺅􁭜􀢏􁍘􀝶􀝇􀷄􁌱 bean􀒅􀦇􀺎􀣁􀨻􀢏􀓾􁀌􀹍􀲤􀚩􀓨􀺅􁭜􀢏􀝇􀷄􁔄􀣳􀓞􁛘
􁌱 bean􀒅􁮎􀔍􀩙􀕿􀲲􀚊􀭑􀬉􀌶
5. autodetect:􁧆􀽜􀭗􁛔􀛖􀴱􁁥􀖵􁊠􀺅􁭜􀢏􁛔􀛖􁤰􁯈􀱲􁘏 byType 􁛔􀛖􁤰
􁯈􀌶􁸒􀘶􀒅􁸒􀘶􀕿􀩤􁦶􀲤􀝳􁭇􁌱􀬃􀝇􀷄􁌱􀺅􁭜􀢏􀒅􀦇􀺎􀲤􀚩􁌱􁦾􀩪􀸎􁊠􀺅
􁭜􀢏􁛔􀛖􁤰􁯈􀒅􀦇􀺎􀣁 bean 􀙖􁮱􁀌􀹍􀲤􀚩􁍘􀬫􁌱􀺅􁭜􀢏􀱲􁘏􀸎􀷫􀝇􀺅􁭜
􀢏􀒅􀨻􀢏􀩪􀕿􁛔􀛖􁭌􀳠 byTpe 􁌱􁛔􀛖􁤰􁯈􀷜􀭗􀌶
18􀌵􀦇􀖜􀭏􀞐􀤚􀔭􁀳􁥴􁌱􁛔􀛖􁤰􁯈?
􁥝􀖵􁊠 @Autowired􀒅􁵱􁥝􁀳􀙙 AutowiredAnnotationBeanPostProcessor􀒅
􀝢􀕦
􀹍􀕦􀓥􀓷􁐿􀷜􀭗􀹶􀨫􁈿:
1􀌵􀭚􀙁􁯈􁗝􀷈􀕯􀓾􁌱 <bean> 􀓥􀭚􀙁 <context:annotation-config>
<beans>
<context:annotation-config />
</beans>
2􀌵􀣁 bean 􁯈􁗝􀷈􀕯􀓾􁍗􀴳􀭚􀙁 AutowiredAnnotationBeanPostProcessor
<beans>
<bean
class="org.springframework.beans.factory.annotation.AutowiredA
nnotati
onBeanPostProcessor"/>
</beans>
19􀌵􁧗􀔈􀖺􁥴􁯽@Required 􁀳􁥴?
􀣁􀔾􀟝􁕆􀚦􁌱􀬫􁊠􀓾􀒅IoC 􀨻􀢏􀝢􁚆􀥍􀸁􀔧􀷄􀜈􀓡􀔧 bean􀒅bean 􀓨 bean
􀔏􁳵􀹍􁍳􀥔􀹥􁌱􀗁􁩢􀙉􁔮􀌶􁦡􊧊􁀳􁥴􀷜􁀩􁌱􁎨􀺃􀔏􀓞􀩪􀸎􁸵􁦤􀲅􀹍􁌱􀪂􀯔
􀸎􀞈􁤩􁀳􁥴􀸎􀓞􁶱􀜈􀚓􀢯􁵙􁌱􀶙􀖢􀌶􀝢􀕦􁭗􁬦􀣁 <bean> 􀓾􁦡
􁗝“dependency-check”􀹶􁥴􀙬􁬯􀓻􁳯􁷌􀌶
􀣁􀬫􁊠􁑕􀬧􁌱􁊞􀞸􀞮􀹗􀓾􀒅􀖦􀝢􁚆􀓧􀥟􀱄􀰺􁜰􀷸􁳵􀣁􁸵􁦤􀲅􀹍 bean 􁌱􀪂
􀯔􀸎􀞈􀳲􁆙􀓤􀓥􀷈􀕯􀾋􁏟􁯈􁗝􀌶􀱲􁘏􀖦􀨘􀝢􁸵􁦤􀺤􀓻 bean 􁌱􁇙􀨧􀪂􀯔􀸎
􀞈􁤩􀾋􁏟􁌱􁦡􁗝􀌶􀜨􀖵􀸎􁊠“dependency- check”􀪂􀯔􀔞􀓧􁚆􀮉􀦅􁌱􁥴􀙬􁬯
􀓻􁳯􁷌􀒅􀣁􁬯􁐿􀰘􀙭􀓥􀒅􀖦􁵱􁥝􀖵􁊠@Required 􁀳􁥴􀌶
􁵱􁥝􁊠􀦇􀓥􁌱􀷜􀭗􀖵􁊠􀹶􀺽􀸁 bean 􁌱􁦡􊧊􀷜􁀩􀌶
public class EmployeeFactoryBean extends AbstractFactoryBean<O
bject>{
private String designation;
public String getDesignation() {
return designation;
}
@Required
public void setDesignation(String designation) {
this.designation = designation;
}
//more code here
}
RequiredAnnotationBeanPostProcessor 􀸎 Spring 􀓾􁌱􀝸􁗝􀥒􁉘􁊠􀹶􁸵􁦤
􁤩 @Required 􁀳􁥴􁌱 bean 􀪂􀯔􀸎􀞈􁤩􀾋􁏟􁌱􁦡􁗝􀔧􀌶􀣁􀖵􁊠
RequiredAnnotationBeanPostProcesso 􀹶􁸵􁦤 bean 􀪂􀯔􀔏􀚹􀒅􁸒􀘶􁥝􀣁
IoC 􀨻􀢏􀓾􀩒􀙌􁬰􁤈􁀳􀙙:
<bean
class="org.springframework.beans.factory.annotation.RequiredAn
notatio
nBeanPostProcessor" />
􀖕􀸎􀦇􀺎􁀌􀹍􀪂􀯔􁤩􁊠 @Required 􁀳􁥴􁬦􁌱􁦾􀒅􀝸􁗝􀥒􁉘􀢏􀕿􀲲􀚊􀓞􀓻
BeanInitializationException 􀭑􀬉􀌶
20􀌵􁧗􀔈􀖺􁥴􁯽@Autowired 􁀳􁥴?
@Autowired 􁀳􁥴􀩒􁛔􀛖􁤰􁯈􀖜􀷸􀖜􀥒􁤩􀨫􁈿􀵉􀗀􀔧􀹅􀥚􁕡􁔉􀬶􁌱􀴴􀚫􀌶
@Autowired 􁀳􁥴􀝢 􀕦􀘟@Required 􁀳􁥴􀌵􀺅􁭜􀢏􀓞􀻏􁤩􁊠􀔭􀣁 bean 􁌱􁦡
􊧊􀷜􁀩􀓤􁛔􀛖􁤰􁯈 bean 􁌱􀪂􀯔􀒅􀓞􀓻􀝇􀷄􀱲􁘏􀬃􀹍􀕱􀰺􀝷􁑍􀱲􀬃􀹍􀥚􀓻
􀝇􀷄􁌱􀷜􁀩􀌶􀾲􀦇􀒅􀝢􀕦􀣁􁦡􊧊􀷜􁀩􀓤􀖵􁊠@Autowired 􁀳􁥴􀹶􀹊􀕤􁯈􁗝
􀷈􀕯􀓾􁌱 <property> 􀘲􁔰􀌶􀭮 Spring 􀨻􀢏􀣁 setter 􀷜􁀩􀓤􀲤􀚩
@Autowired 􁀳􁥴􀷸􀒅􀕿􀩤􁦶􁊠 byType 􁛔􀛖􁤰􁯈􀌶
􀭮􁆐􀱯􀕪􀔞􀝢􀕦􀣁􀺅􁭜􀷜􁀩􀓤􀖵􁊠@Autowired 􁀳􁥴􀌶􀬃􀹍@Autowired 􁀳
􁥴􁌱􀺅􁭜􀷜􁀩􀰺􀞱􁍳 􀣁􀚠􀭌􀓞􀓻 bean 􀷸􀩙􀕿􁤩􁛔􀛖􁤰􁯈􀒅􀜨􀗎􀣁􁯈􁗝􀷈
􀕯􀓾􀖵􁊠 􀘲􁔰􀌶
public class TextEditor {
private SpellChecker spellChecker;
@Autowired
public TextEditor(SpellChecker spellChecker){
System.out.println("Inside TextEditor constructor." );
this.spellChecker = spellChecker;
}
public void spellCheck(){
spellChecker.checkSpelling();
} }
􀓥􁶎􀸎􁀌􀹍􀺅􁭜􀝇􀷄􁌱􁯈􁗝􀷜􀭗:
<beans>
<context:annotation-config/>
<!-- Definition for textEditor bean without constructor-arg
-->
<bean id="textEditor" class="com.howtodoinjava.TextEditor"/

<!-- Definition for spellChecker bean -->
<bean id="spellChecker" class="com.howtodoinjava.SpellCheck
er"/>
</beans>
21􀌵􁧗􀔈􀖺􁧔􀸁@Qualifier 􁀳􁥴?
@Qualifier 􁀳􁥴􀰺􀞱􁍳􀝢􀕦􀣁􁤩􀺽􁀳 bean 􁌱􀨁􀾧􀓤􀝢􀕦􁛔􀛖􁤰􁯈􀌶
Qualifier 􁀳􁥴􀝢􀕦􁊠􀹶􀝐􁁾 Spring 􀓧􁚆􀝐􁁾􁌱 bean 􀬫􁊠􀌶
􀓥􁶎􁌱􁐏􀖺􀩙􀕿􀣁 Customer 􁌱 person 􀪂􀯔􀓾􁛔􀛖􁤰􁯈 person 􁌱􊧊􀌶
public class Customer{
@Autowired
private Person person;
}
􀓥􁶎􀱯􀕪􁥝􀣁􁯈􁗝􀷈􀕯􀓾􀹶􁯈􁗝 Person 􁔄􀌶
<bean id="customer" class="com.somnus.common.Customer" />
<bean id="personA" class="com.somnus.common.Person" >
<property name="name" value="lokesh" />
</bean>
<bean id="personB" class="com.somnus.common.Person" >
<property name="name" value="alex" />
</bean>
Spring 􀕿􁎣􁭲􁥝􁛔􀛖􁤰􁯈􀟺􀓻 person bean 􀔍?􀓧􀕿􁌱􀒅􀖕􀸎􁬩􁤈􀓤􁶎􁌱
􁐏􀖺􀷸􀒅􀕿􀲲􀚊􀓥􁶎􁌱􀭑􀬉:
Caused by:
org.springframework.beans.factory.NoSuchBeanDefinitionExceptio
n:
No unique bean of type [com.howtodoinjava.common.Person] is de
fined: expected single matching bean but found 2: [personA, pe
rsonB]
􁥝􁥴􀙬􀓤􁶎􁌱􁳯􁷌􀒅􁵱􁥝􀖵􁊠 @Quanlifier 􁀳􁥴􀹶􀞞􁦫 Spring 􀨻􀢏􁥝􁤰􁯈
􀟺􀓻 bean:
public class Customer{
@Autowired
@Qualifier("personA")
private Person person;
}
22􀌵􀺅􁭜􀷜􁀩􁀳􀙁􀞾􁦡􊧊􁀳􀙁􀹍􀕋􀔍􀜄􀚦? 􁧗􁀳􀰺􀕦􀓥􀸁􀸔􁌱􀜄􀚦:
1. 􀣁􁦡􊧊􁀳􀙁􀷜􁀩􀶪􀳮􀥟􁮱􀚓􁌱􀗁􁩢􁀳􀙁􀒅􀦇􀺎􀱯􀕪􀕐􁵱􁥝􁀳􀙁int􀌵
string􀞾long􀣳􁌱􀝒􁰁􀒅􀱯􀕪􀓧􁥝􁊠􁦡􊧊􁌱􀷜􁀩􁀳􀙁􀌶􀩒􀔭􀤚􀹜􁔄􀣳􀒅􀦇􀺎
􀱯􀕪􁀌􀹍􁀳􀙁􁌱􁦾􀒅􀝢􀕦􀔅􀤚􀹜􁔄􀣳􁦡􁗝􁼕􁦊􊧊􀌶􀣁􀺅􁭜􀷜􁀩 􁀳􀙁􀓧􀶪􀳮
􀥟􁮱􀚓􁌱􀗁􁩢􁀳􀙁􀒅􀢩􀔅􀣁􁧣􁊠􀺅􁭜􀷜􁀩􀓾􀮠􁶳􀖃􀙁􀾋􁏟􁌱􀺅􁭜􀝇􀷄􀒅􀞈
􀚞􁌱􁦾􀔅􀲸􁲙􀌶
2. 􁦡􊧊􁀳􀙁􀓧􀕿􁯿􀙟􀺅􁭜􀷜􁀩􁌱􊧊􀌶􀦇􀺎􀱯􀕪􀩒􀝶􀓞􀓻􀝒􁰁􀝶􀷸􀖵􁊠􀔧􀺅
􁭜􀷜􁀩􁀳􀙁􀝈􀖵􁊠􀔧􁦡􁗝􀷜􁀩􁀳􀙁􁌱􁦾􀒅􁮎􀔍􀺅􁭜􀷜􁀩􀩙􀓧􁚆􁥟􁍍􁊧􁦡􊧊
􀷜􁀩􁀳􀙁􁌱􊧊􀌶􀮉􀸁􀸔􀒅􀢩􀔅􀺅􁭜􀷜􁀩􀩱􀣁􀩒􁨝􁤩􀚠􀭌􀷸􁧣􁊠􀌶
3. 􀣁􀖵􁊠􁦡􊧊􁀳􀙁􀷸􀹍􀝢􁚆􁬮􀓧􁚆􀗛􁦤􀺤􁐿􀗁􁩢􀸎􀞈􀫪􁕪􁤩􁀳􀙁􀒅􀔞􀩪􀸎
􁧔􁬯􀷸􀩒􁨝􁌱􀗁􁩢􀙉􁔮􀹍􀝢􁚆􀸎􀓧􀨠􀷆􁌱􀌶􁘒􀣁􀝚􀓞􁐿􀰘􀙭􀓥􀒅􀺅􁭜􀢏􁀳
􀙁􀚞􀓧􊧋􁦜􁊞􀱮􀗁􁩢􀙉􁔮􀓧􀨠􀷆􁌱􀩒􁨝􀌶
4. 􀣁􁦡􊧊􁀳􀙁􀷸􀦇􀺎􀩒􁨝A􀞾􀩒􁨝B􀔰􁍘􀗁􁩢􀒅􀣁􀚠􀭌􀩒􁨝A􀷸Spring􀕿􀲲
􀚊 sObjectCurrentlyInCreationException 􀭑􀬉􀒅􀢩􀔅􀣁 B 􀩒􁨝􁤩􀚠􀭌􀔏􀚹
A 􀩒 􁨝􀸎􀓧􁚆􁤩􀚠􀭌􁌱􀒅􀝍􀔏􀔽􁆐􀌶􀲅􀕦 Spring 􁊠􁦡􊧊􁀳􀙁􁌱􀷜􁀩􁥴􀙬
􀔧􀮗􁈾􀗁􁩢􁌱􁳯􁷌􀒅􀢩􀩒􁨝􁌱􁦡􊧊􀷜􁀩􀸎􀣁􀩒􁨝􁤩􀚠􀭌􀔏􀚹􁤩􁧣􁊠􁌱􀌶
23􀌵Spring 􀻛􀺝􀓾􀹍􀟺􀔶􀓧􀝶􁔄􀣳􁌱􀔪􀕯?
Spring 􁌱 ApplicationContext 􀵉􀗀􀔧􀶪􀳮􀔪􀕯􀞾􀕤􁎱􀓾􁍊􀞍􀢏􁌱􀛑􁚆􀌶
􀱯􀕪􀝢􀕦􀚠􀭌 bean 􁊠􀹶􁍊􀞍􀣁 ApplicationContext 􀓾􀝎􀫲􁌱􀔪􀕯􀌶
ApplicationEvent 􁔄􀞾􀣁 ApplicationContext 􀴳􀝗􀓾􀥒􁉘􁌱􀔪􀕯􀒅􀦇􀺎􀓞􀓻
bean 􀨫􁈿􀔧 ApplicationListener 􀴳􀝗􀒅􀭮􀓞􀓻 ApplicationEvent 􁤩􀝎􀫲􀕦
􀝸􀒅bean 􀕿􁛔􀛖􁤩􁭗􁎣􀌶
public class AllApplicationEventListener implements Applicatio
nListener < ApplicationEvent >{
@Override
public void onApplicationEvent(ApplicationEvent applicatio
nEvent)
{
//process event
}
}
Spring 􀵉􀗀􀔧􀕦􀓥 5 􀓾􀺽􀙵􁌱􀔪􀕯:
1. 􀓤􀓥􀷈􀹅􀷛􀔪􀕯(ContextRefreshedEvent):􁧆􀔪􀕯􀕿􀣁ApplicationContext
􁤩􀚡􀦤􀛸􀱲􁘏􀹅􀷛􀷸􀝎􀫲􀌶􀔞􀝢􀕦􀣁􁧣􁊠 ConfigurableApplicationContext
􀴳􀝗􀓾􁌱 refresh()􀷜􁀩􀷸􁤩􁥶􀝎􀌶
2. 􀓤􀓥􀷈􀭏􀦤􀔪􀕯(ContextStartedEvent):􀭮􀨻􀢏􁧣􁊠
ConfigurableApplicationContext􁌱 Start()􀷜􁀩􀭏􀦤/􁯿􀷛􀭏􀦤􀨻􀢏􀷸􁥶􀝎􁧆
􀔪􀕯􀌶
3. 􀓤􀓥􀷈􀘊􀾊􀔪􀕯(ContextStoppedEvent):􀭮􀨻􀢏􁧣􁊠
ConfigurableApplicationContext􁌱 Stop()􀷜􁀩􀘊􀾊􀨻􀢏􀷸􁥶􀝎􁧆􀔪􀕯􀌶
4. 􀓤􀓥􀷈􀙉􁳮􀔪􀕯(ContextClosedEvent):􀭮ApplicationContext􁤩􀙉􁳮􀷸􁥶
􀝎􁧆􀔪􀕯􀌶􀨻􀢏􁤩􀙉􁳮􀷸􀒅􀙌􁓕􁉘􁌱􀲅􀹍􀜔􀖺 Bean 􁮷􁤩􁲀􀾪􀌶
5. 􁧗􀿢􀥒􁉘􀔪􀕯(RequestHandledEvent):􀣁Web􀬫􁊠􀓾􀒅􀭮􀓞􀓻http􁧗􀿢
(request)􁕮􀹳 􁥶􀝎􁧆􀔪􀕯􀌶
􁴻􀔧􀓤􁶎􀕕􁕨􁌱􀔪􀕯􀕦􀥘􀒅􁬮􀝢􀕦􁭗􁬦􀲘􀪀 ApplicationEvent 􁔄􀹶􀭏􀝎􁛔
􀨧􀔎􁌱􀔪􀕯􀌶
public class CustomApplicationEvent extends ApplicationEvent{
public CustomApplicationEvent ( Object source, final String ms
g ){
super(source);
System.out.println("Created a Custom event");
}
}
􀔅􀔧􁍊􀞍􁬯􀓻􀔪􀕯􀒅􁬮􁵱􁥝􀚠􀭌􀓞􀓻􁍊􀞍􀢏:
public class CustomEventListener implements ApplicationListene
r <
CustomApplicationEvent >{
@Override
public void onApplicationEvent(CustomApplicationEvent
applicationEvent) {
//handle event
}
}
􀔏􀝸􁭗􁬦 applicationContext 􀴳􀝗􁌱 publishEvent()􀷜􁀩􀹶􀝎􀫲􁛔􀨧􀔎􀔪
􀕯􀌶
CustomApplicationEvent customEvent = new
CustomApplicationEvent(applicationContext, "Test message");
applicationContext.publishEvent(customEvent);
24􀌵FileSystemResource 􀞾 ClassPathResource 􀹍􀖜􀜄􀚦?
􀣁 FileSystemResource 􀓾􁵱􁥝􁕳􀚊 spring-config.xml 􀷈􀕯􀣁􀖦􁶱􁍓􀓾􁌱􁍘
􀩒􁪠􀮆􀱲􁘏􁕷􀩒􁪠􀮆􀌶􀣁 ClassPathResource 􀓾 spring 􀕿􀣁 ClassPath 􀓾
􁛔􀛖􀵤􀩔􁯈􁗝􀷈􀕯􀒅􀲅􀕦􁥝􀲩 ClassPathResource 􀷈􀕯􀶱􀣁 ClassPath
􀓥􀌶
􀦇􀺎􀩙 spring-config.xml 􀗛􀨂􀣁􀔧 src 􀷈􀕯􀥪􀓥􁌱􁦾􀒅􀝝􁵱􁕳􀚊􁯈􁗝􀷈􀕯
􁌱􀝷􁑍􀜨􀝢􀒅􀢩􀔅 src 􀷈􀕯􀥪􀸎􁼕􁦊􀌶
􁓌􁘒􁥺􀔏􀒅ClassPathResource 􀣁􁈾􀤹􀝒􁰁􀓾􁧛􀝐􁯈􁗝􀷈􀕯􀒅
FileSystemResource 􀣁􁯈􁗝􀷈􀕯􀓾􁧛􀝐􁯈􁗝􀷈􀕯􀌶
25􀌵Spring 􀻛􀺝􀓾􁮷􁊠􀚩􀔧􀟺􀔶􁦡􁦇􀽜􀭗?
Spring 􀻛􀺝􀓾􀖵􁊠􀚩􀔧􀥟􁰁􁌱􁦡􁦇􀽜􀭗􀒅􀓥􁶎􀚜􀔈􀔧􀾲􁫾􀹍􀕤􁤒􀯔􁌱:
o 􀕤􁉘􀽜􀭗—􀣁AOP􀞾remoting􀓾􁤩􁊠􁌱􀾲􁫾􀥚􀌶
o 􀜔􀖺􀽜􀭗—􀣁spring􁯈􁗝􀷈􀕯􀓾􀨧􀔎􁌱bean􁼕􁦊􀔅􀜔􀖺􀽜􀭗􀌶
o 􀽜􀺃􀷜􁀩—􁊠􀹶􁥴􀙬􀕤􁎱􁯿􀥔􁌱􁳯􁷌􀌶􀾲
􀦇.RestTemplate,JmsTemplate,JpaTempl ate􀌶
o 􀚹􁒒􀴴􀚫􀢏—Spring􀵉􀗀􀔧DispatcherServlet􀹶􀩒􁧗􀿢􁬰􁤈􀚓􀝎􀌶
o 􁥤􀢶􀬆􀛗(ViewHelper)—Spring􀵉􀗀􀔧􀓞􁔮􀚜􁌱JSP􀺽􁓋􀒅􁹛􀶴􀨡􀹶􁬀􀛗
􀩙􀚓􀷀􁌱􀕤􁎱􀷆􀝳􀣁􁥤􀢶􁯾􀌶
o 􀗁􁩢􁀳􀙁—􁨽􁑯􀔭BeanFactory/ApplicationContext􀴳􀝗􁌱􀻐􀮞􁉘􀮷􀌶
o 􀫡􀜯􀽜􀭗—BeanFactory􁊠􀹶􀚠􀭌􀩒􁨝􁌱􀨫􀖺
26􀌵􀭏􀝎􀓾􀔆􁥝􀖵􁊠 Spring 􁌱􀕋􀔍􀲦􀹞 ?
1. IOC 􀨻􀢏􁓕􁉘􀝱􀩶􁌱􁕟􀕯
2. 􀖵􁊠 AOP 􁯈􁗝􀥍􀸁􀭗􀔪􀛓
3. 􀷆􀝳􀙌􀕜􀻛􀺝.
27􀌵􁓌􁬿 AOP 􀞾 IOC 􀼷􀮷 AOP:
Aspect Oriented Program, 􁶎􀝻(􀷜􁶎)􀚔􁶎􁌱􁖫􁑕;Filter(􁬦􁄁􀢏) 􀔞􀸎􀓞􁐿
AOP. AOP 􀸎􀓞􁐿􀷛􁌱􀷜􁀩􁦞, 􀸎􀩒􀖃􁕹 OOP(Object-Oriented
Programming, 􁶎􀝻􀩒􁨝􁖫􁑕) 􁌱􁤑􊧌. AOP 􁌱 􀔆􁥝􁖫􁑕􀩒􁨝􀸎􀚔􁶎
(aspect), 􁘒􀚔􁶎􀽜􀣘􀛸􀽞􀚔􀙉􁀳􁅩.􀝢􀕦􀔈􀖺􁭗􁬦􀔪􀛓􁧔􀸁.
IOC: Invert Of Control, 􀴴􀚫􀝍􁫨. 􀔞􀱮􀔅 DI(􀗁􁩢􁀳􀙁)􀙌􀯏􀰮􀸎􀝍􁫨􁩒􁃠􁞴
􀝐􁌱􀷜􀝻. 􀖃􁕹􁌱􁩒􁃠􀺱􀲤􀷜􀭗􁥝􀿢􁕟􀕯􀝻􀨻􀢏􀝎􁩸􁧗􀿢􀺱􀲤􁩒􁃠.􀖢􀔅􀢧
􀬫, 􀨻􀢏􁭇􀷸􁌱􁬬􀢧􁩒􁃠. 􁘒􀬫􁊠􀔧 IOC 􀔏􀝸, 􀚞􀸎􀨻􀢏􀔆􀛖􀣈􀩙􁩒􁃠􀴵􁭆
􁕳􀨙􀲅􁓕􁉘􁌱􁕟􀕯,􁕟􀕯􀲅􁥝􀘉􁌱􀕐􀸎􁭌􀳠􀓞􁐿􀝳􁭇􁌱􀷜􀭗􀹶􀴳􀝑􁩒􁃠. 􁬯
􁐿􁤈􀔅􀔞􁤩􁑍􀔅􀺱􀲤􁌱􁤩􀛖􀭵􀭗
28􀌵􀣁 Spring 􀓾􀦇􀖜􁯈􁗝 Bean ?
Bean 􁌱􁯈􁗝􀷜􀭗: 􁭗􁬦􀙂􁔄􀝷(􀝍􀩘)􀌵􁭗􁬦􀫡􀜯􀷜􁀩(􁶉􀮾􀫡􀜯􀷜􁀩 & 􀨫􀖺
􀫡􀜯􀷜􁀩)􀌵FactoryBean
29􀌵IOC 􀨻􀢏􀩒 Bean 􁌱􁊞􀞸􀞮􀹗:
1. 􁭗􁬦􀺅􁭜􀢏􀱲􀫡􀜯􀷜􁀩􀚠􀭌 Bean 􀨫􀖺
2. 􀔅 Bean 􁌱􀪂􀯔􁦡􁗝􊧊􀞾􀩒􀙌􀕜 Bean 􁌱􀭚􁊠
3. 􀩙 Bean 􀨫􀖺􀖃􁭓􁕳 Bean 􀝸􁗝􀥒􁉘􀢏􁌱 postProcessBeforeInitialization
􀷜􁀩
4. 􁧣􁊠 Bean 􁌱􀚡􀦤􀛸􀷜􁀩(init-method)
5. 􀩙 Bean 􀨫􀖺􀖃􁭓􁕳 Bean 􀝸􁗝􀥒􁉘􀢏􁌱 postProcessAfterInitialization
􀷜􁀩
6. Bean 􀝢􀕦􀖵􁊠􀔧
7. 􀭮􀨻􀢏􀙉􁳮􀷸, 􁧣􁊠 Bean 􁌱􁲀􀾪􀷜􁀩(destroy-method)
4.2 SpringMVC􁶎􁦶􀷆􁉘
1􀌵􀕋􀔍􀸎 SpringMvc?
SpringMvc 􀸎 spring 􁌱􀓞􀓻􀽜􀣘􀒅􀤚􀔭 MVC 􁌱􀓞􀓻􀻛􀺝􀒅􀷫􁵱􀓾􁳵􀷆􀝳
􀩶􀹶􀷆􀝳􀌶
2􀌵Spring MVC 􁌱􀕽􁅩:
1.􀨙􀸎􀤚􀔭􁕟􀕯􀲦􀹞􁌱.􀙂􁮱􁌱􀬫􁊠􀩒􁨝,􀷫􁦞􀴴􀚫􀢏􀞾􁥤􀢶,􁬮􀸎􀓱􀛓􀩒􁨝
􀔏􁔄􁌱􁮷􀸎 java 􁕟􀕯.􀬚􀓬􀞾 Spring 􀵉􀗀􁌱􀙌􀕜􀤚􁏐􁕮􀺅􁔲􀩂􁵞􀱮.
2.􀓧􀗁􁩢􀔭 Servlet API(􁍓􀺽􁡱􀸎􀦇􀾌,􀖕􀸎􀣁􀨫􁈿􁌱􀷸􀗲􁏟􀨫􀸎􀗁􁩢􀔭
Servlet 􁌱)
3.􀝢􀕦􀕱􀰺􀖵􁊠􀝱􁐿􁥤􀢶􀲦􀹞,􁘒􀓧􀕐􀕐􀩴􁴴􀔭 JSP
4.􀶪􀳮􀝱􁐿􁧗􀿢􁩒􁃠􁌱􀸉􀩘􁒽􁊼
5.􀨙􀬫􀸎􀸃􀔭􀲘􀪀􁌱
3􀌵SpringMVC 􀫡􀖢􀜻􁉘?
1.􀨮􀲁􁒒􀝎􁭆􁧗􀿢􀚩 DispatcherServlet
2.DispatcherServlet 􀺱􁧃 handlerMapping 􀲤􀚩􀥒􁉘􁧗􀿢􁌱 Controller
3.Controller 􁧣􁊠􀓱􀛓􁭦􁬋􀝸􀒅􁬬􀢧 ModelAndView
4.DispatcherServlet 􀺱􁧃 ModelAndView􀒅􀲤􀚩􀳰􀨧􁥤􀢶
5.􁥤􀢶􀩙􁕮􀺎􁬬􀢧􀚩􀨮􀲁􁒒
4􀌵SpringMVC 􁁞􁑕?
1.􁊠􀲁􀝎􁭆􁧗􀿢􁛗􀚹􁒒􀴴􀚫􀢏 DispatcherServlet􀌶
2.DispatcherServlet 􀶭􀚩􁧗􀿢􁧣􁊠 HandlerMapping 􀥒􁉘􀢏􀸉􀩘􀢏􀌶
3.􀥒􁉘􀢏􀸉􀩘􀢏􀲤􀚩􀙍􀖛􁌱􀥒􁉘􀢏(􀝢􀕦􀻑􀴝 xml 􁯈􁗝􀌵􁀳􁥴􁬰􁤈􀺱􀲤)􀒅􁊞
􀱮􀥒􁉘􀢏􀩒􁨝􀝊􀥒􁉘􀢏􀳝􀱼􀢏(􀦇􀺎􀹍􀚞􁊞􀱮)􀓞􀬚􁬬􀢧􁕳
DispatcherServlet􀌶
4.DispatcherServlet 􁧣􁊠 HandlerAdapter 􀥒􁉘􀢏􁭇􁯈􀢏􀌶
5.HandlerAdapter 􁕪􁬦􁭇􁯈􁧣􁊠􀙍􀖛􁌱􀥒􁉘􀢏(Controller􀒅􀔞􀝞􀝸􁒒􀴴􀚫
􀢏)􀌶
6.Controller 􀲗􁤈􀨠􀱮􁬬􀢧 ModelAndView􀌶
7.HandlerAdapter 􀩙 controller 􀲗􁤈􁕮􀺎 ModelAndView 􁬬􀢧􁕳
DispatcherServlet􀌶
8.DispatcherServlet 􀩙 ModelAndView 􀖃􁕳 ViewReslover 􁥤􀢶􁥴􀺉􀢏􀌶
9.ViewReslover 􁥴􀺉􀝸􁬬􀢧􀙍􀖛 View􀌶
10.DispatcherServlet 􀻑􀴝 View 􁬰􁤈􁃉􀺧􁥤􀢶(􀜨􀩙􀽜􀣳􀷄􀴝􀤴􊧌􁛗􁥤􀢶
􀓾)􀌶
11.DispatcherServlet 􀟥􀬫􁊠􀲁􀌶
5􀌵SpringMvc 􁌱􀴴􀚫􀢏􀸎􀓧􀸎􀜔􀖺􀽜􀭗,􀦇􀺎􀸎,􀹍􀕋􀔍􁳯􁷌,􀯆􀔍􁥴􀙬?
􀸎􀜔􀖺􀽜􀭗,􀲅􀕦􀣁􀥚􁕚􁑕􁦢􁳯􁌱􀷸􀗲􀹍􁕚􁑕􀨞􀙂􁳯􁷌,􀓧􁥝􁊠􀝶􀾍,􀕿􀭽􀟥
􀯔􁚆􁌱,􁥴􀙬􀷜􀻜􀸎􀣁􀴴􀚫􀢏􁯾􁶎􀓧􁚆􀙟􀨁􀾧􀌶
6􀌵􀦇􀺎􀖦􀔞􁊠􁬦 struts2.􁓌􀜔􀕕􁕨􀓥 springMVC 􀞾 struts2 􁌱􀜄􀚦􀹍􀟺
􀔶?
1.springmvc 􁌱􀙁􀝗􀸎􀓞􀓻 servlet 􀜨􀚹􁒒􀴴􀚫􀢏􀒅􁘒 struts2 􀙁􀝗􀸎􀓞􀓻
filter 􁬦􁡤􀢏􀌶
2.springmvc 􀸎􀤚􀔭􀷜􁀩􀭏􀝎(􀓞􀓻 url 􀩒􀬫􀓞􀓻􀷜􁀩)􀒅􁧗􀿢􀝇􀷄􀖃􁭓􀚩􀷜
􁀩􁌱􀭵􀝇􀒅􀝢􀕦 􁦡􁦇􀔅􀜔􀖺􀱲􀥚􀖺(􀭌􁦓􀜔􀖺)􀒅struts2 􀸎􀤚􀔭􁔄􀭏􀝎􀒅􀖃
􁭓􀝇􀷄􀸎􁭗􁬦􁔄􁌱􀪂􀯔􀒅􀝝􁚆􁦡 􁦇􀔅􀥚􀖺􀌶
3.Struts 􁯻􁊠􊧊􀺾􀨂􀘙􁧗􀿢􀞾􀟥􀬫􁌱􀷄􀴝􀒅􁭗􁬦 OGNL 􀨂􀝐􀷄􀴝􀒅
springmvc 􁭗􁬦􀝇􀷄􁥴􀺉􀢏􀸎􀩙 request 􁧗􀿢􀙖􀨻􁥴􀺉􀒅􀬚􁕳􀷜􁀩􀭵􀝇􁩙
􊧊􀒅􀩙􀷄􀴝􀞾􁥤􀢶􀩗􁤰􀱮 ModelAndView 􀩒􁨝􀒅􀹋􀝸􀝈􀩙 ModelAndView
􀓾􁌱􀽜􀣳􀷄􀴝􁭗􁬦 reques 􀤒􀖃􁬌􀚩􁶭􁶎􀌶Jsp 􁥤􀢶􁥴􀺉􀢏􁼕􁦊􀖵􁊠 jstl􀌶
7􀌵SpingMvc 􀓾􁌱􀴴􀚫􀢏􁌱􁀳􁥴􀓞􁛱􁊠􁮎􀓻,􀹍􁀌􀹍􀚦􁌱􁀳􁥴􀝢􀕦􀹊􀕤?
􀓞􁛱􁊠@Conntroller 􁀳􁥴,􁤒􁐏􀸎􁤒􁈿􀩶,􀓧􁚆􁊠􁊠􀚦􁌱􁀳􁥴􀕤􀹊􀌶
8􀌵 @RequestMapping 􁀳􁥴􁊠􀣁􁔄􀓤􁶎􀹍􀕋􀔍􀖢􁊠?
􀸎􀓞􀓻􁊠􀹶􀥒􁉘􁧗􀿢􀣈􀣎􀸉􀩘􁌱􁀳􁥴􀒅􀝢􁊠􀔭􁔄􀱲􀷜􁀩􀓤􀌶􁊠􀔭􁔄􀓤􀒅􁤒
􁐏􁔄􀓾􁌱􀲅􀹍􀟥􀬫􁧗􀿢􁌱􀷜􁀩􁮷􀸎􀕦􁧆􀣈􀣎􀖢􀔅􁆿􁪠􀮆􀌶
9􀌵􀯆􀔍􀻏􀲩􀺤􀓻􁧗􀿢􀸉􀩘􀚩􁇙􀨧􁌱􀷜􁀩􀓤􁶎?
􁒼:􁍗􀴳􀣁􀷜􁀩􀓤􁶎􀛒􀓤􁀳􁥴@RequestMapping,􀬚􀓬􀣁􁬯􀓻􁀳􁥴􁯾􁶎􀙟􀓤
􁥝􀳝􀱼􁌱􁪠􀮆
10􀌵􀦇􀺎􀣁􀳝􀱼􁧗􀿢􀓾,􀱯􀰮􀳝􀱼 get 􀷜􀭗􀵉􀔻􁌱􀷜􁀩,􀯆􀔍􁯈􁗝?
􀝢􀕦􀣁@RequestMapping 􁀳􁥴􁯾􁶎􀛒􀓤 method=RequestMethod.GET
11􀌵􀯆􀔍􀻏􀣁􀷜􁀩􁯾􁶎􀮑􀚩 Request,􀱲􁘏 Session?
􁍗􀴳􀣁􀷜􁀩􁌱􀭵􀝇􀓾􀥍􀸁 request,SpringMvc 􀩪􁛔􀛖􀲩 request 􀩒􁨝􀖃􀙁
12􀌵􀱯􀰮􀣁􀳝􀱼􁌱􀷜􁀩􁯾􁶎􀮑􀚩􀕗􀚹􀝣􀖃􀙁􁌱􀝇􀷄,􀯆􀔍􀮑􀚩?
􁒼:􁍗􀴳􀣁􀭵􀝇􁯾􁶎􀥍􀸁􁬯􀓻􀝇􀷄􀩪􀝢􀕦,􀖕􀮠􁶳􀝷􀨁􀞾􀖃􁬦􀹶􁌱􀝇􀷄􀓞􀻏
13􀌵􀦇􀺎􀚹􀝣􀹍􀮉􀥚􀓻􀝇􀷄􀖃􀙁,􀬚􀓬􁬯􀔶􀝇􀷄􁮷􀸎􀓞􀓻􀩒􁨝􁌱,􁮎􀔍􀯆􀔍
􀻏􀮳􁭛􀮑􀚩􁬯􀓻􀩒􁨝?
􁍗􀴳􀣁􀷜􁀩􀓾􀥍􀸁􁬯􀓻􀩒􁨝,SpringMvc 􀩪􁛔􀛖􀕿􀲩􀪂􀯔􁩙􊧊􀚩􁬯􀓻􀩒􁨝􁯾
􁶎􀌶
14􀌵SpringMvc 􀓾􀚍􀷄􁌱􁬬􀢧􊧊􀸎􀕋􀔍?
􁒼:􁬬􀢧􊧊􀝢􀕦􀹍􀮉􀥚􁔄􀣳,􀹍 String, ModelAndView,􀭮􀓞􁛱􁊠 String 􀾲􁫾
􀦅􀌶
15􀌵SpringMVC 􀯆􀔍􀻏􁦡􀨧􁯿􀨧􀝻􀞾􁫨􀝎􁌱?
􀣁􁬬􀢧􊧊􀚹􁶎􀛒"forward:"􀩪􀝢􀕦􁦏􁕮􀺎􁫨􀝎,􁦅􀦇"forward:user.do?
name=method4" 􀣁􁬬􀢧􊧊􀚹􁶎􀛒"redirect:"􀩪􀝢􀕦􁦏􁬬􀢧􊧊􁯿􀨧􀝻,􁦅
􀦇 "redirect:http://www.baidu.com"
16􀌵SpringMvc 􁊠􀕋􀔍􀩒􁨝􀕗􀝸􀝣􀝻􀚹􀝣􀖃􁭓􀷄􀴝􁌱?
􁒼:􁭗􁬦 ModelMap 􀩒􁨝,􀝢􀕦􀣁􁬯􀓻􀩒􁨝􁯾􁶎􁊠 put 􀷜􁀩,􀲩􀩒􁨝􀛒􀚩􁯾􁶎,
􀚹􀝣􀩪􀝢􀕦􁭗􁬦 el 􁤒􁬡􀭗􀳭􀚩􀌶
17􀌵SpringMvc 􀓾􀹍􀓻􁔄􀲩􁥤􀢶􀞾􀷄􀴝􁮷􀝳􀬚􁌱􀓞􁩸􁌱,􀝞􀕋􀔍?
􀝞 ModelAndView􀌶
18􀌵􀯆􀔍􀻏􀲩 ModelMap 􁯾􁶎􁌱􀷄􀴝􀶱􀙁 Session 􁯾􁶎?
􀝢􀕦􀣁􁔄􀓤􁶎􀛒􀓤@SessionAttributes 􁀳􁥴,􁯾􁶎􀛱􀞌􁌱􀨁􁒧􀔀􀩪􀸎􁥝􀶱􀙁
session 􁯾􁶎􁌱 key
19􀌵SpringMvc 􀯆􀔍􀞾 AJAX 􁍘􀔰􁧣􁊠􁌱?
􁭗􁬦 Jackson 􀻛􀺝􀩪􀝢􀕦􀲩 Java 􁯾􁶎􁌱􀩒􁨝􁍗􀴳􁫨􀛸􀱮 Js 􀝢􀕦􁦩􀚦􁌱
Json 􀩒􁨝􀌶􀙍􀖛􀾍􁹈􀦇􀓥 :
1.􀛒􀙁 Jackson.jar
2.􀣁􁯈􁗝􀷈􀕯􀓾􁯈􁗝 json 􁌱􀸉􀩘
3.􀣁􀴳􀝑 Ajax 􀷜􁀩􁯾􁶎􀝢􀕦􁍗􀴳􁬬􀢧 Object,List 􁒵,􀖕􀷜􁀩􀚹􁶎􁥝􀛒􀓤
@ResponseBody 􁀳􁥴
20􀌵􀭮􀓞􀓻􀷜􁀩􀝻 AJAX 􁬬􀢧􁇙􀾛􀩒􁨝,􁦅􀦇 Object,List 􁒵,􁵱􁥝􀘉􀕋􀔍
􀥒􁉘?
􁥝􀛒􀓤@ResponseBody 􁀳􁥴
21􀌵SpringMvc 􁯾􁶎􀳝􀱼􀢏􀸎􀯆􀔍􀙟􁌱
􀹍􀓷􁐿􀙟􁀩,􀓞􁐿􀸎􀨫􁈿􀴳􀝗,􀝚􀥘􀓞􁐿􀸎􁖀􀲥􁭇􁯈􀢏􁔄,􁆐􀝸􀣁 SpringMvc
􁌱􁯈􁗝􀷈􀕯􀓾 􁯈􁗝􀳝􀱼􀢏􀜨􀝢:
<!-- 􁯈􁗝 SpringMvc 􁌱􀳝􀱼􀢏 --> <mvc:interceptors>
<!-- 􁯈􁗝􀓞􀓻􀳝􀱼􀢏􁌱 Bean 􀩪􀝢􀕦􀔧 􁼕􁦊􀸎􀩒􀲅􀹍􁧗􀿢􁮷􀳝􀱼 -->
<bean id="myInterceptor" class="com.et.action.MyHandlerInterce
ptor"></bean> <!-- 􀝝􁰒􀩒􁮱􀚓􁧗􀿢􀳝􀱼 -->
<mvc:interceptor>
<mvc:mapping path="/modelMap.do" />
<bean class="com.et.action.MyHandlerInterceptorAdapter" /> </m
vc:interceptor>
</mvc:interceptors>
22􀌵􁦖􀓥 SpringMvc 􁌱􀲗􁤈􁁞􁑕
􁔮􁕹􀞐􀛖􁌱􀷸􀗲􀻑􀴝􁯈􁗝􀷈􀕯􀚠􀭌spring􁌱􀨻􀢏, 􁸒􀘶􀸎􀝎􁭆http􁧗􀿢􀚩􀻐
􀮞􀴴􀚫􀢏 disPatherServlet􀒅spring 􀨻􀢏􁭗􁬦􀸉􀩘􀢏􀝄􀩔􀲤􀓱􀛓􀴴􀚫􀢏􀒅􀖵
􁊠􁭇􁯈􀢏􀲤􀚩􁍘􀬫􁌱􀓱􀛓􁔄􀒅􀣁􁬰􀓱􀛓􁔄􀷸􁬰􁤈􀷄􀴝􀩗􁤰􀒅􀣁􀩗􁤰􀚹􀝢􁚆
􀕿􁁿􀝊􀚩􁔄􀣳􁫨􀴘􀒅􀲗􁤈􀨠􀓱􀛓􁔄􀝸􀖵􁊠 ModelAndView 􁬰􁤈􁥤􀢶􁫨􀝎􀒅
􀷄􀴝􀶱􀣁 model 􀓾􀒅􁊠 map 􀖃􁭓􀷄􀴝􁬰􁤈􁶭􁶎􀸔􁐏􀌶
4.3􀌵MyBatis􁶎􁦶􀷆􁉘
1􀌵􀕋􀔍􀸎 MyBatis?
MyBatis 􀸎􀓞􀓻􀝢􀕦􁛔􀨧􀔎 SQL􀌵􀨂􀘙􁬦􁑕􀞾􁹛􁕆􀸉􀩘􁌱􀳮􀔋􀩶􀻛􀺝􀌶
2􀌵􁦖􀓥 MyBatis 􁌱􁖨􀨂
MyBatis 􁌱􁖨􀨂􀚓􀔅􀓞􁕆􁖨􀨂􀞾􀔫􁕆􁖨􀨂,􀓞􁕆􁖨􀨂􀶱􀣁 session 􁯾􁶎,􁼕􁦊
􀩪􀹍,􀔫􁕆􁖨 􀨂􀶱􀣁􀨙􁌱􀞸􀝷􁑮􁳵􁯾,􁼕􁦊􀸎􀓧􀲑􀭏􁌱,􀖵􁊠􀔫􁕆􁖨􀨂􀪂􀯔􁔄
􁵱􁥝􀨫􁈿 Serializable 􀬧􀚜􀛸􀴳􀝗(􀝢􁊠􀹶􀗛􀨂􀩒􁨝􁌱􁇫􀮾),􀝢􀣁􀨙􁌱􀸉􀩘􀷈
􀕯􀓾􁯈􁗝 <cache/>
3􀌵Mybatis 􀸎􀦇􀖜􁬰􁤈􀚓􁶭􁌱?􀚓􁶭􀵊􀕯􁌱􀜻􁉘􀸎􀕋􀔍?
1.Mybatis 􀖵􁊠 RowBounds 􀩒􁨝􁬰􁤈􀚓􁶭􀒅􀔞􀝢􀕦􁍗􀴳􁖫􀙟 sql 􁈿􀚓􁶭􀒅
􀔞􀝢􀕦􀖵􁊠 Mybatis 􁌱􀚓􁶭􀵊􀕯􀌶
2.􀚓􁶭􀵊􀕯􁌱􀜻􁉘:􀨫􁈿 Mybatis 􀵉􀗀􁌱􀴳􀝗􀒅􀨫􁈿􁛔􀨧􀔎􀵊􀕯􀒅􀣁􀵊􀕯􁌱
􀳝􀱼􀷜􁀩􀙖􀳝􀱼􀮇􀲗􁤈􁌱 sql􀒅􁆐􀝸􁯿􀙟 sql􀌶
􀔈􀖺:
select * from student
􀳝􀱼 sql 􀝸􁯿􀙟􀔅:
select t.* from (select * from student)t limit 0􀒅10
4􀌵􁓌􁬿 Mybatis 􁌱􀵊􀕯􁬩􁤈􀜻􁉘􀒅􀕦􀝊􀦇􀖜􁖫􀙟􀓞􀓻􀵊􀕯?
1.Mybatis 􀕐􀝢􀕦􁖫􀙟􁰒􀩒 ParameterHandler􀌵ResultSetHandler􀌵
StatementHandler􀌵 Executor 􁬯 4 􁐿􀴳􀝗􁌱􀵊􀕯􀒅Mybatis 􁭗􁬦􀛖􀮾􀕤
􁉘􀒅􀔅􁵱􁥝􀳝􀱼􁌱􀴳􀝗􁊞􀱮􀕤􁉘􀩒􁨝􀕦􀨫 􁈿􀴳􀝗􀷜􁀩􀳝􀱼􀛑􁚆􀒅􀾯􀭮􀲗􁤈
􁬯 4 􁐿􀴳􀝗􀩒􁨝􁌱􀷜􁀩􀷸􀒅􀩪􀕿􁬰􀙁􀳝􀱼􀷜􁀩􀒅􀙍􀖛􀩪􀸎
InvocationHandler 􁌱 invoke()􀷜􁀩􀒅􀭮􁆐􀒅􀝝􀕿􀳝􀱼􁮎􀔶􀖦􀳰􀨧􁵱􁥝􀳝􀱼
􁌱􀷜􁀩􀌶
2.􀨫􁈿 Mybatis 􁌱 Interceptor 􀴳􀝗􀬚􀥔􀙟 intercept()􀷜􁀩􀒅􁆐􀝸􀣁􁕳􀵊􀕯
􁖫􀙟􁀳􁥴􀒅􀳰􀨧􁥝􀳝􀱼􀟺􀓞􀓻􀴳􀝗􁌱􀟺􀔶􀷜􁀩􀜨􀝢􀒅􁦕􀖘􀒅􀚦􀮫􀔧􀣁􁯈􁗝
􀷈􀕯􀓾􁯈􁗝􀖦􁖫􀙟􁌱􀵊􀕯􀌶
5􀌵Mybatis 􀛖􀮾 sql 􀸎􀘉􀕋􀔍􁌱?􁮷􀹍􀟺􀔶􀛖􀮾 sql?􁚆􁓌􁬿􀓞􀓥􀛖􀮾 sql
􁌱􀲗􁤈􀜻􁉘􀞀?
1.Mybatis 􀛖􀮾 sql 􀝢􀕦􁦏􀱯􀕪􀣁 Xml 􀸉􀩘􀷈􀕯􀙖􀒅􀕦􀺽􁓋􁌱􀭵􀭗􁖫􀙟􀛖
􀮾 sql􀒅􀨠􀱮􁭦􁬋 􀚣􀷙􀞾􀛖􀮾􀳪􀴳 sql 􁌱􀛑􁚆􀌶
2.Mybatis 􀵉􀗀􀔧 9 􁐿􀛖􀮾 sql 􀺽􁓋:
trim|where|set|foreach|if|choose|when|otherwise|bind􀌶
3.􀙌􀲗􁤈􀜻􁉘􀔅􀒅􀖵􁊠 OGNL 􀕗 sql 􀝇􀷄􀩒􁨝􀓾􁦇􁓒􁤒􁬡􀭗􁌱􊧊􀒅􀻑􀴝􁤒
􁬡􀭗􁌱􊧊􀛖􀮾􀳪􀴳 sql􀒅􀕦􀾌􀹶􀨠􀱮􀛖􀮾 sql 􁌱􀛑􁚆􀌶
6􀌵#{}􀞾${}􁌱􀜄􀚦􀸎􀕋􀔍?
1. #{} 􀸎􁶼􁖫􁦲􀥒􁉘􀒅 ${} 􀸎􀨁􁒧􀔀􀹊􀴘􀌶
2.Mybatis 􀣁􀥒􁉘#{}􀷸􀒅􀕿􀩙 sql 􀓾􁌱#{}􀹊􀴘􀔅?􀝩􀒅􁧣􁊠
PreparedStatement 􁌱 set 􀷜􁀩
􀹶􁩙􊧊;
3.Mybatis 􀣁􀥒􁉘 ${} 􀷸􀒅􀩪􀸎􀲩 ${} 􀹊􀴘􀱮􀝒􁰁􁌱􊧊􀌶
4.􀖵􁊠 #{} 􀝢􀕦􀹍􀶴􁌱􁴠􀾊 SQL 􁀳􀙁􀒅􀵉􁹛􁔮􁕹􀨞􀙂􀯔􀌶
7􀌵􀔅􀕋􀔍􁧔 Mybatis 􀸎􀜎􁛔􀛖 ORM 􀸉􀩘􀫡􀙍?􀨙􀓨􀙂􁛔􀛖􁌱􀜄􀚦􀣁􀟺
􁯾?
Hibernate 􀪂􀔭􀙂􁛔􀛖 ORM 􀸉􀩘􀫡􀙍􀒅􀖵􁊠 Hibernate 􀺱􁧃􀙉􁘶􀩒􁨝􀱲􁘏
􀙉􁘶􁵞􀝳􀩒􁨝􀷸􀒅􀝢􀕦􀻑􀴝􀩒􁨝􀙉􁔮􀽜􀣳􁍗􀴳􁞴􀝐􀒅􀲅􀕦􀨙􀸎􀙂􁛔􀛖􁌱􀌶
􁘒 Mybatis 􀣁􀺱􁧃􀙉􁘶􀩒􁨝􀱲􀙉􁘶􁵞􀝳􀩒􁨝􀷸􀒅􁵱􁥝􀲋􀛖􁖫􀙟 sql 􀹶􀨠
􀱮􀒅􀲅􀕦􀒅􁑍􀔏􀔅􀜎􁛔􀛖 ORM 􀸉􀩘􀫡􀙍􀌶
8􀌵Mybatis 􀸎􀞈􀶪􀳮􀭊􁬴􀛒􁫹?􀦇􀺎􀶪􀳮􀒅􀨙􁌱􀨫􁈿􀜻􁉘􀸎􀕋􀔍?
1.Mybatis 􀕐􀶪􀳮 association 􀙉􁘶􀩒􁨝􀞾 collection 􀙉􁘶􁵞􀝳􀩒􁨝􁌱􀭊􁬴
􀛒􁫹􀒅association 􀳰􁌱􀩪􀸎􀓞􀩒􀓞􀒅collection 􀳰􁌱􀩪􀸎􀓞􀩒􀥚􀺱􁧃􀌶􀣁
Mybatis 􁯈􁗝􀷈􀕯􀓾􀒅􀝢􀕦􁯈􁗝􀸎􀞈 􀞐􁊠􀭊􁬴􀛒􁫹
lazyLoadingEnabled=true|false 􀌶
2.􀨙􁌱􀜻􁉘􀸎􀒅􀖵􁊠 CGLIB 􀚠􀭌􁍓􀺽􀩒􁨝􁌱􀕤􁉘􀩒􁨝􀒅􀭮􁧣􁊠􁍓􀺽􀷜􁀩
􀷸􀒅􁬰􀙁􀳝􀱼􀢏􀷜􁀩􀒅􀾲􀦇􁧣􁊠 a.getB().getName() 􀒅􀳝􀱼􀢏 invoke()
􀷜􁀩􀝎􁈿 a.getB()􀸎 null 􊧊􀒅􁮎􀔍􀩪􀕿􀜔 􁇿􀝎􁭆􀔪􀘶􀗛􀨂􀦅􁌱􀺱􁧃􀙉􁘶 B
􀩒􁨝􁌱 sql􀒅􀲩 B 􀺱􁧃􀓤􀹶􀒅􁆐􀝸􁧣􁊠 a.setB(b) 􀒅􀔭􀸎 a 􁌱 􀩒􁨝 b 􀪂
􀯔􀩪􀹍􊧊􀔧􀒅􀴳􁍳􀨠􀱮 a.getB().getName() 􀷜􁀩􁌱􁧣􁊠􀌶􁬯􀩪􀸎􀭊􁬴
􀛒􁫹􁌱􀤚􀹜􀜻􁉘􀌶
9􀌵MyBatis 􀓨 Hibernate 􀹍􀟺􀔶􀓧􀝶?
1.Mybatis 􀞾 hibernate 􀓧􀝶􀒅􀨙􀓧􀨠􀙂􀸎􀓞􀓻 ORM 􀻛􀺝􀒅􀢩􀔅 MyBatis
􁵱􁥝􁑕􀬧􀞧􁛔􀫩􁖫􀙟 Sql 􁧍􀝙􀒅􀓧􁬦 mybatis 􀝢􀕦􁭗􁬦 XML 􀱲􁀳􁥴􀷜􀭗􁅎
􁁚􁯈􁗝􁥝􁬩􁤈􁌱 sql 􁧍􀝙􀒅􀬚􀩙 java 􀩒􁨝􀞾 sql 􁧍􀝙􀸉􀩘􁊞􀱮􀹋􁕣􀲗􁤈􁌱
sql􀒅􀹋􀝸􀩙 sql 􀲗􁤈􁌱􁕮􀺎􀙚􀸉􀩘􁊞􀱮 java 􀩒􁨝􀌶
2.Mybatis 􀨍􀔟􁳪􀽑􀖗􀒅􁓌􀜔􀸃􀨍􀒅􁑕􀬧􀞧􁍗􀴳􁖫􀙟􀜻􁊞􀮾 sql􀒅􀝢􀓸􀻒􀴴
􀚫 sql 􀲗􁤈􀯔 􁚆􀒅􁅎􁁚􀬶􁹛􀒅􁶋􀬉􁭇􀝳􀩒􀙉􁔮􀷄􀴝􀽜􀣳􁥝􀿢􀓧􁹛􁌱􁫫􀕯􀭏
􀝎􀒅􀖺􀦇􀔰􁘶􁗑􁫫􀕯􀌵􀕴􀓱􁬩􁟠􁔄􁫫􀕯􁒵􀒅􀢩􀔅􁬯􁔄􁫫􀕯􁵱􀿢􀝒􀛸􁷇􁔺􀒅
􀓞􀖕􁵱􀿢􀝒􀛸􁥝􀿢􀱮􀺎􁬌􀚊􁬥􁭛􀌶􀖕􀸎􁅎􁁚􁌱􀚹􀵉􀸎 mybatis 􀷫􁀩􀘉􀚩􀷄
􀴝􀬪􀷫􀙉􀯔􀒅􀦇􀺎􁵱􁥝􀨫􁈿􀶪􀳮􀥚􁐿􀷄􀴝􀬪􁌱􁫫􀕯􀚞􁵱􁥝􁛔􀨧 􀔎􀥚􀥺 sql
􀸉􀩘􀷈􀕯􀒅􀫡􀖢􁰁􀥟􀌶
3.Hibernate 􀩒􁨝/􀙉􁔮􀸉􀩘􁚆􀛎􀭩􀒅􀷄􀴝􀬪􀷫􀙉􀯔􀦅􀒅􀩒􀔭􀙉􁔮􀽜􀣳􁥝􀿢
􁹛􁌱􁫫􀕯(􀖺􀦇􁵱􀿢􀢴􀨧􁌱􀨧􀚫􀛸􁫫􀕯)􀦇􀺎􁊠 hibernate 􀭏􀝎􀝢􀕦􁜓􁍜􀮉􀥚
􀕤􁎱􀒅􀵉􁹛􀶴􁈲􀌶􀖕􀸎 Hibernate 􁌱􁗌􁅩􀸎􀨍􀔟􁳪􀽑􁹛􀒅􁥝􁔜􁭗􁳪􀽑􀹅
􁹛􀒅􁘒􀓬􀯆􀔍􁦡􁦇 O/R 􀸉􀩘􀒅􀣁􀯔􁚆􀞾􀩒􁨝􀽜􀣳􀔏􁳵􀦇􀖜􀹦􁤍􀒅􀕦􀝊􀯆􀻏
􁊠􀦅 Hibernate 􁵱􁥝􀙍􀹍􀮉􀭩􁌱􁕪􁸵􀞾􁚆􀛎􀲍􁤈􀌶 􀯛􀔏􀒅􀳲􁆙􁊠􀲁􁌱􁵱􀿢
􀣁􀹍􁴴􁌱􁩒􁃠􁈾􀤹􀓥􀝝􁥝􁚆􀘉􀚊􁖌􀲷􀯔􀌵􀲘􀪀􀯔􁜉􀦅􁌱􁫫􀕯􀺝􀺅􁮷􀸎􀦅􀺝
􀺅􀒅􀲅􀕦􀻛􀺝􀝝􀹍􁭇􀝳􀲍􀸎􀹋􀦅􀌶
10􀌵MyBatis 􁌱􀦅􀥒􀸎􀕋􀔍?
1.MyBatis 􀲩 sql 􁧍􀝙􀕗 Java 􁃠􁑕􀬧􀓾􁇿􁒈􀚊􀹶􀒅􀶱􀣁􀜔􁇿􁌱 XML 􀷈􀕯􀓾
􁖫􀙟􀒅􁕳􁑕􀬧􁌱􁖌􀲷􀬃􀹶􀔧􀮉􀥟􀗎􀚥􀌶
2.MyBatis 􀩗􁤰􀔧􀬬􀩶 JDBC API 􁌱􁧣􁊠􁕡􁜓􀒅􀬚􁚆􁛔􀛖􀩙􁕮􀺎􁵞􁫨􀴘􀱮
Java Bean 􀩒􁨝􀒅􀥟􀥟􁓌􀛸􀔧 Java 􀷄􀴝􀬪􁖫􁑕􁌱􁯿􀥔􀫡􀖢􀌶
3.􀢩􀔅 MyBatis 􁵱􁥝􁑕􀬧􀞧􁛔􀫩􀝄􁖫􀙟 sql 􁧍􀝙􀒅􁑕􀬧􀞧􀝢􀕦􁕮􀝳􀷄􀴝􀬪
􁛔􁫝􁌱􁇙􁅩􁅎􁁚 􀴴􀚫 sql 􁧍􀝙􀒅􀢩􀾌􁚆􀥜􀨫􁈿􀾲 Hibernate 􁒵􀙂􁛔􀛖 orm
􀻛􀺝􀹅􁹛􁌱􀺱􁧃􀶴􁈲􀒅􁚆􀥜􀨠􀱮􀥔􀹥􀺱􁧃􀌶
11􀌵􁓌􁬿 Mybatis 􁌱 Xml 􀸉􀩘􀷈􀕯􀞾 Mybatis 􀙖􁮱􀷄􀴝􁕮􀺅􀔏􁳵􁌱􀸉􀩘
􀙉􁔮?
Mybatis 􀩙􀲅􀹍 Xml 􁯈􁗝􀗞􀯳􁮷􀩗􁤰􀚩 All-In-One 􁯿􁰁􁕆􀩒􁨝
Configuration 􀙖􁮱􀌶􀣁 Xml 􀸉􀩘􀷈􀕯􀓾􀒅 <parameterMap> 􀺽􁓋􀕿􁤩􁥴
􀺉􀔅 ParameterMap 􀩒􁨝􀒅􀙌􀾯􀓻􀧼􀘲􁔰􀕿 􁤩􁥴􀺉􀔅 ParameterMapping
􀩒􁨝􀌶 <resultMap> 􀺽􁓋􀕿􁤩􁥴􀺉􀔅 ResultMap 􀩒􁨝􀒅􀙌􀾯􀓻􀧼􀘲􁔰􀕿
􁤩􁥴􀺉􀔅 ResultMapping 􀩒􁨝􀌶􀾯􀓞􀓻 <select>􀌵<insert>􀌵
<update>􀌵<delete> 􀺽􁓋􀣐􀕿􁤩􁥴􀺉􀔅 MappedStatement 􀩒􁨝􀒅􀺽􁓋
􀙖􁌱 sql 􀕿􁤩􁥴􀺉􀔅 BoundSql 􀩒􁨝􀌶
12􀌵􀕋􀔍􀸎 MyBatis 􁌱􀴳􀝗􁕬􀨧,􀹍􀕋􀔍􀦅􀥒?
􀴳􀝗􀸉􀩘􀩪􀸎􀣁 MyBatis 􀓾􀕱􀰺􀨧􀔎􀴳􀝗,􁆐􀝸􀲩􀴳􀝗􁯾􁶎􁌱􀷜􁀩􀞾 SQL
􁧍􀝙􁕬􀨧,􀱯􀕪􁍗􀴳􁧣􁊠􀴳􀝗􀷜􁀩􀩪􀝢􀕦,􁬯􀻏􀾲􁩸􀜻􀹶􀔧 SqlSession 􀵉􀗀
􁌱􀷜􁀩􀱯􀕪􀝢􀕦􀹍􀹅􀛒􁅎􁁚􁌱􁭌 􀳠􀞾􁦡􁗝.
13􀌵􀴳􀝗􁕬􀨧􀹍􀙾􁐿􀨫􁈿􀷜􀭗,􀚓􀚦􀸎􀯆􀔍􀨫􁈿􁌱?
􀴳􀝗􁕬􀨧􀹍􀓷􁐿􀨫􁈿􀷜􀭗,􀓞􁐿􀸎􁭗􁬦􁀳􁥴􁕬􀨧,􀩪􀸎􀣁􀴳􀝗􁌱􀷜􁀩􀓤􁶎􀛒
􀓤 @Select@Update 􁒵􁀳􁥴􁯾􁶎􀛱􀞌 Sql 􁧍􀝙􀹶􁕬􀨧,􀝚􀥘􀓞􁐿􀩪􀸎􁭗􁬦
xml 􁯾􁶎􀙟 SQL 􀹶􁕬􀨧,􀣁􁬯􁐿􀰘􀙭􀓥,􁥝􀳰􀨧 xml 􀸉􀩘􀷈􀕯􁯾􁶎􁌱
namespace 􀮠􁶳􀔅􀴳􀝗􁌱􀙂􁪠􀮆􀝷.
14􀌵􀕋􀔍􀰘􀙭􀓥􁊠􁀳􁥴􁕬􀨧,􀕋􀔍􀰘􀙭􀓥􁊠 xml 􁕬􀨧?
􀭮 Sql 􁧍􀝙􀾲􁫾􁓌􀜔􀷸􀗲,􁊠􁀳􁥴􁕬􀨧;􀭮 SQL 􁧍􀝙􀾲􁫾􀥔􀹥􀷸􀗲,􁊠 xml 􁕬
􀨧,􀓞􁛱􁊠 xml 􁕬􀨧􁌱􀾲􁫾􀥚
15􀌵MyBatis 􀨫􁈿􀓞􀩒􀓞􀹍􀙾􁐿􀷜􀭗?􀙍􀖛􀯆􀔍􀶙􀖢􁌱?
􀹍􁘶􀝳􀺱􁧃􀞾􀫍􀥺􀺱􁧃,􁘶􀝳􀺱􁧃􀸎􀙾􀓻􁤒􁘶􀝳􀺱􁧃,􀝝􀺱􁧃􀓞􀽺,􁭗􁬦􀣁
resultMap 􁯾􁶎􁯈􁗝 association 􁜓􁅩􁯈􁗝􀓞􀩒􀓞􁌱􁔄􀩪􀝢􀕦􀨠􀱮;􀫍􀥺􀺱􁧃
􀸎􀘶􀺱􀓞􀓻􁤒,􀻑􀴝􁬯􀓻􁤒􁯾􁶎􁌱􁕮􀺎􁌱􀥘􁲫 id,􀝄􀙚􀝚􀥘􀓞􀓻􁤒􁯾􁶎􀺱􁧃
􀷄􀴝,􀔞􀸎􁭗􁬦 association 􁯈􁗝,􀖕􀝚􀥘􀓞􀓻􁤒􁌱􀺱􁧃􁭗􁬦 select 􀪂􀯔􁯈
􁗝􀌶
16􀌵Mybatis 􁚆􀲗􁤈􀓞􀩒􀓞􀌵􀓞􀩒􀥚􁌱􀙉􁘶􀺱􁧃􀞀?􁮷􀹍􀟺􀔶􀨫􁈿􀷜􀭗􀒅
􀕦􀝊􀨙􀕪􀔏􁳵􁌱􀜄􀚦?
􁚆􀒅Mybatis 􀓧􀕐􀝢􀕦􀲗􁤈􀓞􀩒􀓞􀌵􀓞􀩒􀥚􁌱􀙉􁘶􀺱􁧃􀒅􁬮􀝢􀕦􀲗􁤈􀥚􀩒
􀓞􀒅􀥚􀩒􀥚􁌱􀙉􁘶􀺱􁧃􀒅􀥚􀩒􀓞􀺱􁧃􀒅􀙌􀨫􀩪􀸎􀓞􀩒􀓞􀺱􁧃􀒅􀝝􁵱􁥝􀲩
selectOne()􀗥􀶯􀔅 selectList()􀜨􀝢;􀥚􀩒􀥚􀺱􁧃􀒅􀙌􀨫􀩪􀸎􀓞􀩒􀥚􀺱􁧃􀒅􀝝
􁵱􁥝􀲩 selectOne()􀗥􀶯􀔅 selectList()􀜨􀝢􀌶
􀙉􁘶􀩒􁨝􀺱􁧃􀒅􀹍􀓷􁐿􀨫􁈿􀷜􀭗􀒅􀓞􁐿􀸎􀜔􁇿􀝎􁭆􀓞􀓻 sql 􀝄􀺱􁧃􀙉􁘶􀩒
􁨝􀒅􁩙􁕳􀔆􀩒􁨝􀒅􁆐􀝸􁬬􀢧􀔆􀩒􁨝􀌶􀝚􀓞􁐿􀸎􀖵􁊠􀫍􀥺􀺱􁧃􀒅􀫍􀥺􀺱􁧃􁌱
􀞌􀔎􀔅􀖵􁊠 join 􀺱􁧃􀒅􀓞􁮱􀚓􀚜􀸎 A 􀩒􁨝􁌱􀪂􀯔􊧊􀒅􀝚􀥘􀓞􁮱􀚓􀚜􀸎􀙉􁘶
􀩒􁨝 B 􁌱􀪂􀯔􊧊􀒅􀦅􀥒􀸎􀝝􀝎􀓞􀓻 sql 􀺱􁧃􀒅􀩪􀝢􀕦􀲩􀔆􀩒􁨝􀞾􀙌􀙉􁘶􀩒
􁨝􀺱􀚊􀹶􀌶
17􀌵MyBatis 􁯾􁶎􁌱􀛖􀮾 Sql 􀸎􀯆􀔍􁦡􀨧􁌱?􁊠􀕋􀔍􁧍􁀩?
MyBatis 􁯾􁶎􁌱􀛖􀮾 Sql 􀓞􁛱􀸎􁭗􁬦 if 􁜓􁅩􀹶􀨫􁈿,􁭗􁬦 OGNL 􁧍􁀩􀹶􀨫
􁈿,􀖕􀸎􀦇􀺎􁥝􀙟􁌱􀨠􀷆,􀮠􁶳􁯈􀝳 where,trim 􁜓􁅩,where 􁜓􁅩􀸎􀚣􀷙􀛱􀞌
􁜓􁅩􀹍􀙖􀨻􀩪􀵊􀙁 where,􀞈􀚞􀓧􀵊􀙁,trim 􁜓􁅩􀸎􁊠􀹶􀚣􀷙􀦇􀺎􀛖􀮾􁧍􀝙􀸎
􀕦 and 􀱲 or 􀭏􀦤,􁮎􀔍􀕿􁛔􀛖􀲩􁬯􀓻 and 􀱲􁘏 or 􀝐􀴧􀌶
18􀌵Mybatis 􀸎􀦇􀖜􀩙 sql 􀲗􁤈􁕮􀺎􀩗􁤰􀔅􁍓􀺽􀩒􁨝􀬚􁬬􀢧􁌱?􁮷􀹍􀟺􀔶
􀸉􀩘􀭵􀭗?
􁒫􀓞􁐿􀸎􀖵􁊠 <resultMap> 􀺽􁓋􀒅􁭑􀓞􀨧􀔎􀚜􀝷􀞾􀩒􁨝􀪂􀯔􀝷􀔏􁳵􁌱􀸉
􀩘􀙉􁔮􀌶
􁒫􀔫􁐿􀸎􀖵􁊠 sql 􀚜􁌱􀚦􀝷􀛑􁚆􀒅􀩙􀚜􀚦􀝷􀔡􀙟􀔅􀩒􁨝􀪂􀯔􀝷􀒅􀾲􀦇
T_NAME AS NAME 􀒅􀩒 􁨝􀪂􀯔􀝷􀓞􁛱􀸎 name􀒅􀩜􀙟􀒅􀖕􀸎􀚜􀝷􀓧􀜄􀚓􀥟􀩜􀙟􀒅Mybatis 􀕿􀮺􁊼􀚜􀝷􀥟􀩜􀙟􀒅􀸬􁚆􀲤􀚩􀓨􀔏􀩒􀬫􀩒􁨝􀪂􀯔􀝷􀒅􀖦􁊜
􁛗􀝢􀕦􀙟􀱮 T_NAME AS NaMe􀒅Mybatis 􀓞􀻏􀝢􀕦􀾋􀬉􀫡􀖢􀌶
􀹍􀔧􀚜􀝷􀓨􀪂􀯔􀝷􁌱􀸉􀩘􀙉􁔮􀝸􀒅Mybatis 􁭗􁬦􀝍􀩘􀚠􀭌􀩒􁨝􀒅􀝶􀷸􀖵􁊠
􀝍􀩘􁕳􀩒􁨝􁌱􀪂􀯔􁭑􀓞􁩙􊧊􀬚􁬬􀢧􀒅􁮎􀔶􀲤􀓧􀚩􀸉􀩘􀙉􁔮􁌱􀪂􀯔􀒅􀸎􀷫􁀩
􀨠􀱮􁩙􊧊􁌱􀌶
19􀌵Xml 􀸉􀩘􀷈􀕯􀓾􀒅􁴻􀔧􀬉􁥠􁌱 select|insert|updae|delete 􀺽􁓋􀔏
􀥘􀒅􁬮􀹍􀟺􀔶􀺽􁓋?
􁬮􀹍􀮉􀥚􀙌􀕜􁌱􀺽􁓋􀒅 <resultMap>􀌵<parameterMap>􀌵<sql>􀌵
<include>􀌵 <selectKey> 􀒅􀛒􀓤􀛖􀮾 sql 􁌱 9 􀓻􀺽􁓋􀒅
trim|where|set|foreach|if|choose|when|otherwise|bind 􁒵􀒅􀙌
􀓾 <sql> 􀔅 sql 􁇆􀾧􀺽􁓋􀒅􁭗􁬦 <include> 􀺽􁓋􀭚􀙁 sql 􁇆
􀾧􀒅 <selectKey> 􀔅􀓧􀶪􀳮􁛔􀥀􁌱􀔆􁲫􁊞􀱮􁒽􁊼􀺽􁓋􀌶
20􀌵􀭮􀨫􀖛􁔄􀓾􁌱􀪂􀯔􀝷􀞾􁤒􀓾􁌱􀨁􀾧􀝷􀓧􀓞􀻏􀒅􀦇􀺎􀩙􀺱􁧃􁌱􁕮􀺎􀩗􁤰
􀚩􀳰􀨧 pojo?
1.􁭗􁬦􀣁􀺱􁧃􁌱 sql 􁧍􀝙􀓾􀨧􀔎􀨁􀾧􀝷􁌱􀚦􀝷􀌶
2.􁭗􁬦 <resultMap> 􀹶􀸉􀩘􀨁􀾧􀝷􀞾􀨫􀖛􁔄􀪂􀯔􀝷􁌱􀓞􀓞􀩒􀬫􁌱􀙉􁔮􀌶
21􀌵􀽜􁔡􀺱􁧃 like 􁧍􀝙􁧆􀯆􀔍􀙟
1.􀣁 java 􀓾􀳪􀴳􁭗􁯈􁒧􀒅􁭗􁬦 #{} 􁩙􊧊
2.􀣁 Sql 􁧍􀝙􀓾􀳪􀴳􁭗􁯈􁒧 (􀓧􀨞􀙂􀕿􀭚􁩸 Sql 􁀳􀙁)
22􀌵􁭗􀬉􀓞􀓻 Xml 􀸉􀩘􀷈􀕯􀒅􁮷􀕿􀙟􀓞􀓻 Dao 􀴳􀝗􀓨􀔏􀩒􀬫, Dao 􁌱􀫡
􀖢􀜻􁉘􀒅􀸎􀞈􀝢􀕦􁯿􁫹?
􀓧􁚆􁯿􁫹􀒅􀢩􀔅􁭗􁬦 Dao 􀩔􀲤 Xml 􀩒􀬫􁌱 sql 􁌱􀷸􀗲􀙂􁴴􀝷+􀷜􁀩􀝷􁌱􀗛
􀨂􀞾􀩔􀲤􁒽􁊼􀌶􀴳􀝗􀫡􀖢􀜻􁉘􀔅 jdk 􀛖􀮾􀕤􁉘􀜻􁉘􀒅􁬩􁤈􀷸􀕿􀔅 dao 􁊞􀱮
proxy􀒅􀕤􁉘􀩒􁨝􀕿􀳝􀱼􀴳􀝗􀷜􁀩􀒅􀝄􀲗􁤈􀩒􀬫􁌱 sql 􁬬􀢧􀷄􀴝􀌶
23􀌵Mybatis 􀸉􀩘􀷈􀕯􀓾􀒅􀦇􀺎 A 􀺽􁓋􁭗􁬦 include 􀭚􁊠􀔧 B 􀺽􁓋􁌱􀙖
􀨻􀒅􁧗􁳯􀒅B 􀺽􁓋􁚆 􀞈􀨧􀔎􀣁 A 􀺽􁓋􁌱􀝸􁶎􀒅􁬮􀸎􁧔􀮠􁶳􀨧􀔎􀣁 A 􀺽􁓋
􁌱􀚹􁶎?
􁡱􁆐 Mybatis 􁥴􀺉 Xml 􀸉􀩘􀷈􀕯􀸎􀳲􁆙􁶲􀬧􁥴􀺉􁌱􀒅􀖕􀸎􀒅􁤩􀭚􁊠􁌱 B 􀺽
􁓋􀗁􁆐􀝢􀕦􀨧􀔎􀣁􀕱􀖜􀣈􀷜􀒅Mybatis 􁮷􀝢􀕦􀾋􁏟􁦩􀚦􀌶􀜻􁉘􀸎􀒅Mybatis
􁥴􀺉 A 􀺽􁓋􀒅􀝎􁈿 A 􀺽􁓋􀭚􁊠􀔧 B 􀺽􁓋􀒅􀖕􀸎 B 􀺽􁓋􀩢􀹚􁥴􀺉􀚩􀒅􀩢􀓧
􀨂􀣁􀒅􀾌􀷸􀒅Mybatis 􀕿􀩙 A 􀺽􁓋􀺽􁦕􀔅􀹚􁥴 􀺉􁇫􀮾􀒅􁆐􀝸􁖀􁖅􁥴􀺉􀖟􀓥
􁌱􀺽􁓋􀒅􀛱􀞌 B 􀺽􁓋􀒅􀮇􀲅􀹍􀺽􁓋􁥴􀺉􀨠􀾳􀒅Mybatis 􀕿􁯿􀷛􁥴􀺉􁮎􀔶􁤩
􀺽􁦕􀔅􀹚􁥴􀺉􁌱􀺽􁓋􀒅􀾌􀷸􀙚􁥴􀺉 A 􀺽􁓋􀷸􀒅B 􀺽􁓋􀫪􁕪􀨂􀣁􀒅A 􀺽􁓋􀔞
􀩪􀝢􀕦􀾋􀬉􁥴􀺉􀨠􀱮􀔧􀌶
24􀌵Mybatis 􁌱 Xml 􀸉􀩘􀷈􀕯􀓾􀒅􀓧􀝶􁌱 Xml 􀸉􀩘􀷈􀕯􀒅id 􀸎􀞈􀝢􀕦􁯿
􀥔?
􀓧􀝶􁌱 Xml 􀸉􀩘􀷈􀕯􀒅􀦇􀺎􁯈􁗝􀔧 namespace􀒅􁮎􀔍 id 􀝢􀕦􁯿􀥔;􀦇􀺎􁀌
􀹍􁯈􁗝 namespace􀒅􁮎􀔍 id 􀓧􁚆􁯿􀥔;􀾳􁒌 namespace 􀓧􀸎􀮠􁶳􁌱􀒅􀝝
􀸎􀹋􀖯􀨫􁪢􁘒􀫪􀌶􀜻􀢩􀩪􀸎 namespace+id 􀸎􀖢􀔅 Map<String,
MappedStatement> 􁌱 key 􀖵􁊠􁌱􀒅􀦇􀺎􁀌􀹍 namespace􀒅􀩪􀛃􀓥 id􀒅􁮎
􀔍􀒅id 􁯿􀥔􀕿􀩕􁛘􀷄􀴝􀔰􁍘􁥟􁍍􀌶􀹍􀔧 namespace􀒅􁛔􁆐 id 􀩪􀝢􀕦􁯿
􀥔􀒅namespace 􀓧􀝶􀒅namespace+id 􁛔􁆐􀔞􀩪􀓧􀝶􀌶
25􀌵Mybatis 􀓾􀦇􀖜􀲗􁤈􀲢􀥒􁉘?
􀖵􁊠 BatchExecutor 􀨠􀱮􀲢􀥒􁉘􀌶
26􀌵Mybatis 􁮷􀹍􀟺􀔶 Executor 􀲗􁤈􀢏?􀨙􀕪􀔏􁳵􁌱􀜄􀚦􀸎􀕋􀔍?
Mybatis 􀹍􀓣􁐿􀤚􀹜􁌱 Executor 􀲗􁤈􀢏􀒅 SimpleExecutor􀌵
ReuseExecutor􀌵 BatchExecutor􀌶
1.SimpleExecutor:􀾯􀲗􁤈􀓞􀽺 update 􀱲 select 􀒅􀩪􀭏􀞐􀓞􀓻
Statement 􀩒􁨝􀒅􁊠􀨠􁒈􀚰􀙉􁳮 Statement 􀩒􁨝􀌶
2.ReuseExecutor:􀲗􁤈 update 􀱲 select􀒅􀕦 sql 􀖢􀔅 key 􀺱􀲤 Statement
􀩒􁨝􀒅􀨂􀣁􀩪􀖵􁊠􀒅􀓧􀨂􀣁􀩪􀚠􀭌􀒅􁊠􀨠􀝸􀒅􀓧􀙉􁳮 Statement 􀩒􁨝􀒅􁘒
􀸎􀶱􁗝􀔭 Map
3.BatchExecutor:􀨠􀱮􀲢􀥒􁉘􀌶
27􀌵Mybatis 􀓾􀦇􀖜􀳰􀨧􀖵􁊠􀟺􀓞􁐿 Executor 􀲗􁤈􀢏?
􀣁 Mybatis 􁯈􁗝􀷈􀕯􀓾􀒅􀝢􀕦􀳰􀨧􁼕􁦊􁌱 ExecutorType 􀲗􁤈􀢏􁔄􀣳􀒅􀔞􀝢
􀕦􀲋􀛖􁕳 DefaultSqlSessionFactory 􁌱􀚠􀭌 SqlSession 􁌱􀷜􁀩􀖃􁭓
ExecutorType 􁔄􀣳􀝇􀷄􀌶
28􀌵Mybatis 􀲗􁤈􀲢􁰁􀵊􀙁􀒅􁚆􁬬􀢧􀷄􀴝􀬪􀔆􁲫􀚜􁤒􀞀?
􁚆􀒅JDBC 􁮷􁚆􀒅Mybatis 􀭮􁆐􀔞􁚆􀌶
29􀌵Mybatis 􀸎􀞈􀝢􀕦􀸉􀩘 Enum 􀺍􀔈􁔄?
Mybatis 􀝢􀕦􀸉􀩘􀺍􀔈􁔄􀒅􀓧􀜔􀝢􀕦􀸉􀩘􀺍􀔈􁔄􀒅Mybatis 􀝢􀕦􀸉􀩘􀕱􀖜􀩒
􁨝􀚩􁤒􁌱􀓞􀚜􀓤􀌶􀸉􀩘􀷜􀭗􀔅􁛔􀨧􀔎􀓞􀓻 TypeHandler􀒅􀨫􁈿 TypeHandler
􁌱 setParameter()􀞾 getResult()􀴳􀝗􀷜􁀩􀌶
TypeHandler 􀹍􀓷􀓻􀖢􁊠􀒅􀓞􀸎􀨠􀱮􀕗 javaType 􁛗 jdbcType 􁌱􁫨􀴘􀒅 􀔫
􀸎􀨠􀱮 jdbcType 􁛗 javaType 􁌱􁫨􀴘􀒅􀖛􁈿􀔅 setParameter()􀞾 getResult()
􀓷􀓻􀷜􁀩􀒅􀚓􀚦􀕤􁤒􁦡􁗝 sql 􁳯􀝩􀜛􀖖􁒧􀝇􀷄􀞾􁞴􀝐􀚜􀺱􁧃􁕮􀺎􀌶
30􀌵􀦇􀖜􁞴􀝐􁛔􀛖􁊞􀱮􁌱(􀔆)􁲫􊧊?
􁯈􁗝􀷈􀕯􁦡􁗝 usegeneratedkeys 􀔅 true
31􀌵􀣁 mapper 􀓾􀦇􀖜􀖃􁭓􀥚􀓻􀝇􀷄?
􁒼:
1.􁍗􀴳􀣁􀷜􁀩􀓾􀖃􁭓􀝇􀷄􀒅xml 􀷈􀕯􁊠#{0} #{1}􀹶􁞴􀝐
2.􀖵􁊠 @param 􁀳􁥴:􁬯􀻏􀝢􀕦􁍗􀴳􀣁 xml 􀷈􀕯􀓾􁭗􁬦#{name}􀹶􁞴􀝐
32􀌵resultType resultMap 􁌱􀜄􀚦?
1.􁔄􁌱􀝷􀨁􀞾􀷄􀴝􀬪􁍘􀝶􀷸􀒅􀝢􀕦􁍗􀴳􁦡􁗝 resultType 􀝇􀷄􀔅 Pojo 􁔄
2.􁝑􀓧􀝶􀒅􁵱􁥝􁦡􁗝 resultMap 􀩙􁕮􀺎􀝷􀨁􀞾 Pojo 􀝷􀨁􁬰􁤈􁫨􀴘
33􀌵􀖵􁊠 MyBatis 􁌱 mapper 􀴳􀝗􁧣􁊠􀷸􀹍􀟺􀔶􁥝􀿢?
􁔄􀣳􁍘􀝶
1.Mapper 􀴳􀝗􀷜􁀩􀝷􀞾 mapper.xml 􀓾􀨧􀔎􁌱􀾯􀓻 sql 􁌱 id 􁍘􀝶
2.Mapper 􀴳􀝗􀷜􁀩􁌱􁬌􀙁􀝇􀷄􁔄􀣳􀞾 mapper.xml 􀓾􀨧􀔎􁌱􀾯􀓻 sql􁌱
parameterType 􁌱􁔄􀣳􁍘􀝶
3.Mapper 􀴳􀝗􀷜􁀩􁌱􁬌􀚊􀝇􀷄􁔄􀣳􀞾 mapper.xml 􀓾􀨧􀔎􁌱􀾯􀓻 sql 􁌱
resultType 􁌱􁔄􀣳􁍘􀝶
4.Mapper.xml 􀷈􀕯􀓾􁌱 namespace 􀜨􀸎 mapper 􀴳􀝗􁌱􁔄􁪠􀮆􀌶
34􀌵Mybatis 􀾲 IBatis 􀾲􁫾􀥟􁌱􀙾􀓻􀶯􁬰􀸎􀕋􀔍?
1.􀹍􀴳􀝗􁕬􀨧,􀛱􀳡􁀳􁥴􁕬􀨧 sql 􀞾 xml 􁕬􀨧 Sql
2.􀛖􀮾 sql 􁊧􀜻􀹶􁌱􁜓􁅩􁯈􁗝􀝒􀱮 OGNL 􁤒􁬡􀭗
3.􀣁􀓞􀩒􀓞,􀓞􀩒􀥚􁌱􀷸􀗲􀭚􁬰􀔧association,􀣁􀓞􀩒􀥚􁌱􀷸􀗲􀭚􀙁􀔧
collection 􁜓􁅩,􀓧􁬦􁮷􀸎􀣁 resultMap 􁯾􁶎􁯈􁗝
35􀌵IBatis 􀞾 MyBatis 􀣁􀻐􀮞􀥒􁉘􁔄􀚓􀚦􀝞􀕋􀔍?
IBatis 􁯾􁶎􁌱􀻐􀮞􀥒􁉘􁔄􀔻 SqlMapClient,MyBatis 􁯾􁶎􁌱􀻐􀮞􀥒􁉘􁔄􀝞􀘉
SqlSession􀌶
36􀌵IBatis 􀞾 MyBatis 􀣁􁕡􁜓􀓤􁌱􀓧􀝶􀹍􀟺􀔶?
1.􀣁 sql 􁯾􁶎􀝒􁰁􀞸􀝷􀹍􀜻􀹶􁌱#􀝒􁰁# 􀝒􀱮􀔧#{􀝒􁰁}
2.􀜻􀹶􁌱 $􀝒􁰁$ 􀝒􀱮􀔧${􀝒􁰁}
3.􀜻􀹶􀣁 sql 􁜓􁅩􁯾􁶎􁌱 class 􁮷􀴘􀝷􀨁􀔻 type
4.􀜻􀹶􁌱queryForObject queryForList 􀝒􀱮􀔧selectOne selectList5)􀜻􀹶􁌱
􀚦􀝷􁦡􁗝􀣁􀸉􀩘􀷈􀕯􁯾􁶎􀶱􀣁􀔧􀻐􀮞􁯈􁗝􀷈􀕯􁯾
5.1􀌵􀚓􀫲􀭗􁴴􁁞􁶎􁦶􀷆􁉘
5.1.1 ZooKeeper􀓫􁷌
1.ZooKeeper 􀸎􀕋􀔍?
ZooKeeper 􀸎􀓞􀓻􀚓􀫲􀭗􁌱􀒅􀭏􀶱􁃠􁎱􁌱􀚓􀫲􀭗􀬫􁊠􁑕􀬧􀜐􁧣􀹐􀛓􀒅􀸎
Google 􁌱 Chubby 􀓞􀓻􀭏􁃠􁌱􀨫􁈿􀒅􀨙􀸎􁵞􁗭􁌱􁓕􁉘􁘏􀒅􁍊􁥤􁍳􁵞􁗭􀓾􀝱
􀓻􁜓􁅩􁌱􁇫􀮾􀻑􀴝􁜓􁅩􀵉􀔻􁌱􀝍􁸇􁬰􁤈􀓥􀓞􀾍􀝳􁉘􀶙􀖢􀌶􀹋􁕣􀒅􀩙􁓌􀜔􀸃
􁊠􁌱􀴳􀝗􀞾􀯔􁚆􁹛􀶴􀌵􀛑􁚆􁑞􀨧􁌱􁔮􁕹􀵉􀗀􁕳􁊠􀲁􀌶
􀨮􀲁􁒒􁌱􁧛􁧗􀿢􀝢􀕦􁤩􁵞􁗭􀓾􁌱􀕱􀰺􀓞􀝣􀹢􀢏􀥒􁉘􀒅􀦇􀺎􁧛􁧗􀿢􀣁􁜓􁅩􀓤
􁀳􀙙􀔧􁍊􀞍􀢏􀒅􁬯􀓻􁍊􀞍􀢏􀔞􀸎􁊧􀲅􁬳􀴳􁌱 zookeeper 􀹢􀢏􀹶􀥒􁉘􀌶􀩒􀔭
􀙟􁧗􀿢􀒅􁬯􀔶􁧗􀿢􀕿􀝶􀷸􀝎􁕳􀙌􀕜 zookeeper 􀹢􀢏􀬚􀓬􁬡􀱮􀓞􁛘􀝸􀒅􁧗􀿢
􀲍􀕿􁬬􀢧􀱮􀛑􀌶􀢩􀾌􀒅􁵋􁍳 zookeeper 􁌱􁵞􁗭􀹢􀢏􀥀􀥚􀒅􁧛􁧗􀿢􁌱􀞃􀝺􀕿
􀵉􁹛􀖕􀸎􀙟􁧗􀿢􁌱􀞃􀝺􀕿􀓥􁴳􀌶􀹍􀬧􀯔􀸎 zookeeper 􀓾􁶋􀬉􁯿􁥝􁌱􀓞􀓻􁇙
􀯔􀒅􀲅􀹍􁌱􀹅􀷛􁮷􀸎􀙂􀩴􀹍􀬧􁌱􀒅􀾯􀓻􀹅􀷛􁮷􀹍􀓞􀓻􀠔􀓞􁌱􀷸􁳵􀱿􀒅􁬯􀓻
􀷸􁳵􀱿􁑍􀔅 zxid(Zookeeper Transaction Id)􀌶􁘒􁧛􁧗􀿢􀝝􀕿􁍘􀩒􀔭􀹅􀷛􀹍
􀬧􀒅􀔞􀩪􀸎􁧛􁧗􀿢􁌱􁬬􀢧 􁕮􀺎􀓾􀕿􀬃􀹍􁬯􀓻 zookeeper 􀹋􀷛􁌱 zxid􀌶
2.ZooKeeper 􀵉􀗀􀔧􀕋􀔍?
1􀌵􀷈􀕯􁔮􁕹
2􀌵􁭗􁎣􀹢􀚫
3.Zookeeper 􀷈􀕯􁔮􁕹
Zookeeper 􀵉􀗀􀓞􀓻􀥚􀩶􁕆􁌱􁜓􁅩􀞸􀝷􁑮􁳵(􁜓􁅩􁑍􀔅 znode)􀌶􀓨􀷈􀕯􁔮􁕹
􀓧􀝶􁌱􀸎􀒅􁬯􀔶􁜓􁅩􁮷􀝢􀕦􁦡􁗝􀙉􁘶􁌱􀷄􀴝􀒅􁘒􀷈􀕯􁔮􁕹􀓾􀝝􀹍􀷈􀕯􁜓􁅩
􀝢􀕦􀨂􀶱􀷄􀴝􁘒􁍓􀭯􁜓􁅩􀓧􁤈􀌶Zookeeper 􀔅􀔧􀗛􁦤􁹛􀞃􀝺􀞾􀖗􀭊􁬴􀒅􀣁
􀙖􀨂􀓾􁖌􀲷􀔧􁬯􀓻􀻅􁇫􁌱􁍓􀭯􁕮􀺅􀒅􁬯􁐿􁇙􀯔􀖵􀮑 Zookeeper 􀓧􁚆􁊠􀔭􀨂
􀶱􀥟􁰁􁌱􀷄􀴝􀒅􀾯􀓻􁜓􁅩􁌱􀨂􀶱􀷄􀴝􀓤􁴴􀔅 1M􀌶
4.􀢥􁐿􁔄􀣳􁌱 znode
1􀌵 PERSISTENT- 􀳮􀔋􀛸􁍓􀭯􁜓􁅩
􀨮􀲁􁒒􀓨 zookeeper 􀷙􀭏􁬳􀴳􀝸􀒅􁧆􁜓􁅩􀗁􀷯􀨂􀣁
􀔲􀌵􀚓􀫲􀭗􁶎􁦶􀓫􀻄
2􀌵 PERSISTENT_SEQUENTIAL- 􀳮􀔋􀛸􁶲􀬧􁖫􀝩􁍓􀭯􁜓􁅩
􀨮􀲁􁒒􀓨 zookeeper 􀷙􀭏􁬳􀴳􀝸􀒅􁧆􁜓􁅩􀗁􀷯􀨂􀣁􀒅􀝝􀸎 Zookeeper 􁕳􁧆
􁜓􁅩􀝷􁑍􁬰􁤈􁶲􀬧􁖫􀝩
3􀌵 EPHEMERAL- 􀔁􀷸􁍓􀭯􁜓􁅩
􀨮􀲁􁒒􀓨 zookeeper 􀷙􀭏􁬳􀴳􀝸􀒅􁧆􁜓􁅩􁤩􀚢􁴻
4􀌵 EPHEMERAL_SEQUENTIAL- 􀔁􀷸􁶲􀬧􁖫􀝩􁍓􀭯􁜓􁅩
􀨮􀲁􁒒􀓨 zookeeper 􀷙􀭏􁬳􀴳􀝸􀒅􁧆􁜓􁅩􁤩􀚢􁴻􀒅􀝝􀸎 Zookeeper 􁕳􁧆􁜓
􁅩􀝷􁑍􁬰􁤈􁶲􀬧􁖫􀝩
5.Zookeeper 􁭗􁎣􀹢􀚫
client 􁒒􀕿􀩒􀺤􀓻 znode 􀭌􁒈􀓞􀓻 watcher 􀔪􀕯􀒅􀭮􁧆 znode 􀝎􁊞􀝒􀛸
􀷸􀒅􁬯􀔶 client 􀕿􀶭􀚩 zk 􁌱􁭗􁎣􀒅􁆐􀝸 client 􀝢􀕦􀻑􀴝 znode 􀝒􀛸􀹶􀘉􀚊
􀓱􀛓􀓤􁌱􀶯􀝒􁒵􀌶
6.Zookeeper 􀘉􀔧􀕋􀔍?
1􀌵􀞸􀝷􀹐􀛓
2􀌵􁯈􁗝􁓕􁉘
3􀌵􁵞􁗭􁓕􁉘
4􀌵􀚓􀫲􀭗􁲁
5􀌵􁴚􀚜􁓕􁉘
7.zk 􁌱􀞸􀝷􀹐􀛓(􀷈􀕯􁔮􁕹)
􀞸􀝷􀹐􀛓􀸎􀳰􁭗􁬦􀳰􀨧􁌱􀝷􀨁􀹶􁞴􀝐􁩒􁃠􀱲􁘏􀹐􀛓􁌱􀣈􀣎􀒅􀚥􁊠 zk 􀚠􀭌
􀓞􀓻􀙂􀩴􁌱􁪠􀮆􀒅􀜨􀸎􀠔􀓞􁌱􁪠􀮆􀒅􁬯􀓻􁪠􀮆􀩪􀝢􀕦􀖢􀔅􀓞􀓻􀝷􀨁􀒅􀳰􀝻
􁵞􁗭􀓾􁌱􁵞􁗭􀒅􀵉􀗀􁌱􀹐􀛓􁌱􀣈􀣎􀒅􀱲􁘏􀓞􀓻􁬱􁑕􁌱􀩒􁨝􁒵􁒵􀌶
8.zk 􁌱􁯈􁗝􁓕􁉘(􀷈􀕯􁔮􁕹􀌵􁭗􁎣􀹢􀚫)
􁑕􀬧􀚓􀫲􀭗􁌱􁮱􁗟􀣁􀓧􀝶􁌱􀹢􀢏􀓤􀒅􀩙􁑕􀬧􁌱􁯈􁗝􀗞􀯳􀶱􀣁 zk 􁌱 znode
􀓥􀒅􀭮􀹍􁯈􁗝􀝎􁊞􀶯􀝒􀷸􀒅􀔞􀩪􀸎 znode 􀝎􁊞􀝒􀛸􀷸􀒅􀝢􀕦􁭗􁬦􀶯􀝒 zk
􀓾􀺤􀓻􁍓􀭯􁜓􁅩􁌱􀙖􀨻􀒅􀚥􁊠 watcher 􁭗􁎣􁕳􀝱􀓻􀨮􀲁􁒒􀒅􀕗􁘒􀹅􀶯􁯈
􁗝􀌶
9.Zookeeper 􁵞􁗭􁓕􁉘(􀷈􀕯􁔮􁕹􀌵􁭗􁎣􀹢􀚫)
􀲅􁧲􁵞􁗭􁓕􁉘􀷫􀣁􀔒􀓷􁅩:􀸎􀞈􀹍􀹢􀢏􁭅􀚊􀞾􀛒􀙁􀌵􁭌􀔈 master􀌶
􀩒􀔭􁒫􀓞􁅩􀒅􀲅􀹍􀹢􀢏􁕅􀨧􀣁􁆿􁍓􀭯􀓥􀚠􀭌􀔁􀷸􁍓􀭯􁜓􁅩􀒅􁆐􀝸􁍊􀞍􁆿􁍓
􀭯􁜓􁅩􁌱􀧼􁜓􁅩􀝒􀛸􁁾􀯳􀌶􀓞􀷮􀹍􀹢􀢏􀳯􀴧􀒅􁧆􀹢􀢏􀓨 zookeeper 􁌱􁬳􀴳
􀷙􀭏􀒅􀙌􀲅􀚠􀭌􁌱􀔁􀷸􁍓􀭯􁜓􁅩􁤩􀚢􁴻􀒅􀲅􀹍􀙌􀕜􀹢􀢏􁮷􀶭􀚩􁭗􁎣:􀺤􀓻􀘳
􀭞􁍓􀭯􁤩􀚢􁴻􀒅􀔭􀸎􀒅􀲅􀹍􀕈􁮷􁎣􁭲:􀨙􀓤􁛼􀔧􀌶
􀷛􀹢􀢏􀛒􀙁􀔞􀸎􁔄􀖒􀒅􀲅􀹍􀹢􀢏􀶭􀚩􁭗􁎣:􀷛􀘳􀭞􁍓􀭯􀛒􀙁􀒅highcount 􀝈
􀹍􀔧􀒅􀩒􀔭􁒫􀔫􁅩􀒅􀱯􀕪􁑖􀮙􀶯􀝒 􀓞􀓥􀒅􀲅􀹍􀹢􀢏􀚠􀭌􀔁􀷸􁶲􀬧􁖫􀝩􁍓􀭯
􁜓􁅩􀒅􀾯􀽺􁭌􀝐􁖫􀝩􀹋􀩜􁌱􀹢􀢏􀖢􀔅 master 􀩪􀦅􀌶
10.Zookeeper 􀚓􀫲􀭗􁲁(􀷈􀕯􁔮􁕹􀌵􁭗􁎣 􀹢􀚫)
􀹍􀔧 zookeeper 􁌱􀓞􁛘􀯔􀷈􀕯􁔮􁕹􀒅􁲁􁌱􁳯􁷌􀝒􀮑􀨻􀸃􀌶􁲁􀹐􀛓􀝢􀕦􀚓􀔅
􀓷􁔄􀒅􀓞􀓻􀸎􀗛􀳮􁇿􀜛􀒅􀝚􀓞􀓻􀸎􀴴 􀚫􀷸􀬧􀌶
􀩒􀔭􁒫􀓞􁔄􀒅􀱯􀕪􀩙 zookeeper 􀓤􁌱􀓞􀓻 znode 􁍡􀖢􀸎􀓞􀲩􁲁􀒅􁭗􁬦
createznode 􁌱􀷜􀭗􀹶􀨫􁈿􀌶􀲅􀹍􀨮􀲁􁒒􁮷􀝄􀚠􀭌 /distribute_lock
􁜓􁅩􀒅􀹋􁕣􀱮􀛑􀚠􀭌􁌱􁮎􀓻􀨮􀲁􁒒􀔞􀜨􀳜􀹍􀔧􁬯􀲩􁲁􀌶􁊠􀨠􀚢􁴻􀴧􁛔􀫩􀚠
􀭌􁌱 distribute_lock 􁜓􁅩􀩪􁯽􀶱􀚊􁲁􀌶
􀩒􀔭􁒫􀔫􁔄􀒅 /distribute_lock 􀫪􁕪􁶼􀘶􀨂􀣁􀒅􀲅􀹍􀨮􀲁􁒒􀣁􀨙􀓥􁶎
􀚠􀭌􀔁􀷸􁶲􀬧􁖫􀝩􁍓􀭯􁜓􁅩􀒅􀞾􁭌 master 􀓞􀻏􀒅􁖫􀝩􀹋􀩜􁌱􁞴􀮑􁲁􀒅􁊠
􀨠􀚢􁴻􀒅􀗁􀽺􀷜􀗎􀌶
11.􁞴􀝐􀚓􀫲􀭗􁲁􁌱􁁞􁑕
􀣁􁞴􀝐􀚓􀫲􀭗􁲁􁌱􀷸􀗲􀣁 locker 􁜓􁅩􀓥􀚠􀭌􀔁􀷸􁶲􀬧􁜓􁅩􀒅􁯽􀶱􁲁􁌱􀷸􀗲
􀚢􁴻􁧆􀔁􀷸􁜓􁅩􀌶􀨮􀲁􁒒􁧣􁊠 createNode 􀷜􁀩􀣁 locker 􀓥􀚠􀭌􀔁􀷸􁶲􀬧
􁜓􁅩􀒅
􁆐􀝸􁧣􁊠 getChildren(“locker”)􀹶􁞴􀝐 locker 􀓥􁶎􁌱􀲅􀹍􀧼􁜓􁅩􀒅􁀳􀰺􀾌􀷸
􀓧􁊠􁦡􁗝􀕱􀖜 Watcher􀌶􀨮􀲁􁒒􁞴􀝐􀚩􀲅􀹍􁌱􀧼􁜓􁅩 path 􀔏􀝸􀒅􀦇􀺎􀝎􁈿
􁛔􀫩􀚠􀭌􁌱􁜓􁅩􀣁􀲅􀹍􀚠􀭌􁌱􀧼􁜓􁅩􀬧􀝩􀹋􀩜􀒅􁮎􀔍􀩪􁦊􀔅􁧆􀨮􀲁􁒒􁞴􀝐
􀚩􀔧􁲁􀌶􀦇􀺎􀝎􁈿􁛔􀫩􀚠􀭌􁌱􁜓􁅩􀬚􁶋 locker 􀲅􀹍􀧼􁜓􁅩􀓾􀹋􀩜􁌱􀒅􁧔􀸁
􁛔􀫩􁬮􁀌􀹍􁞴􀝐􀚩􁲁􀒅􀾌􀷸􀨮􀲁􁒒􁵱􁥝􀲤􀚩􀾲􁛔􀫩􀩜􁌱􁮎􀓻􁜓􁅩􀒅􁆐􀝸􀩒
􀙌􁧣􁊠 exist()􀷜􁀩􀒅􀝶􀷸􀩒􀙌􁀳􀙙􀔪􀕯􁍊􀞍􀢏􀌶􀔏􀝸􀒅􁦏􁬯􀓻􁤩􀙉􁀳􁌱􁜓
􁅩􀚢􁴻􀒅􀚞􀨮􀲁􁒒􁌱 Watcher 􀕿􀶭􀚩􁍘􀬫􁭗􁎣􀒅􀾌􀷸􀙚􀽺􀚣􀷙􁛔􀫩􀚠􀭌􁌱
􁜓􁅩􀸎􀞈􀸎 locker 􀧼􁜓􁅩􀓾􀬧􀝩􀹋􀩜􁌱􀒅􀦇􀺎􀸎􀚞􁞴􀝐􀚩􀔧􁲁􀒅􀦇􀺎􀓧􀸎
􀚞􁯿􀥔􀕦􀓤􀾍􁹈􁖀􁖅􁞴􀝐􀚩􀾲􁛔􀫩􀩜􁌱􀓞􀓻􁜓􁅩􀬚􁀳􀙙􁍊􀞍􀌶􀭮􀚹􁬯􀓻􁬦
􁑕􀓾􁬮􁵱􁥝􁦜􀥚􁌱􁭦􁬋􀚣􀷙􀌶
􀕤􁎱􁌱􀨫􁈿􀔆􁥝􀸎􀤚􀔭􀔰􀷕􁲁􀒅􁞴􀝐􀚓􀫲􀭗􁲁􁌱􁯿􁅩􁭦􁬋􀣁􀔭
BaseDistributedLock􀒅􀨫􁈿􀔧􀤚􀔭 Zookeeper 􀨫􁈿􀚓􀫲􀭗􁲁􁌱􁕡􁜓􀌶
12.Zookeeper 􁴚􀚜􁓕􁉘(􀷈􀕯􁔮􁕹􀌵􁭗􁎣􀹢􀚫)
􀓷􁐿􁔄􀣳􁌱􁴚􀚜:
1􀌵􀝶􀾍􁴚􀚜􀒅􀭮􀓞􀓻􁴚􀚜􁌱􀱮􀞧􁮷􁘸􁼶􀷸􀒅􁬯􀓻􁴚􀚜􀲍􀝢􁊠􀒅􀞈􀚞􀓞􁍗
􁒵􀮇􀲅􀹍􀱮􀞧􀚩􁬡􀌶
2􀌵􁴚􀚜􀳲􁆙 FIFO 􀷜􀭗􁬰􁤈􀙁􁴚􀞾􀚊􁴚􀶙􀖢􀌶
􁒫􀓞􁔄􀒅􀣁􁕅􀨧􁍓􀭯􀓥􀚠􀭌􀔁􀷸􁍓􀭯􁜓􁅩􀒅􁍊􀞍􁜓􁅩􀷄􁍓􀸎􀞈􀸎􀱯􀕪􁥝􀿢
􁌱􀷄􁍓􀌶
􁒫􀔫􁔄􀒅􀞾􀚓􀫲􀭗􁲁􀹐􀛓􀓾􁌱􀴴􀚫􀷸􀬧􀣋􀸧􀤚􀹜􀜻􁉘􀓞􁛘􀒅􀙁􀚜􀹍􁖫􀝩􀒅
􀚊􀚜􀳲􁖫􀝩􀌶􀣁􁇙􀨧􁌱􁍓􀭯􀓥􀚠􀭌 PERSISTENT_SEQUENTIAL 􁜓􁅩􀒅􀚠
􀭌􀱮􀛑􀷸 Watcher 􁭗􁎣􁒵􀮇􁌱􁴚􀚜􀒅􁴚􀚜􀚢􁴻􀬧􀚜􀝩􀹋􀩜􁌱􁜓􁅩􁊠􀕦 􁁾
􁩇􀌶􀾌􀣋􀸧􀓥 Zookeeper 􁌱 znode 􁊠􀔭􁁾􀯳􀨂􀘙􀒅znode 􀨂􀘙􁌱􀷄􀴝􀩪􀸎
􁁾􀯳􁴚􀚜􀓾􁌱􁁾􀯳􀙖􀨻􀒅SEQUENTIAL 􀬧􀚜􀝩􀩪􀸎􁁾􀯳􁌱􁖫􀝩􀒅􀳲􀬧􀝐􀚊
􀜨􀝢􀌶􁊧􀔭􀚠􀭌􁌱􁜓􁅩􀸎􀳮􀔋􀛸􁌱􀒅􀲅􀕦􀓧􀮠􀳅􀮞􁴚􀚜􁁾􀯳􁌱􀓶􀥦􁳯􁷌􀌶
13.Zookeeper 􀷄􀴝􀥔􀚫
Zookeeper 􀖢􀔅􀓞􀓻􁵞􁗭􀵉􀗀􀓞􁛘􁌱􀷄􀴝􀹐􀛓􀒅􁛔􁆐􀒅􀨙􁥝􀣁􀲅􀹍􀹢􀢏􁳵
􀘉􀷄􀴝􀥔􀚫􀌶􀷄􀴝􀥔􀚫􁌱􀦅􀥒:
1􀌵􀨻􁲙:􀓞􀓻􁜓􁅩􀚊􁲙􀒅􀓧􁛘􀔭􁦏􀷆􀓻􁔮􁕹􀘊􀾊􀫡􀖢􀒅􀚦􁌱􁜓􁅩􀝢􀕦􀴳􁓕
􀨙􁌱􀫡􀖢;
2􀌵􀵉􁹛􁔮􁕹􁌱􀲘􀪀􁚆􀛎 :􀲩􁨮􁫹􀚓􀫲􀚩􀥚􀓻􁜓􁅩􀓤􀒅􀱲􁘏􀥀􀛒􁜓􁅩􀹶􀵉􁹛
􁔮􁕹􁌱􁨮􁫹􁚆􀛎;
3􀌵􀵉􁹛􀯔􁚆:􁦏􀨮􀲁􁒒􀹜􀣈􁦢􁳯􀩪􁬪􁌱􁜓􁅩􀒅􀵉􁹛􁊠􀲁􁦢􁳯􁭛􀬶􀌶
􀕗􀨮􀲁􁒒􁧛􀙟􁦢􁳯􁌱􁭐􀸁􀬶􀹶􁍡􀒅􀷄􀴝􀥔􀚫􁵞􁗭􁔮􁕹􀚓􀓥􁶎􀓷􁐿:
1􀌵􀙟􀔆(WriteMaster) :􀩒􀷄􀴝􁌱􀗥􀶯􀵉􀔻􁕳􀳰􀨧􁌱􁜓􁅩􀌶􁧛􀷫􀾌􁴴􀚫􀒅􀝢
􀕦􁧛􀝐􀕱􀖜􀓞􀓻􁜓􁅩􀌶􁬯􁐿􀰘􀙭􀓥􀨮􀲁􁒒􁵱􁥝􀩒􁧛􀓨􀙟􁬰􁤈􀜄􀚦􀒅􀗗􁑍􁧛
􀙟􀚓􁐶;
2􀌵􀙟􀕱􀰺(Write Any):􀩒􀷄􀴝􁌱􀗥􀶯􀝢􀵉􀔻􁕳􀕱􀰺􁌱􁜓􁅩􀒅􁪙􁧛􀓞􀻏􀌶􁬯
􁐿􀰘􀙭􀓥􀒅􀨮􀲁􁒒􀩒􁵞􁗭􁜓􁅩􁌱􁥯􁜋􀓨􀝒􀛸􁭐􀸁􀌶
􀩒 zookeeper 􀹶􁧔􀒅􀨙􁯻􁊠􁌱􀷜􀭗􀸎􀙟􀕱􀰺􀌶􁭗􁬦􀥀􀛒􀹢􀢏􀒅􀨙􁌱􁧛􀞃􀝺
􁚆􀛎􀞾􀟥􀬫􁚆􀛎􀲘􀪀􀯔􁶋􀬉􀦅􀒅􁘒􀙟􀒅􁵋􁍳􀹢􀢏􁌱􀥀􀥚􀞃􀝺􁚆􀛎􁙗􀨧􀓥􁴳
(􁬯􀔞􀸎􀨙􀭌􁒈 observer 􁌱􀜻􀢩)􀒅􁘒􀟥􀬫􁚆􀛎􀚞􀝐􀙬􀔭􀙍􀖛􀨫􁈿􀷜􀭗􀒅􀸎
􀭊􁬴􀥔􀚫􀗛􀳮􀹋􁕣􀓞􁛘􀯔􀒅􁬮􀸎􁒈􀜨􀥔􀚫􀮳􁭛􀟥􀬫􀌶
14.Zookeeper 􀫡􀖢􀜻􁉘
Zookeeper 􁌱􀻐􀮞􀸎􀜻􀧼􀬠􀶎􀒅􁬯􀓻􀹢􀚫􀗛􁦤􀔧􀝱􀓻 Server 􀔏􁳵􁌱􀝶􀾍􀌶
􀨫􁈿􁬯􀓻􀹢􀚫􁌱􀜐􁦓􀝞􀘉 Zab 􀜐􁦓􀌶Zab 􀜐􁦓􀹍􀓷􁐿􀽜􀭗􀒅􀨙􀕪􀚓􀚦􀸎􀯩
􀥔􀽜􀭗(􁭌􀔆)􀞾􀬠􀶎􀽜􀭗(􀝶􀾍)􀌶􀭮􀹐􀛓􀞐􀛖􀱲􁘏􀣁􁶾􀩕􁘏􀫄􁃛􀝸􀒅Zab 􀩪
􁬰􀙁􀔧􀯩􀥔􀽜􀭗􀒅􀭮􁶾􀩕􁘏􁤩􁭌􀔈􀚊􀹶􀒅􀓬􀥟􀥚􀷄 Server 􀨠􀱮􀔧􀞾 leader
􁌱􁇫􀮾􀝶􀾍􀕦􀝸􀒅􀯩􀥔􀽜􀭗􀩪􁕮􀹳􀔧􀌶􁇫􀮾􀝶􀾍􀗛􁦤􀔧 leader 􀞾 Server
􀙍􀹍􁍘􀝶􁌱􁔮􁕹􁇫􀮾􀌶
15.zookeeper 􀸎􀦇􀖜􀗛􁦤􀔪􀛓􁌱􁶲􀬧􀓞􁛘􀯔􁌱?
zookeeper 􁯻􁊠􀔧􁭓􀥀􁌱􀔪􀛓 Id 􀹶􀺽􁦩􀒅􀲅􀹍􁌱 proposal(􀵉􁦓)􁮷􀣁􁤩􀵉
􀚊􁌱􀷸􀗲􀛒􀓤􀔧 zxid􀒅zxid 􀨫􁴬 􀓤􀸎􀓞􀓻 64 􀖖􁌱􀷄􀨁􀒅􁹛 32 􀖖􀸎
epoch(􀷸􀹗; 􁕉􀘲; 􀓮; 􀷛􀷸􀕤)􁊠􀹶􀺽􁦩 leader 􀸎􀞈􀝎􁊞􀶯􀝒􀒅􀦇􀺎􀹍 􀷛􁌱
leader 􀔾􁊞􀚊􀹶􀒅epoch 􀕿􁛔􀥀􀒅􀖗 32 􀖖􁊠􀹶􁭓􀥀􁦇􀷄􀌶􀭮􀷛􀔾􁊞
proposal 􁌱􀷸􀗲􀒅􀕿􀗁􀴝􀷄􀴝􀬪􁌱􀓷􁴤􀾧􁬦􁑕􀒅􁸒􀘶􀕿􀝻􀙌􀕜􁌱 server 􀝎
􀚊􀔪􀛓􀲗􁤈􁧗􀿢􀒅􀦇􀺎􁩻􁬦􀜎􀷄􁌱􀹢􀢏􁮷􁚆􀲗􁤈􀬚􀓬􁚆􀥜􀱮􀛑􀒅􁮎􀔍􀩪􀕿
􀭏􀦤􀲗􁤈􀌶
16.Zookeeper 􀓥 Server 􀫡􀖢􁇫􀮾
􀾯􀓻 Server 􀣁􀫡􀖢􁬦􁑕􀓾􀹍􀓣􁐿􁇫􀮾:
LOOKING:􀭮􀚹 Server 􀓧􁎣􁭲 leader 􀸎􁧡􀒅􀾋􀣁􀵤􀩔 LEADING:􀭮􀚹
Server 􀜨􀔅􁭌􀔈􀚊􀹶􁌱 leader FOLLOWING:leader 􀫪􁕪􁭌􀔈􀚊􀹶􀒅􀭮􀚹
Server 􀓨􀔏􀝶􀾍
17.zookeeper 􀸎􀦇􀖜􁭌􀝐􀔆 leader 􁌱?
􀭮 leader 􀫄􁃛􀱲􁘏 leader 􀥦􀝄􀥟􀥚􀷄􁌱 follower􀒅􁬯􀷸 zk 􁬰􀙁􀯩􀥔􀽜
􀭗􀒅􀯩􀥔􀽜􀭗􁵱􁥝􁯿􀷛􁭌􀔈􀚊􀓞􀓻􀷛􁌱 leader􀒅􁦏􀲅􀹍􁌱 Server 􁮷􀯩􀥔􀚩
􀓞􀓻􀾋􁏟􁌱􁇫􀮾􀌶Zk 􁌱􁭌􀔈􁓒􁀩􀹍􀓷􁐿:
􀓞􁐿􀸎􀤚􀔭 basic paxos 􀨫􁈿􁌱􀒅
􀝚􀥘􀓞􁐿􀸎􀤚􀔭 fast paxos 􁓒􁀩􀨫􁈿􁌱􀌶􁔮􁕹􁼕􁦊􁌱􁭌􀔈􁓒􁀩􀔅 fast
paxos􀌶
1􀌵Zookeeper 􁭌􀔆􁁞􁑕(basic paxos)
(1)􁭌􀔈􁕚􁑕􁊧􀭮􀚹 Server 􀝎􁩸􁭌􀔈􁌱􁕚􁑕􀳅􀕱􀒅􀙌􀔆􁥝􀛑􁚆􀸎􀩒􀲭􁐥􁕮􀺎
􁬰􁤈􁕹􁦇􀒅􀬚􁭌􀚊􀴵􁞂􁌱 Server;
(2)􁭌􀔈􁕚􁑕􁸒􀘶􀝻􀲅􀹍 Server 􀝎􁩸􀓞􀽺􁧃􁳯(􀛱􀳡􁛔􀫩);
(3)􁭌􀔈􁕚􁑕􀶭􀚩􀢧􀥔􀝸􀒅􁸵􁦤􀸎􀞈􀸎􁛔􀫩􀝎􁩸􁌱􁧃􁳯(􁸵􁦤 zxid 􀸎􀞈􀓞
􁛘)􀒅􁆐􀝸􁞴􀝐􀩒􀷜􁌱 id(myid)􀒅􀬚􀨂􀘙􀚩􀭮􀚹􁧃􁳯􀩒􁨝􀚜􁤒􀓾􀒅􀹋􀝸􁞴􀝐
􀩒􀷜􀵉􁦓􁌱 leader 􁍘􀙉􀗞􀯳(id,zxid)􀒅􀬚􀩙􁬯􀔶􀗞􀯳􀨂􀘙􀚩􀭮􀽺􁭌􀔈􁌱􀲭
􁐥􁦕􀭯􁤒􀓾;
(4)􀶭􀚩􀲅􀹍 Server 􀢧􀥔􀕦􀝸􀒅􀩪􁦇􁓒􀚊 zxid 􀹋􀥟􁌱􁮎􀓻 Server􀒅􀬚􀩙􁬯
􀓻 Server 􁍘􀙉􀗞􀯳􁦡􁗝􀱮􀓥􀓞􀽺􁥝􀲭􁐥􁌱 Server;
(5)􁕚􁑕􀩙􀭮􀚹 zxid 􀹋􀥟􁌱 Server 􁦡􁗝􀔅􀭮􀚹 Server 􁥝􀴵􁞂􁌱 Leader􀒅􀦇
􀺎􀾌􀷸􁞴􁙯􁌱 Server 􁞴􀮑 n/2 + 1 􁌱 Server 􁐥􀷄􀒅􁦡􁗝􀭮􀚹􀴵􁞂􁌱 leader
􀔅􁞴􁙯􁌱 Server􀒅􀩙􀻑􀴝􁞴􁙯􁌱 Server 􁍘􀙉􀗞􀯳􁦡􁗝􁛔􀫩􁌱􁇫􀮾􀒅􀞈􀚞􀒅
􁖀􁖅􁬯􀓻􁬦􁑕􀒅􁍗􀚩 leader 􁤩􁭌􀔈􀚊􀹶􀌶 􁭗􁬦􁁞􁑕􀚓􀺉􀱯􀕪􀝢􀕦􀮑􀚊:􁥝
􀖵 Leader 􁞴􀮑􀥚􀷄 Server 􁌱􀶪􀳮􀒅􀚞 Server 􀯛􀷄􀮠􁶳􀸎􀥰􀷄 2n+1􀒅􀓬
􀨂􁁚􁌱 Server 􁌱􀷄􁍓􀓧􀮑􀩝􀔭 n+1. 􀾯􀓻 Server 􀞐􀛖􀝸􁮷􀕿􁯿􀥔􀕦􀓤􁁞
􁑕􀌶􀣁􀯩􀥔􀽜􀭗􀓥􀒅􀦇􀺎􀸎􀚟􀕗􀫄􁃛􁇫􀮾􀯩􀥔􁌱􀱲􁘏􀚟􀞐􀛖􁌱 server 􁬮􀕿
􀕗􁏺􁍏􀮳􁆙􀓾􀯩􀥔􀷄􀴝􀞾􀕿􁦾􀗞􀯳􀒅zk 􀕿􁦕􀭯􀔪􀛓􀷭􀮪􀬚􀨧􀹗􁬰􁤈􀮳􁆙􀒅
􀷜􀗎􀣁􀯩􀥔􀷸􁬰􁤈􁇫􀮾􀯩􀥔􀌶
2􀌵Zookeeper 􁭌􀔆􁁞􁑕(basic paxos)
fast paxos 􁁞􁑕􀸎􀣁􁭌􀔈􁬦􁑕􀓾􀒅􀺤 Server 􁸒􀘶􀝻􀲅􀹍 Server 􀵉􁦓􁛔􀫩􁥝
􀱮􀔅 leader􀒅􀭮􀙌􀨙 Server 􀶭􀚩􀵉􁦓􀕦􀝸􀒅􁥴􀙬 epoch 􀞾 zxid 􁌱􀙫􁑱􀒅
􀬚􀴳􀝑􀩒􀷜􁌱􀵉􁦓􀒅􁆐􀝸􀝻􀩒􀷜􀝎􁭆􀴳􀝑􀵉􁦓􀨠􀱮􁌱􁁾􀯳􀒅􁯿􀥔􁬯􀓻􁁞
􁑕􀒅􀹋􀝸􀓞􀨧􁚆􁭌􀔈􀚊 Leader􀌶
18.Zookeeper 􀝶􀾍􁁞􁑕
􁭌􀨠 Leader 􀕦􀝸􀒅zk 􀩪􁬰􀙁􁇫􀮾􀝶􀾍􁬦􁑕􀌶
1􀌵Leader 􁒵􀮇 server 􁬳􀴳;
2􀌵Follower 􁬳􀴳 leader􀒅􀩙􀹋􀥟􁌱 zxid 􀝎􁭆􁕳 leader;
3􀌵Leader 􀻑􀴝 follower 􁌱 zxid 􁏟􀨧􀝶􀾍􁅩;
4􀌵􀨠􀱮􀝶􀾍􀝸􁭗􁎣 follower 􀫪􁕪􀱮􀔅 uptodate 􁇫􀮾;
5􀌵Follower 􀶭􀚩 uptodate 􁁾􀯳􀝸􀒅􀝈􀝢􀕦􁯿􀷛􀴳􀝑 client 􁌱􁧗􀿢􁬰􁤈􀹐
􀛓􀔧􀌶
19.􀚓􀫲􀭗􁭗􁎣􀞾􀜐􁧣
􀩒􀔭􁔮􁕹􁧣􀬶􀹶􁧔:􀶙􀖢􀕈􀞧􀝎􁭆􁭗􁎣􀨫􁴬􀸎􁭗􁬦􀴴􀚫􀝣􀶯􀝒􀺤􀓻􁜓􁅩􁌱􁇫
􀮾􀒅􁆐􀝸 zk 􀩙􁬯􀔶􀝒􀛸􀝎􁭆􁕳􁀳􀙙􀔧􁬯􀓻􁜓􁅩􁌱 watcher 􁌱􀲅􀹍􀨮􀲁
􁒒􀌶
􀩒􀔭􀲗􁤈􀰘􀙭􀿤􀲸:􀾯􀓻􀫡􀖢􁬰􁑕􁮷􀣁􀺤􀓻􁍓􀭯􀓥􀚠􀭌􀓞􀓻􀔁􀷸􁜓􁅩􀌶􀬚􀵭
􀬃􀫡􀖢􁌱􁬰􀬶􀷄􀴝􀒅􁬯􀻏􀿤􀯛􁌱􁬰􁑕􀝢􀕦􁍊􀴴􁍓􀭯􀧼􁜓􁅩􁌱􀝒􀛸􁞴􀮑􀫡􀖢
􁬰􀬶􁌱􀨫􀷸􁌱􀙂􀩴􀰘􀙭􀌶
20.􀹢􀢏􀓾􀔅􀕋􀔍􀕿􀹍 leader?
􀣁􀚓􀫲􀭗􁈾􀤹􀓾􀒅􀹍􀔶􀓱􀛓􁭦􁬋􀝝􁵱􁥝􁵞􁗭􀓾􁌱􀺤􀓞􀝣􀹢􀢏􁬰􁤈􀲗􁤈􀒅􀙌
􀕜􁌱􀹢􀢏􀝢􀕦􀙈􀕁􁬯􀓻􁕮􀺎􀒅􁬯􀻏􀝢􀕦􀥟􀥟􀙺􀩝􁯿􀥔􁦇􁓒􀒅􀵉􁹛􀯔􁚆􀒅􀔭
􀸎􀩪􁵱􁥝􁬰􁤈 leader 􁭌􀔈􀌶
21.zk 􁜓􁅩􀨣􀹢􀦇􀖜􀥒􁉘?
Zookeeper 􀹜􁫝􀔞􀸎􁵞􁗭􀒅􀴵􁞂􁯈􁗝􀓧􀩝􀔭 3 􀓻􀹐􀛓􀢏􀌶Zookeeper 􁛔􁫝
􀔞􁥝􀗛􁦤􀭮􀓞􀓻􁜓􁅩􀨣􀹢􀷸􀒅􀙌􀕜􁜓􁅩􀕿􁖀􁖅􀵉􀗀􀹐􀛓􀌶
􀦇􀺎􀸎􀓞􀓻 Follower 􀨣􀹢􀒅􁬮􀹍 2 􀝣􀹐􀛓􀢏􀵉􀗀􁦢􁳯􀒅􀢩􀔅 Zookeeper
􀓤􁌱􀷄􀴝􀸎􀹍􀥚􀓻􀛅􀹜􁌱􀒅􀷄􀴝􀬚􀓧􀕿􀓶􀥦;
􀦇􀺎􀸎􀓞􀓻 Leader 􀨣􀹢􀒅Zookeeper 􀕿􁭌􀔈􀚊􀷛􁌱 Leader􀌶
ZK 􁵞􁗭􁌱􀹢􀚫􀸎􀝝􁥝􁩻􁬦􀜎􀷄􁌱􁜓􁅩􀾋􀬉􀒅􁵞􁗭􀩪􁚆􀾋􀬉􀵉􀗀􀹐􀛓􀌶􀝝
􀹍􀣁 ZK 􁜓􁅩􀳯􀮑􀥡􀥚􀒅􀝝􀛃􀓞􀜎􀱲􀓧􀚩􀓞􀜎􁜓􁅩􁚆􀫡􀖢􀒅􁵞􁗭􀲍􀥦􀶴􀌶
􀲅􀕦
3 􀓻􁜓􁅩􁌱 cluster 􀝢􀕦􀳯􀴧 1 􀓻􁜓􁅩(leader 􀝢􀕦􀮑􀚩 2 􁐥>1.5)
2 􀓻􁜓􁅩􁌱 cluster 􀩪􀓧􁚆􀳯􀴧􀕱􀖜 1 􀓻􁜓􁅩􀔧(leader 􀝢􀕦􀮑􀚩 1 􁐥<=1)
22.zookeeper 􁨮􁫹􀣐􁤍􀞾 nginx 􁨮􁫹􀣐􁤍􀜄􀚦
zk 􁌱􁨮􁫹􀣐􁤍􀸎􀝢􀕦􁧣􀴴􀒅nginx 􀝝􀸎􁚆􁧣􀹦􁯿􀒅􀙌􀕜􁵱􁥝􀝢􀴴􁌱􁮷􁵱􁥝
􁛔􀫩􀙟􀵊􀕯;􀖕􀸎 nginx 􁌱􀞃􀝺􁰁􀾲 zk 􀥟􀮉􀥚􀒅􀬫􁧆􁧔􀳲􀓱􀛓􁭌􀳠􁊠􀟺􁐿
􀷜􀭗􀌶
23.zookeeper watch 􀹢􀚫
Watch 􀹢􀚫􀨥􀷜􀥍􀸁:􀓞􀓻 Watch 􀔪􀕯􀸎􀓞􀓻􀓞􀽺􀯔􁌱􁥶􀝎􀢏􀒅􀭮􁤩􁦡􁗝
􀔧 Watch 􁌱􀷄􀴝􀝎􁊞􀔧􀶯􀝒􁌱􀷸􀗲􀒅􀚞􀹐􀛓􀢏􀩙􁬯􀓻􀶯􀝒􀝎􁭆􁕳􁦡􁗝􀔧
Watch 􁌱􀨮􀲁􁒒􀒅􀕦􀗎􁭗􁎣􀨙􀕪􀌶
Zookeeper 􀹢􀚫􁌱􁇙􁅩:
1􀌵􀓞􀽺􀯔􁥶􀝎􀷄􀴝􀝎􁊞􀶯􀝒􀷸􀒅􀓞􀓻 watcher event 􀕿􁤩􀝎􁭆􀚩 client􀒅
􀖕􀸎 client 􀝝􀕿􀶭􀚩􀓞􀽺􁬯􀻏􁌱􀗞􀯳􀌶
2􀌵watcher event 􀭑􀾍􀝎􁭆 watcher 􁌱􁭗􁎣􀔪􀕯􀕗 server 􀝎􁭆􀚩 client 􀸎
􀭑􀾍􁌱􀒅􁬯􀩪􀨂􀣁􀓞􀓻􁳯􁷌􀒅􀓧􀝶􁌱􀨮􀲁􁒒􀞾􀹐􀛓􀢏􀔏􁳵􁭗􁬦 socket 􁬰
􁤈􁭗􀗞􀒅􁊧􀔭􁗑􁕶􀭊􁬴􀱲􀙌􀕜􀢩􁔰􀩕􁛘􀨮􀲁􁒒􀣁􀓧􁭗􁌱􀷸􀚰􁍊􀞍􀚩􀔪􀕯􀒅
􁊧􀔭 Zookeeper 􀹜􁫝􀵉􀗀􀔧 ordering guarantee􀒅􀜨􀨮􀲁􁒒􁍊􀞍􀔪􀕯􀝸􀒅
􀲍􀕿􀰽􁎣􀨙􀲅􁍊􁥤 znode 􀝎􁊞􀔧 􀝒􀛸􀌶􀲅􀕦􀱯􀕪􀖵􁊠 Zookeeper 􀓧􁚆􀹗
􀹕􁚆􀥜􁍊􀴴􀚩􁜓􁅩􀾯􀽺􁌱􀝒􀛸􀌶Zookeeper 􀝝􁚆􀗛􁦤􀹋􁕣􁌱􀓞􁛘􀯔􀒅􁘒􀷫
􁀩􀗛􁦤􀭩􀓞􁛘􀯔􀌶
3􀌵􀷄􀴝􁍊􁥤 Zookeeper 􀹍􀷄􀴝􁍊􁥤􀞾􀧼􀷄􀴝􁍊􁥤 getdata() and exists()􁦡
􁗝􀷄􀴝􁍊􁥤􀒅getchildren()􁦡􁗝􀔧􀧼􁜓􁅩􁍊􁥤􀌶
4􀌵􁀳􀙙 watcher getData􀌵exists􀌵getChildren
5􀌵􁥶􀝎 watcher create􀌵delete􀌵setData
6􀌵setData()􀕿􁥶􀝎 znode 􀓤􁦡􁗝􁌱 data watch(􀦇􀺎 set 􀱮􀛑􁌱􁦾)􀌶􀓞􀓻
􀱮􀛑􁌱 create() 􀶙􀖢􀕿􁥶􀝎􁤩􀚠􀭌􁌱 znode 􀓤􁌱􀷄􀴝 watch􀒅􀕦􀝊􀙌􁆿􁜓
􁅩􀓤􁌱 child watch􀌶􁘒􀓞􀓻􀱮􀛑􁌱 delete()􀶙􀖢􀩙􀕿􀝶􀷸􁥶􀝎􀓞􀓻 znode
􁌱 data watch 􀞾 child watch(􀢩􀔅􁬯􀻏􀩪􁀌􀹍􀧼􁜓􁅩􀔧)􀒅􀝶􀷸􀔞􀕿􁥶􀝎􀙌
􁆿􁜓􁅩􁌱 child watch􀌶
7􀌵􀭮􀓞􀓻􀨮􀲁􁒒􁬳􀴳􀚩􀓞􀓻􀷛􁌱􀹐􀛓􀢏􀓤􀷸􀒅watch 􀩙􀕿􁤩􀕦􀕱􀰺􀕿􁦾
􀔪􀕯􁥶􀝎􀌶􀭮􀓨􀓞􀓻􀹐􀛓􀢏􀥦􀝄􁬳􀴳􁌱􀷸􀗲􀒅􀸎􀷫􁀩􀴳􀶭􀚩 watch 􁌱􀌶􁘒
􀭮 client 􁯿􀷛􁬳􀴳􀷸􀒅􀦇􀺎􁵱􁥝􁌱􁦾􀒅􀲅􀹍􀘶􀚹􁀳􀙙􁬦􁌱 watch􀒅􁮷􀕿􁤩
􁯿􀷛􁀳􀙙􀌶􁭗􀬉􁬯􀸎􀨠􀙂􁭐􀸁􁌱􀌶􀝝􀹍􀣁􀓞􀓻􁇙􀾛􀰘􀙭􀓥􀒅watch 􀝢􁚆􀕿
􀓶􀥦:􀩒􀔭􀓞􀓻􀹚􀚠􀭌􁌱 znode 􁌱 exist watch􀒅􀦇􀺎􀣁􀨮􀲁􁒒􀷙􀭏􁬳􀴳􀹗
􁳵􁤩􀚠􀭌􀔧􀒅􀬚􀓬􁵋􀝸􀣁􀨮􀲁􁒒􁬳􀴳􀓤􀔏􀚹􀝈􀚢􁴻􀔧􀒅􁬯􁐿􀰘􀙭􀓥􀒅􁬯􀓻
watch 􀔪􀕯􀝢􁚆􀕿􁤩􀓶􀥦􀌶
8􀌵Watch 􀸎􁫷􁰁􁕆􁌱􀒅􀙌􀨫􀩪􀸎􀹜􀣈 JVM 􁌱 Callback􀒅􀹐􀛓􀢏􁒒􀝝􀸎􀨂
􀔧􀸎􀞈􀹍􁦡􁗝􀔧 Watcher 􁌱􀫲􀩞􁔄􀣳
5.1.2 Nginx􁶎􁦶􀓫􁷌
1􀌵􁧗􁥴􁯽􀓞􀓥􀕋􀔍􀸎 Nginx?
Nginx 􀸎􀓞􀓻 web 􀹐􀛓􀢏􀞾􀝍􀝻􀕤􁉘􀹐􀛓􀢏􀒅􁊠􀔭 HTTP􀌵HTTPS􀌵
SMTP􀌵POP3 􀞾 IMAP 􀜐􁦓􀌶
2􀌵􁧗􀚜􀔈 Nginx 􁌱􀓞􀔶􁇙􀯔􀌶
Nginx 􀹐􀛓􀢏􁌱􁇙􀯔􀛱􀳡:
􀝍􀝻􀕤􁉘/L7 􁨮􁫹􀣐􁤍􀢏
􀫍􀙁􀭗 Perl 􁥴􁯽􀢏
􀛖􀮾􀔫􁬰􀚫􀜋􁕆
􀝢􁊠􀔭􁯿􀷛􁖫􀙟 URL􀒅􀙍􀹍􁶋􀬉􀦅􁌱 PCRE 􀶪􀳮
3􀌵􁧗􁥴􁯽 Nginx 􀦇􀖜􀥒􁉘 HTTP 􁧗􀿢􀌶
Nginx 􀖵􁊠􀝍􀬫􀢏􀽜􀭗􀌶􀔆􀔪􀕯􀮗􁈾􁒵􀮇􀶙􀖢􁔮􁕹􀝎􀚊􀙵􀥓􀔪􀕯􁌱􀗞􀝩􀒅
􁬯􀻏􀷄􀴝􀩪􀝢􀕦􀕗􀥺􀴳􀨁􁧛􀝐􀒅􀣁􁧆􀨫􀖺􀓾􁧛􀝐􀚩􁖨􀙫􀜄􀬚􁬰􁤈􀥒􁉘􀌶􀜔
􀓻􁕚􁑕􀝢􀕦􀵉􀗀􀷄􀓡􀓻􀬚􀝎􁬳􀴳􀌶
4􀌵􀣁 Nginx 􀓾􀒅􀦇􀖜􀖵􁊠􀹚􀨧􀔎􁌱􀹐􀛓􀢏􀝷􁑍􀹶􁴥􀾊􀥒􁉘􁧗􀿢?
􀝝􁵱􀩙􁧗􀿢􀚢􁴻􁌱􀹐􀛓􀢏􀩪􀝢􀕦􀨧􀔎􀔅:
Server {listen 80;server_name “ “ ;return 444;
}
􁬯􁯾􀒅􀹐􀛓􀢏􀝷􁤩􀗛􁊸􀔅􀓞􀓻􁑮􀨁􁒧􀔀􀒅􀨙􀩙􀣁􁀌􀹍“􀔆􀹢”􀥧􀨁􀾧􁌱􀰘􀙭
􀓥􀜃􁯈􁧗􀿢􀒅􁘒􀓞􀓻􁇙􀾛􁌱 Nginx 􁌱􁶋􀺽􀙵􀕤􁎱 444 􁤩􁬬􀢧􀒅􀕗􁘒􁕣􀾊􁬳
􀴳􀌶
5􀌵 􀖵􁊠“􀝍􀝻􀕤􁉘􀹐􀛓􀢏”􁌱􀕽􁅩􀸎􀕋􀔍?
􀝍􀝻􀕤􁉘􀹐􀛓􀢏􀝢􀕦􁵌􁡐􁃠􀹐􀛓􀢏􁌱􀨂􀣁􀞾􁇙􀮄􀌶􀨙􊧌􀭮􀔰􁘶􁗑􀔯􀞾 web
􀹐􀛓􀢏􀔏􁳵􁌱􀓾􁳵􀩶􀌶􁬯􀩒􀔭􀨞􀙂􀷜􁶎􀹶􁧔􀸎􀮉􀦅􁌱􀒅􁇙􀚦􀸎􀭮􀰍􀖵􁊠
web 􀲓􁓕􀹐􀛓􀷸􀌶
6􀌵􁧗􀚜􀔈 Nginx 􀹐􀛓􀢏􁌱􀹋􀖯􁊠􁭔􀌶
Nginx 􀹐􀛓􀢏􁌱􀹋􀖯􁊠􁀩􀸎􀣁􁗑􁕶􀓤􁮱􁗟􀛖􀮾 HTTP 􀙖􀨻􀒅􀖵􁊠 SCGI􀌵
WSGI 􀬫􁊠􁑕􀬧􀹐􀛓􀢏􀌵􁊠􀔭􁚕􀹜􁌱 FastCGI 􀥒􁉘􁑕􀬧􀌶􀨙􁬮􀝢􀕦􀖢􀔅􁨮
􁫹􀣐􁤍􀢏􀌶
7􀌵􁧗􁥴􁯽 Nginx 􀹐􀛓􀢏􀓤􁌱 Master 􀞾 Worker 􁬰􁑕􀚓􀚦􀸎􀕋􀔍?
Master 􁬰􁑕:􁧛􀝐􀝊􁦧􀖌􁯈􁗝􀞾􁖌􀳮
Worker 􁬰􁑕:􀥒􁉘􁧗􀿢
8􀌵􁧗􁥴􁯽􀖦􀦇􀖜􁭗􁬦􀓧􀝶􀔭 80 􁌱􁒒􀝗􀭏􀞐 Nginx?
􀔅􀔧􁭗􁬦􀓞􀓻􀓧􀝶􁌱􁒒􀝗􀭏􀞐 Nginx􀒅􀖦􀮠􁶳􁬰􀙁/etc/Nginx/sitesenabled/
􀒅􀦇􀺎􁬯􀸎􁼕􁦊􀷈􀕯􀒅􁮎􀔍􀖦􀮠􁶳􀲑􀭏􀝷􀔅“default”􁌱􀷈􀕯􀌶􁖫
􁬋􀷈􀕯􀒅􀬚􀶱􁗝􀣁􀖦􀰮􁥝􁌱􁒒􀝗:
Like server { listen 81; }
9􀌵􁧗􁥴􁯽􀸎􀞈􀹍􀝢􁚆􀩙 Nginx 􁌱􁲙􁧏􀹊􀴘􀔅 502 􁲙􁧏􀌵503?
502 =􁲙􁧏􁗑􀙉 503 =􀹐􀛓􀢏􁩻􁫹
􀹍􀝢􁚆􀒅􀖕􀸎􀰍􀝢􀕦􁏟􀗛 fastcgi_intercept_errors 􁤩􁦡􁗝􀔅 ON􀒅
􀬚􀖵􁊠􁲙􁧏􁶭􁶎􀳰􀕥􀌶
Location / {fastcgi_pass 127.0.01:9001;fastcgi_intercept_error
s on;error_page 502 =503/error_page.html;#...}
10􀌵􀣁 Nginx 􀓾􀒅􁥴􁯽􀦇􀖜􀣁 URL 􀓾􀗛􁊸􀝌􀷑􁕚?
􁥝􀣁 URL 􀓾􀗛􁊸􀝌􀷑􁕚􀒅􀩪􀮠􁶳􀖵􁊠 merge_slashes_off ;
􁧍􁀩: merge_slashes [on/off]
􁼕􁦊􊧊: merge_slashes on
􁈾􀤹: http􀒅server
11􀌵􁧗􁥴􁯽 ngx_http_upstream_module 􁌱􀖢􁊠􀸎􀕋􀔍?
ngx_http_upstream_module 􁊠􀔭􀨧􀔎􀝢􁭗􁬦 fastcgi 􀖃􁭓􀌵proxy 􀖃
􁭓􀌵uwsgi 􀖃􁭓􀌵memcached 􀖃􁭓􀞾 scgi 􀖃􁭓􀳰􀕥􀹶􀭚􁊠􁌱􀹐􀛓􀢏􁕟􀌶
12􀌵􁧗􁥴􁯽􀕋􀔍􀸎 C10K 􁳯􁷌?
C10K 􁳯􁷌􀸎􀳰􀷫􁀩􀝶􀷸􀥒􁉘􀥟􁰁􀨮􀲁􁒒(10,000)􁌱􁗑􁕶􀥺􀴳􀨁􀌶
13􀌵􁧗􁴯􁬿 stub_status 􀞾 sub_filter 􀳰􀕥􁌱􀖢􁊠􀸎􀕋􀔍?
Stub_status 􀳰􀕥:􁧆􀳰􀕥􁊠􀔭􀔧􁥴 Nginx 􀭮􀚹􁇫􀮾􁌱􀭮􀚹􁇫􀮾􀒅􀦇􀭮􀚹
􁌱􁁚 􀛖􁬳􀴳􀒅􀴳􀝑􀞾􀥒􁉘􀭮􀚹􁧛/􀙟/􁒵􀮇􁬳􀴳􁌱􀯛􀷄
Sub_filter 􀳰􀕥:􀨙􁊠􀔭􀵤􁔱􀞾􀹊􀴘􀟥􀬫􀓾􁌱􀙖􀨻􀒅􀬚􀮳􁭛􀗥􀥔􁴯􀷯􁌱
􀷄􀴝
14􀌵􁥴􁯽 Nginx 􀸎􀞈􀶪􀳮􀩙􁧗􀿢􀜴􁖽􀚩􀓤􁃋?
􀰍􀝢􀕦􀖵􁊠 Nginx 􀽜􀣘 gunzip 􀩙􁧗􀿢􀜴􁖽􀚩􀓤􁃋􀌶gunzip 􀽜􀣘􀸎􀓞􀓻􁬦
􁄁􀢏􀒅􀨙􀝢􀕦􀩒􀓧􀶪􀳮“gzip”􁖫􁎱􀷜􁀩􁌱􀨮􀲁􀹢􀱲􀹐􀛓􀢏􀖵􁊠“􀙖􀨻􁖫
􁎱:gzip”􀹶􁥴􀜴􁖽􀟥􀬫􀌶
15􀌵􁥴􁯽􀦇􀖜􀣁 Nginx 􀓾􁞴􀮑􀭮􀚹􁌱􀷸􁳵?
􁥝􁞴􀮑 Nginx 􁌱􀭮􀚹􀷸􁳵􀒅􀮠􁶳􀖵􁊠 SSI 􀽜􀣘􀌵 $date_gmt 􀞾
$date_local 􁌱􀝒􁰁􀌶
Proxy_set_header THE-TIME $date_gmt;
16􀌵􁊠 Nginx 􀹐􀛓􀢏􁥴􁯽-s 􁌱􁍓􁌱􀸎􀕋􀔍?
􁊠􀔭􁬩􁤈 Nginx -s 􀝇􀷄􁌱􀝢􀲗􁤈􀷈􀕯􀌶
17􀌵􁥴􁯽􀦇􀖜􀣁 Nginx 􀹐􀛓􀢏􀓤􁂲􀛒􀽜􀣘?
􀣁􁖫􁦲􁬦􁑕􀓾􀒅􀮠􁶳􁭌􀳠 Nginx 􀽜􀣘􀒅􀢩􀔅 Nginx 􀓧􀶪􀳮􀽜􀣘􁌱􁬩􁤈􀷸􁳵
􁭌􀳠􀌶
5.2􀌵􀚓􀫲􀭗􁭗􁦔􁶎􁦶􀷆􁉘
5.2.1 RabbitMQ􁁾􀯳􀓾􁳵􀕯􁶎􁦶􀓫􁷌
1􀌵RabbitMQ 􀓾􁌱 broker 􀸎􀳰􀕋􀔍?cluster 􀝈􀸎􀳰􀕋􀔍?
broker 􀸎􀳰􀓞􀓻􀱲􀥚􀓻 erlang node 􁌱􁭦􁬋􀚓􁕟􀒅􀓬 node 􀓤􁬩􁤈􁍳
RabbitMQ 􀬫􁊠􁑕􀬧􀌶cluster 􀸎􀣁 broker 􁌱􀤚􁏐􀔏􀓤􀒅􀥀􀛒􀔧 node 􀔏􁳵
􀙈􀕁􀘲􀷄􀴝􁌱􁕅􀹳􀌶
2􀌵􀕋􀔍􀸎􀘲􀷄􀴝?􀘲􀷄􀴝􀚓􀔅􀟺􀔶􁔄􀣳?􀛱􀳡􀟺􀔶􀙖􀨻?􀓨 cluster 􁍘􀙉􁌱
􀘲􀷄􀴝 􀹍􀟺􀔶?􀘲􀷄􀴝􀸎􀦇􀖜􀗛􀨂􁌱?􀘲􀷄􀴝􀣁 cluster 􀓾􀸎􀦇􀖜􀚓􀫲􁌱?
􀣁􁶋 cluster 􀽜􀭗􀓥􀒅􀘲􀷄􀴝􀔆􁥝􀚓􀔅 Queue 􀘲􀷄􀴝(queue 􀝷􀨁􀞾􀪂􀯔
􁒵)􀌵 Exchange 􀘲􀷄􀴝(exchange 􀝷􀨁􀌵􁔄􀣳􀞾􀪂􀯔􁒵)􀌵Binding 􀘲􀷄􀴝
(􀨂􀶱􁪠􁊧􀙉􁔮􁌱􀺱􀲤􁤒)􀌵Vhost 􀘲􀷄􀴝(vhost 􁝜􀢱􀙖􁰒􀩒􀚹􀓣􁘏􁌱􀝷􀨁􁑮
􁳵􁕅􀹳􀞾􀨞􀙂􀪂􀯔􁦡􁗝)􀌶􀣁 cluster 􀽜􀭗􀓥􀒅􁬮􀛱􀳡 cluster 􀓾 node 􀖖􁗝
􀗞􀯳􀞾 node 􀙉􁔮􀗞􀯳􀌶􀘲􀷄􀴝􀳲􁆙 erlang node 􁌱􁔄􀣳􁏟􀨧􀸎􀕐􀗛􀨂􀔭
RAM 􀓾􀒅􁬮􀸎􀝶􀷸􀗛􀨂􀣁 RAM 􀞾 disk 􀓤􀌶􀘲􀷄􀴝􀣁 cluster 􀓾􀸎􀙂 node
􀚓􀫲􁌱􀌶
3􀌵RAM node 􀞾 disk node 􁌱􀜄􀚦?
RAM node 􀕐􀩙 fabric(􀜨 queue􀌵exchange 􀞾 binding􁒵 RabbitMQ􀤚􁏐􀺅
􀕯)􁍘􀙉􀘲􀷄􀴝􀗛􀨂􀚩􀙖􀨂􀓾􀒅􀖕 disk node 􀕿􀣁􀙖􀨂􀞾􁏺􁍏􀓾􀣐􁬰􁤈􀨂
􀘙􀌶RAM node 􀓤􀠔􀓞􀕿􀨂􀘙􀚩􁏺􁍏􀓤􁌱􀘲􀷄􀴝􀸎 cluster 􀓾􀖵􁊠􁌱 disk
node 􁌱􀣈􀣎􀌶􁥝􀿢􀣁 RabbitMQ cluster 􀓾􁛗􀩝􀨂􀣁􀓞􀓻 disk node 􀌶
4􀌵RabbitMQ 􀓤􁌱􀓞􀓻 queue 􀓾􀨂􀶱􁌱 message 􀸎􀞈􀹍􀷄􁰁􁴴􀚫?
􀝢􀕦􁦊􀔅􀸎􀷫􁴴􀚫􀒅􀢩􀔅􁴴􀚫􀝐􀙬􀔭􀹢􀢏􁌱􀙖􀨂􀒅􀖕􀸎􁁾􀯳􁬦􀥚􀕿􀩕􁛘􀥒
􁉘􀶴􁈲􁌱􀓥􁴳􀌶
5􀌵vhost 􀸎􀕋􀔍?􁩸􀕋􀔍􀖢􁊠?
vhost 􀝢􀕦􁉘􁥴􀔅􁡦􀳙 broker 􀒅􀜨 mini-RabbitMQ server􀌶􀙌􀙖􁮱􀣐􀞌􀹍
􁇿􁒈􁌱 queue􀌵exchange 􀞾 binding 􁒵􀒅􀖕􀹋􀹋􁯿􁥝􁌱􀸎􀒅􀙌􀳜􀹍􁇿􁒈􁌱
􀹦􁴴􁔮􁕹􀒅􀝢􀕦􀘉􀚩 vhost 􁝜􀢱􁌱􁊠􀲁􀴴􀚫􀌶􀭮􁆐􀒅􀕗 RabbitMQ 􁌱􀙂􀩴
􁥯􀬶􀒅vhost 􀝢􀕦􀖢􀔅􀓧􀝶􀹦􁴴􁵍􁐶 􁌱􀲋􀾧(􀓞􀓻􀙎􀣳􁌱􀖺􀧼􀩪􀸎􀓧􀝶􁌱􀬫
􁊠􀝢􀕦􁪒􀣁􀓧􀝶􁌱 vhost 􀓾)􀌶
6􀌵􀣁􀜔 node 􁔮􁕹􀞾􀥚 node 􀺅􀱮􁌱 cluster 􁔮􁕹􀓾􀥍􀸁 queue􀌵
exchange 􀒅􀕦􀝊􁬰􁤈 binding 􀕿􀹍􀕋􀔍􀓧􀝶?
􀭮􀖦􀣁􀜔 node 􀓤􀥍􀸁 queue 􀷸􀒅􀝝􁥝􁧆 node 􀓤􁍘􀙉􀘲􀷄􀴝􁬰􁤈􀔧􀝒
􀹅􀒅􀖦􀩪􀕿􀮑􀚩 Queue.Declare-ok 􀢧􀬫;􁘒􀣁 cluster 􀓤􀥍􀸁 queue 􀒅􀚞􁥝
􀿢 cluster 􀓤􁌱􀙂􁮱 node 􁮷􁥝􁬰􁤈􀘲􀷄􀴝􀱮􀛑􀹅􀷛􀒅􀲍􀕿􀮑􀚩
Queue.Declare-ok 􀢧􀬫􀌶􀝚􀥘􀒅􁝑 node 􁔄􀣳 􀔅 RAM node 􀚞􀝒􀹅􁌱􀷄􀴝
􀕐􀗛􀨂􀣁􀙖􀨂􀓾􀒅􁝑􁔄􀣳􀔅 disk node 􀚞􁬮􁥝􀝒􀹅􀗛􀨂􀣁􁏺􁍏􀓤􁌱􀷄􀴝􀌶
7􀌵􀨮􀲁􁒒􁬳􀴳􀚩 cluster 􀓾􁌱􀕱􀰺 node 􀓤􀸎􀞈􁮷􁚆􀾋􀬉􀫡􀖢?
􀸎􁌱􀌶􀨮􀲁􁒒􀰽􁥧􀓧􀚩􀹍􀖜􀓧􀝶􀌶
8􀌵􁝑 cluster 􀓾􀳜􀹍􀺤􀓻 queue 􁌱 owner node 􀥦􀶴􀔧􀒅􀓬􁧆 queue
􁤩􀥍􀸁􀙍􀹍 durable 􀪂􀯔􀒅􀸎􀞈􁚆􀥜􀱮􀛑􀕗􀙌􀕜 node 􀓤􁯿􀷛􀥍􀸁􁧆
queue ?
􀓧􁚆􀒅􀣁􁬯􁐿􀰘􀙭􀓥􀒅􀩙􀮑􀚩 404 NOT_FOUND 􁲙􁧏􀌶􀝝􁚆􁒵 queue 􀲅
􀪂􁌱 node 􀯩􀥔􀝸􀲍􁚆􀖵􁊠􁧆 queue 􀌶􀖕􁝑􁧆 queue 􀹜􁫝􀓧􀙍􀹍 durable
􀪂􀯔􀒅􀚞􀝢􀣁􀙌􀕜 node 􀓤􁯿􀷛􀥍􀸁􀌶
9􀌵cluster 􀓾 node 􁌱􀥦􀶴􀕿􀩒 consumer 􀔾􁊞􀕋􀔍􀭽􀟥?􁝑􀸎􀣁
cluster 􀓾􀚠􀭌􀔧 mirrored queue 􀒅􁬯􀷸 node 􀥦􀶴􀕿􀩒 consumer 􀔾
􁊞􀕋􀔍􀭽􀟥?
􁝑􀸎 consumer 􀲅􁬳􀴳􁌱􁮎􀓻 node 􀥦􀶴(􀷫􁦞􁧆 node 􀸎􀞈􀔅 consumer
􀲅􁦈􁴅 queue 􁌱 owner node)􀒅􀚞 consumer 􀕿􀣁􀝎􁈿 TCP 􁬳􀴳􀷙􀭏􀷸􀒅
􀳲􀺽􀙵􁤈􀔅􀲗􁤈􁯿􁬳􁭦􁬋􀒅􀬚􀻑􀴝“Assume Nothing”􀜻􀚞􁯿􀭌􁍘􀬫􁌱
fabric 􀜨􀝢􀌶􁝑􀸎􀥦􀶴􁌱 node 􀔅 consumer 􁦈􁴅 queue 􁌱owner node􀒅
􀚞 consumer 􀝝􁚆􁭗􁬦 Consumer Cancellation Notification 􀹢􀚫􀹶􀼄􁁥􀓨
􁧆 queue 􁦈􁴅􀙉􁔮􁌱􁕣􀾊􀒅􀞈􀚞􀕿􀚊􁈿􀘞􁒵􀜩􁀌􀹍􀕱􀖜􁁾􀯳􀹶 􀚩􁌱􁳯
􁷌􀌶
10􀌵􁚆􀥜􀣁􀣈􁉘􀓤􀚓􀭏􁌱􀓧􀝶􀷄􀴝􀓾􀮞􀖵􁊠 RabbitMQ cluster 􀔍?
􀓧􁚆􀌶
􁒫􀓞􀒅􀖦􀷫􁀩􀴴􀚫􀲅􀚠􀭌􁌱 queue 􀨫􁴬􀚓􀫲􀣁 cluster 􁯾􁌱􀟺􀓻 node 􀓤
(􀓞􁛱􀖵􁊠 HAProxy + cluster 􀽜􀣳􀷸􁮷􀸎􁬯􀻏)􀒅􁬯􀝢􁚆􀕿􀩕􁛘􀝱􁐿􁪜􀣈􀤒
􁦢􁳯􀷸􁌱􀬉􁥠􁳯􁷌;
􁒫􀔫􀒅Erlang 􁌱 OTP 􁭗􀗞􀻛􀺝􀩒􀭊􁬴􁌱􀨻􀮤􀬶􀹍􁴴􀒅􁬯􀝢􁚆􀕿􁥶􀝎􀝱􁐿
􁩻􀷸􀒅􀩕􁛘􀓱􀛓􁋜􀔭􀥒􁉘;
􁒫􀓣􀒅􀣁􀬠􀤒􁗑􀓤􁌱􁬳􀴳􀥦􀶴􁳯􁷌􀩙􀩕􁛘􁕪􀙎􁌱“􁚏􁤯”􁳯􁷌􀒅􁘒
RabbitMQ 􁍓􀚹􀷫􁀩􀥒􁉘(􁧆􁳯􁷌􀔆􁥝􀸎􁧔 Mnesia)􀌶
11􀌵􀔅􀕋􀔍 heavy RPC 􁌱􀖵􁊠􀣋􀸧􀓥􀓧􀭌􁦓􁯻􁊠 disk node
heavy RPC 􀸎􀳰􀣁􀓱􀛓􁭦􁬋􀓾􁹛􁷇􁧣􁊠 RabbitMQ 􀵉􀗀􁌱 RPC 􀹢􀚫􀒅􀩕
􁛘􀓧􀷙􀚠􀭌􀌵 􁲀􀾪 reply queue 􀒅􁬰􁘒􁭜􀱮 disk node 􁌱􀯔􁚆􁳯􁷌(􀢩􀔅􀕿
􁰒􀩒􀘲􀷄􀴝􀓧􀷙􀙟􁍏)􀌶􀲅􀕦􀣁􀖵􁊠 RPC 􀹢􀚫􀷸􁵱􁥝􁘍􁡤􁛔􁫝􁌱􀓱􀛓􀣋
􀸧􀌶
12􀌵􀝻􀓧􀨂􀣁􁌱 exchange 􀝎 publish 􁁾􀯳􀕿􀝎􁊞􀕋􀔍?􀝻􀓧􀨂􀣁􁌱
queue 􀲗􁤈consume 􀛖􀖢􀕿􀝎􁊞􀕋􀔍?
􁮷􀕿􀶭􀚩 Channel.Close 􀗞􀕥􀞞􀔏􀓧􀨂􀣁(􀙖􀞌􀜻􀢩 404 NOT_FOUND)􀌶
13􀌵 routing_key 􀞾 binding_key 􁌱􀹋􀥟􁳩􀬶􀸎􀥚􀩝?
255 􀨁􁜓􀌶
14􀌵RabbitMQ 􊧋􁦜􀝎􁭆􁌱 message 􀹋􀥟􀝢􁬡􀥚􀥟?
􀻑􀴝 AMQP 􀜐􁦓􁥢􀨧􀒅􁁾􀯳􀖛􁌱􀥟􀩜􁊧 64-bit 􁌱􊧊􀹶􀳰􀨧􀒅􀲅􀕦􀖦􀩪􀝢
􀕦􁎣􁭲􀚩􀬬􁚆􀝎􀥚􀥟􁌱􀷄􀴝􀔧􀌶
15􀌵􀕋􀔍􀰘􀙭􀓥 producer 􀓧􀔆􀛖􀚠􀭌 queue 􀸎􀨞􀙂􁌱?
1.message 􀸎􊧋􁦜􀓶􀥦􁌱;
2.􀨫􁈿􀔧􁰒􀩒􀹚􀥒􁉘􁁾􀯳􁌱 republish 􀛑􁚆(􀖺􀦇􁯻􁊠 Publisher Confirm 􀹢
􀚫)􀌶
16􀌵“dead letter”queue 􁌱􁊠􁭔?
􀭮􁁾􀯳􁤩 RabbitMQ server 􀲭􁭓􀚩 consumer 􀝸􀒅􀖕 consumer 􀜩􁭗􁬦
Basic.Reject 􁬰􁤈􀔧􀳏􁕷􀷸(􀝶􀷸􁦡􁗝 requeue=false)􀒅􁮎􀔍􁧆􁁾􀯳􀕿􁤩􀶱
􀙁“dead letter”queue 􀓾􀌶 􁧆 queue 􀝢􁊠􀔭􀴭􀺱 message 􁤩 reject 􀱲
undeliver 􁌱􀜻􀢩􀌶
17􀌵􀕋􀔍􁧔􀗛􁦤 message 􁤩􀝢􁶌􀳮􀔋􀛸􁌱􀹵􀕯􀸎 queue 􀞾 exchange
􀙍􀹍 durable 􀪂􀯔􀒅􀝶􀷸 message 􀙍􀹍 persistent 􀪂􀯔􀲍􁤈?
binding 􀙉􁔮􀝢􀕦􁤒􁐏􀔅 exchange – binding – queue 􀌶􀕗􀷈􀻩􀓾􀱯􀕪􁎣
􁭲􀒅􁝑􁥝􀿢􀲭􁭓􁌱 message 􁚆􀥜􀓧􀓶􀥦􀒅􁥝􀿢 message 􀹜􁫝􁦡􁗝
persistent 􀪂􀯔􀒅􁥝􀿢 exchange 􀞾 queue 􁮷􁦡􁗝 durable 􀪂􀯔􀌶􀙌􀨫􁬯􁳯
􁷌􀝢􀕦􁬯􀔍􀰮􀒅􁝑 exchange 􀱲 queue 􀹚􁦡􁗝 durable 􀪂􀯔􀒅􀚞􀣁􀙌
crash 􀔏􀝸􀩪􀕿􀷫􁀩􀯩􀥔􀒅􁮎􀔍􀜨􀖵 message 􁦡􁗝􀔧 persistent 􀪂􀯔􀒅􀕖
􁆐􀨂􀣁 message 􁡱􁆐􁚆􀯩􀥔􀖕􀜩􀷫􀥒􀨻􁫝􁌱􁳯􁷌;􀝶􁉘􀒅􁝑 message 􀹜􁫝
􀹚􁦡􁗝 persistent 􀪂􀯔􀒅􀚞 message 􁌱􀳮􀔋􀛸􀹅􀷫􀕗􁧨􁩸􀌶
18􀌵􀕋􀔍􀰘􀙭􀓥􀕿􀚊􁈿 blackholed 􁳯􁷌?
blackholed 􁳯􁷌􀸎􀳰􀒅􀝻 exchange 􀲭􁭓􀔧 message 􀒅􁘒􁊧􀔭􀝱􁐿􀜻􀢩􀩕
􁛘􁧆 message 􀓶􀥦􀒅􀖕􀝎􁭆􁘏􀜩􀓧􁎣􁭲􀌶􀝢􀩕􁛘 blackholed 􁌱􀰘􀙭:
1.􀝻􀹚􁕬􀨧 queue 􁌱 exchange 􀝎􁭆 message;
2.exchange 􀕦 binding_key key_A 􁕬􀨧􀔧 queue queue_A 􀒅􀖕􀝻 􁧆
exchange 􀝎􁭆 message 􀖵􁊠􁌱 routing_key 􀜩􀸎 key_B 􀌶
19􀌵􀦇􀖜􁴠􀾊􀚊􁈿 blackholed 􁳯􁷌?
􁀌􀹍􁇙􀚦􀦅􁌱􀛐􁀩􀒅􀝝􁚆􀣁􀙍􀖛􀨫􁪢􀓾􁭗􁬦􀝱􁐿􀷜􀭗􀗛􁦤􁍘􀙉 fabric 􁌱􀨂
􀣁􀌶􀝚􀥘􀒅􀦇􀺎􀣁􀲗􁤈 Basic.Publish 􀷸􁦡􁗝 mandatory=true 􀒅􀚞􀣁􁭬􀚩
􀝢􁚆􀚊􁈿 blackholed 􀰘􀙭 􀷸􀒅􀹐􀛓􀢏􀕿􁭗􁬦􁬬􀢧 Basic.Return 􀞞􀔏􀭮􀚹
message 􀷫􁀩􁤩􀾋􁏟􀲭􁭓(􀙖􀞌􀜻􀢩 312 NO_ROUTE)􀌶
20􀌵Consumer Cancellation Notification 􀹢􀚫􁊠􀔭􀕋􀔍􀣋􀸧?
􁊠􀔭􀗛􁦤􀭮􁳒􀘟 queue 􀓾 master 􀳯􀴧􀷸􀒅􁬳􀴳􀚩 slave 􀓤􁌱 consumer 􀝢
􀕦􀶭􀚩􁛔􁫝 consume 􁤩􀝐􁁾􁌱􁭗􁎣􀒅􁬰􁘒􀝢􀕦􁯿􀷛􀲗􁤈 consume 􀛖􀖢􀕗
􀷛􁭌􀚊􁌱 master 􀚊􁞴􀮑􁁾􀯳􀌶􁝑􀓧􁯻􁊠􁧆􀹢􀚫􀒅􁬳􀴳􀚩 slave 􀓤􁌱
consumer 􀩙􀓧􀕿􀰽􁎣 master 􀳯􀴧􁬯􀓻􀔪􀰘􀒅􀩕􁛘􀝸􁖅􀷫􁀩􀙚􀶭􀚩􀷛
master 􀬠􀶎􀚊􀹶􁌱 message 􀌶􀝚􀥘􀒅􀢩􀔅􀣁􁳒􀘟 queue 􀽜􀭗􀓥􀒅􀨂􀣁􀩙
message 􁬰􁤈 requeue 􁌱􀝢􁚆􀒅􀲅􀕦􀨫􁈿 consumer 􁌱􁭦􁬋􀷸􁵱􁥝􁚆􀥜􀾋
􁏟􀥒􁉘􀚊􁈿􁯿􀥔 message 􁌱􀰘􀙭􀌶
21􀌵Basic.Reject 􁌱􁊠􁀩􀸎􀕋􀔍?
􁧆􀗞􀕥􀝢􁊠􀔭 consumer 􀩒􀶭􀚩􁌱 message 􁬰􁤈 reject 􀌶􁝑􀣁􁧆􀗞􀕥􀓾􁦡
􁗝 requeue=true􀒅􀚞􀭮 RabbitMQ server 􀶭􀚩􁧆􀳏􁕷􀗞􀕥􀝸􀒅􀕿􀩙􁧆
message 􁯿􀷛􀝎􁭆􀚩􀓥􀓞􀓻􀥒􀔭 consume 􁇫􀮾􁌱 consumer 􀥒(􁉘􁦞􀓤􀕖
􀝢􁚆􀩙􁧆􁁾􀯳􀝎􁭆􁕳􀭮􀚹 consumer)􀌶􁝑􁦡􁗝 requeue=false 􀒅􀚞
RabbitMQ server 􀣁􀶭􀚩􀳏􁕷􀗞􀕥􀝸􀒅􀩙􁍗􀴳􀩙􁧆 message 􀕗 queue 􀓾􁑏
􁴻􀌶
􀝚􀥘􀓞􁐿􁑏􁴻 queue 􀓾 message 􁌱􀩜􀲦􀫣􀸎􀒅consumer 􀢧􀥔 Basic.Ack
􀖕􀓧􀩒􁞴􀝐􀚩􁌱 message 􀘉􀕱􀖜􀥒􁉘􀌶
􁘒 Basic.Nack 􀸎􀩒 Basic.Reject 􁌱􀲘􀪀􀒅􀕦􀶪􀳮􀓞􀽺􀳏􁕷􀥚􀹵 message
􁌱􁚆􀛎􀌶
22􀌵􀔅􀕋􀔍􀓧􀬫􁧆􀩒􀲅􀹍􁌱 message 􁮷􀖵􁊠􀳮􀔋􀛸􀹢􀚫?
􁸒􀘶􀒅􀮠􁆐􀩕􁛘􀯔􁚆􁌱􀓥􁴳􀒅􀢩􀔅􀙟􁏺􁍏􀾲􀙟 RAM 􀱌􁌱􀥚􀒅message 􁌱
􀞃􀝺􁰁􀝢􁚆􀹍 10 􀗭􁌱􀫧􁪗􀌶􀙌􀽺􀒅message 􁌱􀳮􀔋􀛸􀹢􀚫􁊠􀣁
RabbitMQ 􁌱􀙖􁗝 cluster 􀷜􀻜􀷸􀕿􀚊􁈿“􀣗􁇂”􁳯􁷌􀌶􁎟􁍛􁅩􀣁􀔭􀒅􁝑
message 􁦡􁗝􀔧 persistent 􀪂􀯔􀒅􀖕 queue 􀹚􁦡􁗝 durable 􀪂􀯔􀒅􁮎􀔍􀭮
􁧆 queue 􁌱 owner node 􀚊􁈿􀭑􀬉􀝸􀒅􀣁􀹚􁯿􀭌􁧆 queue 􀚹􀒅􀝎􀮃􁧆
queue 􁌱 message 􀩙􁤩 blackholed ;􁝑 message 􁦡􁗝􀔧 persistent 􀪂􀯔􀒅
􀝶􀷸 queue 􀔞􁦡􁗝􀔧 durable 􀪂􀯔􀒅􁮎􀔍􀭮 queue 􁌱 owner node 􀭑􀬉􀓬
􀷫􁀩􁯿􀞐􁌱􀰘􀙭􀓥􀒅􀚞􁧆 queue 􀷫􁀩􀣁􀙌􀕜 node 􀓤􁯿􀭌􀒅􀝝􁚆􁒵􀮇􀙌
owner node 􁯿􀞐􀝸􀒅􀲍􁚆􀯩􀥔􁧆 queue 􁌱􀖵􁊠􀒅􁘒􀣁􁬯􀾧􀷸􁳵􀙖􀝎􁭆􁕳
􁧆 queue 􁌱 message 􀩙􁤩 blackholed 􀌶􀲅 􀕦􀒅􀸎􀞈􁥝􀩒 message 􁬰􁤈
􀳮􀔋􀛸􀒅􁵱􁥝􁖓􀝳􁘍􁡤􀯔􁚆􁵱􁥝􀒅􀕦􀝊􀝢􁚆􁭬􀚩􁌱􁳯􁷌􀌶􁝑􀰮 􁬡􀚩
100,000 􀹵/􁑁􀕦􀓤􁌱􁁾􀯳􀞃􀝺􁰁(􀜔 RabbitMQ 􀹐􀛓􀢏)􀒅􀚞􁥝􀔍􀖵􁊠􀙌􀕜
􁌱􀷜􀭗􀹶􁏟􀗛 message 􁌱􀝢􁶌 delivery 􀒅􁥝􀔍􀖵􁊠􁶋􀬉􀮳􁭛􁌱􀨂􀘙􁔮􁕹􀕦
􀶪􀳮􀙂􀳮􀔋􀛸(􀖺􀦇􀖵 􁊠 SSD)􀌶􀝚􀥘􀓞􁐿􀥒􁉘􀜻􀚞􀸎:􀕐􀩒􀙉􁲫􁁾􀯳􀖢􀳮􀔋
􀛸􀥒􁉘(􀻑􀴝􀓱􀛓􁯿􁥝􁑕􀬶)􀒅􀓬􀬫 􁧆􀗛􁦤􀙉􁲫􁁾􀯳􁌱􁰁􀓧􀕿􀩕􁛘􀯔􁚆􁊒
􁷀􀌶
23􀌵RabbitMQ 􀓾􁌱 cluster􀌵mirrored queue􀒅􀕦􀝊 warrens 􀹢􀚫􀚓
􀚦􁊠􀔭􁥴􀙬 􀕋􀔍􁳯􁷌?􀨂􀣁􀟺􀔶􁳯􁷌?
cluster􀸎􀔅􀔧􁥴􀙬􀭮 cluster 􀓾􁌱􀕱􀰺 node 􀥦􀶴􀝸􀒅producer 􀞾
consumer 􀣐􀝢􀕦 􁭗􁬦􀙌􀕜 node 􁖀􁖅􀫡􀖢􀒅􀜨􀵉􁹛􀔧􀝢􁊠􀯔;􀝚􀥘􀝢􀕦􁭗
􁬦􀥀􀛒 node 􀷄􁰁􀥀􀛒 cluster 􁌱􁁾􀯳􀞃􀝺􁰁􁌱􁍓􁌱􀌶cluster 􀹜􁫝􀓧􁨮􁨱
message 􁌱􀝢􁶌􀯔􁳯􁷌(􁧆􁳯􁷌􁊧 producer 􁭗 􁬦􀝱􁐿􀹢􀚫􁛔􁤈􁥴
􀙬);cluster 􀷫􁀩􁥴􀙬􁪜􀷄􀴝􀓾􀮞􁌱􁳯􁷌(􀜨􁚏􁤯􁳯􁷌)􀌶
􀝚􀥘􀒅􀣁 cluster 􀚹􀖵􁊠 HAProxy 􀝢􀕦􁥴􀙬 node 􁌱􁭌􀳠􁳯􁷌􀒅􀜨􀓱􀛓􀷫
􁵱􁎣􁭲 cluster 􀓾􀥚􀓻 node 􁌱 ip 􀣈􀣎􀌶􀝢􀕦􀚥􁊠 HAProxy 􁬰􁤈􀥦􀶴 node
􁌱􀴱􁁥􀒅􀝢􀕦􀖢􁨮􁫹􀣐􁤍􀌶
Mirrored queue 􀸎􀔅􀔧􁥴􀙬􀖵􁊠 cluster 􀷸􀲅􀚠􀭌􁌱 queue 􁌱􀨠􀷆􀗞􀯳􀕐
􀨂􀣁􀔭􀜔􀓞 node 􀓤􁌱􁳯􁷌􀒅􀕗􀝚􀓞􀓻􁥯􀬶􀥀􀛒􀝢􁊠􀯔􀌶􁝑􀰮􀾋􁏟􀖵􁊠􁧆
􀛑􁚆􀒅􁵱􁥝􀗛􁦤:
1.consumer 􁵱􁥝􀶪􀳮 Consumer Cancellation Notification 􀹢􀚫;
2.consumer 􀮠􁶳􁚆􀥜􀾋􁏟􀥒􁉘􁯿􀥔 message 􀌶
Warrens􀸎􀔅􀔧􁥴􀙬 cluster 􀓾 message 􀝢􁚆􁤩 blackholed 􁌱􁳯􁷌􀒅􀜨􀓧
􁚆􀴳􀝑 producer 􀓧􀘊 republish message 􀖕 RabbitMQ server 􀷫􀢧􀬫􁌱􀰘
􀙭􀌶Warrens 􀹍􀓷􁐿􀺅􀱮􀷜􀭗􀒓
􀓞􁐿􀽜􀣳􀸎􀓷􀝣􁇿􁒈􁌱 RabbitMQ server + HAProxy 􀒅􀙌􀓾􀓷􀓻 server 􁌱
􁇫􀮾􀚓􀚦􀔅 active 􀞾 hot-standby 􀌶􁧆􀽜􀣳􁌱􁇙􁅩􀔅:􀓷􀝣 server 􀔏􁳵􀷫􀕱
􀖜􀷄􀴝􀙈􀕁􀞾􀜐􁦓􀔻􀔰􀒅􀓷􀝣 server 􀝢􀕦􀤚􀔭􀓧􀝶􁌱 RabbitMQ 􁇇􀹜􀌶
􀝚􀓞􁐿􀽜􀣳􀔅􀓷􀝣􀙈􀕁􀨂􀘙􁌱 RabbitMQ server + keepalived􀒅􀙌􀓾􀓷􀓻
server 􁌱􁇫􀮾􀚓 􀚦􀔅 active 􀞾 cold-standby􀌶
􁧆􀽜􀣳􁌱􁇙􁅩􀔅:􀓷􀝣 server 􀤚􀔭􀙈􀕁􀨂􀘙􀝢􀕦􀘉􀚩􀨠􀙂 􀯩􀥔􀒅􁥝􀿢􀮠􁶳
􀤚􀔭􀨠􀙂􁍘􀝶􁌱 RabbitMQ 􁇇􀹜􀌶
Warrens 􀽜􀣳􀨂􀣁􁌱􁳯􁷌:
􀩒􀔭􁒫􀓞􁐿􀽜􀣳􀒅􁡱􁆐􁉘􁦞􀓤􁦖􀓧􀕿􀓶􀥦􁁾􀯳􀒅􀖕􁝑􀣁􁧆􀽜􀣳􀓤􀖵􁊠􀳮􀔋
􀛸􀹢􀚫􀒅􀩪􀕿􀚊􁈿􁬯􀻏􀓞􁐿􀰘􀙭􀒅􀜨􁝑􀖢􀔅 active 􁌱 server 􀭑􀬉􀝸􀒅􀳮􀔋
􀛸 􀣁􁧆 server 􀓤􁌱􁁾􀯳􀩙􀸮􀷸􀷫􁀩􁤩 consume 􀒅􀢩􀔅􀾌􀷸􁧆 queue 􀩙􀷫
􁀩􀣁􀖢􀔅 hot- standby 􁌱 server 􀓤􁤩􁯿􀭌􀒅􀲅􀕦􀒅􀝝􁚆􁒵􀚩􀭑􀬉􁌱 active
server 􀯩􀥔􀝸􀒅􀲍􁚆􀕗􀙌􀓤􁌱 queue 􀓾􁞴􀝐􁍘􀬫􁌱 message 􁬰􁤈􀥒􁉘􀌶
􁘒􀩒􀔭􀓱􀛓􀹶􁧔􀒅􁵱􁥝􀙍􀹍:a.􀰽􁎣 AMQP 􁬳􀴳􀷙􀭏􀝸􁯿􀭌􀝱􁐿 fabric 􁌱􁚆
􀛎;b.􀰽􁎣 active server 􀯩􀥔􁌱􁚆􀛎;c.􀚔􀴘􀢧 active server 􁌱􀷸􀹢􀴴􀚫􀒅􀕦
􀝊􀚔􀢧􀝸􀒅􁰒􀩒 message 􀘶􀝸􁶲􀬧􀔾􁊞􁌱􀝒􀛸􁬰􁤈􀥒􁉘􁌱􁚆􀛎􀌶
􀩒􀔭􁒫􀔫􁐿􀽜􀣳􀒅􀢩􀔅􀸎􀤚􀔭􀙈􀕁􀨂􀘙􁌱􀽜􀭗􀒅􀲅􀕦􀩕􁛘 active server 􀭑
􀬉􁌱􀹵􀕯􀒅􀝢􁚆􀝶􀻏􀕿􀩕􁛘 cold-standby server 􀭑􀬉;􀝚􀥘􀒅􀣁􁧆􀽜􀣳􀓥􀒅
􁥝􀿢 active 􀞾 cold-standby 􁌱 server 􀮠􁶳􀙍􀹍􁍘􀝶􁌱 node 􀝷􀞾 UID 􀒅􀞈
􀚞􀩙􀔾􁊞􁦢􁳯􀹦􁴴􁳯􁷌;􀹋􀝸􀒅􁊧􀔭􁧆􀽜􀣳􀸎􀙯􀥓􀷜􀻜􀒅􀶳􀷫􁀩􀗛􁦤 coldstandby
server 􁚆􀣁􀖦􁥝􀿢􁌱􀷸􁴴􀙖􀱮􀛑􀞐􀛖􀌶
5.2.2 Kafka􁶎􁦶􀓫􁷌
1.Kafka 􁌱􁦡􁦇􀷸􀕋􀔍􀻏􁌱􀞫?
Kafka 􀩙􁁾􀯳􀕦 topic 􀔅􀜔􀖖􁬰􁤈􀭭􁕑
􀩙􀝻 Kafka topic 􀝎􀫲􁁾􀯳􁌱􁑕􀬧􀱮􀔅 producers.
􀩙􁶼􁦈 topics 􀬚􁁾􁩇􁁾􀯳􁌱􁑕􀬧􀱮􀔅 consumer.
Kafka 􀕦􁵞􁗭􁌱􀷜􀭗􁬩􁤈􀒅􀝢􀕦􁊧􀓞􀓻􀱲􀥚􀓻􀹐􀛓􁕟􀱮􀒅􀾯􀓻􀹐􀛓􀝞􀘉􀓞
􀓻 broker. producers 􁭗􁬦􁗑􁕶􀩙􁁾􀯳􀝎􁭆􀚩 Kafka 􁵞􁗭􀒅􁵞􁗭􀝻􁁾􁩇􁘏􀵉
􀗀􁁾􀯳
2.􀷄􀴝􀖃􁬌􁌱􀔪􁇔􀨧􀔎􀹍􀟺􀓣􁐿?
􀷄􀴝􀖃􁬌􁌱􀔪􀛓􀨧􀔎􁭗􀬉􀹍􀕦􀓥􀓣􁐿􁕆􀚦:
(1)􀹋􀥚􀓞􀽺: 􁁾􀯳􀓧􀕿􁤩􁯿􀥔􀝎􁭆􀒅􀹋􀥚􁤩􀖃􁬌􀓞􀽺􀒅􀖕􀔞􀹍􀝢􁚆􀓞􀽺􀓧
􀖃􁬌
(2)􀹋􀩝􀓞􀽺: 􁁾􀯳􀓧􀕿􁤩􁄋􀝎􁭆􀒅􀹋􀩝􁤩􀖃􁬌􀓞􀽺􀒅􀖕􀔞􀹍􀝢􁚆􁤩􁯿􀥔􀖃
􁬌.
(3)􁔜􁏟􁌱􀓞􀽺(Exactly once): 􀓧􀕿􁄋􀖃􁬌􀔞􀓧􀕿􁯿􀥔􀖃􁬌,􀾯􀓻􁁾􀯳􁮷􀖃􁬌
􁤩􀓞􀽺􁘒􀓬􀕐􀕐􁤩􀖃􁬌􀓞􀽺􀒅􁬯􀸎􀥟􀨹􀲅􀹗􀹕􁌱
3.Kafka 􀚣􀷙􀓞􀓻􁜓􁅩􀸎􀞈􁬮􁁚􁍳􀹍􁮎􀓷􀓻􀹵􀕯?
(1)􁜓􁅩􀮠􁶳􀝢􀕦􁖌􀲷􀞾 ZooKeeper 􁌱􁬳􀴳􀒅Zookeeper 􁭗􁬦􀮞􁪡􀹢􀚫􀼄􀺱
􀾯􀓻􁜓􁅩􁌱􁬳􀴳
(2)􀦇􀺎􁜓􁅩􀸎􀓻 follower,􀕜􀮠􁶳􁚆􀝊􀷸􁌱􀝶􀾍 leader 􁌱􀙟􀶙􀖢􀒅􀭊􀷸􀓧􁚆
􀥡􀔋
4.producer 􀸎􀞈􁍗􀴳􀩙􀷄􀴝􀝎􁭆􀚩 broker 􁌱 leader(􀔆􁜓􁅩)?
producer 􁍗􀴳􀩙􀷄􀴝􀝎􁭆􀚩 broker 􁌱 leader(􀔆􁜓􁅩)􀒅􀓧􁵱􁥝􀣁􀥚􀓻􁜓􁅩
􁬰􁤈􀚓􀝎􀒅􀔅􀔧􀬆􀛗 producer 􀘉􀚩􁬯􁅩􀒅􀲅􀹍􁌱 Kafka 􁜓􁅩􁮷􀝢􀕦􀝊􀷸
􁌱􀞞􁎣:􀟺􀔶􁜓􁅩􀸎􁁚􀛖􁌱􀒅􁍓􀺽 topic 􁍓􀺽􀚓􀜄􁌱 leader 􀣁􀟺􀌶􁬯􀻏
producer 􀩪􀝢􀕦􁍗􀴳􀩙􁁾􀯳􀝎􁭆􀚩􁍓􁌱􀣈􀔧
5􀌵Kafa consumer 􀸎􀞈􀝢􀕦􁁾􁩇􀳰􀨧􀚓􀜄􁁾􀯳?
Kafa consumer 􁁾􁩇􁁾􀯳􀷸􀒅􀝻 broker 􀝎􀚊"fetch"􁧗􀿢􀝄􁁾􁩇􁇙􀨧􀚓􀜄􁌱
􁁾􀯳􀒅consumer 􀳰􀨧􁁾􀯳􀣁􀷭􀮪􀓾􁌱􀘇􁑏􁰁(offset)􀒅􀩪􀝢􀕦􁁾􁩇􀕗􁬯􀓻
􀖖􁗝􀭏􀦤􁌱􁁾􀯳􀒅customer 􀳜􀹍 􀔧 offset 􁌱􀴴􀚫􀹦􀒅􀝢􀕦􀝻􀝸􀢧􁃻􀝄􁯿
􀷛􁁾􁩇􀔏􀚹􁌱􁁾􀯳􀒅􁬯􀸎􀮉􀹍􀰺􀔎􁌱
6􀌵Kafka 􁁾􀯳􀸎􁯻􁊠 Pull 􀽜􀭗􀒅􁬮􀸎 Push 􀽜􀭗?
Kafka 􀹋􀚡􁘍􁡤􁌱􁳯􁷌􀸎􀒅customer 􀬫􁧆􀕗 brokes 􀳉􀝐􁁾􀯳􁬮􀸎 brokers
􀩙􁁾􀯳􀴵􁭆􀚩 consumer􀒅􀔞􀩪􀸎 pull 􁬮 push􀌶􀣁􁬯􀷜􁶎􀒅Kafka 􁭽􀮗􀔧
􀓞􁐿􀥟􁮱􀚓􁁾􀯳􁔮􁕹􀙈􀝶􁌱􀖃􁕹􁌱􁦡􁦇:producer 􀩙􁁾􀯳􀴵􁭆􀚩 broker􀒅
consumer 􀕗 broker 􀳉􀝐􁁾􀯳
􀓞􀔶􁁾􀯳􁔮􁕹􀾲􀦇 Scribe 􀞾 Apache Flume 􁯻􁊠􀔧 push 􀽜􀭗􀒅􀩙􁁾􀯳􀴵
􁭆􀚩􀓥􁃋􁌱 consumer􀌶
􁬯􀻏􀘉􀹍􀦅􀥒􀔞􀹍􀣕􀥒:􁊧 broker 􀙬􀨧􁁾􀯳􀴵􁭆􁌱􁭛􁈲􀒅􀩒􀔭􀓧􀝶􁁾􁩇􁭛
􁈲􁌱 consumer 􀩪􀓧􀥡􀦅􀥒􁉘􀔧􀌶􁁾􀯳􁔮􁕹􁮷􁛘􀛎􀔭􁦏 consumer 􀕦􀹋􀥟􁌱􁭛􁈲􀹋􀮳􁭛􁌱􁁾􁩇􁁾􀯳􀒅􀖕􀓧􀬛􁌱􀸎􀒅push 􀽜􀭗􀓥􀒅􀭮 broker 􀴵􁭆􁌱
􁭛􁈲􁬱􀥟􀔭 consumer 􁁾􁩇􁌱􁭛􁈲􀷸􀒅 consumer 􀯣􀯊􀩪􁥝􀫄􁃛􀔧􀌶􀹋􁕣
Kafka 􁬮􀸎􁭌􀝐􀔧􀖃􁕹􁌱 pull 􀽜􀭗
Pull 􀽜􀭗􁌱􀝚􀥘􀓞􀓻􀦅􀥒􀸎 consumer 􀝢􀕦􁛔􀔆􀙬􀨧􀸎􀞈􀲢􁰁􁌱􀕗 broker
􀳉􀝐􀷄􀴝􀌶Push 􀽜􀭗􀮠􁶳􀣁􀓧􁎣􁭲􀓥􁃋 consumer 􁁾􁩇􁚆􀛎􀞾􁁾􁩇􁒽􁊼􁌱
􀰘􀙭􀓥􀙬􀨧􀸎􁒈􀜨􀴵􁭆􀾯􀹵􁁾􀯳􁬮􀸎􁖨􀨂􀔏􀝸􀲢􁰁􀴵􁭆􀌶􀦇􀺎􀔅􀔧􁭿􀘹
consumer 􀫄􁃛􁘒􁯻􁊠􁫾􀖗􁌱􀴵􁭆􁭛􁈲􀒅􀩙􀝢􁚆􀩕􁛘􀓞 􀽺􀝝􀴵􁭆􁫾􀩝􁌱􁁾
􀯳􁘒􁭜􀱮􁁵􁩇􀌶Pull 􀽜􀭗􀓥􀒅consumer 􀩪􀝢􀕦􀻑􀴝􁛔􀫩􁌱􁁾􁩇􁚆􀛎􀝄􀙬
􀨧􁬯􀔶􁒽􁊼
Pull 􀹍􀓻􁗌􁅩􀸎􀒅􀦇􀺎 broker 􁀌􀹍􀝢􀗀􁁾􁩇􁌱􁁾􀯳􀒅􀩙􀩕􁛘 consumer 􀓧
􀷙􀣁􀮗􁈾􀓾􁫪􁧃􀒅 􁍗􀚩􀷛􁁾􀯳􀚩 t 􁬡􀌶􀔅􀔧􁭿􀘹􁬯􁅩􀒅Kafka 􀹍􀓻􀝇􀷄􀝢
􀕦􁦏 consumer 􁴥􀤲􁎣􁭲􀷛􁁾􀯳􀚩􁬡 (􀭮􁆐􀔞􀝢􀕦􁴥􀤲􁎣􁭲􁁾􀯳􁌱􀷄􁰁􁬡􀚩
􀺤􀓻􁇙􀨧􁌱􁰁􁬯􀻏􀩪􀝢􀕦􀲢􁰁􀝎
7.Kafka 􀨂􀘙􀣁􁏝􁍏􀓤􁌱􁁾􀯳􀻒􀭗􀸎􀕋􀔍?
􁁾􀯳􁊧􀓞􀓻􀢴􀨧􁳩􀬶􁌱􀥧􁮱􀞾􀝢􀝒􁳩􀬶􁌱􀨁􁜓􀷄􁕟􁕟􀱮􀌶􀥧􁮱􀛱􀞌􀔧􀓞􀓻
􁇇􀹜􀝩􀞾 CRC32 􀻊􁸵􁎱􀌶
•􁁾􀯳􁳩􀬶: 4 bytes (value: 1+4+n)
•􁇇􀹜􀝩: 1 byte
•CRC 􀻊􁸵􁎱: 4 bytes
•􀙍􀖛􁌱􁁾􀯳: n bytes
8.Kafka 􁹛􀶴􀷈􀕯􀨂􀘙􁦡􁦇􁇙􁅩:
(1).Kafka 􀲩 topic 􀓾􀓞􀓻 parition 􀥟􀷈􀕯􀚓􀱮􀥚􀓻􀩜􀷈􀕯􀾧􀒅􁭗􁬦􀥚􀓻􀩜
􀷈􀕯􀾧􀒅􀩪􀨻􀸃􀨧􀹗􁂴􁴻􀱲􀚢􁴻􀫪􁕪􁁾􁩇􀨠􀷈􀕯􀒅􀙺􀩝􁏺􁍏􀜛􁊠􀌶
(2).􁭗􁬦􁔱􀭚􀗞􀯳􀝢􀕦􀮳􁭛􀨧􀖖 message 􀞾􁏟􀨧 response 􁌱􀹋􀥟􀥟􀩜􀌶
(3).􁭗􁬦 index 􀘲􀷄􀴝􀙂􁮱􀸉􀩘􀚩 memory􀒅􀝢􀕦􁭿􀘹 segment file 􁌱 IO 􁏺
􁍏􀶙􀖢􀌶
(4).􁭗􁬦􁔱􀭚􀷈􀕯􁑑􁋇􀨂􀘙􀒅􀝢􀕦􀥟􀬏􁴳􀖗 index 􀷈􀕯􀘲􀷄􀴝􀜛􁊠􁑮􁳵􀥟􀩜􀌶
9.Kafka 􀓨􀖃􁕹􁁾􀯳􁔮􁕹􀔏􁳵􀹍􀓣􀓻􀙉􁲫􀜄􀚦
(1).Kafka 􀳮􀔋􀛸􀷭􀮪􀒅􁬯􀔶􀷭􀮪􀝢􀕦􁤩􁯿􀥔􁧛􀝐􀞾􀷫􁴴􀹗􀗛􁊸
(2).Kafka 􀸎􀓞􀓻􀚓􀫲􀭗􁔮􁕹:􀨙􀕦􁵞􁗭􁌱􀷜􀭗􁬩􁤈􀒅􀝢􀕦􁅎􁁚􀖐􁖽􀒅􀣁􀙖􁮱
􁭗􁬦􀥔􀚫􀷄􀴝􀵉􀜋􀨻􁲙􁚆􀛎􀞾􁹛􀝢􁊠􀯔
(3).Kafka 􀶪􀳮􀨫􀷸􁌱􁁞􀭗􀥒􁉘
10.Kafka 􀚠􀭌 Topic 􀷸􀦇􀖜􀩙􀚓􀜄􀶱􁗝􀚩􀓧􀝶􁌱 Broker 􀓾
• 􀛅􀹜􀢩􀧼􀓧􁚆􀥟􀔭 Broker 􁌱􀓻􀷄;
• 􁒫􀓞􀓻􀚓􀜄(􁖫􀝩􀔅 0)􁌱􁒫􀓞􀓻􀛅􀹜􀶱􁗝􀖖􁗝􀸎􁵋􀹢􀕗 brokerList 􁭌􀳠􁌱;
• 􀙌􀕜􀚓􀜄􁌱􁒫􀓞􀓻􀛅􀹜􀶱􁗝􀖖􁗝􁍘􀩒􀔭􁒫 0 􀓻􀚓􀜄􀗁􀽺􀮃􀝸􁑏􀌶􀔞􀩪􀸎
􀦇􀺎􀱯􀕪􀹍 5 􀓻 Broker􀒅5􀓻􀚓􀜄􀒅􀘃􁦡􁒫􀓞􀓻􀚓􀜄􀶱􀣁􁒫􀢥􀓻 Broker
􀓤􀒅􁮎􀔍􁒫􀔫􀓻􀚓􀜄􀩙􀕿􀶱􀣁􁒫􀔲􀓻 Broker 􀓤;􁒫􀓣􀓻􀚓􀜄􀩙􀕿􀶱􀣁􁒫􀓞
􀓻 Broker 􀓤;􁒫􀢥􀓻􀚓􀜄􀩙􀕿􀶱􀣁􁒫􀔫􀓻 Broker 􀓤􀒅􀗁􀽺􁔄􀴵;
• 􀛃􀖟􁌱􀛅􀹜􁍘􀩒􀔭􁒫􀓞􀓻􀛅􀹜􀶱􁗝􀖖􁗝􀙌􀨫􀸎􁊧 nextReplicaShift 􀙬􀨧
􁌱􀒅􁘒􁬯􀓻􀷄􀔞􀸎 􁵋􀹢􀔾􁊞􁌱
11.Kafka 􀷛􀭌􁌱􀚓􀜄􀕿􀣁􀟺􀓻􁍓􀭯􀓥􀚠􀭌
􀣁􀞐􀛖 Kafka 􁵞􁗭􀔏􀚹􀒅􀱯􀕪􁵱􁥝􁯈􁗝􀦅 log.dirs 􀝇􀷄􀒅􀙌􊧊􀸎 Kafka 􀷄
􀴝􁌱􀨂􀶱􁍓􀭯􀒅􁬯􀓻􀝇􀷄􀝢􀕦􁯈􁗝􀥚􀓻􁍓􀭯􀒅􁍓􀭯􀔏􁳵􀖵􁊠􁭖􀝩􀚓􁵍􀒅􁭗
􀬉􁬯􀔶􁍓􀭯􀸎􀚓􀫲􀣁􀓧􀝶􁌱􁏺􁍏􀓤􁊠􀔭􀵉􁹛􁧛􀙟􀯔􁚆􀌶
􀭮􁆐􀱯􀕪􀔞􀝢􀕦􁯈􁗝 log.dir 􀝇􀷄􀒅􀞌􀔎􀓞􀻏􀌶􀝝􁵱􁥝􁦡􁗝􀙌􀓾􀓞􀓻􀜨􀝢􀌶
􀦇􀺎 log.dirs 􀝇􀷄􀝝􁯈􁗝􀔧􀓞􀓻􁍓􀭯􀒅􁮎􀔍􀚓􁯈􀚩􀝱􀓻 Broker 􀓤􁌱􀚓􀜄􁙗
􀨧􀝝􁚆􀣁􁬯􀓻􁍓􀭯􀓥􀚠􀭌􀷈􀕯􀥪􁊠􀔭􀨂􀶱􀷄􀴝􀌶
􀖕􀸎􀦇􀺎 log.dirs 􀝇􀷄􁯈􁗝􀔧􀥚􀓻􁍓􀭯􀒅􁮎􀔍 Kafka 􀕿􀣁􀟺􀓻􀷈􀕯􀥪􀓾􀚠
􀭌􀚓􀜄􁍓􀭯􀞫? 􁒼􀻜􀸎:Kafka 􀕿􀣁􀞌􀹍􀚓􀜄􁍓􀭯􀹋􀩝􁌱􀷈􀕯􀥪􀓾􀚠􀭌􀷛􁌱
􀚓􀜄􁍓􀭯􀒅􀚓􀜄􁍓􀭯􀝷􀔅 Topic 􀝷+􀚓􀜄 ID􀌶􁀳􀰺􀒅􀸎􀚓􀜄􀷈􀕯􀥪􀯛􀷄􀹋
􀩝􁌱􁍓􀭯􀒅􁘒􀓧􀸎􁏺􁍏􀖵􁊠􁰁􀹋􀩝􁌱􁍓􀭯!􀔞􀩪􀸎􁧔􀒅􀦇􀺎􀖦􁕳 log.dirs 􀝇
􀷄􀷛􀥀􀔧􀓞􀓻􀷛􁌱􁏺􁍏􀒅􀷛􁌱􀚓􀜄􁍓􀭯􁙗􀨧􀸎􀘶􀣁􁬯􀓻􀷛􁌱􁏺􁍏􀓤􀚠􀭌􁍗
􀚩􁬯􀓻􀷛􁌱􁏺􁍏􁍓􀭯􀳜􀹍􁌱􀚓􀜄􁍓􀭯􀓧􀸎􀹋􀩝􀔅􀾊􀌶
12.partition 􁌱􀷄􀴝􀦇􀖜􀗛􀨂􀚩􁏝􁍏
topic 􀓾􁌱􀥚􀓻 partition 􀕦􀷈􀕯􀥪􁌱􀭵􀭗􀗛􀨂􀚩 broker􀒅􀾯􀓻􀚓􀜄􀬧􀝩􀕗 0
􁭓􀥀􀒅􀓬􁁾􀯳􀹍􀬧
Partition 􀷈􀕯􀓥􀹍􀥚􀓻 segment(xxx.index􀒅xxx.log)
segment 􀷈􀕯􁯾􁌱􀥟􀩜􀞾􁯈􁗝􀷈􀕯􀥟􀩜􀓞􁛘􀝢􀕦􀻑􀴝􁥝􀿢􀗥􀶯 􁼕􁦊􀔅 1g
􀦇􀺎􀥟􀩜􀥟􀔭 1g 􀷸􀒅􀕿􁃻􀛖􀓞􀓻􀷛􁌱 segment 􀬚􀓬􀕦􀓤􀓞􀓻 segment 􀹋
􀝸􀓞􀹵􁁾􀯳􁌱􀘇􁑏􁰁􀞸􀝷
13.kafka 􁌱 ack 􀹢􀚫
request.required.acks 􀹍􀓣􀓻􊧊 0 1 -1
0:􁊞􀔾􁘏􀓧􀕿􁒵􀮇 broker 􁌱 ack􀒅􁬯􀓻􀭊􁬴􀹋􀖗􀖕􀸎􀨂􀘙􁌱􀗛􁦤􀹋􀭧􀭮
server 􀳯􀴧􁌱􀷸􀗲􀩪􀕿􀓶􀷄􀴝
1:􀹐􀛓􁒒􀕿􁒵􀮇 ack 􊧊 leader 􀛅􀹜􁏟􁦊􀴳􀶭􀚩􁁾􀯳􀝸􀝎􁭆 ack 􀖕􀸎􀦇􀺎
leader 􀳯􀴧􀝸􀕜􀓧􁏟􀗛􀸎􀞈􀥔􀚫􀨠􀱮􀷛 leader 􀔞􀕿􀩕􁛘􀷄􀴝􀓶􀥦
-1:􀝶􀻏􀣁1􁌱􀤚􁏐􀓤􀹐􀛓􁒒􀕿􁒵􀲅􀹍􁌱follower􁌱􀛅􀹜􀝑􀚩􀷄􀴝􀝸􀲍􀕿􀝑􀚩
leader􀝎􀚊􁌱 ack􀒅􁬯􀻏􀷄􀴝􀓧􀕿􀓶􀥦
14.Kafka 􁌱􁁾􁩇􁘏􀦇􀖜􁁾􁩇􀷄􀴝
􁁾􁩇􁘏􀾯􀽺􁁾􁩇􀷄􀴝􁌱􀷸􀗲􀒅􁁾􁩇􁘏􁮷􀕿􁦕􀭯􁁾􁩇􁌱􁇔􁉘􀘇􁑏􁰁(offset)􁌱
􀖖􁗝 􁒵􀚩􀓥􀽺􁁾􁩇􀷸􀒅􀕜􀕿􀴳􁍳􀓤􀽺􀖖􁗝􁖀􁖅􁁾􁩇
15.􁁾􁩇􁘏􁨮􁫹􀣐􁤍􁒽􁊼
􀓞􀓻􁁾􁩇􁘏􁕟􀓾􁌱􀓞􀓻􀚓􁇆􀩒􀬫􀓞􀓻􁁾􁩇􁘏􀱮􀞧􀒅􀕜􁚆􀗛􁦤􀾯􀓻􁁾􁩇􁘏􀱮
􀞧􁮷􁚆􁦢􁳯􀒅􀦇􀺎􁕟􀓾􀱮􀞧􀥡􀥚􀕿􀹍􁑮􁳳􁌱􀱮􀞧
16.􀷄􀴝􀹍􀬧
􀓞􀓻􁁾􁩇􁘏􁕟􁯾􀨙􁌱􀙖􁮱􀸎􀹍􀬧􁌱
􁁾􁩇􁘏􁕟􀓨􁁾􁩇􁘏􁕟􀔏􁳵􀸎􀷫􀬧􁌱
17.kafaka 􁊞􀔾􀷄􀴝􀷸􀷄􀴝􁌱􀚓􁕟􁒽􁊼
􁊞􀔾􁘏􀙬􀨧􀷄􀴝􀔾􁊞􀚩􁵞􁗭􁌱􀟺􀓻 partition 􀓾􀾯􀓞􀹵􁁾􀯳􁮷􀸎􀕦(key􀒅
value)􀻒􀭗
Key 􀸎􁊧􁊞􀔾􁘏􀝎􁭆􀷄􀴝􀖃􀙁􀲅􀕦􁊞􀔾􁘏(key)􀙬􀨧􀔧􀷄􀴝􀔾􁊞􀚩􁵞􁗭􁌱􀟺
􀓻 partition
ActiveMQ􁁾􀯳􀓾􁳵􀕯􁶎􁦶􀓫􁷌
1.􀕋􀔍􀸎 ActiveMQ?
activeMQ 􀸎􀓞􁐿􀭏􁃠􁌱􀒅􀨫􁈿􀔧 JMS1.1 􁥢􁝜􁌱􀒅􁶎􀝻􁁾􀯳(MOM)􁌱􀓾􁳵
􀕯􀒅􀔅􀬫􁊠􁑕􀬧􀵉􀗀􁹛􀶴􁌱􀌵􀝢􀲘􀪀􁌱􀌵􁑞􀨧􁌱􀞾􀨞􀙂􁌱􀕴􀓱􁕆􁁾􀯳􁭗􀗞
2. ActiveMQ 􀹐􀛓􀢏􀨣􀹢􀯆􀔍􀛐?
􁬯􀮑􀕗 ActiveMQ 􁌱􀘙􀨂􀹢􀚫􁧔􁩸􀌶􀣁􁭗􀬉􁌱􀰘􀙭􀓥􀒅􁶋􀳮􀔋􀛸􁁾􀯳􀸎􀨂
􀘙􀣁􀙖􀨂􀓾􁌱􀒅􀳮􀔋􀛸􁁾􀯳􀸎􀨂􀘙􀣁􀷈􀕯􀓾􁌱􀒅􀨙􀕪􁌱􀹋􀥟􁴴􀚫􀣁􁯈􁗝􀷈
􀕯􁌱 <systemUsage> 􁜓􁅩􀓾􁯈􁗝􀌶􀖕􀸎􀒅􀣁􁶋􀳮􀔋􀛸􁁾􀯳􀤞 􁑌􀚩􀓞􀨧􁑕
􀬶􀒅􀙖􀨂􀞞􀯒􁌱􀷸􀗲􀒅ActiveMQ 􀕿􀩙􀙖􀨂􀓾􁌱􁶋􀳮􀔋􀛸􁁾􀯳􀙟􀙁􀔁􀷸􀷈
􀕯􀓾􀒅􀕦􁚸􀚊􀙖􀨂􀌶 􁡱􁆐􁮷􀗛􀨂􀚩􀔧􀷈􀕯􁯾􀒅􀖕􀨙􀞾􀳮􀔋􀛸􁁾􀯳􁌱􀜄􀚦
􀸎􀒅􁯿􀞐􀝸􀳮􀔋􀛸􁁾􀯳􀕿􀕗􀷈􀕯􀓾􀯩􀥔􀒅􁶋􀳮􀔋􀛸􁌱􀔁 􀷸􀷈􀕯􀕿􁍗􀴳􀚢
􁴻􀌶
􁮎􀦇􀺎􀷈􀕯􀥀􀥟􀚩􁬡􀔧􁯈􁗝􀓾􁌱􀹋􀥟􁴴􀚫􁌱􀷸􀗲􀕿􀝎􁊞􀕋􀔍?􀱯􀘉􀔧􀕦􀓥
􀨫􁸵:
􁦡􁗝 2G 􀫢􀝦􁌱􀳮􀔋􀛸􀷈􀕯􁴴􀚫􀒅􀥟􁰁􁊞􀔾􀳮􀔋􀛸􁁾􀯳􁍗􀚩􀷈􀕯􁬡􀚩􀹋􀥟􁴴􀚫􀒅􀾌􀷸􁊞􀔾􁘏􁴥􀤲􀒅􀖕􁁾􁩇􁘏􀝢􀾋􀬉􁬳􀴳􀬚􁁾􁩇􁁾􀯳􀒅􁒵􁁾􀯳􁁾􁩇􀴧
􀓞􁮱􀚓􀒅􀷈􀕯􀚢􁴻􀝈􁚸􀚊􁑮􁳵􀔏􀝸􀒅􁊞􀔾􁘏􀝈􀝢􁖀􁖅􀝎􁭆􁁾􀯳􀒅􀹐􀛓􁛔􀛖
􀯩􀥔􀾋􀬉􀌶
􁦡􁗝 2G 􀫢􀝦􁌱􀔁􀷸􀷈􀕯􁴴􀚫􀒅􀥟􁰁􁊞􀔾􁶋􀳮􀔋􀛸􁁾􀯳􀬚􀙟􀙁􀔁􀷸􀷈􀕯􀒅
􀣁􁬡􀚩􀹋􀥟􁴴􀚫􀷸􀒅􁊞􀔾􁘏􁴥􀤲􀒅􁁾􁩇􁘏􀝢􀾋􀬉􁬳􀴳􀖕􀓧􁚆􁁾􁩇􁁾􀯳􀒅􀱲
􁘏􀜻􀹜􀱌􁭛􁁾􁩇􁌱􁁾􁩇􁘏􀒅􁁾􁩇􁑱􁆐􀘊􀾊􀌶􀷆􀓻􁔮􁕹􀝢􁬳􀴳􀒅 􀖕􀸎􀷫􁀩􀵉
􀗀􀹐􀛓􀒅􀩪􁬯􀻏􀳯􀔧􀌶
􀙍􀖛􀜻􀢩􀓧􁧇􀒅􁥴􀙬􀷜􀻜:􀩱􁰁􀓧􁥝􁊠􁶋􀳮􀔋􀛸􁁾􀯳􀒅􁶋􁥝􁊠􁌱􁦾􀒅􀩙􀔁􀷸
􀷈􀕯􁴴􀚫􀩱􀝢􁚆􁌱􁧣􀥟􀌶
3. 􀓶􁁾􀯳􀯆􀔍􀛐?
􁬯􀮑􀕗 java 􁌱 java.net.SocketException 􀭑􀬉􁧔􁩸􀌶􁓌􀜔􁅩􁧔􀩪􀸎􀭮􁗑􁕶
􀝎􁭆􀷜􀝎􁭆􀓞􀤞􀷄􀴝􀒅􁆐􀝸􁧣􁊠 close 􀙉􁳮􁬳􀴳􀔏􀝸􀌶􁬯􀔶􀝎􁭆􁌱􀷄􀴝􁮷
􀣁􀴳􀶭􁘏􁌱􁖨􀨂􁯾􀒅􀴳􀶭􁘏􀦇􀺎􁧣􁊠 read 􀷜􁀩􀕖􀷯􁚆􀕗􁖨􀨂􀓾􁧛􀝐􁬯􀔶
􀷄􀴝􀒅􀩱􁓕􀩒􀷜􀫪􁕪􀙉􁳮􀔧􁬳􀴳􀌶􀖕􀸎􀭮􀴳􀶭􁘏􀩤􁦶􀝎􁭆􀷄􀴝􀷸􀒅􁊧􀔭􀾌
􀷸􁬳􀴳􀫪􀙉􁳮􀒅􀲅􀕦􀕿􀝎􁊞􀭑􀬉􀒅􁬯􀓻􀮉􀦅􁉘􁥴􀌶􀓧􁬦􁵱􁥝􁀳􀰺􁌱􀸎􀒅􀭮
􀝎􁊞 SocketException 􀝸􀒅􀜻􀹜􁖨􀨂􀜄􀓾􀷄􀴝􀔞􀖢􀬳􀔧􀒅􀾌􀷸􀴳􀶭􁘏􀙚􀽺
􁧣􁊠 read 􀷜􁀩􀝄􁧛􀝐􁖨􀨂􀓾􁌱􀷄􀴝􀒅􀩪􀕿􀲸 Software caused connection
abort: recv failed 􁲙􁧏􀌶
􁭗􁬦􀲬􀛱􀮑􁎣􀒅ActiveMQ 􀕿􀾯􁵍 10 􁑁􀝎􁭆􀓞􀓻􀮞􁪡􀛱􀒅􁬯􀓻􀮞􁪡􀛱􀸎􀹐
􀛓􀢏􀝎􁭆􁕳􀨮􀲁􁒒􁌱􀒅􁊠􀹶􀚣􀷙􀨮􀲁􁒒􀾒􁀌􀾒􀌶􀦇􀺎􀖦􁍡􁬦􀓤􁶎􁒫􀓞􀹵􀒅
􀩪􀕿􁎣􁭲􁶋􀳮􀔋􀛸􁁾􀯳􀤞􁑌􀚩􀓞􀨧􁑕􀬶􀕿􀙟􀚩􀷈􀕯􁯾􀒅􁬯􀓻􀙟 􁌱􁬦􁑕􀕿􁴥
􀤲􀲅􀹍􀛖􀖢􀒅􁘒􀓬􀕿􀳮􁖅 20 􀚩 30 􁑁􀒅􀬚􀓬􁵋􁍳􀙖􀨂􁌱􀥀􀥟􁘒􀥀􀥟􀌶􀭮􀨮
􀲁􁒒􀝎􀨠􁁾􀯳􁧣􁊠 connection.close()􀷸􀒅􀕿􀹗􀮇􀹐􀛓􀢏􀩒􀔭􀙉􁳮􁬳􀴳􁌱􀢧
􁒼􀒅􀦇􀺎􁩻􁬦 15 􁑁􁀌􀢧􁒼􀩪􁍗􀴳􁧣􁊠 socket 􀩶􁌱 close 􀙉􁳮 tcp 􁬳􀴳
􀔧􀌶􁬯􀷸􀨮􀲁􁒒􀝎􀚊􁌱􁁾􀯳􀙌􀨫􁬮􀣁􀹐􀛓􀢏􁌱􁖨􀨂􁯾􁒵􀮇􀥒􁉘􀒅􀓧􁬦􁊧􀔭
􀹐􀛓􀢏􀮞􁪡􀛱􁌱􁦡􁗝􀒅􀩕􁛘􀝎􁊞􀔧 java.net.SocketException 􀭑􀬉􀒅􀲩􁖨
􀨂􁯾􁌱􀷄􀴝􀖢􀬳􀔧􀒅􁀌􀥒􁉘􁌱􁁾􀯳􀙂􁮱􀓶􀥦􀌶
􁥴􀙬􀷜􀻜:􁊠􀳮􀔋􀛸􁁾􀯳􀒅􀱲􁘏􁶋􀳮􀔋􀛸􁁾􀯳􀝊􀷸􀥒􁉘􀓧􁥝􀤞􁑌􀒅􀱲􁘏􀞐􀛖
􀔪􀛓􀒅􀞐􀛖􀔪􀛓􀝸􀒅commit()􀷜􁀩􀕿􁨮􁨱􀕱􁌱􁒵􀮇􀹐􀛓􀢏􁌱􁬬􀢧􀒅􀔞􀩪􀓧
􀕿􀙉􁳮􁬳􀴳􀩕􁛘􁁾􀯳􀓶􀥦􀔧􀌶
4. 􀳮􀔋􀛸􁁾􀯳􁶋􀬉􀱌􀌶
􁼕􁦊􁌱􀰘􀙭􀓥􀒅􁶋􀳮􀔋􀛸􁌱􁁾􀯳􀸎􀭑􀾍􀝎􁭆􁌱􀒅􀳮􀔋􀛸􁌱􁁾􀯳􀸎􀝶􀾍􀝎􁭆
􁌱􀒅􁭬􀚩􀱌􀓞􁅩􁌱􁏝􁍏􀒅􀝎􁭆􁁾􀯳􁌱􁭛􀬶􀸎􀷫􁀩􀮤􀝑􁌱􀌶􀖕􀸎􀣁􀭏􀞐􀔪􀛓
􁌱􀰘􀙭􀓥􀒅􁁾􀯳􁮷􀸎􀭑􀾍􀝎􁭆􁌱􀒅􀶴􁈲􀕿􀹍 2 􀓻􀷄􁰁􁕆􁌱􀵉􀜋􀌶 􀲅􀕦􀣁
􀝎􁭆􀳮􀔋􀛸􁁾􀯳􀷸􀒅􁧗􀛓􀮠􀭏􀞐􀔪􀛓􀽜􀭗􀌶􀙌􀨫􀝎􁭆􁶋􀳮􀔋􀛸􁁾􀯳􀷸􀔞􀭌
􁦓􀭏􀞐􀔪􀛓􀒅􀢩􀔅􀻑􀹜􀓧􀕿􀭽􀟥􀯔􁚆􀌶
5. 􁁾􀯳􁌱􀓧􀣐􀛰􁁾􁩇􀌶
􀹍􀷸􀣁􀝎􁭆􀓞􀔶􁁾􀯳􀔏􀝸􀒅􀭏􀞐 2 􀓻􁁾􁩇􁘏􀝄􀥒􁉘􁁾􀯳􀌶􀕿􀝎􁈿􀓞􀓻􁁾􁩇
􁘏􀥒􁉘􀔧􀲅􀹍􁌱􁁾􀯳􀒅􀝚􀓞􀓻􁁾􁩇􁘏􀻑􀹜􁀌􀶭􀚩􁁾􀯳􀌶􀜻􀢩􀣁􀔭
ActiveMQ 􁌱 prefetch 􀹢􀚫􀌶􀭮􁁾􁩇􁘏􀝄􁞴􀝐􁁾􀯳􀷸􀒅􀓧􀕿􀓞􀹵􀓞􀹵􀝄􁞴
􀝐􀒅􁘒􀸎􀓞􀽺􀯔􁞴􀝐􀓞􀲢􀒅􁼕􁦊􀸎 1000 􀹵􀌶􁬯􀔶􁶼􁞴􀝐􁌱􁁾􀯳􀒅􀣁􁬮􁀌
􁏟􁦊􁁾􁩇􀔏􀚹􀒅􀣁􁓕􁉘􀴴􀚫􀝣􁬮􀸎􀝢􀕦􁍡􁥠􁬯􀔶􁁾􀯳􁌱􀒅􀖕􀸎􀓧􀕿􀙚􀚓􁯈
􁕳􀙌􀕜􁁾􁩇􁘏􀒅􀾌􀷸􁬯􀔶􁁾􀯳􁌱􁇫􀮾􀬫􁧆􁓒􀖢“􀫪􀚓􁯈􀹚􁁾 􁩇”􀒅􀦇􀺎􁁾􀯳
􀹋􀝸􁤩􁁾􁩇􀒅􀚞􀕿􀣁􀹐􀛓􀢏􁒒􁤩􀚢􁴻􀒅􀦇􀺎􁁾􁩇􁘏􀫄􁃛􀒅􀚞􁬯􀔶􁁾􀯳􀕿􁤩
􁯿􀷛􀚓􁯈􁕳􀷛􁌱􁁾􁩇􁘏􀌶􀖕􀸎􀦇􀺎􁁾􁩇􁘏􀷬􀓧􁁾􁩇􁏟􁦊􀒅􀝈􀓧􀫄􁃛􀒅􁮎􁬯
􀔶􁁾􀯳􀩪􀿞􁬱􁫡􀣁􁁾􁩇􁘏􁌱􁖨􀨂􀜄􁯾􀷫􁀩􀥒􁉘􀌶􀹅􁭗􀬉􁌱􀰘􀙭􀸎􀒅􁁾􁩇􁬯
􀔶􁁾􀯳􁶋􀬉􁘙􀷸􀒅􀖦􀭏􀔧 10 􀓻􁁾􁩇􁘏􀝄􀥒􁉘􀒅􁕮􀺎􀝎􁈿􀝝􀹍􀓞􀝣􀹢􀢏􀞎
􀟷􀞎􀟷􀥒􁉘􀒅􀝚􀥘 9 􀝣􀠨􀔪􀓧􀬗􀌶
􁥴􀙬􀷜􀻜:􀩙 prefetch 􁦡􀔅 1􀒅􀾯􀽺􀥒􁉘 1 􀹵􁁾􀯳􀒅􀥒􁉘􀨠􀙚􀝄􀝐􀒅􁬯􀻏􀔞
􀱌􀓧􀔧􀥚􀩝􀌶
6. 􀾒􀗞􁴚􀚜􀌶
􀦇􀺎􀖦􀰮􀣁􁁾􀯳􀥒􁉘􀥦􁨳􀝸􀒅􀓧􁤩􀹐􀛓􀢏􀚢􁴻􀒅􁬮􁚆􁤩􀙌􀕜􁁾􁩇􁘏􀥒􁉘􀱲
􁯿􁦶􀒅􀝢􀕦􀙉􁳮 AUTO_ACKNOWLEDGE 􀒅􀩙 ack 􀔻􁊧􁑕􀬧􁛔􀫩􀥒􁉘􀌶􁮎􀦇
􀺎􀖵􁊠􀔧 AUTO_ACKNOWLEDGE 􀒅􁁾􀯳􀸎􀕋􀔍􀷸􀗲􁤩􁏟􁦊􁌱􀒅􁬮􀹍􁀌􀹍􁴥
􀾊􁁾􀯳􁏟􁦊􁌱􀷜􁀩?􀹍!
􁁾􁩇􁁾􀯳􀹍 2 􁐿􀷜􁀩􀒅􀓞􁐿􀸎􁧣􁊠 consumer.receive()􀷜􁀩􀒅􁧆􀷜􁀩􀩙􁴥􀤲
􁍗􀚩􁞴􀮑􀬚􁬬􀢧􀓞􀹵􁁾􀯳􀌶􁬯􁐿􀰘􀙭􀓥􀒅􁁾􀯳􁬬􀢧􁕳􀷜􁀩􁧣􁊠􁘏􀔏􀝸􀩪􁛔
􀛖􁤩􁏟􁦊􀔧􀌶􀝚􀓞􁐿􀷜􁀩􀸎􁯻􁊠 listener 􀢧􁧣􀚍􀷄􀒅􀣁􀹍􁁾􀯳􀚩􁬡􀷸􀒅􀕿
􁧣􁊠 listener 􀴳􀝗􁌱 onMessage 􀷜􁀩􀌶􀣁􁬯􁐿􀰘􀙭􀓥􀒅􀣁 onMessage 􀷜
􁀩􀲗􁤈􀨠􀾳􀝸􀒅􁁾􀯳􀲍􀕿􁤩􁏟􁦊􀒅􀾌􀷸􀝝􁥝􀣁􀷜􁀩􀓾􀲲􀚊􀭑􀬉􀒅􁧆􁁾􀯳􀩪
􀓧􀕿􁤩􁏟􁦊􀌶􁮎􀔍􁳯􁷌􀹶􀔧􀒅􀦇􀺎􀓞􀹵􁁾􀯳􀓧􁚆 􁤩􀥒􁉘􀒅􀕿􁤩􁭅􀢧􀹐􀛓􀢏
􁯿􀷛􀚓􁯈􀒅􀦇􀺎􀝝􀹍􀓞􀓻􁁾􁩇􁘏􀒅􁧆􁁾􀯳􀝈􀕿􁯿􀷛􁤩􁞴􀝐􀒅􁯿􀷛􀲲􀭑􀬉􀌶
􀩪􁓒􀹍􀥚􀓻􁁾􁩇􁘏􀒅􀮃􀮃􀣁􀓞􀓻􀹐􀛓􀢏􀓤􀓧􁚆􀥒􁉘􁌱􁁾􀯳􀒅􀣁􀝚􀥘􁌱􀹐􀛓
􀢏􀓤􀗁􁆐􀓧􁚆􁤩􀥒􁉘􀌶􁵙􁭲􀩪􁬯􀔍􁭅􀢧 --􁞴􀝐--􀲸􁲙􀾒􀮗􁈾􀔧􀞀?
􀣁􁯿􁦶 6 􀽺􀝸􀒅ActiveMQ 􁦊􀔅􁬯􀹵􁁾􀯳􀸎“􀹍􀾰”􁌱􀒅􀩙􀕿􀲩􁁾􀯳􀓶􀚩􀾒􀗞
􁴚􀚜􁯾􀌶􀦇􀺎􀖦􁌱􁁾􀯳􀓧􁥠 􀔧􀒅􀝄 ActiveMQ.DLQ 􁯾􀲤􀲤􀒅􁧔􀓧􀨧􀩪􁫡􀣁
􁮎􁯾􀌶
7. ActiveMQ 􀓾􁌱􁁾􀯳􁯿􀝎􀷸􁳵􁳵􁵍􀞾􁯿􀝎􀽺􀷄􀞀?
ActiveMQ:􀸎 Apache 􀚊􀟝􀒅􀹋􁁞􁤈􁌱􀒅􁚆􀛎􀭩􀛝􁌱􀭏􁃠􁁾􀯳􀯛􁕚􀌶􀸎􀓞􀓻
􀨠􀙂􀶪􀳮 JMS1.1 􀞾 J2EE 1.4 􁥢􁝜􁌱 JMS Provider 􀨫􁈿􀌶JMS(Java 􁁾􀯳
􀹐􀛓):􀸎􀓞􀓻 Java 􀬘􀝣􀓾􀙉􀔭􁶎􀝻􁁾􀯳􀓾􁳵􀕯 (MOM)􁌱 API􀒅􁊠􀔭􀣁􀓷􀓻
􀬫􁊠􁑕􀬧􀔏􁳵􀒅􀱲􀚓􀫲􀭗􁔮􁕹􀓾􀝎􁭆􁁾􀯳􀒅􁬰􁤈􀭑􀾍􁭗􀗞􀌶
􁸒􀘶􀒅􀱯􀕪􀮑􀥟􀼷􀔧􁥴􀓥􀒅􀣁􀟺􀔶􀰘􀙭􀓥􀒅ActiveMQ 􀹐􀛓􀢏􀕿􀩙􁁾􀯳􁯿
􀝎􁕳􁁾􁩇􁘏􀒅􁬯􁯾􀔅􁓌􀜔􁩸􁥠􀒅􀘃􀨧􁯻􁊠􁌱􁁾􀯳􀝎􁭆􀽜􀭗􀔅􁴚􀚜(􀜨􁁾􀯳􀝎
􁭆􁘏􀞾􁁾􀯳􀴳􀶭􁘏)􀌶
1 􀦇􀺎􁁾􀯳􀴳􀶭􁘏􀣁􀥒􁉘􀨠􀓞􀹵􁁾􀯳􁌱􀥒􁉘􁬦􁑕􀝸􁀌􀹍􀩒 MOM 􁬰􁤈􀬫
􁒼􀒅􀚞􁧆􁁾􀯳􀩙􁊧 MOM 􁯿􀝎.
2 􀦇􀺎􀱯􀕪􁴚􀺤􀓻􁴚􀚜􁦡􁗝􀔧􁶼􁧛􀝇􀷄(consumer.prefetchSize)􀒅􀦇􀺎􁁾􀯳
􀴳􀶭􁘏􀣁􀥒􁉘􁒫􀓞􀹵􁁾􀯳􀷸(􁀌􀝻 MOM 􀝎􁭆􁁾􀯳􀴳􀶭􁏟􁦊)􀩪􀨣􀹢􀔧􀒅􀚞
􁶼􁧛􀷄􁰁􁌱􀲅􀹍􁁾􀯳􁮷􀩙􁤩􁯿􀝎!
3 􀦇􀺎 Session 􀸎􀔪􀛓􁌱􀒅􀚞􀝝􁥝􁁾􀯳􀴳􀶭􁘏􀹍􀓞􀹵􁁾􀯳􁀌􀹍􁏟􁦊􀒅􀱲􀝎
􁭆􁁾􀯳􀹗􁳵 MOM 􀱲􀨮􀲁􁒒􀺤􀓞􀷜􁑱􁆐􀨣􀹢􀔧􀒅􀚞􁧆􀔪􀛓􁝜􀢱􀓾􁌱􀲅􀹍􁁾
􀯳 MOM 􁮷􀩙􁯿􀝎􀌶
4 􁧔􀚩􁬯􁯾􀒅􀥟􀨹􀝢􁚆􀕿􀹍􁋈􁳯􀒅ActiveMQ 􁁾􀯳􀹐􀛓􀢏􀯆􀔍􁎣􁭲􁁾􁩇􁘏􀨮
􀲁􁒒􀚩􀬬􀸎􁁾􀯳􀾋􀣁􀥒􁉘􀓾 􁬮􁀌􀹶􀮑􀯒􀩒􁁾􀯳􁬰􁤈􀬫􁒼􁬮􀸎􀫪􁕪􀥒􁉘􀨠􀱮
􀔧􁀌􀹍􀬫􁒼􀱲􀸎􀨣􀹢􀔧􀻑􀹜􁀌􀹢􀕿􀬫􁒼􀞫?􀙌􀨫􀣁􀲅􀹍􁌱􀨮􀲁􁒒􀹢􀢏􀓤􀒅
􀙖􀨂􀓾􁮷􁬩􁤈􁍳􀓞􀥺􀨮􀲁􁒒􁌱 ActiveMQ 􁈾􀤹􀒅􁧆􁈾􀤹􁨮􁨱􁖨􀨂􀝎􀹶􁌱􁁾
􀯳􀒅􁨮􁨱􁖌􀳮􁍳 􀞾 ActiveMQ 􀹐􀛓􀢏􁌱􁁾􀯳􁭗􁦔􀒅􁨮􁨱􀥦􀶴􁫨􁑏(fail-over)
􁒵􀒅􀲅􀹍􁌱􀚣􀷙􀞾􀥒􁉘􁮷􀸎􁊧􁬯􀥺􀨮􀲁􁒒􁈾􀤹􀹶􀨠􀱮􁌱􀌶
􀱯􀕪􀝢􀕦􀹶􀩒 ActiveMQ 􁌱􁯿􀝎􁒽􁊼(Redelivery Policy)􀹶􁬰􁤈􁛔􀨧􀔎􁯈
􁗝􀒅􀙌􀓾􁌱􁯈􁗝􀝇􀷄􀔆􁥝􀹍􀕦􀓥􀙾􀓻:
􀝢􁊠􁌱􀪂􀯔
􀪂􀯔􁼕􁦊􊧊􁧔􀸁
l collisionAvoidanceFactor 􁼕􁦊􊧊 0.15 , 􁦡􁗝􁴠􀾊􀙫􁑱􁝜􀢱􁌱􀾋􁨮􁌯􀚓
􀾲􀒅􀝝􀹍􀞐􁊠 useCollisionAvoidance 􀝇􀷄􀷸􀲍􁊞􀶴􀌶
l maximumRedeliveries 􁼕􁦊􊧊 6 , 􀹋􀥟􁯿􀖃􀽺􀷄􀒅􁬡􀚩􀹋􀥟􁯿􁬳􀽺􀷄􀝸􀲲
􀚊􀭑􀬉􀌶􀔅-1 􀷸􀓧􁴴􀚫􀽺􀷄􀒅􀔅 0 􀷸􁤒􁐏􀓧􁬰􁤈􁯿􀖃􀌶
l maximumRedeliveryDelay 􁼕􁦊􊧊-1, 􀹋􀥟􀖃􁭆􀭊􁬴􀒅􀝝􀣁
useExponentialBackOff 􀔅 true 􀷸􀹍􀶴 (V5.5)􀒅􀘃􁦡􁸒􀽺􁯿􁬳􁳵􁵍􀔅
10ms􀒅􀗭􀷄􀔅 2􀒅􁮎􀔍􁒫􀔫􀽺􁯿􁬳􀷸􁳵􁳵􁵍􀔅 20ms􀒅􁒫􀓣􀽺􁯿􁬳􀷸􁳵􁳵
􁵍􀔅 40ms􀒅􀭮􁯿􁬳􀷸􁳵􁳵􁵍􀥟􁌱􀹋􀥟􁯿􁬳􀷸􁳵􁳵􁵍􀷸􀒅􀕦􀝸􀾯􀽺􁯿􁬳􀷸
􁳵􁳵􁵍􁮷􀔅􀹋􀥟􁯿􁬳􀷸􁳵􁳵􁵍􀌶
l initialRedeliveryDelay 􁼕􁦊􊧊 1000L, 􀚡􀦤􁯿􀝎􀭊􁬴􀷸􁳵
l redeliveryDelay 􁼕􁦊􊧊 1000L, 􁯿􀝎􀭊􁬴􀷸􁳵􀒅􀭮 initialRedeliveryDelay=0
􀷸􁊞􀶴(v5.4)
l useCollisionAvoidance 􁼕􁦊􊧊 false, 􀞐􁊠􁴠􀾊􀙫􁑱􀛑􁚆􀒅􀢩􀔅􁁾􀯳􀴳􀶭􀷸
􀸎􀝢􀕦􀖵􁊠􀥚􁕚􁑕􀬚􀝎􀥒􁉘􁌱􀒅􀬫􁧆􀸎􀔅􀔧􁯿􀝎􁌱􀨞􀙂􀯔􀒅􁭿􀭏􀲅􀹍􀬚􀝎
􁕚􁑕􁮷􀣁􀝶􀓞􀓻􀷸􁳵􁅩􁬰􁤈􁁾􀯳􀴳􀶭􀥒􁉘􀌶􀲅􀹍􁕚􁑕􀣁􀝶􀓞􀓻􀷸􁳵􁅩􀥒􁉘
􀷸􀕿􀝎􁊞􀕋􀔍􁳯􁷌􀞫?􀬫􁧆􁀌􀹍􁳯􁷌􀒅􀝝􀸎􀔅􀔧􀬘􁤍 broker 􀥒􁉘􀯔􁚆􀒅􀓧
􀕿􀹍􀷸􀮉􀮬􀒅􀹍􀷸􀮉􁑮􁳳􀌶
l useExponentialBackOff 􁼕􁦊􊧊 false, 􀞐􁊠􀳰􀷄􀗭􀷄􁭓􀥀􁌱􀷜􀭗􀥀􀛒􀭊􁬴
􀷸􁳵􀌶
l backOffMultiplier 􁼕􁦊􊧊 5, 􁯿􁬳􀷸􁳵􁳵􁵍􁭓􀥀􀗭􀷄􀒅􀝝􀹍􊧊􀥟􀔭 1 􀞾􀞐
􁊠 useExponentialBackOff 􀝇􀷄􀷸􀲍􁊞􀶴􀌶
5.3􀌵􀚓􀫲􀭗􀷄􀴝􀬪􁶎􁦶􀷆􁉘
5.3.1 redis􁶎􁦶􀓫􁷌
1􀌵redis 􀞾 memcached 􀕋􀔍􀜄􀚦?􀔅􀕋􀔍􁹛􀬚􀝎􀓥􀹍􀷸􀜔􁕚􁑕􁌱 redis
􀾲􀥚􁕚􁑕􁌱 memcached 􀶴􁈲􁥝􁹛?
􀜄􀚦:
1.mc 􀝢􁖨􀨂􀢶􁇆􀞾􁥤􁷇􀌶rd 􀶪􀳮􁴻 k/v 􀹅􀥚􁌱􀷄􀴝􁕮􀺅;
2.rd 􀝢􀕦􀖵􁊠􁡦􀳙􀙖􀨂􀒅rd 􀝢􀳮􀔋􀛸􀞾 aof 􁅒􁵙􀯩􀥔􀒅rd 􁭗􁬦􀔆􀕗􀶪􀳮􀷄
􀴝􀥓􀕲; 3.rd 􀝢􀕦􀘉􁁾􀯳􁴚􀚜􀌶
􀜻􀢩:mc 􀥚􁕚􁑕􀽜􀣳􀭚􀙁􀔧􁖨􀨂􀓞􁛘􀯔􀞾􁲁􀒅􀛒􁲁􀬃􀹶􀔧􀯔􁚆􀴖􁘙􀌶
2􀌵redis 􀔆􀕗􀥔􀚫􀦇􀖜􀨫􁈿􁌱?redis 􁌱􁵞􁗭􀽜􀭗􀦇􀖜􀨫􁈿?redis 􁌱 key
􀸎􀦇􀖜􀩔􀣎􁌱?
􀔆􀕗􀥔􀚫􀨫􁈿:􀔆􁜓􁅩􀩙􁛔􀫩􀙖􀨂􀓾􁌱􀷄􀴝􀘉􀓞􀕲􀮳􁆙􀒅􀩙􀮳􁆙􀝎􁕳􀕗􁜓
􁅩􀒅􀕗􁜓􁅩􀩙􀷄 􀴝􀯩􀥔􀚩􀙖􀨂􀓾􀌶􀔏􀝸􀙚􀾯􀽺􀥀􀛒􀷛􀷄􀴝􁌱􀷸􀗲􀒅􀔆􁜓􁅩
􀕦􁔄􀖒􀔭 mysql 􁌱􀔫􁬰􀚫􀷭􀮪􀷜 􀭗􀩙􁧍􀝙􀝎􁭆􁕳􀕗􁜓􁅩􀒅􀕗􁜓􁅩􀳭􀚩􀔆􁜓
􁅩􀝎􁭆􁬦􀹶􁌱􁧍􀝙􁬰􁤈􁯿􀶱􀌶
􀚓􁇆􀷜􀭗:
-􀨮􀲁􁒒􀚓􁇆
-􀤚􀔭􀕤􁉘􁌱􀚓􁇆
● Twemproxy
● codis
-􁪠􁊧􀺱􁧃􀚓􁇆
● Redis-cluster(􀹜􁫝􀵉􀗀􀔧􁛔􀛖􀩙􀷄􀴝􀚓􀷀􀚩 Redis Cluster 􀓧􀝶􁜓􁅩􁌱􁚆
􀛎􀒅􀷆􀓻􀷄􀴝􁵞􀝳􁌱􀺤􀓻􀷄􀴝􀧼􁵞􀨂􀘙􀣁􀟺􀓻􁜓􁅩􀩒􀔭􁊠􀲁􀹶􁧔􀸎􁭐􀸁􁌱)
redis-cluster 􀚓􁇆􀜻􁉘:Cluster 􀓾􀹍􀓞􀓻 16384 􁳩􀬶􁌱􀽖(􁡦􀳙􀽖)􀒅􁖫􀝩􀚓
􀚦􀔅 0-16383􀌶 􀾯􀓻 Master 􁜓􁅩􁮷􀕿􁨮􁨱􀓞􁮱􀚓􁌱􀽖􀒅􀭮􀹍􀺤􀓻 key 􁤩
􀸉􀩘􀚩􀺤􀓻 Master 􁨮􁨱􁌱􀽖􀒅􁮎􀔍􁬯􀓻 Master 􁨮􁨱􀔅􁬯􀓻 key 􀵉􀗀􀹐
􀛓􀒅􁛗􀔭􀟺􀓻 Master 􁜓􁅩􁨮􁨱􀟺􀓻􀽖􀒅􀝢􀕦􁊧􁊠􀲁􀳰􀨧􀒅􀔞􀝢􀕦􀣁􀚡􀦤
􀛸􁌱􀷸􀗲􁛔􀛖􁊞􀱮􀒅􀝝􀹍 Master 􀲍􀳜􀹍􀽖􁌱􀲅􀹍􀹦􀌶Master 􁜓􁅩􁖌􀲷􁍳
􀓞􀓻 16384/8 􀨁􁜓􁌱􀖖􀬧􀚜􀒅Master 􁜓􁅩􁊠 bit 􀹶􀺽􁦩􀩒􀔭􀺤􀓻􀽖􁛔􀫩􀸎
􀞈􀳜􀹍􀌶􀾲􀦇􀩒􀔭􁖫􀝩􀔅 1 􁌱􀽖􀒅Master 􀝝􁥝􀚣􀷙􀬧􀚜􁌱􁒫􀔫􀖖(􁔱􀭚􀕗
0 􀭏􀦤)􀸎􀓧􀸎􀔅 1 􀜨􀝢􀌶􁬯􁐿􁕮􀺅􀮉􀨻􀸃􁂲􀛒􀱲􁘏􀚢􁴻􁜓􁅩􀌶􀾲􀦇􀦇􀺎􀱯
􀰮􀷛􁂲􀛒􀓻􁜓􁅩 D, 􀱯􁵱􁥝􀕗􁜓􁅩 A􀌵B􀌵 C 􀓾􀮑􁮱􀚓􀽖􀚩 D 􀓤􀌶
3􀌵􀖵􁊠 redis 􀦇􀖜􁦡􁦇􀚓􀫲􀭗􁲁?􁧔􀓞􀓥􀨫􁈿􀯏􁪠?􀖵􁊠 zk 􀝢􀕦􀞀?􀦇􀖜
􀨫􁈿?􁬯􀓷􁐿􀹍􀕋􀔍􀜄􀚦?
redis:
1.􁕚􁑕 A setnx(􀓤􁲁􁌱􀩒􁨝,􁩻􀷸􀷸􁌱􀷸􁳵􀱿 t1)􀒅􀦇􀺎􁬬􀢧 true􀒅􁞴􀮑􁲁􀌶
2.􁕚􁑕 B 􁊠 get 􁞴􀝐 t1,􀓨􀭮􀚹􀷸􁳵􀱿􀾲􁫾,􀚣􀷙􀸎􀸎􀞈􁩻􀷸,􁀌􁩻􀷸 false,
􁝑􁩻􀷸􀲗􁤈􁒫 3 􀾍;
3.􁦇􁓒􀷛􁌱􁩻􀷸􀷸􁳵 t2,􀖵􁊠 getset 􀞸􀕥􁬬􀢧 t3(􁧆􊧊􀝢􁚆􀙌􀕜􁕚􁑕􀫪􁕪􀗥
􀶯􁬦),􀦇􀺎 t1==t3􀒅􁞴􀮑􁲁􀒅􀦇􀺎 t1!=t3 􁧔􀸁􁲁􁤩􀙌􀕜􁕚􁑕􁞴􀝐􀔧􀌶
4.􁞴􀝐􁲁􀝸􀒅􀥒􁉘􀨠􀓱􀛓􁭦􁬋􀒅􀙚􀝄􀚣􀷙􁲁􀸎􀞈􁩻􀷸􀒅􀦇􀺎􁀌􁩻􀷸􀚢􁴻
􁲁􀒅􀦇􀺎􀫪􁩻􀷸􀒅􀓧􁊠􀥒􁉘(􁴠􀾊􀚢􁴻􀙌􀕜􁕚􁑕􁌱􁲁)􀌶
zk:
1.􀨮􀲁􁒒􀩒􀺤􀓻􀷜􁀩􀛒􁲁􀷸􀒅􀣁 zk 􀓤􁌱􀓨􁧆􀷜􁀩􀩒􀬫􁌱􀳰􀨧􁜓􁅩􁌱􁍓􀭯
􀓥􀒅􁊞􀱮􀓞􀓻􀠔􀓞􁌱􁎖􀷸􀹍􀬧􁜓􁅩 node1;
2.􀨮􀲁􁒒􁞴􀝐􁧆􁪠􀮆􀓥􀲅􀹍􀫪􁕪􀚠􀭌􁌱􀧼􁜓􁅩􀒅􀦇􀺎􀝎􁈿􁛔􀫩􀚠􀭌􁌱
node1 􁌱􀬧􀝩􀸎􀹋􀩜􁌱􀒅􀩪􁦊􀔅􁬯􀓻􀨮􀲁􁒒􁞴􀮑􀔧􁲁􀌶
3.􀦇􀺎􀝎􁈿 node1 􀓧􀸎􀹋􀩜􁌱􀒅􀚞􁍊􀞍􀾲􁛔􀫩􀚠􀭌􁜓􁅩􀬧􀝩􀩜􁌱􀹋􀥟􁌱􁜓
􁅩􀒅􁬰􀙁􁒵􀮇􀌶
4.􁞴􀝐􁲁􀝸􀒅􀥒􁉘􀨠􁭦􁬋􀒅􀚢􁴻􁛔􀫩􀚠􀭌􁌱 node1 􀜨􀝢􀌶􀜄􀚦:zk 􀯔􁚆􀫧
􀓞􀔶􀒅􀭏􁲀􀥟􀒅􀨫􁈿􁓌􀜔􀌶
4􀌵􁎣􁭲 redis 􁌱􀳮􀔋􀛸􀞀?􀬬􀩶􀦇􀖜􀨫􁈿􁌱?􀹍􀕋􀔍􀕽􁅩􁗌􁅩?
RDB(Redis DataBase:􀣁􀓧􀝶􁌱􀷸􁳵􁅩􀩙 redis 􁌱􀷄􀴝􁊞􀱮􁌱􀮳􁆙􀝶􀾍􀚩􁏺
􁍏􁒵􀕕􁨶􀓤):􀙖􀨂􀚩􁏝􁍏􁌱􀮳􁆙􀒅􀨧􀹗􀹅􀷛􀌶􁗌􁅩:􁘙􀷸􀒅􁘙􀯔􁚆(fork+io 􀶙
􀖢)􀒅􀸃􀓶􀥦􀷄􀴝􀌶
AOF(Append Only File:􀩙redis􀲅􀲗􁤈􁬦􁌱􀲅􀹍􀳰􀕥􁮷􁦕􀭯􀓥􀹶􀒅􀣁􀓥􀽺
redis􁯿􀞐􀷸􀒅􀝝􁵱􁥝􀲗􁤈􀳰􀕥􀩪􀝢􀕦􀔧):􀙟􀷭􀮪􀌶􁗌􁅩:􀖛􁑌􀥟􀒅􀯩􀥔􁭛􀬶
􀱌􀌶
bgsave 􀘉􁳒􀘟􀙂􁰁􀳮􀔋􀛸􀒅aof 􀘉􀥀􁰁􀳮􀔋􀛸􀌶􀢩􀔅 bgsave 􀕿􁁾􁘙􀾲􁫾
􁳩􁌱􀷸􁳵􀒅􀓧􀥜􀨫􀷸􀒅􀣁􀘊􀹢􁌱􀷸􀗲􀕿􀩕􁛘􀥟􁰁􁌱􀷄􀴝􀓶􀥦􀒅􁵱􁥝 aof 􀹶
􁯈􀝳􀒅􀣁 redis 􀨫􀖺􁯿􀞐􀷸􀒅􀕽􀘶􀖵􁊠 aof 􀹶􀯩􀥔􀙖􀨂􁌱􁇫􀮾􀒅􀦇􀺎􁀌􀹍
aof 􀷭􀮪􀒅􀩪􀕿􀖵􁊠 rdb 􀷈􀕯􀹶􀯩􀥔􀌶Redis 􀕿􀨧􀹗􀘉 aof 􁯿􀙟􀒅􀜴􁖽 aof
􀷈􀕯􀷭􀮪􀥟􀩜􀌶Redis4.0 􀔏􀝸􀹍􀔧􁂰􀝳􀳮􀔋􀛸􁌱􀛑􁚆􀒅􀩙 bgsave 􁌱􀙂􁰁
􀞾 aof 􁌱􀥀􁰁􀘉􀔧􁣟􀝳􀥒􁉘􀒅􁬯􀻏􀷬􀗛􁦤􀔧􀯩􀥔􁌱􀶴􁈲􀝈􀙑􁶶􀔧􀷄􀴝􁌱􀨞
􀙂􀯔􀌶bgsave 􁌱􀜻􁉘􀒅fork 􀞾 cow, fork 􀸎􀳰 redis 􁭗􁬦􀚠􀭌􀧼􁬰􁑕􀹶􁬰
􁤈 bgsave 􀶙􀖢􀒅cow 􀳰􁌱􀸎 copy on write􀒅􀧼􁬰􁑕􀚠􀭌􀝸􀒅􁆿􀧼􁬰􁑕􀙈
􀕁􀷄􀴝􀾧􀒅􁆿􁬰􁑕􁖀􁖅􀵉􀗀􁧛􀙟􀹐􀛓􀒅􀙟􁚍􁌱􁶭􁶎􀷄􀴝􀕿􁭑􁂹􀞾􀧼􁬰􁑕􀚓
􁐶􀭏􀹶􀌶
5􀌵redis 􁬦􀹗􁒽􁊼􁮷􀹍􀟺􀔶?LRU 􁓒􁀩􁎣􁭲􀞀?􀙟􀓞􀓥 java 􀕤􁎱􀨫􁈿?
􁬦􀹗􁒽􁊼:
􀨧􀷸􁬦􀹗(􀓞 key 􀓞􀨧􀷸􀢏)􀒅􀰭􀯔􁬦􀹗:􀝝􀹍􀖵􁊠 key 􀷸􀲍􀚣􀷙 key 􀸎􀞈􀫪
􁬦􀹗􀒅􁬦􀹗􀚞􁂴􁴻􀌶􀨧􀹗􁬦􀹗:􀚹􀓷􁘏􀲰􀓾􀌶
LRU:new LinkedHashMap<K, V>(capacity, DEFAULT_LOAD_FACTORY, tr
ue);
//􁒫􀓣􀓻􀝇􀷄􁗝􀔅 true􀒅􀕤􁤒 linkedlist 􀳲􁦢􁳯􁶲􀬧􀴭􀬧􀒅􀝢􀖢􀔅 LRU 􁖨􀨂
;􁦡􀔅 false 􀕤􁤒 􀳲􀵊􀙁􁶲􀬧􀴭􀬧􀒅􀝢􀖢􀔅 FIFO 􁖨􀨂
LRU 􁓒􁀩􀨫􁈿:
1.􁭗􁬦􀝌􀝻􁱾􁤒􀹶􀨫􁈿􀒅􀷛􀷄􀴝􀵊􀙁􀚩􁱾􁤒􀥧􁮱;
2.􀾯􀭮􁖨􀨂􀞸􀓾(􀜨􁖨􀨂 􀷄􀴝􁤩􁦢􁳯)􀒅􀚞􀩙􀷄􀴝􁑏􀚩􁱾􁤒􀥧􁮱;
3.􀭮􁱾􁤒􁃿􁌱􀷸􀗲􀒅􀩙􁱾􁤒􀩲􁮱􁌱􀷄􀴝􀓶􀭒􀌶
LinkedHashMap:HashMap 􀞾􀝌􀝻􁱾􁤒􀝳􀔫􀔅􀓞􀜨􀸎 LinkedHashMap􀌶
HashMap 􀸎􀷫􀬧 􁌱􀒅LinkedHashMap 􁭗􁬦􁖌􀲷􀓞􀓻􁷐􀥘􁌱􀝌􀝻􁱾􁤒􀗛􁦤
􀔧􁬽􀕤􁶲􀬧􀌶􁧆􁬽􀕤􁶲􀬧􀝢􀕦􀸎􀵊􀙁􁶲􀬧(􁼕􁦊)􀒅􀔞􀝢􀕦􀸎􁦢􁳯􁶲􀬧􀌶
6􀌵􁖨􀨂􁑯􁭐􀌵􁖨􀨂􀚋􁑯􀌵􁖨􀨂􁵪􀫄􁥴􀙬􀷜􀻜?
􁖨􀨂􁑯􁭐:􀳰􀺱􁧃􀓞􀓻􀓞􀨧􀓧􀨂􀣁􁌱􀷄􀴝􀒅􀦇􀺎􀕗􀨂􀘙􀩶􀺱􀓧􀚩􀷄􀴝􀚞􀓧􀙟􀙁􁖨􀨂􀒅􁬯􀩙􀩕􁛘􁬯􀓻􀓧􀨂􀣁􁌱􀷄􀴝􀾯􀽺􁧗􀿢􁮷􁥝􀚩 DB 􀝄􀺱􁧃􀒅􀝢􁚆􀩕
􁛘 DB 􀳯􀴧􀌶
􁥴􀙬􀷜􀻜:
1.􀺱􁧃􁬬􀢧􁌱􀷄􀴝􀔅􁑮􀒅􀕖􀲩􁬯􀓻􁑮􁕮􀺎􁬰􁤈􁖨􀨂􀒅􀖕􁬦􀹗􀷸􁳵􀕿􀾲􁫾􁎨;
2.􀫲 􁵇􁬦􁄁􀢏:􀩙􀲅􀹍􀝢􁚆􀨂􀣁􁌱􀷄􀴝􀟢􀫶􀚩􀓞􀓻􁪃􀥜􀥟􁌱 bitmap 􀓾􀒅􀓞
􀓻􀓞􀨧􀓧􀨂􀣁􁌱􀷄􀴝􀕿􁤩􁬯􀓻 bitmap 􀳝􀱼􀴧􀒅􀕗􁘒􁭿􀘹􀔧􀩒 DB 􁌱􀺱
􁧃􀌶
􁖨􀨂􀚋􁑯:􀩒􀔭􁦡􁗝􀔧􁬦􀹗􀷸􁳵􁌱 key􀒅􁖨􀨂􀣁􀺤􀓻􀷸􁳵􁅩􁬦􀹗􁌱􀷸􀗲􀒅􀯴
􀦅􁬯􀷸􁳵􁅩􀩒􁬯􀓻 Key 􀹍􀥟􁰁􁌱􀬚􀝎􁧗􀿢􁬦􀹶􀒅􁬯􀔶􁧗􀿢􀝎􁈿􁖨􀨂􁬦􀹗􀓞
􁛱􁮷􀕿􀕗􀝸􁒒 DB 􀛒􁫹􀷄􀴝􀬚􀢧􁦡􀚩􁖨􀨂􀒅􁬯􀓻􀷸􀗲􀥟􀬚􀝎􁌱􁧗􀿢􀝢􁚆􀕿
􁎖􁳵􀲩 DB 􀜴􀤂􀌶
􁥴􀙬􀷜􀻜:
1.􀖵􁊠􀔰􀷕􁲁:􀭮􁖨􀨂􀥦􀶴􀷸􀒅􀓧􁒈􀜨􀝄load db􀒅􀘶􀖵􁊠􀦇Redis􁌱setnx􀝄
􁦡􁗝􀓞􀓻􀔰􀷕􁲁􀒅􀭮􀶙􀖢􀱮􀛑􁬬􀢧􀷸􀙚􁬰􁤈load db􁌱􀶙􀖢􀬚􀢧􁦡􁖨􀨂􀒅􀞈
􀚞􁯿􁦶get􁖨􀨂􁌱􀷜􁀩􀌶
2.􀿞􁬱􀓧􁬦􀹗:􁇔􁉘􀓧􁬦􀹗􀒅􀖕􁭦􁬋􁬦􀹗(􀝸􀝣􀭑􀾍􁕚􁑕􀝄􀚬􀷛)􀌶􁖨􀨂􁵪􀫄:
􁦡􁗝􁖨􀨂􀷸􁯻􁊠􀔧􁍘􀝶􁌱􁬦􀹗􀷸􁳵􀒅􀩕􁛘􁖨􀨂􀣁􀺤􀓞􀷸􀚰􀝶􀷸􀥦􀶴􀒅􁧗􀿢
􀙂􁮱􁫨􀝎􀚩 DB􀒅DB 􁎖􀷸􀜴􀛎􁬦􁯿􁵪􀫄􀌶􀓨􁖨􀨂􀚋􁑯􁌱􀜄􀚦:􁵪􀫄􀸎􀮉􀥚
key􀒅􀚋􁑯􀸎􀺤􀓞􀓻 key 􁖨􀨂􀌶
􁥴􀙬􀷜􀻜:􀩙􁖨􀨂􀥦􀶴􀷸􁳵􀚓􀷀􀭏􀒅􀾲􀦇􀝢􀕦􀣁􀜻􀹍􁌱􀥦􀶴􀷸􁳵􀤚􁏐􀓤􀥀􀛒
􀓞􀓻􁵋􀹢􊧊􀒅 􀾲􀦇 1-5 􀚓􁰦􁵋􀹢􀒅􁬯􀻏􀾯􀓞􀓻􁖨􀨂􁌱􁬦􀹗􀷸􁳵􁌱􁯿􀥔􁈲􀩪
􀕿􁴳􀖗􀒅􀩪􀮉􁵙􀭚􀝎􁵞􀖛􀥦􀶴􁌱􀔪􀕯􀌶
7􀌵􀣁􁭌􀳠􁖨􀨂􀷸􀒅􀕋􀔍􀷸􀗲􁭌􀳠 redis􀒅􀕋􀔍􀷸􀗲􁭌􀳠 memcached
􁭌􀳠 redis 􁌱􀰘􀙭:
1􀌵􀥔􀹥􀷄􀴝􁕮􀺅􀒅value 􁌱􀷄􀴝􀸎􀟢􀫶􀒅􀚜􁤒􀒅􁵞􀝳􀒅􀹍􀬧􁵞􀝳􁒵􁬯􁐿􀰘
􀙭􀓥􀒅􀕿􁭌􀳠 redis, 􀢩􀔅 memcache 􀷫􁀩􁃿􁪃􁬯􀔶􀷄􀴝􁕮􀺅􀒅􀹋􀙎􀣳􁌱􁌱
􀖵􁊠􀣋􀸧􀸎􀒅􁊠􀲁􁦈􀜔􀚜􁤒􀒅􁊠􀲁􁁾􀯳􀒅􀫼􀧼􁦧􁦞􁒵􀌶
2􀌵􁵱􁥝􁬰􁤈􀷄􀴝􁌱􀳮􀔋􀛸􀛑􁚆􀒅􀖕􀸎􁀳􀰺􀒅􀓧􁥝􀲩 redis 􀭮􀱮􀷄􀴝􀬪􀖵
􁊠􀒅􀦇􀺎 redis 􀳯􀔧􀒅􀙖􀨂􁚆􀥜􀮳􁭛􀯩􀥔􁅾􀷄􀴝􀒅􀓧􀕿􀩙􀜴􀛎􁎖􁳵􀜴􀣁􀷄
􀴝􀬪􀓤􀒅􁀌􀹍 cache 􁶼􁅾􁌱􁬦􁑕􀌶􀩒􀔭􀝝􁧛􀞾􀷄􀴝􀓞􁛘􀯔􁥝􀿢􀓧􁹛􁌱􀣋􀸧
􀝢􀕦􁯻􁊠􀳮􀔋􀛸􀨂􀘙
3􀌵􁹛􀝢􁊠􀒅redis 􀶪􀳮􁵞􁗭􀒅􀝢􀕦􀨫􁈿􀔆􀛖􀥔􀚫􀒅􁧛􀙟􀚓􁐶􀒅􁘒􀩒􀔭
memcache 􀦇􀺎􀰮􁥝􀨫􁈿􁹛􀝢􁊠􀒅􁵱􁥝􁬰􁤈􀔫􀽺􀭏􀝎􀌶
4􀌵􀨂􀘙􁌱􀙖􀨻􀾲􁫾􀥟􀒅memcache 􀨂􀘙􁌱 value 􀹋􀥟􀔅 1M􀌶
􁭌􀳠 memcache 􁌱􀣋􀸧:
1􀌵􁕍 KV,􀷄􀴝􁰁􁶋􀬉􀥟􁌱􀓱􀛓􀒅􀖵􁊠 memcache 􀹅􀝳􁭇􀒅􀜻􀢩􀸎􀒅
a)memcache 􁌱􀙖􀨂􀚓􁯈􁯻􁊠􁌱􀸎􁶼􀚓􁯈􀙖􀨂􀿰􁌱􁓕􁉘􀷜􀭗􀒅􁚆􀥜􁍜􀝄􀙖
􀨂􀚓􁯈􁌱􀷸􁳵􀒅redis 􀸎􀔁􀷸􁊩􁧗􁑮􁳵􀒅􀝢􁚆􀩕􁛘􁏦􁇆􀛸􀌶
b)􁡦􀳙􀙖􀨂􀖵􁊠􀒅memcache 􀩙􀲅􀹍􁌱􀷄􀴝􀨂􀘙􀣁􁇔􁉘􀙖􀨂􁯾􀒅redis 􀹍􁛔
􀫩􁌱 vm 􀹢􀚫􀒅􁉘􁦞􀓤􁚆􀥜􀨂􀘙􀾲􁇔􁉘􀙖􀨂􀹅􀥚􁌱􀷄􀴝􀒅􀭮􀷄􀴝􁩻􁰁􀷸􀒅
􀭚􀝎 swap,􀲩􀙯􀷄􀴝􀚬􀷛􀚩􁏺􁍏􀓤􀒅􀕗􁬯􁅩􀓤􀒅􀷄􀴝􁰁􀥟􀷸􀒅memcache
􀹅􀮳
c)􁗑􁕶􀽜􀣳􀒅memcache 􀖵􁊠􁶋􁴥􀤲􁌱 IO 􀥔􁊠􀽜􀣳􀒅redis 􀔞􀸎􀖵􁊠􁶋􁴥
􀤲􁌱 IO 􀥔􁊠 􀽜􀣳􀒅􀖕􀸎 redis 􁬮􀵉􀗀􀔧􀓞􀔶􁶋 KV 􀨂􀘙􀔏􀥘􁌱􀴭􀬧􀒅􁘸􀝳
􀛑􁚆􀒅􀥔􀹥􁌱 CPU 􁦇􁓒􀒅􀕿􁴥 􀤲􀷆􀓻 IO 􁧣􀬶􀒅􀕗􁬯􁅩􀓤􁊧􀔭 redis 􀵉􀗀
􁌱􀛑􁚆􁫾􀥚􀒅memcache 􀹅􀮳􀔶
d) 􁕚􁑕􀽜􀣳􀒅memcache􀖵􁊠􀥚􁕚􁑕􀒅􀔆􁕚􁑕􁍊􀞍􀒅worker􀧼􁕚􁑕􀴳􀝑􁧗
􀿢􀒅􀲗􁤈􁧛􀙟􀒅􁬯􀓻􁬦􁑕􀝢􁚆􀨂􀣁􁲁􀙫􁑱􀌶redis 􀖵􁊠􁌱􀜔􁕚􁑕􀒅􁡱􁆐􀷫􁲁
􀙫􁑱􀒅􀖕􀸎􁵙􀕦􀚥􁊠􀥚􀻐􁌱􁇙􀯔􀵉􀜋􀞃􀝺􁰁􀌶
8􀌵􁖨􀨂􀓨􀷄􀴝􀬪􀓧􀓞􁛘􀯆􀔍􀛐
􀘃􁦡􁯻􁊠􁌱􀔆􀨂􀚓􁐶􀒅􁧛􀙟􀚓􁐶􁌱􀷄􀴝􀬪􀒅
􀦇􀺎􀓞􀓻􁕚􁑕 A 􀘶􀚢􁴻􁖨􀨂􀷄􀴝􀒅􁆐􀝸􀩙􀷄􀴝􀙟􀙁􀚩􀔆􀬪􀭮􀓾􀒅􁬯􀓻􀷸
􀗲􀒅􀔆􀬪􀞾􀕗􀬪􀝶 􀾍􁀌􀹍􀨠􀱮􀒅􁕚􁑕 B 􀕗􁖨􀨂􀭮􀓾􁧛􀝐􀷄􀴝􀥦􁨳􀒅􀕗􀕗
􀬪􀭮􀓾􁧛􀝐􀚩􀷯􀷄􀴝􀒅􁆐􀝸􀹅􀷛􁛗􁖨􀨂􀒅􁬯􀓻􀷸􀗲􀒅􁖨􀨂􀭮􀓾􁌱􀩪􀸎􀷯􁌱
􀷄􀴝􀌶
􀝎􁊞􀓤􁬿􀓧􀓞􁛘􁌱􀜻􀢩􀣁􀔭􀒅􀔆􀕗􀬪􀷄􀴝􀓧􀓞􁛘􁳯􁷌􀒅􀛒􀙁􀔧􁖨􀨂􀔏􀝸􀒅
􀔆􀕗􀓧􀓞􁛘􁌱􀷸􁳵􁤩􀳉􁳩􀔧
􀥒􁉘􀯏􁪠:􀣁􀕗􀬪􀹍􀷄􀴝􀹅􀷛􀔏􀝸􀒅􀩙􁖨􀨂􀭮􀓾􁌱􀷄􀴝􀔞􀝶􀷸􁬰􁤈􀹅􀷛􀒅􀜨
􀭮􀕗􀬪􀝎􁊞􀔧􀷄􀴝􀹅􀷛􀔏􀝸􀒅􀝻􁖨􀨂􀝎􀚊􀚢􁴻􀒅􁂣􀿶􁬯􀾧􀷸􁳵􀙟􀙁􁌱􀷯􀷄
􀴝􀌶
9􀌵􀔆􀕗􀷄􀴝􀬪􀓧􀓞􁛘􀦇􀖜􁥴􀙬
􀣋􀸧􀵈􁬿􀒅􀩒􀔭􀔆􀕗􀬪􀒅􁧛􀙟􀚓􁐶􀒅􀦇􀺎􀔆􀕗􀬪􀹅􀷛􀝶􀾍􀹍􀷸􀫧􀒅􀩪􀕿􀩕
􁛘􀔆􀕗􀬪􀷄􀴝􁌱􀓧􀓞􁛘
1􀌵􀮺􁊼􁬯􀓻􀷄􀴝􀓧􀓞􁛘􀒅􀣁􀷄􀴝􀓞􁛘􀯔􁥝􀿢􀓧􁹛􁌱􀓱􀛓􀓥􀒅􀹚􀮠􁵱􁥝􀷸
􀷸􀓞􁛘􀯔
2􀌵􀭩􀚫􁧛􀔆􀬪􀒅􀖵􁊠􀓞􀓻􁹛􀝢􁊠􁌱􀔆􀬪􀒅􀷄􀴝􀬪􁧛􀙟􁮷􀣁􀔆􀬪􀒅􁂲􀛒􀓞
􀓻􁖨􀨂􀒅􀵉􀜋􀷄􀴝􁧛􀝐􁌱􀯔􁚆􀌶
3􀌵􁭌􀳠􀯔􁧛􀔆􀬪􀒅􁂲􀛒􀓞􀓻􁖨􀨂􀒅􁊠􀹶􁦕􀭯􀮠􁶳􁧛􀔆􀬪􁌱􀷄􀴝􀒅􀩙􀟺􀓻
􀬪􀒅􀟺􀓻􁤒􀒅􀟺􀓻􀔆􁲫􀒅􀖢􀔅􁖨􀨂􁌱 key,􁦡􁗝􁖨􀨂􀥦􀶴􁌱􀷸􁳵􀔅􀔆􀕗􀬪􀝶
􀾍􁌱􀷸􁳵􀒅􀦇􀺎􁖨􀨂􀭮􀓾􀹍􁬯􀓻􀷄􀴝􀒅􁍗􀴳􁧛􀝐􀔆􀬪􀒅􀦇􀺎􁖨􀨂􀭮􀓾􁀌􀹍
􁬯􀓻􀔆􁲫􀒅􀩪􀚩􀩒􀬫􁌱􀕗􀬪􀓾􁧛􀝐􀌶
10􀌵Redis 􀬉􁥠􁌱􀯔􁚆􁳯􁷌􀞾􁥴􀙬􀷜􀻜
1􀌵master 􀹋􀦅􀓧􁥝􀘉􀳮􀔋􀛸􀫡􀖢􀒅􀦇 RDB 􀙖􀨂􀮳􁆙􀞾 AOF 􀷭􀮪􀷈􀕯
2􀌵􀦇􀺎􀷄􀴝􀾲􁫾􁯿􁥝􀒅􀺤􀓻 slave 􀭏􀞐 AOF 􀥓􀕲􀒅􁒽􁊼􁦡􁗝􀱮􀾯􁑁􀝶􀾍
􀓞􀽺
3􀌵􀔅􀔧􀔆􀕗􀥔􀚫􁌱􁭛􀬶􀞾􁬳􀴳􁌱􁑞􀨧􀯔􀒅master 􀞾 Slave 􀹋􀦅􀣁􀓞􀓻􀩴
􀤒􁗑􀙖
4􀌵􀩱􁰁􁭿􀘹􀣁􀜴􀛎􀥟􀮑􀔆􀬪􀓤􀥀􀛒􀕗􀬪
5􀌵􀔆􀕗􀥔􀚫􀓧􁥝􁯻􁊠􁗑􁇫􁕮􀺅􀒅􀩱􁰁􀸎􁕚􀯔􁕮􀺅􀒅Master<--Slave1<----
Slave2 ....
11􀌵Redis 􁌱􀷄􀴝􁂣􀿶􁒽􁊼􀹍􀟺􀔶
voltile-lru 􀕗􀫪􁕪􁦡􁗝􁬦􀹗􀷸􁳵􁌱􀷄􀴝􁵞􀓾􀳴􁭌􀹋􁬪􀹋􀩝􀖵􁊠􁌱􀷄􀴝􁂣􀿶
voltile-ttl 􀕗􀫪􁕪􁦡􁗝􁬦􀹗􀷸􁳵􁌱􀷄􀴝􀬪􁵞􀭮􀓾􀳴􁭌􀩙􁥝􁬦􀹗􁌱􀷄􀴝
voltile-random 􀕗􀫪􁕪􁦡􁗝􁬦􀹗􀷸􁳵􁌱􀷄􀴝􁵞􀕱􀰺􁭌􀳠􁂣􀿶􀷄􀴝 allkeys-lru
􀕗􀷄􀴝􁵞􀓾􀳴􁭌􀹋􁬪􀹋􀩝􀖵􁊠􁌱􀷄􀴝􁂣􀿶
allkeys-random 􀕗􀷄􀴝􁵞􀓾􀕱􀰺􁭌􀳠􁂣􀿶􁌱􀷄􀴝 no-eviction 􁐬􀾊􁸝􁭑􀷄􀴝
12􀌵Redis 􀭮􀓾􀹍􀟺􀔶􀷄􀴝􁕮􀺅
􀨁􁒧􀔀 String􀌵􀨁􀙎 Hash􀌵􀚜􁤒 List􀌵􁵞􀝳 Set􀌵􀹍􀬧􁵞􀝳 SortedSet􀌶
􀦇􀺎􀸎􁹛􁕆􁊠􀲁􀒅􁮎􀔍􁬮􀕿􀹍􀒅􀦇􀺎􀖦􀸎 Redis 􀓾􁹛􁕆􁊠􀲁􀒅􁬮􁵱􁥝􀛒􀓤
􀓥􁶎􀙾􁐿􀷄􀴝􁕮􀺅 HyperLogLog􀌵 Geo􀌵Pub/Sub􀌶
13􀌵􀘃􀦇 Redis 􁯾􁶎􀹍 1 􀕊􀓻 key􀒅􀙌􀓾􀹍 10w 􀓻 key 􀸎􀕦􀺤􀓻􀢴􀨧􁌱
􀫪􁎣􁌱􀚹􁖗􀭏􀥧􁌱􀒅􀦇􀺎􀩙􀨙􀕪􀙂􁮱􀲤􀚊􀹶?
􀖵􁊠 keys 􀳰􀕥􀝢􀕦􀲚􀚊􀳰􀨧􀽜􀭗􁌱 key 􀚜􁤒􀌶
􀩒􀷜􀴳􁍳􁭄􁳯:􀦇􀺎􁬯􀓻 redis 􀾋􀣁􁕳􁕚􀓤􁌱􀓱􀛓􀵉􀗀􀹐􀛓􀒅􁮎􀖵􁊠 keys
􀳰􀕥􀕿􀹍􀕋􀔍􁳯􁷌?
􁬯􀓻􀷸􀗲􀖦􁥝􀢧􁒼 redis 􀙉􁲫􁌱􀓞􀓻􁇙􀯔:redis 􁌱􀜔􁕚􁑕􁌱􀌶keys 􀳰􀕥􀕿
􀩕􁛘􁕚􁑕􁴥􀤲􀓞􀾧􀷸􁳵􀒅􁕚􀓤􀹐􀛓􀕿􀘊􁶷􀒅􁍗􀚩􀳰􀕥􀲗􁤈􀨠􀾳􀒅􀹐􀛓􀲍􁚆
􀯩􀥔􀌶􁬯􀓻􀷸􀗲􀝢􀕦􀖵􁊠 scan 􀳰 􀕥􀒅scan 􀳰􀕥􀝢􀕦􀷫􁴥􀤲􁌱􀵉􀝐􀚊􀳰􀨧
􀽜􀭗􁌱 key 􀚜􁤒􀒅􀖕􀸎􀕿􀹍􀓞􀨧􁌱􁯿􀥔􀼷􁈲􀒅􀣁􀨮 􀲁􁒒􀘉􀓞􀽺􀝄􁯿􀩪􀝢􀕦
􀔧􀒅􀖕􀸎􀷆􀖛􀲅􁜰􁩇􁌱􀷸􁳵􀕿􀾲􁍗􀴳􁊠 keys 􀳰􀕥􁳩􀌶
14􀌵􀖵􁊠 Redis 􀘉􁬦􀭑􀾍􁴚􀚜􀞀􀒅􀸎􀦇􀖜􀨫􁈿􁌱
􀖵􁊠 list 􁔄􀣳􀗛􀨂􀷄􀴝􀗞􀯳􀒅rpush 􁊞􀔾􁁾􀯳􀒅lpop 􁁾􁩇􁁾􀯳􀒅􀭮 lpop 􁀌
􀹍􁁾􀯳􀷸􀒅􀝢􀕦 sleep 􀓞􀾧􀷸􁳵􀒅􁆐􀝸􀙚􀼄􀺱􀹍􁀌􀹍􀗞􀯳􀒅􀦇􀺎􀓧􀰮
sleep 􁌱􁦾􀒅􀝢􀕦􀖵􁊠 blpop, 􀣁􁀌 􀹍􀗞􀯳􁌱􀷸􀗲􀒅􀕿􀓞􁍗􁴥􀤲􀒅􁍗􀚩􀗞􀯳
􁌱􀚩􀹶􀌶redis 􀝢􀕦􁭗􁬦 pub/sub 􀔆􁷌􁦈􁴅􀽜􀭗􀨫􁈿􀓞􀓻􁊞􀔾􁘏􀒅􀥚􀓻􁁾
􁩇􁘏􀒅􀭮􁆐􀔞􀨂􀣁􀓞􀨧􁌱􁗌􁅩􀒅􀭮􁁾􁩇􁘏􀓥􁕚􀷸􀒅􁊞􀔾􁌱􁁾􀯳􀕿􀓶􀥦􀌶
15􀌵Redis 􀦇􀖜􀨫􁈿􀭊􀷸􁴚􀚜
􀖵􁊠 sortedset􀒅􀖵􁊠􀷸􁳵􀱿􀘉 score, 􁁾􀯳􀙖􀨻􀖢􀔅 key,􁧣􁊠 zadd 􀹶􁊞􀔾
􁁾􀯳􀒅􁁾􁩇􁘏􀖵􁊠 zrangbyscore 􁞴􀝐 n 􁑁􀔏􀚹􁌱􀷄􀴝􀘉􁫪􁧃􀥒􁉘􀌶
16􀌵􀕋􀔍􀸎 Redis?􁓌􁬿􀨙􁌱􀕽􁗌􁅩?
Redis 􀹜􁨶􀓤􀸎􀓞􀓻 Key-Value 􁔄􀣳􁌱􀙖􀨂􀷄􀴝􀬪􀒅􀮉􀘟 memcached􀒅􀷆
􀓻􀷄􀴝􀬪􁕹􁕹􀛒􁫹􀣁􀙖􀨂􀭮􀓾􁬰􁤈􀶙􀖢􀒅􀨧􀹗􁭗􁬦􀭑􀾍􀶙􀖢􀲩􀷄􀴝􀬪􀷄􀴝
flush 􀚩􁏝􁍏􀓤􁬰􁤈􀗛􀨂􀌶
􀢩􀔅􀸎􁕍􀙖􀨂􀶙􀖢􀒅Redis 􁌱􀯔􁚆􁶋􀬉􀚊􁜋􀒅􀾯􁑁􀝢􀕦􀥒􁉘􁩻􁬦 10 􀓡􀽺􁧛
􀙟􀶙􀖢􀒅􀸎􀫪􁎣􀯔􁚆􀹋􀮳􁌱 Key-Value DB􀌶
Redis 􁌱􀚊􁜋􀔏􀥒􀓧􀕐􀕐􀸎􀯔􁚆􀒅Redis 􀹋􀥟􁌱􁹲􀛎􀸎􀶪􀳮􀗛􀨂􀥚􁐿􀷄􀴝
􁕮􀺅􀒅􀾌􀥘􀜔􀓻 value 􁌱􀹋􀥟􁴴􀚫􀸎 1GB􀒅􀓧􀘟 memcached 􀝝􁚆􀗛􀨂
1MB 􁌱􀷄􀴝􀒅􀢩􀾌 Redis 􀝢􀕦􁊠􀹶􀨫􁈿􀮉􀥚􀹍􁊠􁌱􀛑􁚆􀌶
􀾲􀷜􁧔􁊠􀕜􁌱 List 􀹶􀘉 FIFO 􀝌􀝻􁱾􁤒􀒅􀨫􁈿􀓞􀓻􁫷􁰁􁕆􁌱􁹛􀯔 􁚆􁁾􀯳􁴚
􀚜􀹐􀛓􀒅􁊠􀕜􁌱 Set 􀝢􀕦􀘉􁹛􀯔􁚆􁌱 tag 􁔮􁕹􁒵􁒵􀌶
􀝚􀥘Redis􀔞􀝢􀕦􀩒􀨂􀙁􁌱Key-Value􁦡􁗝expire􀷸􁳵􀒅􀢩􀾌􀔞􀝢􀕦􁤩􀭮􀖢􀓞
􀓻􀛑􁚆􀛒􀭩􁇇􁌱memcac hed 􀹶􁊠􀌶 Redis 􁌱􀔆􁥝􁗌􁅩􀸎􀷄􀴝􀬪􀨻􁰁􀝑􀚩
􁇔􁉘􀙖􀨂􁌱􁴴􀚫􀒅􀓧􁚆􁊠􀖢􁁹􁰁􀷄􀴝􁌱􁹛􀯔􁚆􁧛􀙟􀒅􀢩􀾌 Redis 􁭇􀝳􁌱􀣋
􀸧􀔆􁥝􀩴􁴴􀣁􁫾􀩜􀷄􀴝􁰁􁌱􁹛􀯔􁚆􀶙􀖢􀞾􁬩􁓒􀓤􀌶
17􀌵Redis 􁍘􀾲 memcached 􀹍􀟺􀔶􀕽􀛠?
(1) memcached􀲅􀹍􁌱􊧊􀣐􀸎􁓌􀜔􁌱􀨁􁒧􀔀􀒅redis􀖢􀔅􀙌􀹊􀕤􁘏􀒅􀶪􀳮􀹅
􀔅􀓿􀩄􁌱􀷄􀴝􁔄􀣳
(2) redis􁌱􁭛􀬶􀾲memcached􀮳􀮉􀥚
(3) redis􀝢􀕦􀳮􀔋􀛸􀙌􀷄􀴝
18􀌵Redis 􀶪􀳮􀟺􀙾􁐿􀷄􀴝􁔄􀣳?
String􀌵List􀌵Set􀌵Sorted Set􀌵hashes
19􀌵Redis 􀔆􁥝􁁾􁘙􀕋􀔍􁇔􁉘􁩒􁃠?
􀙖􀨂􀌶
20􀌵Redis 􁌱􀙂􁑍􀸎􀕋􀔍?
Remote Dictionary Server􀌶
21􀌵Redis 􀹍􀟺􀙾􁐿􀷄􀴝􁂣􀿶􁒽􁊼?
noeviction:􁬬􀢧􁲙􁧏􀭮􀙖􀨂􁴴􀚫􁬡􀚩􀬚􀓬􀨮􀲁􁒒􀩤􁦶􀲗􁤈􀕿􁦏􀹅􀥚􀙖􀨂􁤩
􀖵􁊠􁌱􀞸􀕥(􀥟􁮱􀚓􁌱􀙟􀙁􀳰􀕥􀒅􀖕 DEL 􀞾􀙾􀓻􀖺􀥘)
allkeys-lru: 􀩤􁦶􀢧􀶭􀹋􀩝􀖵􁊠􁌱􁲫(LRU)􀒅􀖵􀮑􀷛􁂲􀛒􁌱􀷄􀴝􀹍􁑮􁳵􀨂􀶱􀌶
volatile-lru: 􀩤􁦶􀢧􀶭􀹋􀩝􀖵􁊠􁌱􁲫(LRU)􀒅􀖕􀕐􁴴􀔭􀣁􁬦􀹗􁵞􀝳􁌱􁲫,􀖵􀮑
􀷛􁂲􀛒􁌱􀷄􀴝􀹍􁑮􁳵􀨂􀶱􀌶
allkeys-random: 􀢧􀶭􁵋􀹢􁌱􁲫􀖵􀮑􀷛􁂲􀛒􁌱􀷄􀴝􀹍􁑮􁳵􀨂􀶱􀌶
volatile-random: 􀢧􀶭􁵋􀹢􁌱􁲫􀖵􀮑􀷛􁂲􀛒􁌱􀷄􀴝􀹍􁑮􁳵􀨂􀶱􀒅􀖕􀕐􁴴􀔭􀣁
􁬦􀹗􁵞􀝳􁌱􁲫􀌶
volatile-ttl: 􀢧􀶭􀣁􁬦􀹗􁵞􀝳􁌱􁲫􀒅􀬚􀓬􀕽􀘶􀢧􀶭􀨂􁁚􀷸􁳵(TTL)􁫾􁎨􁌱􁲫,􀖵
􀮑􀷛􁂲􀛒􁌱􀷄􀴝􀹍􁑮􁳵􀨂􀶱􀌶
22􀌵Redis 􀨥􀷜􀔅􀕋􀔍􀓧􀵉􀗀 Windows 􁇇􀹜?
􀢩􀔅􁍓􀚹 Linux 􁇇􀹜􀫪􁕪􁍘􀭮􁑞􀨧􀒅􁘒􀓬􁊠􀲁􁰁􀮉􀥟􀒅􀷫􁵱􀭏􀝎 windows
􁇇􀹜􀒅􀝍􁘒􀕿􀬃􀹶􀙑􀨻􀯔􁒵􁳯􁷌􀌶
23􀌵􀓞􀓻􀨁􁒧􀔀􁔄􀣳􁌱􊧊􁚆􀨂􀘙􀹋􀥟􀨻􁰁􀸎􀥚􀩝?
512M
24􀌵􀔅􀕋􀔍 Redis 􁵱􁥝􀲩􀲅􀹍􀷄􀴝􀶱􀚩􀙖􀨂􀓾?
Redis 􀔅􀔧􁬡􀚩􀹋􀮳􁌱􁧛􀙟􁭛􀬶􀩙􀷄􀴝􁮷􁧛􀚩􀙖􀨂􀓾􀒅􀬚􁭗􁬦􀭑􀾍􁌱􀷜􀭗
􀩙􀷄􀴝􀙟􀙁􁏺􁍏􀌶
􀲅􀕦 redis 􀙍􀹍􀮳􁭛􀞾􀷄􀴝􀳮􀔋􀛸􁌱􁇙􀮄􀌶􀦇􀺎􀓧􀩙􀷄􀴝􀶱􀣁􀙖􀨂􀓾􀒅􁏺
􁍏 I/O 􁭛􀬶􀔅􀓸􁯿􀭽􀟥 redis 􁌱􀯔􁚆􀌶
􀣁􀙖􀨂􁩼􀹶􁩼􀗎􀨩􁌱􀕔􀥠􀒅redis􀩙􀕿􁩼􀹶􁩼􀝑􀽻􁬨􀌶􀦇􀺎􁦡􁗝􀔧􀹋􀥟􀖵􁊠
􁌱􀙖􀨂􀒅􀚞􀷄􀴝􀫪􀹍􁦕􀭯􀷄􁬡􀚩􀙖􀨂􁴴􊧊􀝸􀓧􁚆􁖀􁖅􀵊􀙁􀷛􊧊􀌶
25􀌵Redis 􁵞􁗭􀷜􀻜􀬫􁧆􀯆􀔍􀘉?􁮷􀹍􀟺􀔶􀷜􀻜?
1.codis􀌶
􁍓􀚹􁊠􁌱􀹋􀥚􁌱􁵞􁗭􀷜􀻜􀒅􀤚􀹜􀞾twemproxy􀓞􁛘􁌱􀶴􀺎􀒅􀖕􀨙􀶪􀳮􀣁 􁜓
􁅩􀷄􁰁􀶯􀝒􀰘􀙭􀓥􀒅􀷯􁜓􁅩􀷄􀴝􀝢􀯩􀥔􀚩􀷛 hash 􁜓􁅩􀌶
2.redis cluster3.0􁛔􀬃􁌱􁵞􁗭􀒅􁇙􁅩􀣁􀔭􀕜􁌱􀚓􀫲􀭗􁓒􁀩􀓧􀸎􀓞􁛘􀯔
hash􀒅􁘒􀸎hash􀽖􁌱􀼷􀮷􀒅􀕦􀝊􁛔􁫝􀶪􀳮􁜓􁅩􁦡􁗝􀕗􁜓􁅩􀌶􀙍􀖛􁍡􀨥􀷜􀷈
􀻩􀕕􁕨􀌶
3.􀣁􀓱􀛓􀕤􁎱􀩶􀨫􁈿􀒅􁩸􀙾􀓻􀾺􀷫􀙉􁘶􁌱 redis 􀨫􀖺􀒅􀣁􀕤􁎱􀩶􀒅􀩒key 􁬰
􁤈hash􁦇􁓒􀒅􁆐􀝸􀝄􀩒􀬫􁌱 redis 􀨫􀖺􀶙􀖢􀷄􀴝􀌶􁬯􁐿􀷜􀭗􀩒 hash 􀩶􀕤􁎱
􁥝􀿢􀾲􁫾􁹛􀒅􁘍􁡤􁮱􀚓􀛱􀳡􀒅􁜓􁅩􀥦􀶴􀝸􁌱􀹊􀕤􁓒􁀩􀷜 􀻜􀒅􀷄􀴝􁵵􁞌􀝸􁌱
􁛔􀛖􁚕􀹜􀯩􀥔􀒅􀨫􀖺􁌱􁍊􀴴􀒅􁒵􁒵􀌶
26􀌵Redis 􁵞􁗭􀷜􀻜􀕋􀔍􀰘􀙭􀓥􀕿􀩕􁛘􀷆􀓻􁵞􁗭􀓧􀝢􁊠?
􀹍 A􀒅B􀒅C 􀓣􀓻􁜓􁅩􁌱􁵞􁗭,􀣁􁀌􀹍􀥔􀚫􀽜􀣳􁌱􀰘􀙭􀓥,􀦇􀺎􁜓􁅩 B 􀥦􁨳
􀔧􀒅􁮎􀔍􀷆􀓻􁵞􁗭􀩪􀕿􀕦􀔅􁗌􀩝 5 501-11000 􁬯􀓻􁝜􀢱􁌱􀽖􁘒􀓧􀝢􁊠􀌶
27􀌵MySQL 􁯾􀹍 2000w 􀷄􀴝􀒅redis 􀓾􀝝􀨂 20w 􁌱􀷄􀴝􀒅􀦇􀖜􀗛􁦤
redis 􀓾􁌱􀷄􀴝􁮷􀸎􁅾􁅩􀷄􀴝?
redis 􀙖􀨂􀷄􀴝􁵞􀥟􀩜􀓤􀜋􀚩􀓞􀨧􀥟􀩜􁌱􀷸􀗲􀒅􀩪􀕿􀷞􁤈􀷄􀴝􁂣􀿶􁒽􁊼􀌶
28􀌵Redis 􀹍􀟺􀔶􁭇􀝳􁌱􀣋􀸧?
(1)􀕿􁦾􁖨􀨂(Session Cache)
􀹋􀬉􁊠􁌱􀓞􁐿􀖵􁊠Redis􁌱􀰘􀸧􀸎􀕿􁦾􁖨􀨂(session cache)􀌶􁊠Redis􁖨􀨂
􀕿􁦾􀾲􀙌􀕜􀨂􀘙(􀦇Mem cached)􁌱􀕽􀛠􀣁􀔭:Redis 􀵉􀗀􀳮􀔋􀛸􀌶􀭮􁖌􀲷􀓞
􀓻􀓧􀸎􀓸􀻒􁥝􀿢􀓞􁛘􀯔􁌱􁖨􀨂􀷸􀒅􀦇􀺎􁊠􀲁􁌱􁨻􁇔􁫣 􀗞􀯳􀙂􁮱􀓶􀥦􀒅􀥟􁮱
􀚓􀕈􁮷􀕿􀓧􁹛􀙊􁌱􀒅􁈿􀣁􀒅􀕜􀕪􁬮􀕿􁬯􀻏􀞀?
􀬛􁬩􁌱􀸎􀒅􁵋􁍳 Redis 􁬯􀔶􀬙􁌱􀶯􁬰􀒅􀮉􀨻􀸃􀲤􀚩􀯆􀔍􀯴􀭮􁌱􀖵􁊠Redis
􀹶􁖨􀨂􀕿􁦾􁌱􀷈􀻩􀌶􁊜􁛗􀬠􀔅􀕈􁎣􁌱􀠟􀓱􀬘􀝣 Magento 􀔞􀵉􀗀 Redis 􁌱􀵊
􀕯􀌶
(2)􀙂􁶭􁖨􀨂(FPC)
􁴻􀤚􀹜􁌱􀕿􁦾 token 􀔏􀥘􀒅Redis 􁬮􀵉􀗀􀮉􁓌􀗎􁌱 FPC 􀬘􀝣􀌶􀢧􀚩􀓞􁛘􀯔
􁳯􁷌􀒅􀜨􀖵􁯿􀞐􀔧 Redis 􀨫 􀖺􀒅􀢩􀔅􀹍􁏺􁍏􁌱􀳮􀔋􀛸􀒅􁊠􀲁􀔞􀓧􀕿􁍡􀚩􁶭
􁶎􀛒􁫹􁭛􀬶􁌱􀓥􁴳􀒅􁬯􀸎􀓞􀓻􀺄􀥟􀶯􁬰􀒅􁔄􀖒 PHP 􀹜􀣈 FPC􀌶
􀙚􀽺􀕦 Magento 􀔅􀖺􀒅Magento 􀵉􀗀􀓞􀓻􀵊􀕯􀹶􀖵􁊠 Redis 􀖢􀔅􀙂􁶭􁖨
􀨂􀝸􁒒􀌶
􀾌􀥘􀒅􀩒 WordPress 􁌱􁊠􀲁􀹶􁧔􀒅Pantheon 􀹍􀓞􀓻􁶋􀬉􀦅􁌱􀵊􀕯 wpredis
􀒅􁬯􀓻􀵊􀕯􁚆􀬆􀛗􀖦􀕦􀹋􀮳
􁭛􀬶􀛒􁫹􀖦􀹉􁁨􁥦􁬦􁌱􁶭􁶎􀌶
(3)􁴚􀚜
Reids􀣁􀙖􀨂􀨂􀘙􀭚􀶚􁶾􀤒􁌱􀓞􀥟􀕽􁅩􀸎􀵉􀗀 list 􀞾 set 􀶙􀖢􀒅􁬯􀖵􀮑
Redis􁚆􀖢􀔅􀓞􀓻􀮉􀦅􁌱􁁾􀯳􁴚􀚜􀬘􀝣􀹶􀖵􁊠􀌶Redis􀖢􀔅􁴚􀚜􀖵􁊠􁌱􀶙
􀖢􀒅􀩪􁔄􀖒􀔭􀹜􀣈􁑕􀬧􁧍􁥺(􀦇Python)􀩒 list 􁌱 push/pop 􀶙􀖢􀌶
􀦇􀺎􀖦􀮳􁭛􁌱􀣁 Google 􀓾􀵤􁔱“Redis queues”􀒅􀖦􁸘􀓤􀩪􁚆􀲤􀚩􀥟􁰁􁌱􀭏
􁃠􁶱􁍓􀒅􁬯􀔶􁶱􁍓􁌱􁍓􁌱􀩪􀸎 􀚥􁊠 Redis 􀚠􀭌􁶋􀬉􀦅􁌱􀝸􁒒􀫡􀙍􀒅􀕦􁃿􁪃
􀝱􁐿􁴚􀚜􁵱􀿢􀌶􀖺􀦇􀒅Celery 􀹍􀓞􀓻􀝸􀝣􀩪􀸎􀖵􁊠 Redis 􀖢 􀔅 broker􀒅􀖦
􀝢􀕦􀕗􁬯􁯾􀝄􀺱􁍡􀌶
(4)􀴭􁤈􀽂/􁦇􀷄􀢏
Redis 􀣁􀙖􀨂􀓾􀩒􀷄􀨁􁬰􁤈􁭓􀥀􀱲􁭓􀙺􁌱􀶙􀖢􀨫􁈿􁌱􁶋􀬉􀦅􀌶􁵞􀝳(Set)􀞾
􀹍􀬧􁵞􀝳(Sorted Set)􀔞
􀖵􀮑􀱯􀕪􀣁􀲗􁤈􁬯􀔶􀶙􀖢􁌱􀷸􀗲􀝒􁌱􁶋􀬉􁓌􀜔􀒅Redis 􀝝􀸎􀾋􀦅􀵉􀗀􀔧􁬯
􀓷􁐿􀷄􀴝􁕮􀺅􀌶 􀲅􀕦􀒅􀱯􀕪􁥝􀕗􀴭􀬧􁵞􀝳􀓾􁞴􀝐􀚩􀴭􀝷􀹋􁶌􀚹􁌱 10 􀓻􁊠
􀲁–􀱯􀕪􁑍􀔏􀔅 “user_scores” 􀒅􀱯􀕪􀝝􁵱􁥝􀘟􀓥
􁶎􀓞􀻏􀲗􁤈􀜨􀝢:
􀭮􁆐􀒅􁬯􀸎􀘃􀨧􀖦􀸎􀻑􀴝􀖦􁊠􀲁􁌱􀚓􀷄􀘉􁭓􀥀􁌱􀴭􀬧􀌶􀦇􀺎􀖦􀰮􁬬􀢧􁊠􀲁
􀝊􁊠􀲁􁌱􀚓􀷄􀒅􀖦􁵱􁥝􁬯􀻏􀲗􁤈:
ZRANGE user_scores 0 10 WITHSCORES
Agora Games 􀩪􀸎􀓞􀓻􀮉􀦅􁌱􀖺􀧼􀒅􁊠 Ruby 􀨫􁈿􁌱􀒅􀨙􁌱􀴭􁤈􀽂􀩪􀸎􀖵
􁊠 Redis 􀹶􀨂􀘙􀷄􀴝􁌱􀒅􀖦􀝢􀕦􀣁􁬯􁯾􁍡􀚩􀌶
(5)􀝎􀫲/􁦈􁴅
􀹋􀝸(􀖕􁙗􀨧􀓧􀸎􀹋􀓧􁯿􁥝􁌱)􀸎 Redis 􁌱􀝎􀫲/􁦈􁴅􀛑􁚆􀌶􀝎􀫲/􁦈􁴅􁌱􀖵􁊠
􀣋􀸧􁏟􀨫􁶋􀬉􀥚􀌶􀱯􀫪􁍡􁥠􀕈􀕪􀣁􁐒􀔻􁗑􁕶􁬳􀴳􀓾􀖵􁊠􀒅􁬮􀝢􀖢􀔅􀤚􀔭􀝎
􀫲/􁦈􁴅􁌱􁚕􀹜􁥶􀝎􀢏􀒅􁊜􁛗􁊠 Redis 􁌱􀝎􀫲/􁦈􁴅􀛑􁚆􀹶􀭌 􁒈􁘱􀥠􁔮􁕹!
29􀌵Redis 􀶪􀳮􁌱 Java 􀨮􀲁􁒒􁮷􀹍􀟺􀔶?􀨥􀷜􀴵􁞂􁊠􀟺􀓻?
Redisson􀌵Jedis􀌵lettuce 􁒵􁒵􀒅􀨥􀷜􀴵􁞂􀖵􁊠 Redisson􀌶
30􀌵Redis 􀞾 Redisson 􀹍􀕋􀔍􀙉􁔮?
Redisson 􀸎􀓞􀓻􁹛􁕆􁌱􀚓􀫲􀭗􀜐􁧣 Redis 􀨮􀹐􁒒􀒅􁚆􀬆􀛗􁊠􀲁􀣁􀚓􀫲􀭗􁈾
􀤹􀓾􁫷􀺂􀨫􁈿􀓞􀔶 Java 􁌱􀩒􁨝 (Bloom filter, BitSet, Set, SetMultimap,
ScoredSortedSet, SortedSet, Map, ConcurrentMap, List, List Multimap,
Queue, BlockingQueue, Deque, BlockingDeque, Semaphore, Lock,
ReadWriteLock, Atomi cLong, CountDownLatch, Publish / Subscribe,
HyperLogLog)􀌶
31􀌵Jedis 􀓨 Redisson 􀩒􀾲􀹍􀕋􀔍􀕽􁗌􁅩?
Jedis 􀸎 Redis 􁌱 Java 􀨫􁈿􁌱􀨮􀲁􁒒􀒅􀙌 API 􀵉􀗀􀔧􀾲􁫾􀙂􁶎􁌱 Redis 􀞸
􀕥􁌱􀶪􀳮;
Redisson 􀨫􁈿􀔧􀚓􀫲􀭗􀞾􀝢􀲘􀪀􁌱 Java 􀷄􀴝􁕮􀺅􀒅􀞾 Jedis 􁍘􀾲􀒅􀛑􁚆
􁫾􀔅􁓌􀜔􀒅􀓧􀶪􀳮􀨁􁒧􀔀􀶙􀖢􀒅􀓧􀶪􀳮􀴭􀬧􀌵􀔪􀛓􀌵􁓕􁭲􀌵􀚓􀜄􁒵 Redis
􁇙􀯔􀌶Redisson 􁌱􀨤􀷰􀸎􀗏􁬰􀖵􁊠􁘏􀩒 Redis 􁌱􀙉􁀳􀚓􁐶􀒅􀕗􁘒􁦏􀖵􁊠􁘏
􁚆􀥜􀩙􁔜􀛎􀹅􁵞􀓾􀣈􀶱􀣁􀥒􁉘􀓱􀛓􁭦􁬋􀓤􀌶
32􀌵Redis 􀦇􀖜􁦡􁗝􀩂􁎱􀝊􁸵􁦤􀩂􁎱?
􁦡􁗝􀩂􁎱:config set requirepass 123456
􀴦􀹦􀩂􁎱:auth 123456
33􀌵􁧔􁧔 Redis 􀟢􀫶􀽖􁌱􀼷􀮷?
Redis 􁵞􁗭􁀌􀹍􀖵􁊠􀓞􁛘􀯔 hash,􁘒􀸎􀭚􀙁􀔧􀟢􀫶􀽖􁌱􀼷􀮷􀒅Redis 􁵞􁗭􀹍
16384 􀓻􀟢􀫶􀽖􀒅􀾯􀓻 key 􁭗􁬦 CRC16 􀻊􁸵􀝸􀩒 16384 􀝐􀽜􀹶􀙬􀨧􀶱􁗝
􀟺􀓻􀽖􀒅􁵞􁗭􁌱􀾯􀓻􁜓􁅩􁨮􁨱􀓞􁮱􀚓 hash 􀽖􀌶
34􀌵Redis 􁵞􁗭􁌱􀔆􀕗􀥔􀚫􀽜􀣳􀸎􀯆􀻏􁌱?
􀔅􀔧􀖵􀣁􁮱􀚓􁜓􁅩􀥦􁨳􀱲􁘏􀥟􁮱􀚓􁜓􁅩􀷫􁀩􁭗􀗞􁌱􀰘􀙭􀓥􁵞􁗭􀕖􁆐􀝢􁊠􀒅
􀲅􀕦􁵞􁗭􀖵􁊠􀔧􀔆􀕗􀥔􀚫􀽜􀣳,􀾯􀓻􁜓􁅩􁮷􀕿􀹍 N-1 􀓻􀥔􀚫􀟝.
35􀌵Redis 􁵞􁗭􀕿􀹍􀙟􀶙􀖢􀓶􀥦􀞀?􀔅􀕋􀔍?
Redis 􀬚􀓧􁚆􀗛􁦤􀷄􀴝􁌱􀭩􀓞􁛘􀯔􀒅􁬯􀰺􀞱􁬯􀣁􀨫􁴬􀓾􁵞􁗭􀣁􁇙􀨧􁌱􀹵􀕯
􀓥􀝢􁚆􀕿􀓶􀥦􀙟􀶙􀖢􀌶
36􀌵Redis 􁵞􁗭􀔏􁳵􀸎􀦇􀖜􀥔􀚫􁌱?
􀭑􀾍􀥔􀚫
37􀌵Redis 􁵞􁗭􀹋􀥟􁜓􁅩􀓻􀷄􀸎􀥚􀩝?
16384 􀓻􀌶
38􀌵Redis 􁵞􁗭􀦇􀖜􁭌􀳠􀷄􀴝􀬪?
Redis 􁵞􁗭􁍓􀚹􀷫􁀩􀘉􀷄􀴝􀬪􁭌􀳠􀒅􁼕􁦊􀣁 0 􀷄􀴝􀬪􀌶
39􀌵􀯆􀔍􁁥􁦶 Redis 􁌱􁬳􁭗􀯔?
ping
40􀌵Redis 􀓾􁌱􁓕􁭲􀹍􀕋􀔍􁊠?
􀓞􀽺􁧗􀿢/􀟥􀬫􀹐􀛓􀢏􁚆􀨫􁈿􀥒􁉘􀷛􁌱􁧗􀿢􀜨􀖵􀷯􁌱􁧗􀿢􁬮􀹚􁤩􀟥􀬫􀌶􁬯􀻏
􀩪􀝢􀕦􀩙􀥚􀓻􀞸􀕥􀝎􁭆􀚩􀹐􀛓􀢏􀒅􁘒􀓧􁊠􁒵􀮇􀢧􀥔􀒅􀹋􀝸􀣁􀓞􀓻􀾍􁹈􀓾􁧛
􀝐􁧆􁒼􀥔􀌶
􁬯􀩪􀸎􁓕􁭲(pipelining)􀒅􀸎􀓞􁐿􀙾􀜈􀬙􀹶􀬠􁀬􀖵􁊠􁌱􀲦􀹞􀌶􀖺􀦇􁦜􀥚 POP3
􀜐􁦓􀫪􁕪􀨫􁈿􀶪􀳮􁬯􀓻􀛑􁚆􀒅􀥟􀥟􀛒􀮳􀔧􀕗􀹐􀛓􀢏􀓥􁫹􀷛􁮒􀕯􁌱􁬦􁑕􀌶
41􀌵􀯆􀔍􁉘􁥴 Redis 􀔪􀛓?
􀔪􀛓􀸎􀓞􀓻􀜔􁇿􁌱􁵍􁐶􀶙􀖢:􀔪􀛓􀓾􁌱􀲅􀹍􀞸􀕥􁮷􀕿􀬧􀚜􀛸􀌵􀳲􁶲􀬧􀣈􀲗
􁤈􀌶􀔪􀛓􀣁􀲗􁤈􁌱􁬦􁑕􀓾􀒅􀓧􀕿􁤩􀙌􀕜􀨮􀲁􁒒􀝎􁭆􀹶􁌱􀞸􀕥􁧗􀿢􀲅􀲑􀷙􀌶
􀔪􀛓􀸎􀓞􀓻􀜻􀧼􀶙􀖢:􀔪􀛓􀓾􁌱􀞸􀕥􁥝􀔍􀙂􁮱􁤩􀲗􁤈􀒅􁥝􀔍􀙂􁮱􁮷􀓧􀲗􁤈􀌶
42􀌵Redis 􀔪􀛓􁍘􀙉􁌱􀞸􀕥􀹍􀟺􀙾􀓻?
MULTI􀌵EXEC􀌵DISCARD􀌵WATCH
43􀌵Redis key􁌱􁬦􀹗􀷸􁳵􀞾􀿞􀔋􀹍􀶴􀚓􀚦􀯆􀔍􁦡􁗝?
EXPIRE 􀞾 PERSIST 􀞸􀕥􀌶
44􀌵Redis 􀦇􀖜􀘉􀙖􀨂􀕽􀛸?
􀩱􀝢􁚆􀖵􁊠􀷀􀚜􁤒(hashes)􀒅􀷀􀚜􁤒(􀸎􁧔􀷀􀚜􁤒􁯾􁶎􀨂􀘙􁌱􀷄􀩝)􀖵􁊠􁌱􀙖
􀨂􁶋􀬉􀩜􀒅􀲅􀕦􀖦􀬫􁧆􀩱􀝢􁚆􁌱􀩙􀖦􁌱􀷄􀴝􀽜􀣳􀳁􁨝􀚩􀓞􀓻􀷀􀚜􁤒􁯾􁶎􀌶
􀾲􀦇􀖦􁌱 web 􁔮􁕹􀓾􀹍􀓞􀓻􁊠􀲁􀩒􁨝􀒅􀓧􁥝􀔅􁬯􀓻􁊠􀲁􁌱􀝷􁑍􀒅􀦨􀿄􀒅
􁮒􁓟􀒅􀩂􁎱􁦡􁗝􀜔􁇿􁌱 key,􁘒􀸎􀬫􁧆􀲩􁬯􀓻􁊠􀲁􁌱􀲅􀹍􀗞􀯳􀨂􀘙􀚩􀓞􀭟􀷀
􀚜􁤒􁯾􁶎􀌶
45􀌵Redis 􀢧􀶭􁬰􁑕􀦇􀖜􀫡􀖢􁌱?
􀓞􀓻􀨮􀲁􁒒􁬩􁤈􀔧􀷛􁌱􀞸􀕥􀒅􁂲􀛒􀔧􀷛􁌱􀷄􀴝􀌶
Redi 􀼄􀺱􀙖􀨂􀖵􁊠􀰘􀙭􀒅􀦇􀺎􀥟􀔭 maxmemory 􁌱􁴴􀚫, 􀚞􀻑􀴝􁦡􀨧􀦅􁌱
􁒽􁊼􁬰􁤈􀢧􀶭􀌶
􀓞􀓻􀷛􁌱􀞸􀕥􁤩􀲗􁤈􀒅􁒵􁒵􀌶
􀲅􀕦􀱯􀕪􀓧􀷙􀣈􁑯􁩼􀙖􀨂􁴴􀚫􁌱􁬟􁊴􀒅􁭗􁬦􀓧􀷙􁬡􀚩􁬟􁊴􁆐􀝸􀓧􀷙􀣈􀢧􀶭
􀢧􀚩􁬟􁊴􀕦􀓥􀌶
􀦇􀺎􀓞􀓻􀞸􀕥􁌱􁕮􀺎􀩕􁛘􀥟􁰁􀙖􀨂􁤩􀖵􁊠(􀖺􀦇􀮉􀥟􁌱􁵞􀝳􁌱􀔻􁵞􀗛􀨂􀚩􀓞
􀓻􀷛􁌱􁲫)􀒅􀓧􁊠􀥚􀔋􀙖􀨂􁴴􀚫􀩪􀕿􁤩􁬯􀓻􀙖􀨂􀖵􁊠􁰁􁩻􁩼􀌶
5.3.2 MongoDB􁶎􁦶􀓫􁷌
1. 􀖦􁧔􁌱 NoSQL 􀷄􀴝􀬪􀸎􀕋􀔍􀰺􀯏?NoSQL 􀓨 RDBMS 􁍗􀴳􀹍􀕋􀔍􀜄
􀚦?􀔅􀕋􀔍􁥝􀖵􁊠􀞾􀓧􀖵􁊠 NoSQL 􀷄􀴝􀬪?􁧔􀓞􁧔 NoSQL 􀷄􀴝􀬪􁌱􀙾􀓻
􀕽􁅩?
NoSQL 􀸎􁶋􀙉􁔮􀣳􀷄􀴝􀬪􀒅NoSQL = Not Only SQL􀌶
􀙉􁔮􀣳􀷄􀴝􀬪􁯻􁊠􁌱􁕮􀺅􀛸􁌱􀷄􀴝􀒅NoSQL 􁯻􁊠􁌱􀸎􁲫􊧊􀩒􁌱􀷜􀭗􀨂􀘙
􀷄􀴝􀌶
􀣁􀥒􁉘􁶋􁕮􀺅􀛸/􀜎􁕮􀺅􀛸􁌱􀥟􀷄􀴝􀷸;􀣁􀿜􀬘􀷜􀝻􀓤􁬰􁤈􀲘􀪀􀷸;􁵋􀷸􀬫􀩒
􀛖􀮾􀥀􀛒􁌱􀷄􀴝􁶱􀷸􀝢􀕦􀕽 􀘶􁘍􁡤􀖵􁊠 NoSQL 􀷄􀴝􀬪􀌶
􀣁􁘍􁡤􀷄􀴝􀬪􁌱􀱮􁆧􀬶;􀶪􀳮;􀚓􀺉􀞾􀠟􀓱􀸬􁚆;􁓕􁉘􀝊􀓫􀓱􀯔􁒵􁳯􁷌􀷸􀒅􀬫
􀕽􀘶􁘍􁡤􀙉􁔮􀣳􀷄􀴝􀬪􀌶
2. NoSQL 􀷄􀴝􀬪􀹍􀟺􀔶􁔄􀣳?
􀖺􀦇:MongoDB, Cassandra, CouchDB, Hypertable, Redis, Riak, Neo4j,
HBASE, Couchbase, MemcacheDB, RevenDB and Voldemort are the
examples of NoSQL databases.
3. MySQL 􀓨 MongoDB 􀔏􁳵􀹋􀤚􀹜􁌱􀫧􀚦􀸎􀕋􀔍?
MySQL 􀞾 MongoDB 􀓷􁘏􁮷􀸎􀘹􁩇􀭏􁃠􁌱􀷄􀴝􀬪􀌶MySQL 􀞾 MongoDB
􀹍􁦜􀥚􀤚􀹜􀫧􀚦􀛱􀳡􀷄􀴝􁌱􁤒􁐏(data representation)􀒅􀺱􁧃􀒅􀙉􁔮􀒅􀔪
􀛓􀒅schema 􁌱􁦡􁦇􀞾􀨧􀔎􀒅􀺽􀙵􀛸(normalization)􀒅􁭛􀬶􀞾􀯔􁚆􀌶
􁭗􁬦􀾲􁫾 MySQL 􀞾 MongoDB􀒅􀨫􁴬􀓤􀱯􀕪􀸎􀣁􀾲􁫾􀙉􁔮􀣳􀞾􁶋􀙉􁔮􀣳
􀷄􀴝􀬪􀒅􀜨􀷄􀴝􀨂􀘙􁕮􀺅􀓧􀝶􀌶
4. 􀖦􀯆􀔍􀾲􁫾 MongoDB􀌵CouchDB 􀝊 CouchBase?
MongoDB 􀞾 CouchDB 􁮷􀸎􁶎􀝻􀷈􀻩􁌱􀷄􀴝􀬪􀌶MongoDB 􀞾 CouchDB
􁮷􀸎􀭏􁃠 NoSQL 􀷄􀴝􀬪􁌱􀹋􀙎􀣳􀕤􁤒􀌶 􁴻􀔧􁮷􀕦􀷈􀻩􀭵􀭗􀨂􀘙􀥘􀨙􀕪􁀌
􀹍􀙌􀕜􁌱􀙈􀝶􁅩􀌶MongoDB 􀞾 CouchDB 􀣁􀷄􀴝􀽜􀣳􀨫􁈿􀌵􀴳􀝗􀌵􀩒􁨝
􀨂􀘙􀕦􀝊􀥔􀚫􀷜􁀩􁒵􀷜􁶎􀹍􀮉􀥚􀓧􀝶􀌶
5. MongoDB 􀱮􀔅􀹋􀦅 NoSQL 􀷄􀴝􀬪􁌱􀜻􀢩􀸎􀕋􀔍?
􀕦􀓥􁇙􁅩􀖵􀮑 MongoDB 􀱮􀔅􀹋􀦅􁌱 NoSQL 􀷄􀴝􀬪:
● 􁶎􀝻􀷈􀕯􁌱
● 􁹛􀯔􁚆
● 􁹛􀝢􁊠􀯔
● 􀸃􀲘􀪀􀯔
● 􀓿􀩄􁌱􀺱􁧃􁧍􁥺
6. 32 􀖖􁔮􁕹􀓤􀹍􀕋􀔍􁕡􀮙􀫧􀚦?
journaling 􀕿􁄶􁁚􁷐􀥘􁌱􀙖􀨂􀸉􀩘􀷈􀕯􀌶􁬯􀩙􁬰􀓞􀾍􀲪􀚫 32 􀖖􁇇􀹜􀓤􁌱􀷄
􀴝􀬪􀥟􀩜􀌶􀢩􀾌􀒅􁈿􀣁 journaling 􀣁 32 􀖖􁔮􁕹􀓤􁼕􁦊􀸎􁐬􁊠􁌱􀌶
7. journal 􀢧􀶱􀣁􀹵􁍓(entry)􀓧􀨠􀷆􀷸(􀾲􀦇􀯴􀫣􀹍􀓞􀓻􀓾􁭔􀶳􁵑􀔧)􀕿􁭬􀚩
􁳯􁷌􀞀?
􀾯􀓻 journal (group)􁌱􀙟􀶙􀖢􁮷􀸎􀓞􁛘􁌱􀒅􁴻􁶋􀨙􀸎􀨠􀷆􁌱􀞈􀚞􀣁􀯩􀥔􁬦
􁑕􀓾􀨙􀓧􀕿􀢧􀶱􀌶
8. 􀚓􀺉􀢏􀣁 MongoDB 􀓾􁌱􀖢􁊠􀸎􀕋􀔍?
MongoDB 􀓾􀛱􀳡􀔧􀓞􀓻􀝢􀕦􀸔􁐏􀷄􀴝􀬪􀓾􀾯􀓻􀶙􀖢􀯔􁚆􁇙􁅩􁌱􀷄􀴝􀬪􀚓
􀺉􀢏􀌶􁭗􁬦􁬯􀓻􀚓􀺉􀢏􀖦􀝢􀕦􀲤􀚩􀾲􁶼􀹗􀱌􁌱􀺱􁧃(􀱲􀙟􀶙􀖢);􀚥􁊠􁬯􀓞􀗞
􀯳􀒅􀾲􀦇􀒅􀝢􀕦􁏟􀨧􀸎􀞈􁵱􁥝􁂲􀛒􁔱􀭚􀌶
9. 􀝷􀨁􁑮􁳵(namespace)􀸎􀕋􀔍?
MongoDB 􀨂􀘙 BSON 􀩒􁨝􀣁􀓲􁵞(collection)􀓾􀌶􀷄􀴝􀬪􀝷􀨁􀞾􀓲􁵞􀝷􀨁
􀕦􀝙􁅩􁬳􁕮􁩸􀹶􀝞􀘉􀝷􀨁􁑮􁳵 (namespace)􀌶
10. 􀦇􀺎􁊠􀲁􁑏􁴻􀩒􁨝􁌱􀪂􀯔􀒅􁧆􀪂􀯔􀸎􀞈􀕗􀨂􀘙􀩶􀓾􀚢􁴻?
􀸎􁌱􀒅􁊠􀲁􁑏􁴻􀪂􀯔􁆐􀝸􀩒􁨝􀕿􁯿􀷛􀗛􀨂(re-save())􀌶
11. 􁚆􀞈􀖵􁊠􀷭􀮪􁇙􀮄􁬰􁤈􀨞􀙂􀥓􀕲?
􀸎􁌱􀌶
12.􊧋􁦜􁑮􊧊 null 􀞀?
􀩒􀔭􀩒􁨝􀱮􀞧􁘒􁥺􀒅􀸎􁌱􀌶􁆐􁘒􁊠􀲁􀓧􁚆􀥜􁂲􀛒􁑮􊧊(null)􀚩􀷄􀴝􀬪􀓲􁵞
(collection)􀢩􀔅􁑮􊧊􀓧􀸎􀩒􁨝􀌶 􁆐􁘒􁊠􀲁􁚆􀥜􁂲􀛒􁑮􀩒􁨝{}􀌶
13. 􀹅􀷛􀶙􀖢􁒈􀚰 fsync 􀚩􁏺􁍏?
􀓧􀕿􀒅􁏺􁍏􀙟􀶙􀖢􁼕􁦊􀸎􀭊􁬴􀲗􁤈􁌱􀌶􀙟􀶙􀖢􀝢􁚆􀣁􀓷􀓣􁑁(􁼕􁦊􀣁 60 􁑁
􀙖)􀝸􀚩􁬡􁏺􁍏􀌶􀖺􀦇􀒅􀦇􀺎􀓞􁑁􀙖􀷄􀴝􀬪􀶭􀚩􀓞􀜉􀓻􀩒􀓞􀓻􀩒􁨝􁭓􀥀􁌱􀶙
􀖢􀒅􀕐􀚬􀷛􁏺􁍏􀓞􀽺􀌶(􁀳􀰺􀒅􀩱􁓕 fsync 􁭌􁶱􀣁􀞸􀕥􁤈􀞾􁕪 􁬦
getLastError_old 􀸎􀹍􀶴􁌱)(􁦲􁘏:􀔞􁦜􀸎􀣗􀕈􁌱􁶎􁦶􁷌??)􀌶
14. 􀦇􀖜􀲗􁤈􀔪􀛓/􀛒􁲁?
MongoDB 􁀌􀹍􀖵􁊠􀖃􁕹􁌱􁲁􀱲􁘏􀥔􀹥􁌱􀬃􀢧􁃻􁌱􀔪􀛓􀒅􀢩􀔅􀨙􁦡􁦇􁌱􀨤
􀷰􀸎􁫷􁰁􀒅􀮳􁭛􀕦􀝊􀝢􁶼􁦇􁌱􁹛􀯔􁚆􀌶􀝢􀕦􀲩􀨙􁔄􀾲􀱮 MySQL MylSAM
􁌱􁛔􀛖􀵉􀔻􀽜􀭗􀌶􁭗􁬦􁔜􁓌􀩒􀔪􀛓􁌱􀶪􀳮􀒅􀯔􁚆􀮑􀚩􀔧􀵉􀜋􀒅􁇙􀚦􀸎􀣁􀓞
􀓻􀝢􁚆􀕿􁑯􁬦􀥚􀓻􀹐􀛓􀢏􁌱􁔮􁕹􁯾􀌶
15. 􀔅􀕋􀔍􀱯􁌱􀷄􀴝􀷈􀕯􀦇􀾌􀬲􀥟?
MongoDB 􀕿􁑌􀺄􁌱􁶼􀚓􁯈􁶼􁊸􁑮􁳵􀹶􁴠􀾊􀷈􀕯􁔮􁕹􁏦􁇆􀌶
16. 􀞐􁊠􀥓􀕲􀶳􁵑􀯩􀥔􁵱􁥝􀥚􀔋?
􀕗􀥓􀕲􀷄􀴝􀬪􀥍􀸁􀔆􀷄􀴝􀬪􀨣􀹢􀚩􁭌􀚊􀓞􀓻􀥓􀕲􀷄􀴝􀬪􀖢􀔅􀷛􁌱􀔆􀷄􀴝􀬪
􀩙􁜰􁩇 10 􀚩 30 􁑁􀷸􁳵􀌶􁬯􀹗􁳵􀣁􀔆􀷄􀴝􀬪􀓤􁌱􀶙􀖢􀩙􀕿􀥦􁨳--􀛱􀳡􀙟􀙁
􀞾􀭩􀓞􁛘􀯔􁧛􀝐(strong consistent read)􀶙􀖢􀌶􁆐􁘒􀒅􀖦􁬮 􁚆􀣁􁒫􀔫􀷄􀴝􀬪
􀓤􀲗􁤈􀹋􁕣􀓞􁛘􀯔􀺱􁧃(eventually consistent query)(􀣁 slaveOk 􀽜􀭗􀓥)􀒅
􀜨􀖵􀣁􁬯􀾧􀷸􁳵􁯾􀌶
17. 􀕋􀔍􀸎 master 􀱲 primary?
􀨙􀸎􀭮􀚹􀥓􀕲􁵞􁗭(replica set)􀓾􁨮􁨱􀥒􁉘􀲅􀹍􀙟􀙁􀶙􀖢􁌱􀔆􁥝􁜓􁅩/􀱮􀞧􀌶
􀣁􀓞􀓻􀥓􀕲􁵞􁗭􀓾􀒅􀭮􀥦􀶴􀥓􀵔(failover)􀔪􀕯􀝎􁊞􀷸􀒅􀓞􀓻􀝚􀥘􁌱􀱮􀞧􀕿
􀝒􀱮 primary􀌶
18. 􀕋􀔍􀸎 secondary 􀱲 slave?
Seconday 􀕗􀭮􀚹􁌱 primary 􀓤􀥔􀚫􁍘􀬫􁌱􀶙􀖢􀌶􀨙􀸎􁭗􁬦􁪙􁪵􀥔􀚫
oplog(local.oplog.rs)􀘉􀚩􁌱􀌶
19. 􀱯􀮠􁶳􁧣􁊠 getLastError 􀹶􁏟􀗛􀙟􀶙􀖢􁊞􀶴􀔧􀔍?
􀓧􁊠􀌶􀓧􁓕􀖦􀹍􁀌􀹍􁧣􁊠 getLastError(􀝈􀝞"Safe Mode")􀹐􀛓􀢏􀘉􁌱􀶙􀖢
􁮷􀓞􀻏􀌶􁧣􁊠 getLastError 􀝝 􀸎􀔅􀔧􁏟􁦊􀙟􀶙􀖢􀱮􀛑􀵉􀔻􀔧􀌶􀭮􁆐􀒅􀖦􁕪
􀬉􀰮􀮑􀚩􁏟􁦊􀒅􀖕􀸎􀙟􀶙􀖢􁌱􀨞􀙂􀯔􀞾􀸎􀞈􁊞􀶴􀓧􀸎􁊧􁬯􀓻􀙬􀨧􁌱􀌶
20. 􀱯􀬫􁧆􀞐􀛖􀓞􀓻􁵞􁗭􀚓􁇆(sharded)􁬮􀸎􀓞􀓻􁶋􁵞􁗭􀚓􁇆􁌱 MongoDB
􁈾􀤹?
􀔅􀭏􀝎􀗎􀴠􁩸􁥠􀒅􀱯􀕪􀭌􁦓􀕦􁶋􁵞􁗭􀚓􁇆(unsharded)􀷜􀭗􀭏􀦤􀓞􀓻
MongoDB 􁈾􀤹􀒅􁴻􁶋􀓞􀝣􀹐􀛓􀢏􀓧􁪃􀕦􀨂􀶱􀖦􁌱􀚡􀦤􀷄􀴝􁵞􀌶􀕗􁶋􁵞􁗭
􀚓􁇆􀜋􁕆􀚩􁵞􁗭􀚓􁇆(sharding)􀸎􀷫􁖲􁌱􀒅􀲅􀕦􀣁􀖦􁌱􀷄􀴝􁵞􁬮􀓧 􀸎􀮉􀥟􁌱􀷸􀗲􁀌􀮠􁥝􁘍􁡤􁵞􁗭􀚓􁇆(sharding)􀌶
21. 􀚓􁇆(sharding)􀞾􀥔􀚫(replication)􀸎􀯆􀻏􀫡􀖢􁌱?
􀾯􀓞􀓻􀚓􁇆(shard)􀸎􀓞􀓻􀚓􀜄􀷄􀴝􁌱􁭦􁬋􁵞􀝳􀌶􀚓􁇆􀝢􁚆􁊧􀜔􀓞􀹐􀛓􀢏􀱲
􁘏􁵞􁗭􁕟􀱮􀒅􀱯􀕪􀴵􁞂􀔅􀾯􀓞􀓻􀚓􁇆(shard)􀖵􁊠􁵞􁗭􀌶
22. 􀷄􀴝􀣁􀕋􀔍􀷸􀗲􀲍􀕿􀲘􀪀􀚩􀥚􀓻􀚓􁇆(shard)􁯾?
MongoDB 􀚓􁇆􀸎􀤚􀔭􀜄􀤒(range)􁌱􀌶􀲅􀕦􀓞􀓻􁵞􀝳(collection)􀓾􁌱􀲅􀹍􁌱
􀩒􁨝􁮷􁤩􀨂􀶱􀚩􀓞􀓻􀣘 (chunk)􀓾􀌶􀝝􀹍􀭮􀨂􀣁􀥚􀖟􀓞􀓻􀣘􁌱􀷸􀗲􀒅􀲍􀕿
􀹍􀥚􀓻􀚓􁇆􁞴􀝐􀷄􀴝􁌱􁭌􁶱􀌶􁈿􀣁􀒅􀾯􀓻􁼕􁦊􀣘􁌱􀥟􀩜 􀸎 64Mb􀒅􀲅􀕦􀖦
􁵱􁥝􁛗􀩝 64 Mb 􁑮􁳵􀲍􀝢􀕦􀨫􀷞􀓞􀓻􁬢􁑏􀌶
23. 􀭮􀱯􁦶􀢶􀹅􀷛􀓞􀓻􀾋􀣁􁤩􁬢􁑏􁌱􀣘(chunk)􀓤􁌱􀷈􀻩􀷸􀕿􀝎􁊞􀕋􀔍?
􀹅􀷛􀶙􀖢􀕿􁒈􀜨􀝎􁊞􀣁􀷯􁌱􀚓􁇆(shard)􀓤􀒅􁆐􀝸􀹅􀶯􀲍􀕿􀣁􀲅􀹍􀹦􁫨􁑏
(ownership transfers)􀚹􀥔􀚫􀚩􀷛􁌱􀚓􁇆􀓤􀌶
24. 􀦇􀺎􀣁􀓞􀓻􀚓􁇆(shard)􀘊􀾊􀱲􁘏􀮉􀱌􁌱􀷸􀗲􀒅􀱯􀝎􁩸􀓞􀓻􀺱􁧃􀕿􀯆
􀻏?
􀦇􀺎􀓞􀓻􀚓􁇆(shard)􀘊􀾊􀔧􀒅􁴻􁶋􀺱􁧃􁦡􁗝􀔧“Partial”􁭌􁶱􀒅􀞈􀚞􀺱􁧃􀕿􁬬
􀢧􀓞􀓻􁲙􁧏􀌶􀦇􀺎􀓞􀓻􀚓􁇆(shard)􀟥􀬫􀮉􀱌􀒅MongoDB 􀚞􀕿􁒵􀮇􀨙􁌱􀟥
􀬫􀌶
25. 􀱯􀝢􀕦􀲩 moveChunk 􁍓􀭯􁯾􁌱􀷯􀷈􀕯􀚢􁴻􀞀?
􁀌􁳯􁷌􀒅􁬯􀔶􀷈􀕯􀸎􀣁􀚓􁇆(shard)􁬰􁤈􀣐􁤍􀶙􀖢(balancing)􁌱􀷸􀗲􀔾􁊞􁌱
􀔁􀷸􀷈􀕯􀌶􀓞􀷮􁬯􀔶􀶙􀖢􀫪􁕪 􀨠􀱮􀒅􁍘􀙉􁌱􀔁􀷸􀷈􀕯􀔞􀬫􁧆􁤩􀚢􁴻􀴧􀌶􀖕
􁍓􀚹􁂴􁉘􀫡􀖢􀸎􁵱􁥝􀲋􀛖􁌱􀒅􀲅􀕦􁧗􀩜􀮞􀣈􁘍􁡤􀙚􁯽􀶱􁬯􀔶􀷈􀕯􁌱􁑮􁳵􀌶
26. 􀱯􀯆􀔍􀺱􁍡 Mongo 􀾋􀣁􀖵􁊠􁌱􁱾􀴳?
db._adminCommand("connPoolStats");
27. 􀦇􀺎􀣘􁑏􀛖􀶙􀖢(moveChunk)􀥦􁨳􀔧􀒅􀱯􁵱􁥝􀲋􀛖􁂴􁴻􁮱􀚓􁫨􁑏􁌱􀷈
􀻩􀞀?
􀓧􁵱􁥝􀒅􁑏􀛖􀶙􀖢􀸎􀓞􁛘(consistent)􀬚􀓬􀸎􁏟􀨧􀯔􁌱(deterministic);􀓞􀽺􀥦
􁨳􀝸􀒅􁑏􀛖􀶙􀖢􀕿􀓧􀷙􁯿􁦶; 􀭮􀨠􀱮􀝸􀒅􀷄􀴝􀝝􀕿􀚊􁈿􀣁􀷛􁌱􀚓􁇆􁯾
(shard)􀌶
28. 􀦇􀺎􀱯􀣁􀖵􁊠􀥔􀚫􀲦􀹞(replication)􀒅􀝢􀕦􀓞􁮱􀚓􀖵􁊠􀷭􀮪
(journaling)􁘒􀙌􀕜􁮱􀚓􀚞􀓧􀖵􁊠􀞀?
􀝢􀕦􀌶
29.􀭮􀹅􀷛􀓞􀓻􀾋􀣁􁤩􁬢􁑏􁌱􀣘(Chunk)􀓤􁌱􀷈􀻩􀷸􀕿􀝎􁊞􀕋􀔍?
􀹅􀷛􀶙􀖢􀕿􁒈􀜨􀝎􁊞􀣁􀷯􁌱􀣘(Chunk)􀓤􀒅􁆐􀝸􀹅􀶯􀲍􀕿􀣁􀲅􀹍􀹦􁫨􁑏􀚹􀥔
􀚫􀚩􀷛􁌱􀚓􁇆􀓤􀌶
30.MongoDB 􀣁 A:{B,C}􀓤􀭌􁒈􁔱􀭚􀒅􀺱􁧃 A:{B,C}􀞾 A:{C,B}􁮷􀕿􀖵􁊠􁔱
􀭚􀞀?
􀓧􀕿􀒅􀝝􀕿􀣁 A:{B,C}􀓤􀖵􁊠􁔱􀭚􀌶
31.􀦇􀺎􀓞􀓻􀚓􁇆(Shard)􀘊􀾊􀱲􀮉􀱌􁌱􀷸􀗲􀒅􀝎􁩸􀓞􀓻􀺱􁧃􀕿􀯆􀻏?
􀦇􀺎􀓞􀓻􀚓􁇆􀘊􀾊􀔧􀒅􁴻􁶋􀺱􁧃􁦡􁗝􀔧“Partial”􁭌􁶱􀒅􀞈􀚞􀺱􁧃􀕿􁬬􀢧􀓞
􀓻􁲙􁧏􀌶􀦇􀺎􀓞􀓻􀚓􁇆􀟥􀬫􀮉􀱌􀒅MongoDB 􀕿􁒵􀮇􀨙􁌱􀟥􀬫􀌶
32. MongoDB 􀶪􀳮􀨂􀘙􁬦􁑕􀞀?􀦇􀺎􀶪􀳮􁌱􁦾􀒅􀯆􀔍􁊠?
MongoDB 􀶪􀳮􀨂􀘙􁬦􁑕􀒅􀨙􀸎 javascript 􀙟􁌱􀒅􀗛􀨂􀣁 db.system.js 􁤒
􀓾􀌶
33.􀦇􀖜􁉘􁥴 MongoDB 􀓾􁌱 GridFS 􀹢􀚫􀒅MongoDB 􀔅􀖜􀖵􁊠 GridFS
􀹶􀨂􀘙􀷈􀕯?
GridFS 􀸎􀓞􁐿􀩙􀥟􀣳􀷈􀕯􀨂􀘙􀣁 MongoDB 􀓾􁌱􀷈􀕯􁥢􁝜􀌶􀖵􁊠 GridFS
􀝢􀕦􀩙􀥟􀷈􀕯􀚓􁵍􀱮􀥚􀓻􀩜􀷈􀻩􀨂􀶱􀒅􁬯􀻏􀱯􀕪􁚆􀥜􀹍􀶴􁌱􀗛􀨂􀥟􀷈􀻩􀒅
􁘒􀓬􁥴􀙬􀔧 BSON 􀩒􁨝􀹍􁴴􀚫􁌱􁳯􁷌􀌶
5.3.3 memcached􁶎􁦶􀓫􁷌
1􀌵memcached􀸎􀯆􀔍􀫡􀖢􁌱?
Memcached􁌱􁐟􀥰􀹶􁛔􀓷􁴤􀾧􀟢􀫶(two-stagehash)􀌶Memcached􀩪􀘟􀓞
􀓻􀫤􀥟􁌱􀌵􀨂􀘙􀔧􀮉􀥚 <key,value> 􀩒􁌱􀟢􀫶􁤒􀌶􁭗􁬦key􀒅􀝢􀕦􀨂􀘙􀱲
􀺱􁧃􀕱􀰺􁌱􀷄􀴝􀌶
􀨮􀲁􁒒􀝢􀕦􀲩􀷄􀴝􀨂􀘙􀣁􀥚􀝣 memcached 􀓤􀌶􀭮􀺱􁧃􀷄􀴝􀷸􀒅􀨮􀲁􁒒􁸒
􀘶􀝇􁘍􁜓􁅩􀚜􁤒􁦇􁓒􀚊 key 􁌱􀟢􀫶􊧊(􁴤􀾧􀓞􀟢􀫶)􀒅􁬰􁘒􁭌􀓾􀓞􀓻􁜓􁅩;􀨮
􀲁􁒒􀩙􁧗􀿢􀝎􁭆􁕳􁭌􀓾􁌱􁜓􁅩􀒅􁆐􀝸 memcached 􁜓􁅩􁭗􁬦􀓞􀓻􀙖􁮱􁌱􀟢
􀫶􁓒􁀩(􁴤􀾧􀔫􀟢􀫶)􀒅􀺱􀲤􁍥􀾋􁌱􀷄􀴝(item)􀌶
􀔈􀓻􀚜􀧼􀒅􀘃􁦡􀹍3 􀓻􀨮􀹐􁒒 1 2 3 􀝣 memcached A,B,C
Client 1 􀰮􀲩􀷄􀴝”barbaz”􀕦key “foo”􀨂􀘙􀌶Client 1 􁸒􀘶􀝇􁘍􁜓􁅩􀚜􁤒
􀒁A􀒅B􀒅C􀒂􁦇􁓒 key “foo”􁌱􀟢􀫶􊧊􀒅􀘃􁦡 memcached B 􁤩􁭌􀓾􀌶􀴳
􁍳􀒅Client 1 􁍗􀴳 connect 􀚩memcached B 􁭗􁬦 key “foo”􀲩􀷄
􀴝”barbaz”􀨂􀘙􁬰􀝄􀌶 Client 2 􀖵􁊠􀓨 Client 1 􁍘􀝶􁌱􀨮􀲁􁒒􀬪(􀰺􀞱􁍳􁴤
􀾧􀓞􁌱􀟢􀫶􁓒􁀩􁍘􀝶)􀒅􀔞􀳜􀹍􀝶􀻏􁌱 memcached 􀚜􁤒(A􀒅B􀒅C􀒂􀌶
􀔭􀸎􀒅􁕪􁬦􁍘􀝶􁌱􀟢􀫶􁦇􁓒(􁴤􀾧􀓞)􀒅Client 2 􁦇􁓒􀚊 key “foo”􀣁
memcached B 􀓤􀒅􁆐􀝸􀨙􁍗􀴳􁧗􀿢 memcached B􀒅􀮑􀚩􀷄􀴝”barbaz”􀌶
􀝱􁐿􀨮􀲁􁒒􀣁 memcached 􀓾􀷄􀴝􁌱􀨂􀘙􀭵􀭗􀸎􀓧􀝶􁌱(perl Storable php
serialize,java hibernate,JSON􁒵􀒂􀌶􀓞􀔶􀨮􀲁􁒒􀨫􁈿􁌱􀟢􀫶􁓒􁀩􀔞􀓧􀓞
􀻏􀌶􀖕􀸎􀒅memcached 􀹐􀛓􀢏􁒒􁌱􁤈􀔅􀯛􀸎􀓞􁛘􁌱􀌶
􀹋􀝸􀒅􀕗􀨫􁈿􁌱􁥯􀬶􁍡􀒅memcached 􀸎􀓞􀓻􁶋􁴥􀤲􁌱􀌵􀤚􀔭􀔪􀕯􁌱􀹐􀛓
􀢏􁑕􀬧􀌶􁬯􁐿􀺝􀺅􀝢􀕦􀮉􀦅􀣈􁥴􀙬 C10K problem􀒅􀬚􀙍􀹍􀺄􀖯􁌱􀝢􀲘􀪀
􀯔􀌶
􀝢􀕦􀝇􁘍 A Story of Caching 􀒅􁬯􁓤􀷈􁒍􁓌􀜔􁥴􁯽􀔧􀨮􀲁􁒒􀓨 memcached
􀸎􀦇􀖜􀔻􀔰􁌱􀌶
2􀌵memcached 􀹋􀥟􁌱􀕽􀛠􀸎􀕋􀔍?
􁧗􀕚􁕡􁴅􁧛􀓤􁶎􁌱􁳯􁷌(􀜨 memcached 􀸎􀦇􀖜􀫡􀖢􁌱)􀌶Memcached 􀹋􀥟􁌱􀦅􀥒􀩪􀸎􀨙􀬃􀹶􀔧􀺄􀖯􁌱􀿜􀬘􀝢􀲘􀪀􀯔􀒅􁇙􀚦􀸎􀣁􀓞􀓻􀫤􀥟􁌱􁔮􁕹􀓾􀌶
􁊧􀔭􀨮􀲁􁒒􁛔􀫩􀘉􀔧􀓞􀽺􀟢􀫶􀒅􁮎􀔍􀱯􀕪􀮉􀨻􀸃􀥀􀛒􀥟􁰁 memcached 􀚩
􁵞􁗭􀓾􀌶memcached 􀔏􁳵􁀌􀹍􁍘􀔰􁭗􀗞􀒅􀢩􀾌􀓧􀕿􀥀􀛒 memcached 􁌱
􁨮􁫹;􁀌􀹍􀥚􀶎􀜐􁦓􀒅􀓧􀕿􁗑􁕶􁭗􀗞􁰁􁆷􁅨(implode)􀌶memcached 􁌱􁵞􁗭
􀮉􀦅􁊠􀌶􀙖􀨂􀓧􀥜􀔧?􀥀􀛒􀙾􀝣 memcached 􀞉;CPU 􀓧􀥜􁊠􀔧?􀙚􀥀􀛒􀙾
􀝣􀞉􀒔􀹍􀥚􀖟􁌱􀙖􀨂?􀣁􀥀􀛒􀙾􀝣􀞉􀒅􀓧􁥝􁁵􁩇􀔧􀌶
􀤚􀔭 memcached 􁌱􀤚􀹜􀜻􀚞􀒅􀝢􀕦􁍘􀭮􁫷􀺂􀣈􀺅􀭌􀚊􀓧􀝶􁔄􀣳􁌱􁖨􀨂􀺝
􀺅􀌶􁴻􀔧􁬯􁓤 FAQ􀒅􀣁􀙌􀕜􀣈􀷜􀮉􀨻􀸃􀲤􀚩􁧇􁕡􁩒􀷏􁌱􀌶
3􀌵memcached 􀞾 MySQL 􁌱query cache 􁍘􀾲􀹍􀕋􀔍􀕽􁗌􁅩?
􀲩 memcached 􀭚􀙁􀬫􁊠􀓾􀒅􁬮􀸎􁵱􁥝􀓧􀩝􀫡􀖢􁰁􁌱􀌶MySQL 􀹍􀓻􀖵􁊠
􀷜􀗎􁌱 query cache􀒅􀝢􀕦􁛔􀛖􀣈􁖨􀨂 SQL 􀺱􁧃􁌱􁕮􀺎􀒅􁤩􁖨􀨂􁌱 SQL
􀺱􁧃􀝢􀕦􁤩􀝍􀥔􀣈􀮳􁭛􀲗􁤈􀌶Memcached 􀓨􀔏􁍘􀾲􀒅􀯆􀔍􀻏􀞫? MySQL
􁌱 query cache 􀸎􁵞􀓾􀭗􁌱􀒅􁬳􀴳􀚩􁧆 query cache 􁌱 MySQL 􀹐􀛓􀢏􁮷
􀕿􀝑􁍅􀌶
● 􀭮􀰍􀗥􀶯􁤒􀷸􀒅MySQL 􁌱query cache 􀕿􁒈􀚰􁤩􀚬􀷛(flush)􀌶􀨂􀘙􀓞􀓻
memcached item 􀝝􁵱􁥝􀮉􀩝􁌱􀷸􁳵􀒅􀖕􀸎􀭮􀙟􀶙􀖢􀮉􁷇􁔺􀷸􀒅MySQL 􁌱
query cache 􀕿􁕪􀬉􁦏􀲅􀹍􁖨􀨂􀷄􀴝􁮷􀥦􀶴􀌶
● 􀣁􀥚􀻐 CPU 􀓤 MySQL 􁌱 query cache 􀕿􁭬􀚩􀲘􀪀􁳯􁷌(scalability
issues)􀌶􀣁􀥚􀻐 CPU 􀓤 query cache 􀕿􀥀􀛒􀓞􀓻􀙂􀩴􁲁(global lock)􀌵􁊧
􀔭􁵱􁥝􀚬􀷛􀹅􀥚􁌱􁖨􀨂􀷄􀴝􀒅􁭛􀬶􀕿􀝒􀮑􀹅􀱌􀌶
● 􀣁 MySQL 􁌱 query cache 􀓾􀒅􀱯􀕪􀸎􀓧􁚆􀨂􀘙􀕱􀰺􁌱􀷄􀴝􁌱(􀝝􁚆􀸎
SQL 􀺱􁧃􁕮􀺎)􀌶􁘒􀚥􁊠 memcached􀒅􀱯􀕪􀝢􀕦􀵫􀭌􀚊􀝱􁐿􁹛􀶴􁌱􁖨􀨂􀌶
􀾲􀦇􀒅􀝢􀕦􀲗􁤈􀥚􀓻􁇿􁒈􁌱􀺱􁧃􀒅􀺅􀭌􀚊􀓞􀓻􁊠􀲁􀩒􁨝(user object)􀒅􁆐􀝸
􀩙􁊠􀲁􀩒􁨝􁖨􀨂􀚩 memcached 􀓾􀒅􁘒 query cache 􀸎 SQL 􁧍􀝙􁕆􀚦􁌱􀒅
􀓧􀝢􁚆􀘉􀚩􁬯􀓞􁅩􀌶􀣁􀩜􁌱􁗑􁒊􀓾􀒅query cache 􀕿􀹍􀲅􀬆􀛗􀒅􀖕􁵋􁍳􁗑
􁒊􁥢􀽜􁌱􀥀􀛒􀒅query cache 􁌱􀭕􀩙􀥟􀔭􀚥􀌶
● query cache 􁚆􀥜􀚥􁊠􁌱􀙖􀨂􀨻􁰁􀝑􀚩 MySQL 􀹐􀛓􀢏􁑮􁳳􀙖􀨂􁑮􁳵􁌱􁴴
􀚫􀌶􁕳􀷄􀴝􀬪􀹐􀛓􀢏􀥀􀛒􀹅􀥚􁌱􀙖􀨂􀹶􁖨􀨂􀷄􀴝􀒅􀢴􁆐􀸎􀮉􀦅􁌱􀌶􀖕􀸎􀒅
􀹍􀔧 memcached􀒅􀝝􁥝􀰍􀹍􁑮􁳳􁌱􀙖􀨂􀒅􁮷􀝢􀕦􁊠􀹶􀥀􀛒 memcached
􁵞􁗭􁌱􁥢􀽜􀒅􁆐􀝸􀰍􀩪􀝢􀕦􁖨􀨂􀹅􀥚􁌱􀷄􀴝􀌶
4􀌵memcached 􀞾􀹐􀛓􀢏􁌱 local cache (􀾲􀦇 PHP 􁌱 APC􀌵mmap 􀷈
􀕯􁒵􀒂􁍘􀾲􀒅􀹍􀕋􀔍􀕽􁗌􁅩􀒘
􁸒􀘶􀒅local cache 􀹍􁦜􀥚􀓨􀓤􁶎(query cache)􁍘􀝶􁌱􁳯􁷌􀌶local cache 􁚆
􀥜􀚥􁊠􁌱􀙖􀨂􀨻􁰁􀝑􀚩(􀜔􀝣)􀹐􀛓􀢏􁑮􁳳􀙖􀨂􁑮􁳵􁌱􁴴􀚫􀌶􀓧􁬦􀒅local
cache 􀹍􀓞􁅩􀾲 memcached 􀞾 query cache 􁮷􁥝􀦅􀒅􁮎􀩪􀸎􀨙􀓧􀖕􀝢􀕦
􀨂􀘙􀕱􀰺􁌱􀷄􀴝􀒅􁘒􀓬􁀌􀹍􁗑􁕶􀨂􀝐􁌱􀭊􁬴􀌶
● local cache 􁌱􀷄􀴝􀺱􁧃􀹅􀮳􀌶􁘍􁡤􀲩 highly common 􁌱􀷄􀴝􀶱􀣁 local
cache 􀓾􀞉􀌶􀦇􀺎􀾯􀓻􁶭􁶎􁮷􁵱􁥝􀛒􁫹􀓞􀔶􀷄􁰁􁫾􀩝􁌱􀷄􀴝􀒅􁘍􁡤􀲩􀨙􀕪
􀶱􀣁 local cache 􀞉􀌶
● local cache 􁗌􀩝􁵞􀖛􀥦􀶴(group invalidation)􁌱􁇙􀯔􀒅􀣁 memcached 􁵞
􁗭􀓾􀒅􀚢􁴻􀱲􀹅􀷛􀓞􀓻key 􀕿􁦏􀲅􀹍􁌱􁥡􀩊􁘏􁥧􀩊􀚩􀌶􀖕􀸎􀣁 local cache
􀓾􀱯􀕪􀝝􁚆􁭗􁎣􀲅􀹍􁌱􀹐􀛓􀢏􀚬􀷛 cache(􀮉􀱌􀒅􀓧􀙍􀲘􀪀􀯔)􀒅􀱲􁘏􀕐􀕐􀗁
􁩢􁖨􀨂􁩻􀷸􀥦􀶴􀹢􀚫􀌶
● local cache 􁶎􀔁􁍳􀓸􁯿􁌱􀙖􀨂􁴴􀚫􀒅􁬯􀓞􁅩􀓤􁶎􀫪􁕪􀵉􀚩􀌶
5􀌵memcached 􁌱 cache 􀹢􀚫􀸎􀯆􀻏􁌱?
Memcached 􀔆􁥝􁌱 cache 􀹢􀚫􀸎 LRU 􀹋􁬪􀹋􀩝􁊠)􁓒􁀩+􁩻􀷸􀥦􀶴􀌶􀭮􀰍
􀨂􀷄􀴝􀚩 memcached 􀓾􀒅􀝢􀕦􀳰􀨧􁧆􀷄􀴝􀣁􁖨􀨂􀓾􀝢􀕦􀞜􀥚􀔋 Which is
forever,or some time in the future􀌶􀦇􀺎 memcached 􁌱􀙖􀨂􀓧􀥜􁊠􀔧􀒅􁬦
􀹗􁌱 slabs 􀕿􀕽􀘶􁤩􀹊􀴘􀒅􀴳􁍳􀩪􁫪􀚩􀹋􁘌􁌱􀹚􁤩􀖵􁊠􁌱 slabs
6􀌵memcached 􀦇􀖜􀨫􁈿􀙞􀖟􀹢􀚫?
􀓧􀨫􁈿!􀱯􀕪􀩒􁬯􀓻􁳯􁷌􀰽􀚩􀮉􀰚􁦚􀌶Memcached 􀬫􁧆􀸎􀬫􁊠􁌱􁖨􀨂􀩶􀌶
􀨙􁌱􁦡􁦇􀹜􁫝􀩪􀓧􀬃􀹍􀕱􀖜􀙞􀖟􀹢􀚫􀌶􀦇􀺎􀓞􀓻 Memcached 􁜓􁅩􀥦􀝄􀔧
􀲅􀹍􀷄􀴝􀒅􀰍􀬫􁧆􀝢􀕦􀕗􀷄􀴝􁃠(􀾲􀦇􀷄􀴝􀬪)􀙚􀽺􁞴􀝐􀚩􀷄􀴝􀌶􀰍􀬫􁧆􁇙
􀚦􁀳􀰺􀒅􀰍􁌱􀬫􁊠􀬫􁧆􀝢􀕦􀨻􀮤􁜓􁅩􁌱􀥦􀶴􀌶􀓧􁥝􀙟􀓞􀔶􁔩􁔤􁌱􀺱􁧃􀕤
􁎱􀒅􀩀􀫶􀹕􀔭 memcached 􀹶􀗛􁦤􀓞􀚔!􀦇􀺎􀰍􀳅􀮞􁜓􁅩􀥦􀶴􀕿􀥟􀥟􀛒􁯿􀷄
􀴝􀬪􁌱􁨮􀳅􀒅􁮎􀔍􀰍􀝢􀕦􁯻􀝐􀓞􀔶􀛐􁀩􀌶􀾲􀦇􀰍􀝢􀕦􀥀􀛒􀹅􀥚􁌱􁜓􁅩(􀹶􀙺
􀩝􀓶􀥦􀓞􀓻􁜓􁅩􁌱􀭽􀟥)􀒅􁅾􀥓􁜓􁅩(􀣁􀙌􀕜􁜓􁅩 down 􀔧􁌱􀷸􀗲􀴳􁓕 IP􀒂
􁒵􁒵􀌶
7􀌵memcached 􀦇􀖜􀥒􁉘􀨻􁲙􁌱?
􀓧􀥒􁉘!􀣁 memcached 􁜓􁅩􀥦􀶴􁌱􀰘􀙭􀓥􀒅􁵞􁗭􁀌􀹍􀮠􁥝􀘉􀕱􀖜􀨻􁲙􀥒
􁉘􀌶􀦇􀺎􀝎􁊞􀔧􁜓􁅩􀥦􀶴􀒅􀬫􀩒􁌱􀴷􀷞􀨠􀙂􀝐􀙬􀔭􁊠􀲁􀌶􁜓􁅩􀥦􀶴􀷸􀒅􀓥
􁶎􀚜􀚊􀙾􁐿􀷜􀻜􀗀􀰍􁭌􀳠􀒓
● 􀮺􁊼􀨙􀑺􀥦􀶴􁜓􁅩􁤩􀯩􀥔􀱲􀹊􀴘􀔏􀚹􀒅􁬮􀹍􀮉􀥚􀙌􀕜􁜓􁅩􀝢􀕦􀬫􀩒􁜓􁅩
􀥦􀶴􀬃􀹶􁌱􀭽􀟥􀌶
● 􀲩􀥦􀶴􁌱􁜓􁅩􀕗􁜓􁅩􀚜􁤒􀓾􁑏􁴻􀌶􀘉􁬯􀓻􀶙􀖢􀜉􀓡􁥝􀩜􀮞􀑺􀣁􁼕􁦊􀰘􀙭
􀓥􀒁􀖟􀷄􀭗􀟢􀫶􁓒􁀩􀒂􀒅􀨮􀲁􁒒􁂲􀛒􀱲􁑏􁴻􁜓􁅩􀒅􀕿􀩕􁛘􀲅􀹍􁌱􁖨􀨂􀷄􀴝
􀓧􀝢􁊠􀑺􀢩􀔅􀟢􀫶􀝇􁆙􁌱􁜓􁅩􀚜􁤒􀝒􀛸􀔧􀒅􀥟􁮱􀚓 key 􀕿􀢩􀔅􀟢􀫶􊧊􁌱􀶯
􀝒􁘒􁤩􀸉􀩘􀚩(􀓨􀜻􀹶)􀓧􀝶􁌱􁜓􁅩􀓤􀌶
● 􀞐􀛖􁅾􀥓􁜓􁅩􀒅􀴳􁓕􀥦􀶴􁜓􁅩􀲅􀜛􁊠􁌱 IP􀒅􁬯􀻏􀝢􀕦􁴠􀾊􀟢􀫶􁔯􀔤
(hashing chaos)􀌶
● 􀦇􀺎􀫶􀹕􁂲􀛒􀞾􁑏􁴻􁜓􁅩􀒅􁘒􀓧􀭽􀟥􀜻􀘶􁌱􀟢􀫶􁕮􀺎􀒅􀝢􀕦􀖵􁊠􀓞􁛘􀯔
􀟢􀫶􁓒􁀩􀒁consistent hashing)􀌶􀰍􀝢􀕦􁌯􀬶􀓞􀓥􀓞􁛘􀯔􀟢􀫶􁓒􁀩􀌶􀶪􀳮􀓞
􁛘􀯔􀟢􀫶􁌱􀨮􀲁􁒒􀫪􁕪􀮉􀱮􁆧􀒅􁘒􀓬􁤩􀬠􁀬􀖵􁊠􀌶􀝄􀩤􁦶􀓞􀓥􀞉!
● 􀓷􀽺􀟢􀫶(reshing)􀌶􀭮􀨮􀲁􁒒􀨂􀝐􀷄􀴝􀷸􀒅􀦇􀺎􀝎􁈿􀓞􀓻􁜓􁅩􀒁down􀒂
􀔧􀒅􀩪􀙚􀘉􀓞􀽺􀟢􀫶(􀟢􀫶􁓒􁀩􀓨􀚹􀓞􀽺􀓧􀝶)􀒅􁯿􀷛􁭌􀳠􀝚􀓞􀓻􁜓􁅩(􁵱􁥝
􁀳􀰺􁌱􀷸􀒅􀨮􀲁􁒒􀬚􁀌􀹍􀲩 down 􁌱􁜓􁅩􀕗􁜓􁅩􀚜􁤒􀓾􁑏􁴻􀒅􀓥􀽺􁬮􀸎􀹍
􀝢􁚆􀘶􀟢􀫶􀚩􀨙)􀌶􀦇􀺎􀺤􀓻􁜓􁅩􀷸􀦅􀷸􀣕􀒅􀓷􀽺􀟢􀫶􁌱􀷜􁀩􀩪􀹍􁷚􁴾􀔧􀒅
􀦅􁌱􁜓􁅩􀞾􀣕􁌱􁜓􁅩􀓤􁮷􀝢􁚆􀨂􀣁􁚍􀷄􀴝(stale data)􀌶
8􀌵􀦇􀖜􀩙 memcached 􀓾 item 􀲢􁰁􀩕􀙁􀩕􀚊?
􀰍􀓧􀬫􁧆􁬯􀻏􀘉!Memcached 􀸎􀓞􀓻􁶋􁴥􀤲􁌱􀹐􀛓􀢏􀌶􀕱􀖜􀝢􁚆􀩕􁛘
memcached 􀸮􀘊􀱲􁎖􀷸􀳏􁕷􀹐􀛓􁌱􀶙􀖢􁮷􀬫􁧆􊧊􀮑􁂮􀯏􁆧􁡤􀌶􀝻
memcached 􀓾􀲢􁰁􀩕􀙁􀷄􀴝􀮃􀮃􀓧􀸎􀰍􁍥􀾋􀰮􁥝􁌱!􀰮􁨝􁍡􀒅􀦇􀺎􁖨􀨂􀷄
􀴝􀣁􀩕􀚊􀩕􀙁􀔏􁳵􀝎􁊞􀔧􀝒􀛸􀒅􀰍􀩪􁵱􁥝􀥒􁉘􁚍􀷄􀴝􀔧;􀦇􀺎􁖨􀨂􀷄􀴝􀣁􀩕
􀚊􀩕􀙁􀔏􁳵􁬦􀹗􀔧􀒅􀰍􀝈􀯆􀔍􀥒􁉘􁬯􀔶􀷄􀴝􀞫?
􀢩􀾌􀒅􀲢􁰁􀩕􀚊􀩕􀙁􀷄􀴝􀬚􀓧􀘟􀰍􀰮􁨝􀓾􁌱􁮎􀔍􀹍􁊠􀌶􀓧􁬦􀣁􀓞􀓻􀣋􀸧􀗯
􀸎􀮉􀹍􁊠􀌶􀦇􀺎􀰍􀹍􀥟􁰁􁌱􀕗􀓧􀝒􀛸􁌱􀷄􀴝􀒅􀬚􀓬􀫶􀹕􁖨􀨂􀮉􀮳􁅾(warm)
􁩸􀹶􀒅􀲢􁰁􀩕􀙁􁖨􀨂􀷄􀴝􀸎􀮉􀹍􀬆􀛗􁌱􀌶􁡱􁆐􁬯􀓻􀣋􀸧􀬚􀓧􀙎􀣳􀒅􀖕􀜩􁕪
􀬉􀝎􁊞􀒅􀢩􀾌􀱯􀕪􀕿􁘍􁡤􀣁􀩙􀹶􀨫􁈿􀲢􁰁􀩕􀚊􀩕􀙁􁌱􀛑􁚆􀌶
Steven Grimm􀒅􀓞􀦇􀷬􀮃􀣈􀒅􀣁􁮒􀕯􀚜􁤒􀓾􁕳􀚊􀔧􀝚􀓞􀓻􀮉􀦅􁌱􀖺
􀧼: http://lists.danga.com/pipermail/memcached/2007-
July/004802.html 􀌶
9􀌵􀱯􁵱􁥝􀲩 memcached 􀓾􁌱 item 􀲢􁰁􀩕􀚊􀩕􀙁􀒅􀯆􀔍􀛐?
􀦅􀞉􀦅􀞉􀌶􀦇􀺎􀰍􁵱􁥝􀲢􁰁􀩕􀚊􀩕􀙁􀒅􀹋􀝢􁚆􁌱􀜻􀢩􀓞􁛱􀸎􁯿􀷛􁊞􀱮􁖨􀨂
􀷄􀴝􁵱􁥝􁁾􁘙􀮉􁳩􁌱􀷸􁳵􀒅􀱲􁘏􀷄􀴝􀬪􀣕􀔧􁦏􀰍􁷷􀝑􁋳􁝒􀌶
􀦇􀺎􀓞􀓻 memcached 􁜓􁅩 down 􀔧􁦏􀰍􀮉􁋳􁝒􀒅􁮎􀔍􀰍􁬮􀕿􁵅􀙁􀙌􀕜􀮉
􀥚􁼋􁅸􀌶􀰍􁌱􁔮􁕹􀥡􁚈􀭧􀔧􀌶􀰍􁵱􁥝􀘉􀓞􀔶􀕽􀛸􀫡􀖢􀌶􀾲􀦇􀥒􁉘“􀰚􁗭”􁳯
􁷌(􀾲􀦇 memcached 􁜓􁅩􁮷􀥦􀶴􀔧􀒅􀝍􀥔􁌱􀺱􁧃􁦏􀰍􁌱􀷄􀴝􀬪􀓧􀤩􁯿􁨮...
􁬯􀓻􁳯􁷌􀣁 FAQ 􁌱􀙌􀕜􀵉􀚩􁬦)􀒅􀱲􁘏􀕽􀛸􀓧􀦅􁌱􀺱􁧃􀌶􁦕􀖘􀒅
Memcached 􀬚􀓧􀸎􀰍􁭈􁭿􀕽􀛸􀺱􁧃􁌱􀗵􀝗􀌶
􀦇􀺎􀰍􁌱􁼋􁅸􀕐􀕐􀸎􁯿􀷛􁊞􀱮􁖨􀨂􀷄􀴝􁵱􁥝􁁾􁘙􀮉􁳩􀷸􁳵(15 􁑁􀚩􁩻􁬦 5
􀚓􁰦)􀒅􀰍􀝢􀕦􁘍􁡤􁯿􀷛􀖵􁊠􀷄􀴝􀬪􀌶􁬯􁯾􁕳􀚊􀓞􀔶􀵉􁐏:
● 􀖵􁊠 MogileFS (􀱲􁘏 CouchDB 􁒵􁔄􀖒􁌱􁫫􀕯)􀣁􀨂􀘙 item􀌶􀲩 item 􁦇􁓒
􀚊􀹶􀬚 dump 􁏺􁍏􀓤􀌶MogileFS 􀝢􀕦􀮉􀷜􀗎􀣈􁥟􀙟 item􀒅􀬚􀵉􀗀􀮳􁭛􀣈
􁦢􁳯􀌶􀰍􁊜􁛗􀝢􀕦􀲩 MogileFS 􀓾􁌱 item 􁖨􀨂􀣁 memcached 􀓾􀒅􁬯􀻏􀝢
􀕦􀛒􀮳􁧛􀝐􁭛􀬶􀌶MogileFS+Memcached 􁌱􁕟􀝳􀝢􀕦􀛒􀮳􁖨􀨂􀓧􀞸􀓾􀷸􁌱
􀟥􀬫􁭛􀬶􀒅􀵉􁹛􁗑􁒊􁌱􀝢􁊠􀯔􀌶
● 􁯿􀷛􀖵􁊠 MySQL􀌶MySQL 􁌱 InnoDB 􀔆􁲫􀺱􁧃􁌱􁭛􀬶􁶋􀬉􀮳􀌶􀦇􀺎􀥟􁮱􀚓􁖨􀨂􀷄􀴝􁮷􀝢􀕦􀶱􀚩 VARCHAR 􀨁􀾧􀓾􀒅􁮎􀔍􀔆􁲫􀺱􁧃􁌱􀯔􁚆􀩙􀹅
􀦅􀌶􀕗 memcached 􀓾􀳲 key 􀺱􁧃􀙾􀔒􁒵􀕰􀔭 MySQL 􁌱􀔆􁲫􀺱􁧃:􀩙 key
􀟢􀫶􀚩 64-bit 􁌱􀷆􀷄􀒅􁆐􀝸􀩙􀷄􀴝􀨂􀘙􀚩 MySQL 􀓾􀌶􀰍􀝢􀕦􀲩􀜻􀦤(􀓧􀘉
􀟢􀫶)􁌱 key 􀨂􀘙􁮷􀸦􁭗􁌱􀨁􀾧􀓾􀒅􁆐􀝸􀭌􁒈􀔫􁕆􁔱􀭚􀹶􀛒􀮳􀺱􁧃...key 􁤩
􀛖􀣈􀥦􀶴􀒅􀲢􁰁􀚢􁴻􀥦􀶴􁌱 key􀒅􁒵􁒵􀌶
● 􀓤􁶎􁌱􀷜􁀩􁮷􀝢􀕦􀭚􀙁 memcached􀒅􀣁􁯿􀞐 memcached 􁌱􀷸􀗲􀕖􁆐
􀵉􀗀􀮉􀦅􁌱􀯔􁚆􀌶􁊧􀔭􀰍􀓧􁵱􁥝􀭮􀮞”hot”􁌱 item 􁤩 memcached LRU 􁓒
􁀩􁑱􁆐􁂣􀿶􀒅􁊠􀲁􀙚􀔞􀓧􁊠􁜰􀙾􀚓􁰦􀹶􁒵􀮇􁯿􀷛􁊞􀱮􁖨􀨂􀷄􀴝􀒁􀭮􁖨􀨂􀷄
􀴝􁑱􁆐􀕗􀙖􀨂􀓾􁁾􀥦􀷸􀒂􀒅􀢩􀾌􀓤􁶎􁌱􀷜􁀩􀝢􀕦􀙂􁶎􀵉􁹛􀯔􁚆􀌶
10􀌵memcached 􀸎􀦇􀖜􀘉􁫝􀕲􁸵􁦤􁌱?
􁀌􀹍􁫝􀕲􁦊􁦤􀹢􀚫!memcached 􀸎􁬩􁤈􀣁􀬫􁊠􀓥􀩶􁌱􁫫􀕯(􁫝􀕲􁸵􁦤􀬫􁧆􀸎
􀬫􁊠􀓤􀩶􁌱􁘳􁨱)􀌶memcached 􁌱􀨮􀲁􁒒􀞾􀹐􀛓􀢏􁒒􀔏􀲅􀕦􀸎􁫷􁰁􁕆􁌱􀒅
􁮱􀚓􀜻􀢩􀩪􀸎􀨠􀙂􁀌􀹍􀨫􁈿􁫝􀕲􁸵􁦤􀹢􀚫􀌶􁬯􀻏􀒅memcached 􀝢􀕦􀮉􀮳
􀣈􀚠􀭌􀷛􁬳􀴳􀒅􀹐􀛓􀢏􁒒􀔞􀷫􁵱􀕱􀖜􁯈􁗝􀌶
􀦇􀺎􀰍􀫶􀹕􁴴􀚫􁦢􁳯􀒅􀰍􀝢􀕦􀖵􁊠􁴠􁅉􀤾􀒅􀱲􁘏􁦏 memcached 􁍊􀞍 unix
domain socket􀌶
11􀌵memcached 􁌱􀥚􁕚􁑕􀸎􀕋􀔍?􀦇􀖜􀖵􁊠􀨙􀕪?
􁕚􁑕􀩪􀸎􀨧􀮌(threads rule)!􀣁 Steven Grimm 􀞾 Facebook 􁌱􀛘􀛎􀓥􀒅
memcached 1.2 􀝊􀹅􁹛􁇇􀹜􀳜􀹍􀔧􀥚􁕚􁑕􀽜􀭗􀌶􀥚􁕚􁑕􀽜􀭗􊧋􁦜
memcached 􁚆􀥜􊧌􀚓􀚥􁊠􀥚􀓻 CPU􀒅􀬚􀣁 CPU 􀔏􁳵􀙈􀕁􀲅􀹍􁌱􁖨􀨂􀷄
􀴝􀌶memcached 􀖵􁊠􀓞􁐿􁓌􀜔􁌱􁲁􀹢􀚫􀹶􀗛􁦤􀷄􀴝􀹅􀷛􀶙􀖢􁌱􀔰􀷕􀌶􁍘
􀾲􀣁􀝶􀓞􀓻􁇔􁉘􀹢􀢏􀓤􁬩􁤈􀥚􀓻 memcached 􀨫􀖺􀒅􁬯􁐿􀷜􀭗􁚆􀥜􀹅􀹍􀶴
􀣈􀥒􁉘 multi gets􀌶
􀦇􀺎􀰍􁌱􁔮􁕹􁨮􁫹􀬚􀓧􁯿􀒅􀔞􁦜􀰍􀓧􁵱􁥝􀞐􁊠􀥚􁕚􁑕􀫡􀖢􀽜􀭗􀌶􀦇􀺎􀰍􀣁
􁬩􁤈􀓞􀓻􀳜􀹍􀥟􁥢􀽜􁏝􀕯􁌱􀌵􀬲􀥟􁌱􁗑􁒊􀒅􀰍􀩙􀕿􁍡􀚩􀥚􁕚􁑕􁌱􀦅􀥒􀌶
􁓌􀜔􀣈􀯛􁕮􀓞􀓥:􀞸􀕥􁥴􀺉(memcached 􀣁􁬯􁯾􁜰􀔧􀥟􁮱􀚓􀷸􁳵)􀝢􀕦􁬩􁤈
􀣁􀥚􁕚􁑕􀽜􀭗􀓥􀌶memcached 􀙖􁮱􀩒􀷄􀴝􁌱􀶙􀖢􀸎􀤚􀔭􀮉􀥚􀙂􀩴􁲁􁌱(􀢩
􀾌􁬯􁮱􀚓􀫡􀖢􀓧􀸎􀥚􁕚􁑕􁌱)􀌶􀹚􀹶􀩒􀥚􁕚􁑕􀽜􀭗􁌱􀶯􁬰􀒅􀩙􁑏􁴻􀥟􁰁􁌱􀙂
􀩴􁲁􀒅􀵉􁹛 memcached 􀣁􁨮􁫹􀺄􁹛􁌱􀣋􀸧􀓥􁌱􀯔􁚆􀌶
12􀌵memcached 􁚆􀴳􀝑􁌱 key 􁌱􀹋􀥟􁳩􀬶􀸎􀥚􀩝?
key 􁌱􀹋􀥟􁳩􀬶􀸎 250 􀓻􀨁􁒧􀌶􁵱􁥝􁀳􀰺􁌱􀸎􀒅250 􀸎 memcached 􀹐􀛓
􀢏􁒒􀙖􁮱􁌱􁴴􀚫􀒅􀦇􀺎􀰍􀖵􁊠􁌱􀨮􀲁􁒒􀶪􀳮”key 􁌱􀚹􁖗”􀱲􁔄􀖒􁇙􀯔􀒅􁮎
􀔍key(􀚹􁖗+􀜻􀦤 key􀒂􁌱􀹋􀥟􁳩􀬶􀸎􀝢􀕦􁩻􁬦250􀓻􀨁􁒧􁌱􀌶􀱯􀕪􀴵􁞂􀖵
􁊠􀖵􁊠􁫾􁎨􁌱 key 􀒅􀢩􀔅􀝢􀕦􁜓􁍜􀙖􀨂􀞾􀬃􀨼􀌶
13􀌵memcached 􀩒 item 􁌱􁬦􀹗􀷸􁳵􀹍􀕋􀔍􁴴􀚫?
􁬦􀹗􀷸􁳵􀹋􀥟􀝢􀕦􁬡􀚩 30 􀥠.memcached 􀲩􀖃􀙁􁌱􁬦􀹗􀷸􁳵(􀷸􁳵􀾧)􁥴􁯽
􀱮􀷸􁳵􁅩􀝸􀒅􀓞􀷮􀚩􀔧􁬯􀓻􀷸􁳵􁅩􀒅memcached 􀩪􀲩 item 􁗝􀔅􀥦􀶴􁇫
􀮾􀌶􁬯􀸎􀓞􀓻􁓌􀜔􀖕 obscure 􁌱􀹢􀚫􀌶
14􀌵memcached 􀹋􀥟􁚆􀨂􀘙􀥚􀥟􁌱􀜔􀓻 item?
1MB􀌶􀦇􀺎􀖦􁌱􀷄􀴝􀥟􀔭 1MB􀒅􀝢􀕦􁘍􁡤􀣁􀨮􀲁􁒒􀜴􁖽􀱲􀳆􀚓􀚩􀥚􀓻 key
􀓾􀌶