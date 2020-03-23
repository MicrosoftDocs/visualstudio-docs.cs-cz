---
title: Poradce při potížích s emulátorem sady Visual Studio pro Android | Dokumenty společnosti Microsoft
ms.custom: ''
ms.prod: visual-studio-dev15
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: f3fb5df4-3aae-40e4-9450-bbe15b0c5af5
author: conceptdev
ms.author: crdun
manager: crdun
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 85a7748f25e284a7c746d5779b3d177a15e1d37b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77272069"
---
# <a name="troubleshoot-the-visual-studio-emulator-for-android"></a>Poradce při potížích s emulátorem sady Visual Studio pro Android
Toto téma obsahuje informace, které vám pomohou vyřešit problémy, které mohou narazíte při použití emulátoru Visual Studio pro Android.

> [!WARNING]
> Po instalaci emulátoru instalační program zkontroluje předpoklady pro spuštění softwaru. Zobrazí upozornění, pokud nejsou k dispozici požadavky, ale nevyžaduje je pro instalaci.

 Toto téma obsahuje tyto části:

- [Než začnete](#BeforeYouStart)

- [Emulátor se nepodaří nainstalovat](#NoInstall)

- [Nelze se připojit k síťovým cílům v doméně nebo podnikové síti.](#DomainNetwork)

- [Nelze se připojit k cílům sítě, pokud nastavení sítě vyžaduje ruční konfiguraci.](#ManualNetworkConfig)

- [Emulátor se spustí pomalu, nespustí se kvůli časovému výtce nebo se nasazení aplikace nezdaří.](#SlowStart)

- [Emulátor se nespustí](#NoStart2)

- [Emulátor se nespustí (první použití)](#NoStart)

- [Počítač se po instalaci emulátoru nespustí](#NoBoot)

- [Visual Studio uvízne při pokusu o nasazení aplikace do emulátoru nebo emulátor nezobrazí jako ladicí cíl v jiných IDE](#ADB)

- [Emulátor přestane reagovat, protože nelze nastavit port UDP.](#XamarinPlayer)

- [Ladicí program nelze připojit k projektu Xamarin.](#Skylake)

- [Emulátoru se nepodaří spustit aplikaci, která používá služby Google Play](#GooglePlay)

- [Přetažení souboru, souboru APK nebo flashable zip nefunguje](#DragAndDrop)

- [Rozlišení snímku obrazovky je nesprávné](#Resolution)

- [Emulátor nevykresluje obsah OpenGL](#OpenGL)

- [Emulátor nereaguje na vícedotyková gesta](#Multitouch)

- [Zdroje podpory](#Support)

## <a name="before-you-start"></a><a name="BeforeYouStart"></a>Než začnete
 Než začnete s odstraňováním potíží, může být užitečné zkontrolovat následující témata:

- [Systémové požadavky pro emulátor visual studio pro Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

## <a name="emulator-fails-to-install"></a><a name="NoInstall"></a>Emulátor se nepodaří nainstalovat
 Pokud nemáte nainstalovanou technologii Hyper-V, zobrazí se při pokusu o instalaci emulátoru následující zpráva. Musíte mít počítač, který podporuje HyperV a musí být povolen.

 ![Android&#95;Emu&#95;problém s&#95;instalací](../cross-platform/media/android_emu_install_issue.png "Android_Emu_Install_Issue")

> [!NOTE]
> Tato zpráva platí pro emulátor Visual Studio pro Android a Emulátor Windows Phone. Windows 8.1 a Windows 10 podporují emulátor.

 Pokud se zobrazí tato zpráva, zkontrolujte [systémové požadavky pro emulátor Visual Studio pro Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) a zjistěte, zda můžete spustit emulátor.

## <a name="cannot-connect-to-network-destinations-on-a-domain-or-corporate-network"></a><a name="DomainNetwork"></a>Nelze se připojit k síťovým cílům v doméně nebo podnikové síti.
 Emulátor visual studio pro Android se zobrazí v síti jako samostatné zařízení s vlastní IP adresou. Není připojen k doméně systému Windows a nesdílí pověření domény nebo pracovní skupiny s hostitelským počítačem.

 Pokud vaše síť vyžaduje autorizaci domény nebo pracovní skupiny pro základní připojení k síti a Internetu, požádejte o výjimku správce IT. Tato výjimka umožňuje vývojovému počítači sloužit jako hraniční počítač a přijímat připojení ze síťových zařízení, která nejsou připojena k doméně, jako je emulátor.

 Emulátor Visual Studio pro Android také používá vlastní sadu adres MAC. Pokud nemůžete získat přístup k síťovým nebo internetovým prostředkům z emulátoru, obraťte se na správce IT a ujistěte se, že adresy MAC emulátoru byly v síti autorizovány.

#### <a name="to-view-the-emulators-mac-addresses"></a>Zobrazení MAC adres emulátoru

1. Spusťte emulátor.

2. Na panelu nástrojů emulátoru otevřete klepnutím na tlačítko dvojité šipky (>>).

3. V okně Další nástroje klikněte na kartu Síť.

4. Na stránce Síť vyhledejte položky fyzické adresy.

## <a name="cannot-connect-to-network-destinations-when-network-settings-require-manual-configuration"></a><a name="ManualNetworkConfig"></a>Nelze se připojit k cílům sítě, pokud nastavení sítě vyžaduje ruční konfiguraci.
 Chcete-li se připojit k cílům sítě z emulátoru, musí síť splňovat následující požadavky:

- Dhcp. Emulátor vyžaduje službu DHCP, protože se konfiguruje jako samostatné zařízení v síti s vlastní adresou IP.

- Automaticky nakonfigurované nastavení DNS a brány. Pro emulátor není možné ručně konfigurovat nastavení DNS a brány.

  Pokud vaše síť vyžaduje ručně nakonfigurovaná nastavení, obraťte se na správce IT a zjistěte, jak můžete povolit připojení k síti pro emulátor.

## <a name="emulator-starts-slowly-fails-to-start-due-to-a-timeout-or-app-deployment-fails"></a><a name="SlowStart"></a>Emulátor se spustí pomalu, nespustí se kvůli časovému výtce nebo se nasazení aplikace nezdaří.
 Za určitých podmínek trvá spuštění emulátoru několik minut nebo se nespustí z důvodu časového oddlužení. Pokud se emulátor nespustí, zobrazí se `App deployment failed. Please try again`následující zpráva: . Následující podmínky může mít za následek tuto chybu.

- Spuštění emulátoru Visual Studio pro Android ze spouštěcího virtuálního pevného disku. Tato konfigurace není podporovaná.

- Vadný pevný disk. Zvažte spuštění programu chkdsk.

- Pevný disk, který je třeba defragmentovat. Zvažte defragmentaci jednotky.

- Pevný disk, který je téměř plný. Zkontrolujte volné místo na jednotce.

- Nedostatek paměti je k dispozici z důvodu jiných spuštěných aplikací. Snižte počet aplikací, které spotřebovávají paměť, nebo zvyšte množství paměti.

- Obecně platí, že jakýkoli faktor, který přispívá ke špatnému výkonu v systému. Začněte s odstraňováním potíží s komponentou, která má nejnižší dílčí skóre v indexu uživatelských zkušeností se systémem Windows, který najdete na stránce Informace o výkonu a nástroje v Ovládacích panelech.

## <a name="emulator-fails-to-start"></a><a name="NoStart2"></a>Emulátor se nespustí
 Pokud emulátor pracoval dříve, ale nefunguje nyní, projděte si následující úkoly. Pokud používáte emulátor poprvé, naleznete v [tématu emulátor se nezdaří spuštění (první použití)](#NoStart) před pokusem o tyto kroky.

- Odeberte všechny ostatní instance hyper-v emulátoru.

    1. Zavřete Visual Studio.

    2. Otevřete Správce technologie Hyper-V a zastavte všechny instance technologie Hyper-V emulátoru (virtuální počítače), které jsou již spuštěny a případně v poškozeném stavu.

    3. Ve Správci technologie Hyper-V odstraňte všechny ostatní virtuální virtuální aplikace emulátoru.

    4. Restartujte počítač.

- Ujistěte se, že máte alespoň 4 GB systémové paměti a že není spotřebována jinými programy a procesy náročnými na prostředky (zkuste například zavřít všechna okna prohlížeče).

- Ve Správci technologie Hyper-V otevřete Správce virtuálních přepínačů a zkontrolujte, zda máte dva síťové přepínače. ověřte, zda první je interní přepínač a druhý externí.

     ![Android&#95;Emu&#95;V&#95;Switch&#95;Man](../cross-platform/media/android_emu_v_switch_man.png "Android_Emu_V_Switch_Man")

     Pokud je instalace nesprávná a používáte Systém Windows 10, můžete se pokusit [přeinstalovat síťová zařízení pomocí příkazu netcfg -d](https://support.microsoft.com/help/10741/windows-fix-network-connection-issues) (oddíl 6).

- Pokud tyto kroky problém nevyřeší, naleznete [v tématu emulátor se nepodaří spustit (první použití)](#NoStart) informace o softwaru třetích stran, které mohou být rušivé v emulátoru.

## <a name="emulator-fails-to-start-first-use"></a><a name="NoStart"></a>Emulátor se nespustí (první použití)
 Pokud se emulátor nespustí, projděte následující úkoly k identifikaci a vyřešení problému.

- Zkontrolujte, zda jsou splněny minimální požadavky na hardware a zda jsou nastavení systému BIOS správná.

   Emulátor a Windows 8 Hyper-V vyžadují 64bitový procesor s překladem adres druhé úrovně (SLAT). Pro Intel v podstatě potřebujete procesor Core i3, i5 nebo i7 (nebo jeden z mnoha Xeons). Seznam Čipů AMD je k dispozici [zde](https://www.amd.com/en/support).

  1. Zkontrolujte, zda počítač splňuje [systémové požadavky](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md).

  2. Ověřte, zda [nástroj SLAT](https://slatstatuscheck.codeplex.com/) hlásí, že váš počítač je schopen SLAT.

  3. V rámci nastavení systému BIOS počítače zkontrolujte, zda je povolena veškerá technologie virtualizace. Přesné popisy systému BIOS se mohou u každého výrobce hardwaru lišit. Obecně povolte funkce související s:

     - SLAT (překlad adresy druhé úrovně)

     - EPT (rozšířené stránkovací tabulky) (Intel)

     - NPT (vnořené stránkovací tabulky) (AMD)

     - RVI (rychlé indexování virtualizace) (AMD)

     - VMX (zkratka Intel označující podporu virtualizace s podporou virtualizace s hardwarovou podporou)

     - SVM (zkratka AMD označující podporu virtualizace s podporou virtualizace s hardwarovou podporou)

     - XD (Spustit zakázat) (Intel); to musí být povoleno

     - NX (Bez spuštění)(AMD); to musí být povoleno.

  4. Pokud jsou v systému BIOS k dispozici následující možnosti, zakažte je.

     - Zakázání technologie Intel VT-d

     - Zakázat důvěryhodné spuštění

       Další informace naleznete v tomto článku: Technet: Hyper-V: Jak opravit chyby systému BIOS umožňující technologie Hyper-V

  5. Ujistěte se, že máte alespoň 4 GB systémové paměti a že není spotřebována jinými programy a procesy náročnými na prostředky.

  6. Zkontrolujte, zda používáte systém Windows 8 Professional nebo vyšší (systém Windows Server 2008 není podporován). Windows Server 2012 je podporovaný, ale je nutné povolit možnosti plochy.

     Můžete zkontrolovat Prohlížeč událostí a zjistit, zda se nezobrazují chyby hypervisoru. Chcete-li to provést, otevřete Prohlížeč `eventvwr`událostí ( Start**key**+**R**, potom zadejte ) a vyberte **windows protokoly**, **systém**. Potom filtrujte protokol podle zdroje událostí a nastavte zdroj na **Hyper-V-Hypervisor**. Zkontrolujte chyby, které pomáhají identifikovat hlavní příčinu.

     Pokud váš procesor splňuje minimální požadavky, ale hypervisor stále selhává, zvažte zjištění, zda je pro váš počítač k dispozici upgrade systému BIOS. Pokud existuje a rozhodnete se provést upgrade, dodržujte při upgradu systému BIOS všechna opatření výrobce (například ujistěte se, že upgrade firmwaru systému BIOS není přerušen ztrátou napájení, která může trvale poškodit systém BIOS).

- Ujistěte se, že máte alespoň 4 GB systémové paměti a že není spotřebována jinými programy a procesy náročnými na prostředky.

- Odeberte nebo zakažte ovladače nebo software třetích stran, který může rušit virtuální síť.

   Existují některé známé problémy s některými produkty třetích stran nainstalovanými v systému Windows 8, jako jsou síťové ovladače nebo protokoly, které nejsou plně kompatibilní se síťovým zásobníkem Technologie Hyper-V.

   Obecně platí, že bude na vývojářích těchto produktů, aby aktualizovali svůj software tak, aby byl kompatibilní se systémy Windows 8 a Hyper-V.

   Následující produkty mohou vyžadovat upgrade pro dodržování předpisů ve Windows 8: VirtualBox, Virtual PC 7, VMWare, někteří klienti VPN, softwarové brány firewall, některé verze klientů Cisco VPN a další virtualizační systémy. Spolupracujte s vývojářem sporného virtualizačního softwaru a povzbuďte je k upgradu softwaru tak, aby byl kompatibilní se systémy Windows 8 a Hyper-V.

   Jako *řešení*můžete zakázat všechny ovladače a aplikace třetích stran, které mohou rušit virtuální síť používanou emulátorem ke komunikaci s aplikací Visual Studio. Tyto žádosti mohou zahrnovat:

  - Antivirové aplikace (které se zavěsí do síťového zásobníku)

  - Nástroje pro sledování sítě

  - Nástroje pro protokolování sítě

  - Jiný software pro sledování systému

    Dalším možným zástupným řešením, které nechybí odinstalování daného produktu (a požadavek, aby vývojář produktu vydal aktualizovanou verzi), je provést následující kroky.

  1. Spusťte Správce síťových připojení (na úvodní obrazovce zadejte `View Network Connections` a vyberte tuto možnost, chcete-li síťová připojení zobrazit.)

  2. Pro adaptér vEthernet (Interní ethernetový port Windows Phone Emulátor interní přepínač) zvolte **Vlastnosti** z kontextové nabídky.

      ![Virtuální adaptér používaný hyper&#45;V](../cross-platform/media/android_emu_virtual_adapter.png "Android_Emu_Virtual_Adapter")

      Zde jsou zobrazeny vlastnosti adaptéru.

      ![Vlastnosti virtuálního adaptéru](../cross-platform/media/android_emu_virtual_adapter_properties.png "Android_Emu_Virtual_Adapter_Properties")

  3. Pro tento adaptér pouze položky, které by měly být vybrány v části **Toto připojení používá následující položky** by měly být následující:

     - Klient sítě Microsoft

     - Plánovač paketů QoS

     - Sdílení souborů a tiskáren v sítích Microsoft

     - Ovladač protokolu LLDP společnosti Microsoft

     - Ovladač i/O mapovači mapovače topologie propojení

     - Respond i pro zjišťování topologie linkové vrstvy

     - Protokol IP verze 6 (TCP/IPv6)

     - Protokol IP verze 4 (TCP/IPv4)

  4. Odznačte všechny ostatní položky.

     Nevýhodou použití této techniky je, že kdykoli nový produkt třetí strany nainstaluje nepodporované ovladače nebo kdykoli je emulátor nainstalován, bude nutné tyto kroky opakovat.

     Po odinstalování produktů třetích stran možná budete muset obnovit interní přepínač emulátoru Windows Phone. Postup:

  - Otevřete Hyper V a přejděte do Správce virtuálních přepínačů. Vytvořte virtuální přepínač s názvem "Windows Phone Emulator Internal Switch" a nastavte jeho typ připojení k **interní síti**.

     ![Správce virtuálních přepínačů](../cross-platform/media/android_emu_virtual_switch_manager.png "Android_Emu_Virtual_Switch_Manager")

    Nyní spusťte emulátor. Mělo by to fungovat.

## <a name="computer-fails-to-boot-after-installing-the-emulator"></a><a name="NoBoot"></a>Počítač se po instalaci emulátoru nespustí
 K tomuto problému může dojít, pokud jsou splněny následující podmínky:

- Počítač má základní desku Gigabyte.

- USB3 je povolena na základní desce.

  Chcete-li tento problém vyřešit, zakažte USB3 v nastavení systému BIOS základní desky a restartujte počítač. Pak zkontrolujte, zda Gigabyte vydala aktualizaci pro bios základní desky.

  Další informace naleznete v následujícím článku znalostní báze Knowledge Base: [Selhání spuštění po instalaci role Hyper-V v systémech Gigabyte](https://support.microsoft.com/en-us/kb/2693144).

## <a name="visual-studio-gets-stuck-trying-to-deploy-the-app-to-the-emulator-or-the-emulator-does-not-appear-as-a-debug-target-in-other-ides"></a><a name="ADB"></a>Visual Studio uvízne při pokusu o nasazení aplikace do emulátoru nebo emulátor nezobrazí jako ladicí cíl v jiných IDE
 Pokud je emulátor spuštěn, ale nezdá se, že je připojen k ADB (Android Debug Bridge) nebo se nezobrazí v nástrojích Android, které využívají ADB (například Android Studio nebo Eclipse), možná budete muset upravit, kde emulátor hledá ADB. Emulátor používá klíč registru k identifikaci základního umístění sady Android SDK a vyhledá soubor \platform-tools\adb.exe pod tímto adresářem. Chcete-li upravit cestu sady Android SDK používanou emulátorem:

- Otevřete Editor registru **Run** tak, že vyberete Spustit `regedit` z kontextové nabídky Tlačítka Start, zadáte do dialogového okna a zvolíte **OK**.

- Přejděte do *HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Android SDK Tools* ve stromu složek vlevo.

- Upravte proměnnou **registru cesta** tak, aby odpovídala cestě k androids ddk.

  Restartujte emulátor a nyní byste měli být schopni vidět emulátor připojený k ADB a přidruženým nástrojům Android.

## <a name="emulator-hangs-because-it-couldnt-set-up-the-udp-port"></a><a name="XamarinPlayer"></a>Emulátor přestane reagovat, protože nelze nastavit port UDP.
 K tomuto problému může dojít z důvodu nekompatibility s přehrávačem Xamarin. Pokud se zdá, že emulátor přestane reagovat nebo pokud se zobrazí tato chybová zpráva, "Emulátor se nemůže připojit k operačnímu systému zařízení: Nelze nastavit port UDP.  Některé funkce mohou být zakázány", může dojít k tomuto problému. Postupujte podle následujících kroků.

1. Odinstalujte přehrávač Xamarin.

2. Ověřte, zda byl virtuální rámeček odebrán (přehrávač Xamarin běží nad virtuálním boxem).

3. Přejděte do Správce zařízení, vyberte možnost zobrazení skrytých zařízení a pak odstraňte vše kromě fyzických síťových karet.

4. Po odebrání nefyzických síťových adaptérů můžete zkusit odinstalovat nebo přeinstalovat technologii Hyper-V.

## <a name="cannot-attach-debugger-to-a-xamarin-project"></a><a name="Skylake"></a>Ladicí program nelze připojit k projektu Xamarin.
 Pokud používáte Windows 10 s procesory Intel Skylake, aplikace Xamarin nemusí selhat ke spuštění v emulátoru nebo visual studio ladicí program nemusí připojit k nim. To je způsobeno problémem s procesory Hyper-V a Skylake. Jako řešení postupujte podle následujících kroků.

1. Otevřete Správce technologie Hyper-V a vyberte virtuální počítač pro profil emulátoru, který používáte.

2. Vyberte **Odstranit uložený stav** (vpravo dole).

3. Zvolte **Nastavení...**

4. Rozbalte uzel procesoru a zvolte **Kompatibilita**.

5. Povolit **migraci do fyzického počítače s jinou verzí procesoru**.

6. Restartujte službu (v části **Akce)** a akci opakujte.

## <a name="emulator-fails-to-run-app-that-uses-google-play-services"></a><a name="GooglePlay"></a>Emulátoru se nepodaří spustit aplikaci, která používá služby Google Play
 Emulátor se nedoručuje s knihovnami služeb Google Play. Emulátor však podporuje instalaci flashable zip souborů.

## <a name="drag-and-drop-of-a-file-apk-or-flashable-zip-file-does-not-work"></a><a name="DragAndDrop"></a>Přetažení souboru, souboru APK nebo flashable zip nefunguje
 Emulátor používá ADB.exe k usnadnění přenosu souborů při přetažení souboru na obrazovku. Pokud při pokusu o přetažení souboru narazíte na chybu, pravděpodobně to znamená, že emulátor není připojen k souboru ADB.exe. Chcete-li vyřešit, postupujte podle kroků v [sadě Visual Studio uvízne při pokusu o nasazení aplikace do emulátoru nebo emulátor nezobrazí jako ladicí cíl v jiných IDE](#ADB).

## <a name="resolution-of-screenshot-is-incorrect"></a><a name="Resolution"></a>Rozlišení snímku obrazovky je nesprávné
 Pokud pořídíte snímek obrazovky pomocí karty Snímek obrazovky v okně **Další nástroje** a výsledný obrázek má neočekávanou velikost, bude pravděpodobně nutné upravit úroveň zvětšení obrazovky před výběrem **možnosti Zachytit**. Emulátor pořizuje snímky obrazovky v rozlišení obrazovky na monitoru hostitelského počítače.

## <a name="emulator-fails-to-render-opengl-content"></a><a name="OpenGL"></a>Emulátor nevykresluje obsah OpenGL
 Emulátor vykresluje obsah OpenGL pomocí GPU hostitelského počítače a používá projekt ANGLE k převodu těchto volání do a z DirectX. Pokud vaše aplikace vykreslí správně na zařízení, ale nesprávně na emulátoru, je pravděpodobné, že zařízení je zmírnění nesprávné OpenGL volání (například pomocí shader proměnné, které se neshodují).

## <a name="emulator-does-not-respond-to-multi-touch-gestures"></a><a name="Multitouch"></a>Emulátor nereaguje na vícedotyková gesta
 V některých případech se emulátor spustí a nebude reagovat na vícedotykové ovládání buď přímou interakcí z dotykového displeje nebo pomocí nástroje Multi-Touch Tool na panelu nástrojů emulátoru. V takovém případě zvolte tlačítko **Otočit** na panelu nástrojů emulátoru a pokuste se znovu použít vícedotykové ovládání. Pokud problém přetrvává, přečtěte si [emulátor nepodaří vykreslit problém s obsahem OpenGL.](#OpenGL)

## <a name="support-resources"></a><a name="Support"></a>Zdroje podpory
 Pokud hostitelský počítač splňuje systémové požadavky a narazíte na problém, který není uveden v této příručce pro řešení potíží:

- Zeptejte se na StackOverflow pomocí [android-emulátor](https://stackoverflow.com/questions/tagged/android-emulator) a visual-studio tagy.

- Nahlaste problém pomocí nástroje Odeslat úsměv v sadě Visual Studio nebo ve Správci emulátorů.
