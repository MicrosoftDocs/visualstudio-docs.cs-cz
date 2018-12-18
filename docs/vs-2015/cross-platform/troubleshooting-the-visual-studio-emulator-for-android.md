---
title: Poradce při potížích s emulátorem pro Android | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3fb5df4-3aae-40e4-9450-bbe15b0c5af5
caps.latest.revision: 25
ms.author: crdun
manager: crdun
ms.openlocfilehash: c1d8310cb2585dfd2041ce25fd4301b557521911
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068228"
---
# <a name="troubleshooting-the-visual-studio-emulator-for-android"></a>Poradce při potížích s emulátorem sady Visual Studio pro Android
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Toto téma obsahuje informace, které pomáhají při řešení problémů, které mohou nastat při používání Visual Studio Emulator for Android.

> [!WARNING]
>  Po nainstalování emulátoru, instalační program zkontroluje požadavky pro spuštění softwaru. Upozornění se zobrazí, pokud požadavky nejsou k dispozici, ale ta je není nutné pro instalaci.

 Toto téma obsahuje následující části.

-   [Než začnete](#BeforeYouStart)

-   [Emulator se nenainstaluje](#NoInstall)

-   [Nejde se připojit k síti cíle v doméně nebo v podnikové síti](#DomainNetwork)

-   [Nejde se připojit k síti cíle při vyžadují ruční konfiguraci nastavení sítě](#ManualNetworkConfig)

-   [Spuštění emulátoru pomalu, se nedaří spustit z důvodu vypršení časového limitu nebo selhání nasazení aplikace](#SlowStart)

-   [Emulátor se nepodaří spustit](#NoStart2)

-   [Emulátor se nepodaří spustit (první použití)](#NoStart)

-   [Nepodaří spustit po nainstalování emulátoru](#NoBoot)

-   [Visual Studio zasekne při pokusu o nasazení aplikace na emulátoru nebo emulátor se nezobrazí jako cíl ladění ve jiná Integrovaná vývojová prostředí](#ADB)

-   [Emulátor přestane reagovat, protože ji nelze nastavit UDP port](#XamarinPlayer)

-   [Nelze připojit ladicí program na projekt Xamarin](#Skylake)

-   [Emulátor se nepodaří spustit aplikaci, která využívá služby Google Play](#GooglePlay)

-   [Přetažení souboru, APK nebo soubor aktualizačního souboru zip nefunguje](#DragAndDrop)

-   [Rozlišení obrazovky je nesprávný](#Resolution)

-   [Emulátor se nepodaří zpracovat obsah OpenGL](#OpenGL)

-   [Emulátor neodpovídá na gesta více dotyků](#Multitouch)

-   [Informační zdroje podpory](#Support)

##  <a name="BeforeYouStart"></a> Než začnete
 Než začnete řešit potíže, může být užitečné v následujících tématech:

-   [Systémové požadavky pro emulátor sady Visual Studio pro Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

##  <a name="NoInstall"></a> Emulator se nenainstaluje
 Pokud nemáte nainstalovanou technologii Hyper-V, zobrazí se následující zpráva při pokusu o instalaci emulátoru. Musíte mít počítač, který podporuje Hyper-v a musí být povolené.

 ![Android&#95;Emu&#95;Install&#95;Issue](../cross-platform/media/android-emu-install-issue.png "Android_Emu_Install_Issue")

> [!NOTE]
>  Tato zpráva platí jak pro Visual Studio Emulator for Android a emulátor Windows Phone. Windows 8.1 a Windows 10 podporovat emulátor.

 Pokud se zobrazí tato zpráva, zkontrolujte, [požadavky na systém pro Visual Studio Emulator for Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) chcete zobrazit, zda lze spustit emulátor.

##  <a name="DomainNetwork"></a> Nejde se připojit k síti cíle v doméně nebo v podnikové síti
 Visual Studio Emulator for Android se zobrazí v síti jako samostatný zařízení pomocí jeho vlastní IP adresu. Není připojený k doméně Windows a nesdílí přihlašovací údaje domény nebo pracovní skupině se hostitelský počítač.

 Pokud síť vyžaduje ověřování domény nebo pracovní skupiny pro základní síť a připojení k Internetu, obraťte se na správce IT se pro výjimku. Tato výjimka umožňuje vývojovém počítači, který bude sloužit jako počítač hranice a tak, aby přijímal připojení ze zařízení není připojené k doméně sítě jako emulátor.

 Visual Studio Emulator for Android také využívá vlastní sadu adresy MAC. Pokud nemůžete použít síť nebo internetovým prostředkům z emulátoru serveru, obraťte se na správce IT, abyste měli jistotu, že jsou adresy MAC v emulátoru autorizovaná ve vaší síti.

#### <a name="to-view-the-emulators-mac-addresses"></a>Chcete-li zobrazit v emulátoru MAC adresy

1.  Spusťte emulátor.

2.  Na panelu nástrojů emulátor, klikněte na tlačítko s dvojitou šipkou (>>) Chcete-li otevřít v okně Další nástroje.

3.  V okně Další nástroje klikněte na kartu síť.

4.  Na stránce sítě vyhledejte položky fyzickou adresu.

##  <a name="ManualNetworkConfig"></a> Nejde se připojit k síti cíle při vyžadují ruční konfiguraci nastavení sítě
 Pro připojení k síti cíle z emulátoru serveru, musí vaše síť splňovat následující požadavky:

- DHCP. Emulátor vyžaduje DHCP, protože samotný nakonfiguruje jako samostatnou zařízení v síti s jeho vlastní IP adresu.

- Automaticky nakonfigurované DNS a nastavení brány. Není možné konfigurovat nastavení DNS a bránu ručně pro emulátor.

  Pokud síť vyžaduje ručně nakonfigurované nastavení, obraťte se na správce IT k určení, jak můžete zajistit připojení k síti pro emulátor.

##  <a name="SlowStart"></a> Spuštění emulátoru pomalu, se nedaří spustit z důvodu vypršení časového limitu nebo selhání nasazení aplikace
 Za určitých podmínek emulátor trvá několik minut nebo nepodaří spustit z důvodu vypršení časového limitu. Když emulátor nepodaří spustit, zobrazí se následující zpráva: `App deployment failed. Please try again`. Následující podmínky může vést k této chybě.

-   Spuštění emulátoru Visual Studia pro Android z spouštěcí virtuální pevný disk. Tato konfigurace není podporována.

-   Chybný pevný disk. Zvažte spuštění programu chkdsk.

-   Pevný disk, který je potřeba defragmentovat. Vezměte v úvahu defragmentace jednotce.

-   Pevný disk, který je téměř plná. Kontrola místa na jednotce.

-   Nedostatek paměti je k dispozici z důvodu ostatní spuštěné aplikace. Snížení počtu aplikací, které spotřebovávají paměť nebo zvětšete velikost paměti.

-   Obecně platí všechny faktorem, který přispívá ke špatnému výkonu v systému. Začněte řešit potíže se součástí, která má nejnižší skóre v indexu prostředí Windows, které můžete vyhledat na stránce informace o výkonu a nástrojů ovládacích panelů.

##  <a name="NoStart2"></a> Emulátor se nepodaří spustit
 Pokud emulátor fungovala předtím, ale teď nefunguje, projděte si následující úlohy. Pokud používáte emulátor poprvé, přečtěte si téma [emulátoru se nepodaří spustit (první použití)](#NoStart) před provedením těchto kroků.

-   Odeberte ostatní instance Hyper-V emulátoru.

    1.  Zavřete Visual Studio.

    2.  Otevřete Správce technologie Hyper-V a zastavte všechny instance Hyper-V emulátoru (virtuální počítače), která už jsou spuštěné a případně v poškozeném stavu.

    3.  Ve Správci technologie Hyper-V odstraňte všechny ostatní emulátor virtuálních počítačů.

    4.  Po restartování počítače.

-   Ujistěte se, že máte alespoň 4 GB systémové paměti a že není se využívat v jiných prostředků náročné programy a procesů (např. Zkuste zavřít všechna okna prohlížeče).

-   Ve Správci technologie Hyper-V otevřete Správce virtuálních přepínačů a zkontrolujte, zda máte dvě síťové přepínače; Ověřte, že první z nich je interní přepínač a druhý je externí.

     ![Android&#95;Emu&#95;V&#95;Switch&#95;Man](../cross-platform/media/android-emu-v-switch-man.png "Android_Emu_V_Switch_Man")

     Instalační program je nesprávný a používáte Windows 10, může pokusit se [přeinstalovat síťová zařízení pomocí příkazu – d netcfg](http://windows.microsoft.com/windows-10/fix-network-connection-issues) (část 6).

-   Pokud těchto kroků problém nevyřeší, přečtěte si téma [emulátoru se nepodaří spustit (první použití)](#NoStart) o 3. stran software, který může být zasahovala do emulátoru.

##  <a name="NoStart"></a> Emulátor se nepodaří spustit (první použití)
 Pokud emulátor nespustí, projděte si následující úkoly a identifikovat a opravit tento problém.

- Ujistěte se, že jsou splněny minimální požadavky na hardware a správnost nastavení systému BIOS.

   Emulátor a Windows 8 Hyper-V vyžaduje 64bitový procesor s druhou překlad adres úrovně (SLAT). Pro Intel musíte v podstatě Core i3 i5 nebo i7 procesoru (nebo jeden z mnoha Xeons). Je k dispozici seznam AMD čipy [tady](http://support.amd.com/en-us).

  1. Ujistěte se, že váš počítač splňuje [požadavky na systém](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md).

  2. Ověřte, že [SLAT nástroj](https://slatstatuscheck.codeplex.com/) hlásí, že je počítač podporuje technologii SLAT.

  3. V rámci nastavení systému BIOS v počítači Ujistěte se, že je povoleno všechny technologie virtualizace. Pro každého výrobce hardwaru se můžou lišit přesné popisy systému BIOS. Obecně platí povolte funkce související s:

     -   SLAT (překladu adres druhé úrovně)

     -   EPT (Extended Page Tables) (Intel)

     -   NPT (vnořené Page Tables) (AMD)

     -   RVI (Rapid Virtualization Indexing) (AMD)

     -   VMX (zkratka Intel označující podpora virtualizace s hardwarovým řízením)

     -   SVM (zkratka AMD označující podpora virtualizace s hardwarovým řízením)

     -   XD (spuštění zakázat) (Intel); Tato možnost musí být povolena

     -   NX (žádné Execute)(AMD); Toto musí být povolena.

  4. Pokud tyto možnosti jsou k dispozici v systému BIOS, je zakážete.

     - Zakázat Intel VT-d

     - Zakázat Trusted Execution

       Další informace najdete v tomto článku: Technet: jak Hyper-V: na oprava systému BIOS chyby povolení Hyper-V

  5. Ujistěte se, že máte alespoň 4 GB systémové paměti a že není právě využívat v jiných prostředků náročné aplikace a procesy.

  6. Zkontrolujte, že se systémem Windows 8 Professional nebo vyšší (Windows Server 2008 se nepodporuje). Windows Server 2012 je podporována, ale je nutné povolit desktopové prostředí.

     Můžete si prohlédnout Prohlížeč událostí, jestli jsou všechny chyby hypervisoru. Chcete-li to provést, otevřete Prohlížeč událostí (počáteční klíč + R a potom zadejte `eventvwr`) a pak vyberte **protokoly Windows**, **systému**. Vyfiltrujte v protokolu podle zdroje události nastavení zdroje na **Hyper-V hypervisoru**. Vyhledejte chyby vám pomůže identifikovat hlavní příčinu.

     Pokud váš procesor splňuje minimální požadavky, ale hypervisor stále nedaří, zvažte hledání na co si je upgrade systému BIOS dostupné pro váš počítač. Pokud existuje, a vy zvolíte upgradovat, je nutné sledovat všechna opatření od výrobce, při upgradu systému BIOS (jako je zajištění upgrade firmwaru systému BIOS není přerušení kvůli výpadku napájení, který může poškodit trvale systému BIOS).

- Ujistěte se, že máte alespoň 4 GB systémové paměti a že není právě využívat v jiných prostředků náročné aplikace a procesy.

- Odebrat nebo zakázat ovladačů jiných výrobců nebo software, který může být zasahovala do virtuální sítě.

   Existují některé známé problémy s některými 3. stran produkty nainstalované v systému Windows 8 například síťové ovladače a protokoly, které nejsou plně kompatibilní s Hyper-V síťového zásobníku.

   Obecně platí bude až vývojářům tyto produkty se aktualizace softwaru se kvůli kompatibilitě s Windows 8 a technologie Hyper-V.

   Následující produkty mohou vyžadovat upgradování pro dodržování předpisů pro Windows 8: VirtualBox, virtuální počítače VMWare, 7 někteří klienti VPN software brány firewall, některé verze klientů Cisco VPN a dalšími systémy virtualizace. Spolupracovat s vývojáři sporná virtualizačního softwaru Doporučte jim upgrade softwaru, aby byl kompatibilní s Windows 8 a technologie Hyper-V.

   Jako **řešení**, zakážete všechny aplikace, které mohou být zasahovala do virtuální sítě pomocí emulátoru ke komunikaci s aplikací Visual Studio a ovladačů jiných výrobců. Tyto aplikace mohou zahrnovat:

  - Antivirové aplikace (které integrovat do síťových protokolů)

  - Nástroje pro monitorování sítě

  - Nástroje protokolování sítě

  - Monitorovací software jiných systému

    Jiné možných alternativních nemá odinstalaci produktů dotaz (a žádosti o produktu pro vývojáře k uvolnění aktualizovanou verzi), je provést následující kroky.

  1. Spusťte Správce připojení k síti (na obrazovce Start zadejte `View Network Connections` a vyberte tuto možnost, chcete-li zobrazit síťová připojení.)

  2. Pro adaptér vEthernet (interní Port Windows Phone Emulator interní přepínač Ethernet) vyberte **vlastnosti** v místní nabídce.

      ![Virtuální adaptér používá Hyper&#45;V](../cross-platform/media/android-emu-virtual-adapter.png "Android_Emu_Virtual_Adapter")

      Zde jsou zobrazeny vlastnosti adaptéru.

      ![Vlastnosti virtuálního adaptéru](../cross-platform/media/android-emu-virtual-adapter-properties.png "Android_Emu_Virtual_Adapter_Properties")

  3. Pro tento adaptér pouze položky, které by měl být zvolena možnost **toto připojení používá následující položky** by měl být následující:

     -   Klient sítě Microsoft

     -   Plánovač paketů technologie QoS

     -   Sdílení souborů a tiskáren v sítích Microsoft

     -   Ovladač Microsoft LLDP protokolu

     -   Ovladač vstupně-výstupních operací mapovače zjišťování topologie linkové vrstvě

     -   Respondér zjišťování topologie linkové vrstvě

     -   Internet Protocol verze 6 (TCP/IPv6)

     -   Protokol IP verze 4 (TCP/IPv4)

  4. Zrušte výběr další položky.

     Nevýhodou použití této techniky je, že kdykoli nový 3. stran produkt instaluje nepodporované ovladače nebo pokaždé, když nainstalování emulátoru těchto kroků bude nutné jej opakovat.

     Po odinstalování serveru produkty třetích stran, budete muset obnovit interní přepínač emulátoru Windows Phone. Postup:

  - Otevřete Hyper-V a přejděte do Správce virtuálního přepínače. Vytvořit virtuální přepínač s názvem "Windows Phone Emulator interní přepínač" a nastavte její typ připojení na **interní síti**.

     ![Správce virtuálních přepínačů](../cross-platform/media/android-emu-virtual-switch-manager.png "Android_Emu_Virtual_Switch_Manager")

    Nyní spusťte emulátor. Mělo by to fungovat.

##  <a name="NoBoot"></a> Nepodaří spustit po nainstalování emulátoru
 Tomuto problému může dojít, pokud jsou splněny následující podmínky:

- Počítač se základní desky GB.

- USB3 je povolena na základní desce.

  Chcete-li tento problém vyřešit, zakažte USB3 v nastavení systému BIOS základní desky a restartujte počítač. Zkontrolujte, zda GB vydala aktualizace systému BIOS základní desky.

  Další informace najdete v tématu v následujícím článku znalostní báze Knowledge Base: [spouštěcí selhání po instalaci role Hyper-V v systémech GB](https://support.microsoft.com/en-us/kb/2693144).

##  <a name="ADB"></a> Visual Studio zasekne při pokusu o nasazení aplikace na emulátoru nebo emulátor se nezobrazí jako cíl ladění ve jiná Integrovaná vývojová prostředí
 Pokud je spuštěný emulátor, ale nezobrazí se chcete připojit k ADB (Android Debug Bridge) nebo se nezobrazují v nástroje pro Android, která využívají ADB (Android Studio nebo Eclipse), budete muset upravit, kde emulátor hledá ADB. Emulátor používá klíč registru pro určení základní umístění sady Android SDK a hledá soubor \platform-tools\adb.exe v tomto adresáři. Chcete-li změnit cesta sady Android SDK používaná emulátorem:

- Otevřete Editor registru tak, že vyberete **spustit** z místní nabídky Start tlačítka zadáním `regedit` v dialogovém okně a zvolíte **OK**.

- Přejděte do HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Android SDK Tools ve stromové struktuře složek na levé straně.

- Upravit **cesta** proměnnou registru tak, aby odpovídaly cestu k vaší sady Android SDK.

  Restartujte emulátor a byste teď měli zobrazíte emulátor připojen k ADB a související nástroje pro Android.

##  <a name="XamarinPlayer"></a> Emulátor přestane reagovat, protože ji nelze nastavit UDP port
 Tento problém z důvodu nekompatibility s Xamarin Playerem může docházet. Pokud se zobrazí emulátor přestane reagovat, nebo pokud se zobrazí tato chybová zpráva "nelze se připojit k operační systém zařízení je emulátor: Nelze nastavit UDP port.  Některé funkce můžou být zakázané", může dojít k tomuto problému. Proveďte následující kroky.

1.  Odinstalujte Xamarin Playeru.

2.  Ověřte, že tohoto virtuálního pole byla odebrána (Xamarin Playeru se spouští nad virtuální pole).

3.  Přejděte do Správce zařízení, vyberte možnost Zobrazit skrytá zařízení a odstraňte všechno kromě fyzické síťové karty.

4.  Můžete vyzkoušet, odinstalace a opětovné instalace technologie Hyper-V po odebrání všech jiných fyzických síťových adaptérů.

##  <a name="Skylake"></a> Nelze připojit ladicí program na projekt Xamarin
 Pokud používáte Windows 10 s procesory Intel Skylake, aplikace Xamarin se nemusí podařit spustit v emulátoru nebo k nim nemusí připojit ladicí program sady Visual Studio. Toto je kvůli problému s Hyper-V a Skylake procesory. Jako alternativní řešení proveďte následující kroky.

1.  Otevřete Správce technologie Hyper-V a vyberte virtuální počítač pro emulátor profil, který se pomocí.

2.  Vyberte **odstranit uložený stav** (vpravo dole).

3.  Zvolte **nastavení...**

4.  Rozbalte uzel procesoru a zvolte **kompatibility**.

5.  Povolit **migrovat do fyzického počítače s jinou verzí procesoru**.

6.  Restartujte službu (v části **akce**) a zkuste to znovu.

##  <a name="GooglePlay"></a> Emulátor se nepodaří spustit aplikaci, která využívá služby Google Play
 Emulátor se nedodává s knihovny služby Google Play. Emulátor však nepodporuje instalaci a přetažení aktualizačního souboru zip souborů.

##  <a name="DragAndDrop"></a> Přetažení souboru, APK nebo soubor aktualizačního souboru zip nefunguje
 Emulátor používá ADB.exe pro usnadnění přenos souborů, když přetahujete souboru na obrazovku. Pokud narazíte na chybu při pokusu o přetažení souboru, to pravděpodobně znamená, že není emulátor připojen k ADB.exe. Pokud chcete vyřešit, postupujte podle kroků v [sady Visual Studio zasekne při pokusu o nasazení aplikace na emulátoru nebo emulátor se nezobrazí jako cíl ladění ve jiná Integrovaná vývojová prostředí](#ADB).

##  <a name="Resolution"></a> Rozlišení obrazovky je nesprávný
 Pokud můžete pořídit snímek obrazovky na kartě snímek obrazovky v **dalších nástrojů** okno a výsledná bitová kopie má neočekávanou velikost, může být potřeba upravit úroveň zvětšení obrazovky před výběrem **zachycení**. Emulátor trvá snímky obrazovky na rozlišení obrazovky na monitoru hostitelský počítač.

##  <a name="OpenGL"></a> Emulátor se nepodaří zpracovat obsah OpenGL
 Emulátor vykreslí obsah OpenGL pomocí hostitelský počítač GPU a používá úhel projektu pro převod těchto volání do a z rozhraní DirectX. Pokud vaše aplikace správně vykresluje na zařízení ale nesprávně v emulátoru, je pravděpodobné, že zařízení je snížení rizik souvisejících s nesprávné volání OpenGL (například pomocí proměnné shaderu, které se neshodují s).

##  <a name="Multitouch"></a> Emulátor neodpovídá na gesta více dotyků
 V některých případech se emulátor spustí a nereaguje na více dotyků buď prostřednictvím přímé interakce ze zobrazení dotykově ovládaný nebo pomocí nástroje více dotyků na panelu nástrojů emulátoru. Pokud je to tento případ, vyberte **otočit** tlačítko na panelu nástrojů emulátor a pokuste se znovu použít více dotyků. Pokud se problém nevyřeší, přečtěte si [Emulator se vykreslení obsahu OpenGL](#OpenGL) problém.

##  <a name="Support"></a> Informační zdroje podpory
 Pokud hostitelský počítač splňuje požadavky na systém a narazíte na problém, která nejsou zahrnuta do tohoto průvodce odstraňováním potíží:

-   Položit dotaz na StackOverflow pomocí [emulátor android](http://stackoverflow.com/questions/tagged/android-emulator) a visual studio.

-   Nahlaste problém pomocí odeslat úsměv nástroje v sadě Visual Studio nebo v správce emulátoru.
