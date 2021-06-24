---
title: Ukázka ImageOptimizer pro aktualizaci rozšíření sady Visual Studio
description: Podle následujícího příkladu se dozvíte, jak aktualizovat rozšíření sady Visual Studio pro práci se sadou Visual Studio 2022 Preview.
ms.date: 06/08/2021
ms.topic: sample
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 12bbc159884c16ea89849e5c97a4b87292f7089d
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602224"
---
# <a name="imageoptimizer---update-a-visual-studio-extension-step-by-step"></a>ImageOptimizer – aktualizace rozšíření sady Visual Studio krok za krokem

[!INCLUDE [preview-note](../includes/preview-note.md)]

V této příručce se zobrazí všechny kroky nutné pro přidání podpory sady Visual Studio 2022 a podpora sady Visual Studio 2019 pomocí rozšíření pro optimalizaci imagí jako případovou studii.  
To je, že se jedná o důkladnou příručku s odkazy na potvrzení Git pro každý krok, ale tu můžete zdarma vidět tady: [https://github.com/madskristensen/ImageOptimizer/pull/46](https://github.com/madskristensen/ImageOptimizer/pull/46) .

Na konci tohoto průvodce máme také [Další ukázky](#other-samples) .

## <a name="step-1---modernize-the-project"></a>Krok 1 – modernizovat projektu

Viz [modernizovat projektu](update-visual-studio-extension.md#modernize-your-vsix-project).

[e052465 potvrzení Git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e052465f30e6bed37e6d76eac016047095e8e18b)

Nejdřív se projekt VSIX a testování částí zanárazníke do .NET 4.7.2 na stránce vlastnosti v projektech:

   ![Rozhraní Framework – segmentace verze](media/samples/framework-bump.png)

Nástroj pro optimalizaci imagí odkazoval na některé staré balíčky s vlastními 14. * a 15. *, ale nainstalujeme [ `Microsoft.VisualStudio.Sdk` balíček NuGet](https://www.nuget.org/packages/microsoft.visualstudio.sdk) , který konsoliduje všechny naše požadované odkazy.

```Diff
-  <ItemGroup>
-    <PackageReference Include="Madskristensen.VisualStudio.SDK">
-      <Version>14.0.0-beta4</Version>
-    </PackageReference>
-    <PackageReference Include="Microsoft.VSSDK.BuildTools">
-      <Version>15.8.3247</Version>
-      <IncludeAssets>runtime; build; native; contentfiles; analyzers</IncludeAssets>
-      <PrivateAssets>all</PrivateAssets>
-    </PackageReference>
-  </ItemGroup>

+  <ItemGroup>
+    <PackageReference Include="Microsoft.VisualStudio.SDK">
+      <Version>16.9.31025.194</Version>
+    </PackageReference>
+  </ItemGroup>
```

Sestavení projektu je úspěšné a získáme několik upozornění na vlákna. Tato upozornění opravujeme kliknutím `ctrl` a `.` pomocí IntelliSense a přidáte chybějící řádky přepínání vlákna.

## <a name="step-2---refactor-source-code-into-a-shared-project"></a>Krok 2 – refaktorování zdrojového kódu do sdíleného projektu

Viz [sdílené projekty](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting).

Podpora sady Visual Studio 2022 vyžaduje přidání nového sdíleného projektu, který bude obsahovat zdrojový kód rozšíření, který bude sdílen mezi projekty VSIX sady Visual Studio 2019 a Visual Studio 2022.

1. Přidání nového sdíleného projektu do řešení

   [abf249d potvrzení Git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/abf249d5a4bed9010652f3f3fc4753c7c771c892)

   ![Přidat sdílený projekt](media/samples/add-shared-project.png)

1. Do projektu VSIX přidejte odkaz na sdílený projekt.

   [e8e941e potvrzení Git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e8e941e5a5482cc15f5b9e7e4f1727f5cab5b12c)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Přidat odkaz na sdílený projekt" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Přesuňte soubory zdrojového kódu (cs, XAML, RESX) do nového sdíleného projektu **s výjimkou** následujících:
    - `source.extension.vsixmanifest`
    - Soubory metadat rozšíření (ikony, licence, poznámky k verzi atd.)
    - Soubory VSCT
    - Propojené soubory
    - Externí nástroje nebo knihovny, které je potřeba zahrnout do VSIX

   [f31f051 potvrzení Git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/f31f0515305623988f2c355ed3bf5952fc8f1d9e)

   ![Přesunout soubory do sdíleného projektu](media/samples/move-to-shared-project.png)

1. Teď přesuňte všechna metadata, soubory VSCT, propojené soubory a externí nástroje/knihovny do sdíleného umístění a přidejte je zpátky jako propojené položky do projektu VSIX.  Neodstraňujte `source.extension.vsixmanifest` .

   [Git Commit 73ba920 – přesun souborů](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/73ba920b7db0bdb7c4d66aa9bc932c268efd49cb)

   [Git Commit d5e36b2 – přidání externích nástrojů/knihoven](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d5e36b2d047290d38ffc977511510bc03e257f13)

   1. Pro tento projekt musíme přesunout ikonu rozšíření, soubor VSCT a externí nástroje do naší nové složky `ImageOptimizer\Resources` . Zkopírujte je do sdílené složky a odeberte je z projektu VSIX.
   1. Přidány je zpátky jako propojené položky a pokud jsou položky již propojeny, mohou zůstat v podobě (například licence).
   1. Ověřte, zda je akce sestavení a další vlastnosti správně nastavena v přidaných propojených souborech výběrem každého z nich a zaškrtnutím okna nástroje vlastnosti. Pro náš projekt jsme museli nastavit následující:
       - Nastavit `icon.png` akci sestavení na `Content` a označit jako zahrnuté v souboru VSIX na `true`
       - Nastavit `ImageOptimizer.vsct` akci sestavení pro `VSCTComplile` a zahrnout do souboru VSIX na `false`
       - Nastavte všechny akce sestavení souborů `Resources\Tools` do `Content` a označené jako include v souboru VSIX. `true`

           ![Přidat propojené soubory do projektu VSIX](media/samples/add-linked-files.png)

       - Navíc `ImageOptimizer.cs` je závislost `ImageOptimizer.vsct` pro, aby bylo možné tuto závislost ručně přidat do souboru csproj:

          ```diff  
          - <Content Include="..\SharedFiles\ImageOptimizer.vsct">
          -   <Link>ImageOptimizer.vsct</Link>
          - </Content>
          - <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          -   <Link>ImageOptimizer.cs</Link>
          - </Compile>

          + <VSCTCompile Include="..\SharedFiles\ImageOptimizer.vsct">
          +   <ResourceName>Menus.ctmenu</ResourceName>
          +   <Generator>VsctGenerator</Generator>
          +   <LastGenOutput>..\SharedFiles\ImageOptimizer.cs</LastGenOutput>
          + </VSCTCompile>
          + <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          +   <AutoGen>True</AutoGen>
          +   <DesignTime>True</DesignTime>
          +   <DependentUpon>..\SharedFiles\ImageOptimizer.vsct</DependentUpon>
          + </Compile>
          ```

       - Pokud okno nástroje vlastnosti zabraňuje nastavení konkrétní akce sestavení, můžete ručně upravit hodnotu csproj jak je uvedeno výše a nastavit akci sestavení podle potřeby.

1. Sestavte projekt, abyste ověřili změny a opravili všechny chyby a problémy. Běžné problémy najdete v části [Nejčastější dotazy](update-visual-studio-extension.md#q--a) .

## <a name="step-3---add-a-visual-studio-2022-vsix-project"></a>Krok 3 – přidání projektu VSIX sady Visual Studio 2022

Viz [Přidat cíl sady Visual Studio 2022](update-visual-studio-extension.md#add-a-visual-studio-2022-target).

1. Přidejte do svého řešení nový projekt VSIX.
1. Odebrat veškerý další zdrojový kód v novém projektu s výjimkou `source.extension.vsixmanifest.`

   ![Vytvořit nový projekt VSIX](media/samples/visual-studio-2022-vsix-initial.png)

1. Přidejte odkaz na svůj sdílený projekt.

   [dd49cb2 potvrzení Git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/dd49cb227b52c46206bf4be5c25790ac0377568d)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Přidat odkaz na sdílený projekt" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Přidejte propojené soubory z projektu VSIX sady Visual Studio 2019 a ověřte, že se shodují jejich vlastnosti "akce sestavení" a "zahrnout do VSIX". Také můžete zkopírovat `source.extension.vsixmanifest` soubor a později ho upravit, abychom podporovali Visual Studio 2022.

   [98c43ee potvrzení Git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/98c43ee6fbe912c38a1275542c44c65e11d7dbd9)

   ![Přidat propojené soubory do projektu VSIX](media/samples/visual-studio-2022-add-linked-files.png)

1. Pokusy o sestavení ukazují, že chybí odkaz na `System.Windows.Forms` . Jednoduše ho přidejte do našeho projektu sady Visual Studio 2022 a znovu ho sestavte.

   [de71ccd potvrzení Git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/de71ccd9baff703aa6679392ad41a2cfe7bd7d72)

   ```Diff
   + <Reference Include="System.Windows.Forms" />
   ```

1. Upgrade `Microsoft.VisualStudio.SDK` a `Microsoft.VSSDK.BuildTools` balíček odkazuje na verze sady Visual Studio 2022.

   [d581fc3 potvrzení Git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d581fc3c954974124dc7e31e5ecc85f78f7828ab)

   > [!NOTE]
   > Toto jsou nejnovější verze, které jsou k dispozici po vytvoření této příručky. Doporučuje se získat nejnovější dostupné verze.
   >
   > ```diff
   > -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
   > +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview-1-31216-1036" />
   > -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
   > +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-Visual Studio 2022-g3f11f5ab" />
   > ```

1. Upravte `source.extension.vsixmanifest` soubor tak, aby odrážel cílení na Visual Studio 2022.

   [9d393c7 potvrzení Git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/9d393c708c04ac4af48d1eb9ce3da4470db5d5cc)
   1. Nastavte `<InstallationTarget>` značku tak, aby odrážela sadu Visual Studio 2022 a označovala datovou část amd64:

      ```xml
      <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
          <ProductArchitecture>amd64</ProductArchitecture>
      </InstallationTarget>
      ```

   1. Upravte požadavek tak, aby zahrnoval jenom Visual Studio 2022 a novější:

      ```Diff
      - <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,)" DisplayName="Visual Studio core editor" />
      + <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,)" DisplayName="Visual Studio core editor" />
      ```

A hotovi!

V takovém případě sestavování nyní vytváří VSIX sady Visual Studio 2019 i sady Visual Studio 2022.

## <a name="other-samples"></a>Další ukázky

- [Nástroje Power nástrojů](https://github.com/microsoft/VS-PPT/pull/244)
  - PeekF1
    - Umožňuje prohlížení ve webovém prohlížeči pomocí informací o vybrané třídě nebo objektu.
  - FixMixedTabs
    - Vyhledá dokumenty a nahradí karty mezerami nebo naopak.

## <a name="next-steps"></a>Další kroky

Příprava na aktualizaci rozšíření načtením tohoto [Průvodce zahájením práce na dokončení](update-visual-studio-extension.md).
