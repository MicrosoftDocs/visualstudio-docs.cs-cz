---
title: Stránka aplikace vlastností projektu jazyka C#
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595823"
---
# <a name="application-page-project-designer-c"></a>Stránka Aplikace, návrhář projektu (C#)

Na stránce **Aplikace** **Návrháře projektu** můžete určit nastavení a vlastnosti aplikace projektu.

Chcete-li získat přístup ke stránce **Aplikace,** zvolte uzel projektu (nikoli uzel **řešení)** v **Průzkumníku řešení**. Pak na řádku nabídek zvolte**Vlastnosti** **projektu.** >  Po zobrazení **Návrháře projektů** klikněte na kartu **Aplikace.**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Obecné nastavení aplikace

Následující možnosti umožňují konfigurovat obecné nastavení aplikace.

**Název sestavení**

Určuje název výstupního souboru, který bude obsahovat manifest sestavení. Změna této vlastnosti také změní **vlastnost Výstupní název.**

Tuto změnu můžete také provést z příkazového řádku pomocí [/out (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).

Chcete-li získat přístup k <xref:VSLangProj.ProjectProperties.AssemblyName%2A>této vlastnosti programově, naleznete v tématu .

**Výchozí obor názvů**

Určuje základní obor názvů pro soubory přidané do projektu.

Další informace o vytváření oborů názvů v kódu naleznete v [oboru názvů.](/dotnet/csharp/language-reference/keywords/namespace)

Chcete-li získat přístup k <xref:VSLangProj.ProjectProperties.RootNamespace%2A>této vlastnosti programově, naleznete v tématu .

**Cílová architektura**

Určuje verzi rozhraní .NET, na kterou se aplikace zaměřuje. Tato možnost může mít různé hodnoty v závislosti na tom, které verze rozhraní .NET jsou v počítači nainstalovány.

U projektů rozhraní .NET Framework se výchozí hodnota shoduje s cílovým rámcem, který jste zadali při vytváření projektu.

U projektu, který cílí na jádro .NET Core, se dostupné verze mohou zobrazit následujícím způsobem:

![Cílové verze architektury pro projekt .NET Core](../media/application-target-framework.png)

> [!NOTE]
> Balíčky požadavků uvedené v [dialogovém okně Požadavky](../../ide/reference/prerequisites-dialog-box.md) jsou nastaveny automaticky při prvním otevření dialogového okna. Pokud následně změníte cílové rozhraní projektu, musíte ručně vybrat požadavky tak, aby odpovídaly nové cílové rozhraní.

Další informace naleznete v [tématu Přehled cílení na rozhraní Framework](../../ide/visual-studio-multi-targeting-overview.md).

**Typ výstupu**

Určuje typ aplikace, která má být vytvářena. Hodnoty se liší v závislosti na typu projektu. Například pro projekt **konzolové aplikace** můžete jako typ výstupu zadat **aplikaci systému Windows**, **konzolovou aplikaci**nebo **knihovnu tříd.**

Pro projekt webové aplikace je nutné zadat **knihovnu tříd**.

Další informace o vlastnosti **Output type** naleznete v tématu [/target (C# Compiler Options).](/dotnet/csharp/language-reference/compiler-options/target-compiler-option)

Informace o tom, jak programově přistupovat k této vlastnosti, naleznete v tématu <xref:VSLangProj.ProjectProperties.OutputType%2A>.

**Automaticky generovat přesměrování vazeb**

Přesměrování vazeb se přidají do projektu, pokud vaše aplikace nebo její součásti odkazují na více než jednu verzi stejného sestavení. Pokud chcete ručně definovat přesměrování vazeb v souboru projektu, zrušte výběr **automatických generování přesměrování vazeb**.

Další informace o přesměrování naleznete v [tématu Přesměrování verzí sestavení](/dotnet/framework/configure-apps/redirect-assembly-versions).

**Spouštěcí objekt**

Definuje vstupní bod, který má být volán při načtení aplikace. Obecně je to nastaveno buď na hlavní `Main` formulář v aplikaci nebo na postup, který by měl být spuštěn při spuštění aplikace. Vzhledem k tomu, že knihovny tříd nemají vstupní bod, jejich jedinou možností pro tuto vlastnost je **(Není nastaveno).**

Ve výchozím nastavení je tato možnost v projektu aplikace WPF nastavena na **hodnotu (Není nastavena).** Druhou možností \[je název projektu].App. V projektu WPF je nutné nastavit spouštěcí identifikátor URI tak, aby načítat prostředek ui při spuštění aplikace. Chcete-li to provést, otevřete soubor *Application.xaml* v projektu a nastavte `StartupUri` vlastnost na soubor *XAML* v projektu, například *Window1.xaml*. Seznam přijatelných kořenových prvků <xref:System.Windows.Application.StartupUri%2A>naleznete v tématu . Musíte také definovat `public static void Main()` metodu ve třídě v projektu. Tato třída se zobrazí v seznamu **objektů Po spuštění** jako *Název_třídy.* Potom můžete vybrat třídu jako spouštěcí objekt.

Další informace naleznete v tématu [/main (C# Compiler Options).](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) Chcete-li získat přístup k <xref:VSLangProj.ProjectProperties.StartupObject%2A>této vlastnosti programově, naleznete v tématu .

**Informace o sestavení**

Toto tlačítko otevře dialogové okno [Informace o sestavě.](../../ide/reference/assembly-information-dialog-box.md)

## <a name="resources"></a>Zdroje informací

Možnosti **zdroje** vám pomohou nakonfigurovat nastavení prostředků pro vaši aplikaci.

**Ikona a manifest**

Ve výchozím nastavení je toto přepínací tlačítko vybráno a jsou povoleny možnosti **Ikona** a **Manifest.** To umožňuje vybrat vlastní ikonu nebo vybrat různé možnosti generování manifestu. Toto přepínací tlačítko ponechejte vybrané, pokud neposkytujete soubor zdrojů pro projekt.

**Ikona:**

Nastaví soubor *.ico,* který chcete použít jako ikonu programu. Chcete-li vyhledat existující grafiku, klepněte na tlačítko **Procházet** nebo zadejte požadovaný název souboru. Další informace naleznete v tématu [/win32icon (C# Compiler Options).](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)

Chcete-li získat přístup k <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>této vlastnosti programově, naleznete v tématu .

Informace o vytvoření ikony naleznete v [tématu Image Editor for icons](/cpp/windows/image-editor-for-icons).

**Manifest**

Vybere možnost generování manifestu, když je aplikace spuštěna v systému Windows Vista v části Řízení uživatelských účtů (UAC). Tato možnost může mít následující hodnoty:

- **Vložit manifest s výchozím nastavením**. Podporuje typický způsob, jakým visual studio pracuje v systému Windows Vista, který je vložit informace `requestedExecutionLevel` o `AsInvoker`zabezpečení do spustitelného souboru aplikace, určení, které mají být . Toto je výchozí možnost.

- **Vytvořte aplikaci bez manifestu**. Tato metoda se označuje jako *virtualizace*. Tuto možnost použijte pro kompatibilitu s dřívějšími aplikacemi.

- **Vlastnosti\manifest aplikace**. Tato možnost je vyžadována pro aplikace nasazené clickonce nebo registrace bez COM. Pokud publikujete aplikaci pomocí nasazení ClickOnce, **manifest** je automaticky nastavena na tuto možnost.

**Soubor prostředků**

Toto přepínací tlačítko vyberte, pokud poskytujete soubor zdrojů pro projekt. Výběrem této možnosti zakážete možnosti **Ikona** a **Manifest.**

Zadejte název cesty nebo pomocí tlačítka Procházet (**...**) přidejte do projektu soubor prostředků Win32.

Další informace naleznete v [tématu Vytváření souborů prostředků pro aplikace .NET](/dotnet/framework/resources/creating-resource-files-for-desktop-apps).
