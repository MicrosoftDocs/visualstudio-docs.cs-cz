---
title: Přehled šablon projektů Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], about project templates
- Excel Workbook project template
- Word Template project template
- Excel [Office development in Visual Studio], project templates
- Project [Office development in Visual Studio], project templates
- project templates [Office development in Visual Studio]
- project templates, Word
- InfoPath [Office development in Visual Studio], project templates
- Excel Template project template
- project templates, 2007 Microsoft Office system
- project templates, Excel
- PowerPoint [Office development in Visual Studio], project templates
- Word [Office development in Visual Studio], Word project templates
- Office projects [Office development in Visual Studio], templates
- Excel projects in Visual Studio
- Word Document project template
- Visio [Office development in Visual Studio], project templates
- Word projects in Visual Studio
- Outlook [Office development in Visual Studio], project templates
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d1ad35b9aecc9e7559902104f447cbbec3415b49
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934324"
---
# <a name="office-project-templates-overview"></a>Přehled šablon projektů Office
  Nástroje Microsoft Office developer tools v sadě Visual Studio obsahují šablony projektů pro vytváření následujících typů řešení pro systém Office:  
  
- [Přizpůsobení na úrovni dokumentu](#DocLevel)  
  
- [Doplňky VSTO](#AppLevel)  
  
  Podrobné porovnání těchto typů řešení pro systém Office najdete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
  Šablony projektů pro Office jsou k dispozici v **nový projekt** dialogovém okně **Office** uzlu **Visual C#** a **jazyka Visual Basic**jazyky. Každá šablona generuje projekt s odpovídající konfigurací pro cílovou aplikaci, včetně odkazů na sestavení a nastavení ladění.  
  
  Každý projekt obsahuje soubory a kód umožňující začít pracovat na konkrétním typu řešení. Vygenerovaný kód pro každý projekt obsahuje obslužné rutiny událostí spuštění a ukončení. Do těchto obslužných rutin událostí můžete přidat kód pro inicializaci vašeho řešení při spuštění a pro vyčištění při jeho uvolnění z paměti. Další informace najdete v tématu [projektech pro systém Office v prostředí sady Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md) a [události v projektech pro systém Office](../vsto/events-in-office-projects.md).  
  
> [!NOTE]  
>  Nástroje pro vývoj pro Office jsou součástí určitých edicí sady Visual Studio. Další informace najdete v tématu [konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
##  <a name="DocLevel"></a> Přizpůsobení na úrovni dokumentu  
 **Office** uzlu **nový projekt** dialogové okno obsahuje následující šablony projektů, které vám pomůžou začít vytvářet přizpůsobení na úrovni dokumentu pro Word a Excel:  
  
- **Pro Word 2013 a 2016 VSTO dokumentu**  
  
- **Pro Word 2013 a 2016 VSTO šablony**  
  
- **Excel 2013 a 2016 VSTO sešitu**  
  
- **Excel 2013 a 2016 VSTO šablony**  
  
- **Dokument aplikace Word 2010 VSTO**  
  
- **Šablona VSTO pro Word 2010**  
  
- **Excelový sešit VSTO 2010**  
  
- **Šablona VSTO pro Excel 2010**  
  
  Šablony projektů Dokument aplikace Word a Sešit aplikace Excel poskytují kód, pomocí něhož můžete začít vytvářet řešení založené na konkrétním dokumentu nebo sešitu. V těchto typech řešení je váš kód spuštěn, pouze když je přidružený dokument otevřen v aplikaci Word nebo Excel.  
  
  Šablony projektů Šablona aplikace Word a Šablona aplikace Excel se chovají stejně jako šablony projektů Dokument aplikace Word a Sešit aplikace Excel. Šablony projektů Šablona aplikace Word a Šablona aplikace Excel ale usnadňují uživatelům vytvoření nových místních kopií dokumentu nebo sešitu pomocí přizpůsobené šablony z vašeho řešení. Funkce vašeho řešení jsou k dispozici z nového dokumentu, který uživatel z šablony vytvoří.  
  
> [!NOTE]  
>  Šablony aplikace Word, které odkazují na rozšíření spravovaného kódu nelze použít jako globální doplňky VSTO. Sestavení není voláno, pokud je šablona načtena z adresáře Po spuštění aplikace Word. Další informace najdete v tématu [omezení globálních šablon a doplňků aplikace Excel (souborů .xla)](#Limitations)  
  
 Informace, jak začít pracovat s těmito typy projektů, naleznete v následujících tématech:  
  
-   [Programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md)  
  
-   [Řešení aplikace Word](../vsto/word-solutions.md)  
  
-   [Řešení pro aplikaci Excel](../vsto/excel-solutions.md)  
  
-   [Návod: Vytvoření prvního přizpůsobení na úrovni dokumentu pro Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
-   [Návod: Vytvoření prvního přizpůsobení na úrovni dokumentu pro Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)  
  
##  <a name="AppLevel"></a> Doplňky VSTO  
 **Office/SharePoint** uzlu **nový projekt** dialogové okno obsahuje následující šablony projektů, které vám pomůžou začít vytvářet doplňky VSTO.  
  
- **Doplněk aplikace Excel 2013 a 2016 VSTO**  
  
- **Doplněk aplikace InfoPath 2013 VSTO**  
  
- **Doplněk aplikace Outlook 2013 a 2016 VSTO**  
  
- **Doplněk aplikace PowerPoint 2013 a 2016**  
  
- **Project 2013 a 2016 Add-in**  
  
- **Doplněk Visio 2013 a 2016**  
  
- **Doplněk aplikace Word 2013 a 2016**  
  
- **Doplněk aplikace Excel 2010**  
  
- **Doplněk aplikace InfoPath 2010**  
  
- **Doplněk aplikace Outlook 2010**  
  
- **Doplněk aplikace PowerPoint 2010**  
  
- **Doplněk aplikace Project 2010**  
  
- **Doplněk Visio 2010**  
  
- **Doplněk aplikace Word 2010**  
  
  Když vytvoříte projekt, který je založen na jedné z těchto šablon projektů, je kód ve vašem řešení spuštěn při spuštění přidružené aplikace. Na rozdíl od projektů na úrovni dokumentu není váš kód přidružen k jednomu dokumentu.  
  
  Další informace o tom, jak začít pracovat s těmito typy projektů, naleznete v následujících tématech:  
  
- [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
- [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)  
  
- [Návod: Vytvoření vašeho prvního doplňku VSTO pro Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
- [Návod: Vytvoření vašeho prvního doplňku VSTO pro Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
- [Návod: Vytvoření vašeho prvního doplňku VSTO pro PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
- [Návod: Vytvoření vašeho prvního doplňku VSTO pro Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
- [Návod: Vytvoření vašeho prvního doplňku VSTO pro Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
## <a name="document-vs-template-solutions"></a>Zdokumentujte vs. šablony řešení  
 Při návrhu řešení, které je založeno na dokumentu aplikace Word nebo sešitu aplikace Excel, se musíte rozhodnout, jak nejlépe zpřístupnit tento dokument uživateli.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 V některých situacích může být vhodné poskytnout každému uživateli kopii dokumentu. V takovém případě vytvořte řešení pomocí projektu dokumentu aplikace Excel nebo Word.  
  
 V jiných situacích může být vhodné zpřístupnit šablonu na serveru, aby si každý uživatel mohl šablonu otevřít a uložit si místní kopii dokumentu. V takovém případě vytvořte řešení pomocí projektu šablony aplikace Excel nebo Word.  
  
## <a name="comparison"></a>Srovnání  
 Následující tabulka popisuje rozdíly mezi dokumenty a šablonami.  
  
|Dokumenty|Šablony|  
|---------------|---------------|  
|Uživatelé mohou dokument otevřít a upravit, pokud není nastaven jen pro čtení. Jakékoli uložené změny se uchovávají v originálu dokumentu.|Uživatelé mohou šablonu otevřít a vytvořit pomocí ní místní kopii jako nový dokument. Nemohou originál upravovat, pokud jim neudělíte speciální oprávnění.|  
|Po otevření vyvolá dokument <xref:Microsoft.Office.Tools.Word.Document.Open> událostí.|Po otevření vyvolá šablona <xref:Microsoft.Office.Tools.Word.Document.New> událostí.|  
  
##  <a name="Limitations"></a> Omezení globálních šablon a doplňků aplikace Excel (souborů .xla)  
 Dokumenty, sešity a šablony nemusejí správně fungovat jako globální šablony nebo doplňky VSTO pro Excel (souborů .xla).  
  
## <a name="word-templates"></a>Šablony aplikace Word  
 Pokud má šablona aplikace Microsoft Office Word rozšíření se spravovaným kódem, není voláno sestavení projektu, pokud je šablona připojena jako globální šablona nebo načtena z adresáře Po spuštění aplikace Word. Dokument navíc nerozpozná formát šablony, která je součástí řešení pro Office.  
  
## <a name="excel-add-ins-xla-files"></a>Doplňky aplikace Excel (souborů .xla)  
 Neexistuje žádný projekt Office pro vytvoření doplňku VSTO pro Excel (*.xla* souboru). Je možné uložit sešit jako soubor s příponou .xla, ale tato operace není podporována ani doporučena. Pokud uložíte sešit, který má rozšíření se spravovaným kódem jako **Microsoft Office Excel Add-In (\*.xla)** soubor, můžete ho vybrat v **Add-Ins** dialogové okno použít pro jiný sešit. V některých případech může váš kód poběží v cílovém sešitu po použití doplňku VSTO, ale takové použití řešení pro Office se nepodporuje.  
  
## <a name="see-also"></a>Viz také:  
 [Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)   
 [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)   
 [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Začínáme s programováním přizpůsobení na úrovni dokumentu pro Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)   
 [Začínáme s programováním přizpůsobení na úrovni dokumentu pro Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)   
 [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  