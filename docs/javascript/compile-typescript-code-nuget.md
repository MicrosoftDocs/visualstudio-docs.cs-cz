---
title: Kompilování a sestavení kódu TypeScript pomocí NuGetu
description: Naučte se kompilovat a sestavovat TypeScript v aplikaci Visual Studio.
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: ac917248915129b8d93dc776ac7d35a2ed227069
ms.sourcegitcommit: b8ec700fc4c14c68c6ce280f29c19870261990d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2020
ms.locfileid: "87454595"
---
# <a name="compile-typescript-code-aspnet-core"></a>Kompilovat kód TypeScriptu (ASP.NET Core)

Do svých projektů můžete přidat podporu TypeScript pomocí TypeScript SDK, která je ve výchozím nastavení dostupná v instalačním programu sady Visual Studio nebo pomocí balíčku NuGet. Pro projekty vyvinuté v aplikaci Visual Studio 2019 doporučujeme, abyste používali NuGet pro TypeScript pro větší přenositelnost napříč různými platformami a prostředími.

Pro ASP.NET Core projekty je jedním z běžných využití balíčku NuGet kompilace TypeScript pomocí .NET Core CLI. Pokud soubor projektu neupravíte ručně pro import cílů sestavení z instalace TypeScript SDK, balíček NuGet je jediným způsobem, jak povolit kompilaci TypeScriptu pomocí .NET Core CLI příkazů, jako jsou `dotnet build` a `dotnet publish` . Pro [integraci MSBuild](https://www.staging-typescript.org/docs/handbook/compiler-options-in-msbuild.html) s ASP.NET Core a TypeScript si taky v balíčku npm vyberte balíček NuGet.

## <a name="add-typescript-support-with-nuget"></a>Přidání podpory TypeScript pomocí NuGetu

[Balíček NuGet pro TypeScript](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) přidává podporu TypeScript. Při instalaci balíčku NuGet pro TypeScript 3,2 nebo vyšší do projektu se v editoru načte odpovídající verze jazykové služby TypeScript.

Pokud je nainstalována aplikace Visual Studio, bude sada Visual Studio automaticky vyzvednuta node.exe, na kterou se zabalí. Pokud nemáte nainstalované Node.js, doporučujeme nainstalovat verzi LTS z webu [Node.js](https://nodejs.org/en/download/) .

1. Otevřete projekt ASP.NET Core v aplikaci Visual Studio.

1. V Průzkumník řešení (pravé podokno). Klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Spravovat balíčky NuGet**. Na kartě **Procházet** vyhledejte **Microsoft. TypeScript. MSBuild**a kliknutím na **nainstalovat** napravo nainstalujte balíček.

   ![Přidat balíček NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Sada Visual Studio přidá balíček NuGet pod uzel **závislosti** v Průzkumník řešení. Následující odkaz na balíček se přidá do souboru *. csproj.

   ```xml
   <PackageReference Include="Microsoft.TypeScript.MSBuild" Version="3.9.7">
      <PrivateAssets>all</PrivateAssets>
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
   </PackageReference>
   ```

1. Klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **přidat > novou položku**. Zvolte **konfigurační soubor JSON pro TypeScript**a pak klikněte na **Přidat**.

   Visual Studio přidá *tsconfig.js* do souboru do kořenového adresáře projektu. Tento soubor můžete použít ke [konfiguraci možností](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) pro kompilátor TypeScript.

1. Otevřete *tsconfig.jsna* a aktualizujte, abyste nastavili požadované možnosti kompilátoru.

   Následuje příklad jednoduchého *tsconfig.js* souboru.

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "wwwroot/js"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   V tomto příkladu:
   - *Zahrnout* instruuje kompilátor, kde se mají najít soubory TypeScript (*. TS).
   - možnost *outDir* určuje výstupní složku pro soubory prostého JavaScriptu, které jsou přepsány kompilátorem TypeScript.
   - možnost *sourceMap* označuje, zda kompilátor generuje soubory *sourceMap* .

   Předchozí konfigurace poskytuje jenom základní úvodní informace ke konfiguraci TypeScript. Informace o dalších možnostech najdete v tématu [tsconfig.js](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

### <a name="build-the-application"></a>Sestavení aplikace

1. Přidejte do projektu soubory TypeScript (*. TS*) nebo TypeScript JSX (*. TSX*) a pak přidejte kód TypeScript. Pro jednoduchý příklad TypeScript použijte následující:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. Pokud používáte starší projekt ve stylu mimo sadu SDK, postupujte podle pokynů v tématu [odebrání výchozích importů](#remove-default-imports) před sestavením.

1. Vyberte **sestavení řešení sestavení >**.

   I když se aplikace při spuštění automaticky vytvoří, chceme se podívat na něco, co se děje během procesu sestavení:

   Pokud jste vygenerovali zdrojová mapování, otevřete složku zadanou v možnosti *outDir* a vygenerované soubory *. js najdete spolu s generovanými soubory * JS. map.

   Zdrojové soubory mapování jsou vyžadovány pro ladění.

1. Pokud chcete kompilovat při každém uložení projektu, použijte možnost *compileOnSave* ve *. tsconfig.

   ```json
   ```{
      "compileOnSave":  true,
      "compilerOptions": {
      }
   }
   ```

Příklad použití Gulp s spouštěčem úloh k sestavení vaší aplikace naleznete v tématu [ASP.NET Core a TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html).

Pokud narazíte na problémy, kde aplikace Visual Studio používá verzi Node.js nebo nástroj třetí strany, který se liší od očekávané verze, bude pravděpodobně nutné nastavit cestu pro aplikaci Visual Studio, která se má použít. Vyberte **Tools**  >  **Možnosti**nástrojů. V části **projekty a řešení**vyberte **Web Správa balíčků**  >  **externí webové nástroje**.

### <a name="nuget-package-structure-details"></a>Podrobnosti o struktuře balíčku NuGet

`Microsoft.TypeScript.MSBuild.nupkg`obsahuje dvě hlavní složky:

- Složka *sestavení*

    V této složce se nacházejí dva soubory.
    Oba jsou vstupní body – pro hlavní cílový soubor TypeScript a soubor props (v uvedeném pořadí).

    1. *Microsoft. TypeScript. MSBuild. targets*

        Tento soubor nastaví proměnné, které určují platformu za běhu, jako je například cesta k *TypeScript.Tasks.dll*, před importem *Microsoft. TypeScript. targets* ze složky *Tools* .

    2. *Microsoft. TypeScript. MSBuild. props*

        Tento soubor importuje soubory *Microsoft. TypeScript. default. props* ze složky *Tools* a nastaví vlastnosti indikující, že sestavení bylo iniciováno prostřednictvím NuGet.

- Složka *nástroje*

    Verze balíčků starší než 2,3 obsahují pouze složku TSC. *Microsoft. TypeScript. targets* a *TypeScript.Tasks.dll* jsou umístěné na kořenové úrovni.

    V balíčcích verze 2,3 a novější obsahuje kořenová úroveň `Microsoft.TypeScript.targets` a `Microsoft.TypeScript.Default.props` . Další podrobnosti o těchto souborech najdete v tématu [Konfigurace nástroje MSBuild](https://www.typescriptlang.org/docs/handbook/compiler-options-in-msbuild.html).

    Kromě toho složka obsahuje tři podsložky:

    1. *net45*

        Tato složka obsahuje `TypeScript.Tasks.dll` a další knihovny DLL, na kterých závisí.
        Při sestavování projektu na platformě Windows používá nástroj MSBuild knihovny DLL z této složky.

    2. *netstandard 1.3*

        Tato složka obsahuje jinou verzi nástroje `TypeScript.Tasks.dll` , která se používá při sestavování projektů v počítači s jiným systémem než Windows.

    3. *Čítač*

        Tato složka obsahuje `tsc.js` `tsserver.js` a všechny soubory závislosti, které jsou nutné ke spuštění jako skripty uzlu.

        > [!NOTE]
        > Pokud je nainstalována sada Visual Studio, bude automaticky vyzvednuta *node.exe* , na kterou se bude nacházet. V opačném případě musí být na počítači nainstalovaná Node.js.

        Verze před 3,1 obsahovaly `tsc.exe` spustitelný soubor pro spuštění kompilace. Ve verzi 3,1 se tato odebrání odebrala místo použití `node.exe` .

### <a name="remove-default-imports"></a>Odebrat výchozí importy

Ve starších ASP.NET Core projektech, které používají [formát, který není ve stylu sady SDK](https://docs.microsoft.com/nuget/resources/check-project-format), bude pravděpodobně nutné odebrat některé prvky souboru projektu.

Pokud používáte balíček NuGet pro podporu nástroje MSBuild pro projekt, soubor projektu nesmí importovat `Microsoft.TypeScript.Default.props` nebo `Microsoft.TypeScript.targets` . Soubory jsou importovány balíčkem NuGet, takže včetně těchto souborů mohou způsobit nezamýšlené chování.

1. Klikněte pravým tlačítkem na projekt a vyberte **Uvolnit projekt**.

1. Klikněte pravým tlačítkem myši na projekt a vyberte možnost **Upravit \<*project file name*\> **.

   Otevře se soubor projektu.

1. Odeberte odkazy na `Microsoft.TypeScript.Default.props` a `Microsoft.TypeScript.targets` .

   Importy, které mají být odebrány, vypadají podobně jako následující:

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```
