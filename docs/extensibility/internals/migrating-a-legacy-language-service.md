---
title: Migrace služby starší verze jazyka | Microsoft Docs
description: Naučte se aktualizovat službu jazyka na nejnovější verzi sady Visual Studio, a to tak, že aktualizujete projekt a přidáte zdrojový soubor. extension. vsixmanifest.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ced200ff24b17f312e63642c8083f038a6fc6a4d
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877829"
---
# <a name="migrating-a-legacy-language-service"></a>Migrace služby starší verze jazyka
Službu starší verze jazyka můžete migrovat na novější verzi sady Visual Studio tak, že aktualizujete projekt a přidáte do projektu soubor source. extension. vsixmanifest. Samotná služba jazyka bude nadále fungovat stejně jako dříve, protože editor sady Visual Studio ho přizpůsobí.

 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace o novém způsobu implementace jazykové služby najdete v tématu [rozšíření pro Editor a jazykové služby](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrace řešení jazykové služby sady Visual Studio 2008 na novější verzi
 Následující kroky ukazují, jak upravit ukázku sady Visual Studio 2008 s názvem RegExLanguageService. Tuto ukázku najdete v instalaci sady Visual Studio 2008 SDK ve složce *Instalační cesta sady Visual Studio SDK*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\.

> [!IMPORTANT]
> Pokud vaše jazyková služba nedefinuje barvy, musíte explicitně nastavit <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> na `true` VSPackage:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Migrace jazykové služby sady Visual Studio 2008 na novější verzi

1. Nainstalujte novější verze sady Visual Studio a sadu Visual Studio SDK. Další informace o způsobech instalace sady SDK najdete v tématu [instalace sady Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).

2. Upravte soubor RegExLangServ. csproj (bez jeho načtení v aplikaci Visual Studio.

     V `Import` uzlu, který odkazuje na soubor Microsoft. VsSDK. targets, nahraďte hodnotu následujícím textem.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Uložte soubor a pak ho zavřete.

4. Otevřete řešení RegExLangServ. sln.

5. Zobrazí se okno **jednosměrného upgradu** . Klikněte na **OK**.

6. Aktualizujte vlastnosti projektu. Otevřete okno **Vlastnosti projektu** tak, že v **Průzkumník řešení** vyberete uzel projektu, kliknete pravým tlačítkem a vyberete **vlastnosti**.

    - Na kartě **aplikace** změňte **cílové rozhraní .NET Framework** na **4.6.1**.

    - Na kartě **ladění** v poli **spustit externí program** zadejte **\<Visual Studio installation path>\Common7\IDE\devenv.exe.**.

         Do pole **argumenty příkazového řádku** zadejte/**rootsuffix exp**.

7. Aktualizujte tyto odkazy:

    - Odeberte odkaz na Microsoft.VisualStudio.Shell.9.0.dll a pak přidejte odkazy na Microsoft.VisualStudio.Shell.14.0.dll a Microsoft.VisualStudio.Shell.Immutable.11.0.dll.

    - Odeberte odkaz na Microsoft.VisualStudio.Package.LanguageService.9.0.dll a pak přidejte odkaz na Microsoft.VisualStudio.Package.LanguageService.14.0.dll.

    - Přidejte odkaz na Microsoft.VisualStudio.Shell.Interop.10.0.dll.

8. Otevřete soubor VsPkg.cs a změňte hodnotu `DefaultRegistryRoot` atributu na

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. Původní ukázka neregistruje svou jazykovou službu, takže musíte do VsPkg.cs přidat následující atribut.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. Je nutné přidat soubor source. extension. vsixmanifest.

    - Zkopírujte tento soubor z existujícího rozšíření do adresáře projektu. (Jedním ze způsobů, jak tento soubor získat, je vytvoření projektu VSIX (v části **soubor** klikněte na **Nový** a potom na **projekt**. V části Visual Basic nebo C# klikněte na **rozšiřitelnost** a pak vyberte **projekt VSIX**.)

    - Přidejte soubor do projektu.

    - Ve **vlastnostech** souboru nastavte **akci sestavení** na **žádná**.

    - Otevřete soubor pomocí **editoru manifestu VSIX**.

    - Změňte následující pole:

    - **ID**: RegExLangServ

    - **Název produktu**: RegExLangServ

    - **Popis**: služba jazyka regulárních výrazů.

    - V části **assety** klikněte na **Nový**, **Vyberte typ** pro **Microsoft. VisualStudio. VSPackage**, nastavte **zdroj** na **projekt v aktuálním řešení** a pak nastavte **projekt** na **RegExLangServ**.

    - Uložte soubor a zavřete ho.

11. Sestavte řešení. Sestavené soubory se nasadí do **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ \\ RegExLangServ**.

12. Spuštění ladění Byla otevřena druhá instance aplikace Visual Studio.

## <a name="see-also"></a>Viz také
- [Rozšíření služeb starší verze jazyka](../../extensibility/internals/legacy-language-service-extensibility.md)
