---
title: Stránka aplikace vlastností projektu VB
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
ms.openlocfilehash: fe303f86b282e7e803dacc1dd8f4d3c1d6b72121
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595810"
---
# <a name="application-page-project-designer-visual-basic"></a>Stránka Aplikace, návrhář projektu (Visual Basic)

Na stránce **Aplikace** Návrháře projektu můžete určit nastavení a vlastnosti aplikace projektu.

Chcete-li získat přístup ke stránce **Aplikace,** zvolte uzel projektu (nikoli uzel **řešení)** v **Průzkumníku řešení**. Pak na řádku nabídek zvolte**Vlastnosti** **projektu.** >  Po zobrazení **Návrháře projektů** vyberte kartu **Aplikace.**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Obecná nastavení aplikace

Následující možnosti umožňují konfigurovat obecné nastavení aplikace.

### <a name="assembly-name"></a>Název sestavení

Určuje název výstupního souboru, který bude obsahovat manifest sestavení. Pokud změníte tuto vlastnost, změní se také vlastnost **Výstupní název.**

Můžete také zadat název výstupního souboru z příkazového řádku pomocí přepínače kompilátoru [/out (Visual Basic).](/dotnet/visual-basic/reference/command-line-compiler/out)

Informace o tom, jak programově přistupovat k této vlastnosti, naleznete v tématu <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

### <a name="root-namespace"></a>Kořenový obor názvů

Určuje základní obor názvů pro všechny soubory v projektu. Pokud například nastavíte **kořenový obor názvů** `Project1` a máte `Class1` mimo libovolný obor názvů v `Project1.Class1`kódu, bude jeho obor názvů . Pokud máte `Class2` v oboru `Order` názvů v kódu, jeho `Project1.Order.Class2`obor názvů by .

Pokud zrušete **kořenový obor názvů**, můžete určit strukturu oboru názvů projektu v kódu.

> [!NOTE]
> Pokud použijete `Global` klíčové slovo v [prohlášení oboru názvů](/dotnet/visual-basic/language-reference/statements/namespace-statement), můžete definovat obor názvů z kořenového oboru názvů projektu. Pokud zrušete **kořenový obor názvů**, `Global` stane se oborem názvů `Global` nejvyšší `Namespace` úrovně, který odstraní potřebu klíčového slova v příkazu. Další informace naleznete v tématu Global Keyword in Namespace Statements v [části Obory názvů v jazyce Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces).

Informace o vytváření oborů názvů v kódu naleznete v [tématu Prohlášení oboru názvů](/dotnet/visual-basic/language-reference/statements/namespace-statement).

Další informace o vlastnosti kořenového oboru názvů naleznete v tématu [/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace).

Informace o tom, jak programově přistupovat k této vlastnosti, naleznete v tématu <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

### <a name="target-framework-all-configurations"></a>Cílový rámec (všechny konfigurace)

Určuje verzi rozhraní .NET, na kterou se aplikace zaměřuje. Tato možnost může mít různé hodnoty v závislosti na tom, které verze rozhraní .NET jsou v počítači nainstalovány.

U projektů rozhraní .NET Framework se výchozí hodnota shoduje s cílovým rámcem, který jste zadali při vytváření projektu.

> [!NOTE]
> Balíčky požadavků, které jsou uvedeny v [dialogovém okně Požadavky,](../../ide/reference/prerequisites-dialog-box.md) jsou nastaveny automaticky při prvním otevření dialogového okna. Pokud následně změníte cílové rozhraní projektu, je nutné zadat požadavky ručně tak, aby odpovídaly nové cílové rozhraní.

Další informace naleznete v [tématu Přehled cílení na rozhraní Framework](../../ide/visual-studio-multi-targeting-overview.md).

### <a name="application-type"></a>Typ aplikace

Určuje typ aplikace, která má být vytvářena. Hodnoty se liší v závislosti na typu projektu. Například pro projekt **aplikace Windows Forms App** můžete zadat aplikace Windows **Forms**, **Knihovna tříd**, **Konzolová aplikace**, Služba **systému Windows**nebo **Knihovna webových ovládacích prvku**.

Pro projekt webové aplikace je nutné zadat **knihovnu tříd**.

Další informace o vlastnosti **Typu aplikace** naleznete v tématu [/target (Visual Basic).](/dotnet/visual-basic/reference/command-line-compiler/target) Informace o tom, jak k této <xref:VSLangProj.ProjectProperties.OutputType%2A>vlastnosti přistupovat programově, naleznete v tématu .

### <a name="auto-generate-binding-redirects"></a>Automaticky generovat přesměrování vazeb

Přesměrování vazeb se přidají do projektu, pokud vaše aplikace nebo její součásti odkazují na více než jednu verzi stejného sestavení. Pokud chcete ručně definovat přesměrování vazeb v souboru projektu, zrušte výběr **automatických generování přesměrování vazeb**.

Další informace o přesměrování naleznete v [tématu Přesměrování verzí sestavení](/dotnet/framework/configure-apps/redirect-assembly-versions).

### <a name="startup-form--startup-object--startup-uri"></a>Spouštěcí formulář / Spouštěcí objekt / Spouštěcí identifikátor URI

Určuje spouštěcí formulář nebo vstupní bod aplikace.

Pokud je **vybrána možnost Povolit rozhraní aplikace** (výchozí), tento seznam se nazývá **Spouštěcí formulář** a zobrazuje pouze formuláře, protože rozhraní aplikace podporuje pouze spouštěcí formuláře, nikoli objekty.

Pokud se jedná o aplikaci prohlížeče WPF, tento seznam se nazývá **Identifikátor URI spuštění**a výchozí je **Page1.xaml**. Seznam **Identifikátor URI při spuštění** umožňuje zadat prostředek uživatelského rozhraní (prvek XAML), který aplikace zobrazí při spuštění aplikace. Další informace naleznete v tématu <xref:System.Windows.Application.StartupUri%2A>.

Pokud **povolit rozhraní aplikace** není zaškrtnuto, tento seznam se stane **objektem Po spuštění** a zobrazí formuláře a třídy nebo moduly s . `Sub Main`

**Spouštěcí objekt** definuje vstupní bod, který má být volán při načtení aplikace. Obecně je to nastaveno na hlavní formulář `Sub Main` v aplikaci nebo na postup, který by měl být spuštěn při spuštění aplikace. Vzhledem k tomu, že knihovny tříd nemají vstupní bod, jejich jedinou možností pro tuto vlastnost je **(Žádný)**. Další informace naleznete v tématu [/main](/dotnet/visual-basic/reference/command-line-compiler/main). Chcete-li získat přístup k <xref:VSLangProj.ProjectProperties.StartupObject%2A>této vlastnosti programově, naleznete v tématu .

### <a name="icon"></a>Ikona

Nastaví soubor .ico, který chcete použít jako ikonu programu. Vyberte ** \<Procházet... >** a vyhledejte existující grafiku. Viz [/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) (nebo [/win32icon (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)) další informace. Chcete-li získat přístup k <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>této vlastnosti programově, naleznete v tématu .

### <a name="assembly-information"></a>Informace o sestavení

Klepnutím na toto tlačítko zobrazíte [dialogové okno Informace o sestavě](../../ide/reference/assembly-information-dialog-box.md).

### <a name="enable-application-framework"></a>Povolit architekturu aplikace

Určuje, zda bude projekt používat rozhraní aplikace. Nastavení této možnosti ovlivní možnosti dostupné v**objektu Po** **spuštění**/.

Pokud je toto políčko zaškrtnuto, aplikace používá standard `Sub Main`. Zaškrtnutím tohoto políčka povolíte funkce v části **Vlastnosti rozhraní aplikace systému Windows** a také vyberete spouštěcí formulář.

Pokud toto políčko není zaškrtnuto, `Sub Main` aplikace použije vlastní nastavení, které jste zadali ve **formuláři Po spuštění**. V takovém případě můžete zadat buď spouštěcí `Sub Main` objekt (vlastní v metodě nebo ve třídě) nebo formulář. Možnosti v části **vlastnosti rozhraní aplikace systému Windows** také nebudou k dispozici.

### <a name="view-windows-settings"></a>Zobrazení nastavení systému Windows

Klepnutím na toto tlačítko vygenerujete a otevřete soubor *app.manifest.* Visual Studio používá tento soubor ke generování dat manifestu pro aplikaci. Potom nastavte úroveň požadovaného spuštění nástroj `<requestedExecutionLevel>` řízení o řízení pomocí a upravte značku v *aplikaci app.manifest* takto:

`<requestedExecutionLevel level="asInvoker" />`

ClickOnce pracuje s `asInvoker` úrovní nebo v virtualizovaném režimu (bez generování manifestu). Chcete-li určit virtualizovaný režim, odeberte celou značku z app.manifest.

Další informace o generování manifestu naleznete v [tématu ClickOnce Deployment on Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Vlastnosti architektury aplikace systému Windows

Následující nastavení jsou k dispozici v části **vlastnosti rozhraní aplikace systému Windows.** Tyto možnosti jsou k dispozici pouze v případě, že je zaškrtnuto políčko **Povolit rozhraní aplikace.**

> [!TIP]
> Následující část popisuje nastavení **vlastností rozhraní aplikace systému Windows** specifické pro aplikace WPF (Windows Presentation Foundation).

### <a name="enable-xp-visual-styles"></a>Povolení vizuálních stylů XP

Povolí nebo zakáže vizuální styly systému Windows XP, známé také jako *motivy systému Windows XP*. Vizuální styly systému Windows XP umožňují například ovládací prvky se zaoblenými rohy a dynamickými barvami. Výchozí nastavení je povoleno.

### <a name="make-single-instance-application"></a>Vytvořit aplikaci pro jednu instanci

Zaškrtnutím tohoto políčka zabráníte uživatelům ve spuštění více instancí aplikace. Výchozí nastavení tohoto políčka není *zaškrtnuto*, což umožňuje spuštění více instancí aplikace. Další informace naleznete <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> na události.

### <a name="save-mysettings-on-shutdown"></a>Uložit my.nastavení při vypnutí

Zaškrtnutím tohoto políčka určíte, že `My.Settings` nastavení aplikace se uloží, když uživatelé vypnou své počítače. Výchozí nastavení je povoleno. Pokud je tato možnost zakázána, můžete nastavení `My.Settings.Save`aplikace uložit ručně voláním .

### <a name="authentication-mode"></a>Režim ověřování

Výběrem **možnosti Systém windows** (výchozí) určete použití ověřování systému Windows k identifikaci aktuálně přihlášeného uživatele. Tyto informace můžete načíst za `My.User` běhu pomocí objektu. Vyberte **definované aplikace,** pokud budete poskytovat svůj vlastní kód k ověření uživatelů namísto použití výchozímetody ověřování systému Windows.

### <a name="shutdown-mode"></a>Režim vypnutí

Výběrem **možnosti Při zavření spouštěcího formuláře** (výchozího) určete, že ukončení aplikace při zavření formuláře jako spouštěcího formuláře, a to i v případě, že jsou otevřeny jiné formuláře. Vyberte **Při zavření posledního formuláře** určete, že ukončení `My.Application.Exit` aplikace `End` při zavření posledního formuláře nebo při explicitním volání příkazu.

Chcete-li určit, že aplikace bude ukončena explicitně , `Shutdown`vyberte možnost Při **explicitním vypnutí.**

Výběrem **možnosti Při posledním okně v blízkosti** určete, že `Shutdown`aplikace ukončí, když se zavře poslední okno nebo když explicitně zavoláte . Toto je výchozí nastavení.

Vyberte **V hlavním okně zavřít** určit, že aplikace ukončit při `Shutdown`zavření hlavního okna nebo při explicitním volání .

### <a name="splash-screen"></a>Úvodní obrazovka

Vyberte formulář, který chcete použít jako úvodní obrazovku. Pomocí formuláře nebo šablony musíte již dříve vytvořit úvodní obrazovku. Výchozí hodnota je **(Žádný).**

### <a name="view-application-events"></a>Zobrazit události aplikace

Klepnutím na toto tlačítko zobrazíte soubor kódu událostí, ve `Startup` `Shutdown`kterém `UnhandledException` `StartupNextInstance` můžete `NetworkAvailabilityChanged`psát události pro události rozhraní aplikace , , a . Můžete také přepsat určité metody architektury aplikace. Můžete například změnit chování zobrazení úvodní obrazovky přepsáním `OnInitialize`.

## <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-apps"></a>Vlastnosti architektury aplikací systému Windows pro aplikace WPF (Windows Presentation Foundation)

Následující nastavení jsou k dispozici v části **vlastnosti rozhraní aplikace systému Windows,** pokud je projekt aplikace WPF (Windows Presentation Foundation). Tyto možnosti jsou k dispozici pouze v případě, že je zaškrtnuto políčko **Povolit rozhraní aplikace.** Možnosti uvedené v této tabulce jsou k dispozici pouze pro aplikace prohlížeče WPF nebo WPF. Nejsou k dispozici pro uživatelské ovládací prvek WPF nebo knihovny vlastního ovládacího prvku.

### <a name="shutdown-mode"></a>Režim vypnutí

Tato vlastnost je použitelná pouze pro aplikace WPF (Windows Presentation Foundation).

Chcete-li určit, že aplikace bude ukončena explicitně , <xref:System.Windows.Application.Shutdown%2A>vyberte možnost Při **explicitním vypnutí.**

Výběrem **možnosti Při posledním okně v blízkosti** určete, že <xref:System.Windows.Application.Shutdown%2A>aplikace ukončí, když se zavře poslední okno nebo když explicitně zavoláte . Toto je výchozí nastavení.

Vyberte **V hlavním okně zavřít** určit, že aplikace ukončit při <xref:System.Windows.Application.Shutdown%2A>zavření hlavního okna nebo při explicitním volání .

Další informace o použití tohoto nastavení naleznete v tématu<xref:System.Windows.Application.Shutdown%2A>

### <a name="edit-xaml"></a>Upravit XAML

Toto tlačítko otevře soubor definice aplikace (Application.xaml) v editoru XAML. Po klepnutí na toto tlačítko se *soubor Application.xaml* otevře v uzlu definice aplikace. Tento soubor bude pravděpodobně třeba upravit, abyste mohli provádět určité úkoly, například definovat zdroje. Pokud soubor definice aplikace neexistuje, Návrhář projektu jej vytvoří.

### <a name="view-application-events"></a>Zobrazit události aplikace

Toto tlačítko `Application` otevře soubor třídy (*Application.xaml.vb*) v editoru kódu. Pokud soubor neexistuje, Návrhář projektu vytvoří jeden s příslušným názvem třídy a oborem názvů.

Objekt <xref:System.Windows.Application> vyvolá události, když dojde k určitým změnám stavu aplikace (například při spuštění nebo vypnutí aplikace). Úplný seznam událostí, které tato třída zveřejňuje, naleznete v tématu <xref:System.Windows.Application>. Tyto události jsou zpracovány v `Application` části uživatelského kódu částečné třídy.
