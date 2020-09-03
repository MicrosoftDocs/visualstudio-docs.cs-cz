---
title: Řešení potíží s emulátorem pro Android | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: troubleshooting
ms.assetid: f3fb5df4-3aae-40e4-9450-bbe15b0c5af5
caps.latest.revision: 25
ms.author: crdun
manager: crdun
ms.openlocfilehash: 27f69a3295deb8d3335878acc865314635af7c0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387301"
---
# <a name="troubleshooting-the-visual-studio-emulator-for-android"></a>Poradce při potížích s emulátorem sady Visual Studio pro Android
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma obsahuje informace, které vám pomohou vyřešit problémy, se kterými se můžete setkat při použití emulátoru sady Visual Studio pro Android.

> [!WARNING]
> Po instalaci emulátoru zkontroluje instalační program požadavky na spuštění softwaru. Zobrazí se upozornění, pokud požadavky nejsou k dispozici, ale nevyžadují jejich instalaci.

 Toto téma obsahuje tyto části:

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

## <a name="before-you-start"></a><a name="BeforeYouStart"></a> Než začnete
 Než začnete řešit potíže, může být užitečné projít si následující témata:

- [Systémové požadavky pro emulátor sady Visual Studio pro Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

## <a name="emulator-fails-to-install"></a><a name="NoInstall"></a> Instalace emulátoru se nezdařila
 Pokud nemáte nainstalovanou technologii Hyper-V, při pokusu o instalaci emulátoru se zobrazí následující zpráva. Musíte mít počítač, který podporuje HyperV a musí být povolený.

 ![Android&#95;EMU&#95;instalaci&#95;problému](../cross-platform/media/android-emu-install-issue.png "Android_Emu_Install_Issue")

> [!NOTE]
> Tato zpráva se vztahuje na emulátor sady Visual Studio pro Android a emulátor Windows Phone. Windows 8.1 a Windows 10 podporují emulátor.

 Pokud se zobrazí tato zpráva, podívejte se na [požadavky na systém pro emulátor sady Visual Studio pro Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) , abyste viděli, jestli můžete spustit emulátor.

## <a name="cannot-connect-to-network-destinations-on-a-domain-or-corporate-network"></a><a name="DomainNetwork"></a> Nejde se připojit k síťovým cílům v doméně nebo podnikové síti.
 Emulátor sady Visual Studio pro Android se zobrazí v síti jako samostatné zařízení s vlastní IP adresou. Není připojen k doméně systému Windows a nesdílí přihlašovací údaje domény nebo pracovní skupiny s hostitelským počítačem.

 Pokud vaše síť vyžaduje autorizaci v doméně nebo pracovní skupině pro základní připojení k síti a Internetu, požádejte o výjimku správce IT. Tato výjimka umožňuje, aby váš vývojový počítač sloužil jako hraniční počítač a přijímal připojení ze síťových zařízení, která nejsou připojená k doméně, jako je emulátor.

 Emulátor sady Visual Studio pro Android používá také vlastní sadu adres MAC. Pokud nemůžete získat přístup k síti nebo k prostředkům sítě Internet z emulátoru, obraťte se na správce IT a ujistěte se, že jsou adresy MAC emulátoru autorizovány ve vaší síti.

#### <a name="to-view-the-emulators-mac-addresses"></a>Zobrazení adres MAC emulátoru

1. Spusťte emulátor.

2. Kliknutím na tlačítko se šipkou (>>) na panelu nástrojů emulátoru otevřete další okno nástrojů.

3. V okně Další nástroje klikněte na kartu síť.

4. Na stránce síť vyhledejte položky fyzických adres.

## <a name="cannot-connect-to-network-destinations-when-network-settings-require-manual-configuration"></a><a name="ManualNetworkConfig"></a> Nelze se připojit k cílům v síti, pokud nastavení sítě vyžaduje ruční konfiguraci.
 Aby bylo možné se připojit k síťovým cílům z emulátoru, musí vaše síť splňovat následující požadavky:

- Dané. Emulátor vyžaduje protokol DHCP, protože nakonfiguruje sám sebe jako samostatné zařízení v síti s vlastní IP adresou.

- Automaticky nakonfigurovaná nastavení DNS a brány. Pro emulátor není možné ručně nakonfigurovat nastavení DNS a brány.

  Pokud vaše síť vyžaduje ručně nakonfigurovaná nastavení, obraťte se na správce IT a zjistěte, jak můžete pro emulátor povolit síťové připojení.

## <a name="emulator-starts-slowly-fails-to-start-due-to-a-timeout-or-app-deployment-fails"></a><a name="SlowStart"></a> Emulátor se spouští pomalu, nespustí se z důvodu vypršení časového limitu nebo se nasazení aplikace nezdařilo.
 Za určitých podmínek trvá emulátor několik minut, než se spustí z důvodu vypršení časového limitu. Po neúspěšném spuštění emulátoru se zobrazí následující zpráva: `App deployment failed. Please try again` . Následující podmínky mohou mít za následek tuto chybu.

- Spouští se emulátor sady Visual Studio pro Android ze spouštěcího virtuálního pevného disku. Tato konfigurace není podporovaná.

- Chybný pevný disk. Zvažte spuštění programu Chkdsk.

- Pevný disk, který je třeba defragmentovat. Zvažte defragmentaci jednotky.

- Pevný disk, který je skoro plný. Ověřte místo na disku, které je k dispozici.

- K dispozici není dostatek paměti z důvodu ostatních spuštěných aplikací. Snižte počet aplikací, které spotřebovávají paměť nebo zvyšují množství paměti.

- Obecně platí, že každý faktor, který přispívá k špatnému výkonu systému. Začněte s řešením potíží s komponentou, která má nejnižší dílčí skóre v indexu Windows Experience Index, který můžete najít na stránce informace o výkonu a nástroje v Ovládacích panelech.

## <a name="emulator-fails-to-start"></a><a name="NoStart2"></a> Emulátor se nepodařilo spustit.
 Pokud emulátor dříve fungoval, ale nefunguje, Projděte si následující úlohy. Pokud používáte emulátor poprvé, přečtěte si článek o [spuštění emulátoru (první použití)](#NoStart) , než se pustíte do těchto kroků.

- Odeberte všechny ostatní instance technologie Hyper-V emulátoru.

    1. Zavřete Visual Studio.

    2. Otevřete Správce technologie Hyper-V a zastavte všechny instance technologie Hyper-V emulátoru (Virtual Machines), které jsou již spuštěny a pravděpodobně v poškozeném stavu.

    3. Ve Správci technologie Hyper-V odstraňte všechny další virtuální počítače emulátoru.

    4. Restartujte počítač.

- Ujistěte se, že máte alespoň 4GB systémové paměti a že nespotřebovává jiné programy a procesy náročné na prostředky (například zkuste zavřít všechna okna prohlížeče).

- Ve Správci technologie Hyper-V otevřete Správce virtuálního přepínače a zkontrolujte, že máte dvě síťové přepínače. Ověřte, že první z nich je interní přepínač a druhá je externí.

     ![Android&#95;EMU&#95;V&#95;přepínač&#95;muž](../cross-platform/media/android-emu-v-switch-man.png "Android_Emu_V_Switch_Man")

     Pokud není instalace správná a používáte Windows 10, můžete se pokusit [znovu nainstalovat síťová zařízení pomocí příkazu netcfg – d](https://support.microsoft.com/help/10741/windows-fix-network-connection-issues) (oddíl 6).

- Pokud tyto kroky problém nevyřeší, přečtěte si informace o softwaru třetích stran, který může kolidovat s emulátorem, v tématu [spuštění emulátoru se nespustí (první použití)](#NoStart) .

## <a name="emulator-fails-to-start-first-use"></a><a name="NoStart"></a> Spuštění emulátoru se nezdařilo (první použití)
 Pokud se emulátor nespustí, Projděte si následující úlohy a identifikujte a opravte problém.

- Ujistěte se, že jsou splněné minimální hardwarové požadavky a že jsou správně nastavená nastavení systému BIOS.

   Emulátor a Windows 8 Hyper-V vyžadují 64 procesor s překladem adres druhé úrovně (SLAT). V případě Intel budete potřebovat základní procesor i3, i5 nebo i7 (nebo jeden z mnoha Xeon). Seznam čipů AMD je k dispozici [zde](https://www.amd.com/en/support).

  1. Ujistěte se, že váš počítač splňuje [požadavky na systém](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md).

  2. Ověřte, že [Nástroj SLAT](https://slatstatuscheck.codeplex.com/) hlásí, že váš počítač podporuje technologii SLAT.

  3. V nastavení systému BIOS počítače se ujistěte, že je povolena veškerá technologie virtualizace. Přesné popisy systému BIOS se mohou lišit pro každého výrobce hardwaru. Obecně je možné povolit funkce související s:

     - SLAT (překlad adres druhé úrovně)

     - EPT (tabulky rozšířených stránek) (Intel)

     - NPT (vnořené tabulky stránky) (AMD)

     - RVI (rychlé indexování virtualizace) (AMD)

     - VMX (akronym Intel s označením podpory virtualizace hardwaru s asistencí)

     - SVM (akronym AMD označující hardwarovou podporu virtualizace)

     - XD (Execute Disable) (Intel); Tato možnost musí být povolená.

     - NX (bez spuštění) (AMD); Tato možnost musí být povolená.

  4. Pokud je v systému BIOS k dispozici následující možnosti, zakažte je.

     - Zakázat Intel VT-d

     - Zakázat důvěryhodné spuštění

       Další informace najdete v tomto článku: TechNet: Hyper-V: Oprava chyb systému BIOS povolení technologie Hyper-V.

  5. Ujistěte se, že máte alespoň 4GB systémové paměti a že nespotřebovává žádné další programy a procesy náročné na prostředky.

  6. Ujistěte se, že používáte systém Windows 8 Professional nebo vyšší (systém Windows Server 2008 není podporován). Systém Windows Server 2012 je podporován, ale je nutné povolit možnosti práce s počítačem.

     Můžete zkontrolovat Prohlížeč událostí a zjistit, jestli nedochází k chybám hypervisoru. Provedete to tak, že otevřete Prohlížeč událostí (spusťte klíč + R, pak zadáte `eventvwr` ) a pak vyberete **protokoly Windows**, **systém**. Pak vyfiltrujte protokol podle zdroje událostí a nastavte zdroj na **Hyper-V-hypervisor**. Zjistí chyby, které vám pomůžou identifikovat hlavní příčinu.

     Pokud váš procesor splňuje minimální požadavky, ale hypervisor stále selhává, zvažte, jestli je pro váš počítač k dispozici upgrade systému BIOS. Pokud existuje, a Vy se rozhodnete upgradovat, nezapomeňte při upgradu systému BIOS pozorovat všechna opatření od výrobce (například zajistit, aby upgrade firmwaru systému BIOS nebyl přerušený ztrátou napájení, který může trvale poškodit systém BIOS).

- Ujistěte se, že máte alespoň 4GB systémové paměti a že nespotřebovává žádné další programy a procesy náročné na prostředky.

- Odeberte nebo zakažte ovladače nebo software třetích stran, které můžou být v konfliktu s virtuálními sítěmi.

   Existují některé známé problémy s některými produkty třetích stran nainstalovanými v systému Windows 8, jako jsou například síťové ovladače/protokoly, které nejsou plně kompatibilní se zásobníkem sítě Hyper-V.

   Obecně platí, že až budou vývojáři těchto produktů aktualizovat software tak, aby byly kompatibilní se systémy Windows 8 a Hyper-V.

   Následující produkty mohou vyžadovat upgrade dodržování předpisů pro systém Windows 8: VirtualBox, Virtual PC 7, VMWare, někteří klienti VPN, brány firewall softwaru, některé verze klientů Cisco VPN a další virtualizační systémy. Spolupracujte s vývojářem problematického virtualizačního softwaru, který jim pomůžete upgradovat software tak, aby byl kompatibilní s Windows 8 a Hyper-V.

   Jako **alternativní řešení**můžete zakázat všechny ovladače a aplikace třetích stran, které by mohly být v konfliktu s virtuální sítí, kterou používá emulátor ke komunikaci se sadou Visual Studio. Tyto aplikace můžou zahrnovat:

  - Antivirové aplikace (které se připojí k zásobníku sítě)

  - Nástroje pro monitorování sítě

  - Nástroje pro protokolování sítě

  - Jiný software pro monitorování systému

    Dalším možným řešením je, že je nutné provést následující kroky, a to i v případě, že dojde k jejich zkrácení.

  1. Spusťte Správce síťových připojení (na obrazovce Start zadejte `View Network Connections` a vyberte tuto možnost, chcete-li zobrazit síťová připojení.)

  2. V případě adaptéru vEthernet (interní adaptér Ethernet Windows Phone emulátor interního přepínače) vyberte z kontextové nabídky možnost **vlastnosti** .

      ![Virtuální adaptér používaný technologií Hyper&#45;V](../cross-platform/media/android-emu-virtual-adapter.png "Android_Emu_Virtual_Adapter")

      Tady jsou uvedené vlastnosti adaptéru.

      ![Vlastnosti virtuálního adaptéru](../cross-platform/media/android-emu-virtual-adapter-properties.png "Android_Emu_Virtual_Adapter_Properties")

  3. V případě tohoto adaptéru by se v rámci **tohoto připojení** měly vybrat jenom tyto položky:

     - Klient sítě Microsoft

     - Plánovač paketů technologie QoS

     - Sdílení souborů a tiskáren v sítích Microsoft

     - Ovladač protokolu Microsoft LLDP

     - Vstupně-výstupní ovladač mapovače zjišťování topologie propojení

     - Respondér zjišťování topologie linkové vrstvy

     - Internet Protocol verze 6 (TCP/IPv6)

     - Internet Protocol verze 4 (TCP/IPv4)

  4. Zrušte výběr všech ostatních položek.

     Nevýhodou pro použití tohoto postupu je to, že pokud nový produkt třetí strany nainstaluje nepodporované ovladače nebo kdykoli bude emulátor nainstalovaný, bude nutné tyto kroky zopakovat.

     Po odinstalaci produktů třetích stran možná budete muset obnovit interní přepínač emulátoru Windows Phone. Postup:

  - Otevřete Hyper V a přejděte do Správce virtuálního přepínače. Vytvořte virtuální přepínač s názvem Windows Phone interní přepínač emulátoru a nastavte jeho typ připojení na **interní síť**.

     ![Správce virtuálních přepínačů](../cross-platform/media/android-emu-virtual-switch-manager.png "Android_Emu_Virtual_Switch_Manager")

    Nyní spusťte emulátor. Měla by fungovat.

## <a name="computer-fails-to-boot-after-installing-the-emulator"></a><a name="NoBoot"></a> Spuštění počítače po instalaci emulátoru se nezdařilo.
 K tomuto problému může dojít, pokud jsou splněné následující podmínky:

- Váš počítač má základní desku (GB).

- USB3 je na základní desce zapnuté.

  Chcete-li tento problém vyřešit, zakažte USB3 v nastavení systému BIOS základní desky a restartujte počítač. Potom zkontrolujte, zda gigabajt vydal aktualizaci pro systém BIOS základní desky.

  Další informace najdete v následujícím článku znalostní báze: [Chyba spuštění po instalaci role Hyper-V v systémech gigabajtů](https://support.microsoft.com/kb/2693144).

## <a name="visual-studio-gets-stuck-trying-to-deploy-the-app-to-the-emulator-or-the-emulator-does-not-appear-as-a-debug-target-in-other-ides"></a><a name="ADB"></a> Visual Studio se zablokuje při pokusu o nasazení aplikace do emulátoru nebo se emulátor nezobrazuje jako cíl ladění v jiných prostředích.
 Pokud emulátor běží, ale zdá se, že není připojený k ADB (Android Debug Bridge), nebo se nezobrazuje v nástrojích pro Android, který využívá ADB (například Android Studio nebo zatmění), může být potřeba upravit, kde emulátor hledá ADB. Emulátor používá klíč registru k identifikaci základního umístění vašeho Android SDK a vyhledá soubor \platform-tools\adb.exe v tomto adresáři. Postup úpravy Android SDK cestou používané emulátorem:

- Otevřete Editor registru výběrem možnosti **Spustit** z kontextové nabídky tlačítka Start, zadáním `regedit` do dialogového okna a kliknutím na **tlačítko OK**.

- Ve stromu složek na levé straně přejděte na HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Android SDK Tools.

- Upravte proměnnou registru **path** tak, aby odpovídala cestě k vašemu Android SDK.

  Restartujte emulátor a teď byste měli mít přístup k emulátoru připojenému k ADB a souvisejícím nástrojům pro Android.

## <a name="emulator-stops-responding-because-it-couldnt-set-up-the-udp-port"></a><a name="XamarinPlayer"></a> Emulátor přestane reagovat, protože nedokázal nastavit port UDP.
 K tomuto problému může docházet z důvodu nekompatibility s Xamarin Playerem. Pokud se zdá, že emulátor přestane reagovat, nebo pokud se zobrazí tato chybová zpráva, "emulátor se nemůže připojit k operačnímu systému zařízení: Nepodařilo se nastavit port UDP.  Některé funkce můžou být zakázané, možná se vám tento problém vyskytl. Proveďte následující kroky.

1. Odinstalujte Xamarin Player.

2. Ověřte, zda bylo zrušeno odebrání virtuálního pole (spouští se Xamarin Player na virtuálním poli).

3. Otevřete Správce zařízení, vyberte možnost pro zobrazení skrytých zařízení a pak odstraňte vše kromě fyzických síťových karet.

4. Po odebrání všech nefyzických síťových adaptérů se můžete pokusit odinstalovat nebo znovu nainstalovat Hyper-V.

## <a name="cannot-attach-debugger-to-a-xamarin-project"></a><a name="Skylake"></a> Nejde připojit ladicí program k projektu Xamarin.
 Pokud používáte Windows 10 s procesory Intel Skylake, nemusí se aplikace Xamarin spouštět v emulátoru nebo se k nim nemusí připojit ladicí program sady Visual Studio. Příčinou je problém s procesory Hyper-V a Skylake. Jako alternativní řešení proveďte následující kroky.

1. Otevřete Správce technologie Hyper-V a vyberte virtuální počítač pro profil emulátoru, který používáte.

2. Vyberte **Odstranit uložený stav** (vpravo dole).

3. Zvolit **nastavení...**

4. Rozbalte uzel procesor a vyberte možnost **Kompatibilita**.

5. Povolte **migraci do fyzického počítače s jinou verzí procesoru**.

6. Restartujte službu (v části **Akce**) a zkuste to znovu.

## <a name="emulator-fails-to-run-app-that-uses-google-play-services"></a><a name="GooglePlay"></a> Emulátor nemůže spustit aplikaci, která používá Služby Google Play
 Emulátor se nedodává s knihovnami pro Služby Google Play. Emulátor však podporuje instalaci souborů zip s podporou přetahování myší.

## <a name="drag-and-drop-of-a-file-apk-or-flashable-zip-file-does-not-work"></a><a name="DragAndDrop"></a> Přetahování souborů, APK nebo souboru zip s příponou souboru ZIP nefunguje
 Emulátor používá ADB.exe k usnadnění přenosu souborů při přetahování souboru na obrazovku. Pokud dojde k chybě při pokusu o přetahování souboru, pravděpodobně to znamená, že emulátor není připojen k ADB.exe. Chcete-li problém vyřešit, postupujte podle kroků v [aplikaci Visual Studio, které se pokouší o nasazení aplikace do emulátoru, nebo se emulátor nezobrazí jako cíl ladění v jiném](#ADB)prostředí.

## <a name="resolution-of-screenshot-is-incorrect"></a><a name="Resolution"></a> Rozlišení obrazovky je nesprávné.
 Pokud naberete snímek obrazovky pomocí karty snímku obrazovky v **dalších oknech nástrojů** a výsledný obraz má neočekávanou velikost, možná budete muset před výběrem možnosti **zachytit**upravit úroveň přiblížení obrazovky. Emulátor přijme snímky obrazovky na rozlišení obrazovky na monitoru hostitelského počítače.

## <a name="emulator-fails-to-render-opengl-content"></a><a name="OpenGL"></a> Emulátor nedokáže vykreslovat obsah OpenGL.
 Emulátor vykresluje obsah OpenGL pomocí GPU vašeho hostitelského počítače a používá k převodu těchto volání do a z rozhraní DirectX rozlomený projekt. Pokud se vaše aplikace správně vykresluje na zařízení, ale nesprávně v emulátoru, je pravděpodobný, aby zařízení zmírnilo nesprávné volání OpenGL (například pomocí proměnných shaderu, které se neshodují).

## <a name="emulator-does-not-respond-to-multi-touch-gestures"></a><a name="Multitouch"></a> Emulátor nereaguje na gesta s více dotyky.
 V některých případech se emulátor spustí a nebude reagovat na více dotyků buď prostřednictvím přímé interakce z obrazovky s povolenými dotyky, nebo pomocí nástroje pro více dotyků na panelu nástrojů emulátoru. Pokud se jedná o tento případ, klikněte na panelu nástrojů emulátoru na tlačítko **otočit** a pokuste se znovu použít dotykové ovládání. Pokud se problém nevyřeší, přečtěte si v emulátoru nepovedlo [se vykreslit problém s obsahem OpenGL](#OpenGL) .

## <a name="support-resources"></a><a name="Support"></a> Prostředky podpory
 Pokud hostitelský počítač splňuje požadavky na systém a narazíte na problém, který není popsaný v této příručce pro odstraňování potíží:

- Položte otázku na StackOverflow pomocí značek [Androidu](https://stackoverflow.com/questions/tagged/android-emulator) a Visual-Studio.

- Nahlaste problém pomocí nástroje odeslat smajlíka v aplikaci Visual Studio nebo ve Správci emulátorů.
