# स्वस्य SMTP मेल प्रेषणसर्वरं निर्मायताम्

## प्रस्तावना

SMTP प्रत्यक्षतया मेघविक्रेतृभ्यः सेवां क्रेतुं शक्नोति, यथा-

* [अमेजन एसईएस एसएमटीपी](https://docs.aws.amazon.com/ses/latest/dg/send-email-smtp.html)
* [अली मेघ ईमेल धक्का](https://www.alibabacloud.com/help/directmail/latest/three-mail-sending-methods)

भवान् स्वस्य मेलसर्वरं अपि निर्मातुम् अर्हति - असीमितप्रेषणम्, समग्रव्ययः न्यूनः ।

अधः वयं स्वस्य मेलसर्वरस्य निर्माणं कथं करणीयम् इति पदे पदे दर्शयामः ।

## सर्वर चयनम्

स्वयमेव होस्ट् कृतस्य SMTP सर्वरस्य कृते सार्वजनिक IP आवश्यकं यस्य पोर्ट् 25, 456, 587 च उद्घाटिताः सन्ति ।

सामान्यतया प्रयुक्ताः सार्वजनिकमेघाः पूर्वनिर्धारितरूपेण एतान् पोर्ट्-स्थानानि अवरुद्धवन्तः, कार्य-आदेशं निर्गत्य तान् उद्घाटयितुं शक्यते, परन्तु सर्वथा अतीव कष्टप्रदम् अस्ति

अहं एकस्मात् होस्ट् इत्यस्मात् क्रयणं अनुशंसयामि यस्य एते पोर्ट् उद्घाटिताः सन्ति तथा च विपरीतडोमेन् नामस्थापनं समर्थयति ।

अत्र, अहं [Contabo](https://contabo.com) इति अनुशंसयामि ।

कोण्टाबो जर्मनीदेशस्य म्यूनिखनगरे स्थितः होस्टिंग् प्रदाता अस्ति, यस्य स्थापना २००३ तमे वर्षे अतीव प्रतिस्पर्धात्मकमूल्यानां सह अभवत् ।

यदि भवान् क्रयणस्य मुद्रारूपेण यूरो चिनोति तर्हि मूल्यं सस्तां भविष्यति (८GB स्मृतिः ४ CPU च युक्तस्य सर्वरस्य मूल्यं प्रतिवर्षं प्रायः ५२९ युआन् भवति, प्रारम्भिकस्थापनशुल्कं च एकवर्षं यावत् निःशुल्कं भवति)

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/UoAQkwY.webp)

आदेशं ददाति समये टिप्पणीं कुर्वन्तु `prefer AMD` , AMD CPU युक्तस्य सर्वरस्य उत्तमं प्रदर्शनं भविष्यति ।

निम्नलिखितरूपेण अहं Contabo इत्यस्य VPS उदाहरणरूपेण गृह्णामि यत् भवतः स्वस्य मेलसर्वरस्य निर्माणं कथं करणीयम् इति प्रदर्शयिष्यामि ।

## उबण्टु प्रणाली विन्यास

अत्र प्रचालनतन्त्रम् उबण्टु २२.०४ अस्ति

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/smpIu1F.webp)

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/m7Mwjwr.webp)

यदि ssh इत्यत्र सर्वरः प्रदर्शयति तर्हि `Welcome to TinyCore 13!` (यथा अधोलिखिते चित्रे दर्शितम्), अद्यापि प्रणाली न स्थापिता इति अर्थः । कृपया ssh इत्यस्य संयोजनं विच्छिद्य पुनः प्रवेशार्थं कतिपयानि निमेषाणि प्रतीक्ष्यताम् ।

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/-qKACz9.webp)

यदा `Welcome to Ubuntu 22.04.1 LTS` इति दृश्यते तदा आरम्भः सम्पन्नः भवति, ततः भवन्तः निम्नलिखितपदार्थैः निरन्तरं कर्तुं शक्नुवन्ति ।

### [वैकल्पिकम्] विकासवातावरणं आरभत

एतत् पदं वैकल्पिकम् अस्ति ।

सुविधायै अहं ubuntu सॉफ्टवेयरस्य संस्थापनं प्रणालीविन्यासं च [github.com/wactax/ops.os/tree/main/ubuntu](https://github.com/wactax/ops.os/tree/main/ubuntu) इत्यत्र स्थापयामि ।

एकेन क्लिक् कृत्वा संस्थापयितुं निम्नलिखितम् आदेशं चालयन्तु ।

```
bash <(curl -s https://raw.githubusercontent.com/wactax/ops.os/main/ubuntu/boot.sh)
```

चीनी उपयोक्तारः, कृपया तस्य स्थाने निम्नलिखित-आदेशस्य उपयोगं कुर्वन्तु, ततः भाषा, समयक्षेत्रम् इत्यादयः स्वयमेव सेट् भविष्यन्ति ।

```
CN=1 bash <(curl -s https://ghproxy.com/https://raw.githubusercontent.com/wactax/ops.os/main/ubuntu/boot.sh)
```

### Contabo IPV6 सक्षमं करोति

IPV6 सक्षमं कुर्वन्तु येन SMTP IPV6 पताभिः सह ईमेल अपि प्रेषयितुं शक्नोति ।

`/etc/sysctl.conf` सम्पादयतु

निम्नलिखितपङ्क्तयः परिवर्तयन्तु अथवा योजयन्तु

```
net.ipv6.conf.all.disable_ipv6 = 0
net.ipv6.conf.default.disable_ipv6 = 0
net.ipv6.conf.lo.disable_ipv6 = 0
```

[contabo पाठ्यक्रमस्य अनुसरणं कुर्वन्तु: स्वस्य सर्वरे IPv6 संयोजनं योजयति](https://contabo.com/blog/adding-ipv6-connectivity-to-your-server/)

`/etc/netplan/01-netcfg.yaml` सम्पादयन्तु, अधोलिखिते चित्रे दर्शितवत् कतिपयानि पङ्क्तयः योजयन्तु (Contabo VPS पूर्वनिर्धारितविन्याससञ्चिकायां पूर्वमेव एताः पङ्क्तयः सन्ति, केवलं तान् अटिप्पणीं कुर्वन्तु) ।

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/5MEi41I.webp)

ततः परिवर्तितं विन्यासं प्रभावी कर्तुं `netplan apply` ।

विन्यासस्य सफलतायाः अनन्तरं भवान् स्वस्य बाह्यजालस्य ipv6 पतां द्रष्टुं `curl 6.ipw.cn` उपयोगं कर्तुं शक्नोति ।

## विन्यासभण्डारस्य क्लोनीकरणं ops

```
git clone https://github.com/wactax/ops.soft.git
```

## स्वस्य डोमेननामस्य कृते निःशुल्कं SSL प्रमाणपत्रं जनयन्तु

मेल प्रेषणार्थं एन्क्रिप्शनं हस्ताक्षरं च कर्तुं SSL प्रमाणपत्रस्य आवश्यकता भवति ।

प्रमाणपत्राणि जनयितुं वयं [acme.sh इत्यस्य](https://github.com/acmesh-official/acme.sh) उपयोगं कुर्मः ।

acme.sh इति मुक्तस्रोतस्वचालितं प्रमाणपत्रहस्ताक्षरसाधनम् अस्ति,

विन्यासगोदाम ops.soft प्रविष्टं कुर्वन्तु, `./ssl.sh` चालयन्तु, ततः **उपरि निर्देशिकायां** `conf` पुटं निर्मितं भविष्यति ।

[acme.sh dnsapi](https://github.com/acmesh-official/acme.sh/wiki/dnsapi) इत्यस्मात् स्वस्य DNS प्रदातां अन्वेष्टुम् , `conf/conf.sh` सम्पादयतु ।

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/Qjq1C1i.webp)

ततः स्वस्य डोमेननामस्य कृते `123.com` तथा `*.123.com` प्रमाणपत्राणि जनयितुं `./ssl.sh 123.com` चालयन्तु ।

प्रथमं चालनं स्वयमेव [acme.sh](https://github.com/acmesh-official/acme.sh) संस्थापयिष्यति तथा च स्वचालितनवीकरणाय निर्धारितं कार्यं योजयिष्यति । `crontab -l` द्रष्टुं शक्नुवन्ति, एतादृशी रेखा अस्ति यथा ।

```
52 0 * * * "/mnt/www/.acme.sh"/acme.sh --cron --home "/mnt/www/.acme.sh" > /dev/null
```

उत्पन्नप्रमाणपत्रस्य मार्गः `/mnt/www/.acme.sh/123.com_ecc。`

प्रमाणपत्रस्य नवीकरणेन `conf/reload/123.com.sh` स्क्रिप्ट् आह्वयति, एतत् स्क्रिप्ट् सम्पादयतु, सम्बन्धित-अनुप्रयोगानाम् प्रमाणपत्र-सञ्चयं ताजगीं कर्तुं `nginx -s reload` इत्यादीन् आदेशान् योजयितुं शक्नुथ

## chasquid इत्यनेन सह SMTP सर्वरं निर्मायताम्

[chasquid](https://github.com/albertito/chasquid) इति Go भाषायां लिखितः मुक्तस्रोतः SMTP सर्वरः अस्ति ।

Postfix, Sendmail इत्यादीनां प्राचीनमेलसर्वरकार्यक्रमानाम् विकल्परूपेण chasquid सरलतरं सुलभतरं च भवति, गौणविकासाय अपि सुलभतरम् अस्ति

Run `./chasquid/init.sh 123.com` एकेन क्लिकेण स्वयमेव संस्थाप्यते (123.com इत्यस्य स्थाने भवतः प्रेषण-डोमेन-नाम स्थापयन्तु) ।

## ईमेल हस्ताक्षर DKIM विन्यस्तं कुर्वन्तु

पत्राणां स्पैमरूपेण व्यवहारः न भवेत् इति कृते ईमेलहस्ताक्षराणि प्रेषयितुं DKIM इत्यस्य उपयोगः भवति ।

आदेशस्य सफलतया चालनस्य अनन्तरं भवन्तः DKIM अभिलेखं (यथा अधः दर्शितम्) सेट् कर्तुं प्रेरिताः भविष्यन्ति ।

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/LJWGsmI.webp)

केवलं स्वस्य DNS मध्ये TXT अभिलेखं योजयन्तु (यथा अधः दर्शितम्) ।

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/0szKWqV.webp)

## सेवास्थितिः & लॉग्स् च पश्यन्तु

 `systemctl status chasquid` सेवा स्थितिं पश्यन्तु।

सामान्यसञ्चालनस्य स्थितिः अधोलिखिते चित्रे यथा दर्शिता तथा अस्ति

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/CAwyY4E.webp)

 `grep chasquid /var/log/syslog` अथवा `journalctl -xeu chasquid` त्रुटिवृत्तं द्रष्टुं शक्नोति ।

## डोमेननाम विन्यासं विपर्ययम्

विपरीत-डोमेन्-नाम IP-सङ्केतं तत्सम्बद्धे डोमेन-नाम्नि समाधानं कर्तुं अनुमन्यते ।

विपरीत-डोमेन्-नाम सेट् कृत्वा ईमेल-पत्राणि स्पैम्-रूपेण चिह्नितुं न शक्नुवन्ति ।

यदा मेलः प्राप्यते तदा ग्राहकः सर्वरः प्रेषकसर्वरस्य IP-सङ्केते विपरीत-डोमेन्-नाम-विश्लेषणं करिष्यति यत् प्रेषक-सर्वरस्य वैधं विपरीत-डोमेन-नाम अस्ति वा इति पुष्टिं करिष्यति

यदि प्रेषकसर्वरस्य विपरीतक्षेत्रनाम नास्ति अथवा यदि विपरीतक्षेत्रनाम प्रेषकसर्वरस्य IP-सङ्केतेन सह न मेलति तर्हि ग्राहकसर्वरः ईमेलं स्पैमरूपेण ज्ञातुं वा अङ्गीकुर्वितुं वा शक्नोति

[https://my.contabo.com/rdns](https://my.contabo.com/rdns) इति गत्वा अधः दर्शितवत् विन्यस्यताम्

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/IIPdBk_.webp)

विपरीत-डोमेन्-नाम सेट् कृत्वा, ipv4 तथा ipv6 इति डोमेन्-नामस्य अग्रे-संकल्पं सर्वरे विन्यस्तुं स्मर्यताम् ।

## chasquid.conf इत्यस्य होस्ट्नाम सम्पादयन्तु

`conf/chasquid/chasquid.conf` इत्येतत् विपरीतडोमेननामस्य मूल्ये परिवर्तयन्तु ।

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/6Fw4SQi.webp)

ततः सेवां पुनः आरभ्य `systemctl restart chasquid` चालयन्तु ।

## git भण्डारं प्रति conf इत्यस्य बैकअपं कुर्वन्तु

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/Fier9uv.webp)

यथा, अहं conf फोल्डर् इत्यस्य बैकअप मम स्वस्य github प्रक्रियायां निम्नलिखितरूपेण करोमि

प्रथमं निजीगोदामस्य निर्माणं कुर्वन्तु

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/ZSCT1t1.webp)

conf निर्देशिकां प्रविश्य गोदामे प्रस्तूयताम्

```
git init
git add .
git commit -m "init"
git branch -M main
git remote add origin git@github.com:wac-tax-key/conf.git
git push -u origin main
```

## प्रेषकं योजयतु

धावनं करोतु

```
chasquid-util user-add i@wac.tax
```

प्रेषकं योजयितुं शक्नोति

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/khHjLof.webp)

### गुप्तशब्दः सम्यक् सेट् कृतः इति सत्यापयन्तु

```
chasquid-util authenticate i@wac.tax --password=xxxxxxx
```

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/e92JHXq.webp)

उपयोक्तारं योजयित्वा `chasquid/domains/wac.tax/users` अद्यतनं भविष्यति, गोदामे प्रस्तूयताम् इति स्मर्यताम्।

## DNS SPF अभिलेखं योजयति

SPF ( Sender Policy Framework ) इति ईमेल-सत्यापन-प्रौद्योगिकी अस्ति यस्य उपयोगः ईमेल-धोखाधड़ी-निवारणाय भवति ।

एतत् प्रेषकस्य IP-सङ्केतं यस्य डोमेन-नामस्य DNS-अभिलेखैः सह मेलति इति परीक्ष्य मेलप्रेषकस्य परिचयं सत्यापयति, येन धोखाधड़ीः बोगस-ईमेल-प्रेषणं न कुर्वन्ति

SPF अभिलेखान् योजयित्वा ईमेल-पत्राणि यथासम्भवं स्पैम् इति चिह्नितुं न शक्नुवन्ति ।

यदि भवतां डोमेननामसर्वरः SPF प्रकारस्य समर्थनं न करोति तर्हि केवलं TXT प्रकारस्य अभिलेखं योजयन्तु ।

यथा, `wac.tax` इत्यस्य SPF यथा भवति

`v=spf1 a mx include:_spf.wac.tax include:_spf.google.com ~all`

`_spf.wac.tax` कृते SPF

`v=spf1 a:smtp.wac.tax ~all`

ध्यानं कुर्वन्तु यत् मया अत्र `include:_spf.google.com` , एतत् यतोहि अहं पश्चात् Google मेलबॉक्स् मध्ये `i@wac.tax` इत्येतत् प्रेषणसङ्केतं विन्यस्यामि ।

## DNS विन्यास DMARC

DMARC इति (Domain-based Message Authentication, Reporting & Conformance) इत्यस्य संक्षिप्तरूपम् ।

इदं SPF-उच्छ्वास-ग्रहणाय उपयुज्यते (कदाचित् विन्यास-दोषाणां कारणेन, अथवा अन्यः कोऽपि स्पैम-प्रेषणार्थं भवतः अभिनयं करोति) ।

TXT अभिलेखं योजयन्तु `_dmarc` , .

विषयवस्तु यथा

```
v=DMARC1; p=quarantine; fo=1; ruf=mailto:ruf@wac.tax; rua=mailto:rua@wac.tax
```

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/k44P7O3.webp)

प्रत्येकस्य पैरामीटर् इत्यस्य अर्थः यथा भवति

### प (नीति) ९.

SPF (Sender Policy Framework) अथवा DKIM (DomainKeys Identified Mail) सत्यापनम् विफलं कुर्वन्तः ईमेल कथं नियन्त्रयितुं शक्नुवन्ति इति सूचयति । p पैरामीटर् त्रयाणां मूल्यानां मध्ये एकं मूल्यं सेट् कर्तुं शक्यते:

* none: कोऽपि कार्यवाही न क्रियते, केवलं सत्यापनपरिणामं ईमेल-रिपोर्टिंग्-तन्त्रेण प्रेषकं प्रति पुनः प्रदत्तं भवति ।
* क्वारेन्टाइनः - यत् मेलं सत्यापनं न पारितं तत् स्पैम् फोल्डर् मध्ये स्थापयतु, परन्तु मेलं प्रत्यक्षतया न अङ्गीकुर्यात् ।
* reject: सत्यापनं विफलं कुर्वन्तः ईमेल प्रत्यक्षतया अङ्गीकुर्वन्तु।

### fo (विफलता विकल्पाः) २.

रिपोर्टिंग् तन्त्रेण प्रत्यागतानां सूचनानां परिमाणं निर्दिशति । निम्नलिखितमूल्येषु एकस्मिन् सेट् कर्तुं शक्यते ।

* 0: सर्वेषां सन्देशानां प्रमाणीकरणपरिणामानां सूचनां ददातु
* 1: केवलं तान् सन्देशान् प्रतिवेदयन्तु ये सत्यापनं विफलं कुर्वन्ति
* d: केवलं डोमेननामसत्यापनविफलतायाः सूचनां ददातु
* s: केवलं SPF सत्यापनविफलतायाः सूचनां ददातु
* l: केवलं DKIM सत्यापनविफलतायाः सूचनां ददातु

### rua & ruf

* rua (समुच्चय-रिपोर्ट्-कृते URI-रिपोर्टिंग्): समुच्चय-रिपोर्ट्-प्राप्त्यर्थं ईमेल-सङ्केतः
* ruf (Forensic reports कृते URI रिपोर्टिंग्): विस्तृतप्रतिवेदनानि प्राप्तुं ईमेल-सङ्केतः

## Google Mail मध्ये ईमेलं अग्रे प्रेषयितुं MX अभिलेखान् योजयन्तु

यतः मया सार्वभौमिकसङ्केतानां समर्थनं कुर्वन् निःशुल्कं निगमीयं मेलबॉक्सं न लब्धम् (Catch-All, अस्मिन् डोमेननाम्नि प्रेषितं किमपि ईमेल-पत्रं प्राप्तुं शक्नोति, उपसर्गेषु प्रतिबन्धं विना), अहं सर्वाणि ईमेल-पत्राणि मम Gmail-मेलपेटिकायां अग्रे प्रेषयितुं chasquid-इत्यस्य उपयोगं कृतवान्

**यदि भवतां स्वकीयः सशुल्कव्यापारमेलबॉक्सः अस्ति तर्हि कृपया MX परिवर्तनं न कुर्वन्तु तथा च एतत् पदं त्यजन्तु ।**

`conf/chasquid/domains/wac.tax/aliases` सम्पादयन्तु , अग्रे प्रेषणं मेलबॉक्सं सेट् कुर्वन्तु

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/OBDl2gw.webp)

`*` सर्वाणि ईमेल-पत्राणि सूचयति, `i` उपरि निर्मितस्य प्रेषकस्य उपयोक्तुः ईमेल-सङ्केत-उपसर्गः अस्ति । मेलम् अग्रे प्रेषयितुं प्रत्येकं उपयोक्त्रेण रेखां योजयितुं आवश्यकम् ।

ततः MX अभिलेखं योजयन्तु (अहम् अत्र विपरीत-डोमेन्-नामस्य पतां प्रत्यक्षतया दर्शयामि, यथा अधोलिखिते चित्रे प्रथमपङ्क्तौ दर्शितम्) ।

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/7__KrU8.webp)

विन्यासस्य समाप्तेः अनन्तरं भवान् अन्येषां ईमेल-सङ्केतानां उपयोगेन `i@wac.tax` इत्यत्र ईमेल प्रेषयितुं शक्नोति तथा च `any123@wac.tax` ईमेल-पत्राणि प्रेषयितुं शक्नोति यत् भवान् Gmail मध्ये ईमेल-पत्राणि प्राप्तुं शक्नोति वा इति।

यदि न, तर्हि chasquid log ( `grep chasquid /var/log/syslog` ) पश्यन्तु ।

## Google Mail इत्यनेन i@wac.tax इत्यत्र ईमेल प्रेषयन्तु

गूगलमेल इत्यनेन मेल प्राप्तस्य अनन्तरं स्वाभाविकतया अहं i.wac.tax@gmail.com इत्यस्य स्थाने `i@wac.tax` इत्यनेन उत्तरं दास्यामि इति आशां कृतवान्।

[https://mail.google.com/mail/u/1/#settings/accounts](https://mail.google.com/mail/u/1/#settings/accounts) इति गत्वा "अन्यं ईमेल-सङ्केतं योजयतु" इति क्लिक् कुर्वन्तु ।

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/PAvyE3C.webp)

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/_OgLsPT.webp)

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/XIUf6Dc.webp)

ततः, यस्य ईमेलस्य कृते अग्रे प्रेषितः आसीत् तया प्राप्तं सत्यापनसङ्केतं प्रविशतु ।

अन्ते, पूर्वनिर्धारितप्रेषकसङ्केतः (समानसङ्केतेन उत्तरं दातुं विकल्पेन सह) सेट् कर्तुं शक्यते ।

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/a95dO60.webp)

एवं प्रकारेण वयं SMTP मेलसर्वरस्य स्थापनां सम्पन्नवन्तः तथा च तत्सहकालं ईमेल प्रेषयितुं प्राप्तुं च Google Mail इत्यस्य उपयोगं कृतवन्तः।

## विन्यासः सफलः अस्ति वा इति परीक्षितुं परीक्षण-ईमेलं प्रेषयन्तु

`ops/chasquid` इति प्रविष्टं कुर्वन्तु

रन `direnv allow` to install dependencies (direnv पूर्वस्मिन् एक-कुंजी आरम्भप्रक्रियायां संस्थापितम् अस्ति तथा च शेल् मध्ये एकः हुकः योजितः अस्ति)

ततः धावतु

```
user=i@wac.tax pass=xxxx to=iuser.link@gmail.com ./sendmail.coffee
```

पैरामीटर्-अर्थः यथा

* उपयोक्ता: SMTP उपयोक्तृनाम
* pass: SMTP गुप्तशब्दः
* to: प्राप्तकर्ता

भवान् परीक्षण-ईमेलं प्रेषयितुं शक्नोति।

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/ae1iWyM.webp)

विन्यासाः सफलाः सन्ति वा इति परीक्षितुं परीक्षण-ईमेल-प्राप्त्यर्थं Gmail-इत्यस्य उपयोगः अनुशंसितः अस्ति ।

### TLS मानक एन्क्रिप्शन

यथा अधोलिखिते चित्रे दर्शितं, अस्ति एतत् लघु तालं, यस्य अर्थः अस्ति यत् SSL प्रमाणपत्रं सफलतया सक्षमं कृतम् अस्ति ।

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/SrdbAwh.webp)

ततः "Show Original Email" इत्यत्र क्लिक् कुर्वन्तु ।

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/qQQsdxg.webp)

### DKIM

यथा अधोलिखिते चित्रे दर्शितं, Gmail मूलमेलपृष्ठं DKIM प्रदर्शयति, यस्य अर्थः अस्ति यत् DKIM विन्यासः सफलः अस्ति ।

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/an6aXK6.webp)

मूल-ईमेलस्य शीर्षके Received इति पश्यन्तु, ततः प्रेषकस्य पता IPV6 इति द्रष्टुं शक्नुवन्ति, यस्य अर्थः अस्ति यत् IPV6 अपि सफलतया विन्यस्तम् अस्ति ।
