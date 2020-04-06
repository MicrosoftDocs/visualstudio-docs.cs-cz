---
title: Migrace služby staršího jazyka | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 9e2eff3f3a27b7d8a276c8ed776c1e11d5ce332e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707115"
---
# <a name="migrating-a-legacy-language-service"></a>Migrace služby starší verze jazyka
Starší jazykovou službu můžete migrovat do novější verze sady Visual Studio aktualizací projektu a přidáním souboru source.extension.vsixmanifest do projektu. Samotná jazyková služba bude nadále fungovat jako dříve, protože editor sady Visual Studio ji přizpůsobí.

 Starší jazykové služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace o novém způsobu implementace jazykové služby naleznete v [tématu Editor and Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Doporučujeme, abyste co nejdříve začali používat nové rozhraní API editoru. Tím se zlepší výkon služby jazyka a umožní vám využít nové funkce editoru.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrace řešení jazykové služby sady Visual Studio 2008 na novější verzi
 Následující kroky ukazují, jak přizpůsobit ukázku sady Visual Studio 2008 s názvem RegExLanguageService. Tuto ukázku naleznete v instalaci sady SDK sady Visual Studio 2008 ve *složce instalace sady Visual Studio SDK*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ .

> [!IMPORTANT]
> Pokud vaše jazyková služba nedefinuje barvy, musíte explicitně nastavit <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> `true` na VSPackage:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Migrace jazykové služby sady Visual Studio 2008 na novější verzi

1. Nainstalujte novější verze sady Visual Studio a sady Visual Studio SDK. Další informace o způsobech instalace sady SDK naleznete v [tématu Instalace sady Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).

2. Upravte soubor RegExLangServ.csproj (bez načtení v sadě Visual Studio.

     V `Import` uzlu, který odkazuje na soubor Microsoft.VsSDK.targets, nahraďte hodnotu následujícím textem.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Uložte soubor a zavřete jej.

4. Otevřete řešení RegExLangServ.sln.

5. Zobrazí se okno **jednosměrného upgradu.** Klikněte na tlačítko **OK**.

6. Aktualizujte vlastnosti projektu. Otevřete okno **Vlastnosti projektu** tak, že v **Průzkumníku řešení**vyberete uzel projektu , klepnete pravým tlačítkem myši a **vyberete vlastnosti**.

    - Na kartě **Aplikace** změňte **cílový rámec** na **4.6.1**.

    - Na kartě **Ladění** zadejte **Start external program** do pole Spustit externí program ** \<instalační cestu sady Visual Studio>\Common7\IDE\devenv.exe.**.

         Do pole **Argumenty příkazového řádku** zadejte /**rootsuffix Exp**.

7. Aktualizujte následující odkazy:

    - Odeberte odkaz na microsoft.VisualStudio.Shell.9.0.dll a přidejte odkazy na Microsoft.VisualStudio.Shell.14.0.dll a Microsoft.VisualStudio.Shell.Immutable.11.0.dll.

    - Odeberte odkaz na soubor Microsoft.VisualStudio.Package.LanguageService.9.0.dll a přidejte odkaz na soubor Microsoft.VisualStudio.Package.LanguageService.14.0.dll.

    - Přidejte odkaz na soubor Microsoft.VisualStudio.Shell.Interop.10.0.dll.

8. Otevřete soubor VsPkg.cs a změňte hodnotu atributu `DefaultRegistryRoot` na

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. Původní ukázka nezaregistruje svou jazykovou službu, takže je nutné přidat následující atribut do VsPkg.cs.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. Je nutné přidat soubor source.extension.vsixmanifest.

    - Zkopírujte tento soubor z existující přípony do adresáře projektu. (Jedním ze způsobů, jak získat tento soubor, je vytvořit projekt VSIX (v části **Soubor**klepněte na **tlačítko Nový**a potom klepněte na **položku Project**. V části Visual Basic nebo C# klepněte na **položku Rozšiřitelnost**a vyberte **možnost VSIX Project**.)

    - Přidejte soubor do projektu.

    - Ve **vlastnostech**souboru nastavte **akci sestavení** na **žádnou**.

    - Otevřete soubor pomocí **Editoru manifestů VSIX**.

    - Změňte následující pole:

    - **ID**: RegexlangServ

    - **Název produktu**: RegexLangServ

    - **Popis**: Služba jazyka regulárních výrazů.

    - V části **Datové zdroje**klepněte na tlačítko **Nový**, vyberte **položku Type** to **Microsoft.VisualStudio.VsPackage**, nastavte **zdroj** na projekt **V aktuálním řešení**a potom nastavte **projekt** na **RegExLangServ**.

    - Uložte soubor a zavřete ho.

11. Sestavte řešení. Vytvořené soubory jsou nasazeny do **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\\\RegExLangServ**.

12. Začněte ladit. Byla otevřena druhá instance sady Visual Studio.

## <a name="see-also"></a>Viz také
- [Rozšíření služeb starší verze jazyka](../../extensibility/internals/legacy-language-service-extensibility.md)
