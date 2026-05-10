Active Directory Domain Controller (ADDC) quraşdırılması

Biz əvvəl ilkin konfuqrasiyyaları etməliyik və bunun üçün aşağıdakı addımları izləmək şərtdir.
1.	Local Server bölməsinə gəldikdən sonra konfuqrasiyaya başlaya bilərik. İlk addım olarağ Computer name dəyişək :

 

“Change...” daha sonra “Computer name” kompyuterimizin adını yazırığ. Misal: win-19




2.	FireWall  deaktiv olunmalıdır. Bunun üçün:

 
 




Açılan bu pəncərədə “On”   “Off” la əvəz olunmalıdır. Bunu Domain, private və public network üçün etməliyik.
 







Və son olarağ nəticəmiz aşağıdakı kimi görsənməlidir:
 





3.	Remote Desktop:  Ola bilərki əməkdaş həmin gün işə gəlməyibdi və serverdə nasazlığ yaranmasıvəziyyətində Servere uzağdan qoşulma mümkün olsun deyə Remote Desktop enabled vəziyyətində olmalıdır. Və bunun üçün :
 
Burda “Allow remote connections to this computer” seçimini edirik.
 
Daha sonra “Apply”  daha sonra  “OK”







4.	Network connection  Bölməsinə gəliriy bunun üçün WIN + R  da ‘ncpa.cpl’ yazmalıyığ.
Halhazırda burayla bir işimiz yoxdu ancaq daha sonra görəcəyimiz işlər bir qədər rahat olsun deyə adını dəyişməliyik.
 

5.	Daha sonra gəliriy “security” bölməsini   “off”  vəziyyətinə gətiririk.

Administrators “off”
Users “off”
Və son olarağ OK vurub bitiririk.

Aşağıdakı şəkildə hər şey aydın olacağ.
 







6.	Time zona bölməsinə gəlib dəyişikliklər etmək lazımdır. Biz burda “(UTC +04:00) Baku” seçimini edirik.
 



7.	Konfuqrasiyyamızın bitməsi üçün son addım qaldı. Bizim etdiyimiz dəyişiklərin qeydə alınması üçün restart etməliyik.
 

Və son olarağ Local Server pəncərəsi belə görsənməlidir :
 




Bəli, biz artığ kompyuterimizi domen mühitə sala biləriy bunun üçün lazım olan addımları ardıcıllığla aşağı qeyd edirəm.


1.	Dashboard pəncərəsinə gəlir Add roles and features seçimini edirik.  Və açılan pəncərələrdə ilk 3 addımı heçbir dəyişiklilik etmədən Next ə basırığ.

 
Seçimimizi etdikdən sonra, növbəti 3 addımıda Next ə basırığ. Daha sonra isə “install” a tıklayıb yüklənməyini gözləyirik.












2.Yüklənikdən sonra bu konfuqrasiyyanın tamamlandığı mənasına gəlmir. Sağ yuxarıdakı bayrağa tıklayarağ konfuqrasiyaya davam etməliyik. 
 
Daha sonra “Promote this server to a domain controller”










3.
 

‘Add a new forest’  seçimini etdikdən sonra domein ə ad veririk məsələn : code.local
Daha sonra Next.
 




Burda şifrə təyin edirəm daha sonra ardıcıl olarağ  Nextlərə basarağ install edirəm.
 
İnstallation pəncərəsi.
4.Yüklənmə bitdikdən sonra restart.
 
Restart dan sonra giriş ekranımız belə görünəcək.
 
Artığ code.local , Local Server pəncərəsində görünür.

Bəli bizim artığ domen mühitimiz var. Və mən kənarda yatardığım kompyuteri domenə üzv etmək isdəyirəm və bunun üçün aşağıdakı addımlar izlənir.
 1.İlkin olarağ bir Network Adapter əlavə etməliyəm.
 
Sonra Finish və OK.
 
Bəli, yeni Ethernet kabelimiz artığ mövcuddur.
Və yenidən WIN+RUN da ncpa.cpl yazıb adını LAN olarağ dəyişiriy.

 





Daha sonra “Properties” daxil olub, İPv4 ü klikləyirik.
 

Və özümüzdən ip veririk ancaq test məqsədiylə olduğu üçün  bunu edirik. Siz işlədiyiniz yerin ip sini bilməlisiz və ona uyğun dəyişikliklər aparmalısınız.
Bu dəyişiklikləri etdikdən sonra biz serverimizin ip sini qurmuş oluruğ və keçiriy Windows a və burdada eyni qaydada WIN +RUN da ncpa.cpl yazıb  daxil oluram. 
“Properties” daxil olub, İPv4 ü klikləyirik. Və ip ni statikə çəkirik. 1 ip 1 cihaza bağlı olur ona görədə serverdə yazdığım ipni bura verənmərəm ona görədə eyni şəbəkədən fərqli ip verəcəm.
 Daha sonra Default Gateway  bu nədi?  Default Gateway məni fərqli şəbəkələrlə danışdırması üçün nəzərdə tutulur. Yəni bir növ qapı rolunu oynayır.
Mən digər şəbəkələrlə danışmaq üçün birinci hara müraciət edirəm ? Serverə. Və daha sonra serverin daxilində routing edərək digər şəbəkələrlə rahatlığla danışa və internetə çıxa bilirəm onun üçün kompyuterimizin Default Gateway i serverimiz olacaq. 
DNS serverədə eyni qaydada Serverimizin ip sini qeyd edəcəm.
 



İndi gələk əsas məsələyə... Kabellərə:




Virtual maşın xəyali olarağ switch funksiyasını daşıyır. Biz kompyuterimizdə adapterimiz NAT da qalıbdı onu LAN a çəkməliyik və yeni Lan segment yaratmalıyığ. Bu Lan segment nədir? Pc nin ethernet yeri var ora bir kabel taxırığ digər bir kabeli isə gətirib serverin portuna taxırığ
 
 Daha sonra bu dəyişiklik etdiyimiz adapterlərimizi söndürüb təzədən yandırırığ.

Yoxlamağ məqsədi ilə kompyuterimizdə cmd yə daxil olarağ serverimizə ping atağ.
 


Ancaq eyni şəbəkədə olub cihazların bir birini görməsi, bir birinə İCMP paket göndərməsi o demək deyilki biz domeinə qoşulmuşuğ. Domeinə qoşmağ isdəyiriksə əgər WIN+RUN da “sysdm.cpl” yazıb daxil oluruğ və “Change” bölməsini klikləyirirk.
 
 

Domein adımı qeyd etdikdən sonra dodmein administratorunun adını və parolumuzu yazırığ. Daha sonra OK. 
Belə bir mesaj qarşımıza çıxdığdan sonra OK klikləyib restart edirik.
  
Bəli biz artığ isdədiyimzə nail olduğ domein mühit yaratdığ kompyuterimizi domeinə qoşduğ yeni NİC lər yaratdıq.
[Active Directory Domain Controller.docx](https://github.com/user-attachments/files/27572054/Active.Directory.Domain.Controller.docx)
