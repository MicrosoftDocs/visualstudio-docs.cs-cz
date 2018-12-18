---
title: Migrace služby jazyk starší | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 412b09016a3f889e0d6c5e40ff75895d5ae8ff48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135847"
---
# <a name="migrating-a-legacy-language-service"></a>Migrace služby jazyk starší verze
Služba starší verze jazyka na novější verzi sady Visual Studio můžete migrovat aktualizace projektu a přidáním soubor source.extension.vsixmanifest do projektu. Samotnou službu jazyk nadále fungovat jako předtím, protože editoru Visual Studio přizpůsobuje ho.  
  
 Starší verze jazyka služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkce služby jazyk je použití MEF rozšíření. Další informace o nový způsob implementace služba jazyka, najdete v tématu [Editor a rozšíření služeb jazyk](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat co nejdříve editoru nové rozhraní API. Tím zvýšit výkon služby jazyk a umožňují využívat výhod nových funkcí editoru.  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrace řešení jazyk služby sady Visual Studio 2008 na novější verzi  
 Následující kroky ukazují, jak přizpůsobit ukázku Visual Studio 2008 s názvem RegExLanguageService. Tato ukázka v rámci instalace Visual Studio 2008 SDK, můžete najít v *cesta instalace Visual Studio SDK*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ složky.  
  
> [!IMPORTANT]
>  Pokud vaše služba jazyka nedefinuje barvy, je nutné explicitně nastavit <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> k `true` na VSPackage:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>K migraci služby jazyk Visual Studio 2008 na novější verzi  
  
1.  Nainstalujte novější verze sady Visual Studio a sadu Visual Studio SDK. Další informace o způsobech instalace sady SDK najdete v tématu [instalace sady Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Upravte soubor RegExLangServ.csproj (bez načítání ho v sadě Visual Studio.  
  
     V `Import` uzlu, který odkazuje na soubor Microsoft.VsSDK.targets nahraďte následujícím textem hodnotu.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  Soubor uložte a zavřete ji.  
  
4.  Otevřete RegExLangServ.sln řešení.  
  
5.  **Jednosměrný upgrade** se zobrazí v okně. Click **OK**.  
  
6.  Aktualizujte vlastnosti projektu. Otevřete **vlastnosti projektu** okna tak, že vyberete v uzlu projektu **Průzkumníku řešení**, klikněte pravým tlačítkem na a vyberete **vlastnosti**.  
  
    -   Na **aplikace** změňte **cílové rozhraní** k **4.6.1**.  
  
    -   Na **ladění** ve **počáteční vnějšímu programu** zadejte  **\<cesta instalace sady Visual Studio > \Common7\IDE\devenv.exe.**.  
  
         V **argumenty příkazového řádku** zadejte /**rootsuffix Exp**.  
  
7.  Aktualizujte následující odkazy:  
  
    -   Odeberte odkaz na Microsoft.VisualStudio.Shell.9.0.dll a pak přidejte odkazy na Microsoft.VisualStudio.Shell.14.0.dll a Microsoft.VisualStudio.Shell.Immutable.11.0.dll.  
  
    -   Odeberte odkaz na Microsoft.VisualStudio.Package.LanguageService.9.0.dll a pak přidejte odkaz na Microsoft.VisualStudio.Package.LanguageService.14.0.dll.  
  
    -   Přidáte odkaz na Microsoft.VisualStudio.Shell.Interop.10.0.dll.  
  
8.  Otevřete soubor VsPkg.cs a změňte hodnotu `DefaultRegistryRoot` atribut  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. Původní ukázce nezaregistruje jeho služba jazyka, musíte do VsPkg.cs přidat následující atribut.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. Je nutné přidat soubor source.extension.vsixmanifest.  
  
    -   Tento soubor zkopírujte z existující rozšíření do vašeho adresáře projektu. (Je možné získat tento soubor k vytvoření projektu VSIX (v části **soubor**, klikněte na tlačítko **nový**, pak klikněte na tlačítko **projektu**. Klikněte v části Visual Basic a C# **rozšiřitelnost**, pak vyberte **projektu VSIX**.)  
  
    -   Přidejte soubor do projektu.  
  
    -   V souboru **vlastnosti**, nastavte **akce sestavení** k **žádné**.  
  
    -   Otevřete soubor s **VSIX Manifest Editor**.  
  
    -   Změňte následující pole:  
  
    -   **ID**: RegExLangServ  
  
    -   **Název produktu**: RegExLangServ  
  
    -   **Popis**: služba jazyka regulární výraz.  
  
    -   V části **prostředky**, klikněte na tlačítko **nový**, vyberte **typ** k **Microsoft.VisualStudio.VsPackage**, nastavte **zdroj** k **na projekt v aktuálním řešení**a poté nastavte **projektu** k **RegExLangServ**.  
  
    -   Soubor uložte a zavřete.  
  
11. Sestavte řešení. Vytvořené soubory se nasadí do **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\**.  
  
12. Spusťte ladění. Otevřít druhou instanci sady Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření služeb starší verze jazyka](../../extensibility/internals/legacy-language-service-extensibility.md)