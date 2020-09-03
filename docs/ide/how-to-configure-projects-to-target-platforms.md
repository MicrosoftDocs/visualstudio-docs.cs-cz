---
title: 'Postupy: konfigurace projektů pro cílové platformy'
ms.date: 08/16/2019
ms.technology: vs-ide-compile
ms.topic: how-to
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
ms.openlocfilehash: a58b60e23bf08fb86a8dd7bc09d760085b6ea25f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284595"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Postupy: konfigurace projektů pro cílové platformy

Sada Visual Studio umožňuje nastavit vaše aplikace na různé platformy, včetně 64 bitů na platformě. Další informace o podpoře 64 bitových platforem v aplikaci Visual Studio naleznete v tématu [64-bitové aplikace](/dotnet/framework/64-bit-apps).

## <a name="target-platforms-with-the-configuration-manager"></a>Cílové platformy s Configuration Manager

**Configuration Manager** poskytuje způsob, jak rychle přidat novou platformu pro cílení na váš projekt. Pokud vyberete jednu z platforem, které jsou součástí sady Visual Studio, vlastnosti projektu jsou upraveny pro sestavení projektu pro vybranou platformu.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Konfigurace projektu pro cílení na 64 platformu

1. Na panelu nabídek vyberte možnost **sestavit**  >  **Configuration Manager**.

2. V seznamu **Aktivní platforma řešení** zvolte 64 platformu pro cílové řešení a pak klikněte na tlačítko **Zavřít** .

    1. Pokud se požadovaná platforma nezobrazí v seznamu **Aktivní platforma řešení** , vyberte možnost **nové**.

         Zobrazí se dialogové okno **Nová platforma řešení** .

    2. V rozevíracím seznamu **Typ vyberte Nová platforma** a zvolte možnost **x64**.

        > [!NOTE]
        > Pokud vaší konfiguraci přiřadíte nový název, může být nutné upravit nastavení v **Návrháři projektu** , aby se zacíleno na správnou platformu.

    3. Pokud chcete zkopírovat nastavení z aktuální konfigurace platformy, vyberte ji a pak klikněte na tlačítko **OK** .

Vlastnosti pro všechny projekty, které cílí na 64, jsou aktualizovány a další sestavení projektu bude optimalizováno pro 64-bitové platformy.

> [!NOTE]
> Název platformy **Win32** se používá pro projekty v jazyce C++ a to znamená **x86**. Visual Studio zohledňuje platformy na úrovni projektu i platformy na úrovni řešení a projektové platformy pocházejí ze systémů projektů specifických pro jazyk. Projekty C++ používají **Win32** a **x64**, ale platformy řešení používají **platformu x86** a **x64**. Když jako konfiguraci řešení zvolíte **x86** , Visual Studio vybere platformu **Win32** pro projekty v jazyce C++. Chcete-li zobrazit nastavení platformy na úrovni projektu i na úrovni řešení, otevřete **Configuration Manager** a poznamenejte si nastavení těchto dvou platforem. Platforma na úrovni řešení je zobrazena v rozevírací nabídce **aktivní řešení platformy** a tabulka zobrazuje platformu na úrovni projektu pro každý projekt.
> ![Snímek obrazovky znázorňující platformu řešení a platformu projektu](media/project-platform-win32.png)

## <a name="target-platforms-in-the-project-designer"></a>Cílové platformy v Návrháři projektu

**Návrhář projektu** také poskytuje způsob, jak cílit na různé platformy s vaším projektem. Pokud výběr jedné z platforem zahrnutých v seznamu v dialogovém okně **Nová platforma řešení** nefunguje pro vaše řešení, můžete vytvořit vlastní název konfigurace a upravit nastavení v **Návrháři projektu** , abyste mohli cílit na správnou platformu.

Provádění tohoto úkolu se liší v závislosti na programovacím jazyku, který používáte. Další informace najdete na následujících odkazech:

- Pro [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projekty naleznete v tématu [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- Pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projekty, viz [Stránka sestavení, Návrhář projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).

- Pro [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projekty naleznete v tématu [/CLR (Common Language Runtime Compilation)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="manually-editing-the-project-file"></a>Ruční úprava souboru projektu

V některých případech je nutné ručně upravit soubor projektu pro určitou vlastní konfiguraci. Příkladem je, že máte podmínky, které nelze zadat v integrovaném vývojovém prostředí (IDE), jako je například odkaz, který je odlišný pro dvě různé platformy, jako v následujícím příkladu.

### <a name="example-referencing-x86-and-x64-assemblies-and-dlls"></a>Příklad: odkazování na sestavení a knihovny DLL pro x86 a x64

Je možné, že máte sestavení .NET nebo knihovnu DLL, které mají verze x86 i x64. Chcete-li nastavit projekt pro použití těchto odkazů, přidejte nejprve odkaz a poté otevřete soubor projektu a upravte jej tak, aby se přidala `ItemGroup` podmínka, která odkazuje jak na konfiguraci, tak na cílovou platformu.  Předpokládejme například, že binární soubor, na který odkazujete, je ClassLibrary1 a jsou k dispozici různé cesty pro konfigurace ladění a vydaných verzí a také verze x86 a x64.  Pak použijte čtyři `ItemGroup` prvky se všemi kombinacemi nastavení následujícím způsobem:

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
> V aplikaci Visual Studio 2017 je nutné před úpravou souboru projektu uvolnit projekt. Chcete-li uvolnit projekt, klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Uvolnit projekt**. Po dokončení úprav uložte změny a znovu načtěte projekt kliknutím pravým tlačítkem myši na uzel projektu a výběrem možnosti **znovu načíst projekt**.
::: moniker-end

Další informace o souboru projektu naleznete v tématu [Referenční dokumentace schématu souboru projektu nástroje MSBuild](../msbuild/msbuild-project-file-schema-reference.md).

## <a name="see-also"></a>Viz také

- [Vysvětlení platforem sestavení](../ide/understanding-build-platforms.md)
- [/Platform (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [64 – bitové aplikace](/dotnet/framework/64-bit-apps)
- [Visual Studio IDE 64 – Podpora bitových procesorů](../ide/visual-studio-ide-64-bit-support.md)
- [Porozumění souboru projektu](/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file)
