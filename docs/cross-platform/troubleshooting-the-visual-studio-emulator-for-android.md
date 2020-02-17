---
title: Řešení potíží s emulátorem sady Visual Studio pro Android | Microsoft Docs
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
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272069"
---
# <a name="troubleshoot-the-visual-studio-emulator-for-android"></a>Poradce při potížích s emulátorem sady Visual Studio pro Android
Toto téma obsahuje informace, které vám pomohou vyřešit problémy, se kterými se můžete setkat při použití emulátoru sady Visual Studio pro Android.

> [!WARNING]
> Po nainstalování emulátoru, instalační program zkontroluje požadavky pro spuštění softwaru. Upozornění se zobrazí, pokud požadavky nejsou k dispozici, ale ta je není nutné pro instalaci.

 Toto téma obsahuje následující části.

- [Než začnete](#BeforeYouStart)

- [Instalace emulátoru se nezdařila](#NoInstall)

- [Nejde se připojit k síťovým cílům v doméně nebo podnikové síti.](#DomainNetwork)

- [Nelze se připojit k cílům v síti, pokud nastavení sítě vyžaduje ruční konfiguraci.](#ManualNetworkConfig)

- [Emulátor se spouští pomalu, nespustí se z důvodu vypršení časového limitu nebo se nasazení aplikace nezdařilo.](#SlowStart)

- [Emulátor se nepodařilo spustit.](#NoStart2)

- [Spuštění emulátoru se nezdařilo (první použití)](#NoStart)

- [Spuštění počítače po instalaci emulátoru se nezdařilo.](#NoBoot)

- [Visual Studio se zablokuje při pokusu o nasazení aplikace do emulátoru nebo se emulátor nezobrazuje jako cíl ladění v jiných prostředích.](#ADB)

- [Emulátor přestane reagovat, protože nedokázal nastavit port UDP.](#XamarinPlayer)

- [Nejde připojit ladicí program k projektu Xamarin.](#Skylake)

- [Emulátor nemůže spustit aplikaci, která používá Služby Google Play](#GooglePlay)

- [Přetahování souborů, APK nebo souboru zip s příponou souboru ZIP nefunguje](#DragAndDrop)

- [Rozlišení obrazovky je nesprávné.](#Resolution)

- [Emulátor nedokáže vykreslovat obsah OpenGL.](#OpenGL)

- [Emulátor nereaguje na gesta s více dotyky.](#Multitouch)

- [Prostředky podpory](#Support)

## <a name="BeforeYouStart"></a>Než začnete
 Než začnete řešit potíže, může být užitečné v následujících tématech:

- [Požadavky na systém pro emulátor sady Visual Studio pro Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

## <a name="NoInstall"></a>Instalace emulátoru se nezdařila
 Pokud nemáte nainstalovanou technologii Hyper-V, zobrazí se následující zpráva při pokusu o instalaci emulátoru. Musíte mít počítač, který podporuje Hyper-v a musí být povolené.

 ![Problém&#95;instalace&#95;&#95;pro Android EMU](../cross-platform/media/android_emu_install_issue.png "Android_Emu_Install_Issue")

> [!NOTE]
> Tato zpráva platí jak pro Visual Studio Emulator for Android a emulátor Windows Phone. Windows 8.1 a Windows 10 podporovat emulátor.

 Pokud se zobrazí tato zpráva, podívejte se na [požadavky na systém pro emulátor sady Visual Studio pro Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) , abyste viděli, jestli můžete spustit emulátor.

## <a name="DomainNetwork"></a>Nejde se připojit k síťovým cílům v doméně nebo podnikové síti.
 Visual Studio Emulator for Android se zobrazí v síti jako samostatný zařízení pomocí jeho vlastní IP adresu. Není připojený k doméně Windows a nesdílí přihlašovací údaje domény nebo pracovní skupině se hostitelský počítač.

 Pokud síť vyžaduje ověřování domény nebo pracovní skupiny pro základní síť a připojení k Internetu, obraťte se na správce IT se pro výjimku. Tato výjimka umožňuje vývojovém počítači, který bude sloužit jako počítač hranice a tak, aby přijímal připojení ze zařízení není připojené k doméně sítě jako emulátor.

 Visual Studio Emulator for Android také využívá vlastní sadu adresy MAC. Pokud nemůžete získat přístup k síti nebo k prostředkům sítě Internet z emulátoru, obraťte se na správce IT a ujistěte se, že jsou adresy MAC emulátoru autorizovány ve vaší síti.

#### <a name="to-view-the-emulators-mac-addresses"></a>Zobrazení adres MAC emulátoru

1. Spusťte emulátor.

2. Na panelu nástrojů emulátor, klikněte na tlačítko s dvojitou šipkou (>>) Chcete-li otevřít v okně Další nástroje.

3. V okně Další nástroje klikněte na kartu síť.

4. Na stránce sítě vyhledejte položky fyzickou adresu.

## <a name="ManualNetworkConfig"></a>Nelze se připojit k cílům v síti, pokud nastavení sítě vyžaduje ruční konfiguraci.
 Pro připojení k síti cíle z emulátoru serveru, musí vaše síť splňovat následující požadavky:

- DHCP. Emulátor vyžaduje DHCP, protože samotný nakonfiguruje jako samostatnou zařízení v síti s jeho vlastní IP adresu.

- Automaticky nakonfigurované DNS a nastavení brány. Pro emulátor není možné ručně nakonfigurovat nastavení DNS a brány.

  Pokud síť vyžaduje ručně nakonfigurované nastavení, obraťte se na správce IT k určení, jak můžete zajistit připojení k síti pro emulátor.

## <a name="SlowStart"></a>Emulátor se spouští pomalu, nespustí se z důvodu vypršení časového limitu nebo se nasazení aplikace nezdařilo.
 Za určitých podmínek emulátor trvá několik minut nebo nepodaří spustit z důvodu vypršení časového limitu. Po neúspěšném spuštění emulátoru se zobrazí následující zpráva: `App deployment failed. Please try again`. Následující podmínky může vést k této chybě.

- Spuštění emulátoru Visual Studia pro Android z spouštěcí virtuální pevný disk. Tato konfigurace není podporovaná.

- Chybný pevný disk. Zvažte spuštění programu chkdsk.

- Pevný disk, který je potřeba defragmentovat. Vezměte v úvahu defragmentace jednotce.

- Pevný disk, který je téměř plná. Kontrola místa na jednotce.

- Nedostatek paměti je k dispozici z důvodu ostatní spuštěné aplikace. Snížení počtu aplikací, které spotřebovávají paměť nebo zvětšete velikost paměti.

- Obecně platí všechny faktorem, který přispívá ke špatnému výkonu v systému. Začněte řešit potíže se součástí, která má nejnižší skóre v indexu prostředí Windows, které můžete vyhledat na stránce informace o výkonu a nástrojů ovládacích panelů.

## <a name="NoStart2"></a>Emulátor se nepodařilo spustit.
 Pokud emulátor fungovala předtím, ale teď nefunguje, projděte si následující úlohy. Pokud používáte emulátor poprvé, přečtěte si článek o [spuštění emulátoru (první použití)](#NoStart) , než se pustíte do těchto kroků.

- Odeberte ostatní instance Hyper-V emulátoru.

    1. Zavřete Visual Studio.

    2. Otevřete Správce technologie Hyper-V a zastavte všechny instance Hyper-V emulátoru (virtuální počítače), která už jsou spuštěné a případně v poškozeném stavu.

    3. Ve Správci technologie Hyper-V odstraňte všechny ostatní emulátor virtuálních počítačů.

    4. Po restartování počítače.

- Ujistěte se, že máte alespoň 4 GB systémové paměti a že není se využívat v jiných prostředků náročné programy a procesů (např. Zkuste zavřít všechna okna prohlížeče).

- Ve Správci technologie Hyper-V otevřete Správce virtuálních přepínačů a zkontrolujte, zda máte dvě síťové přepínače; Ověřte, že první z nich je interní přepínač a druhý je externí.

     ![Přepínač&#95;&#95;muž&#95;V&#95;EMU V pro Android](../cross-platform/media/android_emu_v_switch_man.png "Android_Emu_V_Switch_Man")

     Pokud není instalace správná a používáte Windows 10, můžete se pokusit [znovu nainstalovat síťová zařízení pomocí příkazu netcfg-d](https://support.microsoft.com/help/10741/windows-fix-network-connection-issues) (oddíl 6).

- Pokud tyto kroky problém nevyřeší, přečtěte si informace o softwaru třetích stran, který může kolidovat s emulátorem, v tématu [spuštění emulátoru se nespustí (první použití)](#NoStart) .

## <a name="NoStart"></a>Spuštění emulátoru se nezdařilo (první použití)
 Pokud emulátor nespustí, projděte si následující úkoly a identifikovat a opravit tento problém.

- Ujistěte se, že jsou splněny minimální požadavky na hardware a správnost nastavení systému BIOS.

   Emulátor a Windows 8 Hyper-V vyžaduje 64bitový procesor s druhou překlad adres úrovně (SLAT). Pro Intel musíte v podstatě Core i3 i5 nebo i7 procesoru (nebo jeden z mnoha Xeons). Seznam čipů AMD je k dispozici [zde](https://www.amd.com/en/support).

  1. Ujistěte se, že váš počítač splňuje [požadavky na systém](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md).

  2. Ověřte, že [Nástroj SLAT](https://slatstatuscheck.codeplex.com/) hlásí, že váš počítač podporuje technologii SLAT.

  3. V rámci nastavení systému BIOS v počítači Ujistěte se, že je povoleno všechny technologie virtualizace. Pro každého výrobce hardwaru se můžou lišit přesné popisy systému BIOS. Obecně platí povolte funkce související s:

     - SLAT (překladu adres druhé úrovně)

     - EPT (Extended Page Tables) (Intel)

     - NPT (vnořené Page Tables) (AMD)

     - RVI (Rapid Virtualization Indexing) (AMD)

     - VMX (zkratka Intel označující podpora virtualizace s hardwarovým řízením)

     - SVM (zkratka AMD označující podpora virtualizace s hardwarovým řízením)

     - XD (spuštění zakázat) (Intel); Tato možnost musí být povolena

     - NX (žádné Execute)(AMD); Toto musí být povolena.

  4. Pokud tyto možnosti jsou k dispozici v systému BIOS, je zakážete.

     - Zakázat Intel VT-d

     - Zakázat Trusted Execution

       Další informace najdete v tomto článku: Technet: jak Hyper-V: na oprava systému BIOS chyby povolení Hyper-V

  5. Ujistěte se, že máte alespoň 4 GB systémové paměti a že není právě využívat v jiných prostředků náročné aplikace a procesy.

  6. Zkontrolujte, že se systémem Windows 8 Professional nebo vyšší (Windows Server 2008 se nepodporuje). Windows Server 2012 je podporována, ale je nutné povolit desktopové prostředí.

     Můžete si prohlédnout Prohlížeč událostí, jestli jsou všechny chyby hypervisoru. Provedete to tak, že otevřete Prohlížeč událostí (**Spusťte klíčovou**+**R**, pak zadáte `eventvwr`) a pak vyberete **protokoly Windows**, **systém**. Pak vyfiltrujte protokol podle zdroje událostí a nastavte zdroj na **Hyper-V-hypervisor**. Vyhledejte chyby vám pomůže identifikovat hlavní příčinu.

     Pokud váš procesor splňuje minimální požadavky, ale hypervisor stále nedaří, zvažte hledání na co si je upgrade systému BIOS dostupné pro váš počítač. Pokud existuje, a vy zvolíte upgradovat, je nutné sledovat všechna opatření od výrobce, při upgradu systému BIOS (jako je zajištění upgrade firmwaru systému BIOS není přerušení kvůli výpadku napájení, který může poškodit trvale systému BIOS).

- Ujistěte se, že máte alespoň 4 GB systémové paměti a že není právě využívat v jiných prostředků náročné aplikace a procesy.

- Odebrat nebo zakázat ovladačů jiných výrobců nebo software, který může být zasahovala do virtuální sítě.

   Existují některé známé problémy s některými 3. stran produkty nainstalované v systému Windows 8 například síťové ovladače a protokoly, které nejsou plně kompatibilní s Hyper-V síťového zásobníku.

   Obecně platí bude až vývojářům tyto produkty se aktualizace softwaru se kvůli kompatibilitě s Windows 8 a technologie Hyper-V.

   Následující produkty mohou vyžadovat upgradování pro dodržování předpisů pro Windows 8: VirtualBox, virtuální počítače VMWare, 7 někteří klienti VPN software brány firewall, některé verze klientů Cisco VPN a dalšími systémy virtualizace. Spolupracovat s vývojáři sporná virtualizačního softwaru Doporučte jim upgrade softwaru, aby byl kompatibilní s Windows 8 a technologie Hyper-V.

   Jako *alternativní řešení*můžete zakázat všechny ovladače a aplikace třetích stran, které by mohly být v konfliktu s virtuální sítí, kterou používá emulátor ke komunikaci se sadou Visual Studio. Tyto aplikace mohou zahrnovat:

  - Antivirové aplikace (které integrovat do síťových protokolů)

  - Nástroje pro monitorování sítě

  - Nástroje protokolování sítě

  - Monitorovací software jiných systému

    Jiné možných alternativních nemá odinstalaci produktů dotaz (a žádosti o produktu pro vývojáře k uvolnění aktualizovanou verzi), je provést následující kroky.

  1. Spusťte Správce síťových připojení (na obrazovce Start zadejte `View Network Connections` a vyberte tuto možnost, chcete-li zobrazit síťová připojení.)

  2. V případě adaptéru vEthernet (interní adaptér Ethernet Windows Phone emulátor interního přepínače) vyberte z kontextové nabídky možnost **vlastnosti** .

      ![Virtuální adaptér používaný technologií Hyper&#45;V](../cross-platform/media/android_emu_virtual_adapter.png "Android_Emu_Virtual_Adapter")

      Zde jsou zobrazeny vlastnosti adaptéru.

      ![Vlastnosti virtuálního adaptéru](../cross-platform/media/android_emu_virtual_adapter_properties.png "Android_Emu_Virtual_Adapter_Properties")

  3. V případě tohoto adaptéru by se v rámci **tohoto připojení** měly vybrat jenom tyto položky:

     - Klient sítě Microsoft

     - Plánovač paketů technologie QoS

     - Sdílení souborů a tiskáren v sítích Microsoft

     - Ovladač Microsoft LLDP protokolu

     - Ovladač vstupně-výstupních operací mapovače zjišťování topologie linkové vrstvě

     - Respondér zjišťování topologie linkové vrstvě

     - Internet Protocol verze 6 (TCP/IPv6)

     - Protokol IP verze 4 (TCP/IPv4)

  4. Zrušte výběr další položky.

     Nevýhodou použití této techniky je, že kdykoli nový 3. stran produkt instaluje nepodporované ovladače nebo pokaždé, když nainstalování emulátoru těchto kroků bude nutné jej opakovat.

     Po odinstalování serveru produkty třetích stran, budete muset obnovit interní přepínač emulátoru Windows Phone. Postup:

  - Otevřete Hyper-V a přejděte do Správce virtuálního přepínače. Vytvořte virtuální přepínač s názvem Windows Phone interní přepínač emulátoru a nastavte jeho typ připojení na **interní síť**.

     ![Správce virtuálních přepínačů](../cross-platform/media/android_emu_virtual_switch_manager.png "Android_Emu_Virtual_Switch_Manager")

    Nyní spusťte emulátor. Mělo by to fungovat.

## <a name="NoBoot"></a>Spuštění počítače po instalaci emulátoru se nezdařilo.
 Tomuto problému může dojít, pokud jsou splněny následující podmínky:

- Počítač se základní desky GB.

- USB3 je povolena na základní desce.

  Chcete-li tento problém vyřešit, zakažte USB3 v nastavení systému BIOS základní desky a restartujte počítač. Potom zkontrolujte, zda gigabajt vydal aktualizaci pro systém BIOS základní desky.

  Další informace najdete v následujícím článku znalostní báze: [Chyba spuštění po instalaci role Hyper-V v systémech gigabajtů](https://support.microsoft.com/en-us/kb/2693144).

## <a name="ADB"></a>Visual Studio se zablokuje při pokusu o nasazení aplikace do emulátoru nebo se emulátor nezobrazuje jako cíl ladění v jiných prostředích.
 Pokud je spuštěný emulátor, ale nezobrazí se chcete připojit k ADB (Android Debug Bridge) nebo se nezobrazují v nástroje pro Android, která využívají ADB (Android Studio nebo Eclipse), budete muset upravit, kde emulátor hledá ADB. Emulátor používá klíč registru pro určení základní umístění sady Android SDK a hledá soubor \platform-tools\adb.exe v tomto adresáři. Chcete-li změnit cesta sady Android SDK používaná emulátorem:

- Otevřete Editor registru výběrem možnosti **Spustit** z kontextové nabídky tlačítka Start, zadáním `regedit` v dialogovém okně a kliknutím na **tlačítko OK**.

- Ve stromu složek na levé straně přejděte na *HKEY_LOCAL_MACHINE \software\wow6432node\android SDK Tools* .

- Upravte proměnnou registru **path** tak, aby odpovídala cestě k vašemu Android SDK.

  Restartujte emulátor a byste teď měli zobrazíte emulátor připojen k ADB a související nástroje pro Android.

## <a name="XamarinPlayer"></a>Emulátor přestane reagovat, protože nedokázal nastavit port UDP.
 Tento problém z důvodu nekompatibility s Xamarin Playerem může docházet. Pokud se zdá, že emulátor přestane reagovat nebo se zobrazí tato chybová zpráva, "emulátor se nemůže připojit k operačnímu systému zařízení: Nepodařilo se nastavit port UDP.  Některé funkce můžou být zakázané", může dojít k tomuto problému. Proveďte následující kroky.

1. Odinstalujte Xamarin Playeru.

2. Ověřte, že tohoto virtuálního pole byla odebrána (Xamarin Playeru se spouští nad virtuální pole).

3. Přejděte do Správce zařízení, vyberte možnost Zobrazit skrytá zařízení a odstraňte všechno kromě fyzické síťové karty.

4. Můžete vyzkoušet, odinstalace a opětovné instalace technologie Hyper-V po odebrání všech jiných fyzických síťových adaptérů.

## <a name="Skylake"></a>Nejde připojit ladicí program k projektu Xamarin.
 Pokud používáte Windows 10 s procesory Intel Skylake, aplikace Xamarin se nemusí podařit spustit v emulátoru nebo k nim nemusí připojit ladicí program sady Visual Studio. Toto je kvůli problému s Hyper-V a Skylake procesory. Jako alternativní řešení proveďte následující kroky.

1. Otevřete Správce technologie Hyper-V a vyberte virtuální počítač pro emulátor profil, který se pomocí.

2. Vyberte **Odstranit uložený stav** (vpravo dole).

3. Zvolit **nastavení...**

4. Rozbalte uzel procesor a vyberte možnost **Kompatibilita**.

5. Povolte **migraci do fyzického počítače s jinou verzí procesoru**.

6. Restartujte službu (v části **Akce**) a zkuste to znovu.

## <a name="GooglePlay"></a>Emulátor nemůže spustit aplikaci, která používá Služby Google Play
 Emulátor se nedodává s knihovny služby Google Play. Emulátor však nepodporuje instalaci a přetažení aktualizačního souboru zip souborů.

## <a name="DragAndDrop"></a>Přetahování souborů, APK nebo souboru zip s příponou souboru ZIP nefunguje
 Emulátor používá ADB.exe pro usnadnění přenos souborů, když přetahujete souboru na obrazovku. Pokud narazíte na chybu při pokusu o přetažení souboru, to pravděpodobně znamená, že není emulátor připojen k ADB.exe. Chcete-li problém vyřešit, postupujte podle kroků v [aplikaci Visual Studio, které se pokouší o nasazení aplikace do emulátoru, nebo se emulátor nezobrazí jako cíl ladění v jiném](#ADB)prostředí.

## <a name="Resolution"></a>Rozlišení obrazovky je nesprávné.
 Pokud naberete snímek obrazovky pomocí karty snímku obrazovky v **dalších oknech nástrojů** a výsledný obraz má neočekávanou velikost, možná budete muset před výběrem možnosti **zachytit**upravit úroveň přiblížení obrazovky. Emulátor trvá snímky obrazovky na rozlišení obrazovky na monitoru hostitelský počítač.

## <a name="OpenGL"></a>Emulátor nedokáže vykreslovat obsah OpenGL.
 Emulátor vykresluje obsah OpenGL pomocí GPU vašeho hostitelského počítače a používá k převodu těchto volání do a z rozhraní DirectX rozlomený projekt. Pokud vaše aplikace správně vykresluje na zařízení ale nesprávně v emulátoru, je pravděpodobné, že zařízení je snížení rizik souvisejících s nesprávné volání OpenGL (například pomocí proměnné shaderu, které se neshodují s).

## <a name="Multitouch"></a>Emulátor nereaguje na gesta s více dotyky.
 V některých případech se emulátor spustí a nereaguje na více dotyků buď prostřednictvím přímé interakce ze zobrazení dotykově ovládaný nebo pomocí nástroje více dotyků na panelu nástrojů emulátoru. Pokud se jedná o tento případ, klikněte na panelu nástrojů emulátoru na tlačítko **otočit** a pokuste se znovu použít dotykové ovládání. Pokud se problém nevyřeší, přečtěte si v emulátoru nepovedlo [se vykreslit problém s obsahem OpenGL](#OpenGL) .

## <a name="Support"></a>Prostředky podpory
 Pokud hostitelský počítač splňuje požadavky na systém a narazíte na problém, která nejsou zahrnuta do tohoto průvodce odstraňováním potíží:

- Položte otázku na StackOverflow pomocí značek [Androidu](https://stackoverflow.com/questions/tagged/android-emulator) a Visual-Studio.

- Nahlaste problém pomocí odeslat úsměv nástroje v sadě Visual Studio nebo v správce emulátoru.
