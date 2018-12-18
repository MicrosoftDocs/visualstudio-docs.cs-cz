---
title: 'Postupy: Přidání nebo odebrání odkazů pomocí Správce odkazů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- Visual C# projects, references
- references [Visual Studio], adding
- assemblies [Visual Studio], references
- Visual Basic projects, references
- project references, adding
- referencing components, adding references
- project references, removing
- referencing assemblies
- referencing components, removing references
- references [Visual Studio], removing
- referencing components, assemblies not listed
ms.assetid: 1aabb520-99b0-46c6-9368-21b4d84793eb
caps.latest.revision: 48
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 82e09b1d27c8ac7905fd0e6511381b97fcae2cd7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917546"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Postupy: Přidání nebo odebrání odkazů pomocí správce odkazů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít **správce odkazů** dialogové okno Přidat a spravovat odkazy na součásti, které jste společnosti Microsoft, nebo jiné firmy vyvíjí. Pokud vyvíjíte aplikace Universal Windows, váš projekt automaticky odkazuje na všechny správné DLL knihovny Windows SDK. Pokud vyvíjíte aplikaci .NET, váš projekt se automaticky odkazuje na knihovnu mscorlib.dll. Některá rozhraní API .NET jsou přístupné na součásti, které je nutné přidat ručně. Odkazy na součásti modelu COM nebo vlastní součásti nutné přidat ručně.  
  
## <a name="adding-and-removing-a-reference"></a>Přidání a odebrání odkazu  
  
#### <a name="to-add-a-reference"></a>Přidání odkazu  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel odkazy a zvolte **přidat odkaz**.  
  
2. Určete odkazy, které chcete přidat a pak klikněte **OK** tlačítko.  
  
   **Správce odkazů** otevře a zobrazí seznam dostupných odkazů seřazených ve skupinách. Typ projektu určuje, které z těchto skupin se zobrazí:  
  
-   Skupina Sestavení s podskupinami Rozhraní a Rozšíření  
  
-   Skupina Řešení s podskupinou Projekty  
  
-   Skupina Windows s podskupinami Jádro a Rozšíření. Odkazy v sadě Windows SDK nebo rozšiřujících sadách SDK můžete prozkoumat pomocí **prohlížeče objektů**.  
  
-   Skupina Procházení s podskupinou Nedávné  
  
## <a name="assemblies-tab"></a>Karta Sestavení  
 **Sestavení** karta obsahuje seznam všech sestavení rozhraní .NET Framework, které jsou k dispozici pro odkazování. **Sestavení** kartu neobsahuje žádná sestavení z globální mezipaměti sestavení (GAC), protože sestavení v GAC jsou součástí běhového prostředí. Pokud nasadíte nebo zkopírujete aplikaci, která obsahuje odkaz na sestavení registrované v GAC, nebude toto sestavení nasazeno nebo zkopírováno spolu s aplikací, a to bez ohledu na nastavení Kopírovat místní. Další informace najdete v tématu [odkazy na projekt](http://go.microsoft.com/fwlink/?LinkId=238512).  
  
 Pokud ručně přidáte odkaz na jakýkoli obor názvů EnvDTE (EnvDTE, EnvDTE80, EnvDTE90, EnvDTE90a nebo EnvDTE100), nastavte vlastnost Vložit typy spolupráce pro daný odkaz v okně Vlastnosti na hodnotu Nepravda. Nastavení této vlastnosti na hodnotu Pravda může způsobit problémy sestavení z důvodu určitých vlastností EnvDTE, které není možné vložit.  
  
 Všechny projekty určené pro klasickou plochu obsahují implicitní odkaz na knihovnu mscorlib. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekty obsahují implicitní odkaz na Microsoft.VisualBasic. V [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], všechny projekty obsahují implicitní odkaz na System.Core, i když je odebrán ze seznamu odkazů.  
  
 Pokud typ projektu nepodporuje sestavení, na kartě nezobrazí v **správce odkazů** dialogové okno.  
  
 Karta Sestavení se skládá ze dvou dílčích karet:  
  
1. Karta Rozhraní obsahuje všechna sestavení, která tvoří cílené rozhraní.  
  
   -   Inzerovaná sestavení se nacházejí v plné verzi rozhraní a jejich výčet je uveden v seznamu rozhraní, jestliže váš projekt cílí na profil cíleného rozhraní. Inzerovaná sestavení jsou zobrazena šedou barvou z důvodu odlišení od sestavení, která existují v cíleném profilu Rozhraní daného projektu. Pokud například projekt cílí na rozhraní .NET Framework 4 Client, seznam rozhraní obsahuje inzerovaná sestavení z rozhraní .NET Framework 4. Při přidání inzerovaného sestavení, je mu oznámeno, že po **správce odkazů** zavření okna, projekt se změní cílení na rozhraní .NET Framework 4 a přidá dané inzerované sestavení.  
  
   -   Projekty pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace obsahují odkazy na všechna sestavení v cíleném [!INCLUDE[net_win8_profile](../includes/net-win8-profile-md.md)] ve výchozím nastavení při vytvoření projektu. Ve spravovaných projektech, uzel jen pro čtení ve složce odkazy v **Průzkumníka řešení** označuje odkaz na celé rozhraní. Proto tedy karta Rozhraní nezobrazí žádná sestavení z rozhraní a namísto toto se zobrazí následující zpráva: „Na všechna sestavení rozhraní je již odkazováno. Použijte prohlížeč objektů pro prozkoumání odkazů rozhraní Framework." Pro desktopové projekty karta rozhraní zobrazuje sestavení z cíleného rozhraní a uživatel musí přidat odkazy, které aplikace vyžaduje.  
  
2. Karta Rozšíření obsahuje seznam všech sestavení, která vyvinuli externí dodavatelé součástí a ovládacích prvků za účelem rozšíření cíleného rozhraní. Podle účelu dané aplikace mohou být tato sestavení potřebná.  
  
   -   Karta Rozšíření zobrazuje výčet sestavení, která jsou zaregistrována v následujících umístěních:  
  
       ```  
       32-bit machine:  
       HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
       HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
       64-bit machine:  
       HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
       HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
       And older versions of the [Target Framework Identifier]  
       ```  
  
        Pokud projekt cílí na rozhraní .NET Framework 4 na 32bitovém počítači, například vytvoří rozšíření výčet sestavení, která jsou registrována pod \Microsoft\\. NETFramework\v4.0\AssemblyFoldersEx\\, \Microsoft\\. NETFramework\v3.5\AssemblyFoldersEx\\, \Microsoft\\. NETFramework\v3.0\AssemblyFoldersEx\\a \Microsoft\\. NETFramework\v2.0\AssemblyFoldersEx\\.  
  
   Některé součásti v seznamu se nemusí zobrazit, v závislosti na tom [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verzi vašeho projektu. Tato situace může nastat za následujících podmínek:  
  
-   Komponenta, která používá nejnovější verzi rozhraní .NET Framework je nekompatibilní s projektem, který se zaměřuje na starší verzi rozhraní .NET Framework.  
  
     Informace o tom, jak změnit cílovou verzi rozhraní .NET Framework pro projekt, naleznete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
-   Komponenty, která používá [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] je nekompatibilní s projektem, který se zaměřuje [!INCLUDE[net_v45](../includes/net-v45-md.md)].  
  
     Když vytvoříte novou aplikaci, některé projekty zaměřují [!INCLUDE[net_v45](../includes/net-v45-md.md)] ve výchozím nastavení. Další informace najdete v tématu [rozhraní .NET Framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).  
  
-   Můžete byste se vyhnout přidávání odkazů na soubory do výstupů jiného projektu ve stejném řešení, protože to může způsobit chyby kompilace. Místo toho použijte **projekty** karty **přidat odkaz** dialogové okno k vytvoření odkazů typu projekt projekt. Toto usnadňuje vývoj v týmu povolením lepší správy knihoven tříd, které vytvoříte ve svých projektech. Další informace najdete v tématu [řešení potíží s nefunkční odkazy](../ide/troubleshooting-broken-references.md).  
  
-   > [!NOTE]
    >  V sadě Visual Studio 2015 je odkaz na soubor místo odkazu na projekt vytvořen, pokud cílová verze rozhraní .NET Framework jednoho projektu je verze 4.5 a cílová verze jiného projektu je verze 2, 3, 3.5 nebo 4.0.  
  
#### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Zobrazení sestavení v dialogovém okně Přidat odkaz  
  
- Přesuňte nebo zkopírujte sestavení do jednoho z následujících umístění:  
  
  - Aktuální adresář projektu. (Můžete vyhledat tato sestavení pomocí **Procházet** tab.)  
  
  - Další adresáře projektu ve stejném řešení. (Můžete vyhledat tato sestavení pomocí **projekty** tab.)  
  
    \- nebo –  
  
- Nastavte klíč registru určující umístění sestavení, které chcete zobrazit:  
  
   Pro 32bitový operační systém přidejte jeden z následujících klíčů registru.  
  
  - [HKEY_CURRENT_USER\SOFTWARE\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"  
  
  - [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"  
  
    Pro 64bitový operační systém přidejte jeden z následujících klíčů registru v 32 bitů podregistru.  
  
  - [HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"  
  
  - [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"  
  
    *VersionMinimum* je nejnižší verze rozhraní .NET Framework, která se použije. Pokud *VersionMinimum* je v3.0, složky zadané v AssemblyFoldersEx platí pro projekty, které cílí na .NET Framework 3.0 nebo novější.  
  
    *AssemblyLocation* je adresář sestavení, která se má zobrazit v **přidat odkaz** dialogové okno, například C:\MyAssemblies\\.  
  
    Vytvoření klíče registru pod uzlem HKEY_LOCAL_MACHINE umožňuje všem uživatelům zobrazit sestavení v zadaném umístění v **přidat odkaz** dialogové okno. Vytvoření klíče registru pod uzlem HKEY_CURRENT_USER ovlivní pouze nastavení pro aktuálního uživatele.  
  
    Otevřít **přidat odkaz** dialog již příště nezobrazovat. Sestavení by se měla objevit na **.NET** kartu. Pokud tomu tak není, ujistěte se, že sestavení jsou umístěny v zadaném *AssemblyLocation* adresáře, restartujte Visual Studio a zkuste to znovu.  
  
## <a name="com-tab"></a>Karta COM  
 Karta COM obsahuje seznam všech komponent COM, které jsou k dispozici pro odkazování. Pokud chcete přidat odkaz na registrovanou knihovnu DLL modelu COM, která obsahuje vnitřní manifest, nejprve zrušte registraci dané knihovny DLL. V opačném případě sada Visual Studio přidá odkaz na sestavení jako ovládací prvek ActiveX namísto jako nativní knihovnu DLL.  
  
 Pokud typ projektu nepodporuje model COM, nebude tato karta se v **správce odkazů** dialogové okno.  
  
## <a name="solution-tab"></a>Karta Řešení  
 Na kartě Řešení jsou uvedeny všechny kompatibilní projekty v aktuálním řešení, a to na dílčí kartě Projekty.  
  
 Projekt může odkazovat na jiný projekt, který cílí na jinou verzi rozhraní .NET Framework. Například můžete vytvořit projekt, který cílí [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] , ale který odkazuje na sestavení vytvořené pro rozhraní .NET Framework 2. Však nemůže odkazovat na rozhraní .NET Framework 2 projekt [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] projektu. Další informace najdete v tématu [cílení na konkrétní verzi rozhraní .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
 Projekt, který se zaměřuje [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] je nekompatibilní s projektem, který se zaměřuje [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)].  
  
 V [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], odkaz na soubor místo odkazu na projekt je vytvořen, pokud jeden projekt cílí na rozhraní .NET Framework 4 a jiný projekt cílí na dřívější verzi.  
  
 Projekt, který se zaměřuje [!INCLUDE[net_win8_profile](../includes/net-win8-profile-md.md)] nelze přidat odkaz na projekt do projektu, který cílí na rozhraní .NET Framework a naopak versa.  
  
## <a name="windows-tab"></a>Karta Windows  
 Karta Windows obsahuje všechny sady SDK, které jsou specifické pro platformy, na kterých běží operační systém Windows.  
  
 Soubor WinMD je možné v sadě Visual Studio vygenerovat dvěma způsoby:  
  
- **[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] spravované projekty aplikací**: [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projekty aplikací můžete výstup binární soubory WinMD nastavením vlastnosti projektu &#124; typ výstupu na soubor WinMD. Název souboru WinMD musí představovat nadřazený obor názvů všech oborů názvů, které existují jeho v rámci. Pokud například projekt obsahuje obory názvů A.B a A.B.C, možné názvy pro soubory WinMD na jeho výstupu jsou A.winmd a A.B.winmd. Pokud uživatel zadá vlastnosti projektu &#124; název sestavení nebo vlastnosti projektu &#124; Namespace hodnotu, která je mimo sadu oborů názvů v projektu nebo není žádný nadřazený obor názvů v rámci projektu, vygeneruje se upozornění sestavení: "A.winmd není platný název souboru .winmd pro toto sestavení. Všechny typy v rámci souboru metadat systému Windows musejí existovat v podřízeném oboru názvů daného názvu souboru. Typy, které neexistují v podřízeném oboru daného názvu souboru, nebude možné za běhu nalézt. V tomto sestavení je nejmenší společný obor názvů CSWSClassLibrary1“. Desktopový projekt jazyka Visual Basic nebo Visual C# může využívat pouze soubory Winmd vygenerované pomocí [!INCLUDE[win8](../includes/win8-md.md)] sad SDK, které jsou známy jako soubory Winmd první strany a nemůže generovat soubory Winmd.  
  
- **[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Nativní projekty aplikací**: nativní soubor WinMD obsahuje pouze metadata. Jeho implementace se nachází v samostatném souboru knihovny DLL. Výběrem šablonu projektu součásti prostředí Windows Runtime v je možné vytvořit nativní binární soubory **nový projekt** dialogové okno nebo spuštěním prázdným projektem a upravíte vlastnosti projektu pro vytvoření souboru WinMD. Pokud projekt obsahuje nesouvislé obory názvů, chyba sestavení oznámí uživateli, aby sloučit své obory názvů nebo spustit nástroj MSMerge.  
  
  Karta Windows se skládá ze dvou podskupin.  
  
### <a name="core-subgroup"></a>Podskupina Jádro  
 Podskupina Jádro obsahuje seznam všech souborů WinMD (pro elementy prostředí Windows Runtime) v sadě SDK pro cílenou verzi systému Windows.  
  
 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] odkazy na všechny soubory winmd v obsahují projekty aplikací [!INCLUDE[win8](../includes/win8-md.md)] SDK ve výchozím nastavení při vytvoření projektu. Ve spravovaných projektech, uzel jen pro čtení ve složce odkazy v **Průzkumníka řešení** označuje odkaz na celý [!INCLUDE[win8](../includes/win8-md.md)] SDK. Proto podskupina jádro ve Správci odkazů nezobrazí seznam všech sestavení ze [!INCLUDE[win8](../includes/win8-md.md)] sady SDK a místo toho zobrazí zpráva: "Windows SDK se už odkazuje. Pomocí Prohlížeče objektů můžete prozkoumat odkazy v sadě Windows SDK.“  
  
 V projektech aplikací pro klasickou plochu se ve výchozím nastavení podskupina Jádro nezobrazuje. Modul Windows Runtime můžete přidat tak, že otevřete místní nabídku uzlu projektu zvolíte **uvolnit projekt**, přidáte následující fragment kódu a znovu otevřete projekt (na uzel projektu, zvolte **znovu načíst projekt**). Při vyvolání **správce odkazů** se zobrazí podskupina jádro dialogovém okně.  
  
```  
<PropertyGroup>  
  <TargetPlatformVersion>8.0</TargetPlatformVersion>  
</PropertyGroup>  
```  
  
 Je nutné vybrat **Windows** v této podskupině zaškrtávací políčko. Poté budete moci používat elementy prostředí Windows Runtime. Je také vhodné přidat System.Runtime, ve kterém Windows Runtime definuje některé standardní třídy a rozhraní, například rozhraní IEnumerable, které se používají v knihovnách prostředí Windows Runtime. Informace o tom, jak přidat System.Runtime, naleznete v tématu [spravované aplikace klasické pracovní plochy a prostředí Windows Runtime](http://msdn.microsoft.com/library/windows/apps/jj856306.aspx#consuming_standard_windows_runtime_types).  
  
### <a name="extensions-subgroup"></a>Podskupina Rozšíření  
 Podskupina Rozšíření obsahuje seznam uživatelských sad SDK, které rozšiřují cílenou platformu Windows. Na této kartě se zobrazí pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] pouze pro projekty aplikací. Projekty aplikací pro klasickou plochu tuto kartu nezobrazují, protože používají pouze soubory .winmd první strany.  
  
 Sada SDK je kolekce souborů, které sada Visual Studio považuje za jedinou součást. Na kartě rozšíření jsou sady SDK, které platí pro projekt, ze kterých **správce odkazů** bylo vyvoláno dialogové jsou uvedeny jako jedna položka. Po přidání do projektu je veškerý obsah sady SDK využíván sadou Visual Studio tak, že uživatel nemusí provádět žádné další akce za účelem využití obsahu sady SDK v prostředí IntelliSense, sadě nástrojů, návrhářích, Prohlížeči objektů, sestavení, nasazení, ladění a balení. Informace o tom, jak zobrazit vaši sadu SDK na kartě rozšíření najdete v tématu [vytváření Software Development Kit](../extensibility/creating-a-software-development-kit.md).  
  
> [!NOTE]
>  Pokud se projekt odkazuje na sadu SDK, která závisí na jiné sadě SDK, sada Visual Studio nebude využívat druhou sadu SDK, pokud uživatel ručně nepřidá odkaz na tuto druhou sadu SDK. Když uživatel vybere sadu SDK na **rozšíření** karta, **správce odkazů** dialogové okno pomáhá uživateli určit závislosti sady SDK uvedením nejen název a verzi sady SDK, ale také název všechny sady SDK závislosti v podokně podrobností. Pokud si uživatel nevšimne závislostí a přidá pouze sadu SDK, nástroj MSBuild vyzve uživatele k přidání závislostí.  
  
 Pokud typ projektu nepodporuje **rozšíření**, nebude tato karta se v **správce odkazů** dialogové okno.  
  
## <a name="browse-button"></a>Tlačítko Procházet  
 Můžete použít **Procházet** tlačítko vyhledat součást v systému souborů.  
  
 Projekt se může odkazovat na součást, která cílí na jinou verzi rozhraní .NET Framework. Můžete například vytvořit aplikaci, která cílí na rozhraní .NET Framework 4 Client Profile, jež odkazuje na součást, která cílí na rozhraní .NET Framework 2. Další informace najdete v tématu [cílení na konkrétní verzi rozhraní .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
 Měli byste se vyhnout přidávání odkazů na soubory do výstupů jiného projektu ve stejném řešení, protože to může vést k chybám při kompilaci. Místo toho použijte **řešení** karty **správce odkazů** dialogové okno k vytvoření odkazů typu projekt projekt. Tento postup usnadňuje vývoj v týmu, neboť umožňuje lepší správu knihoven tříd, které vytvoříte ve svých projektech. Další informace najdete v tématu [řešení potíží s nefunkční odkazy](../ide/troubleshooting-broken-references.md).  
  
 Nemůžete přejít k sadě SDK a přidat ji do projektu. Je možné přejít pouze k souboru (například sestavení nebo souboru .winmd) a přidat jej do projektu.  
  
 Při provádění odkaz na soubor na o soubor WinMD je očekávané rozložení je, že *FileName*.winmd, *FileName*.dll, a *FileName*soubory .pri jsou umístěny spolu. Pokud odkazujete na soubor WinMD v následujících scénářích, do výstupního adresáře projektu budou zkopírovány neúplné sady souborů a v důsledku toho dojde k chybám při sestavení a za běhu.  
  
-   **Nativní součást**: nativní projekt vytvoří jeden soubor WinMD pro každou sadu nesouvislých oborů názvů a jednu knihovnu DLL, který se skládá z implementace. Soubory WinMDs budou mít nesouvislé názvy. Při odkazování na tento soubor nativní součásti nástroj MSBuild nerozpozná, že tyto různě nazvané soubory WinMD tvoří jednu součást. V důsledku toho pouze identicky pojmenované *FileName*.dll a *FileName*zkopírují .winmd a dojde k chybám za běhu. Chcete-li tento problém vyřešit, vytvořte rozšiřující sadu SDK. Další informace najdete v tématu [vytváření Software Development Kit](../extensibility/creating-a-software-development-kit.md).  
  
-   **Využívající ovládací prvky**:, ovládací prvek XAML přinejmenším z *FileName*.winmd, *FileName*.dll, *FileName*.pri, *XamlName* .xaml a *ImageName*.jpg. Při sestavení projektu nebudou soubory prostředků, které jsou spojeny s odkaz na soubor získat zkopírovány do výstupního adresáře projektu a to jenom *FileName*.winmd, *FileName*.dll a *FileName*.pri budou zkopírovány. Bude zaznamenána chyba sestavení informovat uživatele, který prostředky *XamlName*.xaml a *ImageName*.jpg nebyly nalezeny. Aby sestavení proběhlo úspěšně, bude uživatel muset ručně zkopírovat tyto soubory prostředků do výstupního adresáře projektu pro sestavení a ladění/dobu běhu. Chcete-li tento problém obejít, buď vytvořte rozšiřující sadu SDK pomocí kroků v [vytváření Software Development Kit](../extensibility/creating-a-software-development-kit.md) nebo upravit soubor projektu a přidejte následující vlastnost:  
  
    ```  
    <PropertyGroup>  
    <GenerateLibraryOutput>True</GenerateLibraryOutput>  
    </PropertyGroup>  
    ```  
  
    > [!NOTE]
    >  Pokud tuto vlastnost přidáte, může být sestavení pomalejší.  
  
## <a name="recent"></a>Nedávné  
 Kartu Nedávné podporují karty Sestavení, COM, Windows a Procházet. Tato karta obsahuje seznam součástí, které byly v poslední době přidány do projektu.  
  
## <a name="search"></a>Hledat  
 Na panelu hledání v **správce odkazů** dialogové okno funguje na kartě, která je aktivní. Například, pokud uživatel zadá panelu hledání text "Systém" **řešení** má fokus karta, vyhledávání nevrátí žádné výsledky, pokud řešení obsahuje název projektu, který obsahuje "slovo systém".  
  
## <a name="see-also"></a>Viz také  
 [NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)



