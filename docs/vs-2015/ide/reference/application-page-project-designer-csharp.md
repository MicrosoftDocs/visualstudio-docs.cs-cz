---
title: Stránka aplikace, Návrhář projektu (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: f13701a8-4e2e-4474-9d60-bb43decbe0c1
caps.latest.revision: 61
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2bf9c64a55f6f3b49cb1e0a50fa532f276394dac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851999"
---
# <a name="application-page-project-designer-c"></a>Stránka Aplikace, návrhář projektu (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Použijte stránku **aplikace** **Návrháře projektu** k určení nastavení aplikace a vlastností projektu.

 Pro přístup ke stránce **aplikace** vyberte uzel projektu (nikoli uzel **řešení** ) v **Průzkumník řešení**. Pak zvolte **projekt**, **vlastnosti** na řádku nabídek. Když se zobrazí Návrhář projektu, klikněte na kartu **aplikace** .

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="general-application-settings"></a>Obecné nastavení aplikace
 Následující možnosti umožňují nakonfigurovat obecná nastavení aplikace.

 **Název sestavení** Určuje název výstupního souboru, který bude obsahovat manifest sestavení. Změnou této vlastnosti se změní také vlastnost **Název výstupu** . Tuto změnu můžete provést také z příkazového řádku pomocí [/out (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5). Chcete-li získat přístup k této vlastnosti programově, přečtěte si téma <xref:VSLangProj.ProjectProperties.AssemblyName%2A> .

 **Výchozí obor názvů** Určuje základní obor názvů pro soubory přidané do projektu.

 Další informace o vytváření oborů názvů v kódu naleznete v tématu [obor názvů](https://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f) .

 Chcete-li získat přístup k této vlastnosti programově, přečtěte si téma <xref:VSLangProj.ProjectProperties.RootNamespace%2A> .

 **Cílová architektura** Určuje verzi .NET Framework, na kterou aplikace cílí. Tato možnost může mít různé hodnoty v závislosti na tom, které verze .NET Framework jsou nainstalovány ve vašem počítači.

 Ve výchozím nastavení je hodnota shodná s cílovou architekturou, kterou jste vybrali v dialogovém okně **Nový projekt** .

> [!NOTE]
> Požadované balíčky uvedené v [dialogovém okně požadavky](../../ide/reference/prerequisites-dialog-box.md) se nastaví automaticky při prvním otevření dialogového okna. Pokud následně změníte cílovou architekturu projektu, bude nutné vybrat požadované součásti ručně, aby odpovídaly novému cílovému rozhraní.

 Další informace najdete v tématu [Postupy: cílení na verzi .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) a [Visual Studio – Přehled cílení na více](../../ide/visual-studio-multi-targeting-overview.md)verzí.

 **Typ aplikace** Určuje typ aplikace, která se má sestavit. Pro [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikace můžete zadat aplikaci pro **Windows Store**, **knihovnu tříd**nebo **soubor winmd**. Pro většinu ostatních typů aplikací můžete určit **aplikaci systému Windows**, **konzolovou aplikaci**, **knihovnu tříd**, **službu systému Windows**nebo **knihovnu webového ovládacího prvku**.

 Pro projekt webové aplikace je nutné zadat **knihovnu tříd**.

 Pokud zadáte možnost **soubor winmd** , typy lze promítnout do libovolného programovacího jazyka prostředí Windows Runtime. Sbalením výstupu projektu jako souboru WinMD můžete kódovat aplikaci v různých jazycích a nechat kód fungovat, jako kdybyste ho vytvořili ve stejném jazyce. Tuto možnost můžete zadat pro řešení, která cílí na knihovny prostředí Windows Runtime, včetně [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikací. Další informace naleznete v tématu [vytváření prostředí Windows runtimech komponent v jazyce C# a Visual Basic](https://msdn.microsoft.com/library/windows/apps/br230301(v=VS.85).aspx).

> [!NOTE]
> Prostředí Windows Runtime mohou být typy projektů tak, aby se zobrazily jako nativní objekty v jakémkoli jazyku, který je používá. Například aplikace JavaScriptu, které pracují s prostředí Windows Runtime použít jako sadu objektů jazyka JavaScript a aplikace jazyka C# používají knihovnu jako kolekci objektů rozhraní .NET. Sbalením výstupu projektu jako souboru WinMD můžete využít stejnou technologii, jakou prostředí Windows Runtime používá.

 Další informace o vlastnosti **Typ aplikace** naleznete v tématu [/target (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f). Informace o tom, jak získat přístup k této vlastnosti prostřednictvím kódu programu, najdete v tématu <xref:VSLangProj.ProjectProperties.OutputType%2A> .

 **Informace o sestavení** Kliknutím na toto tlačítko se zobrazí [dialogové okno informace o sestavení](../../ide/reference/assembly-information-dialog-box.md).

 **Spouštěcí objekt** Definuje vstupní bod, který se má volat při načtení aplikace. Obecně je tato možnost nastavena buď na hlavní formulář v aplikaci, nebo na `Main` proceduru, která by měla být spuštěna při spuštění aplikace. Vzhledem k tomu, že knihovny tříd nemají vstupní bod, je jejich jediná možnost pro tuto vlastnost **(nenastavená)**.

 Ve výchozím nastavení je v projektu aplikace prohlížeče WPF Tato možnost **(Nenastaveno)**. Druhou možností je *ProjectName*. app. V tomto typu projektu je nutné nastavit spouštěcí identifikátor URI pro načtení prostředku uživatelského rozhraní při spuštění aplikace. Provedete to tak, že otevřete soubor Application. XAML v projektu a nastavíte `StartupUri` vlastnost na soubor. XAML v projektu, například Window1. XAML. Seznam přijatelných kořenových elementů naleznete v tématu <xref:System.Windows.Application.StartupUri%2A> . Také je nutné definovat `public static void Main()` metodu ve třídě v projektu. Tato třída se zobrazí v seznamu **spouštěcích objektů** jako *ProjectName. ClassName*. Pak můžete vybrat třídu jako spouštěcí objekt.

 Další informace naleznete v tématu [/Main (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049) . Chcete-li získat přístup k této vlastnosti programově, přečtěte si téma <xref:VSLangProj.ProjectProperties.StartupObject%2A> .

## <a name="resources"></a>Zdroje a prostředky
 Následující možnosti umožňují nakonfigurovat obecná nastavení aplikace.

 **Ikona a manifest** Ve výchozím nastavení je tento přepínač vybraný a jsou povolené **ikony** a možnosti **manifestu** . To vám umožní vybrat si vlastní ikonu nebo vybrat jiné možnosti generování manifestu. Pokud pro projekt neposkytnete soubor prostředků, ponechte tento přepínač vybraný.

 **Ikona** Nastaví soubor. ico, který chcete použít jako ikonu programu. Kliknutím na tlačítko se třemi tečkami vyhledejte existující grafiku nebo zadejte název souboru, který chcete. Další informace naleznete v tématu [/win32icon (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138) . Chcete-li získat přístup k této vlastnosti programově, přečtěte si téma <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A> .

 **Manifest** Vybere možnost generování manifestu, pokud je aplikace spuštěna v systému Windows Vista pod nástrojem Řízení uživatelských účtů (UAC). Tato možnost může mít následující hodnoty:

- **Vloží manifest s výchozími nastaveními**. Podporuje typický způsob, jakým aplikace Visual Studio funguje v systému Windows Vista, což znamená vložení informací o zabezpečení do spustitelného souboru aplikace. tím se určí `requestedExecutionLevel` `AsInvoker` . Toto je výchozí možnost.

- **Vytvořit aplikaci bez manifestu** Tato metoda se označuje jako *virtualizace*. Tato možnost slouží k zajištění kompatibility se staršími aplikacemi.

- **Properties\app.manifest**. Tato možnost je vyžadována pro aplikace nasazené pomocí technologie ClickOnce nebo bez registrace modelu COM. Pokud publikujete aplikaci pomocí nasazení ClickOnce, **manifest** je automaticky nastaven na tuto možnost.

  **Soubor prostředků** Vyberte tento přepínač při poskytování souboru prostředků pro projekt. Výběrem této možnosti zakážete **ikonu** a možnosti **manifestu** .

  Zadejte název cesty nebo použijte tlačítko Procházet (**...**) a přidejte soubor prostředků Win32 do projektu.

## <a name="see-also"></a>Viz také
[Správa vlastností aplikace](../../ide/application-properties.md) [při psaní kódu v řešeních pro systém Office](https://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0)
