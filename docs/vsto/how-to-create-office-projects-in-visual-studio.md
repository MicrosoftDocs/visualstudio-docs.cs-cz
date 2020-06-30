---
title: 'Postupy: vytváření projektů Office v sadě Visual Studio'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VST.SelectDocWizard.Page1
- VST.SelectDocWizard.Http
- VST.SelectDocWizard.Extension
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], creating projects
- Office applications [Office development in Visual Studio], creating
- Office projects [Office development in Visual Studio]
- projects [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], creating projects
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c70668f2d4cb9597e00a7e3848b78b9f2ed49db7
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547560"
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>Postupy: vytváření projektů Office v sadě Visual Studio
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]K vytvoření doplňku VSTO a přizpůsobení na úrovni dokumentu pro systém Microsoft Office aplikace můžete použít. Další informace o těchto typech projektů naleznete v tématu [Přehled vývoje řešení pro systém Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-a-vsto-add-in-project"></a>Vytvoření projektu doplňku VSTO

1. V nabídce **soubor** klikněte na příkaz **Nový**  >  **projekt**. Pokud je vaše integrované vývojové prostředí (IDE) nastaveno na použití [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Nastavení vývoje, v nabídce **soubor** klikněte na položku **Nový**  >  **projekt**.

    Zobrazí se dialogové okno **Nový projekt**.

   > [!NOTE]
   > Projekty Office jsou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ve výchozím nastavení cílené. Další informace najdete v tématu [.NET Framework profil klienta](/dotnet/framework/deployment/client-profile).

2. V podokně šablony pod uzlem pro jazyk, který chcete použít, rozbalte možnost **Office/SharePoint**.

3. Vyberte uzel **Doplňky pro Office** .

4. V seznamu šablon projektů vyberte šablonu projektu doplňku VSTO. Seznam dostupných šablon projektů doplňku VSTO najdete v tématu [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md).

   > [!NOTE]
   > Pokud se šablony projektu nezobrazí, když vyberete uzel **Doplňky pro Office** , ujistěte se, že je v poli se seznamem v horní části dialogového okna vybraná možnost **.NET Framework 4** nebo novější. Šablony projektů Office jsou viditelné pro obě verze .NET Framework.

5. Do pole **název** zadejte název projektu. Ve výchozím nastavení se název projektu používá také jako název řešení.

6. Do pole **umístění** zadejte cestu, kam chcete projekt vytvořit. Můžete použít absolutní cesty a cesty UNC (Universal Naming Convention). Nepoužívejte HTTP, FTP nebo jiné cesty protokolu.

    Umístění mají následující formáty:

   * [*jednotka*\]\:

   * \\\\*Server* \\ *Sdílet*

     Nepoužívejte tyto znaky v umístění:

   * Hvězdička (*)

   * Svislá čára (|)

   * Dvojtečka (:) (S výjimkou následujících písmen jednotky)

   * Dvojité uvozovky (") (cesty, které obsahují mezery, nepotřebují uvozovky.)

   * Menší než ( \< )

   * Větší než (>)

   * Otazník (?)

   * Znak procenta (%)

7. Klikněte na tlačítko **OK** .

   ::: moniker range="vs-2017"

   > [!NOTE]
   > Projekty doplňku jsou vždy uloženy při jejich vytvoření. Nelze je vytvořit jako dočasné projekty. Další informace o dočasných projektech naleznete v tématu [dočasné projekty](../ide/creating-solutions-and-projects.md#create-a-temporary-project).

   ::: moniker-end

### <a name="to-create-a-document-level-customization-project"></a>Vytvoření projektu přizpůsobení na úrovni dokumentu

1. V nabídce **soubor** klikněte na příkaz **Nový**  >  **projekt**. Pokud je vaše rozhraní IDE nastaveno na použití Visual Basic vývojové nastavení, v nabídce **soubor** klikněte na příkaz **Nový**  >  **projekt**.

    Zobrazí se dialogové okno **Nový projekt**.

2. V podokně šablony pod uzlem pro jazyk, který chcete použít, rozbalte možnost **Office/SharePoint**.

3. Vyberte uzel **Doplňky pro Office** .

4. V seznamu šablon projektů vyberte šablonu projektu na úrovni dokumentu. Seznam dostupných šablon projektů na úrovni dokumentu najdete v tématu [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md).

   > [!NOTE]
   > Pokud se šablony projektu nezobrazí, když vyberete uzel **Doplňky Office** , ujistěte se, že je vybraná možnost **.NET Framework 4** nebo novější.

5. Do pole **název** zadejte název projektu. Ve výchozím nastavení se tento název používá také pro dokument. Pokud je vaše rozhraní IDE nastaveno na použití nastavení vývoje v jazyce Visual C# nebo Obecné vývojové nastavení, zadejte také umístění a název řešení.

   > [!NOTE]
   > V cestě k umístění projektu nebo v názvu projektu nemůžete použít náhradní znaky. Také Pokud plánujete nasadit řešení pro použití v režimu offline, znaky v názvu projektu musí odpovídat specifikacím protokolu HTTP.

6. Klikněte na tlačítko **OK** .

    Otevře se **Průvodce projektem Visual Studio Tools for Office** .

7. Vyberte možnost **vytvořit nový dokument** , pokud chcete vytvořit nový dokument pro řešení, nebo vyberte možnost **zkopírovat existující dokument** , pokud chcete upravit existující dokument.

    Pokud vytvoříte nový dokument, zadejte název do pole **název** a vyberte formát dokumentu pomocí pole **Formát** . Další informace o dostupných formátech najdete v tématu [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md).

    Pokud použijete existující dokument, zadejte umístění dokumentu do pole **Úplná cesta k existujícímu dokumentu** . Můžete použít absolutní cesty a cesty UNC. Nepoužívejte k dokumentu cesty protokolu HTTP, FTP nebo jiné.

    Umístění mají následující formáty:

   - [*jednotka*\]\:

   - \\\\*Server* \\ *Sdílet*

     Nepoužívejte tyto znaky v umístění:

   - Hvězdička (*)

   - Svislá čára (|)

   - Dvojtečka (:) (S výjimkou následujících písmen jednotky)

   - Dvojité uvozovky (") (cesty, které obsahují mezery, nepotřebují uvozovky.)

   - Menší než ( \< )

   - Větší než (>)

   - Otazník (?)

   - Znak procenta (%)

   > [!NOTE]
   > Použijete-li v projektu existující dokument [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] , použijte pouze dokumenty, které byly vytvořeny v nebo převedené na [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] . Podobně platí, že pokud použijete existující dokument v projektu aplikace Word 2010, budou použity pouze dokumenty, které byly vytvořeny v nebo byly převedeny do aplikace Word 2010. Pokud použijete dokument, který byl vytvořen v dřívější verzi aplikace Word, budou některé funkce v dokumentu zakázány. Pokud se pokusíte napsat kód, který používá tyto funkce, může dojít k chybám v projektu. Chcete-li převést dokument, otevřete ho ve [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] formátu nebo Word 2010, na kartě **soubor** na pásu karet vyberte **informace**  >  **převést**.

8. Klikněte na tlačítko **Dokončit**.

9. Přidejte složku projektu a její podsložky do seznamu důvěryhodných umístění v centru zabezpečení v aplikaci Word v následujících případech:

   - Vytváříte dokument aplikace Word, který je založen na souboru *. docm* , a dokument obsahuje projekt VBA nebo hosty model Windows Forms ovládacích prvků. Přidání složky projektu do seznamu důvěryhodných umístění vám pomůže zajistit, že dokument funguje podle očekávání v době návrhu.

   - Vytváříte projekt šablony aplikace Word, který je založen na souboru *. dotx* . Složku projektu je nutné přidat do seznamu důvěryhodných umístění, aby bylo možné spustit a ladit projekt.

     Další informace o tom, jak přidat dokument do důvěryhodných umístění, najdete na webu systém Microsoft Office Online [Vytvoření, odebrání nebo změna důvěryhodného umístění souborů](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

## <a name="see-also"></a>Viz také
- [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)
- [Spolupráce na vývoji řešení pro systém Office](../vsto/collaborative-development-of-office-solutions.md)
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
- [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
