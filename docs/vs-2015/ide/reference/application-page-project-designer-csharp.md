---
title: Stránka aplikace, Návrhář projektu (C#) | Dokumentace Microsoftu
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
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: f13701a8-4e2e-4474-9d60-bb43decbe0c1
caps.latest.revision: 61
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4a130a04be7a0645fef44ff6c8ae9dcc31b55dcf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867231"
---
# <a name="application-page-project-designer-c"></a>Stránka Aplikace, návrhář projektu (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Použití **aplikace** stránku **Návrháře projektu** k určení nastavení aplikace a vlastnosti projektu.  
  
 Pro přístup k **aplikace** zvolte uzel projektu (ne **řešení** uzlu) v **Průzkumníka řešení**. Klikněte na tlačítko **projektu**, **vlastnosti** na řádku nabídek. Jakmile se zobrazí Návrhář projektu, klikněte na tlačítko **aplikace** kartu.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="general-application-settings"></a>Obecné nastavení aplikace  
 Tyto možnosti umožňují nakonfigurovat obecná nastavení pro aplikaci.  
  
 **Název sestavení**  
 Určuje název výstupního souboru, který bude obsahovat manifest sestavení. Změna této vlastnosti se také změní **název výstupního** vlastnost. Tuto změnu z příkazového řádku můžete také provést pomocí [/out (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5). Programový přístup k této vlastnosti, najdete v článku <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.  
  
 **výchozí obor názvů**  
 Určuje základní obor názvů pro soubory přidané do projektu.  
  
 Zobrazit [obor názvů](http://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f) pro další informace o vytváření oborů názvů ve vašem kódu.  
  
 Programový přístup k této vlastnosti, najdete v článku <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.  
  
 **Cílová architektura**  
 Určuje verzi rozhraní .NET Framework, který aplikace cílí. Tato možnost může mít různé hodnoty v závislosti na nainstalovaných verzí rozhraní .NET Framework v počítači.  
  
 Výchozí hodnota je stejná jako Cílová architektura, kterou jste vybrali v **nový projekt** dialogové okno.  
  
> [!NOTE]
>  Požadované balíčky uvedené v [dialogové okno požadavky](../../ide/reference/prerequisites-dialog-box.md) se nastaví automaticky při prvním otevření dialogu. Pokud později změníte cílový rámec projektu, budete muset vybrat předpoklady ručně, aby odpovídaly novému cílovému rozhraní.  
  
 Další informace najdete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) a [Visual Studio přehled multiplatformního zacílení](../../ide/visual-studio-multi-targeting-overview.md).  
  
 **Typ aplikace**  
 Určuje typ aplikace k sestavení. Pro [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikace, můžete zadat **aplikace Windows Store**, **knihovny tříd**, nebo **soubor WinMD**. Pro většinu ostatních typů aplikací, můžete zadat **aplikace Windows**, **konzolovou aplikaci**, **knihovny tříd**, **Windows Service**, nebo **Knihovna webových prvků**.  
  
 Pro projekt webové aplikace, je nutné zadat **knihovny tříd**.  
  
 Pokud zadáte **soubor WinMD** možnost, typy je možné promítnout do jakékoli Windows Runtime programovací jazyk. Balení výstup projektu jako soubor WinMD, může kód aplikace v několika jazycích a spolupracovat, jako kdyby jste napsali kód vše ve stejném jazyce. Můžete určit tuto možnost pro řešení, které se zaměřují na modul Windows Runtime knihovny, včetně [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikace. Další informace najdete v tématu [vytváření komponent Windows Runtime v jazyce C# a Visual Basic](http://go.microsoft.com/fwlink/?LinkId=231895).  
  
> [!NOTE]
>  Modul Windows Runtime můžete promítnout typy tak, aby byly zobrazeny jako nativních objektů v libovolný preferovaný jazyk je využívá. Například použít jako sadu JavaScript – objekty jazyka JavaScript aplikace, které spolupracují s modulem Windows Runtime a aplikace C# použít knihovnu jako kolekce objektů .NET. Díky balení výstup projektu jako soubor WinMD, můžete využívat stejné technologie, která používá prostředí Windows Runtime.  
  
 Další informace o **typ aplikace** vlastnost, naleznete v tématu [/Target (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f). Informace o tom, jak programově přístup k této vlastnosti naleznete v tématu <xref:VSLangProj.ProjectProperties.OutputType%2A>.  
  
 **Informace o sestavení**  
 Kliknutím na toto tlačítko se zobrazí [dialogové okno informace o sestavení](../../ide/reference/assembly-information-dialog-box.md).  
  
 **Spouštěcí objekt**  
 Definuje vstupní bod, který bude volán při načtení aplikace. Obvykle je tato možnost nastavená buď hlavního formuláře v aplikaci nebo na `Main` proceduru, která se má spustit při spuštění aplikace. Vzhledem k tomu, že nemá vstupní bod knihovny tříd, jejich jedinou možností pro tuto vlastnost je **(Nenastaveno)**.  
  
 Ve výchozím nastavení v projektu aplikace WPF pro prohlížeč, tato možnost je **(Nenastaveno)**. Další možností je *Projectname*. App. V tento druh projektu je nutné nastavit počáteční identifikátor URI pro načtení prostředku uživatelského rozhraní při spuštění aplikace. Chcete-li to provést, otevřete soubor Application.xaml ve vašem projektu a nastavit `StartupUri` vlastnosti do souboru .xaml v projektu, jako je například Window1.xaml. Seznam prvků přijatelný kořenový najdete v tématu <xref:System.Windows.Application.StartupUri%2A>. Budete také muset definovat `public static void Main()` metody ve třídě v projektu. Tato třída se objeví v **spouštěcí objekt** jako seznam *ProjectName.ClassName*. Pak můžete vybrat třídu jako spouštěcí objekt.  
  
 Zobrazit [/Main (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049) Další informace. Programový přístup k této vlastnosti, najdete v článku <xref:VSLangProj.ProjectProperties.StartupObject%2A>.  
  
## <a name="resources"></a>Prostředky  
 Tyto možnosti umožňují nakonfigurovat obecná nastavení pro aplikaci.  
  
 **Ikona a manifest**  
 Ve výchozím nastavení, je přepínač vybrán a **ikonu** a **Manifest** aktivnují možnosti. To umožňuje vybrat vlastní ikona nebo vyberte jiný generování manifestu možnosti. Nechte tento přepínač vybrat, pokud poskytujete soubor prostředků pro projekt.  
  
 **Ikona**  
 Nastavuje soubor .ico, který chcete použít jako ikona programu. Klikněte na tlačítko se třemi tečkami k vyhledání existujícího obrázku nebo zadejte název souboru, který chcete. Zobrazit [/win32icon (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138) Další informace. Programový přístup k této vlastnosti, najdete v článku <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.  
  
 **Manifest**  
 Vybere možnost generování manifestu, když je aplikace spuštěná v systému Windows Vista v rámci řízení uživatelských účtů (UAC). Tato možnost může mít následující hodnoty:  
  
- **Vložit manifest s výchozím nastavením**. Podporuje typické způsobem, ve kterém aplikace Visual Studio pracuje na Windows Vista, který je pro vložení informací o zabezpečení ve spustitelném souboru aplikace, určení, že `requestedExecutionLevel` být `AsInvoker`. Toto je výchozí možnost.  
  
- **Vytvořit aplikaci bez manifestu**. Tato metoda se označuje jako *virtualizace*. Tuto možnost použijte, pokud z důvodu kompatibility s dřívějšími aplikacemi.  
  
- **Properties\app.manifest**. Tato možnost je vyžadována pro aplikace nasazené pomocí technologie ClickOnce nebo bez registrace modelu COM Pokud publikujete třeba aplikaci pomocí nasazení ClickOnce **Manifest** se automaticky nastaví na tuto možnost.  
  
  **Soubor prostředků**  
  Když poskytujete soubor prostředků pro projekt, vyberte přepínač. Výběrem této možnosti zakáže **ikonu** a **Manifest** možnosti.  
  
  Zadejte název cesty nebo klikněte na tlačítko Procházet (**...** ) Chcete-li přidat soubor prostředků Win32 do projektu.  
  
## <a name="see-also"></a>Viz také  
[Správa vlastností aplikace](../../ide/application-properties.md)  
 [Psaní kódu v řešeních pro systém Office](http://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0)



