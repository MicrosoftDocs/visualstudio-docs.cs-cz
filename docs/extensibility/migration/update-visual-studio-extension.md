---
title: Aktualizace rozšíření sady Visual Studio
description: Naučte se aktualizovat rozšíření sady Visual Studio pro práci se sadou Visual Studio 2022.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 6e7c4990d513bfb276984611b2d38f3e35a825eb
ms.sourcegitcommit: a7a4c5545a269ca74a7291966ff77afb3b57f5ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2021
ms.locfileid: "112424650"
---
# <a name="update-a-visual-studio-extension-for-visual-studio-2022"></a>Aktualizace rozšíření sady Visual Studio pro Visual Studio 2022

> [!IMPORTANT]
> Doporučení v tomto průvodci je určeno pro vývojáře v migraci rozšíření, která vyžadují významné změny v práci v aplikaci Visual Studio 2019 a 2022. V těchto případech doporučujeme mít dva VSIX projekty a podmíněnou kompilaci.
> Mnohé rozšíření budou moci pracovat v rámci sady Visual Studio 2019 a 2022 s menšími změnami, které nevyžadují postup podle pokynů pro modernizaci rozšíření v této příručce.
> Vyzkoušejte si rozšíření v aplikaci Visual Studio 2022 a vyhodnoťte, jaká možnost je nejvhodnější pro vaše rozšíření.

Pomocí této příručky můžete aktualizovat rozšíření pro práci se sadou Visual Studio 2022 Preview. Visual Studio 2022 Preview je 64 aplikace a zavádí některé zásadní změny v sadě VS SDK. Tato příručka vás provede kroky potřebnými k tomu, aby vaše rozšíření fungovalo s aktuální verzí Preview sady Visual Studio 2022, takže vaše rozšíření může být připravené pro uživatele, aby je nainstaloval před tím, než Visual Studio 2022 dosáhne GA.

## <a name="installing"></a>Instalace

Nainstalujte Visual Studio 2022 Preview ze sady [Visual studio 2022 Preview downloads](https://visualstudio.microsoft.com/vs/preview/vs2022).

### <a name="extensions-written-in-a-net-language"></a>Rozšíření napsaná v jazyce .NET

Sada VS SDK cílící na Visual Studio 2022 pro spravovaná rozšíření je *výhradně* na NuGet:

- Meta balíček [Microsoft. VisualStudio. SDK](https://www.nuget.org/packages/Microsoft.VisualStudio.Sdk/) (17. x verze) přináší většinu nebo všechna referenční sestavení, která budete potřebovat.
- Na balíček [Microsoft. VSSDK. BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools/) (verze 17. x) by se měl odkazovat z projektu VSIX, aby mohl sestavit soubor VSIX kompatibilní s Visual studiem 2022.

Rozšíření *musí* být kompilována s platformou "any CPU" nebo "x64". Platforma "x86" není kompatibilní s procesem 64 sady Visual Studio 2022.

### <a name="extensions-written-in-c"></a>Rozšíření napsaná v jazyce C++

Sada VS SDK pro rozšíření kompilovaná s jazykem C++ je k dispozici s nainstalovanou sadou Visual Studio SDK, a to obvyklým způsobem.

Rozšíření *musí* být zkompilována konkrétně pro sadu Visual Studio 2022 SDK a pro AMD64.

### <a name="update-your-extension-to-visual-studio-2022"></a>Aktualizace rozšíření na Visual Studio 2022

#### <a name="extensions-with-running-code"></a>Rozšíření s běžícím kódem

Rozšíření se spuštěným kódem *musí* být zkompilována speciálně pro Visual Studio 2022. Visual Studio 2022 nebude načítat žádné rozšíření, které necílí na Visual Studio 2022 konkrétně.

Naučte se migrovat rozšíření pre-Visual Studio 2022 do sady Visual Studio 2022:

1. [Modernizovat své projekty](#modernize-your-vsix-project).
1. [Refaktorujte zdrojový kód do sdíleného projektu](#use-shared-projects-for-multi-targeting) , aby bylo možné cílit na Visual Studio 2022 a starší verze.
1. [Přidejte projekt VSIX cílené na sadu Visual Studio 2022](#add-a-visual-studio-2022-target)a naše [tabulka přemapování balíčku nebo sestavení](migrated-assemblies.md).
1. [Provádění nezbytných úprav kódu](#handle-breaking-api-changes).
1. [Testování rozšíření sady Visual Studio 2022](#test-your-extension).
1. [Publikování rozšíření sady Visual Studio 2022](#publish-your-extension).

#### <a name="extensions-without-running-code"></a>Rozšíření bez spuštění kódu

Rozšíření, která neobsahují žádný spuštěný Kód (například šablony projektu nebo položky), *nemusejí splňovat* výše uvedené kroky, včetně výroby dvou různých VSIX.

Místo toho by se měl změnit jeden VSIX, takže jeho `source.extension.vsixmanifest` soubor deklaruje dva cíle instalace, například:

```xml
<Installation>
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0,17.0)">
      <ProductArchitecture>x86</ProductArchitecture>
   </InstallationTarget>
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
</Installation>
```

Pomocí sdílených projektů a více VSIX můžete přeskočit kroky v tomto článku. Můžete pokračovat v [testování](#test-your-extension).

> [!NOTE]
> Pokud vytváříte *nové* rozšíření sady Visual Studio, pomocí sady visual Studio 2022 Preview a chcete (také) cílit na visual Studio 2019 nebo starší verzi, Projděte si [tuto příručku](target-previous-versions.md).

### <a name="msbuild-tasks"></a>úlohy nástroje MSBuild

Pokud vytváříte úlohy MSBuild, uvědomte si, že v aplikaci Visual Studio 2022 je mnohem pravděpodobnější, že budou načteny do 64 bitového procesu MSBuild.exe. Pokud úloha vyžaduje spuštění procesu 32, přečtěte si v [této dokumentaci](../../msbuild/how-to-configure-targets-and-tasks.md#usingtask-attributes-and-task-parameters) k nástroji MSBuild, abyste zajistili, že nástroj MSBuild ví, jak načíst úlohu v procesu 32.

## <a name="modernize-your-vsix-project"></a>Modernizovat projekt VSIX

Než do svého rozšíření přidáte podporu sady Visual Studio 2022, důrazně doporučujeme, abyste tuto dobu vyčistili a modernizovati stávající projekt, a teprve potom můžete pokračovat, včetně:

1. [Migrujte z packages.config `PackageReference` na ](/nuget/consume-packages/migrate-packages-config-to-package-reference).

1. Nahraďte všechna přímá sestavení a odkazy sestavení sady SDK s PackageReference položkami.

   ```diff
   -<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   +<PackageReference Include="Microsoft.VisualStudio.OLE.Interop" Version="..." />
   ```

   > [!TIP]
   > Můžete nahradit *mnoho* odkazů na sestavení pouze *jedním* PackageReference na naši Metapackage:
   >
   >```diff
   >-<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop.8.0" />
   >+<PackageReference Include="Microsoft.VisualStudio.Sdk" >Version="..." />
   >```

   Nezapomeňte vybrat verze balíčků, které odpovídají minimální verzi sady Visual Studio, na kterou cílíte.

   Některá sestavení, která nejsou jedinečná pro sadu VS SDK (například Newtonsoft.Json.dll), mohla být zjistitelná prostřednictvím jednoduchého `<Reference Include="Newtonsoft.Json" />` odkazu před sadou Visual studio 2022, ale v sadě Visual studio 2022 místo toho vyžaduje odkaz na balíček z důvodu, že v sadě Visual studio 2022 odeberu některé adresáře modulu runtime a sady Visual Studio z výchozího umístění pro vyhledávání sestavení nástroje MSBuild.

   Při přepínání z přímých odkazů sestavení na odkazy na balíček NuGet můžete vybrat další odkazy na sestavení a balíčky analyzátoru, protože NuGet automaticky instaluje přenosný uzávěr závislostí. Tato situace je obecně v pořádku, ale může vést k tomu, že během sestavení dojde k příznaku dalších upozornění. Pomocí těchto upozornění můžete vyřešit tolik, kolik máte, jak můžete, a zvažte potlačení těchto upozornění, která nebudete moci vyřešit pomocí oblastí v kódu `#pragma warning disable <id>` .

## <a name="use-shared-projects-for-multi-targeting"></a>Použití sdílených projektů pro cílení na více platforem

[Sdílené projekty](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) jsou typ projektu, který byl představen v aplikaci Visual Studio 2015. Sdílené projekty v sadě Visual Studio umožňují sdílet soubory zdrojového kódu mezi více projekty a sestavovat jinak pomocí symbolů podmíněné kompilace a jedinečných sad odkazů.

Vzhledem k tomu, že sada Visual Studio 2022 vyžaduje odlišnou sadu referenčních sestavení ze všech předchozích verzí VS, náš návod je použít sdílené projekty k pohodlnému vícenásobnému zaměření rozšíření na předběžnou sadu Visual Studio 2022 a sady Visual Studio 2022 (a novější verze), což vám umožní sdílení kódu, ale jedinečné odkazy.

V kontextu rozšíření aplikace Visual Studio můžete mít jeden projekt VSIX pro Visual Studio 2022 a novější a jeden projekt VSIX pro Visual Studio 2019 a starší. Každá z těchto projektů by obsahovala pouze `source.extension.vsixmanifest` a a balíček odkazuje buď na 16. x SDK, nebo na sadu 17. x SDK. Tyto projekty VSIX by také měly odkaz na sdílený projekt na nový sdílený projekt, který bude hostovat veškerý zdrojový kód, který lze sdílet ve dvou verzích VS.

Jako výchozí bod pro tento dokument budeme předpokládat, že už máte projekt VSIX, který se zaměřuje na Visual Studio 2019 a že chcete, aby rozšíření fungovalo v aplikaci Visual Studio 2022.

Všechny tyto kroky lze dokončit v aplikaci Visual Studio 2019.

1. Pokud jste to ještě neudělali, [modernizovat své projekty](#modernize-your-vsix-project) , aby se v tomto procesu aktualizace usnadnily kroky později.

1. Přidejte nový sdílený projekt do řešení pro každý existující projekt, který odkazuje na sadu VS SDK.
   ![Přidat nový projekt – příkaz ](media/update-visual-studio-extension/add-new-project.png)
    ![ Nová šablona projektu](media/update-visual-studio-extension/new-shared-project-template.png)

1. Přidejte odkaz z každého projektu sady VS SDK odkazující na jeho protějšek sdíleného projektu.
   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Přidat odkaz na sdílený projekt" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Přesuňte veškerý zdrojový kód (včetně. cs,. resx) z každého projektu sady VS SDK odkazující na jeho protějšek sdíleného projektu.
Ponechte `source.extension.vsixmanifest` soubor v projektu VSIX.
   ![Sdílený projekt obsahuje všechny zdrojové soubory.](media/update-visual-studio-extension/source-files-in-shared-project.png)

1. Soubory metadat (poznámky k verzi, licence, ikony atd.) a soubory VSCT by měly být přesunuty do sdíleného adresáře a přidány jako propojené soubory do projektu VSIX.
   ![Přidání metadat a souborů VSCT jako propojených souborů](media/update-visual-studio-extension/add-linked-items-to-vsix.png)
    - V případě souborů metadat nastavte BuildAction na `Content` a set include in VSIX na `true` .

      ![Zahrnutí souborů metadat do VSIX](./media/update-visual-studio-extension/include-metadata-files-in-vsix.png)
    - Pro soubory VSCT nastavte BuildAction na `VSCTCompile` a nezahrnovat do VSIX.
      Visual Studio může stěžovateli, že toto nastavení není podporované, ale můžete ručně změnit akci sestavení uvolněním projektu a změnou `Content` na `VSCTCompile`

    ```diff
    -<Content Include="..\SharedFiles\VSIXProject1Package.vsct">
    -  <Link>VSIXProject1Package.vsct</Link>
    -</Content>
    +<VSCTCompile Include="..\SharedFiles\VSIXProject1Package.vsct">
    +  <Link>VSIXProject1Package.vsct</Link>
    +  <ResourceName>Menus.ctmenu</ResourceName>
    +</VSCTCompile>
    ```

      ![Nastavení souborů VSCT jako VSCTCompile](media/update-visual-studio-extension/build-linked-vsct-files.png)

1. Sestavte projekt (y) a potvrďte, že jste nepředstavili žádné nové chyby.

Váš projekt je teď připravený přidat podporu sady Visual Studio 2022.

## <a name="add-a-visual-studio-2022-target"></a>Přidat cíl sady Visual Studio 2022

Tento dokument předpokládá, že jste dokončili kroky pro [faktorování rozšíření sady Visual Studio se sdílenými projekty](#use-shared-projects-for-multi-targeting).

Pokračujte přidáním podpory sady Visual Studio 2022 k vašemu rozšíření pomocí těchto kroků, které mohou být dokončeny pomocí sady Visual Studio 2019:

1. Přidejte do svého řešení nový projekt VSIX. To bude projekt, který se zaměřuje na Visual Studio 2022. Odeberte veškerý zdrojový kód, který byl dodán se šablonou, ale *`source.extension.vsixmanifest` soubor nechte*.

1. V novém projektu VSIX přidejte odkaz na sdílený projekt do stejného sdíleného projektu, který zacílí na odkazy na VSIX v rámci sady Visual Studio 2019.

   ![Řešení s jedním sdíleným projektem a dvěma projekty VSIX](media/update-visual-studio-extension/shared-project-with-two-heads.png)

1. Ověřte, zda se nový projekt VSIX správně vytvoří. Je možné, že budete muset přidat odkazy, které odpovídají původnímu projektu VSIX za účelem vyřešení chyb kompilátoru.

1. U spravovaných rozšíření VS aktualizujte odkazy na balíčky z 16. x (nebo dříve) na verze balíčku 17. x v cílovém souboru projektu sady Visual Studio 2022 nebo pomocí Správce balíčků NuGet nebo přímo úpravou souboru projektu:

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    ```

   Použijete verze, které jsou skutečně dostupné z nuget.org. Dříve použitá jsou jenom pro demonstrační účely.

   V mnoha případech se změnila ID balíčků. Seznam změn v aplikaci Visual Studio 2022 naleznete v [tabulce mapování balíčku nebo sestavení](migrated-assemblies.md) .

   Rozšíření napsaná v jazyce C++ ještě nemají k dispozici sadu SDK, pomocí které by bylo možné kompilovat.

1. Pro projekty v jazyce C++ musí být kompilovány pro AMD64. U spravovaných rozšíření zvažte možnost změnit projekt od sestavení pro jakýkoliv procesor na cílený `x64` , aby odrážel, že v aplikaci Visual Studio 2022 vaše rozšíření vždy načítá v 64m procesu. `Any CPU` je příliš přesné, ale může způsobovat upozornění, pokud odkazujete na jakékoli nativní binární soubory pouze s platformou x64.

   Všechny závislosti, které vaše rozšíření může mít v nativním modulu, bude nutné aktualizovat z image x86 na Image amd64.

1. Upravte `source.extension.vsixmanifest` soubor tak, aby odrážel cílení na Visual Studio 2022. Nastavte `<InstallationTarget>` značku tak, aby odrážela sadu Visual Studio 2022 a označovala datovou část amd64:

   ```xml
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
   ```

   V aplikaci Visual Studio 2019 Návrhář pro tento soubor nevystavuje nový `ProductArchitecture` prvek, takže tuto změnu je třeba provést pomocí editoru XML, ke kterému můžete přistupovat prostřednictvím příkazu **otevřít pomocí** v **Průzkumník řešení**.

   Tento `ProductArchitecture` prvek je kritický. Visual Studio 2022 *nenainstaluje rozšíření* bez něj.

   | Prvek | Hodnota | Popis |
   | - | - | - |
   | ProductArchitecture | X86, AMD64 | Platformy, které tento VSIX podporuje. Nerozlišuje velká a malá písmena. Jedna platforma na prvek a jeden prvek na InstallTarget. Pro verze produktu nižší než 17,0 je výchozí hodnota x86 a lze ji vynechat.  Pro verze produktu 17,0 a větší tento prvek je vyžadován a neexistuje žádná výchozí hodnota. Pro Visual Studio 2022 jediný platný obsah pro tento element je "amd64". |

1. Proveďte další úpravy, které jsou nezbytné ve zdroji. extension. vsixmanifest, aby odpovídaly rozhraní, které cílí na Visual Studio 2019 (pokud existuje). Je důležité, aby ID VSIX v `Identity` elementu manifestu bylo identické pro obě rozšíření.

V tomto okamžiku máte Visual Studio 2022-cílené rozšíření VSIX. Měli byste sestavit projekt VSIX v rámci sady Visual Studio 2022 a [pracovat s případnými konci sestavení, která se zobrazí](#handle-breaking-api-changes). Pokud v projektu VSIX sady Visual Studio 2022 nemáte žádné zalomení sestavení, Blahopřejeme: jste připraveni na testování.

## <a name="handle-breaking-api-changes"></a>Zpracovat přerušující změny rozhraní API

V aplikaci Visual Studio 2022 jsou k dispozici zásadní [změny rozhraní API](breaking-api-list.md) , které mohou vyžadovat změny kódu v případě, že byly spuštěny v předchozích verzích. V tomto dokumentu najdete tipy, jak aktualizovat kód pro každou z nich.

Při úpravách kódu doporučujeme použít [podmíněnou kompilaci](#use-conditional-compilation-symbols) , aby váš kód mohl nadále podporovat předběžnou aplikaci visual Studio 2022 při přidávání podpory pro visual Studio 2022.

Když získáte vytváření rozšíření cílené na Visual Studio 2022, pokračujte v [testování](#test-your-extension).

## <a name="use-conditional-compilation-symbols"></a>Použít symboly podmíněné kompilace

Pokud chcete použít stejný zdrojový kód, dokonce i stejný soubor, pro Visual Studio 2022 a starší verze, může být nutné použít podmíněnou kompilaci, aby bylo možné rozvětvit kód pro přizpůsobení k zásadním změnám. Podmíněná kompilace je funkce jazyků C#, Visual Basic a C++, které lze použít ke sdílení většiny kódu a současnému přijetí odlišných rozhraní API na určitých místech.

Další informace o použití direktiv preprocesoru a symbolů podmíněné kompilace najdete v [direktivě preprocesoru #if](/dotnet/csharp/language-reference/preprocessor-directives#conditional-compilation)Microsoft docs.

Vaše projekty, které cílí na starší verze sady Visual Studio, budou potřebovat symbol podmíněné kompilace, který pak můžete použít k rozvětvení kódu pro použití různých rozhraní API. Můžete nastavit symbol podmíněné kompilace na stránce vlastností projektu, jak je znázorněno na následujícím obrázku:

![Nastavení symbolů podmíněné kompilace](media/update-visual-studio-extension/conditional-compilation-symbols.png)

Nezapomeňte nastavit symbol kompilace pro *všechny* konfigurace, protože ve výchozím nastavení se symbol, který zadáte, může vztahovat jenom na jednu konfiguraci.

### <a name="c-techniques"></a>Techniky jazyka C \#

Pak můžete použít tento symbol jako direktivu pre-Processor ( `#if` ), jak je znázorněno v následujícím kódu. Svůj kód pak můžete rozvětvit a řešit zásadní změnu mezi různými verzemi sady Visual Studio.

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
#if Visual Studio 2019
    shell.LoadUILibrary(myGuid, myFlags, out uint ptrLib);
#else
    shell.LoadUILibrary(myGuid, myFlags, out IntPtr ptrLib);
#endif
```

V některých případech můžete jednoduše použít, `var` Chcete-li se vyhnout pojmenovávání typu, čímž se vyhnete nutnosti použití `#if` oblastí. Výše uvedený fragment kódu lze také zapsat jako:

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
    shell.LoadUILibrary(myGuid, myFlags, out var ptrLib);
```

Při použití `#if` syntaxe si všimněte, jak můžete pomocí rozevíracího seznamu kontext služby jazyka v dokumentu, který vidíte níže, změnit zvýrazňování syntaxe a další pomoc, kterou nabízí služba jazyka, zaměřit pozornost na jednu cílovou verzi sady Visual Studio pro naše rozšíření vs. Další.

![Podmíněná kompilace ve sdíleném projektu](media/update-visual-studio-extension/conditional-compilation-if-region.png)

### <a name="xaml-sharing-techniques"></a>Techniky sdílení XAML

Jazyk XAML nemá žádný preprocesor, který umožňuje přizpůsobení obsahu na základě symbolů preprocesoru. Kopírování a údržba dvou stránek XAML, kde se jejich obsah musí lišit mezi Visual Studio 2022 a staršími verzemi může být vyžadováno.

V některých případech však odkaz na typ, který existuje v různých sestaveních v rámci sady Visual Studio 2022 a starších verzí, může být stále reprezentovatelné v jednom souboru XAML odebráním oboru názvů, který odkazuje na sestavení:

```diff
-xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
-Value="{DynamicResource {x:Static vsui:TreeViewColors.SelectedItemActiveBrushKey}}"
+Value="{DynamicResource TreeViewColors.SelectedItemActiveBrushKey}"
```

## <a name="test-your-extension"></a>Otestování rozšíření

Chcete-li otestovat rozšíření, které se zaměřuje na Visual Studio 2022, bude nutné mít nainstalovanou aplikaci Visual Studio 2022 Preview.
Ve verzích sady Visual Studio nebudete moct spouštět 64 rozšíření verze Visual Studio 2022 Preview.

Můžete použít Visual Studio 2022 Preview k sestavení a otestování rozšíření bez ohledu na to, jestli jsou určené pro Visual Studio 2022 nebo starší verze. Při spuštění projektu VSIX ze sady Visual Studio 2022 se spustí experimentální instance sady Visual Studio.

Důrazně doporučujeme, abyste provedli testování v každé verzi sady Visual Studio, pro kterou chcete rozšíření podporovat.

Teď jste připraveni [publikovat své rozšíření](#publish-your-extension).

## <a name="publish-your-extension"></a>Publikování rozšíření

Skvělé, takže jste do svého rozšíření přidali cíl sady Visual Studio 2022 a otestovali jste ho. Teď jste připraveni publikovat rozšíření pro celý svět do obdivujete.

### <a name="visual-studio-marketplace"></a>Visual Studio Marketplace

Publikování rozšíření na [Visual Studio Marketplace](https://marketplace.visualstudio.com/) je skvělým způsobem, jak získat nové uživatele, aby našli a nainstalovali vaše rozšíření. Bez ohledu na to, jestli vaše rozšíření cílí jenom na verzi sady Visual Studio 2022 nebo na starší verze VS, je na webu Marketplace.

V budoucnu vám web Marketplace umožní nahrávat více VSIX do jednoho seznamu Marketplace, což vám umožní nahrát na web Visual Studio 2022-cílené VSIX a předběžnou Visual Studio 2022 VSIX. Při použití Správce rozšíření VS budou uživatelé automaticky dostávat správný VSIX pro nainstalované verze VS.

Pro verze Preview sady Visual Studio 2022 bude Marketplace podporovat pouze jeden soubor VSIX na jeden seznam na webu Marketplace. I když je Visual Studio 2022 ve verzi Preview, doporučujeme mít pro vaše rozšíření samostatný seznam Marketplace pro Visual Studio 2022. Tímto způsobem můžete podle potřeby iterovat rozšíření aplikace Visual Studio 2022, aniž by to ovlivnilo vaše zákazníky v dřívějších verzích sady Visual Studio. Můžete také označit rozšíření jako "Preview" a nastavit tak očekávanou hodnotu, která bude pravděpodobně méně spolehlivá, i když je zdrojem tohoto unreliability sada Visual Studio 2022, než vaše hlavní rozšíření.

### <a name="custom-installer"></a>Vlastní instalační program

Pokud vytváříte soubor MSI/EXE pro instalaci rozšíření a zadáte vsixinstaller.exe pro instalaci (součást) rozšíření, zjistěte, že instalační program VSIX v aplikaci Visual Studio 2022 byl aktualizován. Pro instalaci rozšíření do sady Visual Studio 2022 bude vývojář potřebovat použít verzi instalátoru VSIX, která se dodává se sadou Visual Studio 2022. Instalační program VSIX v aplikaci Visual Studio 2022 nainstaluje také příslušná rozšíření, která cílí na předchozí verze sady Visual Studio, které jsou nainstalovány souběžně se sadou Visual Studio 2022 ve stejném počítači.

### <a name="network-share"></a>Sdílená síťová složka

Rozšíření můžete sdílet přes síť LAN nebo jakýmkoli jiným způsobem. Pokud cílíte na Visual Studio 2022 a pre-Visual Studio 2022, budete muset sdílet více VSIX jednotlivě a dát jim názvy souborů (nebo je umístit do jedinečných složek), které uživatelům pomůžou zjistit, který VSIX se má nainstalovat, na základě nainstalované verze sady Visual Studio.

### <a name="other-considerations"></a>Další důležité informace

#### <a name="dependencies"></a>Závislosti

Pokud váš VSIX určí další VSIX jako závislost prostřednictvím `<dependency>` elementu, každý ODKAZOVANÝ VSIX musí nainstalovat ve stejných cílech a architekturách produktu jako VSIX. Pokud závislý VSIX nepodporuje cílovou instalaci sady Visual Studio, váš VSIX se nezdaří. Je v pořádku, aby závislý VSIX podporoval více cílů a architektur než na vašem Toto omezení znamená, že přístup k nasazení a distribuci VSIX se závislostmi by měl zrcadlit na svých závislých objektech.

## <a name="q--a"></a>Otázky a odpovědi

**Otázka**: Moje rozšíření nevyžaduje žádné změny spolupráce, protože poskytuje jenom data (například šablony), můžu vytvořit jedno rozšíření, které zahrnuje i Visual Studio 2022?

Odpověď **: Ano**!  Další informace najdete v tématu [rozšíření bez spuštěného kódu](#extensions-without-running-code) .

**Otázka**: závislost NuGet je součástí starých sestavení vzájemné spolupráce a způsobuje konflikt tříd.

**O**: přidejte následující řádek do souboru. csproj, aby nedocházelo k duplicitním sestavením:

```xml
    <PackageReference Include="<Name of offending assembly>" ExcludeAssets="compile" PrivateAssets="all" />
```

Tím zabráníte odkazům na balíčky v importu staré verze sestavení z jiných závislostí.

**Otázka**: moje příkazy a klávesové zkratky nefungují v aplikaci Visual Studio po přepnutí zdrojových souborů do sdíleného projektu.

Odpověď: [Krok 2,4](samples.md#step-2---refactor-source-code-into-a-shared-project) ukázky Optimalizátoru imagí ukazuje, jak přidat soubory vsct jako propojené položky, aby byly zkompilovány do souboru vsct.

## <a name="next-steps"></a>Další kroky

Postupujte podle podrobného příkladu [ImageOptimizer](samples.md)s odkazy na projekt a změny kódu pro jednotlivé kroky.
