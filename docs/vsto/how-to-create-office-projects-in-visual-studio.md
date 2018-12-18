---
title: 'Postupy: vytváření projektů pro systém Office v sadě Visual Studio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6930ce085405c010e59e13adb8a3d380cff28d0e
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672766"
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>Postupy: vytváření projektů pro systém Office v sadě Visual Studio
  Můžete použít [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pro vytvoření doplňku VSTO a na úrovni dokumentu přizpůsobení pro aplikace Microsoft Office. Další informace o těchto typech projektů naleznete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-vsto-add-in-project"></a>Vytvoření projektu doplňku VSTO  
  
1. Na **souboru** nabídce zvolte **nový** > **projektu**. Pokud je vaše integrované vývojové prostředí (IDE) nastaveno pro použití [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] vývojové nastavení na **souboru** nabídce zvolte **nový** > **projektu**.  
  
    **Nový projekt** zobrazí se dialogové okno.  
  
   > [!NOTE]  
   >  Cílové projekty Office [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ve výchozím nastavení. Další informace najdete v tématu [profil klienta rozhraní .NET Framework](/dotnet/framework/deployment/client-profile).  
  
2. V podokně šablon, pod uzlem jazyka, které chcete použít, rozbalte **Office/SharePoint**.  
  
3. Zvolte **Office Add-ins** uzlu.  
  
4. V seznamu šablon projektu vyberte šablonu projektu doplňku VSTO. Seznam dostupných doplňku VSTO šablony projektů, naleznete v tématu [Přehled šablon projektů Office project](../vsto/office-project-templates-overview.md).  
  
   > [!NOTE]  
   >  Pokud šablony projektů nejsou zobrazeny po výběru **Office Add-ins** uzlu, ujistěte se, že **rozhraní .NET Framework 4** nebo novější je vybrané v poli se seznamem v horní části dialogového okna. Šablony projektů pro Office jsou zobrazeny pro obě verze rozhraní .NET Framework.  
  
5. V **název** zadejte název projektu. Ve výchozím nastavení název projektu slouží také jako název řešení.  
  
6. V **umístění** zadejte cestu, kde chcete vytvořit projekt. Můžete použít absolutní a univerzální naming convention (UNC) cesty. Nepoužívejte HTTP, FTP nebo jiné cesty protokolu.  
  
    Umístění mají následující formáty:  
  
   * [*jednotky*\]\:  
  
   * \\\\*Server*\\*sdílené složky*  
  
     Nepoužívejte tyto znaky v umístění:  
  
   * Hvězdička (*)  
  
   * Svislá čára (|)  
  
   * Dvojtečka (:) (S výjimkou následujících písmeno jednotky.)  
  
   * Dvojité uvozovky (") (cesty obsahující mezery není nutné vkládat do uvozovek.)  
  
   * Menší než (\<)  
  
   * Větší než (>)  
  
   * Otazník (?)  
  
   * Znak procenta (%)  
  
7. Zvolte **OK** tlačítko.
  
    > [!NOTE]  
    >  Doplňkové projekty jsou vždy uloženy při jejich vytváření. Nemůže být vytvořeny jako dočasné projekty. Další informace o dočasných projektech naleznete v tématu [dočasné projekty](https://msdn.microsoft.com/9cf1944c-7045-44cc-8701-7b0eb4099f2b).  
  
### <a name="to-create-a-document-level-customization-project"></a>Chcete-li vytvořit projekt přizpůsobení na úrovni dokumentu  
  
1. Na **souboru** nabídce zvolte **nový** > **projektu**. Pokud vaše rozhraní IDE nastaveno pro použití vývojového nastavení jazyka Visual Basic, na **souboru** nabídce zvolte **nový** > **projektu**.  
  
    **Nový projekt** zobrazí se dialogové okno.  
  
   > [!NOTE]  
   >  Cílové projekty Office [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ve výchozím nastavení.  Další informace najdete v tématu [profil klienta rozhraní .NET Framework](/dotnet/framework/deployment/client-profile).  
  
2. V podokně šablon, pod uzlem jazyka, které chcete použít, rozbalte **Office/SharePoint**.  
  
3. Vyberte **Office Add-ins** uzlu.  
  
4. V seznamu šablon projektu vyberte šablonu projektu na úrovni dokumentu. Seznam dostupných projektů na úrovni dokumentu šablony najdete v tématu [Přehled šablon projektů Office project](../vsto/office-project-templates-overview.md).  
  
   > [!NOTE]  
   >  Pokud šablony projektů nejsou zobrazeny po výběru **Office Add-ins** uzlu, ujistěte se, že **rozhraní .NET Framework 4** nebo novější je vybrané v poli se seznamem v horní části dialogového okna. Šablony projektů pro Office jsou zobrazeny pro obě verze rozhraní .NET Framework.  
  
5. V **název** zadejte název projektu. Ve výchozím nastavení tento název se používá také pro dokument. Pokud vaše rozhraní IDE nastaveno pro použití vývojového nastavení jazyka Visual C# nebo obecného vývojového nastavení, také zadejte umístění a název řešení.  
  
   > [!NOTE]  
   >  Náhradní znaky nelze použít v cestě umístění projektu nebo v názvu projektu. Také pokud plánujete nasadit řešení pro použití v režimu offline, znaky v názvu projektu se musí vejít specifikacím protokolu HTTP.  
  
6. Zvolte **OK** tlačítko.  
  
    **Visual Studio Tools for Office Project Wizard** otevře.  
  
7. Vyberte **vytvoříte nový textový dokument** Pokud chcete vytvořit nový dokument pro řešení, nebo vyberte **zkopírovat existující dokument** Pokud budete chtít upravit existující dokument.  
  
    Pokud vytvoříte nový textový dokument, zadejte název do **název** pole a vyberte formát dokumentu pomocí **formátu** pole. Další informace o dostupných formátech naleznete v tématu [architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
    Pokud používáte existující dokument, zadejte umístění dokumentu **úplnou cestu k existujícímu dokumentu** pole. Můžete použít absolutní a cesty UNC. Nepoužívejte HTTP, FTP nebo jiné cesty protokolu k dokumentu.  
  
    Umístění mají následující formáty:  
  
   - [*jednotky*\]\:  
  
   - \\\\*Server*\\*sdílené složky*  
  
     Nepoužívejte tyto znaky v umístění:  
  
   - Hvězdička (*)  
  
   - Svislá čára (|)  
  
   - Dvojtečka (:) (S výjimkou následujících písmeno jednotky.)  
  
   - Dvojité uvozovky (") (cesty obsahující mezery není nutné vkládat do uvozovek.)  
  
   - Menší než (\<)  
  
   - Větší než (>)  
  
   - Otazník (?)  
  
   - Znak procenta (%)  
  
   > [!NOTE]  
   >  Při použití existujícího dokumentu v [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] projektu, použijte pouze dokumenty, které byly vytvořeny v nebo převést na [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. Podobně pokud používáte existující dokument aplikace Word 2010 projektu, použijte pouze dokumenty, které byly vytvořeny v nebo převést na aplikaci Word 2010. Některé funkce budou zakázány v dokumentu, při použití dokumentu, který byl vytvořen v dřívější verzi aplikace Word. Pokud se pokusíte napsat kód, který používá tyto funkce, mohou se vyskytnout chyby ve vašem projektu. Chcete-li převést dokument, otevřete ho v [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] nebo Word 2010 na **souboru** kartu na pásu karet, zvolte **informace** > **převést**.  
  
8. Zvolte **Dokončit**.  
  
9. Přidáte složky projektu a její podsložky do seznamu důvěryhodných umístění v Centru zabezpečení v aplikaci Word v následujících případech:  
  
   - Vytváříte dokumentu aplikace Word, který je založen na *DOCM* souboru a dokument obsahuje projekt VBA nebo hostuje ovládací prvky Windows Forms. Přidání složky projektů do seznamu důvěryhodných umístění vám pomůže zajistit, že dokument funguje podle očekávání v době návrhu.  
  
   - Vytváření projektu šablony aplikace Word, který je založen na *DOTX* souboru. Složku projektu musíte přidat do seznamu důvěryhodných umístění tak, aby mohli spustit a ladit projekt.  
  
     Další informace o přidání dokumentu do seznamu důvěryhodných umístění naleznete na webu Microsoft Office Online [vytvoření, odebrání nebo změna důvěryhodného umístění pro soubory](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="see-also"></a>Viz také:  
 [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)   
 [Spolupráce na vývoji řešení pro systém Office](../vsto/collaborative-development-of-office-solutions.md)   
 [Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)   
 [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  
