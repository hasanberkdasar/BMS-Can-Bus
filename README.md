🇬🇧 English
I am a 1st-year Electrical and Electronics Engineering student at Kahramanmaraş Sütçü İmam University (KSU). In this project, I designed a smart BMS hardware for electric vehicles featuring cell monitoring, charge/discharge control, and CAN Bus communication.

⚠️ Note / Transparency:
This board is a prototype developed entirely during my learning process. Since I am a first-year student, there might be some amateur routing choices or layout imperfections in the schematic and PCB. I am continuously improving and fixing these in future revisions.

Purpose and Why 4S?
The main goal is to individually monitor cell voltages of series-connected lithium batteries and protect against overcharge, over-discharge, and current spikes.

Why 4S?: I chose a 4S (4-Series) configuration for this initial design to grasp the core concepts, keep prototyping costs low, and work easily with standard battery packs.

Components and Purpose
BQ76952 IC (U1):
Why chosen?: It is an industry-standard, highly integrated battery monitor and protection IC.

How it's connected & its role: Cell positive and negative terminals are wired directly to the IC's cell input pins (VC0 through VC5) to monitor individual cell voltages. It also reads temperature sensors (TS1, etc.) and triggers hardware protections when necessary.

Shunt Resistor (RShuntResistor):
Why chosen?: A low-ohm, high-power resistor designed to safely handle and measure high currents.

How it's connected & its role: Placed in series with the main power path. The tiny voltage drop across it is measured by the BQ76952 (SRP and SRN pins) to accurately calculate the real-time current flowing through the system.

Power MOSFETs (Q3, Q4, Q5, Q6):
Why chosen?: Power semiconductors with low on-resistance (Rds_on) capable of switching high current loads.

How it's connected & its role: Placed in series along the charge and discharge paths. They are driven by the CHG_GATE and DSG_GATE signals from the main IC. In case of a fault (overcurrent, overvoltage), they turn off to disconnect the power path and protect the cells.

Filter and Protection Components (R1-R12, C3-C6):
Why chosen?: Resistors and capacitors used to ensure signal integrity and suppress external electromagnetic noise.

How it's connected & its role: Connected as RC filter networks along sensitive signal traces leading to IC pins, preventing false readings or erroneous triggers caused by electrical noise.

📂 Dosya Yapısı / File Structure
BMS-Can-Bus.kicad_sch - Şematik / Schematic

BMS-Can-Bus.kicad_pcb - PCB Yerleşimi / PCB Layout

BMS-Can-Bus.kicad_pro - KiCad Proje Dosyası / Project File

ksulog2.kicad_mod - KSÜ Logo Footprint
******************************************************************************************************
🇹🇷 Türkçe
Kahramanmaraş Sütçü İmam Üniversitesi (KSÜ) Elektrik-Elektronik Mühendisliği 1. sınıf öğrencisiyim. Bu projede, elektrikli araçlar için hücre takibi, şarj/deşarj kontrolü ve CAN Bus haberleşmesi yapabilen akıllı bir BMS donanımı tasarladım.

⚠️ Not / Şeffaflık:
Bu kart tamamen öğrenme sürecimde geliştirdiğim bir prototiptir. İlk senemde olduğum için şematik ve PCB yerleşiminde bazı amatör hatalar veya karmaşık yollar olabilir. Sistemi geliştirdikçe yeni revizyonlarda bunları düzeltmeye devam ediyorum.

Projenin Amacı ve Neden 4S Seçildi?
Bu kartın amacı; seri bağlı lityum hücrelerin voltajlarını tek tek okumak, aşırı şarj/deşarj ve akım dalgalanmalarına karşı kartı korumaktır.

Neden 4S?: Sistemi ilk başta anlamak, maliyeti düşük tutmak ve yaygın 4S (yaklaşık 14.8V) batarya bloklarıyla çalışabilmek için bu konfigürasyonu seçtim.

Parçalar ve Kullanım Amaçları:
BQ76952 Entegresi (U1):
Ne için seçildi?: Endüstride çok güvenilen, yüksek entegrasyona sahip bir batarya yönetim ve koruma entegresidir.

Nasıl bağlandı ve görevi nedir?: Hücrelerin artı ve eksi uçları (VC0 - VC5 arası pinler) doğrudan bu entegreye bağlanarak her bir hücrenin voltajı anlık olarak okunur. Ayrıca entegre, üzerindeki sıcaklık sensörleri (TS1 vb.) ile bataryanın ısısını takip eder ve kritik durumlarda korumayı tetikler.

Şönt Direnci (RShuntResistor):
Ne için seçildi?: Kart üzerinden geçen yüksek akımı hassas bir şekilde ölçebilmek için düşük ohm değerine ve yüksek güç dayanımına sahip özel bir dirençtir.

Nasıl bağlandı ve görevi nedir?: Ana akım hattı üzerine seri olarak bağlanır. Üzerinden akım geçerken yarattığı çok küçük voltaj düşümünü (SRP ve SRN pinleri üzerinden) BQ76952 okur, böylece anlık olarak kaç amper çekildiği hesaplanır.

Güç MOSFET'leri (Q3, Q4, Q5, Q6):
Ne için seçildi?: Düşük iç dirence (Rds_on) sahip, yüksek akım geçişini anahtarlayabilen güç yarı iletkenleridir.

Nasıl bağlandı ve görevi nedir?: Şarj ve deşarj hatları üzerine seri yerleştirilmiştir. BQ76952'nin CHG_GATE ve DSG_GATE pinlerinden gelen sinyallerle kontrol edilirler. Herhangi bir tehlike anında (aşırı akım veya yüksek voltaj) bu anahtarlar açılarak akım akışı kesilir ve sistem korunur.

Filtre ve Koruma Elemanları (R1-R12, C3-C6):
Ne için seçildi?: Sinyal bütünlüğünü korumak ve dış elektromanyetik gürültüleri engellemek için kullanılan direnç ve kondansatörlerdir.

Nasıl bağlandı ve görevi nedir?: Entegre bacaklarına giden hassas hatlara seri dirençler ve paralel kondansatörler (RC filtreler) şeklinde yerleştirilmiştir. Amaç, hatlardaki parazitleri süzerek yanlış ölçümlerin veya hatalı tetiklemelerin önüne geçmektir.

📂 Dosya Yapısı / File Structure
BMS-Can-Bus.kicad_sch - Şematik / Schematic

BMS-Can-Bus.kicad_pcb - PCB Yerleşimi / PCB Layout

BMS-Can-Bus.kicad_pro - KiCad Proje Dosyası / Project File

ksulog2.kicad_mod - KSÜ Logo Footprint
