---
title: Integrace obchodních dat do služby SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e75367844a3a62e044a98f9d52c567fcfca3590e
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120363"
---
# <a name="integrate-business-data-into-sharepoint"></a>Integrace obchodních dat do služby SharePoint
  Obchodní data můžete integrovat do služby SharePoint. Obchodní data mohou pocházet z back-end serverů aplikace, jako například [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel a SAP, nebo webové službě. Uživatele můžete zobrazit, přidat, aktualizovat nebo odstranit podniková data pomocí externí seznamy nebo obchodní Data webových částí služby SharePoint.  Uživatelé mohou také přístup k těmto datům do offline režimu v aplikaci Microsoft Office, jako je například Microsoft Outlook. Další informace najdete v tématu [kde můžete můžete zobrazit externí Data](http://go.microsoft.com/fwlink/?LinkId=169295).  
  
 K integraci dat do služby SharePoint, vytvořte model pro službu Business Data Connectivity (BDC). Služby BDC je aplikace ve službě SharePoint, která ukládá informace o datech v podnikových aplikací. Další informace najdete v tématu [Business Data Connectivity (BDC) služby](http://go.microsoft.com/fwlink/?LinkID=169276).  
  
## <a name="models-in-visual-studio"></a>Modely v sadě Visual Studio  
 Modely v sadě Visual Studio umožňují psát vlastní kód načíst a aktualizovat data ze zdrojů dat back-end. Můžete také agregovaná data z více zdrojů dat. Například můžete zobrazit seznam zákazníků, které obsahuje data z [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] databáze a webové služby.  
  
 Můžete také importovat modely, které jsou již nasazeny do služby SharePoint. Po importu modelu, můžete přidat vlastní kód nebo právě použijte sadu Visual Studio pro zabalení a nasazení modelu na více serverové farmy služby SharePoint. Další informace najdete v tématu [vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="design-a-model-in-visual-studio"></a>Návrh model v sadě Visual Studio
 Model můžete navrhnout pomocí návrháře a několik nástroje systému windows. Při návrhu modelu, Visual Studio generuje modelu XML. Další informace najdete v tématu [návrhu modelu služby BDC nástroje Přehled](../sharepoint/bdc-model-design-tools-overview.md).  
  
 Model obsahuje entity a metody.  
  
### <a name="entities"></a>entity  
 Entity popisuje kolekci polí. Například entita může představovat tabulky v databázi. Entita se zobrazí jako externí obsah ve službě SharePoint. Další informace o externích typů obsahu najdete v tématu [co jsou externích typů obsahu?](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### <a name="methods"></a>Metody  
 Metoda umožňuje uživatelé externí obsah k provedení akce na pole entity. Například může povolit uživatelům změnit adresu aktualizační metody a narození datum zákazník kde `Address` a `BirthDate` jsou pole `Customer` entity.  
  
 Visual Studio generuje souboru kódu služby pro každé entity v modelu. Když přidáte metodu modelu, Visual Studio vygeneruje odpovídající metodu v souboru kódu služby. Přidávání kódu do jednotlivých možností, jak provést na příslušnou úlohu. Pokud přidáte metody vytvoření modelu, Visual Studio generuje metody vytvoření v souboru kódu služby. Tato metoda je volána službou BDC, když uživatel klikne **nová položka** tlačítko v seznamu, která je založená na modelu. Proto přidejte kód do metody vytvoření, která přidává nová data do zdroje dat. Další informace najdete v tématu [návrhu modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
## <a name="related-topics"></a>Související témata
  
|Název|Popis|  
|-----------|-----------------|  
|[Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md)|Ukazuje, jak vytvořit nový model nebo importovat model, který můžete exportovat ze služby SharePoint.|  
|[Navrhování modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)|Vysvětluje, jak navrhnout elementy modelu pomocí nástrojů Visual Studio návrhu.|  
|[Při použití aplikace SharePoint Designer vs. Visual Studio při sestavování řešení pomocí BCS](http://go.microsoft.com/fwlink/?LinkID=183448)|Pomoc při rozhodování, jestli se má použít Visual Studio nebo pomocí služby SharePoint Designer pro vytvoření modelu pro Záložní.|  
  
