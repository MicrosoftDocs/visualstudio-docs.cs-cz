---
title: Přidání odkazů ve Správci odkazů
description: Naučte se používat dialogové okno Správce odkazů k přidávání a správě odkazů na vyvinuté komponenty.
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 552ec8364bb58b72199bacecca99283303eb174c
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924913"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Postupy: Přidání nebo odebrání odkazů pomocí Správce odkazů

Pomocí dialogového okna Správce odkazů můžete přidávat a spravovat odkazy na komponenty, které jste vyvinuli vy, Microsoft nebo jiná společnost. Pokud vyvíjíte univerzální aplikaci pro Windows, váš projekt automaticky odkazuje na všechny správné Windows SDK DLL. Pokud vyvíjíte aplikaci .NET, projekt automaticky odkazuje na *mscorlib.dll*. Některá rozhraní API .NET jsou zveřejněná v komponentách, které musíte přidat ručně. Odkazy na komponenty modelu COM nebo vlastní součásti je nutné přidat ručně.

## <a name="reference-manager-dialog-box"></a>Dialogové okno Správce odkazů

V dialogovém okně Správce odkazů se na levé straně zobrazují různé kategorie v závislosti na typu projektu:

- **Sestavení s** podskupinami **Framework** a **Extensions**

- **Com** uvádí všechny součásti modelu COM, které jsou k dispozici pro odkazování

- **Projekty**

- **Sdílené projekty**

- **Windows** s **podskupinami** Core a **Extensions.** Odkazy v nástroji nebo Windows SDK SDK můžete prozkoumat pomocí **prohlížeče objektů**.

- **Procházení s** **podskupinou Poslední**
 
    > [!NOTE]
    > Při vývoji projektů **jazyka** C++ se v dialogovém okně Správce odkazů nemusí zobrazit procházení.

## <a name="add-a-reference"></a>Přidání odkazu

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **uzel Odkazy** nebo **Závislosti** a zvolte **Přidat odkaz.** Můžete také kliknout pravým tlačítkem na uzel projektu a vybrat **Přidat**  >  **odkaz.**

   **Správce odkazů** otevře a zobrazí seznam dostupných odkazů podle skupin.

2. Zadejte odkazy, které chcete přidat, a pak vyberte **OK.**

## <a name="assemblies-tab"></a>Karta Sestavení

Karta **Sestavení obsahuje** seznam všech sestavení .NET, která jsou k dispozici pro odkazování. Karta Sestavení neukaždá žádná sestavení z globální mezipaměti sestavení (GAC), protože sestavení v GAC jsou součástí prostředí za běhu.  Pokud nasadíte nebo zkopírujete aplikaci, která obsahuje odkaz na sestavení zaregistrované v GAC, sestavení nebude nasazeno ani zkopírováno s aplikací bez ohledu na nastavení **Kopírovat** místní. Další informace najdete v tématu [Správa odkazů v projektu](../ide/managing-references-in-a-project.md).

Když ručně přidáte odkaz na některý z oborů názvů EnvDTE ( , , , nebo ), nastavte vlastnost Embed Interop Types odkazu v okně Vlastnosti na <xref:EnvDTE> <xref:EnvDTE80> hodnotu <xref:EnvDTE90> <xref:EnvDTE90a> <xref:EnvDTE100> False.    Nastavení této vlastnosti na **hodnotu True** může způsobit problémy se sestavením kvůli určitým vlastnostem EnvDTE, které nelze vložit.

Všechny desktopové projekty obsahují implicitní odkaz na **mscorlib**. Visual Basic projekty obsahují implicitní odkaz na <xref:Microsoft.VisualBasic> . Všechny projekty obsahují implicitní odkaz na **System.Core,** i když jsou odebrány ze seznamu odkazů.

Pokud typ projektu nepodporuje sestavení, karta se nezobrazí v dialogovém okně Správce odkazů.

Karta **Sestavení se** skládá ze dvou dílčích karet:

1. **Rozhraní** obsahuje seznam všech sestavení, která tvoří cílovou rozhraní.

   U projektů, které nejsou zaměřené na .NET Core nebo Univerzální platforma Windows rozhraní, se na kartě **Rozhraní** zobrazí výčet sestavení z cílové architektury. Uživatel musí přidat všechny odkazy, které aplikace vyžaduje.

   Univerzální projekty systému Windows obsahují ve výchozím nastavení odkazy na všechna sestavení v cílovém rozhraní. Ve spravovaných projektech uzel jen  pro čtení ve složce Odkazy v **Průzkumník řešení** označuje odkaz na celou rozhraní. Karta Framework  proto nevyčísluje žádná sestavení z rozhraní a místo toho zobrazí následující zprávu: "Všechna sestavení rozhraní jsou již odkazována. K prozkoumání odkazů v rozhraní použijte Prohlížeč objektů.

2. **Rozšíření** vypíše všechna sestavení, která vyvinuli externí dodavatelé komponent a ovládacích prvků pro rozšíření cílové architektury. Podle účelu dané aplikace mohou být tato sestavení potřebná.

   **Rozšíření** se naplní výčtem sestavení, která jsou zaregistrována v následujících umístěních:

   32bitový počítač:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   64bitový počítač:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   A starší verze identifikátoru [Target Framework Identifier]

   Pokud například projekt cílí na 32bitový počítač .NET Framework **4,** rozšíření vytvoří výčet sestavení registrovaných ve *složce \Microsoft \. NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft \. NETFramework\v3.5\AssemblyFoldersEx*, *\Microsoft \. NETFramework\v3.0\AssemblyFoldersEx* a *\Microsoft \. NETFramework\v2.0\AssemblyFoldersEx*.

Některé komponenty v seznamu se nemusí zobrazit v závislosti na verzi architektury projektu. K tomu může dojít za následujících podmínek:

- Komponenta, která používá nejnovější verzi architektury, je nekompatibilní s projektem, který cílí na starší verzi.

   Informace o tom, jak změnit verzi cílové architektury projektu, najdete v tématu [Přehled cílení na rozhraní.](visual-studio-multi-targeting-overview.md)

- Komponenta, která používá .NET Framework 4, není kompatibilní s projektem, který cílí na .NET Framework 4.5.

Měli byste se vyhnout přidávání odkazů na soubory do výstupů jiného projektu ve stejném řešení, protože to může způsobit chyby kompilace. Místo toho použijte kartu  **Projekty** dialogového okna Přidat odkaz k vytvoření odkazů mezi projekty. To usnadňuje týmový vývoj tím, že umožňuje lepší správu knihoven tříd, které vytvoříte ve svých projektech. Další informace najdete v tématu Řešení [potíží s poškozenými odkazy.](../ide/troubleshooting-broken-references.md)

> [!NOTE]
> V Visual Studio 2015 nebo novějším se místo odkazu na projekt vytvoří odkaz na soubor, pokud je verze cílové architektury jednoho projektu .NET Framework 4.5 nebo novější a cílová verze druhého projektu je .NET Framework 2, 3, 3.5 nebo 4.0.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Zobrazení sestavení v dialogovém okně Přidat odkaz

- Přesuňte nebo zkopírujte sestavení do jednoho z následujících umístění:

  - Aktuální adresář projektu. (Tato sestavení najdete na kartě **Procházet.)**

  - Další adresáře projektu ve stejném řešení. (Tato sestavení můžete najít na kartě **Projekty.)**

  \- nebo –

- Nastavte klíč registru, který určuje umístění sestavení, která se mají zobrazit:

  Pro 32bitový operační systém přidejte jeden z následujících klíčů registru.

  - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  Pro 64bitový operační systém přidejte do 32bitového podregistru registru jeden z následujících klíčů registru.

  - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  *\<VersionMinimum\>* je nejnižší verze architektury, která se na tuto verzi vztahuje. Pokud je verze 3.0, složky zadané v AssemblyFoldersEx se vztahují na projekty, které jsou *\<VersionMinimum\>* .NET Framework 3.0 a  novější.

  *\<AssemblyLocation\>* je adresář sestavení, která chcete zobrazit v  dialogovém okně Přidat odkaz, například *C:\MyAssemblies*.

  Vytvoření klíče registru v uzlu umožňuje všem uživatelům zobrazit sestavení v zadaném umístění `HKEY_LOCAL_MACHINE` v dialogovém okně **Přidat** odkaz. Vytvoření klíče registru v `HKEY_CURRENT_USER` uzlu ovlivní pouze nastavení aktuálního uživatele.

  Znovu otevřete **dialogové okno** Přidat odkaz. Sestavení by se měla zobrazit na **kartě .NET.** Pokud ne, ujistěte se, že jsou sestavení umístěna v zadaném adresáři *AssemblyLocation,* restartujte Visual Studio a zkuste to znovu.

## <a name="projects-tab"></a>Karta Projekty

Karta **Projekty** obsahuje seznam všech kompatibilních projektů v rámci aktuálního řešení na dílčí **kartě** Řešení.

Projekt může odkazovat na jiný projekt, který cílí na jinou verzi architektury. Můžete například vytvořit projekt, který cílí na .NET Framework 4, ale který odkazuje na sestavení vytvořené pro .NET Framework 2. Projekt .NET Framework 2 ale nemůže odkazovat na projekt .NET Framework 4. Další informace najdete v tématu [Přehled cílení na rozhraní.](../ide/visual-studio-multi-targeting-overview.md)

> [!NOTE]
> Projekt, který cílí na .NET Framework 4, není kompatibilní s projektem, který cílí na .NET Framework 4 Profil klienta.

## <a name="shared-projects-tab"></a>Karta Sdílené projekty

Přidejte odkaz na sdílený projekt na **kartě Sdílené projekty** v dialogovém okně Správce odkazů. [Sdílené projekty](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) umožňují psát společný kód, na který odkazuje řada různých projektů aplikací.

## <a name="universal-windows-tab"></a>Karta Univerzální systém Windows

Karta **Univerzální systém Windows** obsahuje seznam všech sdk specifických pro platformy, na kterých běží operační systém Windows.
Tato karta má dvě podskupiny: **Core (Jádro)** a **Extensions (Rozšíření).**

### <a name="core-subgroup"></a>Základní podskupina

Projekty univerzálních aplikací pro Windows mají ve výchozím nastavení odkaz Windows SDK univerzálních aplikací. Proto  **podskupina Core** ve Správci odkazů nevyjmenováuje žádná sestavení z univerzálního Windows SDK.

### <a name="extensions-subgroup"></a>Podskupina rozšíření

**Rozšíření** uvádí seznam uživatelských sdk, které rozšiřují cílovou platformu Windows.

Sada SDK je kolekce souborů, které sada Visual Studio považuje za jedinou součást. Na kartě **Rozšíření** jsou jako jednotlivé položky uvedeny skupiny SDK, které platí pro projekt, ze kterého bylo vyvoláno dialogové okno Správce odkazů. Při přidání do projektu využívá veškerý obsah sady SDK Visual Studio tak, že uživatel nemusí provádět žádné další akce, aby využil obsah sady SDK v IntelliSense, sadě nástrojů, návrhářích, prohlížeči objektů, sestavení, nasazení, ladění a balení.

Informace o tom, jak zobrazit sadu SDK na **kartě Rozšíření,** najdete v tématu [Creating a Software Development Kit](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> Pokud projekt odkazuje na sadu SDK, která závisí na jiné sadě SDK, Visual Studio nebude druhou sadu SDK využívat, pokud ručně přidáte odkaz na druhou sadu SDK. Když uživatel vybere sadu SDK  na kartě Rozšíření, dialogové okno Správce odkazů vám pomůže identifikovat závislosti sady SDK výpisem závislostí v podokně podrobností.

Pokud typ projektu nepodporuje rozšíření, tato karta se v dialogovém okně Správce odkazů nezobrazí.

## <a name="com-tab"></a>Karta COM

Karta **com** obsahuje seznam všech komponent modelu COM, které jsou k dispozici pro odkazování. Pokud chcete přidat odkaz na registrovanou knihovnu DLL modelu COM, která obsahuje vnitřní manifest, nejprve zrušte registraci dané knihovny DLL. V opačném případě Visual Studio přidá odkaz na sestavení jako ovládací prvek ActiveX namísto jako nativní knihovnu DLL.

Pokud typ projektu nepodporuje model COM, karta se v dialogovém okně Správce odkazů nezobrazí.

## <a name="browse"></a>Procházet

K procházení součásti v systému souborů můžete použít tlačítko **Procházet** .

Projekt může odkazovat na komponentu, která cílí na jinou verzi rozhraní. Můžete například vytvořit aplikaci, která cílí na .NET Framework 4,7, ale odkazuje na součást, která cílí na .NET Framework 4. Další informace najdete v tématu [Přehled cílení na rozhraní](../ide/visual-studio-multi-targeting-overview.md).

Vyhněte se přidávání odkazů na soubory do výstupů jiného projektu ve stejném řešení, protože tento cílem může způsobit chyby kompilace. Místo toho použijte kartu **řešení** v dialogovém okně Správce odkazů k vytvoření odkazů typu projekt-projekt. To usnadňuje vývoj v týmu povolením lepší správy knihoven tříd, které vytvoříte ve svých projektech. Další informace najdete v tématu [řešení potíží s poškozenými odkazy](../ide/troubleshooting-broken-references.md).

Nemůžete procházet sadu SDK a přidat ji do projektu. Můžete přejít pouze k souboru (například sestavení nebo *. winmd*) a přidat ho do projektu.

Při odkazování na soubor winmd je očekávané rozložení, že soubory *\<FileName> . winmd*, *\<FileName>.dll* a *\<FileName> . pri* jsou umístěny vedle sebe. Pokud odkazujete na soubor WinMD v následujících scénářích, do výstupního adresáře projektu budou zkopírovány neúplné sady souborů a v důsledku toho dojde k chybám při sestavení a za běhu.

- **Nativní komponenta**: nativní projekt vytvoří jednu winmd pro každou nesouvislou sadu oborů názvů a jednu knihovnu DLL, která se skládá z implementace. Soubory WinMDs budou mít nesouvislé názvy. Při odkazování na tento soubor nativní komponenty nástroj MSBuild nerozpozná, že s názvem soubory WinMD vytvořit jednu komponentu. V důsledku toho budou zkopírovány pouze identicky pojmenované *\<FileName>.dll* a *\<FileName> . winmd* a dojde k chybám za běhu. Pokud chcete tento problém obejít, vytvořte sadu SDK rozšíření. Další informace najdete v tématu [Vytvoření sady SDK (Software Development Kit](../extensibility/creating-a-software-development-kit.md)).

- **Spotřebovávání ovládacích prvků**: ovládací prvek XAML je přinejmenším tvořen *\<FileName> příponou winmd*, *\<FileName>.dll*, *\<FileName> . pri*, *\<XamlName> . XAML* a *\<ImageName>.jpg*. Po sestavení projektu se soubory prostředků, které jsou spojeny s odkazem na soubor, nezkopírují do výstupního adresáře projektu a zkopírují se pouze soubory *\<FileName> . winmd*, *\<FileName>.dll* a *\<FileName> . pri* . Chyba sestavení je protokolována, aby informovala uživatele o chybějících objektech Resources *\<XamlName> . xaml* a *\<ImageName>.jpg* . Aby sestavení proběhlo úspěšně, bude uživatel muset ručně zkopírovat tyto soubory prostředků do výstupního adresáře projektu pro sestavení a ladění/dobu běhu. Pokud chcete tento problém obejít, buď vytvořte sadu rozšíření SDK podle kroků v části [Vytvoření sady Software Development Kit](../extensibility/creating-a-software-development-kit.md) nebo upravte soubor projektu a přidejte následující vlastnost:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Pokud tuto vlastnost přidáte, může být sestavení pomalejší.

## <a name="recent"></a>Nedávné

**Sestavení**, **com**, **Windows** a **procházení** jednotlivých **podporovaných karet,** které vyčíslují seznam komponent, které byly nedávno přidány do projektů.

## <a name="search"></a>Hledat

Panel hledání v dialogovém okně Správce odkazů funguje na kartě, která je zaostření. Pokud například uživatel zadá na panelu hledání text "System", zatímco je karta **řešení** aktivní, hledání nevrátí žádné výsledky, pokud se toto řešení neskládá z názvu projektu, který obsahuje "System".

## <a name="see-also"></a>Viz také

- [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)
