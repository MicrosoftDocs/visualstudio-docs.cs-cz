---
title: 'Postup: Konfigurace projektů pro cílové platformy'
ms.date: 08/16/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cbe4bc3f982ae18b9f85fe8bf5c21495c98beee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76112540"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Postup: Konfigurace projektů pro cílové platformy

Visual Studio umožňuje nastavit aplikace tak, aby cílily na různé platformy, včetně 64bitových platforem. Další informace o podpoře 64bitové platformy v sadě Visual Studio najdete v [tématu 64bitové aplikace](/dotnet/framework/64-bit-apps).

## <a name="target-platforms-with-the-configuration-manager"></a>Cílové platformy pomocí Nástroje pro konfiguraci

**Nástroj Configuration Manager** nabízí způsob, jak rychle přidat novou platformu, na kterou chcete cílit s projektem. Pokud vyberete jednu z platforem součástí sady Visual Studio, vlastnosti pro váš projekt jsou upraveny tak, aby vytvořily projekt pro vybranou platformu.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Konfigurace projektu pro cílovou 64bitovou platformu

1. Na řádku nabídek zvolte **Build** > **Configuration Manager**.

2. V seznamu **Aktivní platforma řešení** zvolte 64bitovou platformu pro řešení, na které chcete cílit, a pak zvolte tlačítko **Zavřít.**

    1. Pokud se požadovaná platforma nezobrazí v seznamu **Aktivní platforma řešení,** zvolte **Nový**.

         Zobrazí se dialogové okno **Nová platforma řešení.**

    2. V seznamu **Typ nebo vyberte novou platformu** zvolte **x64**.

        > [!NOTE]
        > Pokud přidáváte konfiguraci nový název, bude pravděpodobně nutné upravit nastavení v **Návrháři projektu,** abyste cílili na správnou platformu.

    3. Pokud chcete zkopírovat nastavení z aktuální konfigurace platformy, zvolte ji a pak zvolte tlačítko **OK.**

Vlastnosti pro všechny projekty, které cílí na 64bitovou platformu, se aktualizují a další sestavení projektu bude optimalizováno pro 64bitové platformy.

## <a name="target-platforms-in-the-project-designer"></a>Cílové platformy v návrháři projektů

**Návrhář projektu** také poskytuje způsob, jak cílit na různé platformy s projektem. Pokud výběr jedné z platforem zahrnutých v seznamu v dialogovém okně **Nová platforma řešení** nefunguje pro vaše řešení, můžete vytvořit vlastní název konfigurace a upravit nastavení v **Návrháři projektu** tak, aby se zaměřilo na správnou platformu.

Provedení této úlohy se liší v závislosti na programovacím jazyce, který používáte. Další informace naleznete na následujících odkazech:

- Pro [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projekty naleznete [v tématu /platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- Pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projekty naleznete v [tématu Sestavení stránky, Návrhář projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).

- Pro [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projekty naleznete v tématu [/clr (Kompilace common language runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="manually-editing-the-project-file"></a>Ruční úprava souboru projektu

Někdy je třeba ručně upravit soubor projektu pro některé vlastní konfigurace. Příkladem je, když máte podmínky, které nelze zadat v ide, jako je například odkaz, který se liší pro dvě různé platformy, jako v následujícím příkladu.

### <a name="example-referencing-x86-and-x64-assemblies-and-dlls"></a>Příklad: Odkazování na sestavení x86 a x64 a knihovny DLL

Můžete mít sestavení .NET nebo DLL, která má verze x86 a x64. Chcete-li nastavit projekt pro použití těchto odkazů, nejprve přidejte odkaz a potom `ItemGroup` otevřete soubor projektu a upravte jej tak, aby se přidala podmínka, která odkazuje na konfiguraci i cílovou platformu.  Předpokládejme například, že binární soubor, na který odkazujete, je ClassLibrary1 a existují různé cesty pro konfigurace ladění a vydání, stejně jako verze x86 a x64.  Potom použijte `ItemGroup` čtyři prvky se všemi kombinacemi nastavení, a to následovně:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
    <Platforms>AnyCPU;x64;x86</Platforms>
  </PropertyGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
  
  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
</Project>
```

::: moniker range="vs-2017"
> [!NOTE]
> V sadě Visual Studio 2017 je třeba uvolnit projekt před úpravou souboru projektu. Chcete-li projekt uvolnit, klepněte pravým tlačítkem myši na uzel projektu a zvolte **Uvolnit projekt**. Po dokončení úprav uložte změny a znovu načtěte projekt kliknutím pravým tlačítkem myši na uzel projektu a výběrem **možnosti Znovu načíst projekt**.
::: moniker-end

Další informace o souboru projektu naleznete v [tématu MSBuild](../msbuild/msbuild-project-file-schema-reference.md)odkaz na schéma souboru projektu .

## <a name="see-also"></a>Viz také

- [Vysvětlení platforem sestavení](../ide/understanding-build-platforms.md)
- [/platforma (možnosti kompilátoru Jazyka C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [64bitové aplikace](/dotnet/framework/64-bit-apps)
- [Podpora 64bitového zařízení Visual Studio IDE](../ide/visual-studio-ide-64-bit-support.md)
- [Principy souboru projektu](/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file)
