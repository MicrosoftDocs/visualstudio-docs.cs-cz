---
title: 'Postupy: Přidání nebo odebrání odkazů pomocí Správce odkazů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1ed9a341e1b0f7247175e62aceafc6051f83e8f9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300159"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Postupy: Přidání nebo odebrání odkazů pomocí správce odkazů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dialogové okno **Správce odkazů** můžete použít k přidání a správě odkazů na komponenty, které jste vy, společnost Microsoft nebo jinou společnost vyvinuli. Pokud vyvíjíte univerzální aplikaci pro Windows, váš projekt automaticky odkazuje na všechny správné knihovny dll Windows SDK. Pokud vyvíjíte aplikaci .NET, projekt automaticky odkazuje na mscorlib. dll. Některá rozhraní API rozhraní .NET jsou vystavena v součástech, které je nutné přidat ručně. Odkazy na komponenty modelu COM nebo vlastní komponenty je nutné přidat ručně.

## <a name="adding-and-removing-a-reference"></a>Přidání a odebrání odkazu

#### <a name="to-add-a-reference"></a>Přidání odkazu

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel odkazy a vyberte možnost **Přidat odkaz**.

2. Určete odkazy, které chcete přidat, a poté klikněte na tlačítko **OK** .

   Otevře se **Správce odkazů** a zobrazí seznam dostupných odkazů podle skupin. Typ projektu určuje, které z těchto skupin se zobrazí:

- Skupina Sestavení s podskupinami Rozhraní a Rozšíření

- Skupina Řešení s podskupinou Projekty

- Skupina Windows s podskupinami Jádro a Rozšíření. Můžete prozkoumat odkazy v sadách SDK Windows SDK nebo rozšíření pomocí **Prohlížeč objektů**.

- Skupina Procházení s podskupinou Nedávné

## <a name="assemblies-tab"></a>Karta Sestavení
 Na kartě **sestavení** jsou uvedena všechna .NET Framework sestavení, která jsou k dispozici pro odkazování. Na kartě **sestavení** se nezobrazí žádná sestavení z globální mezipaměti sestavení (GAC), protože sestavení v mezipaměti GAC jsou součástí prostředí modulu runtime. Pokud nasadíte nebo zkopírujete aplikaci, která obsahuje odkaz na sestavení registrované v GAC, nebude toto sestavení nasazeno nebo zkopírováno spolu s aplikací, a to bez ohledu na nastavení Kopírovat místní. Další informace najdete v tématu [odkazy na projekt](https://go.microsoft.com/fwlink/?LinkId=238512).

 Pokud ručně přidáte odkaz na jakýkoli obor názvů EnvDTE (EnvDTE, EnvDTE80, EnvDTE90, EnvDTE90a nebo EnvDTE100), nastavte vlastnost Vložit typy spolupráce pro daný odkaz v okně Vlastnosti na hodnotu Nepravda. Nastavení této vlastnosti na hodnotu Pravda může způsobit problémy sestavení z důvodu určitých vlastností EnvDTE, které není možné vložit.

 Všechny projekty určené pro klasickou plochu obsahují implicitní odkaz na knihovnu mscorlib. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekty obsahují implicitní odkaz na Microsoft. VisualBasic. V [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]všechny projekty obsahují implicitní odkaz na System. Core, i když je odebrán ze seznamu odkazů.

 Pokud typ projektu nepodporuje sestavení, karta se v dialogovém okně **Správce odkazů** nezobrazí.

 Karta Sestavení se skládá ze dvou dílčích karet:

1. Karta Rozhraní obsahuje všechna sestavení, která tvoří cílené rozhraní.

   - Inzerovaná sestavení se nacházejí v plné verzi rozhraní a jejich výčet je uveden v seznamu rozhraní, jestliže váš projekt cílí na profil cíleného rozhraní. Inzerovaná sestavení jsou zobrazena šedou barvou z důvodu odlišení od sestavení, která existují v cíleném profilu Rozhraní daného projektu. Pokud například projekt cílí na rozhraní .NET Framework 4 Client, seznam rozhraní obsahuje inzerovaná sestavení z rozhraní .NET Framework 4. Když uživatel přidá inzerované sestavení, bude uživatel upozorněn, že po zavření dialogového okna **Správce odkazů** se projekt změní na .NET Framework 4 a přidá se inzerované sestavení.

   - Projekty pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace obsahují odkazy na všechna sestavení v cílovém [!INCLUDE[net_win8_profile](../includes/net-win8-profile-md.md)] ve výchozím nastavení při vytváření projektu. V spravovaných projektech uzel jen pro čtení ve složce odkazy v **Průzkumník řešení** označuje odkaz na celé rozhraní. Proto tedy karta Rozhraní nezobrazí žádná sestavení z rozhraní a namísto toto se zobrazí následující zpráva: „Na všechna sestavení rozhraní je již odkazováno. K prozkoumání odkazů v rozhraní prosím použijte Prohlížeč objektů. " V případě projektů pro stolní počítače karta rozhraní vytváří výčet sestavení z cílového rozhraní a uživatel musí přidat odkazy, které aplikace vyžaduje.

2. Karta Rozšíření obsahuje seznam všech sestavení, která vyvinuli externí dodavatelé součástí a ovládacích prvků za účelem rozšíření cíleného rozhraní. Podle účelu dané aplikace mohou být tato sestavení potřebná.

   - Karta Rozšíření zobrazuje výčet sestavení, která jsou zaregistrována v následujících umístěních:

       ```
       32-bit machine:
       HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       64-bit machine:
       HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       And older versions of the [Target Framework Identifier]
       ```

        Například pokud projekt cílí na .NET Framework 4 v 32m počítači, rozšíření budou vytvářet výčet sestavení, která jsou registrována v rámci \Microsoft\\. NETFramework\v4.0\AssemblyFoldersEx\\, \Microsoft\\. NETFramework\v3.5\AssemblyFoldersEx\\, \Microsoft\\. NETFramework\v3.0\AssemblyFoldersEx\\a \Microsoft\\. NETFramework\v2.0\AssemblyFoldersEx\\.

   Některé součásti v seznamu nemusí být zobrazeny v závislosti na [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verzi projektu. K tomu může dojít při splnění následujících podmínek:

- Komponenta, která používá nejnovější verzi .NET Framework, není kompatibilní s projektem, který cílí na starší verzi .NET Framework.

     Informace o tom, jak změnit cílovou verzi .NET Framework pro projekt, naleznete v tématu [How to: Target a verze .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

- Komponenta, která používá [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)], je nekompatibilní s projektem, který cílí na [!INCLUDE[net_v45](../includes/net-v45-md.md)].

     Při vytváření nové aplikace se některé projekty cílí na [!INCLUDE[net_v45](../includes/net-v45-md.md)] ve výchozím nastavení. Další informace najdete v tématu [.NET Framework profil klienta](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).

- Měli byste se vyhnout přidávání odkazů na soubory do výstupů jiného projektu ve stejném řešení, protože to může způsobit chyby kompilace. Místo toho použijte kartu **projekty** v dialogovém okně **Přidat odkaz** k vytvoření odkazů typu projekt-projekt. To usnadňuje vývoj v týmu povolením lepší správy knihoven tříd, které vytvoříte ve svých projektech. Další informace najdete v tématu [řešení potíží s poškozenými odkazy](../ide/troubleshooting-broken-references.md).

- > [!NOTE]
    > V aplikaci Visual Studio 2015 se odkaz na soubor místo odkazu na projekt vytvoří, pokud je cílová verze .NET Framework jednoho projektu verze 4,5 a cílová verze druhého projektu je verze 2, 3, 3,5 nebo 4,0.

#### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Zobrazení sestavení v dialogovém okně Přidat odkaz

- Přesuňte nebo zkopírujte sestavení do jednoho z následujících umístění:

  - Aktuální adresář projektu. (Tato sestavení můžete najít pomocí karty **Procházet** .)

  - Další adresáře projektu ve stejném řešení. (Tato sestavení můžete najít pomocí karty **projekty** .)

    \- nebo –

- Nastavte klíč registru, který určuje umístění sestavení, která se mají zobrazit:

   Pro 32 operační systém přidejte jeden z následujících klíčů registru.

  - [HKEY_CURRENT_USER\SOFTWARE\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"

  - [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"

    Pro 64 operační systém přidejte jeden z následujících klíčů registru do 32 podregistru.

  - [HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"

  - [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"

    *VersionMinimum* je nejnižší .NET Framework verze, která se vztahuje. Pokud je *VersionMinimum* v 3.0, složky zadané v AssemblyFoldersEx platí pro projekty, které cílí na .NET Framework 3,0 a novější.

    *AssemblyLocation* je adresář sestavení, která se mají zobrazit v dialogovém okně **Přidat odkaz** , například C:\MyAssemblies\\.

    Vytvoření klíče registru pod uzlem HKEY_LOCAL_MACHINE umožňuje všem uživatelům zobrazit sestavení v zadaném umístění v dialogovém okně **Přidat odkaz** . Vytvoření klíče registru pod uzlem HKEY_CURRENT_USER má vliv pouze na nastavení pro aktuálního uživatele.

    Znovu otevřete dialogové okno **Přidat odkaz** . Sestavení by se měla zobrazit na kartě **.NET** . Pokud ne, ujistěte se, že se sestavení nacházejí v zadaném adresáři *AssemblyLocation* , restartujte Visual Studio a zkuste to znovu.

## <a name="com-tab"></a>Karta COM
 Karta COM obsahuje seznam všech komponent COM, které jsou k dispozici pro odkazování. Pokud chcete přidat odkaz na registrovanou knihovnu DLL modelu COM, která obsahuje vnitřní manifest, nejprve zrušte registraci dané knihovny DLL. V opačném případě sada Visual Studio přidá odkaz na sestavení jako ovládací prvek ActiveX namísto jako nativní knihovnu DLL.

 Pokud typ projektu nepodporuje model COM, karta se v dialogovém okně **Správce odkazů** nezobrazí.

## <a name="solution-tab"></a>Karta Řešení
 Na kartě Řešení jsou uvedeny všechny kompatibilní projekty v aktuálním řešení, a to na dílčí kartě Projekty.

 Projekt může odkazovat na jiný projekt, který cílí na jinou verzi rozhraní .NET Framework. Můžete například vytvořit projekt, který cílí na [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)], ale který odkazuje na sestavení sestavené pro .NET Framework 2. Projekt .NET Framework 2 však nemůže odkazovat na projekt [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)]. Další informace najdete v tématu [cílení na konkrétní verzi .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).

 Projekt, který cílí na [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)], je nekompatibilní s projektem, který cílí na [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)].

 V [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]je odkaz na soubor místo odkazu na projekt vytvořen, pokud je jeden projekt cílen na .NET Framework 4 a jiný projekt cílí na starší verzi.

 Projekt, který cílí na [!INCLUDE[net_win8_profile](../includes/net-win8-profile-md.md)], nemůže přidat odkaz na projekt, který cílí na .NET Framework a naopak.

## <a name="windows-tab"></a>Karta Windows
 Karta Windows obsahuje všechny sady SDK, které jsou specifické pro platformy, na kterých běží operační systém Windows.

 Soubor WinMD je možné v sadě Visual Studio vygenerovat dvěma způsoby:

- **[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] spravovaných projektů aplikace**: projekty [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikací můžou výstupy souborů winmd nastavovat &#124; pomocí vlastností výstupního typu projektu. Název souboru WinMD musí představovat nadřazený obor názvů všech oborů názvů, které existují jeho v rámci. Pokud například projekt obsahuje obory názvů A.B a A.B.C, možné názvy pro soubory WinMD na jeho výstupu jsou A.winmd a A.B.winmd. Pokud uživatel zadá vlastnost &#124; projektu název sestavení nebo název oboru názvů vlastností &#124; projektu, který je nesouvislý ze sady oborů názvů v projektu, nebo v rámci projektu není žádný nadřazený obor názvů, je vygenerováno upozornění sestavení: "a. winmd" není platným názvem souboru. winmd pro toto sestavení. Všechny typy v rámci souboru metadat systému Windows musejí existovat v podřízeném oboru názvů daného názvu souboru. Typy, které neexistují v podřízeném oboru daného názvu souboru, nebude možné za běhu nalézt. V tomto sestavení je nejmenší společný obor názvů CSWSClassLibrary1“. Desktopové Visual Basic nebo Visual C# projekt mohou využívat pouze soubory WinMD, které jsou generovány pomocí sady [!INCLUDE[win8](../includes/win8-md.md)] SDK, které jsou označovány jako soubory WinMD pro první stranu, a nemohou generovat soubory WinMD.

- **nativní projekty[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace**: nativní soubor winmd se skládá jenom z metadat. Jeho implementace se nachází v samostatném souboru knihovny DLL. Jeden může vytvořit nativní binární soubory výběrem šablony projektu prostředí Windows Runtime komponenty v dialogovém okně **Nový projekt** nebo spuštěním z prázdného projektu a úpravou vlastností projektu pro vygenerování souboru winmd. Pokud projekt obsahuje nesouvislé obory názvů, chyba sestavení oznámí uživateli, aby sloučit své obory názvů nebo spustit nástroj MSMerge.

  Karta Windows se skládá ze dvou podskupin.

### <a name="core-subgroup"></a>Podskupina Jádro
 Podskupina Jádro obsahuje seznam všech souborů WinMD (pro elementy prostředí Windows Runtime) v sadě SDK pro cílenou verzi systému Windows.

 projekty [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikací obsahují odkazy na všechny soubory WinMD ve výchozím nastavení [!INCLUDE[win8](../includes/win8-md.md)] SDK při vytváření projektu. V spravovaných projektech uzel jen pro čtení ve složce odkazy v **Průzkumník řešení** označuje odkaz na celou sadu [!INCLUDE[win8](../includes/win8-md.md)] SDK. Proto podskupina Core ve Správci odkazů neprovede výčet žádného sestavení ze sady SDK [!INCLUDE[win8](../includes/win8-md.md)] a místo toho zobrazí zprávu: "Windows SDK je již odkazováno. Pomocí Prohlížeče objektů můžete prozkoumat odkazy v sadě Windows SDK.“

 V projektech aplikací pro klasickou plochu se ve výchozím nastavení podskupina Jádro nezobrazuje. Prostředí Windows Runtime můžete přidat tak, že otevřete místní nabídku pro uzel projektu, zvolíte **Uvolnit projekt**, přidáte následující fragment kódu a znovu otevřete projekt (na uzlu projektu zvolíte možnost **znovu načíst projekt**). Když vyvoláte dialogové okno **Správce odkazů** , zobrazí se podskupina Core.

```
<PropertyGroup>
  <TargetPlatformVersion>8.0</TargetPlatformVersion>
</PropertyGroup>
```

 Nezapomeňte zaškrtnout políčko **Windows** v této podskupině. Poté budete moci používat elementy prostředí Windows Runtime. Je také vhodné přidat System.Runtime, ve kterém Windows Runtime definuje některé standardní třídy a rozhraní, například rozhraní IEnumerable, které se používají v knihovnách prostředí Windows Runtime. Informace o tom, jak přidat System. Runtime, najdete v tématu [spravovaná aplikace klasické pracovní plochy a prostředí Windows Runtime](https://msdn.microsoft.com/library/windows/apps/jj856306.aspx#consuming_standard_windows_runtime_types).

### <a name="extensions-subgroup"></a>Podskupina Rozšíření
 Podskupina Rozšíření obsahuje seznam uživatelských sad SDK, které rozšiřují cílenou platformu Windows. Tato karta se zobrazí jenom pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projekty aplikace. Projekty aplikací pro klasickou plochu tuto kartu nezobrazují, protože používají pouze soubory .winmd první strany.

 Sada SDK je kolekce souborů, které sada Visual Studio považuje za jedinou součást. Na kartě rozšíření jsou sady SDK, které se vztahují k projektu, ze kterého byl vyvolán dialog **Správce odkazů** , uvedeny jako samostatné položky. Po přidání do projektu je veškerý obsah sady SDK využíván sadou Visual Studio tak, že uživatel nemusí provádět žádné další akce za účelem využití obsahu sady SDK v prostředí IntelliSense, sadě nástrojů, návrhářích, Prohlížeči objektů, sestavení, nasazení, ladění a balení. Informace o tom, jak zobrazit sadu SDK na kartě rozšíření, najdete v tématu Vytvoření sady SDK ( [Software Development Kit](../extensibility/creating-a-software-development-kit.md)).

> [!NOTE]
> Pokud se projekt odkazuje na sadu SDK, která závisí na jiné sadě SDK, sada Visual Studio nebude využívat druhou sadu SDK, pokud uživatel ručně nepřidá odkaz na tuto druhou sadu SDK. Když uživatel zvolí sadu SDK na kartě **rozšíření** , dialogové okno **Správce odkazů** pomůže uživateli identifikovat závislosti sady SDK, a to tak, že uvede nejen název a verzi sady SDK, ale také název libovolné závislosti sady SDK v podokně podrobností. Pokud si uživatel nevšimne závislostí a přidá pouze sadu SDK, nástroj MSBuild vyzve uživatele k přidání závislostí.

 Pokud typ projektu nepodporuje **rozšíření**, karta se v dialogovém okně **Správce odkazů** nezobrazí.

## <a name="browse-button"></a>Tlačítko Procházet
 K procházení součásti v systému souborů můžete použít tlačítko **Procházet** .

 Projekt se může odkazovat na součást, která cílí na jinou verzi rozhraní .NET Framework. Můžete například vytvořit aplikaci, která cílí na rozhraní .NET Framework 4 Client Profile, jež odkazuje na součást, která cílí na rozhraní .NET Framework 2. Další informace najdete v tématu [cílení na konkrétní verzi .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).

 Měli byste se vyhnout přidávání odkazů na soubory do výstupů jiného projektu ve stejném řešení, protože to může vést k chybám při kompilaci. Místo toho použijte kartu **řešení** v dialogovém okně **Správce odkazů** k vytvoření odkazů typu projekt-projekt. Tento postup usnadňuje vývoj v týmu, neboť umožňuje lepší správu knihoven tříd, které vytvoříte ve svých projektech. Další informace najdete v tématu [řešení potíží s poškozenými odkazy](../ide/troubleshooting-broken-references.md).

 Nemůžete přejít k sadě SDK a přidat ji do projektu. Je možné přejít pouze k souboru (například sestavení nebo souboru .winmd) a přidat jej do projektu.

 Při odkazování na soubor WinMD je očekávané rozložení, že soubory *filename*. winmd, *filename*. dll a *filename*. pri jsou umístěny vedle sebe. Pokud odkazujete na soubor WinMD v následujících scénářích, do výstupního adresáře projektu budou zkopírovány neúplné sady souborů a v důsledku toho dojde k chybám při sestavení a za běhu.

- **Nativní komponenta**: nativní projekt vytvoří jednu winmd pro každou nesouvislou sadu oborů názvů a jednu knihovnu DLL, která se skládá z implementace. Soubory WinMDs budou mít nesouvislé názvy. Při odkazování na tento soubor nativní součásti nástroj MSBuild nerozpozná, že tyto různě nazvané soubory WinMD tvoří jednu součást. V důsledku toho budou zkopírovány pouze identicky pojmenované *filename*. dll a *filename*. winmd a dojde k chybám za běhu. Chcete-li tento problém vyřešit, vytvořte rozšiřující sadu SDK. Další informace najdete v tématu [Vytvoření sady SDK (Software Development Kit](../extensibility/creating-a-software-development-kit.md)).

- Používání **ovládacích prvků**: ovládací prvek XAML je přinejmenším tvořen *názvem filename*. winmd, *filename*. dll, *filename*. pri, *XAML*. XAML a *ImageName*. jpg. Když je projekt sestaven, soubory prostředků, které jsou přidruženy k odkazu na soubor, nebudou zkopírovány do výstupního adresáře projektu a budou zkopírovány pouze *filename*. winmd, *filename*. dll a *filename*. pri. Chyba sestavení je protokolována pro informování uživatele, že chybí prostředky *XAML*. XAML a *ImageName*. jpg. Aby sestavení proběhlo úspěšně, bude uživatel muset ručně zkopírovat tyto soubory prostředků do výstupního adresáře projektu pro sestavení a ladění/dobu běhu. Pokud chcete tento problém obejít, buď vytvořte sadu rozšíření SDK podle kroků v části [Vytvoření sady Software Development Kit](../extensibility/creating-a-software-development-kit.md) nebo upravte soubor projektu a přidejte následující vlastnost:

    ```
    <PropertyGroup>
    <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Pokud tuto vlastnost přidáte, může být sestavení pomalejší.

## <a name="recent"></a>Nedávné
 Kartu Nedávné podporují karty Sestavení, COM, Windows a Procházet. Tato karta obsahuje seznam součástí, které byly v poslední době přidány do projektu.

## <a name="search"></a>Hledat
 Panel hledání v dialogovém okně **Správce odkazů** funguje na kartě, která je zaostření. Pokud například uživatel zadá na panelu hledání text "System", zatímco je karta **řešení** aktivní, hledání nevrátí žádné výsledky, pokud se toto řešení neskládá z názvu projektu, který obsahuje "System".

## <a name="see-also"></a>Viz také
 [NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)
