---
title: Stránky aplikace C# vlastnosti projektu
ms.date: 10/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6ac755bfab72a2e87b652bfb92d3343b46ff45dc
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672818"
---
# <a name="application-page-project-designer-c"></a>Stránka Aplikace, návrhář projektu (C#)

Použití **aplikace** stránku **Návrháře projektu** k určení nastavení aplikace a vlastnosti projektu.

Pro přístup k **aplikace** zvolte uzel projektu (ne **řešení** uzlu) v **Průzkumníka řešení**. Klikněte na tlačítko **projektu** > **vlastnosti** na řádku nabídek. Když **Návrháře projektu** se zobrazí, klikněte na tlačítko **aplikace** kartu.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Obecné nastavení aplikace

Tyto možnosti umožňují nakonfigurovat obecná nastavení pro aplikaci.

**Název sestavení**

Určuje název výstupního souboru, který bude obsahovat manifest sestavení. Změna této vlastnosti změní také **název výstupního** vlastnost.

Tuto změnu z příkazového řádku můžete také provést pomocí [/out (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).

Programový přístup k této vlastnosti, najdete v článku <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**výchozí obor názvů**

Určuje základní obor názvů pro soubory přidané do projektu.

Zobrazit [obor názvů](/dotnet/csharp/language-reference/keywords/namespace) pro další informace o vytváření oborů názvů ve vašem kódu.

Programový přístup k této vlastnosti, najdete v článku <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Cílová architektura**

Určuje verzi rozhraní .NET Framework, který aplikace cílí. Tato možnost může mít různé hodnoty v závislosti na nainstalovaných verzí rozhraní .NET Framework v počítači.

Výchozí hodnota je stejná jako Cílová architektura, kterou jste vybrali v **nový projekt** dialogové okno.

> [!NOTE]
> Požadované balíčky uvedené v [dialogové okno požadavky](../../ide/reference/prerequisites-dialog-box.md) se nastaví automaticky při prvním otevření dialogu. Pokud později změníte cílový rámec projektu, je třeba vybrat předpoklady ručně, aby odpovídaly novému cílovému rozhraní.

Další informace najdete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) a [Visual Studio přehled multiplatformního zacílení](../../ide/visual-studio-multi-targeting-overview.md).

**Typ výstupu**

Určuje typ aplikace k sestavení. Hodnoty se liší v závislosti na typu projektu. Třeba **konzolovou aplikaci** projektu, můžete zadat **aplikace Windows**, **konzolovou aplikaci**, nebo **knihovny tříd** jako Typ výstupu.

Pro projekt webové aplikace, je nutné zadat **knihovny tříd**.

Další informace o **typ výstupu** vlastnost, naleznete v tématu [/target (C# – možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).

Informace o tom, jak programově přístup k této vlastnosti naleznete v tématu <xref:VSLangProj.ProjectProperties.OutputType%2A>.

**Automaticky generovat přesměrování vazby**

Přesměrování vazby jsou přidány do projektu, pokud vaše aplikace nebo její součásti odkazují na více verzí stejného sestavení. Pokud chcete ručně definovat přesměrování vazby v souboru projektu, zrušte zaškrtnutí možnosti **generovat automatické přesměrování vazby**. Toto zaškrtávací políčko byla zavedena v sadě Visual Studio 2017 verze 15.7.

Další informace o přesměrování najdete v tématu [přesměrování verze sestavení](/dotnet/framework/configure-apps/redirect-assembly-versions).

**Spouštěcí objekt**

Definuje vstupní bod, který bude volán při načtení aplikace. Obvykle je tato možnost nastavená buď hlavního formuláře v aplikaci nebo na `Main` proceduru, která se má spustit při spuštění aplikace. Vzhledem k tomu, že nemá vstupní bod knihovny tříd, jejich jedinou možností pro tuto vlastnost je **(Nenastaveno)**.

Ve výchozím nastavení v rámci projektu aplikace WPF, je tato možnost nastavená na **(Nenastaveno)**. Další možností je \[názevprojektu] .app. V rámci projektu WPF musíte nastavit počáteční identifikátor URI pro načtení prostředku uživatelského rozhraní při spuštění aplikace. Chcete-li to provést, otevřete *Application.xaml* souboru ve vašem projektu a nastavit `StartupUri` vlastnost *.xaml* souborů ve vašem projektu, jako například *Window1.xaml*. Seznam prvků přijatelný kořenový najdete v tématu <xref:System.Windows.Application.StartupUri%2A>. Musíte také definovat `public static void Main()` metody ve třídě v projektu. Tato třída se objeví v **spouštěcí objekt** jako seznam *ProjectName.ClassName*. Pak můžete vybrat třídu jako spouštěcí objekt.

Zobrazit [/Main (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) Další informace. Programový přístup k této vlastnosti, najdete v článku <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

**Informace o sestavení**

Toto tlačítko otevře [informace o sestavení](../../ide/reference/assembly-information-dialog-box.md) dialogové okno.

## <a name="resources"></a>Prostředky

**Prostředky** možnosti vám pomohou nakonfigurovat nastavení prostředků pro vaši aplikaci.

**Ikona a manifest**

Ve výchozím nastavení, je přepínač vybrán a **ikonu** a **Manifest** aktivnují možnosti. To umožňuje vybrat vlastní ikona nebo vyberte jiný generování manifestu možnosti. Nechte tento přepínač vybrat, pokud zadáváte soubor prostředků pro projekt.

**Ikona**

Nastaví *.ico* soubor, který chcete použít jako ikona programu. Klikněte na tlačítko **Procházet** k vyhledání existujícího obrázku nebo zadejte název souboru, který chcete. Zobrazit [/win32icon (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option) Další informace.

Programový přístup k této vlastnosti, najdete v článku <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

**Manifest**

Vybere možnost generování manifestu, když je aplikace spuštěná v systému Windows Vista v rámci řízení uživatelských účtů (UAC). Tato možnost může mít následující hodnoty:

- **Vložit manifest s výchozím nastavením**. Podporuje typické způsobem, ve kterém aplikace Visual Studio pracuje na Windows Vista, který je pro vložení informací o zabezpečení ve spustitelném souboru aplikace, určení, že `requestedExecutionLevel` být `AsInvoker`. Toto je výchozí možnost.

- **Vytvořit aplikaci bez manifestu**. Tato metoda se označuje jako *virtualizace*. Tuto možnost použijte, pokud z důvodu kompatibility s dřívějšími aplikacemi.

- **Properties\app.manifest**. Tato možnost je vyžadována pro aplikace nasazené pomocí technologie ClickOnce nebo bez registrace modelu COM Pokud publikujete třeba aplikaci pomocí nasazení ClickOnce **Manifest** se automaticky nastaví na tuto možnost.

**Soubor prostředků**

Když zadáváte soubor prostředků pro projekt, vyberte přepínač. Výběrem této možnosti zakáže **ikonu** a **Manifest** možnosti.

Zadejte název cesty nebo klikněte na tlačítko Procházet (**...** ) Chcete-li přidat soubor prostředků Win32 do projektu.