---
title: Stránka aplikace, Návrhář (Visual Basic) projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: 8cec9fea-cd92-47ff-88dd-7c928f0b4a74
caps.latest.revision: 68
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9d2b23b5570a6372b727906a63ffb51513019df7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175484"
---
# <a name="application-page-project-designer-visual-basic"></a>Stránka Aplikace, návrhář projektu (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Použití **aplikace** stránky Návrháře projektu k určení nastavení aplikace a vlastnosti projektu.  
  
 Pro přístup k **aplikace** zvolte uzel projektu (ne **řešení** uzlu) v **Průzkumníka řešení**. Klikněte na tlačítko **projektu**, **vlastnosti** na řádku nabídek. Jakmile se zobrazí Návrhář projektu, klikněte na tlačítko **aplikace** kartu.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="general-application-settings"></a>Obecné nastavení aplikace  
 Tyto možnosti umožňují nakonfigurovat obecná nastavení pro aplikaci.  
  
 **Název sestavení**  
 Určuje název výstupního souboru, který bude obsahovat manifest sestavení. Pokud změníte tuto vlastnost **název výstupního** vlastnost se také změní. Můžete také provedení této změny na příkazovém řádku s použitím [/out (Visual Basic)](http://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae). Informace o tom, jak programově přístup k této vlastnosti naleznete v tématu <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.  
  
 **Kořenový obor názvů**  
 Určuje základní obor názvů pro všechny soubory v projektu. Například, pokud jste nastavili **kořenové Namespace** k `Project1` a máte `Class1` mimo libovolný obor názvů ve vašem kódu, jeho obor názvů by `Project1.Class1`. Pokud máte `Class2` v oboru názvů `Order` v kódu, jeho obor názvů by `Project1.Order.Class2`.  
  
 Pokud zrušíte výběr **kořenové Namespace**, obor názvů strukturu projektu můžete zadat v kódu.  
  
> [!NOTE]
>  Pokud používáte Global – klíčové slovo v [příkaz Namespace](http://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2), můžete definovat obor názvů mimo kořenový obor názvů vašeho projektu. Pokud zrušíte výběr **kořenové Namespace**, `Global` stane oboru nejvyšší úrovně, která eliminuje potřebu `Global` – klíčové slovo v `Namespace` příkaz. Další informace najdete v tématu "Globální – klíčové slovo v Namespace příkazy" v [obory názvů v jazyce Visual Basic](http://msdn.microsoft.com/library/cffac744-ab8c-4f1f-ba50-732c22ab4b88).  
  
 Informace o tom, jak vytvořit obory názvů ve vašem kódu, naleznete v tématu [příkaz Namespace](http://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2).  
  
 Další informace o vlastnosti kořenový obor názvů najdete v tématu [/RootNamespace](http://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783).  
  
 Informace o tom, jak programově přístup k této vlastnosti naleznete v tématu <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.  
  
 **Cílová architektura (všechny konfigurace)**  
 Určuje verzi rozhraní .NET Framework, který aplikace cílí. Tato možnost může mít různé hodnoty v závislosti na nainstalovaných verzí rozhraní .NET Framework v počítači.  
  
 Výchozí hodnota se shoduje s cílovou architekturu, která jste zadali v **nový projekt** dialogové okno.  
  
> [!NOTE]
>  Požadované balíčky, které jsou uvedeny v [dialogové okno požadavky](../../ide/reference/prerequisites-dialog-box.md) se nastaví automaticky, když otevřete dialogové okno poprvé. Pokud později změníte cílový rámec projektu, je nutné zadat předpoklady ručně, aby odpovídaly novému cílovému rozhraní.  
  
 Další informace najdete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) a [Visual Studio přehled multiplatformního zacílení](../../ide/visual-studio-multi-targeting-overview.md).  
  
 **Typ aplikace**  
 Určuje typ aplikace k sestavení. Pro [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikace, můžete zadat **aplikace Windows Store**, **knihovny tříd**, nebo **soubor WinMD**. Pro většinu ostatních typů aplikací, můžete zadat **aplikace Windows**, **konzolovou aplikaci**, **knihovny tříd**, **Windows Service**, nebo **Knihovna webových prvků**.  
  
 Pro projekt webové aplikace, je nutné zadat **knihovny tříd**.  
  
 Pokud zadáte **soubor WinMD** možnost, typy je možné promítnout do jakékoli Windows Runtime programovací jazyk. Balení výstup projektu jako soubor WinMD, může kód aplikace v několika jazycích a spolupracovat, jako kdyby jste napsali kód vše ve stejném jazyce. Můžete použít **soubor WinMD** možnost pro řešení, které se zaměřují na modul Windows Runtime knihovny, včetně [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikace. Další informace najdete v tématu [vytváření komponent Windows Runtime v jazyce C# a Visual Basic](http://go.microsoft.com/fwlink/?LinkId=231895).  
  
> [!NOTE]
>  Modul Windows Runtime můžete promítnout typy tak, aby byly zobrazeny jako nativních objektů v libovolný preferovaný jazyk je využívá. Například použít jako sadu JavaScript – objekty jazyka JavaScript aplikace, které spolupracují s modulem Windows Runtime a aplikace C# použít knihovnu jako kolekce objektů .NET. Díky balení výstup projektu jako soubor WinMD, můžete využívat stejné technologie, která používá prostředí Windows Runtime.  
  
 Další informace o **typ aplikace** vlastnost, naleznete v tématu [/Target (Visual Basic)](http://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c). Informace o tom, jak programově přístup k této vlastnosti naleznete v tématu <xref:VSLangProj.ProjectProperties.OutputType%2A>.  
  
 **Ikona**  
 Nastavuje soubor .ico, který chcete použít jako ikona programu. Vyberte  **\<Procházet... >** k vyhledání existujícího obrázku. Zobrazit [/win32icon](http://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) (nebo [/win32icon (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138)) pro další informace. Programový přístup k této vlastnosti, najdete v článku <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.  
  
 **Úvodní formulář nebo spouštěcí objekt / spouštěcí identifikátor URI**  
 Určuje formuláře nebo vstupní bod při spuštění aplikace.  
  
 Pokud **Povolit aplikační framework** je vybrán tento seznam (výchozí), má název **úvodní formulář** a zobrazuje pouze formuláře rozhraní framework aplikace podporuje pouze formuláře při spuštění nejsou objekty.  
  
 Pokud je projekt aplikace WPF pro prohlížeč, je tento seznam s názvem **spouštěcí identifikátor URI**, a výchozí hodnota je **Page1.xaml**. **Spouštěcí identifikátor URI** seznamu vám umožní zadat prostředek rozhraní uživatele (a XAML element), které aplikace se zobrazí při spuštění aplikace. Další informace naleznete v tématu <xref:System.Windows.Application.StartupUri%2A>.  
  
 Pokud **Povolit aplikační framework** není zaškrtnuto, tento seznam bude **spouštěcí objekt** a zobrazuje formuláře a tříd nebo moduly s `Sub Main`.  
  
 **Spouštěcí objekt** definuje vstupní bod, který bude volán při načtení aplikace. Obecně je nastavené na hodnotu hlavního formuláře v aplikaci nebo na `Sub Main` proceduru, která se má spustit při spuštění aplikace. Vzhledem k tomu, že nemá vstupní bod knihovny tříd, jejich jedinou možností pro tuto vlastnost je **(žádný)**. Další informace najdete v tématu [/main](http://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0). Programový přístup k této vlastnosti, najdete v článku <xref:VSLangProj.ProjectProperties.StartupObject%2A>.  
  
 **Informace o sestavení**  
 Kliknutím na toto tlačítko Zobrazit [dialogové okno informace o sestavení](../../ide/reference/assembly-information-dialog-box.md).  
  
 **Povolit aplikační framework**  
 Určuje, zda projekt bude používat aplikační platformu. Nastavení této možnosti má vliv na možnosti dostupné v **úvodní formulář**/**spouštěcí objekt**.  
  
 Pokud je toto políčko zaškrtnuto, vaše aplikace používá standardní `Sub Main`. Výběrem tohoto zaškrtávacího políčka povoluje funkce v **vlastnosti rozhraní framework aplikace Windows** části a také vyžaduje, abyste vyberte formulář spuštění.  
  
 Pokud je toto políčko zaškrtnuté, vaše aplikace používá vlastní `Sub Main` , který jste zadali v **úvodní formulář**. V tomto případě můžete zadat buď objekt při spuštění (vlastní `Sub Main` v metodě nebo třídě) nebo formuláře. Navíc možnosti **vlastnosti rozhraní framework aplikace Windows** oddílu k dispozici.  
  
 **Zobrazit nastavení Windows**  
 Kliknutím na toto tlačítko Generovat a otevřete soubor app.manifest. Visual Studio tento soubor používá ke generování manifestu data aplikace. Pak sadu UAC požadovaná úroveň spuštění úpravou `<requestedExecutionLevel>` značku app.manifest následujícím způsobem:  
  
 `<requestedExecutionLevel level="asInvoker" />`  
  
 ClickOnce – funguje s úrovní `asInvoker` nebo ve virtualizovaných režimu (bez generování manifestu). Pro určení virtualizované režimu, odeberte celou z app.manifest.  
  
 Další informace o generování manifestu naleznete v tématu [nasazení ClickOnce v systému Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md).  
  
## <a name="windows-application-framework-properties"></a>Vlastnosti rozhraní Framework aplikace Windows  
 Následující nastavení jsou dostupná **vlastnosti rozhraní framework aplikace Windows** oddílu. Tyto možnosti jsou dostupné pouze tehdy, pokud **Povolit aplikační framework** je zaškrtnuto políčko. Popisuje části následující za touto možností **vlastnosti rozhraní framework aplikace Windows** nastavení pro aplikace Windows Presentation Foundation (WPF).  
  
 **Povolení vizuálních stylů XP**  
 Povolí nebo zakáže vizuálních stylů Windows XP, označované také jako *Windows XP motivy*. Vizuální styly Windows XP povolit, například ovládací prvky s oblých rohů a dynamické barvy. Výchozí hodnota je povolená. Další informace o vizuálních stylů Windows XP, naleznete v tématu [funkce Windows XP a ovládací prvky Windows Forms](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)).  
  
 **Ujistěte se, jedna instance aplikace**  
 Zaškrtněte toto políčko, pokud chcete zabránit uživatelům ve spouštění více instancí aplikace. Ve výchozím nastavení toto políčko není zaškrtnuto. Toto nastavení umožňuje několik instancí aplikace ke spuštění.  
  
 **Při vypnutí ukládání My.Settings**  
 Zaškrtněte toto políčko, chcete-li určit, že aplikace `My.Settings` nastavení se ukládají, když uživatelé vypnutí počítačů. Ve výchozím nastavení zapnutá. Pokud tato možnost je zakázaná, můžete uložit nastavení aplikace ručně voláním `My.Settings.Save`.  
  
 **Režim ověřování**  
 Vyberte **Windows** (výchozí) k určení použití ověřování Windows k identifikaci aktuálně přihlášeného uživatele. Tyto informace za běhu můžete načíst pomocí `My.User` objektu. Vyberte **definovaného aplikací** budete poskytovat vlastní kód pro ověření uživatelům, tedy ne pomocí výchozí metody ověřování Windows.  
  
 **Ukončení režimu**  
 Vyberte **když se zavře úvodní formulář** (výchozí) k určení, že ukončení aplikace, když se formulář nastaven jako spouštěcí zavře, i v případě, že jsou otevřené jiné formuláře. Vyberte **při poslední formuláře zavře** k určení, že aplikace ukončena při zavření posledního formuláře, nebo když `My.Application.Exit` nebo `End` příkaz je explicitně volána.  
  
 Vyberte **při jednoznačném vypnutí** k určení, že aplikaci ukončit, pokud explicitně volat `Shutdown`.  
  
 Vyberte **na poslední okno zavřete** k určení, že aplikace ukončena při zavření posledního okna, nebo když explicitně volat `Shutdown`. Toto je výchozí nastavení.  
  
 Vyberte **na hlavní okno zavřete** k určení, že aplikace ukončena, když hlavní okno se zavře, nebo když explicitně volat `Shutdown`.  
  
 **Úvodní obrazovka**  
 Vyberte formulář, který chcete použít jako úvodní obrazovka. Musí mít dříve vytvoříte úvodní obrazovky pomocí formuláře nebo šablony. Výchozí hodnota je **(žádný)**.  
  
 **Zobrazit události aplikace**  
 Kliknutím na toto tlačítko zobrazíte kód souboru události, ve kterém můžete zapisovat události pro události rozhraní framework aplikace `Startup`, `Shutdown`, `UnhandledException`, `StartupNextInstance` a `NetworkAvailabilityChanged`. Můžete také přepsat metody rozhraní framework určitých aplikací. Například můžete změnit chování zobrazení na úvodní obrazovce přepsáním `OnInitialize`.  
  
### <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-applications"></a>Vlastnosti rozhraní Framework aplikace Windows pro aplikace Windows Presentation Foundation (WPF)  
 Následující nastavení jsou dostupná **vlastnosti rozhraní framework aplikace Windows** části, pokud je projekt aplikace Windows Presentation Foundation. Tyto možnosti jsou dostupné pouze tehdy, pokud **Povolit aplikační framework** je zaškrtnuto políčko. Možnosti uvedené v této tabulce jsou k dispozici pouze pro aplikace WPF nebo aplikace prohlížeče WPF. Nejsou k dispozici pro uživatelský ovládací prvek WPF nebo vlastní ovládací prvek knihovny.  
  
 **Ukončení režimu**  
 Tato vlastnost platí jenom pro aplikace Windows Presentation Foundation.  
  
 Vyberte **při jednoznačném vypnutí** k určení, že aplikaci ukončit, pokud explicitně volat <xref:System.Windows.Application.Shutdown%2A>.  
  
 Vyberte **na poslední okno zavřete** k určení, že aplikace ukončena při zavření posledního okna, nebo když explicitně volat <xref:System.Windows.Application.Shutdown%2A>. Toto je výchozí nastavení.  
  
 Vyberte **na hlavní okno zavřete** k určení, že aplikace ukončena, když hlavní okno se zavře, nebo když explicitně volat <xref:System.Windows.Application.Shutdown%2A>.  
  
 Další informace o použití tohoto nastavení najdete v tématu <xref:System.Windows.Application.Shutdown%2A>  
  
 **Upravit XAML**  
 Kliknutím na toto tlačítko otevřete a upravte soubor definice aplikace (Application.xaml) v editoru XAML. Po kliknutí na toto tlačítko otevře Application.xaml v definici uzlu aplikace. Budete muset upravit tento soubor k provádění určitých úloh, jako je například definování prostředků. Pokud soubor definice aplikace buď neexistuje, Návrhář projektu ho vytvoří.  
  
 **Zobrazit události aplikace**  
 Kliknutím na toto tlačítko Zobrazit `Application` soubor částečné třídy (Application.xaml.vb) v editoru kódu. Pokud soubor neexistuje, vytvoří Návrháře projektu s názvem příslušné třídy a oboru názvů.  
  
 <xref:System.Windows.Application> Objekt vyvolává události, když dojde k určitým změnám stavu aplikace (třeba na spuštění aplikace nebo ukončení). Úplný seznam událostí, které tato třída zveřejňuje najdete v tématu <xref:System.Windows.Application>. Tyto události jsou zpracovány v oddíle kód uživatele `Application` částečné třídy.  
  
## <a name="see-also"></a>Viz také  
[Správa vlastností aplikace](../../ide/application-properties.md) [psaní kódu v řešeních pro systém Office](http://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0)



