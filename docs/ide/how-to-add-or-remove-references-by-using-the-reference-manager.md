---
title: Přidání odkazů ve Správci odkazů
ms.date: 04/11/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- C# projects, references
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3668b5e4275071513deb31e2e479adcd91d11589
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839268"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Postupy: Přidání nebo odebrání odkazů pomocí Správce odkazů

Můžete použít **správce odkazů** dialogové okno Přidat a spravovat odkazy na součásti, které jste společnosti Microsoft, nebo jiné firmy vyvíjí. Pokud vyvíjíte aplikace Universal Windows, váš projekt automaticky odkazuje na všechny správné DLL knihovny Windows SDK. Pokud vyvíjíte aplikaci .NET, váš projekt se automaticky odkazuje na *mscorlib.dll*. Některá rozhraní API .NET jsou přístupné na součásti, které je nutné přidat ručně. Odkazy na součásti modelu COM nebo vlastní součásti nutné přidat ručně.

## <a name="reference-manager-dialog-box"></a>Dialogové okno Správce odkazů

**Správce odkazů** dialogové okno zobrazí na levé straně, v závislosti na typu projektu různých kategorií:

- **Sestavení**, se **Framework** a **rozšíření** podskupiny.

- **COM**, jsou uvedeny všechny komponenty modelu COM, které jsou k dispozici pro odkazování.

- **Řešení**, se **projekty** podskupiny.

- **Windows**, se **Core** a **rozšíření** podskupiny. Odkazy v sadě Windows SDK nebo rozšiřujících sadách SDK můžete prozkoumat pomocí **prohlížeče objektů**.

- **Procházet**, se **poslední** podskupiny.

## <a name="add-and-remove-a-reference"></a>Přidání a odebrání odkazu

### <a name="to-add-a-reference"></a>Přidání odkazu

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** nebo **závislosti** uzlu a zvolte **přidat odkaz**. Můžete také kliknout pravým tlačítkem na uzel projektu a vyberte **přidat** > **odkaz**.

   **Správce odkazů** otevře a zobrazí seznam dostupných odkazů seřazených ve skupinách.

2. Zadejte odkazy, které chcete přidat a pak vyberte **OK**.

## <a name="assemblies-tab"></a>Karta Sestavení

**Sestavení** karta obsahuje seznam všech sestavení rozhraní .NET Framework, které jsou k dispozici pro odkazování. **Sestavení** kartu neobsahuje žádná sestavení z globální mezipaměti sestavení (GAC), protože sestavení v GAC jsou součástí běhového prostředí. Pokud nasadíte nebo zkopírujete aplikaci, která obsahuje odkaz na sestavení, které je registrované v GAC, sestavení nebude nasazena nebo zkopírována s aplikací, bez ohledu na to **Kopírovat místně** nastavení. Další informace najdete v tématu [Správa odkazů v projektu](../ide/managing-references-in-a-project.md).

Pokud ručně přidáte odkaz na jakýkoli obor názvů EnvDTE (<xref:EnvDTE>, <xref:EnvDTE80>, <xref:EnvDTE90>, <xref:EnvDTE90a>, nebo <xref:EnvDTE100>), můžete nastavit **Embed Interop Types** vlastnosti odkazu na **False** v **vlastnosti** okna. Nastavení této vlastnosti na **True** může způsobit problémy sestavení z důvodu určitých vlastností EnvDTE, které nemůže být vložený.

Všechny desktopové projekty obsahují implicitní odkaz na **mscorlib**. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projekty obsahují implicitní odkaz na <xref:Microsoft.VisualBasic>. Všechny projekty obsahují implicitní odkaz na **System.Core**, i když je odebrán ze seznamu odkazů.

Pokud typ projektu nepodporuje sestavení, na kartě nezobrazí v **správce odkazů** dialogové okno.

**Sestavení** karta se skládá ze dvou dílčích karet:

1. **Rozhraní Framework** obsahuje seznam všech sestavení, které tvoří cílené rozhraní.

    Projekty pro Windows 8.x Store aplikace obsahují odkazy na všechna sestavení v cíleném [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] ve výchozím nastavení při vytvoření projektu. Ve spravovaných projektech, uzel jen pro čtení v rámci **odkazy** složky **Průzkumníka řešení** označuje odkaz na celé rozhraní. Odpovídajícím způsobem **Framework** kartu nebude žádná sestavení z rozhraní a místo toho zobrazí následující zpráva: "všechna sestavení rozhraní je již odkazováno. Použijte prohlížeč objektů pro prozkoumání odkazů rozhraní Framework." Pro desktopové projekty **Framework** karta zobrazuje sestavení z cíleného rozhraní a uživatel musí přidat odkazy, které aplikace vyžaduje.

2. **Rozšíření** obsahuje seznam všech sestavení, která vyvinuli externí dodavatelé součástí a ovládacích prvků pro rozšíření cíleného rozhraní. Podle účelu dané aplikace mohou být tato sestavení potřebná.

   **Rozšíření** zobrazuje výčet sestavení, která jsou zaregistrována v následujících umístěních:

   32bitový počítač:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   64bitový počítač:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   A starší verze identifikátoru [Target Framework]

   Například, pokud projekt cílí na rozhraní .NET Framework 4 na 32bitovém počítači **rozšíření** vytvoří výčet sestavení, která jsou registrována pod *\Microsoft\.NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.5\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.0\AssemblyFoldersEx*, a  *\Microsoft\.NETFramework\v2.0\AssemblyFoldersEx*.

Některé součásti v seznamu se nemusí zobrazit, v závislosti na verzi rozhraní .NET Framework projektu. Tato situace může nastat za následujících podmínek:

- Komponenta, která používá nejnovější verzi rozhraní .NET Framework je nekompatibilní s projektem, který se zaměřuje na starší verzi rozhraní .NET Framework.

    Informace o tom, jak změnit cílovou verzi rozhraní .NET Framework pro projekt, naleznete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

- Komponenty, která používá [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] je nekompatibilní s projektem, který se zaměřuje [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)].

    Když vytvoříte novou aplikaci, některé projekty zaměřují [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] ve výchozím nastavení.

Můžete byste se vyhnout přidávání odkazů na soubory do výstupů jiného projektu ve stejném řešení, protože to může způsobit chyby kompilace. Místo toho použijte **projekty** karty **přidat odkaz** dialogové okno k vytvoření odkazů typu projekt projekt. Toto usnadňuje vývoj v týmu povolením lepší správy knihoven tříd, které vytvoříte ve svých projektech. Další informace najdete v tématu [nefunkční odkazy na řešení potíží](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> V sadě Visual Studio 2015 nebo vyšší odkaz na soubor místo odkazu na projekt je vytvořen, pokud cílová verze rozhraní .NET Framework jednoho projektu je verze 4.5 nebo novější a cílová verze jiného projektu je verze 2, 3, 3.5 nebo 4.0.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Zobrazení sestavení v dialogovém okně Přidat odkaz

- Přesuňte nebo zkopírujte sestavení do jednoho z následujících umístění:

   - Aktuální adresář projektu. (Můžete vyhledat tato sestavení pomocí **Procházet** tab.)

   - Další adresáře projektu ve stejném řešení. (Můžete vyhledat tato sestavení pomocí **projekty** tab.)

    \- nebo –

- Nastavte klíč registru určující umístění sestavení, které chcete zobrazit:

   Pro 32bitový operační systém přidejte jeden z následujících klíčů registru.

   - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   Pro 64bitový operační systém přidejte jeden z následujících klíčů registru v 32 bitů podregistru.

   - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   *\<VersionMinimum\>*  je nejnižší verze rozhraní .NET Framework, která se použije. Pokud *\<VersionMinimum\>* je v3.0, složky zadané v *AssemblyFoldersEx* vztahují na projekty, které cílí na .NET Framework 3.0 nebo novější.

   *\<AssemblyLocation\>*  je adresář sestavení, která se má zobrazit v **přidat odkaz** dialogové okno, například *C:\MyAssemblies*.

   Vytvoření klíče registru pod `HKEY_LOCAL_MACHINE` uzel umožňuje všem uživatelům zobrazit sestavení v zadaném umístění v **přidat odkaz** dialogové okno. Vytvoření klíče registru pod `HKEY_CURRENT_USER` uzlu ovlivní pouze nastavení pro aktuálního uživatele.

   Otevřít **přidat odkaz** dialog již příště nezobrazovat. Sestavení by se měla objevit na **.NET** kartu. Pokud tomu tak není, ujistěte se, že sestavení jsou umístěny v zadaném *AssemblyLocation* adresáře, restartujte Visual Studio a zkuste to znovu.

## <a name="projects-tab"></a>Kartu projekty

**Projekty** karta obsahuje všechny kompatibilní projekty v aktuálním řešení, v **řešení** dílčí kartu.

Projekt může odkazovat na jiný projekt, který cílí na jinou verzi rozhraní .NET Framework. Například můžete vytvořit projekt, který cílí [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] , ale který odkazuje na sestavení vytvořené pro rozhraní .NET Framework 2. Však nemůže odkazovat na rozhraní .NET Framework 2 projekt [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] projektu. Další informace najdete v tématu [přehled multiplatformního zacílení](../ide/visual-studio-multi-targeting-overview.md).

Projekt, který se zaměřuje [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] je nekompatibilní s projektem, který se zaměřuje [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].

Odkaz na soubor místo odkazu na projekt je vytvořen, pokud jeden projekt cílí na .NET Framework 4 a jiný projekt cílí na starší verzi.

Projekt, který cílí na [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] nelze přidat odkaz na projekt do projektu, který cílí na .NET Framework a naopak.

## <a name="windows-tab"></a>Karta Windows

**Windows** karta obsahuje seznam všech sad SDK, které jsou specifické pro platformy, na které operační systémy Windows spouštět.

Soubor WinMD je možné v sadě Visual Studio vygenerovat dvěma způsoby:

- **Spravované projekty aplikací Windows 8.x Store**: projekty aplikací pro Windows 8.x Store můžete výstup binární soubory WinMD nastavením **vlastnosti projektu** > **typ výstupu na soubor WinMD**. Název souboru WinMD musí představovat nadřazený obor názvů všech oborů názvů, které existují jeho v rámci. Například, pokud projekt obsahuje obory názvů `A.B` a `A.B.C`, jsou možné názvy pro soubory WinMD na jeho *A.winmd* a *A.B.winmd*. Pokud uživatel zadá **vlastnosti projektu** > **název sestavení** nebo **vlastnosti projektu** > **Namespace**hodnotu, která je mimo sadu oborů názvů v projektu nebo není žádný nadřazený obor názvů v rámci projektu, vygeneruje se upozornění sestavení: "" A.winmd není platný název souboru .winmd pro toto sestavení." Všechny typy v rámci souboru metadat systému Windows musejí existovat v podřízeném oboru názvů daného názvu souboru. Typy, které neexistují v podřízeném oboru daného názvu souboru nebude moct za běhu nalézt. V tomto sestavení je nejmenší společný obor názvů `CSWSClassLibrary1`. Stolní počítač Visual Basic nebo C# projekt může využívat pouze soubory Winmd vygenerované pomocí sad SDK Windows 8, které jsou označovány jako soubory Winmd první strany, a nemůže generovat soubory Winmd.

- **Nativní projekty aplikací pro Windows 8.x Store**: nativní soubor WinMD obsahuje pouze metadata. Jeho implementace se nachází v samostatném souboru knihovny DLL. Výběrem šablonu projektu součásti prostředí Windows Runtime v je možné vytvořit nativní binární soubory **nový projekt** dialogové okno nebo spuštěním prázdným projektem a upravíte vlastnosti projektu pro vytvoření souboru WinMD. Pokud projekt obsahuje nesouvislé obory názvů, chyba sestavení oznámí uživateli, aby sloučit své obory názvů nebo spustit nástroj MSMerge.

**Windows** karta se skládá ze dvou podskupin.

### <a name="core-subgroup"></a>Podskupina jádro

**Core** podskupina obsahuje seznam všech souborů Winmd (pro elementy prostředí Windows Runtime) v sadě SDK pro cílenou verzi systému Windows.

Projekty aplikací pro Windows 8.x Store obsahují odkazy na všechny soubory winmd v systému Windows 8 SDK ve výchozím nastavení při vytvoření projektu. Ve spravovaných projektech, uzel jen pro čtení v rámci **odkazy** složky **Průzkumníka řešení** označuje odkaz na celou sadu SDK Windows 8. Toho **Core** podskupiny v **správce odkazů** nezobrazí seznam všech sestavení ze sady SDK Windows 8 a místo toho zobrazí zpráva: "Windows SDK se už odkazuje. Použijte prohlížeč objektů pro prozkoumání odkazů v sadě Windows SDK."

V desktopové projekty **Core** podskupiny nezobrazuje ve výchozím nastavení. Modul Windows Runtime můžete přidat tak, že otevřete místní nabídku uzlu projektu zvolíte **uvolnit projekt**, přidáte následující fragment kódu a znovu otevřete projekt (na uzel projektu, zvolte **znovu načíst projekt**). Při vyvolání **správce odkazů** dialogové okno, **Core** se zobrazí podskupina.

```xml
<PropertyGroup>
  <TargetPlatformVersion>8.0</TargetPlatformVersion>
</PropertyGroup>
```

Je nutné vybrat **Windows** v této podskupině zaškrtávací políčko. Poté budete moci používat elementy prostředí Windows Runtime. Však budete také chtít přidat <xref:System.Runtime>, ve které modulu Windows Runtime definuje některé standardní třídy a rozhraní, jako například <xref:System.Collections.IEnumerable>, která se používají v knihovnách prostředí Windows Runtime. Informace o tom, jak přidat <xref:System.Runtime>, naleznete v tématu [spravované aplikace klasické pracovní plochy a prostředí Windows Runtime](/previous-versions/windows/apps/jj856306(v=win.10)#consuming-standard-windows-runtime-types).

### <a name="extensions-subgroup"></a>Podskupina rozšíření

**Rozšíření** obsahuje seznam uživatelských sad SDK, které rozšiřují cílovou platformu Windows. Na této kartě se zobrazí Windows 8.x Store aplikace pouze pro projekty. Desktopové projekty tuto kartu nezobrazují, protože používají pouze první strany *.winmd* soubory.

Sada SDK je kolekce souborů, které sada Visual Studio považuje za jedinou součást. V **rozšíření** kartu, sady SDK, které platí pro projekt, ze kterých **správce odkazů** bylo vyvoláno dialogové jsou uvedeny jako jedna položka. Když se přidá do projektu, veškerý obsah sady SDK je využívána sady Visual Studio tak, aby uživatel nemusí provádět žádné další akce za účelem využití obsahu sady SDK v technologii IntelliSense, sadě nástrojů, návrhářích, prohlížeči objektů, sestavení, nasazení, ladění a balení. Informace o tom, jak zobrazit vaši sadu SDK v **rozšíření** kartu, najdete v článku [vytváření Software Development Kit](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> Pokud se projekt odkazuje na sadu SDK, která závisí na jiné sady SDK, Visual Studio nebude využívat druhou sadu SDK, pokud uživatel ručně nepřidá odkaz na tuto druhou sadu SDK. Když uživatel vybere sadu SDK na **rozšíření** karta, **správce odkazů** dialogové okno pomáhá uživateli určit závislosti sady SDK uvedením nejen název a verzi sady SDK, ale také název všechny sady SDK závislosti v podokně podrobností. Pokud uživatel nevšimne závislostí a přidá pouze sadu SDK, nástroj MSBuild vyzve uživatele k přidání závislostí.

Pokud typ projektu nepodporuje rozšíření, na kartě nezobrazí v **správce odkazů** dialogové okno.

## <a name="com-tab"></a>Karta COM

**COM** karta obsahuje všechny komponenty modelu COM, které jsou k dispozici pro odkazování. Pokud chcete přidat odkaz na registrovanou knihovnu DLL modelu COM, která obsahuje vnitřní manifest, nejprve zrušte registraci dané knihovny DLL. V opačném případě sady Visual Studio přidá odkaz na sestavení jako ovládací prvek ActiveX namísto jako nativní knihovnu DLL.

Pokud typ projektu nepodporuje model COM, nebude tato karta se v **správce odkazů** dialogové okno.

## <a name="browse-button"></a>Tlačítko Procházet

Můžete použít **Procházet** tlačítko vyhledat součást v systému souborů.

Projekt se může odkazovat na součást, která cílí na jinou verzi rozhraní .NET Framework. Například můžete vytvořit aplikaci, který cílí .NET Framework 4.7, který odkazuje na součást, která cílí na rozhraní .NET Framework 4. Další informace najdete v tématu [přehled multiplatformního zacílení](../ide/visual-studio-multi-targeting-overview.md).

Měli byste se vyhnout přidávání odkazů na soubory do výstupů jiného projektu ve stejném řešení, protože to může vést k chybám při kompilaci. Místo toho použijte **řešení** karty **správce odkazů** dialogové okno k vytvoření odkazů typu projekt projekt. Toto usnadňuje vývoj v týmu povolením lepší správy knihoven tříd, které vytvoříte ve svých projektech. Další informace najdete v tématu [nefunkční odkazy na řešení potíží](../ide/troubleshooting-broken-references.md).

Nelze procházet k sadě SDK a přidat do projektu. Je možné přejít pouze k souboru (například sestavení nebo *.winmd*) a přidejte ho do projektu.

Při provádění odkaz na soubor na o soubor WinMD je očekávané rozložení je, že  *<FileName>.winmd*,  *<FileName>.dll*, a  *<FileName>.pri* jsou soubory všechny umístěny spolu. Pokud odkazujete na soubor WinMD v následujících scénářích, do výstupního adresáře projektu budou zkopírovány neúplné sady souborů a v důsledku toho dojde k chybám při sestavení a za běhu.

- **Nativní součást**: nativní projekt vytvoří jeden soubor WinMD pro každou sadu nesouvislých oborů názvů a jednu knihovnu DLL, který se skládá z implementace. Soubory WinMDs budou mít nesouvislé názvy. Při odkazování na tento soubor nativní součásti, nástroj MSBuild nerozpozná, že tyto různě nazvané soubory Winmd tvoří jednu součást. V důsledku toho pouze identicky pojmenované  *<FileName>.dll* a  *<FileName>.winmd* budou zkopírovány, a dojde k chybám za běhu. Chcete-li tento problém obejít, vytvořte sady extension SDK. Další informace najdete v tématu [Create a Software Development Kit](../extensibility/creating-a-software-development-kit.md).

- **Využívající ovládací prvky**:, ovládací prvek XAML přinejmenším z  *<FileName>.winmd*,  *<FileName>.dll*,  *<FileName>.pri*,  *<XamlName>.xaml*a  *<ImageName>.jpg*. Při sestavení projektu nebudou soubory prostředků, které jsou spojeny s odkaz na soubor získat zkopírovány do výstupního adresáře projektu a to jenom  *<FileName>.winmd*,  *<FileName>.dll*a  *<FileName>.pri* budou zkopírovány. Bude zaznamenána chyba sestavení informovat uživatele, který prostředky  *<XamlName>.xaml* a  *<ImageName>.jpg* chybí. Aby sestavení proběhlo úspěšně, bude uživatel muset ručně zkopírovat tyto soubory prostředků do výstupního adresáře projektu pro sestavení a ladění/dobu běhu. Tento problém obejít, buď vytvořte rozšiřující sadu SDK pomocí následujících kroků v [Create a Software Development Kit](../extensibility/creating-a-software-development-kit.md) nebo upravit soubor projektu a přidejte následující vlastnost:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Pokud tuto vlastnost přidáte, může být sestavení pomalejší.

## <a name="recent"></a>Nedávné

**Sestavení**, **COM**, **Windows**, a **Procházet** každý podpory **poslední** kartu, která obsahuje seznam součásti, které byly nedávno přidaných do projektů.

## <a name="search"></a>Hledat

Na panelu hledání v **správce odkazů** dialogové okno funguje na kartě, která je aktivní. Například, pokud uživatel zadá panelu hledání text "Systém" **řešení** má fokus karta, vyhledávání nevrátí žádné výsledky, pokud řešení obsahuje název projektu, který obsahuje "slovo systém".

## <a name="see-also"></a>Viz také:

- [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)