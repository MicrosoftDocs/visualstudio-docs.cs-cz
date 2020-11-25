---
title: Stránka aplikace – vlastnosti projektu VB
description: Naučte se používat stránku aplikace Návrháře projektu Visual Basic k určení nastavení a vlastností aplikace projektu.
ms.custom: SEO-VS-2020
ms.date: 10/30/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 675c3fbaaf1a3e49648befebca4927299649b057
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871415"
---
# <a name="application-page-project-designer-visual-basic"></a>Stránka Aplikace, návrhář projektu (Visual Basic)

Použijte stránku **aplikace** Návrháře projektu k určení nastavení aplikace a vlastností projektu.

Pro přístup ke stránce **aplikace** vyberte uzel projektu (nikoli uzel **řešení** ) v **Průzkumník řešení**. Pak zvolte **Project**  >  **vlastnosti** projektu na řádku nabídek. Když se zobrazí **Návrhář projektu** , vyberte kartu **aplikace** .

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Obecné nastavení aplikace

Následující možnosti umožňují nakonfigurovat obecná nastavení pro aplikaci.

### <a name="assembly-name"></a>Název sestavení

Určuje název výstupního souboru, který bude obsahovat manifest sestavení. Změníte-li tuto vlastnost, změní se také vlastnost **Název výstupu** .

Můžete také zadat název výstupního souboru z příkazového řádku pomocí přepínače kompilátoru [/out (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/out) .

Informace o tom, jak získat přístup k této vlastnosti prostřednictvím kódu programu, najdete v tématu <xref:VSLangProj.ProjectProperties.AssemblyName%2A> .

### <a name="root-namespace"></a>Kořenový obor názvů

Určuje základní obor názvů pro všechny soubory v projektu. Například pokud nastavíte **kořenový obor názvů** na `Project1` a máte `Class1` mimo libovolný obor názvů v kódu, jeho obor názvů by byl `Project1.Class1` . Pokud máte `Class2` v oboru názvů `Order` v kódu, jeho obor názvů by byl `Project1.Order.Class2` .

Pokud vymažete **kořenový obor názvů**, můžete zadat strukturu oboru názvů projektu v kódu.

> [!NOTE]
> Použijete-li `Global` klíčové slovo v [příkazu oboru názvů](/dotnet/visual-basic/language-reference/statements/namespace-statement), můžete definovat obor názvů mimo kořenový obor názvů vašeho projektu. Pokud smažete **kořenový obor názvů**, `Global` dojde k oboru názvů nejvyšší úrovně, který `Global` v příkazu odstraní klíčové slovo nutnost `Namespace` . Další informace najdete v části "globální klíčové slovo v příkazech oboru názvů" v tématu [obory názvů v Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces).

Informace o tom, jak vytvořit obory názvů v kódu, naleznete v tématu [Namespace Statement](/dotnet/visual-basic/language-reference/statements/namespace-statement).

Další informace o vlastnosti kořenového oboru názvů naleznete v tématu [/RootNamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace).

Informace o tom, jak získat přístup k této vlastnosti prostřednictvím kódu programu, najdete v tématu <xref:VSLangProj.ProjectProperties.RootNamespace%2A> .

### <a name="target-framework-all-configurations"></a>Cílová architektura (všechny konfigurace)

Určuje verzi rozhraní .NET, na kterou aplikace cílí. Tato možnost může mít různé hodnoty v závislosti na tom, které verze rozhraní .NET jsou nainstalovány v počítači.

Pro .NET Framework projekty je výchozí hodnota shodná s cílovou architekturou, kterou jste zadali při vytváření projektu.

> [!NOTE]
> Požadované balíčky uvedené v [dialogovém okně požadavky](../../ide/reference/prerequisites-dialog-box.md) se nastaví automaticky při prvním otevření dialogového okna. Pokud následně změníte cílovou architekturu projektu, je nutné zadat požadavky ručně, aby odpovídaly novému cílovému rozhraní.

Další informace najdete v tématu [Přehled cílení na rozhraní](../../ide/visual-studio-multi-targeting-overview.md).

### <a name="application-type"></a>Typ aplikace

Určuje typ aplikace, která se má sestavit. Hodnoty se liší v závislosti na typu projektu. Například pro projekt **model Windows Forms aplikace** můžete určit **model Windows Forms aplikace**, **knihovny tříd**, **Konzolová aplikace**, **službu systému Windows** nebo **knihovnu webového ovládacího prvku**.

Pro projekt webové aplikace je nutné zadat **knihovnu tříd**.

Další informace o vlastnosti **Typ aplikace** naleznete v tématu [/target (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/target). Informace o tom, jak tuto vlastnost přistupovat prostřednictvím kódu programu, najdete v tématu <xref:VSLangProj.ProjectProperties.OutputType%2A> .

### <a name="auto-generate-binding-redirects"></a>Automaticky generovat přesměrování vazby

Přesměrování vazby jsou přidána do projektu, pokud vaše aplikace nebo její součásti odkazují na více než jednu verzi stejného sestavení. Chcete-li v souboru projektu definovat přesměrování vazby ručně, zrušte výběr **automatického generování přesměrování vazby**.

Další informace o přesměrování naleznete v tématu [přesměrovávání verzí sestavení](/dotnet/framework/configure-apps/redirect-assembly-versions).

### <a name="startup-form--startup-object--startup-uri"></a>Spouštěcí formulář/spouštěcí objekt/spouštěcí identifikátor URI

Určuje spouštěcí formulář nebo vstupní bod aplikace.

Pokud je vybrána **možnost Povolit aplikační rozhraní** (výchozí), tento seznam má hodnotu " **úvodní formulář** " a zobrazuje pouze formuláře, protože aplikační rozhraní podporuje pouze formuláře po spuštění, nikoli objekty.

Pokud se jedná o aplikaci prohlížeče WPF, tento seznam má hodnotu **spouštěcí identifikátor URI** a výchozí hodnota je **Page1. XAML**. Seznam **spouštěcích identifikátorů URI** umožňuje zadat prostředek uživatelského rozhraní (prvek XAML), který aplikace zobrazuje při spuštění aplikace. Další informace naleznete v tématu <xref:System.Windows.Application.StartupUri%2A>.

Pokud je zaškrtnuto políčko **Povolit rozhraní Application Framework** , tento seznam se zobrazí jako **spouštěcí objekt** a zobrazí jak formuláře, třídy, tak moduly s `Sub Main` příponou.

**Spouštěcí objekt** definuje vstupní bod, který má být volán při načtení aplikace. Obecně je tato možnost nastavena na hlavní formulář v aplikaci nebo na `Sub Main` postup, který by měl být spuštěn při spuštění aplikace. Vzhledem k tomu, že knihovny tříd nemají vstupní bod, je jejich jediná možnost pro tuto vlastnost **(žádná)**. Další informace najdete v tématu [/Main](/dotnet/visual-basic/reference/command-line-compiler/main). Chcete-li získat přístup k této vlastnosti programově, přečtěte si téma <xref:VSLangProj.ProjectProperties.StartupObject%2A> .

### <a name="icon"></a>Ikona

Nastaví soubor. ico, který chcete použít jako ikonu programu. Tuto možnost vyberte **\<Browse...>** , pokud chcete vyhledat existující grafiku. Další informace naleznete v tématu [/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) (nebo [/Win32icon (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)). Chcete-li získat přístup k této vlastnosti programově, přečtěte si téma <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A> .

### <a name="assembly-information"></a>Informace o sestavení

Kliknutím na toto tlačítko zobrazíte [dialogové okno informace o sestavení](../../ide/reference/assembly-information-dialog-box.md).

### <a name="enable-application-framework"></a>Povolit aplikační architekturu

Určuje, zda projekt bude používat aplikační rozhraní. Nastavení této možnosti má vliv na možnosti dostupné při spuštění **Startup form** / **spouštěcího objektu** formuláře.

Pokud je toto políčko zaškrtnuté, vaše aplikace používá standard `Sub Main` . Zaškrtnutí tohoto políčka povolí funkce v části **Vlastnosti rozhraní Windows Application Framework** a také vyžaduje, abyste vybrali úvodní formulář.

Pokud je toto políčko nezaškrtnuté, vaše aplikace používá vlastní `Sub Main` , které jste zadali ve **formuláři po spuštění**. V takovém případě můžete zadat spouštěcí objekt (vlastní `Sub Main` v metodě nebo třídě) nebo formulář. Také možnosti v oddílu **Vlastnosti aplikačního rozhraní systému Windows** nebudou k dispozici.

### <a name="view-windows-settings"></a>Zobrazit nastavení systému Windows

Kliknutím na toto tlačítko vygenerujete a otevřete soubor *App. manifest* . Visual Studio pomocí tohoto souboru generuje data manifestu aplikace. Potom nastavte pomocí `<requestedExecutionLevel>` značky v souboru *App. manifest* požadovanou úroveň spuštění nástroje řízení uživatelských účtů (UAC) následujícím způsobem:

`<requestedExecutionLevel level="asInvoker" />`

ClickOnce pracuje s úrovní `asInvoker` nebo ve virtualizovaném režimu (bez generování manifestu). Chcete-li zadat virtualizovaný režim, odeberte celou značku z App. manifest.

Další informace o generování manifestu naleznete v tématu [nasazení ClickOnce v systému Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Vlastnosti aplikačního rozhraní Windows

V části **Vlastnosti rozhraní Windows Application Framework** jsou k dispozici následující nastavení. Tyto možnosti jsou k dispozici pouze v případě, že je zaškrtnuto políčko **Povolit aplikační architekturu** .

> [!TIP]
> Následující část popisuje nastavení **vlastností aplikační architektury Windows** specifická pro Windows Presentation Foundation (WPF) aplikace.

### <a name="enable-xp-visual-styles"></a>Povolit vizuální styly XP

Povolí nebo zakáže vizuální styly systému Windows XP, označované také jako *motivy systému Windows XP*. Vizuální styly Windows XP umožňují například ovládací prvky s zaoblenými rohy a dynamickými barvami. Výchozí hodnota je povolena.

### <a name="make-single-instance-application"></a>Vytvoření aplikace s jedinou instancí

Zaškrtnutím tohoto políčka zabráníte uživatelům v spuštění více instancí aplikace. Výchozí nastavení pro toto zaškrtávací políčko není *zaškrtnuto*, což umožňuje spustit více instancí aplikace. Další informace najdete v tématu <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> událost.

### <a name="save-mysettings-on-shutdown"></a>Uložit My. Settings při vypnutí

Zaškrtnutím tohoto políčka určíte, že nastavení aplikace `My.Settings` budou uložena, když uživatelé vypnou své počítače. Výchozí nastavení je povoleno. Pokud je tato možnost zakázaná, můžete nastavení aplikace uložit ručně voláním `My.Settings.Save` .

### <a name="authentication-mode"></a>Režim ověřování

Vyberte možnost **Windows** (výchozí) a určete tak použití ověřování systému Windows k identifikaci aktuálně přihlášeného uživatele. Tyto informace lze načíst za běhu pomocí `My.User` objektu. Vyberte možnost **definováno aplikací** , pokud budete poskytovat vlastní kód pro ověřování uživatelů místo použití výchozích metod ověřování systému Windows.

### <a name="shutdown-mode"></a>Režim vypnutí

Vyberte, **když se zavře úvodní formulář** (výchozí) a určí, že se aplikace ukončí, když se zavře formulář, který se spustí po spuštění, i když jsou otevřené další formuláře. Vyberte, **když se zavře poslední formulář** , a určete tak, že se aplikace ukončí, když se zavře poslední formulář, nebo když `My.Application.Exit` `End` se příkaz explicitně zavolá.

Vyberte možnost **při explicitním vypnutí** , chcete-li určit, že se aplikace ukončí při explicitním volání `Shutdown` .

**V nabídce poslední okno vyberte Zavřít** a určete tak, že se aplikace ukončí při zavření posledního okna nebo když explicitně voláte `Shutdown` . Toto je výchozí nastavení.

**V nabídce hlavní okno vyberte Zavřít** a určete tak, že se aplikace ukončí při zavření hlavního okna nebo při explicitním volání `Shutdown` .

### <a name="splash-screen"></a>Úvodní obrazovka

Vyberte formulář, který chcete použít jako úvodní obrazovku. Předtím, než je třeba vytvořit úvodní obrazovku pomocí formuláře nebo šablony. Výchozí hodnota je **(žádné)**.

### <a name="view-application-events"></a>Zobrazit události aplikace

Kliknutím na toto tlačítko zobrazíte soubor s kódem událostí, ve kterém můžete zapisovat události pro události aplikační architektury `Startup` , `Shutdown` , `UnhandledException` `StartupNextInstance` a `NetworkAvailabilityChanged` . Můžete také přepsat určité metody aplikační architektury. Můžete například změnit chování při zobrazení úvodní obrazovky přepsáním `OnInitialize` .

## <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-apps"></a>Vlastnosti aplikační architektury Windows pro aplikace Windows Presentation Foundation (WPF)

Následující nastavení jsou k dispozici v oddílu **Vlastnosti rozhraní Windows Application Framework** , pokud je projekt aplikace Windows Presentation Foundation (WPF). Tyto možnosti jsou k dispozici pouze v případě, že je zaškrtnuto políčko **Povolit aplikační architekturu** . Možnosti uvedené v této tabulce jsou k dispozici pouze pro aplikace WPF nebo prohlížeč WPF. Nejsou k dispozici pro uživatelský ovládací prvek WPF ani pro knihovny vlastního ovládacího prvku.

### <a name="shutdown-mode"></a>Režim vypnutí

Tato vlastnost se vztahuje pouze na aplikace Windows Presentation Foundation (WPF).

Vyberte možnost **při explicitním vypnutí** , chcete-li určit, že se aplikace ukončí při explicitním volání <xref:System.Windows.Application.Shutdown%2A> .

**V nabídce poslední okno vyberte Zavřít** a určete tak, že se aplikace ukončí při zavření posledního okna nebo když explicitně voláte <xref:System.Windows.Application.Shutdown%2A> . Toto je výchozí nastavení.

**V nabídce hlavní okno vyberte Zavřít** a určete tak, že se aplikace ukončí při zavření hlavního okna nebo při explicitním volání <xref:System.Windows.Application.Shutdown%2A> .

Další informace o použití tohoto nastavení najdete v tématu. <xref:System.Windows.Application.Shutdown%2A>

### <a name="edit-xaml"></a>Upravit XAML

Toto tlačítko otevře soubor definice aplikace (Application. XAML) v editoru XAML. Po kliknutí na toto tlačítko se otevře *Application. XAML* v uzlu definice aplikace. Možná budete muset tento soubor upravit, aby se prováděly určité úlohy, například definování prostředků. Pokud soubor definice aplikace neexistuje, Návrhář projektu ho vytvoří.

### <a name="view-application-events"></a>Zobrazit události aplikace

Toto tlačítko otevře `Application` soubor třídy (*Application. XAML. vb*) v editoru kódu. Pokud soubor neexistuje, Návrhář projektu jej vytvoří s odpovídajícím názvem třídy a oborem názvů.

<xref:System.Windows.Application>Objekt vyvolá události, když dojde k určitým změnám stavu aplikace (například při spuštění nebo vypnutí aplikace). Úplný seznam událostí, které tato třída zpřístupňuje, naleznete v tématu <xref:System.Windows.Application> . Tyto události jsou zpracovávány v oddílu uživatelského kódu `Application` částečné třídy.
