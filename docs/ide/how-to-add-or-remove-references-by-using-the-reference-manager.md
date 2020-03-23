---
title: Přidání odkazů do správce odkazů
ms.date: 08/02/2019
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dfad622a7587246836161cd79bb5b759151df1ef
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595307"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Postup: Přidání nebo odebrání odkazů pomocí Správce odkazů

Dialogové okno Správce odkazů můžete použít k přidání a správě odkazů na součásti, které jste vy, společnost Microsoft nebo jiná společnost vyvinula. Pokud vyvíjíte univerzální aplikaci pro Windows, projekt automaticky odkazuje na všechny správné knihovny DLL sady Windows SDK. Pokud vyvíjíte aplikaci .NET, projekt automaticky odkazuje na *soubor mscorlib.dll*. Některá rozhraní API rozhraní .NET jsou vystavena součástem, které je nutné přidat ručně. Odkazy na součásti modelu COM nebo vlastní součásti je třeba přidat ručně.

## <a name="reference-manager-dialog-box"></a>Dialogové okno Správce odkazů

Dialogové okno Správce odkazů zobrazuje různé kategorie na levé straně v závislosti na typu projektu:

- **Sestavení**, s podskupinami **Framework** a **Extensions**

- **Model COM** uvádí všechny součásti modelu COM, které jsou k dispozici pro odkazování.

- **Projekty**

- **Sdílené projekty**

- **Windows**, s podskupinami **Core** a **Extensions.** Odkazy v sadě Windows SDK nebo sadách SDK lze prozkoumat pomocí **prohlížeče objektů**.

- **Procházet**, s **poslední** podskupinou

## <a name="add-a-reference"></a>Přidání odkazu

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel **Odkazy** nebo **závislosti** a zvolte **Přidat odkaz**. Můžete také kliknout pravým tlačítkem myši na uzel projektu a vybrat **přidat** > **odkaz**.

   **Správce odkazů** otevře a zobrazí seznam dostupných odkazů podle skupin.

2. Zadejte odkazy, které chcete přidat, a pak vyberte **OK**.

## <a name="assemblies-tab"></a>Karta Sestavení

Na kartě **Sestavení** jsou uvedena všechna sestavení rozhraní .NET, která jsou k dispozici pro odkazování. Na kartě **Sestavení** nejsou uvedena žádná sestavení z globální mezipaměti sestavení (GAC), protože sestavení v gac jsou součástí prostředí run-time. Pokud nasadíte nebo zkopírujete aplikaci, která obsahuje odkaz na sestavení, které je registrované v GAC, sestavení nebude nasazeno nebo zkopírováno s aplikací, bez ohledu na nastavení **Kopírovat místní.** Další informace naleznete [v tématu Správa odkazů v projektu](../ide/managing-references-in-a-project.md).

Když ručně přidáte odkaz na některý z oborů názvů<xref:EnvDTE> <xref:EnvDTE80>EnvDTE ( , <xref:EnvDTE90>, <xref:EnvDTE90a>, , nebo <xref:EnvDTE100>), nastavte vlastnost **Embed Interop Types** odkazu na **False** v okně **Vlastnosti.** Nastavení této vlastnosti na **Hodnotu True** může způsobit problémy se sestavením z důvodu určitých vlastností EnvDTE, které nelze vložit.

Všechny projekty plochy obsahují implicitní odkaz na **mscorlib**. Projekty jazyka obsahují implicitní odkaz na <xref:Microsoft.VisualBasic>. Všechny projekty obsahují implicitní odkaz na **System.Core**, i v případě, že je odebrán ze seznamu odkazů.

Pokud typ projektu nepodporuje sestavení, karta se nezobrazí v dialogovém okně Správce odkazů.

Karta **Sestavy** se skládá ze dvou dílčích karet:

1. **Framework** uvádí všechny sestavení, které tvoří cílový rámec.

   U projektů, které necílí na rozhraní .NET Core nebo univerzální platformu Windows, se na kartě **Framework** vyjmenovává sestavení z cílového rozhraní. Uživatel musí přidat všechny odkazy, které aplikace vyžaduje.

   Univerzální projekty systému Windows obsahují odkazy na všechna sestavení v cílové matné rámci ve výchozím nastavení. Ve spravovaných projektech uzel jen pro čtení ve složce **References** v **Průzkumníku řešení** označuje odkaz na celý rámec. V souladu s tím **framework** karta není výčet žádné sestavení z rámce a místo toho zobrazí následující zprávu: "Všechny sestavení rozhraní jsou již odkazuje. Prosím, použijte prohlížeč objektů prozkoumat odkazy v rámci".

2. **Rozšíření uvádí** všechna sestavení, která vyvinuli externí dodavatelé součástí a ovládacích prvků pro rozšíření cílového rámce. Podle účelu dané aplikace mohou být tato sestavení potřebná.

   **Rozšíření** je naplněna výčet sestavení, které jsou registrovány v následujících umístěních:

   32bitový stroj:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   64bitový stroj:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   A starší verze [Identifikátor cílového rozhraní]

   Pokud se například projekt zaměřuje na rozhraní .NET Framework 4 v 32bitovém počítači, **rozšíření** vytvoří výčet sestavení, která jsou registrována pod *\Microsoft\.NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.5\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.0\AssemblyFoldersEx*a *\Microsoft\.NETFramework\v2.0\AssemblyExFolders*.

Některé součásti v seznamu nemusí být zobrazeny, v závislosti na verzi architektury projektu. K tomu může dojít za následujících podmínek:

- Součást, která používá poslední verzi architektury, není kompatibilní s projektem, který cílí na starší verzi.

   Informace o tom, jak změnit verzi cílového rozhraní pro projekt, naleznete v [tématu Přehled cílení na rozhraní .](visual-studio-multi-targeting-overview.md)

- Součást, která používá rozhraní .NET Framework 4, není kompatibilní s projektem, který cílí na rozhraní .NET Framework 4.5.

Měli byste se vyhnout přidávání odkazů na soubory do výstupů jiného projektu ve stejném řešení, protože to může způsobit chyby kompilace. Místo toho použijte kartu **Projekty** v dialogovém okně **Přidat odkaz** k vytvoření odkazů projektu na projekt. To usnadňuje vývoj týmu tím, že umožňuje lepší správu knihoven tříd, které vytvoříte ve svých projektech. Další informace naleznete [v tématu Poradce při potížích s nefunkčními odkazy](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> V sadě Visual Studio 2015 nebo novější je vytvořen odkaz na soubor namísto odkazu na projekt, pokud je verze cílového rozhraní jednoho projektu .NET Framework 4.5 nebo novější a cílová verze jiného projektu je .NET Framework 2, 3, 3.5 nebo 4.0.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Zobrazení sestavy v dialogovém okně Přidat odkaz

- Přesunutí nebo zkopírování sestavy do jednoho z následujících umístění:

  - Aktuální adresář projektu. (Tato sestavení můžete najít pomocí karty **Procházet.)**

  - Další adresáře projektu ve stejném řešení. (Tato sestavení můžete najít pomocí karty **Projekty.)**

  \-nebo -

- Nastavte klíč registru, který určuje umístění sestavení, která se mají zobrazit:

  Pro 32bitový operační systém přidejte jeden z následujících klíčů registru.

  - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  Pro 64bitový operační systém přidejte jeden z následujících klíčů registru do podregistru s 32bitovým registrem.

  - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  *VersionMinimum\> je nejnižší verze rozhraní, která \<* platí. Pokud * \<VersionMinimum\> * je v3.0, složky zadané v *AssemblyFoldersEx* platí pro projekty, které cílí na rozhraní .NET Framework 3.0 a novější.

  *AssemblyLocation\> je adresář sestavení, která se mají zobrazit v dialogovém okně Přidat odkaz, například C:\MyAssemblies \<* . **Add Reference** *C:\MyAssemblies*

  Vytvoření klíče registru `HKEY_LOCAL_MACHINE` pod uzlem umožňuje všem uživatelům zobrazit sestavení v zadaném umístění v dialogovém okně **Přidat odkaz.** Vytvoření klíče registru `HKEY_CURRENT_USER` pod uzlem ovlivní pouze nastavení pro aktuálního uživatele.

  Znovu otevřete dialogové okno **Přidat odkaz.** Sestavení by se měla zobrazit na kartě **.NET.** Pokud tomu tak není, ujistěte se, že sestavení jsou umístěny v zadaném *adresáři AssemblyLocation,* restartujte visual studio a zkuste to znovu.

## <a name="projects-tab"></a>Karta Projekty

Na kartě **Projekty** jsou uvedeny všechny kompatibilní projekty v rámci aktuálního řešení na kartě **Řešení.**

Projekt může odkazovat na jiný projekt, který se zaměřuje na jinou verzi architektury. Můžete například vytvořit projekt, který cílí na rozhraní .NET Framework 4, ale odkazuje na sestavení, které bylo vytvořeno pro rozhraní .NET Framework 2. Projekt rozhraní .NET Framework 2 však nemůže odkazovat na projekt rozhraní .NET Framework 4. Další informace naleznete v [tématu Přehled cílení na rozhraní Framework](../ide/visual-studio-multi-targeting-overview.md).

> [!NOTE]
> Projekt, který cílí na rozhraní .NET Framework 4, není kompatibilní s projektem, který cílí na profil klienta rozhraní .NET Framework 4.

## <a name="shared-projects-tab"></a>Karta Sdílené projekty

Přidejte odkaz na sdílený projekt na kartě **Sdílené projekty** v dialogovém okně Správce odkazů. [Sdílené projekty](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) umožňují psát společný kód, na který odkazuje řada různých aplikačních projektů.

## <a name="universal-windows-tab"></a>Univerzální karta Windows

Na kartě **Univerzální systém Windows** jsou uvedeny všechny sady SDK, které jsou specifické pro platformy, na kterých jsou spuštěny operační systémy Windows.
Tato karta má dvě podskupiny: **Core** a **Rozšíření**.

### <a name="core-subgroup"></a>Základní podskupina

Univerzální projekty aplikací pro Windows mají ve výchozím nastavení odkaz na univerzální sadu Windows SDK. V souladu s tím **základní** podskupina ve **Správci odkazů** neuvádí výčet žádné sestavení z univerzální sady Windows SDK.

### <a name="extensions-subgroup"></a>Podskupina rozšíření

**Rozšíření uvádí** uživatelské sady SDK, které rozšiřují cílovou platformu systému Windows.

Sada SDK je kolekce souborů, které sada Visual Studio považuje za jedinou součást. Na kartě **Rozšíření** jsou sady SDK, které se vztahují k projektu, ze kterého bylo vyvoláno dialogové okno Správce odkazů, uvedeny jako jednotlivé položky. Při přidání do projektu je veškerý obsah sady SDK spotřebován aplikací Visual Studio tak, aby uživatel nemusel provádět žádné další akce, aby využil obsah sady SDK v aplikaci IntelliSense, panel nástrojů, návrháři, prohlížeč objektů, sestavení, nasazení, ladění a balení.

Informace o zobrazení sady SDK na kartě **Rozšíření** naleznete v tématu Vytvoření sady [Software Development Kit](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> Pokud projekt odkazuje na sdk, která závisí na jiné sadě SDK, Visual Studio nebude využívat druhou sdk, pokud ručně přidat odkaz na druhou sadu SDK. Když uživatel vybere sadu SDK na kartě **Rozšíření,** dialogové okno Správce odkazů vám pomůže identifikovat závislosti sady SDK tím, že v podokně podrobností uvede všechny závislosti.

Pokud typ projektu rozšíření nepodporuje, tato karta se v dialogovém okně Správce odkazů nezobrazí.

## <a name="com-tab"></a>Karta COM

Na kartě **COM** jsou uvedeny všechny součásti modelu COM, které jsou k dispozici pro odkazování. Pokud chcete přidat odkaz na registrovanou knihovnu DLL modelu COM, která obsahuje vnitřní manifest, nejprve zrušte registraci dané knihovny DLL. V opačném případě Visual Studio přidá odkaz na sestavení jako ovládací prvek ActiveX namísto jako nativní dll.

Pokud typ projektu nepodporuje com, karta se nezobrazí v dialogovém okně Správce odkazů.

## <a name="browse"></a>Procházet

Pomocí tlačítka **Procházet** můžete vyhledat komponentu v systému souborů.

Projekt může odkazovat na komponentu, která se zaměřuje na jinou verzi architektury. Můžete například vytvořit aplikaci, která cílí na rozhraní .NET Framework 4.7, ale odkazuje na komponentu, která cílí na rozhraní .NET Framework 4. Další informace naleznete v [tématu Přehled cílení na rozhraní Framework](../ide/visual-studio-multi-targeting-overview.md).

Vyhněte se přidávání odkazů na soubory do výstupů jiného projektu ve stejném řešení, protože tato taktika může způsobit chyby kompilace. Místo toho použijte kartu **Řešení** v dialogovém okně Správce odkazů k vytvoření odkazů mezi projekty. To usnadňuje vývoj týmu tím, že umožňuje lepší správu knihoven tříd, které vytvoříte ve svých projektech. Další informace naleznete [v tématu Poradce při potížích s nefunkčními odkazy](../ide/troubleshooting-broken-references.md).

Nelze přejít na sdk a přidat ji do projektu. Můžete pouze procházet soubor (například sestavení nebo *.winmd*) a přidat jej do projektu.

Při použití odkazu na soubor WinMD je očekávané rozložení, že soubory * \<FileName>.winmd*, * \<FileName>.dll*a * \<FileName>.pri* jsou umístěny vedle sebe. Pokud odkazujete na soubor WinMD v následujících scénářích, do výstupního adresáře projektu budou zkopírovány neúplné sady souborů a v důsledku toho dojde k chybám při sestavení a za běhu.

- **Nativní komponenta**: nativní projekt vytvoří jeden WinMD pro každou nesouvislou sadu oborů názvů a jednu dll, která se skládá z implementace. Soubory WinMDs budou mít nesouvislé názvy. Při odkazování na tento nativní soubor komponenty MSBuild nerozpozná, že podobně pojmenované WinMD vytvoří jednu součást. V důsledku toho budou zkopírovány pouze identicky pojmenované * \<FileName>.dll* a * \<FileName>.winmd* a dojde k chybám za běhu. Chcete-li tento problém vyřešit, vytvořte rozšíření Sady SDK. Další informace naleznete [v tématu Create a Software Development Kit](../extensibility/creating-a-software-development-kit.md).

- **Spotřebovávající ovládací prvky**: minimálně ovládací prvek XAML se skládá z * \<filename>.winmd*, * \<FileName>.dll*, * \<FileName>.pri*, * \<XamlName>.xaml*a * \<ImageName>.jpg*. Po seřízení projektu nebudou soubory prostředků přidružené k odkazu na soubor zkopírovány do výstupního adresáře projektu a zkopírují se pouze * \<Název souboru>.winmd*, * \<FileName>.dll* a * \<FileName>.pri.* Je zaznamenána chyba sestavení, která informuje uživatele, že chybí prostředky * \<XamlName>.xaml* a * \<ImageName>.jpg.* Aby sestavení proběhlo úspěšně, bude uživatel muset ručně zkopírovat tyto soubory prostředků do výstupního adresáře projektu pro sestavení a ladění/dobu běhu. Chcete-li tento problém vyřešit, vytvořte rozšíření SDK podle kroků v [tématu Vytvoření sady pro vývoj softwaru](../extensibility/creating-a-software-development-kit.md) nebo upravte soubor projektu a přidejte následující vlastnost:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Pokud tuto vlastnost přidáte, může být sestavení pomalejší.

## <a name="recent"></a>Nedávné

**Sestavení**, **COM**, **Windows**a **Procházet** každý podporuje **poslední** kartu, která obsahuje výčet seznamu součástí, které byly nedávno přidány do projektů.

## <a name="search"></a>Search

Vyhledávací panel v dialogovém okně Správce odkazů funguje přes kartu, která je zaostřená. Například pokud uživatel zadá "Systém" v řádku hledání, zatímco **řešení** karta je v centru pozornosti, hledání nevrátí žádné výsledky, pokud řešení se skládá z názvu projektu, který obsahuje "Systém".

## <a name="see-also"></a>Viz také

- [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)
