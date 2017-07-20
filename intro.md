## 简介

Maltrail是一个恶意的流量检测系统，利用公开的黑名单列表，其中包含恶意或可疑的路径，以及从各种AV报告和自定义用户定义的列表中编译的静态路径，其中跟踪可以是域名中的任何内容（例如zvpprsensinaix .com为Banjori恶意软件），URL（例如http://109.162.38.120/harsh02.exe的已知恶意可执行文件），IP地址（例如已知攻击者的185.130.5.231）或HTTP User-Agent头值（例如sqlmap for automatic SQL注入和数据库接管工具）。 此外，它使用（可选）高级启发式机制，可以帮助发现未知威胁（例如新的恶意软件）。

使用的黑名单列表如下

```
alienvault, autoshun, badips, bambenekconsultingc2dns,
bambenekconsultingc2ip, bambenekconsultingdga, bitcoinnodes,
blocklist, botscout, bruteforceblocker, ciarmy, cruzit,
cybercrimetracker, deepviz, dataplanesipinvitation,
dataplanesipquery, dataplane, dshielddns, dshieldip, 
emergingthreatsbot, emergingthreatscip, emergingthreatsdns,
feodotrackerdns, malwaredomainlist, malwaredomains, malwarepatrol,
maxmind, myip, nothink, openbl, openphish, packetmailcarisirt,
packetmailramnode, palevotracker, policeman, proxylists, proxyrss,
proxy, ransomwaretrackerdns, ransomwaretrackerip,
ransomwaretrackerurl, riproxies, rutgers, sblam, securityresearch,
snort, socksproxy, sslipbl, sslproxies, torproject, torstatus,
turris, urlvir, voipbl, vxvault, zeustrackerdns, zeustrackerip,
zeustrackermonitor, zeustrackerurl, etc.
```

对于静态条目，已经手动包括以下恶意实体的路径

```
aboc, adwind, alienspy, almalocker, alureon, android_acecard, 
android_adrd, android_alienspy, android_arspam, 
android_backflash, android_basebridge, android_boxer, 
android_chuli, android_claco, android_coolreaper, 
android_counterclank, android_cyberwurx, android_dendoroid, 
android_dougalek, android_droidjack, android_droidkungfu, 
android_enesoluty, android_ewalls, android_exprespam, 
android_fakebanco, android_fakedown, android_fakeinst, 
android_fakelog, android_fakemart, android_fakemrat, 
android_fakeneflic, android_fakesecsuit, android_feabme, 
android_flexispy, android_frogonal, android_geinimi, 
android_ghostpush, android_ginmaster, android_gmaster, 
android_godwon, android_golddream, android_gonesixty, 
android_ibanking, android_kemoge, android_lockdroid, 
android_lovetrap, android_maistealer, android_maxit, 
android_oneclickfraud, android_opfake, android_ozotshielder, 
android_pikspam, android_pjapps, android_qdplugin, 
android_repane, android_roidsec, android_samsapo, 
android_sandorat, android_selfmite, android_simplocker, 
android_skullkey, android_sndapps, android_spytekcell, 
android_stealer, android_stels, android_teelog, android_tetus, 
android_tonclank, android_torec, android_uracto, 
android_usbcleaver, android_walkinwat, android_windseeker, 
android_zertsecurity, androm, andromem, angler, anuna, arec, 
aridviper, artro, autoit, avalanche, avrecon, axpergle, babar, 
bachosens, badblock, balamid, bamital, bankapol, bankpatch, 
banloa, banprox, bayrob, bedep, blackenergy, blackvine, 
blockbuster, bredolab, bubnix, bucriv, buterat, camerashy, 
carbanak, carberp, careto, casper, cerber, changeup, chanitor, 
chekua, cheshire, chewbacca, chisbur, cleaver, cloud_atlas, 
conficker, contopee, copykittens, corebot, cosmicduke, 
couponarific, criakl, cridex, crilock, cryakl, cryptinfinite, 
cryptodefense, cryptolocker, cryptowall, ctblocker, cutwail, 
darkhotel, defru, desertfalcon, destory, dnschanger, 
dnsmessenger, dnstrojan, dorifel, dorkbot, drapion, dridex, 
dukes, dursg, dyreza, elf_aidra, elf_billgates, elf_darlloz, 
elf_ekoms, elf_fysbis, elf_groundhog, elf_hacked_mint, 
elf_mayhem, elf_mokes, elf_pinscan, elf_rekoobe, elf_shelldos, 
elf_sshscan, elf_themoon, elf_turla, elf_xnote, elf_xorddos, 
elpman, emogen, emotet, equation, evilbunny, ewind, expiro, 
fakeav, fakeran, fantom, fareit, fbi_ransomware, fiexp, 
fignotok, fin4, finfisher, fraudload, fynloski, fysna, gamarue, 
gauss, gbot, generic, golroted, gozi, groundbait, harnig, 
hawkeye, helompy, hiloti, hinired, htran, immortal, injecto, 
ios_keyraider, ios_muda, ios_oneclickfraud, ios_specter, 
ismdoor, jenxcus, kegotip, keydnap, kingslayer, kolab, 
koobface, korgo, korplug, kovter, kradellsh, kulekmoko, 
lazarus, locky, lollipop, lotus_blossom, luckycat, majikpos, 
malwaremustdie, marsjoke, mdrop, mebroot, mestep, mhretriev, 
miniduke, misogow, modpos, morto, nanocor, nbot, necurs, 
nemeot, neshuta, nettraveler, netwire, neurevt, nexlogger, 
nivdort, nonbolqu, nuqel, nwt, nymaim, odcodc, oficla, onkods, 
optima, osx_keranger, osx_keydnap, osx_salgorea, 
osx_wirelurker, palevo, pdfjsc, pegasus, pepperat, phytob, 
picgoo, pift, plagent, plugx, ponmocup, poshcoder, potao, 
powelike, proslikefan, pushdo, pykspa, qakbot, quasar, ramnit, 
ransirac, reactorbot, redoctober, redsip, remcos, renocide, 
reveton, revetrat, rovnix, runforestrun, russian_doll, rustock, 
sakurel, sality, satana, sathurbot, scarcruft, scarletmimic, 
scieron, seaduke, sednit, sefnit, selfdel, shifu, shylock, 
siesta, silentbrute, silly, simda, sinkhole_abuse, 
sinkhole_anubis, sinkhole_arbor, sinkhole_bitdefender, 
sinkhole_blacklab, sinkhole_botnethunter, sinkhole_certgovau, 
sinkhole_certpl, sinkhole_checkpoint, sinkhole_cirtdk, 
sinkhole_conficker, sinkhole_cryptolocker, sinkhole_drweb, 
sinkhole_dynadot, sinkhole_dyre, sinkhole_farsight, 
sinkhole_fbizeus, sinkhole_fitsec, sinkhole_fnord, 
sinkhole_gameoverzeus, sinkhole_georgiatech, sinkhole_gladtech, 
sinkhole_honeybot, sinkhole_kaspersky, sinkhole_microsoft, 
sinkhole_rsa, sinkhole_secureworks, sinkhole_shadowserver, 
sinkhole_sidnlabs, sinkhole_sinkdns, sinkhole_sofacy, 
sinkhole_sugarbucket, sinkhole_tech, sinkhole_unknown, 
sinkhole_virustracker, sinkhole_wapacklabs, sinkhole_zinkhole, 
skeeyah, skynet, skyper, smsfakesky, snake, snifula, snort, 
sockrat, sofacy, sohanad, spyeye, stabuniq, stonedrill, 
stuxnet, synolocker, tdss, teamspy, teerac, teslacrypt, 
themida, tibet, tinba, torpig, torrentlocker, troldesh, turla, 
unruy, upatre, utoti, vawtrak, vbcheman, vinderuf, virtum, 
virut, vittalia, vobfus, volatilecedar, vundo, waledac, 
waterbug, wecorl, wndred, xadupi, xcodeghost, xtrat, yenibot, 
yimfoca, zaletelly, zcrypt, zemot, zeroaccess, zeus, zherotee, 
zlader, zlob, zombrari, zxshell, etc.
```

## 架构

Maltrail基于Traffic - > Sensor < - > Server < - >客户端架构。传感器是在监视节点上运行的独立组件（例如，Linux平台被动地连接到SPAN /镜像端口或在Linux桥上透明内联）或独立机器（例如，蜜罐），“独立机器”对于列入黑名单的项目/路径（即域名，URL和/或IP）。

在匹配的情况下，它会将事件详细信息发送到（中央）服务器，并将其存储在适当的日志记录目录（即配置部分中描述的LOG_DIR）中。

如果Sensor与Server（默认配置）在同一台机器上运行，则日志将直接存储到本地日志记录目录中。否则，它们将通过UDP消息发送到远程服务器（即配置部分中描述的LOG_SERVER）。

服务器的主要作用是存储事件详细信息，并为报告Web应用程序提供后端支持。在默认配置中，服务器和传感器将在同一台机器上运行。因此，为了防止传感器活动中的潜在中断，前端报告部分基于“胖客户端”架构（即所有数据后处理都在客户端的Web浏览器实例中进行）。

所选（24小时）期间的事件（即日志条目）被转移到客户端，报告网络应用程序对演示部分负责。数据以压缩块的形式发送给客户端，并按顺序进行处理。最终报告以高度浓缩的形式创建，实际上允许呈现几乎无限数量的事件。

注意：服务器组件可以完全跳过，只需使用独立的Sensor。在这种情况下，所有事件都将存储在本地日志记录目录中，而日志条目可以手动检查或通过一些CSV读取应用程序进行检查。

## Sensor运行流程

init
    create_log
    check_memory
    load_plugin
    init_multiprocessing
monitor
    packet_handler
        process_packet
            check_domain
            check_ua
            ...
            traverse_plugin
