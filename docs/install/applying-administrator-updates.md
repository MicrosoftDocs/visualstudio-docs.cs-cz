---
title: Použití aktualizací správců v aplikaci Visual Studio s koncovým bodem Microsoft Configuration Manager
titleSuffix: ''
description: Naučte se, jak použít aktualizace správce v aplikaci Visual Studio.
ms.date: 04/16/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 9a3fdb28-db3d-4970-bc17-7417a985f0fb
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: c18c460ebcffdba93279aafec2f3d76503ab2383
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307684"
---
# <a name="applying-administrator-updates-that-use-microsoft-endpoint-configuration-manager"></a>Použití aktualizací správce využívajících Microsoft Endpoint Configuration Manager

Tento dokument popisuje různé typy a charakteristiky aktualizací pro správce sady Visual Studio. Níže najdete informace o tom, jak a kdy by se měly distribuovat v celé organizaci, jaké možnosti konfigurace jsou k dispozici a jak zobrazit sestavy a řešit potíže. Další informace o požadavcích na použití aktualizací správců najdete v tématu [Povolení aktualizací správců](../install/enabling-administrator-updates.md). Aktualizace správců předpokládá, že je v počítači již nainstalována aplikace Visual Studio. Při použití aktualizací správce se nespustí zcela nová instalace.

## <a name="understanding-visual-studio-administrator-updates"></a>Principy aktualizací pro správce sady Visual Studio

Balíček aktualizace pro správce sady Visual Studio, který je publikovaný do Microsoft Update pro použití v katalogu Microsoft a WSUS, obsahuje informace, které Configuration Manager potřebuje ke stažení a distribuci aktualizace sady Visual Studio do klientských počítačů. Obsahuje taky informace, které správce IT potřebuje k tomu, aby se rozhodlo, které aktualizace se budou distribuovat v celé organizaci. Dá se použít i k usnadnění údržby rozložení sítě. Balíčky aktualizací pro správce sady Visual Studio neobsahují dostatek informací, aby bylo možné provést novou instalaci produktu, ani neobsahují žádné ze skutečných binárních souborů produktu, které jsou publikovány na Content Delivery Network. Aktualizace správců sady Visual Studio jsou kumulativní, stejně jako běžné aktualizace sady Visual Studio. Můžete předpokládat, že jakákoli aktualizace sady Visual Studio, která má vyšší číslo verze produktu a pozdější datum vydání, je nadmnožinou starší, nižší verze.

Aktualizace správců sady Visual Studio se vztahují na verze údržby sady Visual Studio, které jsou v rámci podpory. Další informace o tom, které standardní hodnoty údržby sady Visual Studio jsou stále v podpoře během konkrétního časového období, najdete v tématu [životní cyklus a údržba produktu Visual](/visualstudio/productinfo/vs-servicing-vs)Studio. Všechny podporované standardní hodnoty údržby sady Visual Studio budou udržovány v bezpečí.  

## <a name="types-and-characteristics-of-administrator-updates"></a>Typy a charakteristiky aktualizací správců

Existují tři typy aktualizací správců sady Visual Studio:

* **Aktualizace zabezpečení** se vztahují na všechny edice sady Visual Studio (třeba na Enterprise, Professional, Community atd.) a obsahují omezené a vysoce cílené a kompatibilní změny úrovně údržby. Aktualizace zabezpečení neovlivní klienta na pozdější podverzi. jsou navržené tak, aby poskytovaly opravy chyb zabezpečení pro klienta, který je již na určité úrovni dílčí verze. Aktualizace zabezpečení budou mít v nich alespoň jednu opravu zabezpečení, ale Oprava zabezpečení může nebo nemusí být součástí součásti nebo úlohy, která je na klientském počítači nainstalovaná. Mohli byste například opravit chybu zabezpečení v komponentách .NET a tuto aktualizaci by znamenali jako aktualizaci zabezpečení. to ale by v klientském počítači znamenalo, že se jenom nainstalovaly jenom komponenty C++. Aktualizace zabezpečení mohou také obsahovat další opravy spolehlivosti nebo jiné nezbytné aktualizace komponent. Aktualizace zabezpečení jsou publikovány do [katalogu Microsoft Update](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) i [Windows Server Update Services](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus), kde jsou klasifikovány jako aktualizace zabezpečení.
* **Aktualizace funkcí** umožňují SPRÁVCům IT předcházet počítačům v jejich organizaci novější podverzi sady Visual Studio. Aktualizace funkcí se vztahují jenom na edice sady Visual Studio, které se běžně nacházejí v podnicích, jako jsou SKU Enterprise, Professional a Build Tools. Všechny aktualizace funkcí budou publikovány do katalogu služby Microsoft Update jako balíčky funkcí a jsou k dispozici pro volitelně ruční [Import do Configuration Manager z katalogu Microsoft Update](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog). Aktualizace funkcí jsou kumulativní a budou obsahovat další kvality a předchozí opravy zabezpečení. Pokyny ke konfiguraci klientského počítače tak, aby zůstaly na standardních hodnotách údržby a zabránění doručování aktualizací funkcí do konkrétních klientů, najdete v [části Možnosti konfigurace](#understanding-configuration-options) níže.
* **Aktualizace kvality** se vztahují také jenom na ty edice sady Visual Studio, které se běžně nacházejí v podnicích a které obsahují omezené, vysoce cílené a kompatibilní změny úrovně údržby. Aktualizace kvality neovlivní klienta na pozdější podverzi. jsou navržené tak, aby poskytovaly opravy výkonu a spolehlivosti nebo jiné nezbytné aktualizace komponent klienta, který je již na určité úrovni dílčí verze. Aktualizace kvality se nashromáždí spolu s aktualizacemi zabezpečení, a proto budou obsahovat opravy zabezpečení pouze v případě, že oprava zabezpečení již byla uvolněna samostatně. Aktualizace kvality jsou publikovány v katalogu Microsoft Update jako "aktualizace" a jsou také k dispozici, aby je bylo možné volitelně ručně [importovat do Configuration Manager](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog).

### <a name="decoding-the-titles-of-administrator-updates"></a>Dekódování názvů aktualizací správců

Název každé aktualizace správce popisuje platný rozsah verzí a výslednou verzi aktualizace.Třeba

::: moniker range="vs-2017"

* **Visual studio 2017 verze 15.9.0 až 15.9.35 Update** klasifikovaná jako aktualizace zabezpečení se bude vztahovat na všechny edice sady visual Studio 2017 na klientovi mezi verzemi 15.9.0 až 15.9.35 a tyto klientské edice budou aktualizovat na 15.9.35.
* Sada **Visual studio 2017 verze 15.0.0 až 15.9.0 Update** klasifikovaná jako "Feature Pack" bude platit pro edice sady visual Studio 2017 licencované pro podnikové použití v klientovi mezi celým rozsahem verze produktu 15.0.0 až 15.9.0 a aktualizuje tyto klientské edice na 15.9.0. Použití tohoto balíčku funkcí v podstatě umožní klientům získávat aktualizace zabezpečení. 
* **Visual studio 2017 verze 15.9.0 až 15.9.37 Update** klasifikovaná jako jednoduše "Updates" se vztahuje na edice sady Visual Studio 2017 licencované pro podnikové použití v klientovi mezi verzemi 15.9.0 až 15.9.37 a aktualizuje tyto klientské edice na 15.9.37.

::: moniker-end

::: moniker range="vs-2019"

* **Visual studio 2019 verze 16.7.0 až 16.7.12 Update** klasifikovaná jako aktualizace zabezpečení se bude vztahovat na všechny edice sady visual Studio 2019 na klientovi mezi verzemi 16.7.0 až 16.7.12 a tyto klientské edice budou aktualizovat na 16.7.12.  
* Sada **Visual studio 2019 verze 16.0.0 až 16.9.0 Update** klasifikovaná jako "Feature Pack" bude platit pro edice sady visual Studio 2019 licencované pro podnikové použití v klientovi mezi celým rozsahem verze produktu 16.0.0 až 16.9.0 a aktualizuje tyto klientské edice (které nebyly nakonfigurovány tak, aby zůstaly na dřívější směrné plány údržby) do 16.9.0. 
* **Visual studio 2019 verze 16.8.0 až 16.8.7 Update** klasifikovaná jako jednoduše "Updates" se vztahuje na edice sady Visual Studio 2019 licencované pro podnikové použití v klientovi mezi verzemi 16.8.0 až 16.8.7 a aktualizuje tyto klientské edice na 16.8.7.

::: moniker-end

::: moniker range=">=vs-2022"

::: moniker-end

## <a name="using-configuration-manager-to-deploy-visual-studio-updates"></a>Nasazení aktualizací sady Visual Studio pomocí Configuration Manager

### <a name="understanding-configuration-options"></a>Principy možností konfigurace

K dispozici je několik možností konfigurace, které můžete použít k přizpůsobení aktualizací pro správce sady Visual Studio, aby byly kompatibilní a zarovnané na Předvolby a požadavky pro nasazení vaší organizace. Níže jsou uvedené nejběžnější možnosti konfigurace. Úplný seznam všech podporovaných chování aktualizací správců najdete v tématu [použití parametrů příkazového řádku k instalaci sady Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) a placení pozornosti jenom na ty, které odpovídají akci aktualizace.

* **[Výslovný souhlas s aktualizací správce](../install/enabling-administrator-updates.md#encoding-administrator-intent-on-the-client-machines)**: Tento klíč registru je nutný k tomu, aby klientský počítač mohl přijímat aktualizace správce. Je klíč celého počítače, což znamená, že se vztahuje na všechny instance sady Visual Studio nainstalované v poli.
* **Odsouhlasení uživatele sady Visual Studio**: uživatelé sady Visual Studio mohou použít samostatný klíč registru **AdministratorUpdatesOptOut** v rámci počítače k *odsouhlasení* s přijímáním aktualizací pro správce sady Visual Studio. Účelem tohoto klíče je dovolit uživateli aplikace Visual Studio mít určitou kontrolu nad tím, že se aktualizace automaticky aplikují na daný počítač. Chcete-li nakonfigurovat klientský počítač pro blokování aktualizací správců, **** nastavte   klíč REG_DWORD AdministratorUpdatesOptOut na hodnotu **1**. Absence klíče nebo nastavená hodnota **0** znamená, že uživatel sady Visual Studio chce dostávat aktualizace správce do sady Visual Studio.
    Všimněte si, že klíč **AdministratorUpdatesOptOut**   pro kódování uživatelských preferencí je nastaven na prioritu prostřednictvím klíče **AdministratorUpdatesEnabled**   , který zakóduje záměr správce IT. Pokud je **AdministratorUpdatesOptOut**   nastavené na **1**, aktualizace se zablokuje na klientovi, a to i v případě, že je klíč **AdministratorUpdatesEnabled**   také nastavený na hodnotu **1**.Tato akce předpokládá, že správci IT můžou získat přístup k vybraným vývojářům a sledovat, které z nich se můžou odhlásit a že dvě strany si pak mohou projednávat, které potřeby jsou důležitější.Správci IT můžou vždycky kdykoli změnit libovolný klíč.
* **Umístění aktualizovaných aktualizací softwaru**: ve většině případů klientské počítače stáhnou aktualizované produktové bity z Internetu přes Microsoft CDN. Tento scénář vyžaduje, aby klientské počítače měly přístup k Internetu. Některé podniky ale omezují klientské počítače jenom na instalaci a aktualizaci BITS z umístění rozložení interní sítě. Aby bylo zajištěno, že aktualizace správce lze použít pomocí aktualizovaných bitů v umístění interní sítě, musí být splněny následující podmínky před tím, než bude možné úspěšně nasadit aktualizaci správce: 
  * Klientský počítač musí v určitém okamžiku spustit zaváděcí nástroj z umístění rozložení sítě. V ideálním případě by k původní instalaci klienta došlo pomocí zaváděcího nástroje z rozložení sítě, ale je také možné, že jste právě nainstalovali aktualizaci pomocí aktualizovaného zaváděcího nástroje na stejném umístění v síti. Jedna z těchto akcí by mohla být vložena na klientském počítači, připojení s tímto umístěním rozložení.
  * Umístění rozložení sítě (kde je klient připojen k) se musí [aktualizovat tak, aby obsahovalo aktualizované bity produktu](../install/update-a-network-installation-of-visual-studio.md) , které chce správce nasadit.

::: moniker range=">=vs-2019"

* **Vytrvalost směrného plánu údržby**: jak je popsáno výše, aktualizace funkcí správce napřed instalaci sady Visual Studio na aktuálnější podverzi produktu. V některých případech však uživatelé sady Visual Studio musí zůstat na konkrétní stabilní úrovni a na úrovni standardních hodnot údržby a chtějí řídit, kdy jejich počítače přestanou na aktuálnější vedlejší verzi. Chcete-li nakonfigurovat klientský počítač tak, aby zůstal na směrném plánu obsluhy a ignoroval nepožadované aktualizace funkcí správce, je nutné vytvořit a nastavit hodnotu **BaselineStickinessVersions2019** REG_SZ dat na řetězec, který představuje preferovaný směrný plán, který by měl klientský počítač přitahovat a zůstat zapnutý. Řetězec může obsahovat základní verzi údržby, jako je **16.7.0**.  
     Pokud `BaselineStickinessVersions2019` je hodnota registru poškozená, všechny aktualizace funkcí správce budou na počítači zablokovány. Nezapomeňte věnovat pozornost [podporovaným časovým obdobím aktualizací funkcí sady Visual Studio](/visualstudio/productinfo/vs-servicing-vs). Bez ohledu na přítomnost a hodnotu `BaselineStickinessVersions2019` klíče, i když je technicky možné použít aktualizace funkcí správce, které byly dosaženy na konci jejich životnosti, nedoporučujeme, protože nebudou podporovány a tedy potenciálně nezabezpečené.

::: moniker-end

* **Vynutit, aby se aktualizace nastala i v případě, že se používá Visual Studio**: před instalací této aktualizace je nutné aplikaci Visual Studio zavřít. Pokud je aplikace Visual Studio otevřená nebo používaná, instalace aktualizace se ukončí. Snadný způsob, jak zajistit, že je Visual Studio zavřené, je nakonfigurovat Správce potvrzení tak, aby po restartování počítače použili aktualizaci hned. `--force`K vynucení vypnutí sady Visual Studio můžete použít také parametr. Vynucené ukončení sady Visual Studio může způsobit ztrátu práce, takže je používejte opatrně. Spuštění aktualizace správce ve výchozím kontextu systému bude ignorovat `–-force` příznak, takže budete muset nakonfigurovat, aby se aktualizace správce spouštěla v uživatelském kontextu.

### <a name="methods-for-configuring-an-administrator-update"></a>Metody konfigurace aktualizace správce

Existují tři hlavní metody konfigurace aktualizací správců: klíč registru, konfigurační soubor v klientském počítači nebo změna samotného balíčku pro nasazení Configuration Manager.   

* **Klíč registru**: aktualizace správců hledají konkrétní klíče registru ve všech standardních umístěních sady Visual Studio, jak je popsáno v tématu [Nastavení výchozích hodnot pro podniková nasazení](../install/set-defaults-for-enterprise-deployments.md). Možnosti, které jsou ovládány klíči registru, jsou položky jako **AdministratorUpdatesOptOut** REG_DWORD, **AdministratorUpdatesOptOut**   REG_DWORD a **BaselineStickinessVersions2019** REG_SZ. Pro vytvoření a nastavení hodnoty klíčů registru je nutný přístup správce na klientském počítači.

* **Konfigurační soubor**: některá nastavení je možné zachovat v klientském počítači v případě volitelného konfiguračního souboru, který má výhodu nastavení jenom jednou a použije se pro všechny budoucí aktualizace správců. Přístup ke konfiguračnímu souboru se chová jako klíč registru a je celý počítač, což znamená, že se bude vztahovat na všechny instalace sady Visual Studio nainstalované v klientském počítači. Standardní umístění konfiguračního souboru je `C:\ProgramData\Microsoft\VisualStudio\updates.config` . Pokud však chcete použít jiné umístění pro uložení souboru, můžete tak učinit tak, že vytvoříte Reg_SZ klíč registru s názvem **UpdateConfigurationFile** a nastavíte hodnotu tohoto klíče na cestu k konfiguračnímu souboru. Tento klíč registru může být umístěn v libovolném umístění registru sady Visual Studio, jak je popsáno v tématu [Nastavení výchozích hodnot pro podniková nasazení](../install/set-defaults-for-enterprise-deployments.md). Pokud se rozhodnete přidat hodnotu registru pro vlastní umístění konfiguračního souboru, bude tento soubor hledat. Pokud soubor neexistuje, vyvolá se výjimka a aktualizace se nezdaří.

     Konfigurační soubor, který je ve formátu JSON, podporuje možnost, `installerUpdateArgs` což je pole řetězců oddělené čárkami, které určují více přepínačů, které můžete předat instalačnímu programu sady Visual Studio. Pokud obsah souboru obsahuje neplatné pole nebo možnost, která není podporována, aktualizace nebude úspěšná. Další informace najdete v tématu [použití parametrů příkazového řádku k instalaci sady Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md).

   Tady je příklad konfiguračního souboru:

  ```json
  "installerUpdateArgs" : ["--quiet", "--noWeb"], 
  "checkPendingReboot" :  "true" 
  ```

* **Ruční aktualizace balíčku aktualizace pro správce v nástroji SCCM**: parametry příkazového řádku samostatného balíčku aktualizace správce v nástroji SCCM lze také ručně změnit.

## <a name="verification-reports-and-troubleshooting-error-codes"></a>Ověřování, sestavy a chybové kódy pro řešení potíží

### <a name="determining-that-visual-studio-was-updated"></a>Určení, že se aktualizovala aplikace Visual Studio

K ověření, zda byla aktualizace správce nainstalována správně, můžete použít jednu z následujících metod:

* V klientském počítači spusťte sadu Visual Studio, vyberte možnost **nápovědu**   >  **** a ověřte, zda číslo verze odpovídá poslednímu číslu v názvu zamýšlené aktualizace.
* Pomocí nástroje **vswhere** na klientském počítači Identifikujte různé verze sady Visual Studio v počítači. Další informace najdete v tématu [Nástroje pro zjišťování a správu instancí sady Visual Studio](../install/tools-for-managing-visual-studio-instances.md).
* Každý pokus o aktualizaci správy generuje v adresáři klientského počítače několik souborů protokolu `%temp%` , které zachycují průběh operace aktualizace.Seřaďte složku podle data a vyhledejte soubory, které začínají  `dd_updatedriver` ,  `dd_bootstrapper` ,  `dd_client` a  `dd_setup`   pro aktualizace pro správu, zaváděcí nástroj, instalační program pro Visual Studio a instalační modul, v uvedeném pořadí.Ověřte, zda tyto soubory protokolu obsahují hodnotu 0, což znamená, že byla aktualizace úspěšně provedena. Všimněte si, že tyto soubory protokolů lze také použít k ověření, že se konfigurační soubor používá. Další podrobnosti najdete v tématu [Nástroj pro shromažďování protokolů sady Visual Studio](https://www.microsoft.com/download/details.aspx?id=12493) .

### <a name="error-codes-and-conditions"></a>Chybové kódy a podmínky

>[!IMPORTANT]
> Nezapomeňte, že před instalací aktualizace musí být aplikace Visual Studio zavřená. Pokud je aplikace Visual Studio otevřená nebo používaná, instalace aktualizace se zruší.

Aktualizace pro správu mohou vracet následující návratové kódy:  

| Kód chyby | Definice                                                                                                                                                                                                  |
|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0          | Aktualizace pro správu se úspěšně nainstalovala.                                                                                                                                                       |
| 1001       | Je spuštěný Instalační program pro Visual Studio nebo související proces instalace. Aktualizace se nepoužívá.                                                                                                                   |
| 1002       | Instalační program pro Visual Studio je pozastavená. Aktualizace se nepoužívá.                                                                                                                                               |
| 1003       | Je spuštěná aplikace Visual Studio. Aktualizace se nepoužívá. Tento stav může být použit jako nepravidelný pomocí `--force` příznaku.                                                                                              |
| 1004       | Nebylo zjištěno žádné připojení k Internetu.Aktualizace nemohla kontaktovat internetové umístění, kde se nacházejí aktualizované soubory. Aktualizace se nepoužívá.                                                                          |
| 1005       |  ****   Hodnota registru AdministratorUpdatesEnabled je nastavená na hodnotu **0** nebo není nastavená vůbec. Aktualizace se nepoužívá.                                                                                            |
| 1006       |  ****   Hodnota registru AdministratorUpdatesOptOut je nastavená na **1**. Aktualizace se nepoužívá. Klíč je určený pro klientské počítače, které by správce neměl aktualizovat.                     |
| 1007       | Instalační program pro Visual Studio není nainstalován.                                                                                                                                                               |
| 1008       | Hodnota registru **BaselineStickinessVersions2019** není v čitelném formátu. Hodnota registru musí zahrnovat **všechny** nebo platné verze s číslem sestavení nastaveným na hodnotu 0 explicitně, například X. Y. 0. |
| 3010       | Systém vyžaduje restart.Aktualizace možná nebo nemusí být použitá. Restartujte počítač a zkuste aktualizaci zopakovat.                                                                                |
| Jiné      | Při pokusu o instalaci aktualizace došlo k chybě.Aktualizace se nepoužívá.                                                                                                                                   |

Vyčerpávající seznam kódů chyb klienta najdete v tématu věnovaném [použití parametrů příkazového řádku k instalaci sady Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

## <a name="feedback-and-support"></a>Zpětná vazba a podpora

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

Pomocí následujících metod můžete poskytnout zpětnou vazbu o aktualizacích správce sady Visual Studio nebo nahlásit problémy, které mají vliv na aktualizace:

* Přečtěte si pokyny k [řešení potíží s instalací a upgradem sady Visual Studio](../install/troubleshooting-installation-issues.md) .
* Položte otázky do komunity v [instalačním programu sady Visual Studio Q&Fórum](/answers/topics/vs-setup.html).
* Přejít na [stránku podpory sady Visual Studio](https://visualstudio.microsoft.com/vs/support/)a ověřte, zda je váš problém uveden v části Nejčastější dotazy.  Můžete také vybrat tlačítko pro [odkaz na podporu](https://visualstudio.microsoft.com/vs/support/#talktous) pro nápovědu k chatu.
* [Poskytněte zpětnou vazbu k funkcím nebo nahlásit problém](https://aka.ms/vs/wsus/feedback) týmu sady Visual Studio, pokud jde o toto prostředí při použití aktualizací správců.
* Obraťte se na správce technického účtu vaší organizace pro Microsoft.

## <a name="see-also"></a>Viz také

* [Povolení aktualizací správců](../install/enabling-administrator-updates.md)
* [Příručka správce sady Visual Studio](../install/visual-studio-administrator-guide.md)
* [Životní cyklus produktu Visual Studio a jeho údržba](/visualstudio/productinfo/vs-servicing-vs)
* [Zpráva k vydání verze pro Visual Studio 2019](/visualstudio/releases/2019/release-notes)
* [Zpráva k vydání verze pro Visual Studio 2017](/visualstudio/releasenotes/vs2017-relnotes)
* [Instalace sady Visual Studio](../install/install-visual-studio.md)
* [Použití parametrů příkazového řádku k instalaci sady Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md)
* [Nástroje pro zjišťování a správu instancí sady Visual Studio](../install/tools-for-managing-visual-studio-instances.md)
* [Vytvoření síťové instalace sady Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
* [Definování nastavení v souboru odpovědí](../install/automated-installation-with-response-file.md)
* [Řízení aktualizací pro nasazení sady Visual Studio založené na síti](../install/controlling-updates-to-visual-studio-deployments.md)
* [Nejčastější dotazy ke katalogu Microsoft Update](https://www.catalog.update.microsoft.com/faq.aspx)
* [Dokumentace k Microsoft Endpoint Configuration Manager (SCCM)](/mem/configmgr)
* [Import aktualizací z katalogu Microsoft do Configuration Manager](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Windows Server Update Services (WSUS) – dokumentace](/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
