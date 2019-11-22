---
title: Stránka aplikace, Návrhář projektu (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: 8cec9fea-cd92-47ff-88dd-7c928f0b4a74
caps.latest.revision: 68
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ca14cead3b632cb70b817c79fce797078c7069b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299385"
---
# <a name="application-page-project-designer-visual-basic"></a>Stránka Aplikace, návrhář projektu (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Použijte stránku **aplikace** Návrháře projektu k určení nastavení aplikace a vlastností projektu.

 Pro přístup ke stránce **aplikace** vyberte uzel projektu (nikoli uzel **řešení** ) v **Průzkumník řešení**. Pak zvolte **projekt**, **vlastnosti** na řádku nabídek. Když se zobrazí Návrhář projektu, klikněte na kartu **aplikace** .

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="general-application-settings"></a>Obecné nastavení aplikace
 Následující možnosti umožňují nakonfigurovat obecná nastavení pro aplikaci.

 **Název sestavení** Určuje název výstupního souboru, který bude obsahovat manifest sestavení. Změníte-li tuto vlastnost, změní se také vlastnost **Název výstupu** . Tuto změnu můžete provést také na příkazovém řádku pomocí [/out (Visual Basic)](https://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae). Informace o tom, jak získat přístup k této vlastnosti prostřednictvím kódu programu, najdete v tématu <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

 **Kořenový obor názvů** Určuje základní obor názvů pro všechny soubory v projektu. Například pokud nastavíte **kořenový obor názvů** na `Project1` a máte `Class1` mimo libovolný obor názvů v kódu, jeho obor názvů by byl `Project1.Class1`. Pokud máte `Class2` v oboru názvů `Order` v kódu, jeho obor názvů by byl `Project1.Order.Class2`.

 Pokud vymažete **kořenový obor názvů**, můžete zadat strukturu oboru názvů projektu v kódu.

> [!NOTE]
> Použijete-li klíčové slovo Global v [příkazu oboru názvů](https://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2), můžete definovat obor názvů mimo kořenový obor názvů vašeho projektu. Pokud vymažete **kořenový obor názvů**, `Global` se zobrazí jako obor názvů nejvyšší úrovně, který v příkazu `Namespace` odstraní klíčová slova nutnost `Global`. Další informace najdete v části "globální klíčové slovo v příkazech oboru názvů" v tématu [obory názvů v Visual Basic](https://msdn.microsoft.com/library/cffac744-ab8c-4f1f-ba50-732c22ab4b88).

 Informace o tom, jak vytvořit obory názvů v kódu, naleznete v tématu [Namespace Statement](https://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2).

 Další informace o vlastnosti kořenového oboru názvů naleznete v tématu [/RootNamespace](https://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783).

 Informace o tom, jak získat přístup k této vlastnosti prostřednictvím kódu programu, najdete v tématu <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

 **Cílová architektura (všechny konfigurace)** Určuje verzi .NET Framework, na kterou aplikace cílí. Tato možnost může mít různé hodnoty v závislosti na tom, které verze .NET Framework jsou nainstalovány ve vašem počítači.

 Výchozí hodnota se shoduje s cílovou architekturou, kterou jste zadali v dialogovém okně **Nový projekt** .

> [!NOTE]
> Požadované balíčky uvedené v [dialogovém okně požadavky](../../ide/reference/prerequisites-dialog-box.md) se nastaví automaticky při prvním otevření dialogového okna. Pokud následně změníte cílovou architekturu projektu, je nutné zadat požadavky ručně, aby odpovídaly novému cílovému rozhraní.

 Další informace najdete v tématu [Postupy: cílení na verzi .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) a [Visual Studio – Přehled cílení na více](../../ide/visual-studio-multi-targeting-overview.md)verzí.

 **Typ aplikace** Určuje typ aplikace, která se má sestavit. Pro [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikace můžete zadat aplikaci pro **Windows Store**, **knihovnu tříd**nebo **soubor winmd**. Pro většinu ostatních typů aplikací můžete určit **aplikaci systému Windows**, **konzolovou aplikaci**, **knihovnu tříd**, **službu systému Windows**nebo **knihovnu webového ovládacího prvku**.

 Pro projekt webové aplikace je nutné zadat **knihovnu tříd**.

 Pokud zadáte možnost **soubor winmd** , typy lze promítnout do libovolného programovacího jazyka prostředí Windows Runtime. Sbalením výstupu projektu jako souboru WinMD můžete kódovat aplikaci v různých jazycích a nechat kód fungovat, jako kdybyste ho vytvořili ve stejném jazyce. Možnost **soubor winmd** můžete použít pro řešení, která cílí na knihovny prostředí Windows Runtime, včetně [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]ch aplikací. Další informace najdete v tématu [vytváření prostředí Windows runtimech komponent C# v a Visual Basic](https://go.microsoft.com/fwlink/?LinkId=231895).

> [!NOTE]
> Prostředí Windows Runtime mohou být typy projektů tak, aby se zobrazily jako nativní objekty v jakémkoli jazyku, který je používá. Například aplikace jazyka JavaScript, které pracují s prostředí Windows Runtime používají jako sadu objektů jazyka JavaScript a C# aplikace používají knihovnu jako kolekci objektů rozhraní .NET. Sbalením výstupu projektu jako souboru WinMD můžete využít stejnou technologii, jakou prostředí Windows Runtime používá.

 Další informace o vlastnosti **Typ aplikace** naleznete v tématu [/target (Visual Basic)](https://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c). Informace o tom, jak tuto vlastnost přistupovat prostřednictvím kódu programu, najdete v tématu <xref:VSLangProj.ProjectProperties.OutputType%2A>.

 **Ikona** Nastaví soubor. ico, který chcete použít jako ikonu programu. Vyberte **\<Procházet... >** vyhledat existující grafiku. Další informace naleznete v tématu [/win32icon](https://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) (nebo [/Win32icon) (C# možnosti kompilátoru)](https://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138). Chcete-li získat přístup k této vlastnosti programově, přečtěte si téma <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

 **Spouštěcí formulář/spouštěcí objekt/spouštěcí identifikátor URI** Určuje spouštěcí formulář nebo vstupní bod aplikace.

 Pokud je vybrána **možnost Povolit aplikační rozhraní** (výchozí), tento seznam má hodnotu " **úvodní formulář** " a zobrazuje pouze formuláře, protože aplikační rozhraní podporuje pouze formuláře po spuštění, nikoli objekty.

 Pokud se jedná o aplikaci prohlížeče WPF, tento seznam má hodnotu **spouštěcí identifikátor URI**a výchozí hodnota je **Page1. XAML**. Seznam **spouštěcích identifikátorů URI** umožňuje zadat prostředek uživatelského rozhraní (prvek XAML), který aplikace zobrazuje při spuštění aplikace. Další informace najdete v tématu <xref:System.Windows.Application.StartupUri%2A>.

 Pokud je zaškrtnuto políčko **Povolit aplikační architekturu** , tento seznam se bude **spouštěcím objektem** a zobrazí jak formuláře, třídy, tak i moduly s `Sub Main`.

 **Spouštěcí objekt** definuje vstupní bod, který má být volán při načtení aplikace. Obecně je nastaveno buď na hlavní formulář v aplikaci, nebo na `Sub Main` postup, který se má spustit při spuštění aplikace. Vzhledem k tomu, že knihovny tříd nemají vstupní bod, je jejich jediná možnost pro tuto vlastnost **(žádná)** . Další informace najdete v tématu [/Main](https://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0). Chcete-li získat přístup k této vlastnosti programově, přečtěte si téma <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

 **Informace o sestavení** Kliknutím na toto tlačítko zobrazíte [dialogové okno informace o sestavení](../../ide/reference/assembly-information-dialog-box.md).

 **Povolit aplikační architekturu** Určuje, zda projekt bude používat aplikační rozhraní. Nastavení této možnosti má vliv na možnosti dostupné ve **formuláři po spuštění**/**spouštěcí objekt**.

 Pokud je toto políčko zaškrtnuté, vaše aplikace používá standardní `Sub Main`. Zaškrtnutí tohoto políčka povolí funkce v části **Vlastnosti rozhraní Windows Application Framework** a také vyžaduje, abyste vybrali úvodní formulář.

 Pokud toto políčko není zaškrtnuté, vaše aplikace používá vlastní `Sub Main`, kterou jste zadali ve **formuláři po spuštění**. V takovém případě můžete zadat spouštěcí objekt (vlastní `Sub Main` v metodě nebo třídě) nebo ve formuláři. Také možnosti v oddílu **Vlastnosti aplikačního rozhraní systému Windows** nebudou k dispozici.

 **Zobrazit nastavení systému Windows** Kliknutím na toto tlačítko vygenerujete a otevřete soubor App. manifest. Visual Studio pomocí tohoto souboru generuje data manifestu aplikace. Potom nastavte pomocí značky `<requestedExecutionLevel>` v souboru App. manifest požadovanou úroveň spuštění nástroje řízení uživatelských účtů (UAC) následujícím způsobem:

 `<requestedExecutionLevel level="asInvoker" />`

 ClickOnce funguje s úrovní `asInvoker` nebo ve virtualizovaném režimu (bez generování manifestu). Chcete-li zadat virtualizovaný režim, odeberte celou značku z App. manifest.

 Další informace o generování manifestu naleznete v tématu [nasazení ClickOnce v systému Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Vlastnosti aplikačního rozhraní Windows
 V části **Vlastnosti rozhraní Windows Application Framework** jsou k dispozici následující nastavení. Tyto možnosti jsou k dispozici pouze v případě, že je zaškrtnuto políčko **Povolit aplikační architekturu** . Následující část popisuje nastavení **vlastností Windows Application Framework** pro aplikace Windows Presentation Foundation (WPF).

 **Povolit vizuální styly XP** Povolí nebo zakáže vizuální styly systému Windows XP, označované také jako *motivy systému Windows XP*. Vizuální styly Windows XP umožňují například ovládací prvky s zaoblenými rohy a dynamickými barvami. Výchozí hodnota je povolena. Další informace o vizuálních stylech systému Windows XP naleznete v tématu [funkce systému Windows XP a ovládací prvky model Windows Forms](https://msdn.microsoft.com/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)).

 **Vytvoření aplikace s jedinou instancí** Zaškrtnutím tohoto políčka zabráníte uživatelům v spuštění více instancí aplikace. Výchozí nastavení pro toto zaškrtávací políčko je zrušeno. Toto nastavení umožňuje spuštění více instancí aplikace.

 **Uložit My. Settings při vypnutí** Zaškrtnutím tohoto políčka určíte, že nastavení `My.Settings` aplikace budou uložena, když uživatelé vypnou své počítače. Výchozí nastavení je povoleno. Pokud je tato možnost zakázaná, můžete nastavení aplikace uložit ručně voláním `My.Settings.Save`.

 **Režim ověřování** Vyberte možnost **Windows** (výchozí) a určete tak použití ověřování systému Windows k identifikaci aktuálně přihlášeného uživatele. Tyto informace lze načíst za běhu pomocí objektu `My.User`. Vyberte možnost **definováno aplikací** , pokud budete poskytovat vlastní kód pro ověřování uživatelů místo použití výchozích metod ověřování systému Windows.

 **Režim vypnutí** Vyberte, **když se zavře úvodní formulář** (výchozí) a určí, že se aplikace ukončí, když se zavře formulář, který se spustí po spuštění, i když jsou otevřené další formuláře. Vyberte, **když se zavře poslední formulář** , a určete tak, že se aplikace ukončí, když se zavře poslední formulář, nebo když se `My.Application.Exit` nebo se příkaz `End` volá explicitně.

 Vyberte možnost **při explicitním vypnutí** , chcete-li určit, že se aplikace ukončí při explicitním volání `Shutdown`.

 **V nabídce poslední okno vyberte Zavřít** a určete tak, že se aplikace ukončí při zavření posledního okna nebo když explicitně voláte `Shutdown`. Toto je výchozí nastavení.

 **V nabídce hlavní okno vyberte Zavřít** a určete tak, že se aplikace ukončí při zavření hlavního okna nebo když explicitně voláte `Shutdown`.

 **Úvodní obrazovka** Vyberte formulář, který chcete použít jako úvodní obrazovku. Předtím, než je třeba vytvořit úvodní obrazovku pomocí formuláře nebo šablony. Výchozí hodnota je **(žádné)** .

 **Zobrazit události aplikace** Kliknutím na toto tlačítko zobrazíte soubor s kódem událostí, ve kterém můžete zapisovat události pro události aplikační architektury `Startup`, `Shutdown`, `UnhandledException`, `StartupNextInstance` a `NetworkAvailabilityChanged`. Můžete také přepsat určité metody aplikační architektury. Například můžete změnit chování při zobrazení úvodní obrazovky přepsáním `OnInitialize`.

### <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-applications"></a>Vlastnosti aplikačního rozhraní Windows pro aplikace Windows Presentation Foundation (WPF)
 Následující nastavení jsou k dispozici v oddílu **Vlastnosti rozhraní Windows Application Framework** , pokud je projekt Windows Presentation Foundation aplikaci. Tyto možnosti jsou k dispozici pouze v případě, že je zaškrtnuto políčko **Povolit aplikační architekturu** . Možnosti uvedené v této tabulce jsou k dispozici pouze pro aplikace WPF nebo aplikace prohlížeče WPF. Nejsou k dispozici pro uživatelský ovládací prvek WPF ani pro knihovny vlastního ovládacího prvku.

 **Režim vypnutí** Tato vlastnost se vztahuje pouze na Windows Presentation Foundation aplikace.

 Vyberte možnost **při explicitním vypnutí** , chcete-li určit, že se aplikace ukončí při explicitním volání <xref:System.Windows.Application.Shutdown%2A>.

 **V nabídce poslední okno vyberte Zavřít** a určete tak, že se aplikace ukončí při zavření posledního okna nebo když explicitně voláte <xref:System.Windows.Application.Shutdown%2A>. Toto je výchozí nastavení.

 **V nabídce hlavní okno vyberte Zavřít** a určete tak, že se aplikace ukončí při zavření hlavního okna nebo když explicitně voláte <xref:System.Windows.Application.Shutdown%2A>.

 Další informace o použití tohoto nastavení najdete v tématu <xref:System.Windows.Application.Shutdown%2A>

 **Upravit XAML** Kliknutím na toto tlačítko otevřete a upravte soubor definice aplikace (Application. XAML) v editoru XAML. Po kliknutí na toto tlačítko se otevře Application. XAML v uzlu definice aplikace. Možná budete muset tento soubor upravit, aby se prováděly určité úlohy, například definování prostředků. Pokud soubor definice aplikace neexistuje, Návrhář projektu ho vytvoří.

 **Zobrazit události aplikace** Kliknutím na toto tlačítko zobrazíte `Application` soubor částečné třídy (Application. XAML. vb) v editoru kódu. Pokud soubor neexistuje, Návrhář projektu jej vytvoří s odpovídajícím názvem třídy a oborem názvů.

 Objekt <xref:System.Windows.Application> vyvolává události při výskytu určitých změn stavu aplikace (například při spuštění nebo vypnutí aplikace). Úplný seznam událostí, které tato třída zpřístupňuje, naleznete v tématu <xref:System.Windows.Application>. Tyto události jsou zpracovávány v oddílu uživatelského kódu `Application` částečné třídy.

## <a name="see-also"></a>Viz také
[Správa vlastností aplikace](../../ide/application-properties.md) [při psaní kódu v řešeních pro systém Office](https://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0)
