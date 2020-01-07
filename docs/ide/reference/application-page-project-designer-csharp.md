---
title: Stránka aplikace – C# vlastnosti projektu
ms.date: 10/30/2018
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ef9a38fc13d0d9c9f6b912f4cb2b83971d105c29
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595823"
---
# <a name="application-page-project-designer-c"></a>Stránka Aplikace, návrhář projektu (C#)

Použijte stránku **aplikace** **Návrháře projektu** k určení nastavení aplikace a vlastností projektu.

Pro přístup ke stránce **aplikace** vyberte uzel projektu (nikoli uzel **řešení** ) v **Průzkumník řešení**. Pak zvolte **projekt** > **vlastnosti** na řádku nabídek. Když se zobrazí **Návrhář projektu** , klikněte na kartu **aplikace** .

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Obecné nastavení aplikace

Následující možnosti umožňují nakonfigurovat obecná nastavení aplikace.

**Název sestavení**

Určuje název výstupního souboru, který bude obsahovat manifest sestavení. Změna této vlastnosti také změní vlastnost **Název výstupu** .

Tuto změnu můžete provést také z příkazového řádku pomocí [/out (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).

Chcete-li získat přístup k této vlastnosti programově, přečtěte si téma <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Výchozí obor názvů**

Určuje základní obor názvů pro soubory přidané do projektu.

Další informace o vytváření oborů názvů v kódu naleznete v tématu [obor názvů](/dotnet/csharp/language-reference/keywords/namespace) .

Chcete-li získat přístup k této vlastnosti programově, přečtěte si téma <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Cílová architektura**

Určuje verzi rozhraní .NET, na kterou aplikace cílí. Tato možnost může mít různé hodnoty v závislosti na tom, které verze rozhraní .NET jsou nainstalovány v počítači.

Pro .NET Framework projekty je výchozí hodnota shodná s cílovou architekturou, kterou jste zadali při vytváření projektu.

Pro projekt, který cílí na .NET Core, mohou být dostupné verze následující:

![Cílové verze rozhraní pro projekt .NET Core](../media/application-target-framework.png)

> [!NOTE]
> Požadované balíčky uvedené v [dialogovém okně požadavky](../../ide/reference/prerequisites-dialog-box.md) se nastaví automaticky při prvním otevření dialogového okna. Pokud následně změníte cílovou architekturu projektu, je nutné vybrat požadované součásti ručně, aby odpovídaly novému cílovému rozhraní.

Další informace najdete v tématu [Přehled cílení na rozhraní](../../ide/visual-studio-multi-targeting-overview.md).

**Typ výstupu**

Určuje typ aplikace, která se má sestavit. Hodnoty se liší v závislosti na typu projektu. Například pro projekt **konzolové** aplikace můžete jako výstupní typ zadat **aplikaci systému Windows**, **konzolovou aplikaci**nebo **knihovnu tříd** .

Pro projekt webové aplikace je nutné zadat **knihovnu tříd**.

Další informace o vlastnosti **výstupního typu** naleznete v tématu [/target (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).

Informace o tom, jak získat přístup k této vlastnosti prostřednictvím kódu programu, najdete v tématu <xref:VSLangProj.ProjectProperties.OutputType%2A>.

**Automaticky generovat přesměrování vazby**

Přesměrování vazby jsou přidána do projektu, pokud vaše aplikace nebo její součásti odkazují na více než jednu verzi stejného sestavení. Chcete-li v souboru projektu definovat přesměrování vazby ručně, zrušte výběr **automatického generování přesměrování vazby**.

Další informace o přesměrování naleznete v tématu [přesměrovávání verzí sestavení](/dotnet/framework/configure-apps/redirect-assembly-versions).

**Spouštěcí objekt**

Definuje vstupní bod, který se má volat při načtení aplikace. Obecně je tato možnost nastavena buď na hlavní formulář v aplikaci, nebo na `Main` postup, který by se měl spustit při spuštění aplikace. Vzhledem k tomu, že knihovny tříd nemají vstupní bod, je jejich jediná možnost pro tuto vlastnost **(nenastavená)** .

Ve výchozím nastavení je v projektu aplikace WPF Tato možnost nastavená na **(Nenastaveno)** . Druhá možnost je \[ProjectName]. app. V projektu WPF musíte nastavit spouštěcí identifikátor URI pro načtení prostředku uživatelského rozhraní při spuštění aplikace. Provedete to tak, že v projektu otevřete soubor *Application. XAML* a vlastnost `StartupUri` nastavíte na soubor *. XAML* v projektu, jako je například *Window1. XAML*. Seznam přijatelných kořenových elementů naleznete v tématu <xref:System.Windows.Application.StartupUri%2A>. Musíte také definovat metodu `public static void Main()` třídy v projektu. Tato třída se zobrazí v seznamu **spouštěcích objektů** jako *ProjectName. ClassName*. Pak můžete vybrat třídu jako spouštěcí objekt.

Další informace naleznete v tématu [/Main (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) . Chcete-li získat přístup k této vlastnosti programově, přečtěte si téma <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

**Informace o sestavení**

Toto tlačítko otevře dialogové okno [informace o sestavení](../../ide/reference/assembly-information-dialog-box.md) .

## <a name="resources"></a>Prostředky

Možnosti **prostředků** vám pomůžou nakonfigurovat nastavení prostředků pro vaši aplikaci.

**Ikona a manifest**

Ve výchozím nastavení je tento přepínač vybraný a jsou povolené **ikony** a možnosti **manifestu** . To vám umožní vybrat si vlastní ikonu nebo vybrat jiné možnosti generování manifestu. Pokud pro projekt neposkytnete soubor prostředků, ponechte tento přepínač vybraný.

**Ikona**

Nastaví soubor *. ico* , který chcete použít jako ikonu programu. Klikněte na tlačítko **Procházet** a vyhledejte existující grafiku nebo zadejte požadovaný název souboru. Další informace naleznete v tématu [/win32icon (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option) .

Chcete-li získat přístup k této vlastnosti programově, přečtěte si téma <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

Informace o vytvoření ikony najdete v tématu [Editor obrázků pro ikony](/cpp/windows/image-editor-for-icons).

**Manifest**

Vybere možnost generování manifestu, pokud je aplikace spuštěna v systému Windows Vista pod nástrojem Řízení uživatelských účtů (UAC). Tato možnost může mít následující hodnoty:

- **Vloží manifest s výchozími nastaveními**. Podporuje typický způsob, jakým aplikace Visual Studio funguje v systému Windows Vista, což znamená vložení informací o zabezpečení do spustitelného souboru aplikace. tím se určí, že `requestedExecutionLevel` být `AsInvoker`. Toto je výchozí možnost.

- **Vytvořit aplikaci bez manifestu** Tato metoda se označuje jako *virtualizace*. Tato možnost slouží k zajištění kompatibility se staršími aplikacemi.

- **Properties\app.manifest**. Tato možnost je vyžadována pro aplikace nasazené pomocí technologie ClickOnce nebo bez registrace modelu COM. Pokud publikujete aplikaci pomocí nasazení ClickOnce, **manifest** je automaticky nastaven na tuto možnost.

**Soubor prostředků**

Vyberte tento přepínač při poskytování souboru prostředků pro projekt. Výběrem této možnosti zakážete **ikonu** a možnosti **manifestu** .

Zadejte název cesty nebo použijte tlačítko Procházet ( **...** ) a přidejte soubor prostředků Win32 do projektu.

Další informace najdete v tématu [vytvoření souborů prostředků pro aplikace .NET](/dotnet/framework/resources/creating-resource-files-for-desktop-apps).
