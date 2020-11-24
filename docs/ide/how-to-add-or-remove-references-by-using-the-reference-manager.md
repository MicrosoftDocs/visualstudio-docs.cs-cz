---
title: Přidání odkazů ve Správci odkazů
description: Naučte se používat dialogové okno Správce odkazů k přidávání a správě odkazů na vyvíjené komponenty.
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: how-to
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4884fdc857abd524fa62bb126e7a74af48e9ca88
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597311"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Postupy: Přidání nebo odebrání odkazů pomocí Správce odkazů

Dialogové okno Správce odkazů můžete použít k přidání a správě odkazů na komponenty, které jste vy, společnost Microsoft nebo jinou společnost vyvinuli. Pokud vyvíjíte univerzální aplikaci pro Windows, váš projekt automaticky odkazuje na všechny správné knihovny dll Windows SDK. Pokud vyvíjíte aplikaci .NET, projekt automaticky odkazuje na *mscorlib.dll*. Některá rozhraní API rozhraní .NET jsou vystavena v součástech, které je nutné přidat ručně. Odkazy na komponenty modelu COM nebo vlastní komponenty je nutné přidat ručně.

## <a name="reference-manager-dialog-box"></a>Správce odkazů – dialogové okno

Dialogové okno Správce odkazů zobrazuje na levé straně různé kategorie v závislosti na typu projektu:

- **Sestavení** s podskupinami **architektury** a **rozšíření**

- **Com** obsahuje seznam všech komponent modelu COM, které jsou k dispozici pro odkazování

- **Projekty**

- **Sdílené projekty**

- **Windows** s podskupinami **základní** a **rozšíření** . Můžete prozkoumat odkazy v sadách SDK Windows SDK nebo rozšíření pomocí **Prohlížeč objektů**.

- **Procházet**, s **Poslední** podskupinou
 
    > [!NOTE]
    > Pokud vyvíjíte projekty C++, nemusí se vám v dialogovém okně Správce odkazů zobrazovat **procházení** .

## <a name="add-a-reference"></a>Přidat odkaz

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel **odkazy** nebo **závislosti** a vyberte možnost **Přidat odkaz**. Můžete také kliknout pravým tlačítkem myši na uzel projektu a vybrat možnost **Přidat**  >  **odkaz**.

   Otevře se **Správce odkazů** a zobrazí seznam dostupných odkazů podle skupin.

2. Zadejte odkazy, které chcete přidat, a pak vyberte **OK**.

## <a name="assemblies-tab"></a>Karta Sestavení

Na kartě **sestavení** jsou uvedena všechna sestavení .NET, která jsou k dispozici pro odkazování. Na kartě **sestavení** se nezobrazí žádná sestavení z globální mezipaměti sestavení (GAC), protože sestavení v mezipaměti GAC jsou součástí prostředí modulu runtime. Pokud nasadíte nebo zkopírujete aplikaci, která obsahuje odkaz na sestavení, které je registrováno v globální mezipaměti sestavení (GAC), sestavení nebude nasazeno nebo zkopírováno s aplikací bez ohledu na nastavení **Kopírovat místní** . Další informace naleznete v tématu [Správa odkazů v projektu](../ide/managing-references-in-a-project.md).

Pokud ručně přidáte odkaz na jakýkoli obor názvů EnvDTE ( <xref:EnvDTE> , <xref:EnvDTE80> ,, <xref:EnvDTE90> <xref:EnvDTE90a> nebo <xref:EnvDTE100> ), nastavte vlastnost **Embed Interop Types** odkazu na **false** v okně **vlastnosti** . Nastavení této vlastnosti na **hodnotu true** může způsobit problémy sestavení z důvodu určitých vlastností EnvDTE, které nelze vložit.

Všechny desktopové projekty obsahují implicitní odkaz na **mscorlib**. Visual Basic projekty obsahují implicitní odkaz na <xref:Microsoft.VisualBasic> . Všechny projekty obsahují implicitní odkaz na **System. Core**, i když je odebrán ze seznamu odkazů.

Pokud typ projektu nepodporuje sestavení, karta se v dialogovém okně Správce odkazů nezobrazí.

Karta **sestavení** se skládá ze dvou dílčích karet:

1. **Rozhraní** uvádí všechna sestavení, která tvoří cílové rozhraní.

   Pro projekty, které necílí na rozhraní .NET Core nebo Univerzální platforma Windows, karta **rozhraní** vytváří výčet sestavení z cíleného rozhraní. Uživatel musí přidat všechny odkazy, které aplikace vyžaduje.

   Univerzální projekty Windows obsahují odkazy na všechna sestavení v cílovém rozhraní ve výchozím nastavení. V spravovaných projektech uzel jen pro čtení ve složce **odkazy** v **Průzkumník řešení** označuje odkaz na celé rozhraní. Proto karta **rozhraní** nevytvoří výčet žádného sestavení z rozhraní a místo toho zobrazí následující zprávu: "všechna sestavení rozhraní jsou již odkazována. K prozkoumání odkazů v rozhraní prosím použijte Prohlížeč objektů.

2. **Rozšíření** uvádí všechna sestavení, která vyvinuli externí dodavatelé komponent a ovládacích prvků pro rozšíření cíleného rozhraní. Podle účelu dané aplikace mohou být tato sestavení potřebná.

   **Rozšíření** jsou vyplněna vytvořením výčtu sestavení, která jsou registrována v následujících umístěních:

   32 – bitový počítač:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   64 – bitový počítač:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   A starší verze [identifikátor cílového rozhraní .NET Framework]

   Například pokud je projekt .NET Framework cílen na 32-bit počítače, **rozšíření** vytvoří výčet sestavení, která jsou registrována v části *\Microsoft \. NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft \. NETFramework\v3.5\AssemblyFoldersEx*, *\Microsoft \. NETFramework\v3.0\AssemblyFoldersEx* a *\Microsoft \. NETFramework\v2.0\AssemblyFoldersEx*.

Některé součásti v seznamu nemusí být zobrazeny v závislosti na verzi rozhraní projektu. K tomu může dojít při splnění následujících podmínek:

- Komponenta, která používá nejnovější verzi rozhraní, je nekompatibilní s projektem, který cílí na starší verzi.

   Informace o tom, jak změnit cílovou verzi rozhraní pro projekt, najdete v tématu [Přehled cílení na rozhraní](visual-studio-multi-targeting-overview.md).

- Komponenta, která používá .NET Framework 4, je nekompatibilní s projektem, který cílí na .NET Framework 4,5.

Měli byste se vyhnout přidávání odkazů na soubory do výstupů jiného projektu ve stejném řešení, protože to může způsobit chyby kompilace. Místo toho použijte kartu **projekty** v dialogovém okně **Přidat odkaz** k vytvoření odkazů typu projekt-projekt. To usnadňuje vývoj v týmu povolením lepší správy knihoven tříd, které vytvoříte ve svých projektech. Další informace najdete v tématu [řešení potíží s poškozenými odkazy](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> V aplikaci Visual Studio 2015 nebo novější je odkaz na soubor místo odkazu na projekt vytvořen, pokud je cílová verze rozhraní .NET Framework jednoho projektu .NET Framework 4,5 nebo novější a cílová verze druhého projektu .NET Framework 2, 3, 3,5 nebo 4,0.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Zobrazení sestavení v dialogovém okně Přidat odkaz

- Přesuňte nebo zkopírujte sestavení do jednoho z následujících umístění:

  - Aktuální adresář projektu. (Tato sestavení můžete najít pomocí karty **Procházet** .)

  - Další adresáře projektu ve stejném řešení. (Tato sestavení můžete najít pomocí karty **projekty** .)

  \- ani

- Nastavte klíč registru, který určuje umístění sestavení, která se mají zobrazit:

  Pro 32 operační systém přidejte jeden z následujících klíčů registru.

  - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  Pro 64 operační systém přidejte jeden z následujících klíčů registru do 32 podregistru.

  - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  *\<VersionMinimum\>* je nejnižší verze rozhraní, která se používá. Pokud *\<VersionMinimum\>* je v 3.0, složky zadané v *AssemblyFoldersEx* platí pro projekty, které cílí na .NET Framework 3,0 a novější.

  *\<AssemblyLocation\>* je adresář sestavení, která se mají zobrazit v dialogovém okně **Přidat odkaz** , například *C:\MyAssemblies*.

  Vytvoření klíče registru pod `HKEY_LOCAL_MACHINE` uzlem umožní všem uživatelům zobrazit sestavení v zadaném umístění v dialogovém okně **Přidat odkaz** . Vytvoření klíče registru pod `HKEY_CURRENT_USER` uzlem má vliv pouze na nastavení pro aktuálního uživatele.

  Znovu otevřete dialogové okno **Přidat odkaz** . Sestavení by se měla zobrazit na kartě **.NET** . Pokud ne, ujistěte se, že se sestavení nacházejí v zadaném adresáři *AssemblyLocation* , restartujte Visual Studio a zkuste to znovu.

## <a name="projects-tab"></a>Karta projekty

Karta **projekty** obsahuje seznam všech kompatibilních projektů v rámci aktuálního řešení na dílčí kartě **řešení** .

Projekt může odkazovat na jiný projekt, který cílí na jinou verzi rozhraní. Můžete například vytvořit projekt, který se zaměřuje na .NET Framework 4, ale odkazuje na sestavení sestavené pro .NET Framework 2. Projekt .NET Framework 2 však nemůže odkazovat na projekt .NET Framework 4. Další informace najdete v tématu [Přehled cílení na rozhraní](../ide/visual-studio-multi-targeting-overview.md).

> [!NOTE]
> Projekt, který cílí na .NET Framework 4, je nekompatibilní s projektem, který cílí na profil klienta .NET Framework 4.

## <a name="shared-projects-tab"></a>Karta sdílené projekty

Přidejte odkaz na sdílený projekt na kartě **sdílené projekty** v dialogovém okně Správce odkazů. [Sdílené projekty](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) umožňují psát společný kód, na který odkazuje několik různých aplikačních projektů.

## <a name="universal-windows-tab"></a>Karta univerzální pro Windows

Karta **Universal Windows** obsahuje všechny sady SDK, které jsou specifické pro platformy, na kterých běží operační systémy Windows.
Tato karta má dvě podskupiny: **jádro** a **rozšíření**.

### <a name="core-subgroup"></a>Podskupina Core

Projekty univerzálních aplikací pro Windows mají ve výchozím nastavení odkaz na univerzální Windows SDK. Proto podskupina **jádra** ve **Správci odkazů** nevytvoří výčet žádného ze sestavení z univerzálního Windows SDK.

### <a name="extensions-subgroup"></a>Podskupina rozšíření

**Rozšíření** uvádí uživatelské sady SDK, které rozšiřuje cílovou platformu Windows.

Sada SDK je kolekce souborů, které sada Visual Studio považuje za jedinou součást. Na kartě **rozšíření** jsou sady SDK, které se vztahují k projektu, ze kterého byl vyvolán dialog Správce odkazů, uvedeny jako samostatné položky. Po přidání do projektu je veškerý obsah sady SDK spotřebován sadou Visual Studio tak, aby uživatel nemusel provádět žádné další kroky pro využití obsahu sady SDK v technologii IntelliSense, sadě nástrojů, návrháři, Prohlížeč objektů, sestavení, nasazení, ladění a balení.

Informace o tom, jak zobrazit sadu SDK na kartě **rozšíření** , najdete v tématu Vytvoření sady SDK ( [Software Development Kit](../extensibility/creating-a-software-development-kit.md)).

> [!NOTE]
> Pokud projekt odkazuje na sadu SDK, která závisí na jiné sadě SDK, sada Visual Studio nespotřebovává druhou sadu SDK, pokud do druhé sady SDK ručně nepřidáte odkaz. Když uživatel zvolí sadu SDK na kartě **rozšíření** , dialogové okno Správce odkazů vám pomůže identifikovat závislosti sady SDK tím, že v podokně podrobností zobrazí seznam závislostí.

Pokud typ projektu nepodporuje rozšíření, tato karta se v dialogovém okně Správce odkazů nezobrazí.

## <a name="com-tab"></a>Karta COM

Karta **com** obsahuje seznam všech komponent modelu COM, které jsou k dispozici pro odkazování. Pokud chcete přidat odkaz na registrovanou knihovnu DLL modelu COM, která obsahuje vnitřní manifest, nejprve zrušte registraci dané knihovny DLL. V opačném případě Visual Studio přidá odkaz na sestavení jako ovládací prvek ActiveX namísto jako nativní knihovnu DLL.

Pokud typ projektu nepodporuje model COM, karta se v dialogovém okně Správce odkazů nezobrazí.

## <a name="browse"></a>Procházet

K procházení součásti v systému souborů můžete použít tlačítko **Procházet** .

Projekt může odkazovat na komponentu, která cílí na jinou verzi rozhraní. Můžete například vytvořit aplikaci, která cílí na .NET Framework 4,7, ale odkazuje na součást, která cílí na .NET Framework 4. Další informace najdete v tématu [Přehled cílení na rozhraní](../ide/visual-studio-multi-targeting-overview.md).

Vyhněte se přidávání odkazů na soubory do výstupů jiného projektu ve stejném řešení, protože tento cílem může způsobit chyby kompilace. Místo toho použijte kartu **řešení** v dialogovém okně Správce odkazů k vytvoření odkazů typu projekt-projekt. To usnadňuje vývoj v týmu povolením lepší správy knihoven tříd, které vytvoříte ve svých projektech. Další informace najdete v tématu [řešení potíží s poškozenými odkazy](../ide/troubleshooting-broken-references.md).

Nemůžete procházet sadu SDK a přidat ji do projektu. Můžete přejít pouze k souboru (například sestavení nebo *. winmd*) a přidat ho do projektu.

Při odkazování na soubor winmd je očekávané rozložení, že soubory *\<FileName> . winmd*, *\<FileName> . dll* a *\<FileName> . pri* jsou umístěny vedle sebe. Pokud odkazujete na soubor WinMD v následujících scénářích, do výstupního adresáře projektu budou zkopírovány neúplné sady souborů a v důsledku toho dojde k chybám při sestavení a za běhu.

- **Nativní komponenta**: nativní projekt vytvoří jednu winmd pro každou nesouvislou sadu oborů názvů a jednu knihovnu DLL, která se skládá z implementace. Soubory WinMDs budou mít nesouvislé názvy. Při odkazování na tento soubor nativní komponenty nástroj MSBuild nerozpozná, že s názvem soubory WinMD vytvořit jednu komponentu. V důsledku toho budou zkopírovány pouze identicky pojmenované *\<FileName> . dll* a *\<FileName> . winmd* a dojde k chybám za běhu. Pokud chcete tento problém obejít, vytvořte sadu SDK rozšíření. Další informace najdete v tématu [Vytvoření sady SDK (Software Development Kit](../extensibility/creating-a-software-development-kit.md)).

- **Spotřebovávání ovládacích prvků**: ovládací prvek XAML je přinejmenším tvořen *\<FileName> příponou. winmd*, *\<FileName> . dll*, *\<FileName> . pri*, *\<XamlName> . XAML* a *\<ImageName> . jpg*. Po sestavení projektu se soubory prostředků, které jsou spojeny s odkazem na soubor, nezkopírují do výstupního adresáře projektu a zkopírují se pouze soubory *\<FileName> . winmd*, *\<FileName> . dll* a *\<FileName> . pri* . Chyba sestavení je protokolována pro informování uživatele, že nebyly nalezeny prostředky *\<XamlName> . XAML* a *\<ImageName> . jpg* . Aby sestavení proběhlo úspěšně, bude uživatel muset ručně zkopírovat tyto soubory prostředků do výstupního adresáře projektu pro sestavení a ladění/dobu běhu. Pokud chcete tento problém obejít, buď vytvořte sadu rozšíření SDK podle kroků v části [Vytvoření sady Software Development Kit](../extensibility/creating-a-software-development-kit.md) nebo upravte soubor projektu a přidejte následující vlastnost:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Pokud tuto vlastnost přidáte, může být sestavení pomalejší.

## <a name="recent"></a>Nedávné

**Sestavení**, **com**, **Windows** a **procházení** jednotlivých **podporovaných karet,** které vyčíslují seznam komponent, které byly nedávno přidány do projektů.

## <a name="search"></a>Search

Panel hledání v dialogovém okně Správce odkazů funguje na kartě, která je zaostření. Pokud například uživatel zadá na panelu hledání text "System", zatímco je karta **řešení** aktivní, hledání nevrátí žádné výsledky, pokud se toto řešení neskládá z názvu projektu, který obsahuje "System".

## <a name="see-also"></a>Viz také

- [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)
