---
title: Vývoj řešení pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a95c5f5767e227c35763cfaea1e3619093fffda3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833060"
---
# <a name="develop-office-solutions"></a>Vývoj řešení pro systém Office
  Po návrh projektu pomocí nástroje Office developer tools v sadě Visual Studio a nastavit soubory projektu, můžete začít se soustředit na implementaci kódu a vlastní uživatelské rozhraní (UI).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Zajímá vás vývoj řešení, které rozšiřují Office prostředí napříč [více platforem](https://dev.office.com/add-in-availability)? Podívejte se na nové [Office Add-ins modelu](https://dev.office.com/docs/add-ins/overview/office-add-ins). Doplňky sady Office mají malé náklady v porovnání s doplňky VSTO a řešení a je můžete vytvořit s využitím téměř jakékoli webové programování technologie, jako je například HTML5, JavaScript, CSS3 a XML.  
  
## <a name="office-solutions-programming-model"></a>Programovací model řešení pro systém Office  
 Objektový model Office poskytuje širokou škálu objekty, které můžete programovat proti. Pokaždé, když se program řešení pro systém Office pomocí spravovaného kódu, můžete napsat kód, který používá typy v sestavení primární spolupráce sady Office. V řešení, které vytvoříte pomocí šablony projektů pro Office v sadě Visual Studio také napsat kód přímo proti generované třídy ve vašem projektu. Další informace najdete v tématu [psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="program-different-types-of-office-solutions"></a>Program různé druhy řešení pro systém Office  
 Typ řešení, které vytváříte určuje funkcí, které můžete použít ve vašem projektu. Například můžete přidat ovládací prvky Windows Forms a ovládacích prvků rozšířenou Office (s názvem *hostování ovládacích prvků*) do přizpůsobení na úrovni dokumentu přetažením položek z **nástrojů** v sadě Visual Studio v době návrhu . Nicméně pokud vyvíjíte doplňku VSTO, pouze přidáte tyto druhy ovládacích prvků do dokumentů za běhu, napsáním kódu.  
  
 Další informace o funkcích, které jsou specifické pro různé druhy řešení naleznete v následujících tématech:  
  
- [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md).  
  
- [Programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md).  
  
- [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md).  
  
  Obecné informace, které vám pomohou při plánování řešení systému Office a postupy, které vám pomůžou vytvořit projekty, naleznete v tématu [návrhu a vytvořte řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)|Popisuje různé aspekty psaní kódu v řešeních pro systém Office.|  
|[Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)|Přehled modelu programování doplňků VSTO a související úlohy programování.|  
|[Programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md)|Poskytuje přehled o programovací model přizpůsobení na úrovni dokumentu a související úlohy programování.|  
|[Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)|Popisuje různé způsoby, které lze přizpůsobit uživatelské rozhraní aplikací s použitím doplňků VSTO a přizpůsobení na úrovni dokumentu.|  
|[Data v řešeních pro systém Office](../vsto/data-in-office-solutions.md)|Popisuje různé způsoby, které můžete pracovat s daty v řešeních pro systém Office, jako je například vazba dat k ovládacím prvkům a ukládání do mezipaměti data v přizpůsobeních na úrovni dokumentu.|  
|[Jak ovlivňuje automatické ukládání řešení pro systém Office](./how-autosave-impacts-office-solutions.md)|Popisuje úpravy, které můžete potřebovat tak, aby řešení pro systém Office, když je povoleno automatické ukládání.|
|[Řešení potíží s řešení pro systém Office](../vsto/troubleshooting-office-solutions.md)|Poskytuje tipy pro řešení běžných problémů, které se mohou vyskytnout při vytváření řešení pro systém Office.|  
|[Podpora v systému Office práce s vlákny](../vsto/threading-support-in-office.md)|Poskytuje přehled práce s více vlákny v řešeních pro systém Office.|  
|[Usnadnění v projektech pro systém Office](../vsto/accessibility-in-office-projects.md)|Popisuje funkce pro usnadnění přístupu, které jsou k dispozici v řešeních pro systém Office.|  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: vytvoření a změny přizpůsobených vlastností dokumentu](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [Postupy: čtení z a zapisovat do vlastností dokumentu](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [Postupy: cílení na vícejazyčné uživatelské rozhraní sady Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Návod: Vytvoření vašeho prvního doplňku VSTO pro Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [Návod: Vytvoření prvního přizpůsobení na úrovni dokumentu pro Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Návod: Vytvoření vašeho prvního doplňku VSTO pro Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [Návod: Vytvoření vašeho prvního doplňku VSTO pro PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Návod: Vytvoření vašeho prvního doplňku VSTO pro Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Návod: Vytvoření vašeho prvního doplňku VSTO pro Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [Návod: Vytvoření prvního přizpůsobení na úrovni dokumentu pro Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  