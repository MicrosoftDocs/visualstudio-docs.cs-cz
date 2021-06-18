---
title: Aktualizace Visual Studio rozšíření
description: Zjistěte, jak aktualizovat vaše Visual Studio tak, aby fungovalo s Visual Studio 2022.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 514c9654a741e4e1e565f0cb2becdbe3157fab0c
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308737"
---
# <a name="update-a-visual-studio-extension-for-visual-studio-2022"></a>Aktualizace rozšíření Visual Studio pro Visual Studio 2022

Podle tohoto průvodce můžete rozšíření aktualizovat tak, aby fungovalo Visual Studio 2022 Preview. Visual Studio 2022 Preview je 64bitová aplikace a přináší v sadě VS SDK několik rozbíjení změn. Tato příručka vás provede kroky potřebnými k tomu, aby vaše rozšíření pracovalo s aktuální verzí Preview verze Visual Studio 2022, aby vaše rozšíření bylo připravené k instalaci před tím, než Visual Studio 2022 dosáhne ga.

## <a name="installing"></a>Instalace

Nainstalujte Visual Studio 2022 Preview [ze souborů Visual Studio 2022 Preview ke stažení.](https://visualstudio.microsoft.com/vs/preview/vs2022)

### <a name="extensions-written-in-a-net-language"></a>Rozšíření napsaná v jazyce .NET

Sada VS SDK zaměřená Visual Studio 2022 pro spravovaná rozšíření je *výhradně* na NuGetu:

- Balíček [metadat Microsoft.VisualStudio.Sdk](https://www.nuget.org/packages/Microsoft.VisualStudio.Sdk/) (verze 17.x) přináší většinu nebo všechna referenční sestavení, která budete potřebovat.
- Na [balíček Microsoft.VSSDK.BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools/) (verze 17.x) by se měl odkazovat z projektu VSIX, aby mohl sestavit VSIX kompatibilní Visual Studio 2022.

Rozšíření *musí* být kompilována s platformou "Libovolný procesor" nebo "x64". Platforma x86 není kompatibilní s 64bitovým Visual Studio 2022.

### <a name="extensions-written-in-c"></a>Rozšíření napsaná v jazyce C++

Sada VS SDK pro rozšíření zkompilovaná pomocí C++ je jako obvykle dostupná s nainstalovanou Visual Studio SDK.

Rozšíření *musí být* kompilována speciálně proti sadě SDK Visual Studio 2022 a pro amd64.

### <a name="update-your-extension-to-visual-studio-2022"></a>Aktualizace rozšíření na Visual Studio 2022

#### <a name="extensions-with-running-code"></a>Rozšíření se spuštěným kódem

Rozšíření se spuštěným *kódem musí* být kompilována speciálně Visual Studio 2022. Visual Studio 2022 nenačte žádné rozšíření, které není určené Visual Studio 2022.

Naučte se migrovat rozšíření před Visual Studio 2022 do Visual Studio 2022:

1. [Modernizujte své projekty.](#modernize-your-vsix-project)
1. [Refaktorujte zdrojový kód do sdíleného projektu,](#use-shared-projects-for-multi-targeting) abyste umožnili cílení na Visual Studio 2022 a starší verze.
1. Přidejte Visual Studio VSIX cílený na [2022 a](#add-a-visual-studio-2022-target)naši tabulku přemapování balíčků a [sestavení](migrated-assemblies.md).
1. [Provedení potřebných úprav kódu](#handle-breaking-api-changes).
1. [Testování rozšíření Visual Studio 2022](#test-your-extension)
1. [Publikování rozšíření Visual Studio 2022](#publish-your-extension).

#### <a name="extensions-without-running-code"></a>Rozšíření bez spuštění kódu

Rozšíření, která neobsahují žádný spuštěný kód (například šablony  projektů a položek), nemusí postupovat podle výše uvedených kroků, včetně vytvoření dvou různých souborů VSIX.

Místo toho by se měl upravit jeden soubor VSIX tak, aby jeho soubor deklaroval dva cíle `source.extension.vsixmanifest` instalace, například:

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

Kroky v tomto článku o používání sdílených projektů a více souborů VSIX můžete přeskočit. Můžete pokračovat v [testování](#test-your-extension).

> [!NOTE]
> Pokud pomocí verze  Visual Studio 2022 Preview Visual Studio chcete (také) cílit na Visual Studio 2019 nebo starší verzi, podívejte se na tohoto [průvodce.](target-previous-versions.md)

### <a name="msbuild-tasks"></a>úlohy nástroje MSBuild

Pokud budete vytvářet úlohy nástroje MSBuild, uvědomte si, že v nástroji Visual Studio 2022 je mnohem pravděpodobnější, že budou načteny v 64bitovém MSBuild.exe procesu. Pokud vaše úloha vyžaduje spuštění 32bitového procesu, přečtěte si tuto dokumentaci nástroje MSBuild a ujistěte se, že nástroj [MSBuild](../../msbuild/how-to-configure-targets-and-tasks.md#usingtask-attributes-and-task-parameters) ví, že má načíst úlohu v 32bitovém procesu.

## <a name="modernize-your-vsix-project"></a>Modernizace projektu VSIX

Před přidáním Visual Studio 2022 do rozšíření důrazně doporučujeme, abyste si před dalším rozšířením vyčistěte a modernizovali stávající projekt, včetně následujících:

1. [Migrace z packages.config na `PackageReference` ](/nuget/consume-packages/migrate-packages-config-to-package-reference).

1. Nahraďte všechny přímé odkazy na sestavení sady VS SDK položkami PackageReference.

   ```diff
   -<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   +<PackageReference Include="Microsoft.VisualStudio.OLE.Interop" Version="..." />
   ```

   > [!TIP]
   > Mnoho odkazů *na sestavení můžete* nahradit pouze jedním PackageReference k našemu metabalíku: 
   >
   >```diff
   >-<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop.8.0" />
   >+<PackageReference Include="Microsoft.VisualStudio.Sdk" >Version="..." />
   >```

   Nezapomeňte vybrat verze balíčků, které odpovídají minimální verzi Visual Studio cílíte.

   Některá sestavení, která nejsou jedinečná pro sadu VS SDK (například Newtonsoft.Json.dll), byla možná zjistitelná pomocí jednoduchého odkazu před Visual Studio 2022, ale v nástroji Visual Studio 2022 vyžaduje místo toho odkaz na balíček, protože v nástroji Visual Studio 2022 odebereme některé adresáře modulu runtime Visual Studio a adresáře SADY SDK z výchozí cesty hledání sestavení `<Reference Include="Newtonsoft.Json" />` MSBuild.

   Při přechodu z přímých odkazů na sestavení na odkazy na balíčky NuGet můžete vzít další odkazy na sestavení a balíčky analyzátorů, protože NuGet automaticky instaluje tranzitivní uzavření závislostí. Obecně je to v pořádku, ale může to mít za následek další upozornění, která se během sestavení můžou zobrazit jako označená. Propracujte si tato upozornění a vyřešte co nejvíce a zvažte potlačení těchto upozornění, která nemůžete vyřešit pomocí oblastí v `#pragma warning disable <id>` kódu.

## <a name="use-shared-projects-for-multi-targeting"></a>Použití sdílených projektů pro cílení na více verzí

[Sdílené projekty](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) jsou typ projektu, který byl představen v Visual Studio 2015. Sdílené projekty v Visual Studio umožňují sdílet soubory zdrojového kódu mezi více projekty a sestavovat odlišně pomocí symbolů podmíněné kompilace a jedinečných sad odkazů.

Vzhledem k tomu, že Visual Studio 2022 vyžaduje odlišnou sadu referenčních sestavení ze všech předchozích verzí sady VS, je naším pokynem používat sdílené projekty k tomu, aby bylo vaše rozšíření pohodlně cíleno na před Visual Studio 2022 a Visual Studio 2022 (a novější verze), což vám umožní sdílet kód, ale odlišné odkazy.

V kontextu rozšíření Visual Studio můžete mít jeden projekt VSIX pro Visual Studio 2022 a novější a jeden projekt VSIX pro Visual Studio 2019 a starší. Každý z těchto projektů by obsahoval pouze a odkaz na balíček na `source.extension.vsixmanifest` sadu SDK 16.x nebo sadu SDK 17.x. Tyto projekty VSIX by také měly sdílený odkaz na projekt na nový sdílený projekt, který bude hostovat veškerý váš zdrojový kód, který lze sdílet mezi dvěma verzemi VS.

Jako výchozí bod pro tento dokument budeme předpokládat, že už máte projekt VSIX, který cílí na Visual Studio 2019 a že chcete, aby vaše rozšíření fungovalo na Visual Studio 2022.

Všechny tyto kroky můžete dokončit v Visual Studio 2019.

1. Pokud jste to ještě neudělali, [modernizujte své projekty,](#modernize-your-vsix-project) abyste usnadnili kroky v pozdější části tohoto procesu aktualizace.

1. Přidejte do svého řešení nový sdílený projekt pro každý existující projekt, který odkazuje na sadu VS SDK.
   ![Příkaz Add New Project (Přidat ](media/update-visual-studio-extension/add-new-project.png)
    ![ nový projekt) New project template (Nová šablona projektu)](media/update-visual-studio-extension/new-shared-project-template.png)

1. Přidejte odkaz z každého projektu odkazujícího na sadu VS SDK do sdíleného protějšku projektu.
   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Přidání odkazu na sdílený projekt" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Přesuňte veškerý zdrojový kód (včetně .cs, .resx) z každého projektu odkazujícího na sadu VS SDK do sdíleného protějšku projektu.
`source.extension.vsixmanifest`Ponechte soubor v projektu VSIX.
   ![Sdílený projekt obsahuje všechny zdrojové soubory.](media/update-visual-studio-extension/source-files-in-shared-project.png)

1. Soubory metadat (poznámky k verzi, licence, ikony atd.) a soubory VSCT by se měly přesunout do sdíleného adresáře a přidat jako propojené soubory do projektu VSIX.
   ![Přidání metadat a souborů VSCT jako propojených souborů](media/update-visual-studio-extension/add-linked-items-to-vsix.png)
    - Pro soubory metadat nastavte BuildAction na a `Content` include v souboru VSIX nastavte na `true` .

      ![Zahrnutí souborů metadat v souboru VSIX](./media/update-visual-studio-extension/include-metadata-files-in-vsix.png)
    - V případě souborů VSCT nastavte BuildAction na a `VSCTCompile` nezahrnujte do VSIX.
      Visual Studio si může stěžovat, že toto nastavení není podporováno, ale můžete ručně změnit akci sestavení uvolněním projektu a změnou na `Content``VSCTCompile`

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

1. Sestavte své projekty, abyste si potvrdili, že jste nezavřou žádné nové chyby.

Váš projekt je teď připravený k přidání Visual Studio 2022.

## <a name="add-a-visual-studio-2022-target"></a>Přidání cíle Visual Studio 2022

V tomto dokumentu se předpokládá, že jste dokončili kroky pro faktor [Visual Studio rozšíření se sdílenými projekty](#use-shared-projects-for-multi-targeting).

Pokračujte přidáním podpory Visual Studio 2022 do rozšíření pomocí těchto kroků, které můžete dokončit pomocí Visual Studio 2019:

1. Přidejte do svého řešení nový projekt VSIX. To bude projekt, který cílí na Visual Studio 2022. Odeberte zdrojový kód, který jste dodáli se šablonou, ale *soubor nechte `source.extension.vsixmanifest` .*

1. V novém projektu VSIX přidejte odkaz na sdílený projekt do stejného sdíleného projektu, na který Visual Studio odkazy VSIX cílené na verzi 2019.

   ![Řešení s jedním sdíleným projektem a dvěma projekty VSIX](media/update-visual-studio-extension/shared-project-with-two-heads.png)

1. Ověřte, že se nový projekt VSIX správně sestaví. Možná budete muset přidat odkazy tak, aby odpovídaly původnímu projektu VSIX, a vyřešit případné chyby kompilátoru.

1. V případě spravovaných rozšíření VS aktualizujte odkazy na balíčky z verze 16.x (nebo starší) na verze balíčku 17.x v souboru projektu cíleného na Visual Studio 2022 pomocí balíčku NuGet Správce balíčků nebo přímo upravujte soubor projektu:

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    ```

   Použijete verze, které jsou ve skutečnosti dostupné z nuget.org. Ty, které jsme použili dříve, jsou jenom pro demonstrační účely.

   V mnoha případech se ID balíčků změnila. Seznam změn v 2022 najdete v tabulce mapování balíčků a sestavení Visual Studio 2022. [](migrated-assemblies.md)

   Rozšíření napsaná v jazyce C++ zatím nemají k dispozici sadu SDK pro kompilaci.

1. Pro projekty C++ musí být zkompilovány pro amd64. U spravovaných rozšíření zvažte změnu projektu z sestavování pro jakýkoli procesor na cílení , aby odrážel, že v Visual Studio 2022 se vaše rozšíření vždy načte v `x64` 64bitovém procesu. `Any CPU` je také v pořádku, ale může vyvolat upozornění, pokud odkazujete na jakékoli nativní binární soubory pouze x64.

   Všechny závislosti, které vaše rozšíření může mít na nativním modulu, bude třeba aktualizovat z image x86 na image amd64.

1. Upravte soubor `source.extension.vsixmanifest` tak, aby odrážel cílení Visual Studio 2022. Nastavte `<InstallationTarget>` značku tak, aby odrážela Visual Studio 2022 a označte datovou část amd64:

   ```xml
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
   ```

   V Visual Studio 2019 návrhář pro tento soubor nový prvek nezpřístupňuje, takže tuto změnu bude potřeba provést v editoru XML, ke kterému máte přístup prostřednictvím příkazu Otevřít v souboru `ProductArchitecture` **Průzkumník řešení**. 

   Tento `ProductArchitecture` prvek je kritický. Visual Studio 2022 bez *něj* vaše rozšíření nenainstaluje.

   | Prvek | Hodnota | Popis |
   | - | - | - |
   | Architektura produktu | X86, AMD64 | Platformy podporované tímto souborem VSIX. Rozlišují se malá a velká písmena. Jedna platforma na prvek a jeden prvek na InstallTarget. U verzí produktů menších než 17.0 je výchozí hodnota x86 a je možné ji vynechat.  U produktů verze 17.0 a vyšší je tento prvek povinný a neexistuje žádná výchozí hodnota. Pro Visual Studio 2022 je jediným platným obsahem pro tento prvek amd64. |

1. V souboru source.extension.vsixmanifest proveďte všechny další úpravy tak, aby odpovídaly tomu, který cílí na Visual Studio 2019 (pokud je nějaký). Je velmi důležité, aby ID souboru VSIX v elementu manifestu bylo pro obě `Identity` rozšíření stejné.

V tuto chvíli máte rozšíření VSIX Visual Studio 2022. Měli byste sestavit projekt VSIX Visual Studio 2022 a projít všechny konce sestavení, které [se zobrazí.](#handle-breaking-api-changes) Pokud nemáte v projektu VSIX cíleného na Visual Studio 2022 přerušení sestavení, blahopřejeme: jste připraveni k testování.

## <a name="handle-breaking-api-changes"></a>Zpracování změn rozhraní API pro přerušení

V systému Visual Studio 2022 došlo ke změnám rozhraní [API,](breaking-api-list.md) které mohou vyžadovat změny kódu od spuštění v předchozích verzích. V tomto dokumentu najdete tipy, jak aktualizovat kód pro každý z nich.

Při přizpůsobování kódu doporučujeme použít [](#use-conditional-compilation-symbols) podmíněnou kompilaci, aby váš kód mohl dál podporovat před Visual Studio 2022 a současně přidal podporu pro Visual Studio 2022.

Až budete mít k Visual Studio rozšíření cílené na rok 2022, pokračujte [testováním](#test-your-extension).

## <a name="use-conditional-compilation-symbols"></a>Použití symbolů podmíněné kompilace

Pokud chcete použít stejný zdrojový kód, i stejný soubor, pro Visual Studio 2022 a starší verze, možná budete muset použít podmíněnou kompilaci, abyste si mohli vytvořit fork kódu, abyste se přizpůsobili změnám, které mají narušovat zabezpečení. Podmíněná kompilace je funkce jazyků C#, Visual Basic a C++, kterou je možné použít ke sdílení většiny kódu při zachování divergentně používaných rozhraní API na konkrétních místech.

Další informace o použití direktiv preprocesoru a symbolů podmíněné kompilace najdete v dokumentu Microsoft docs [#if direktivě preprocesoru](/dotnet/csharp/language-reference/preprocessor-directives#conditional-compilation).

Vaše projekty, které cílí na starší Visual Studio verzí, budou potřebovat symbol podmíněné kompilace, který lze použít k forku kódu pro použití různých rozhraní API. Symbol podmíněné kompilace můžete nastavit na stránce vlastností projektu, jak je znázorněno na následujícím obrázku:

![Nastavení symbolů podmíněné kompilace](media/update-visual-studio-extension/conditional-compilation-symbols.png)

Nezapomeňte nastavit symbol kompilace pro *všechny* konfigurace, protože ve výchozím nastavení se symbol, který zadáte, může vztahovat pouze na jednu konfiguraci.

### <a name="c-techniques"></a>Techniky jazyka C \#

Tento symbol pak můžete použít jako direktivu před procesorem ( `#if` ), jak je znázorněno v následujícím kódu. Pak můžete vytvořit fork kódu, abyste se vypořádali se změnou, která narušuje chyby mezi různými Visual Studio verzemi.

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

V některých případech můžete jednoduše použít , abyste se vyhnuli pojmenování typu, a tím se `var` vyhnout `#if` použití oblastí. Výše uvedený fragment kódu lze také napsat takto:

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
    shell.LoadUILibrary(myGuid, myFlags, out var ptrLib);
```

Při použití syntaxe si všimněte, jak můžete pomocí rozevíracího seznamu kontextu služby jazyka v níže zobrazeném dokumentu změnit zvýraznění syntaxe Visual Studio druhou pomoct službě jazyka zaměřit pozornost na jednu cílovou verzi rozšíření `#if` vs. jinou.

![Podmíněná kompilace ve sdíleném projektu](media/update-visual-studio-extension/conditional-compilation-if-region.png)

### <a name="xaml-sharing-techniques"></a>Techniky sdílení XAML

XAML nemá žádný preprocesor umožňující přizpůsobení obsahu na základě symbolů preprocesoru. Kopírování a údržba dvou stránek XAML, kde se jejich obsah musí v různých verzích Visual Studio 2022 a starších verzích lišit.

V některých případech však může být odkaz na typ, který existuje v různých sestaveních v rámci Visual Studio 2022 a starších verzích, stále reprezentovatelný v jednom souboru XAML odebráním oboru názvů, který odkazuje na sestavení:

```diff
-xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
-Value="{DynamicResource {x:Static vsui:TreeViewColors.SelectedItemActiveBrushKey}}"
+Value="{DynamicResource TreeViewColors.SelectedItemActiveBrushKey}"
```

## <a name="test-your-extension"></a>Otestování rozšíření

Pokud chcete otestovat rozšíření, které cílí na Visual Studio 2022, musíte mít nainstalovanou Visual Studio 2022 Preview.
Před verzí 2022 Preview nebudete moct spouštět 64bitová rozšíření Visual Studio verzi Visual Studio 2022.

Pomocí verze Visual Studio 2022 Preview můžete sestavit a otestovat rozšíření bez ohledu na to, jestli cílí na Visual Studio 2022 nebo starší verzi. Při spuštění projektu VSIX z Visual Studio 2022 se spustí experimentální instance Visual Studio systému.

Důrazně doporučujeme testovat s každou verzí Visual Studio, kterou máte v úmyslu rozšíření podporovat.

Teď jste připraveni k [publikování rozšíření](#publish-your-extension).

## <a name="publish-your-extension"></a>Publikování rozšíření

Skvělé, takže jste do rozšíření přidali cíl Visual Studio 2022 a otestovali ho. Teď jste připravení publikovat rozšíření pro celý svět.

### <a name="visual-studio-marketplace"></a>Visual Studio Marketplace

Publikování rozšíření do Visual Studio Marketplace [je](https://marketplace.visualstudio.com/) skvělý způsob, jak nové uživatele přimět k vyhledání a instalaci vašeho rozšíření. Ať už vaše rozšíření cílí Visual Studio 2022, nebo cílí také na starší verze VS, marketplace vám může pomoci.

V budoucnu vám Marketplace umožní nahrát několik souborů VSIX jenom do jednoho výpisu z Marketplace, což vám umožní nahrát soubor VSIX cílený na Visual Studio 2022 a soubor VSIX před Visual Studio 2022. Uživatelé při použití správce rozšíření VS automaticky instalují správný soubor VSIX pro nainstalovanou verzi sady VS.

Ve verzích Preview Visual Studio 2022 bude Marketplace podporovat jenom jeden soubor VSIX pro jednotlivé výpisy na Marketplace. Přestože Visual Studio verze 2022 je ve verzi Preview, doporučujeme, abyste měli pro vaše rozšíření samostatný Visual Studio 2022 pouze na Marketplace. Tímto způsobem můžete iterovat rozšíření Visual Studio 2022 podle potřeby, aniž by to ovlivnilo vaše zákazníky v dřívějších verzích Visual Studio. Rozšíření můžete také označit jako "preview" a nastavit tak očekávání, že bude pravděpodobně méně spolehlivé, i když zdroj této nespolehlivosti je Visual Studio 2022 než hlavní rozšíření.

### <a name="custom-installer"></a>Vlastní instalační program

Pokud sestavíte soubor MSI/EXE pro instalaci rozšíření a vsixinstaller.exe k instalaci (součást) rozšíření, je třeba vědět, že instalační program VSIX v Visual Studio 2022 byl aktualizován. Vývojáři budou muset k instalaci rozšíření do Visual Studio 2022 použít verzi instalačního programu VSIX, která je součástí Visual Studio 2022. Instalační program VSIX v Visual Studio 2022 také nainstaluje příslušná rozšíření zaměřená na předchozí verze Visual Studio, která jsou nainstalovaná vedle Visual Studio 2022 na stejném počítači.

### <a name="network-share"></a>Sdílená síťová sdílená síť

Rozšíření můžete sdílet přes síť LAN nebo jiným způsobem. Pokud cílíte na Visual Studio 2022 a před Visual Studio 2022, budete muset sdílet více souborů VSIX jednotlivě a dát jim názvy souborů (nebo je umístit do jedinečných složek), které uživatelům pomůžou vědět, který soubor VSIX se má nainstalovat na základě Visual Studio které nainstalovali.

### <a name="other-considerations"></a>Další důležité informace

#### <a name="dependencies"></a>Závislosti

Pokud váš soubor VSIX specifikuje jiný soubor VSIX jako závislost prostřednictvím elementu , musí se každý odkazovaný soubor VSIX nainstalovat ve stejných cílech a architekturách produktů jako `<dependency>` váš VSIX. Pokud závislý soubor VSIX nepodporuje cílenou instalaci Visual Studio, váš soubor VSIX selže. Závislý soubor VSIX může podporovat více cílů a architektur než ten váš, ale ne méně. Toto omezení znamená, že přístup nasazení a distribuce VSIX se závislostmi by měl zrcadlit přístup jejich závislých objektů.

## <a name="q--a"></a>Otázky a odpovědi

**Otázka:** Moje rozšíření nevyžaduje žádné změny vzájemné spolupráce, protože pouze poskytuje data (například šablony), můžu vytvořit jedno rozšíření, které zahrnuje také Visual Studio 2022?

**A:** Ano!  Další [informace najdete v tématu Rozšíření bez](#extensions-without-running-code) spuštění kódu.

**Otázka:** Závislost NuGet přináší stará sestavení vzájemné spolupráce a způsobuje kolizující třídy.

**A**: Přidejte do souboru .csproj následující řádek, abyste se vyhnuli duplicitním sestavením:

```xml
    <PackageReference Include="<Name of offending assembly>" ExcludeAssets="compile" PrivateAssets="all" />
```

To zabrání odkazům na balíček v importu staré verze sestavení z jiných závislostí.

**Otázka:** Po přepnutí zdrojových souborů na sdílený projekt v Visual Studio příkazy a klávesové zkratky nefungují.

**A**: [Krok 2.4](samples.md#step-2---refactor-source-code-into-a-shared-project) ukázky Nástroje pro optimalizaci obrázků ukazuje, jak přidat soubory VSCT jako propojené položky, aby se zkompiloval do souboru VSCT.

## <a name="next-steps"></a>Další kroky

Postupujte podle podrobného příkladu [ImageOptimizer](samples.md)s odkazy na projekt a změny kódu pro každý krok.
