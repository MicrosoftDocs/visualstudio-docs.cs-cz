---
title: Nastavení vlastního procesoru direktiv
description: Seznamte se s metodami dostupnými pro nasazení vlastního procesoru direktiv v Visual Studio nebo na libovolném počítači.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, custom directive processors
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 30233bf34f523ef53d95cef153fd604cef0b6447
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384899"
---
# <a name="deploying-a-custom-directive-processor"></a>Nastavení vlastního procesoru direktiv

Pokud chcete použít vlastní procesor direktiv v Visual Studio libovolném počítači, musíte ho zaregistrovat jednou z metod popsaných v tomto tématu.

Alternativní metody jsou následující:

- [Visual Studio rozšíření](../extensibility/shipping-visual-studio-extensions.md). Tato metoda poskytuje způsob, jak nainstalovat a odinstalovat procesor direktiv ve vašem vlastním počítači i v jiných počítačích. Zpravidla můžete do stejného rozšíření VSIX zabalit jiné funkce.

- [Balíček VSPackage.](../extensibility/internals/vspackages.md) Pokud definujete VSPackage obsahující kromě procesoru direktiv i jiné funkce, lze procesor direktiv pohodlně zaregistrovat.

- Nastavení klíče registru: Pomocí této metody přidáte položku registru pro procesor direktiv.

Jednu z těchto metod je nutné použít pouze v případě, že chcete transformovat textovou šablonu v nástroji Visual Studio nebo MSBuild. Pokud ve své aplikaci používáte vlastního hostitele, je tento vlastní hostitel odpovědný za vyhledání procesoru direktiv pro jednotlivé direktivy.

## <a name="deploying-a-directive-processor-in-a-vsix"></a>Nasazení procesoru direktiv v rozšíření VSIX

Vlastní procesor direktiv můžete přidat do rozšíření [Visual Studio (VSIX).](../extensibility/starting-to-develop-visual-studio-extensions.md)

 Přitom musíte zajistit, aby v souboru .vsix byly obsaženy následující dvě položky:

- Sestavení (.dll), které obsahuje třídu vlastního procesoru direktiv

- Soubor .pkgdef, který registruje procesor direktiv Kořenový název tohoto souboru musí být stejný jako sestavení. Soubory mohou mít například název CDP.dll a CDP.pkgdef.

Chcete-li zkontrolovat nebo změnit obsah souboru .vsix, změňte jeho příponu na .zip a pak jej otevřete. Po úpravě obsahu změňte příponu souboru zpět na .vsix.

Soubor .vsix lze vytvořit několika způsoby. Jednu metodu popisuje následující postup.

#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>Vývoj vlastního procesoru direktiv v projektu VSIX

1. Vytvořte nový projekt **projektu VSIX.**

2. V **souboru source.extension.vsixmanifest** nastavte typ obsahu a podporované edice.

    1. V editoru manifestu VSIX na kartě  **Prostředky** zvolte Nový a nastavte vlastnosti nové položky:

         **Typ obsahu**  =  **Balíček VSPackage**

         **Zdrojový projekt** = \<*the current project*>

    2. Klikněte **na Vybrané edice** a zkontrolujte typy instalace, na kterých chcete procesor direktiv použít.

3. Přidejte soubor .pkgdef a nastavte jeho vlastnosti, které mají být zahrnuty do rozšíření VSIX.

    1. Vytvořte textový soubor a pojmnujte \<*assemblyName*> ho .pkgdef.

         \<*assemblyName*> je obvykle stejný jako název projektu.

    2. V Průzkumníku řešení ho vyberte a následujícím způsobem nastavte jeho vlastnosti:

         **Akce sestavení**  =  **Obsah**

         **Kopírování do výstupního adresáře**  =  **Vždy kopírovat**

         **Zahrnutí do VSIX**  =  **True (Pravda)**

    3. Nastavte název rozšíření VSIX a ujistěte se, že je ID jedinečné.

4. Do souboru .pkgdef přidejte následující text.

    ```
    [$RootKey$\TextTemplating]
    [$RootKey$\TextTemplating\DirectiveProcessors]
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]
    @="Custom Directive Processor description"
    "Class"="NamespaceName.ClassName"
    "CodeBase"="$PackageFolder$\AssemblyName.dll"
    ```

     Nahraďte následující názvy vlastními názvy: `CustomDirectiveProcessorName` , `NamespaceName` , , `ClassName` `AssemblyName` .

5. Přidejte do projektu následující odkazy:

    - **Microsoft.VisualStudio.TextTemplating. \* . 0**

    - **Microsoft.VisualStudio.TextTemplating.Interfaces. \* . 0**

    - **Microsoft.VisualStudio.TextTemplating.VSHost. \* . 0**

6. Přidejte do projektu třídu vlastního procesoru direktiv.

     Toto je veřejná třída, která by měla implementovat <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> nebo <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> .

#### <a name="to-install-the-custom-directive-processor"></a>Instalace vlastního procesoru direktiv

1. V Průzkumník Windows otevřete adresář sestavení (obvykle bin\Debug nebo bin\Release).

2. Pokud chcete procesor direktiv nainstalovat do jiného počítače, zkopírujte soubor .vsix do tohoto počítače.

3. Dvakrát klikněte na soubor .vsix. Zobrazí Visual Studio instalační program rozšíření.

4. Restartujte Visual Studio. Nyní budete moci spouštět textové šablony obsahující direktivy, které odkazují na vlastní procesor direktiv. Jednotlivé direktivy mají tento formát:

     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" ... #>`

#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>Odinstalace nebo dočasné vypnutí vlastního procesoru direktiv

1. V nabídce Visual Studio **Nástroje** klikněte na **Správce rozšíření.**

2. Vyberte VSIX, který obsahuje procesor direktiv, a potom klikněte na **Odinstalovat** nebo **Zakázat**.

### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>Řešení potíží s procesorem direktiv v rozšíření VSIX
 Pokud procesor direktiv nefunguje, mohou vám pomoci následující návrhy:

- Název procesoru, který zadáte ve vlastní direktivě, by se měl shodovat s názvem zadaným `CustomDirectiveProcessorName` v souboru .pkgdef.

- Vaše `IsDirectiveSupported` metoda se musí `true` vrátit, když se předá název vaší `CustomDirective` metody .

- Pokud rozšíření ve Správci rozšíření nevidíte, ale systém vám ho nepovolí nainstalovat, odstraňte ho ze složky **%localappdata%\Microsoft\VisualStudio \\ \* \\ .0\Extensions.**

- Otevřete soubor .vsix a zkontrolujte jeho obsah. Chcete-li jej otevřít, změňte jeho příponu na .zip. Ověřte, zda obsahuje soubory .dll, .pkgdef a extension.vsixmanifest. Soubor extension.vsixmanifest by měl obsahovat příslušný seznam v uzlu SupportedProducts a měl by také obsahovat uzel VsPackage pod uzlem Content:

     `<Content>`

     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`

     `</Content>`

## <a name="deploying-a-directive-processor-in-a-vspackage"></a>Nasazení procesoru direktiv v sadě VSPackage
 Pokud je procesor direktiv součástí sady VSPackage, která se bude instalovat do mezipaměti GAC, můžete systém nechat vygenerovat soubor .pkgdef za vás.

 Vložte do třídy balíčku následující atribut:

```csharp
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]
```

> [!NOTE]
> Tento atribut je umístěn ve třídě balíčku, nikoli ve třídě procesoru direktiv.

 Soubor .pkgdef se vygeneruje při sestavení projektu. Při instalaci sady VSPackage zaregistruje soubor .pkgdef procesor direktiv.

 Ověřte, zda je soubor .pkgdef ve složce sestavení, obvykle bin\Debug nebo bin\Release. Pokud se nezobrazí, otevřete soubor .csproj v textovém editoru a odeberte následující uzel: `<GeneratePkgDefFile>false</GeneratePkgDefFile>` .

 Další informace najdete v tématu [Balíčky VSPackage.](../extensibility/internals/vspackages.md)

## <a name="setting-a-registry-key"></a>Nastavení klíče registru
 Tato metoda instalace vlastního procesoru direktiv se příliš nedoporučuje. Neposkytuje totiž pohodlný způsob zapnutí a vypnutí procesoru direktiv ani způsob distribuce procesoru direktiv jiným uživatelům.

> [!CAUTION]
> Nesprávná úprava registru může vážně poškodit systém. Před prováděním změn registru nezapomeňte vytvořit zálohu všech cenných dat v počítači.

#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>Registrace procesoru direktiv nastavením klíče registru

1. Spusťte `regedit`.

2. V editoru registru přejděte na

    **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ \* .0\TextTemplating\DirectiveProcessors**

    Pokud chcete procesor direktiv nainstalovat v experimentální verzi Visual Studio vložte "Exp" za "11.0".

3. Přidejte klíč registru, který má stejný název jako třída procesoru direktiv.

   - Ve stromu registru klikněte pravým tlačítkem na uzel **DirectiveProcessors,** přejděte na **Nový** a potom klikněte na **Klíč**.

4. V novém uzlu přidejte podle následujících tabulek řetězcové hodnoty Class a CodeBase nebo Assembly.

   1. Klikněte pravým tlačítkem na uzel, který jste vytvořili, přejděte na **Nový** a pak klikněte na **Řetězcová hodnota**.

   2. Upravte název hodnoty.

   3. Dvakrát klikněte na název a upravte data.

   Pokud vlastní procesor direktiv není v mezipaměti GAC, měly by podklíče registru vypadat podle následující tabulky:

|Název|Typ|Data|
|-|-|-|
|(Výchozí)|REG_SZ|(hodnota nenastavena)|
|Třída|REG_SZ|**\<Namespace Name>.\<Class Name>**|
|CodeBase|REG_SZ|**\<Your Path>\\<názvu sestavení\>**|

 Pokud je sestavení v mezipaměti GAC, měly by podklíče registru vypadat podle následující tabulky:

|Název|Typ|Data|
|-|-|-|
|(Výchozí)|REG_SZ|(hodnota nenastavena)|
|Třída|REG_SZ|\<**Your Fully Qualified Class Name**>|
|Sestavení|REG_SZ|\<**Your Assembly Name in the GAC**>|

## <a name="see-also"></a>Viz také

- [Vytváření vlastních procesorů pro direktivy textových šablon T4](../modeling/creating-custom-t4-text-template-directive-processors.md)
